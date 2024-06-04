## Problem

## Bounded Buffer Problem
Dalam Bounded Buffer Problem terdapat tiga entitas slot buffer penyimpanan, yaitu konsumen dan produsen. Produsen mencoba menyimpan data di slot penyimpanan sedangkan konsumen mencoba mengeluarkan data dari penyimpanan buffer.
Ini adalah salah satu masalah sinkronisasi proses yang paling penting, mari kita pahami lebih lanjut tentang hal yang sama.
Masalah bounded buffer menggunakan Semaphore. Harap baca lebih lanjut tentang Semaphore di sini sebelum melanjutkan dengan posting ini di sini.



![Bound-buffer-problem-ezgif com-webp-to-png-converter](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/29453182-9f6e-4dde-8d94-6da678e5459d)


Kita perlu memastikan bahwa akses ke buffer data hanya dilakukan oleh produsen atau konsumen, yaitu ketika produsen menempatkan item di buffer, konsumen tidak boleh mengonsumsi.
Penjelasan Masalah Produsen (Producer Problem)



Deskripsi:


Produsen menghasilkan data dan menempatkannya ke dalam buffer.
Konsumen mengambil data dari buffer dan mengolahnya.
Buffer memiliki ukuran terbatas yang ditunjukkan oleh n (jumlah slot buffer).


Masalah yang Muncul:


Kondisi Buffer Penuh: Jika produsen terus menghasilkan data tanpa ada konsumen yang mengambil data dari buffer, buffer akan penuh. Pada saat ini, produsen harus menunggu hingga ada slot kosong di buffer sebelum dapat menempatkan data baru.
Kondisi Buffer Kosong: Jika konsumen terus mengambil data dari buffer tanpa ada produsen yang menambahkan data baru, buffer akan kosong. Pada saat ini, konsumen harus menunggu hingga ada data baru yang ditambahkan oleh produsen.



Contoh Alur Kerjanya


Produsen:


Produsen menghasilkan data.
Produsen memanggil wait(kosong) untuk memastikan ada slot kosong di buffer.
Produsen mengunci mutex untuk memastikan tidak ada thread lain yang mengakses buffer.
Produsen menambahkan data ke buffer.
Produsen melepaskan mutex.
Produsen memanggil signal(penuh) untuk menunjukkan ada satu item baru di buffer.


Konsumen:



Konsumen memanggil wait(penuh) untuk memastikan ada item di buffer.
Konsumen mengunci mutex untuk memastikan tidak ada thread lain yang mengakses buffer.
Konsumen mengambil data dari buffer.
Konsumen melepaskan mutex.
Konsumen memanggil signal(kosong) untuk menunjukkan ada satu slot kosong baru di buffer.






## Readers and Writers Problem

Readers/Writers adalah salah satu masalah sinkronisasi klasik yang sering digunakan untuk mendiskusikan dan membandingkan berbagai cara untuk menyelesaikan masalah sinkronisasi. Secara singkat, masalah ini terjadi ketika ada beberapa pembaca dan penulis ingin mengakses suatu berkas pada saat bersamaan.

![readers-writers-problem-of-ipcoperating-system-4-638](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/e1ad11e9-1a3a-4077-9a90-e1cf893b2eee)

Masalah Readers/Writers, seperti yang telah dikatakan di atas bahwa inti dari permasalahan ini adalah adanya beberapa pembaca dan penulis yang ingin mengakses suatu berkas secara simultan. Sebagai syarat bahwa data yang terkandung dalam berkas tersebut tetap konsisten, maka setiap kali berkas tersebut ditulis, maka hanya ada boleh maksimal satu penulis yang menulisnya. Untuk pembaca, hal ini tidak perlu dikhawatirkan sebab membaca suatu berkas tidak mengubah isinya. Dengan kata lain, pada suatu saat diperbolehkan untuk beberapa pembaca untuk membaca berkas tersebut. Akan tetapi, ketika ada yang sedang menulis, tidak boleh ada satupun yang membaca. Ini berarti bahwa thread penulis menjalankan tugasnya secara eksklusif.

Untuk mengatasi masalah ini, ada tiga macam solusi . Dasar pembagian solusi ini adalah prioritas. Pertama, solusi dengan pembaca diprioritaskan akan dibahas. Kemudian dilanjutkan dengan solusi dengan penulis yang diprioritaskan. Terakhir, solusi dengan pembaca dan penulis saling bergantian akan dibahas. Pada setiap solusi akan dilihat mengenai tingkat kesuksesan solusi tersebut bila kita lihat dari sudut pandang syarat penyelesaian critical section. Implementasi dari setiap solusi yang diberikan di bawah ini adalah dengan menggunakan semafor.

Readers and Writers Problem adalah problem yang memodelkan proses yang mengakses database. Masalah ini timbul ketika ada dua proses atau lebih berbagi data yang sama. Data yang dimaksud disini bisa berbentuk buffer, file atau objek dari suatu program
Terdapat dua variasi pada masalah ini, yaitu :
seorang reader tidak perlu menuggu reader lain untuk selesai hanya karena ada writer menunggu (reader memiliki prioritas lebih tinggi disbanding dengan writer)
Jika ada writer yang sedang menunggu, maka tidak boleh ada reader lain yang bekerja (writer memiliki prioritas yang lebih tinggi)
Jika terdapat writer dalam critical section dan terdapat n reader yang menunggu, maka satu reader akan antri di wrt dan n-1 reader akan antri di mutex. Jika writer mengeksekusi signal(wrt), maka dapat disimpulkan bahwa eksekusi adalah menunggu reader atau menunggu satu writer.
Solusi Readers and Writers Problem
a.Pembaca di prioritaskan
b.Penulis di prioritaskan




## Dining Philosophers

Dining Philosophers Prolem
Masalah ini pertama kali ditulis dan diselesaikan oleh Djikstra pada tahun 1965.Masalah ini memodelkan masalah enkapsulasi dari ketergantungan mesin dan masalah portabilitas. Dalam masalah Dining Philosophers, diketahui sejumlah (N) filusuf yang hanya memiliki tiga status, berpikir, lapar, dan makan. Semua filusuf berada di sebuah meja makan bundar yang ditata sehingga di depan setiap filusuf ada sebuah piring berisi mie dan di antara dua piring yang bersebelahan terdapat sebuah sumpit.

![livelock](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/85acf571-b341-463d-9c02-73f9dac00c8c)



## Solusi Dining – Philosophers Problem ada dua, yakni :


a.Solusi Waiter
Solusi Waiter : solusi sederhana ini dilakukan dengan mengadakan seorang waiter yang senantiasa mengawasi penggunaan sumpit di meja makan. Ketika empat buah (dua pasang) sumpit sedang dipakai,orang berikutnya yang ingin memakai sumpit harus meminta izin kepada sang waiter, yang hanya dapat diberi ketika salah satu sumpit telah selesai terpakai.
b.Solusi Hierarki Resource
 Solusi Hirarki Resource: resources (sumpit) di meja makan telah diberi susunan hirarki. Setiap permintaan orang terhadap sebuah sumpit harus dilakukan pada susunan tertentu, dan dikembalikan pada susunan sebaliknya. Dalam hal ini, setiap orang dapat mengambil sumpit dimanapun diatas meja. Misalkan setiap sumpit diberi nomor sebagai tingkat hirarki dari 1 sampai 5, seseorang hanya dapat mengambil sumpit dengan nomor yang paling rendah, kemudian mengambil sumpit yang setingkat lebih tinggi. Ketika ia hendak mengembalikannya, orang itu harus meletakkan sumpit dengan nomor yang lebih tinggi terlebih dahulu, lalu yang rendah.
