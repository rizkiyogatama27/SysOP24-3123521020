<img width="512" alt="Cuplikan layar 2024-03-02 134409" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/2d49549e-3af9-4a3a-8ae6-6e77f1d4e4eb">

Step Step Proses Booting : 
tujuan dari booting adalah untuk menjalankan serangkaian proses yang dibutuhkan oleh komputer sampai pada tahap dapat digunakan oleh user.

Adapun proses booting itu sendiri dimulai dari saat pertama kali  menyalakan komputer.

Jadi, saat  menyalakan komputer, tidak ada program di dalam memori utama (RAM), sehingga CPU mencari program lain, yang disebut BIOS (Basic Input/Output System) dan menjalankannya.

BIOS adalah firmware yang terletak di motherboard dan dijalankan oleh CPU untuk memulai urutan booting.

Setelah BIOS mulai berjalan, ia memulai proses yang disebut POST (Power-On Self-Test) yang menguji semua perangkat keras dan memastikan tidak ada masalah. 

jika POST menemukan beberapa masalah pada perangkat keras, proses booting berhenti dan komputer gagal melakukan booting.

Setelah menjalankan POST, BIOS melanjutkan untuk memuat MBR (Master Boot Record) dari perangkat yang dapat di-boot ke dalam RAM.

MBR terdiri dari 512 atau lebih byte yang terletak di sektor paling awal dari perangkat yang dapat di-boot (yakni berupa HDD, SSD, atau flash drive).

Setelah memuat MBR ke dalam RAM, BIOS menjalankan instruksi pertama yang dimuat dari MBR.

Instruksi pertama biasanya kode bootstrap, alias bootloader, yang merupakan program ditulis dalam kode mesin memuat sistem operasi ke dalam RAM.

Setiap sistem operasi memiliki bootloader sendiri. Misalnya, GNU GRUB, LILO (Linux Loader), dan refind adalah beberapa bootloader Linux yang populer.

Setelah OS dimuat ke dalam memori, OS mulai berjalan. Selanjutnya, OS memulai inisialisasinya sendiri (termasuk memuat driver perangkat, menyiapkan perpustakaan, dll). 

ketika inisialisasi OS selesai, OS memulai shell yang menampilkan prompt login kepada pengguna.

2.	Identifikasi Laptop Anda Melalui CPU Z? 
CPU

<img width="303" alt="Cuplikan layar 2024-03-01 003200" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/e1862744-23ec-4b60-8ee4-27ecae3c9dc7">


Name CPU : Intel Core i5 

Code Name : Tiger Lake-U. Tiger Lake merupakan chip dengan arsitektur 10 nm dari Intel yang dirilis Mei 2021. Prosesor ini awalnya ditujukan terutama untuk laptop. Namun karena persaingan ketat dari AMD Ryzen 4000 (Renoir), Intel kemudian meluncurkan 65W B-series yang memungkinkan klien memasang prosesor Tiger Lake ke sistem desktop

Technology : 10 nm, Nanometer adalah sebuah ukuran panjang yang sama dengan 1.0×10−9 meter — atau sepermilyar meter.

Spesifikasi : Intel Core i5 11320H Generasi 11, (huruf H di belakang angka adalah seri high performance) memiliki 3.20GHz , GHz mengacu pada jumlah siklus getaran elektronik yang terjadi dalam satu detik
Memilki 4 Core dan 8 Threads. Core dan thread merupakan komponen yang dari CPU, core bertugas untuk melakukan dan mengeksekusi tugas, sedangkan thread berfungsi untuk memecah beban kerja core untuk meningkatkan efisiensi dan performa CPU..

Mainboard

<img width="296" alt="Cuplikan layar 2024-03-01 004320" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/417545ef-3d99-4a08-93f5-fde91f438958">


Chipset : Intel Tiger Lake dengan Southbridge Tiger Lake-U/Y PCH Southbridge adalah bagian pada computer yang berfungsi untuk menangani


Memory 

<img width="302" alt="Cuplikan layar 2024-03-01 004813" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/f5670ade-caa3-4e45-af1c-ea238876ed0a">


TYPE MEMORY DDR 4 : DDR4 adalah singkatan dari "Double Data Rate 4”, dan merupakan generasi keempat dari teknologi DDR, yang menggantikan SDRAM SDR (Single Data Rate). DDR4 memiliki tingkat transfer data yang lebih cepat, kapasitas yang lebih besar, dan voltase lebih rendah dibandingkan generasi sebelumnya.
Size Ram yang saya pakai adalah 8 GB dan Memiliki Chanel 4 x 64-bit, Chanel adalah komponen yang berguna sebagai jalur komukasi untuk mengakses data yang akan disimpan sementara di RAM.


SPD

<img width="301" alt="Cuplikan layar 2024-03-01 202206" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/26f96be0-7b6c-4ce9-bf99-d4ce6b3d1823">


Memiliki 8 Memori slot dengan kecepatan DDR 4(DDR4 memiliki tingkat transfer data yang lebih cepat, kapasitas yang lebih besar, dan voltase lebih rendah dibandingkan generasi sebelumnya.)
Dan tipe memori yang di pakai di laptop ini adalah Samsung


GRAPIHCS

<img width="302" alt="Cuplikan layar 2024-03-01 202653" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/a20901e0-a57f-441e-9079-452539a98667">


GPU yang di pakai i5 Version: Intel® Iris® Xᵉ Graphics 


BENCH

<img width="303" alt="Cuplikan layar 2024-03-01 203052" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/a04d08cd-158b-4d7b-886c-f866128c4676">

BENCH untuk melakukan uji coba kecepatan skor prosesor dengan prosesor yang lain 
