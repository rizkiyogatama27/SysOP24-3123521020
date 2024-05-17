## Perbedaan Serial, Parallel, Concurent dan Concurent Parallel

1. [Parallel](parallel)
2. [Concurent](concurent)
3. [Concurent Parallel](concurent-parallel)






Gambar Judul
![331189923-9106f52c-9d9b-4a64-8ddd-2fae76becb24](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/c25cc923-8322-4c09-81bd-fcaa5ca8756b)


Parallel 
Parallel adalah beberapa proses / proses yang dilakukan secara bersamaan
Seperti contoh pada gambar diatas dimana core1 menjalankan task 1 dan core 2 menjalankan task 2 secara bersamaan.

![331191312-46409dcc-8174-45f8-a6df-4fe32154d5ba](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/28a1b0e7-f14d-4ac6-93cb-a44e3439e07d)

Pada gambar ini Proses A dan Proses B menjalankan proses 1, proses 2, proses 3 secara bersamaan / dalam satu waktu 
Ksimpulan : Proses akan lebih efisien dengan membagi kerja sehingga dapat mempercepat waktu eksekusi keseluruhan tugas. 

Concurent

Concurrent adalah sebuah proses yang dijalankan secara sekaligus secara bergantian , bukan seacara bersamaan tapi secara sekaligus. pada gambar {diatas} Core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalu core 1 menjalankan task 2.2 core 2 menjalankan task 1.2 dikarenakan proses task 1.2 belum selesai maka core 1 menjslankan task 2.3 lalu core 2 setelah proses dari task 1.2 selesai maka menjalankan proses task 1.3 lalu setelah core 1 selesai makan akan menjalankan proses setelahnya.

![331197119-f24e60c8-45d1-42c6-bd38-fa261ffb08df](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/95bbf426-f3d0-4491-a9b7-68d0c06a072e)


dari gambar di atas Proses A menjalankan task 1 lalu ketika task 1 selesai makan akan menjalankan proses lainya 

Paraller dan Concurent



Concurrent and Parallel dijalankan secara bersamaan dan bergantian pada dua core.
seperti contoh pada gambar judul di atas core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalau setelah task 1.1 proses selesai lanjut mrnjalankan task 2.2 dan  dan 2.3 secara urut lalu pada core 2 selewsai menjalankan task 2.1 makan akan menjalankan task 1.2 dikarenakan task 1.1 sudah terisi oleh task 2.2 maka core 2 menjalankan task 1.2 dan 1.3 dan seterusnya   
Kesimpulan : penggunaan CPU yang lebih optimal utuk menjaga responsivitas sistem.

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


do
{

    // wait until empty > 0 and then decrement 'empty'
    // that is there must be atleast 1 empty slot
    
    wait (empty);
    
    // acquire the lock, so consumer can't enter
    
    wait (mutex);

    /* perform the insert operation in a slot */

    // release lock
    
    signal (mutex);
    
    // increment 'full'
    
    signal (full);
  }
while (TRUE)


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



