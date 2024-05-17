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



## Producer Buffer Solution





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



