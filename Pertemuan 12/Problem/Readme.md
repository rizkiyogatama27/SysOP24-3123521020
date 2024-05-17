## Problem

## Bounded Buffer Problem
Dalam Bounded Buffer Problem terdapat tiga entitas slot buffer penyimpanan, yaitu konsumen dan produsen. Produsen mencoba menyimpan data di slot penyimpanan sedangkan konsumen mencoba mengeluarkan data dari penyimpanan buffer.
Ini adalah salah satu masalah sinkronisasi proses yang paling penting, mari kita pahami lebih lanjut tentang hal yang sama.
Masalah bounded buffer menggunakan Semaphore. Harap baca lebih lanjut tentang Semaphore di sini sebelum melanjutkan dengan posting ini di sini.



![Bound-buffer-problem-ezgif com-webp-to-png-converter](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/29453182-9f6e-4dde-8d94-6da678e5459d)


Kita perlu memastikan bahwa akses ke buffer data hanya dilakukan oleh produsen atau konsumen, yaitu ketika produsen menempatkan item di buffer, konsumen tidak boleh mengonsumsi.
Kita melakukan itu melalui tiga entitas
Mutex mutex – used to lock and release critical section
empty – Keeps tab on number empty slots in the buffer at any given time
Initialised as n as all slots are empty.
full – Keeps tab on number of entities in buffer at any given time.
Initialised as 0

## Readers Writer Wait and Signal Implementation




wait(Semaphore s)
{
  while(s == 0);
  s = s-1;
}

signal(Semaphore s)
{
  s = s+1;
}



Producer Buffer Solution





#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>

#define BUFFER_SIZE 5

int buffer[BUFFER_SIZE];
int in = 0;
int out = 0;

sem_t empty;
sem_t full;
sem_t mutex;

void *producer(void *param) {
    int item;
    for (int i = 0; i < 10; i++) {
        item = i;  // Producing an item

        // Wait until there's at least one empty slot
        sem_wait(&empty);

        // Acquire the lock, so the consumer can't enter
        sem_wait(&mutex);

        // Perform the insert operation in a slot
        buffer[in] = item;
        in = (in + 1) % BUFFER_SIZE;
        printf("Producer produced: %d\n", item);

        // Release the lock
        sem_post(&mutex);

        // Increment 'full'
        sem_post(&full);
    }
    return NULL;
}

void *consumer(void *param) {
    int item;
    for (int i = 0; i < 10; i++) {
        // Wait until there's at least one full slot
        sem_wait(&full);

        // Acquire the lock, so the producer can't enter
        sem_wait(&mutex);

        // Perform the remove operation from a slot
        item = buffer[out];
        out = (out + 1) % BUFFER_SIZE;
        printf("Consumer consumed: %d\n", item);

        // Release the lock
        sem_post(&mutex);

        // Increment 'empty'
        sem_post(&empty);
    }
    return NULL;
}

int main() {
    pthread_t tid1, tid2;

    // Initialize the semaphores
    sem_init(&empty, 0, BUFFER_SIZE);  // Initial value is BUFFER_SIZE
    sem_init(&full, 0, 0);             // Initial value is 0
    sem_init(&mutex, 0, 1);            // Initial value is 1 (binary semaphore)

    // Create the producer and consumer threads
    pthread_create(&tid1, NULL, producer, NULL);
    pthread_create(&tid2, NULL, consumer, NULL);

    // Wait for both threads to finish
    pthread_join(tid1, NULL);
    pthread_join(tid2, NULL);

    // Destroy the semaphores
    sem_destroy(&empty);
    sem_destroy(&full);
    sem_destroy(&mutex);

    return 0;
}



## Consumer Buffer Solution


do 
{   

    // wait until full > 0 and then decrement 'full'
    // should be atleast 1 full slot in buffer
    
    wait(full);
    
    // acquire the lock
   
    wait(mutex);  
    
    /* perform the remove operation in a slot */ 
    
    // release the lock
    
    signal(mutex); 
    
    // increment 'empty'
    
    signal(empty); 
    
} 
while(TRUE);
Prime Course Trailer



## Readers and Writers Problem

Readers/Writers adalah salah satu masalah sinkronisasi klasik yang sering digunakan untuk mendiskusikan dan membandingkan berbagai cara untuk menyelesaikan masalah sinkronisasi. Secara singkat, masalah ini terjadi ketika ada beberapa pembaca dan penulis ingin mengakses suatu berkas pada saat bersamaan.

![readers-writers-problem-of-ipcoperating-system-4-638](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/e1ad11e9-1a3a-4077-9a90-e1cf893b2eee)

Masalah Readers/Writers, seperti yang telah dikatakan di atas bahwa inti dari permasalahan ini adalah adanya beberapa pembaca dan penulis yang ingin mengakses suatu berkas secara simultan. Sebagai syarat bahwa data yang terkandung dalam berkas tersebut tetap konsisten, maka setiap kali berkas tersebut ditulis, maka hanya ada boleh maksimal satu penulis yang menulisnya. Untuk pembaca, hal ini tidak perlu dikhawatirkan sebab membaca suatu berkas tidak mengubah isinya. Dengan kata lain, pada suatu saat diperbolehkan untuk beberapa pembaca untuk membaca berkas tersebut. Akan tetapi, ketika ada yang sedang menulis, tidak boleh ada satupun yang membaca. Ini berarti bahwa thread penulis menjalankan tugasnya secara eksklusif.

Untuk mengatasi masalah ini, ada tiga macam solusi yang akan dibahas. Dasar pembagian solusi ini adalah prioritas. Pertama, solusi dengan pembaca diprioritaskan akan dibahas. Kemudian dilanjutkan dengan solusi dengan penulis yang diprioritaskan. Terakhir, solusi dengan pembaca dan penulis saling bergantian akan dibahas. Pada setiap solusi akan dilihat mengenai tingkat kesuksesan solusi tersebut bila kita lihat dari sudut pandang syarat penyelesaian critical section. Implementasi dari setiap solusi yang diberikan di bawah ini adalah dengan menggunakan semafor.

Readers and Writers Problem adalah problem yang memodelkan proses yang mengakses database. Masalah ini timbul ketika ada dua proses atau lebih berbagi data yang sama. Data yang dimaksud disini bisa berbentuk buffer, file atau objek dari suatu program
Terdapat dua variasi pada masalah ini, yaitu :
seorang reader tidak perlu menuggu reader lain untuk selesai hanya karena ada writer menunggu (reader memiliki prioritas lebih tinggi disbanding dengan writer)
Jika ada writer yang sedang menunggu, maka tidak boleh ada reader lain yang bekerja (writer memiliki prioritas yang lebih tinggi)
Jika terdapat writer dalam critical section dan terdapat n reader yang menunggu, maka satu reader akan antri di wrt dan n-1 reader akan antri di mutex. Jika writer mengeksekusi signal(wrt), maka dapat disimpulkan bahwa eksekusi adalah menunggu reader atau menunggu satu writer.
Solusi Readers and Writers Problem
a.Pembaca di prioritaskan
b.Penulis di prioritaskan


## Implementasi Readers-Writers Problem


#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>

sem_t rw_mutex;  // Semaphore untuk akses eksklusif oleh penulis
sem_t mutex;     // Semaphore untuk melindungi counter pembaca
int read_count = 0;  // Counter untuk jumlah pembaca aktif

void *writer(void *param) {
    int id = *((int *)param);
    for (int i = 0; i < 5; i++) {
        // Penulis menunggu untuk mendapatkan akses eksklusif
        sem_wait(&rw_mutex);
        printf("Writer %d is writing\n", id);
        // Simulasikan operasi penulisan dengan sleep
        sleep(1);
        printf("Writer %d has finished writing\n", id);
        // Penulis melepaskan akses eksklusif
        sem_post(&rw_mutex);
        // Simulasikan waktu tunggu sebelum menulis lagi
        sleep(1);
    }
    return NULL;
}

void *reader(void *param) {
    int id = *((int *)param);
    for (int i = 0; i < 5; i++) {
        // Pembaca menunggu untuk mendapatkan akses ke counter pembaca
        sem_wait(&mutex);
        read_count++;
        if (read_count == 1) {
            // Pembaca pertama meminta akses eksklusif ke penulis
            sem_wait(&rw_mutex);
        }
        // Pembaca melepaskan akses ke counter pembaca
        sem_post(&mutex);

        // Pembaca membaca data
        printf("Reader %d is reading\n", id);
        // Simulasikan operasi pembacaan dengan sleep
        sleep(1);
        printf("Reader %d has finished reading\n", id);

        // Pembaca menunggu untuk mendapatkan akses ke counter pembaca
        sem_wait(&mutex);
        read_count--;
        if (read_count == 0) {
            // Pembaca terakhir melepaskan akses eksklusif ke penulis
            sem_post(&rw_mutex);
        }
        // Pembaca melepaskan akses ke counter pembaca
        sem_post(&mutex);
        // Simulasikan waktu tunggu sebelum membaca lagi
        sleep(1);
    }
    return NULL;
}

int main() {
    pthread_t readers[5], writers[2];
    int reader_ids[5] = {1, 2, 3, 4, 5};
    int writer_ids[2] = {1, 2};

    // Inisialisasi semafor
    sem_init(&rw_mutex, 0, 1);
    sem_init(&mutex, 0, 1);

    // Membuat thread pembaca
    for (int i = 0; i < 5; i++) {
        pthread_create(&readers[i], NULL, reader, &reader_ids[i]);
    }

    // Membuat thread penulis
    for (int i = 0; i < 2; i++) {
        pthread_create(&writers[i], NULL, writer, &writer_ids[i]);
    }

    // Menunggu semua thread selesai
    for (int i = 0; i < 5; i++) {
        pthread_join(readers[i], NULL);
    }
    for (int i = 0; i < 2; i++) {
        pthread_join(writers[i], NULL);
    }

    // Menghancurkan semafor
    sem_destroy(&rw_mutex);
    sem_destroy(&mutex);

    return 0;
}



## Dining Philosophers

Dining Philosophers Prolem
Masalah ini pertama kali ditulis dan diselesaikan oleh Djikstra pada tahun 1965.Masalah ini memodelkan masalah enkapsulasi dari ketergantungan mesin dan masalah portabilitas. Dalam masalah Dining Philosophers, diketahui sejumlah (N) filusuf yang hanya memiliki tiga status, berpikir, lapar, dan makan. Semua filusuf berada di sebuah meja makan bundar yang ditata sehingga di depan setiap filusuf ada sebuah piring berisi mie dan di antara dua piring yang bersebelahan terdapat sebuah sumpit.

![livelock](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/85acf571-b341-463d-9c02-73f9dac00c8c)



## Solusi Dining – Philosophers Problem ada dua, yakni :


a.Solusi Waiter
Solusi Waiter : solusi sederhana ini dilakukan dengan mengadakan seorang waiter yang senantiasa mengawasi penggunaan sumpit di meja makan. Ketika empat buah (dua pasang) sumpit sedang dipakai,orang berikutnya yang ingin memakai sumpit harus meminta izin kepada sang waiter, yang hanya dapat diberi ketika salah satu sumpit telah selesai terpakai.
b.Solusi Hierarki Resource
 Solusi Hirarki Resource: resources (sumpit) di meja makan telah diberi susunan hirarki. Setiap permintaan orang terhadap sebuah sumpit harus dilakukan pada susunan tertentu, dan dikembalikan pada susunan sebaliknya. Dalam hal ini, setiap orang dapat mengambil sumpit dimanapun diatas meja. Misalkan setiap sumpit diberi nomor sebagai tingkat hirarki dari 1 sampai 5, seseorang hanya dapat mengambil sumpit dengan nomor yang paling rendah, kemudian mengambil sumpit yang setingkat lebih tinggi. Ketika ia hendak mengembalikannya, orang itu harus meletakkan sumpit dengan nomor yang lebih tinggi terlebih dahulu, lalu yang rendah.

## Implementasi Dining Philosophers

#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>
#include <unistd.h>

#define NUM_PHILOSOPHERS 5

sem_t forks[NUM_PHILOSOPHERS];
sem_t mutex; // Semaphore untuk menghindari deadlock

void *philosopher(void *param) {
    int id = *((int *)param);
    int left = id;
    int right = (id + 1) % NUM_PHILOSOPHERS;

    while (1) {
        // Filosof sedang berpikir
        printf("Philosopher %d is thinking.\n", id);
        sleep(1);

        // Ambil kedua garpu
        sem_wait(&mutex);  // Mencegah deadlock dengan membatasi jumlah filsuf yang mencoba makan
        sem_wait(&forks[left]);
        sem_wait(&forks[right]);
        sem_post(&mutex);

        // Filosof sedang makan
        printf("Philosopher %d is eating.\n", id);
        sleep(1);

        // Letakkan kedua garpu
        sem_post(&forks[left]);
        sem_post(&forks[right]);

        // Filosof kembali berpikir
    }

    return NULL;
}

int main() {
    pthread_t philosophers[NUM_PHILOSOPHERS];
    int ids[NUM_PHILOSOPHERS];

    // Inisialisasi semafor
    sem_init(&mutex, 0, NUM_PHILOSOPHERS - 1);  // Membatasi jumlah filsuf yang dapat mengambil garpu
    for (int i = 0; i < NUM_PHILOSOPHERS; i++) {
        sem_init(&forks[i], 0, 1);
    }

    // Membuat thread filsuf
    for (int i = 0; i < NUM_PHILOSOPHERS; i++) {
        ids[i] = i;
        pthread_create(&philosophers[i], NULL, philosopher, &ids[i]);
    }

    // Menunggu semua thread selesai (sebenarnya tidak pernah selesai dalam kasus ini)
    for (int i = 0; i < NUM_PHILOSOPHERS; i++) {
        pthread_join(philosophers[i], NULL);
    }

    // Menghancurkan semafor
    sem_destroy(&mutex);
    for (int i = 0; i < NUM_PHILOSOPHERS; i++) {
        sem_destroy(&forks[i]);
    }

    return 0;
}

