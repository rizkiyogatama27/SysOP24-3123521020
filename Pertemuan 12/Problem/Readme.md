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



