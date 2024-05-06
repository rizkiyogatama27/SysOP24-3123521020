1.  Buatlah presentasi langkah demi langkah tentang siklus CPU (fetch,decode,execute) utk mengeksekusi sebuah program. Jelaskan juga peran dari Bahasa pemrograman dan compiler, begitu juga dengan peran dari Sistem Operasi. Gunakan referensi : [Video referensi 1](https://www.youtube.com/watch?v=Z5JC9Ve1sfI) dan [Video referensi 2](https://www.youtube.com/watch?v=jFDMZpkUWCw)

 **SIKLUS CPU**
<img width="431" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/c357dcb1-0874-49c6-8e9b-19a15c9a1f57">

**pada proses cpu berawal dari fetch(pengambilan alamat) kemudian decode (membaca nilai pada alamat yang diambil) selanjutnya execute (mengeksekusi perintah dari nilai yang diambil) proses itu berjalan dengan looping jadi setelah dieksekusi maka akan kembali mengambil alamat selanjutnya.**

**PROSES PERTAMA**

<img width="433" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/a96328d4-1807-47d8-9cb4-694765ec25ce">

**fetch alamat 0 kemudian membaca nilai dari alamat 0 yaitu load 6 kemudian dieksekusi pada alamat 6 memiliki value 1 dan dimasukkan kedalam accumulator.**

**PROSES KEDUA**
<img width="403" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/9c0823aa-c187-49bd-a4f7-a06bd82a068d">

**setelah looping kembali lagi fetch menambil alamat dalam memori yaitu 1 kemudian alamat 1 dilakukan pengkodean membaca perintah ADD 7 selanjutnya dilakukan eksekusi perintah pada alamat 7 nilai 1 ditambahkan ke accumulator sehingga yang awalnya 1 ditambah value dari address 7 menjadi 2.**

**PROSES KE TIGA** 
<img width="411" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/086c878a-95fe-4e59-9ba4-f3adb928c02a">

**kembali lagi looping ke proses fetch mengambil address 2 kemudian decode membaca value address 2 yang memiliki value store 6 yang kemudian dieksekusi menjadi perintah menyisipkan nilai accumulator ke addres 6 sehingga addres 6 yang awalnya memiliki value 1 berubah menjadi 2.**

**PROSES KE EMPAT**
<img width="407" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/b2798539-7ce9-4fd5-aa0e-2c5511e270e6">

**looping lagi ke proses fetch mengambil nilai 3 kemudian dilakukan decode membaca perintah pada addres 3 yaitu jump 1 kemudian dieksekusi value jump yang berarti melompat ke addres 1 sehingga addres 0 tidak lagi diambil nilainya.proses ini menjadi yang terakhir dimana proses kemudian kembali lagi ke value add 7 seperti pada proses 2 dan seterusnya.**

**KESIMPULAN**
**Kesimpulannya, dalam percobaan tersebut, CPU melakukan siklus kerja yang terdiri dari fetch, decode, dan execute untuk menjalankan instruksi-instruksi program secara berulang. Proses ini memungkinkan manipulasi data, pengambilan instruksi berikutnya, serta penggunaan instruksi jump untuk melompat ke alamat tertentu dalam program. Dengan demikian, CPU memainkan peran kunci dalam menjalankan operasi-operasi dasar komputer.**








**2. Program untuk mengukur Kemampuan CPU dalam satuan IOPS and FLOPS.**

**IOPS (Input/Output Operations Per Second):
IOPS mengukur jumlah operasi masukan/keluaran yang dapat dilakukan oleh suatu perangkat atau sistem dalam satu detik. IOPS biasanya digunakan untuk mengukur kinerja sistem penyimpanan, seperti hard disk drive (HDD), solid-state drive (SSD), atau sistem file secara keseluruhan.**

**FLOPS (Floating Point Operations Per Second):
FLOPS mengukur jumlah operasi floating point yang dapat dilakukan oleh suatu sistem dalam satu detik. Operasi floating point melibatkan operasi matematika yang melibatkan angka desimal (misalnya, pecahan atau bilangan riil). FLOPS adalah ukuran kinerja yang sering digunakan dalam komputasi ilmiah dan teknik, seperti simulasi fisika, analisis data, dan rendering grafis.**


**Build Binaries**
$make
<img width="396" alt="Cuplikan layar 2024-03-18 090542" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/5d574f0f-5c74-4afd-afce-2ab851ce874d">

**Cleaning Old Build**
$make clean
<img width="245" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/220f69e2-5218-41e6-931f-81b2d1bfbff3">

**Install Binaries**
$sudo make install
<img width="387" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/bf7f7c0f-3696-49fe-aa31-059514c32af4">

**Uninstall Binaries**
$ sudo make uninstall
<img width="493" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/cf951add-5b5e-4e1b-8eb6-fb4a6fc347b1">

**Usage**
iops64
<img width="499" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/971a0c38-033e-4d3b-9309-326ff7fa11a1">

flops64
<img width="499" alt="image" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/45046017-405d-4e04-8aeb-f2db34708654">

 **Catat hasilnya dan jelaskan arti dari hasil ekskusi.**
Perintah yang diberikan, "$ iops64 $(nproc)"   dan  "$ flops64 $(nproc)",  menjalankan dua program yang berbeda, "iops64" dan "flops64", dengan argumen yang dihasilkan oleh perintah "nproc" :

$(nproc): Ini adalah ekspresi shell yang mengembalikan jumlah prosesor yang tersedia pada sistem saat ini. Dengan kata lain, perintah ini menghasilkan output yang menunjukkan jumlah CPU core yang ada di sistem.

$ iops64: Ini kemungkinan adalah perintah untuk menjalankan program yang disebut "iops64". Program ini mungkin dirancang untuk mengukur atau menghitung IOPS (Input/Output Operations Per Second) pada sistem dengan menggunakan 64-bit operasi.

$ flops64: Sama seperti sebelumnya, ini perintah untuk menjalankan program yang disebut "flops64". Program ini kemungkinan dirancang untuk mengukur atau menghitung FLOPS (Floating Point Operations Per Second) pada sistem dengan menggunakan 64-bit operasi floatin


**Buat Plot perbandinnga hasil untuk masing-masing PC di tiap kelompokmu.**

kelompok_PC <- list(
  PC1 = c(IOPS = 64, FLOPS = 64),
  PC2 = c(IOPS = 64, FLOPS = 64),
  PC3 = c(IOPS = 64, FLOPS = 64)
)g-point.

Analisa hasil percobaan dan kesimpulan tentang IOPS (Input/Output Operations Per Second) dan FLOPS (Floating Point Operations Per Second), kita perlu memahami konteks percobaan dan data yang terkait. Secara umum, IOPS mengukur seberapa cepat suatu sistem dapat melakukan operasi masukan/keluaran (seperti membaca atau menulis data pada media penyimpanan), sedangkan FLOPS mengukur seberapa cepat suatu sistem dapat melakukan operasi floating-point (operasi matematika dengan angka desimal) dalam satu detik.


Kesimpulan: Berdasarkan hasil percobaan, kita dapat menyimpulkan seberapa efisien sistem dalam melakukan operasi masukan/keluaran dan operasi floating-point. Jika nilai IOPS tinggi, itu menunjukkan bahwa sistem mampu mengakses data dengan cepat dari media penyimpanan. Sementara itu, jika nilai FLOPS tinggi, itu menunjukkan kemampuan sistem untuk menyelesaikan operasi matematika kompleks dalam waktu singkat.




4. **Apabila Debian VM mu masih belum terdapat packeage gcc, make dan git, lakukan instalasi dan catat setiap langkahnya!**
<img width="399" alt="Cuplikan layar 2024-03-18 133628" src="https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/37ac05b2-5d06-4447-84b1-d10aaebd61d5">

**Perintah $ su digunakan untuk mengganti pengguna menjadi superuser atau root.

apt install gcc adalah perintah yang digunakan untuk menginstal compiler GNU Compiler Collection (GCC) melalui sistem manajemen paket Advanced Package Tool (APT). GCC adalah koleksi compiler yang diperlukan untuk mengkompilasi program-program dalam bahasa C, C++, dan beberapa bahasa lainnya di lingkungan Linux.

apt install make menginstal perangkat lunak Make, yang merupakan utilitas yang digunakan untuk mengotomatisasi proses kompilasi program. Make digunakan untuk mengelola dependensi dan mengkompilasi program dari sumber kode.

apt install git menginstal sistem kontrol versi Git. Git digunakan untuk mengelola dan mengontrol versi dari kode sumber perangkat lunak. Ini memungkinkan kolaborasi antar pengembang, pelacakan perubahan kode, dan manajemen proyek yang efisien.**
