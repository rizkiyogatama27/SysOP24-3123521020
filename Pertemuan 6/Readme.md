TUGAS PENDAHULUAN: 
Jawablah pertanyaan-pertanyaan di bawah ini : 

1. Apa yang dimaksud redirection ? 
2. Apa yang dimaksud pipeline ? 
3. Apa yang dimaksud perintah di bawah ini : 
echo, cat, more, sort, grep, wc, cut, uniq
Jawaban :
1.	Redirection adalah proses mengalihkan output dari suatu program atau perintah ke lokasi lain.
2.	Pipeline adalah Mekanisme pipa yang digunakan sebagai alat komunikasi antar proses.
3.	Echo : digunakan untuk menampilkan nilai atau variabel cara menngunakan nya echo “hello word”
cat :  Untuk menggabungkan dan menampilkan isi satu atau beberapa file secara urut.
more :  Untuk menampilkan isi file satu halaman pada satu waktu.
sort : Digunakan untuk mengurutkan masukannya berdasarkan urutan nomor ASCII dari karakter.
grep : untuk menyaring masukannya dan menampilkan baris-baris yang hanya 
mengandung pola yang ditentukan. Pola ini disebut regular expression. 
wc : Digunakan untuk menghitung jumlah baris, kata dan karakter dari baris-baris 
masukan yang diberikan kepadanya
cut : Digunakan untuk mengambil kolom tertentu dari baris-baris masukannya, yang
ditentukan pada option –c.
uniq : Digunakan untuk menghilangkan baris-baris berurutan yang mengalami duplikasi, biasanya digabungkan dalam pipeline dengan sort

Percobaan 1 : File descriptor
1.	Output ke layar (standar output), input dari system (kernel)
$ ps

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/f5b9cbb8-bda5-4bb5-8a77-274f7fdd94bd)


Keterangan : perintah ps digunakan untuk menampilkan daftar proses yang berjalan pada sistem.
2.	Output ke layar (standar output), input dari keyboard (standard input)
 $ cat
 hallo, apa khabar
 hallo, apa khabar
 exit dengan ^d
 exit dengan ^d
 [Ctrl-d]

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/22d8de16-23d7-49c8-a4a2-633191fc245e)


Keterangan : perintah cat digunakan untuk menampilkan isi file
3.	Imknput nama direktori, output tidak ada (membuat direktori baru), bila terjadi error maka tampilan error pada layar (standard error)
$ mkdir mydir
$ mkdir mydir **(Terdapat pesan error)**

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/2d4f553c-d83d-4e9d-99a9-6b153ce92080)


Keterangan : perintah mkdir digunakan untuk membuat directory yang bernama mydir kenapa kog eror yang kedua karena sudah ada directory 
Percobaan 2 : Pembelokan (redirection)
1.	Pembelokan standar output
 $ cat 1> myfile.txt
 Ini adalah teks yang saya simpan ke file myfile.txt


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/c833309e-f416-4ba7-ba78-4038c9529e73)


Keterangan : perintah ini akan menjalankan perintah cat, dan output dari perintah tersebut akan dituliskan ke dalam file baru yang disebut myfile.txt.

2.	Pembelokan standar input, yaitu input dibelokkan dari keyboard menjadi dari file
 $ cat 0< myfile.txt
 $ cat myfile.txt


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/a0cc74c5-f08e-445e-8126-5590c7090c67)

 
Keterangan : $ cat 0< myfile.txt: Perintah ini menggunakan operator < untuk mengalihkan standar input dari perintah cat menjadi berasal dari file myfile.txt (file descriptor 0 menunjukkan standar input).
$ cat myfile.txt: Perintah ini langsung menampilkan isi dari file myfile.txt di layar.
3.	Pembelokan standar error untuk disimpan di file
 $ mkdir mydir (Terdapat pesan error)
 $ mkdir mydir 2> myerror.txt
 $ cat myerror.txt

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/4f852259-1ec8-4c4b-998d-3d8a86b854de)


Keterangan : mkdir mydir: Perintah ini mencoba membuat direktori baru bernama mydir.
2>: Operator 2> digunakan untuk mengalihkan standar error dari perintah ke dalam file yang ditentukan. Angka 2 disini adalah file descriptor untuk standar error.
myerror.txt: Ini adalah nama file tempat pesan kesalahan akan dituliskan dalam file tersebut.

4.	Notasi 2>&1 : pembelokan standar error (2>) adalah identik dengan file descriptor 1.
 $ ls filebaru (Terdapat pesan error)
 $ ls filebaru 2> out.txt
 $ cat out.txt
 $ ls filebaru 2> out.txt 2>&
 $ cat out.txt

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/8ee804b2-59a8-4b65-a543-21a542b02efe)


Keterangan : $ ls filebaru (Terdapat pesan error): Ini adalah perintah untuk mengecek keberadaan file atau direktori filebaru. Jika file atau direktori tersebut tidak ada, akan muncul pesan error di terminal.
$ ls filebaru 2> out.txt: Perintah ini juga mengecek keberadaan file atau direktori filebaru, tetapi jika terjadi kesalahan, pesan kesalahan akan ditangkap dan ditulis ke dalam file out.txt. Operator 2> digunakan untuk mengalihkan standar error ke dalam file out.txt.
$ ls filebaru 2> out.txt 2>&: Perintah ini tampaknya salah karena tidak memiliki tujuan. Operator 2>& digunakan untuk mengalihkan standar error ke lokasi yang sama dengan standar output.
$ cat out.txt: Ini adalah perintah untuk menampilkan isi dari file out.txt di layar. 

5.	Notasi 1>&2 (atau >&2) : pembelokan standar output adalah sama dengan file descriptor 2 yaitu standar error
$ echo “mencoba menulis file” 1> baru
$ cat filebaru 2> baru 1>&
$ cat baru

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/b471ae47-6be6-4ac0-befb-7258728575fb)
Keterangan : Perintah ini Ini akan mengalihkan standar output dari cat filebaru ke file baru, dan juga mengalihkan standar error ke lokasi yang sama dengan standar output.


6.	Notasi >> (append)
$ echo “kata pertama” > surat
$ echo “kata kedua” >> surat
$ echo “kata ketiga” >> surat
$ cat surat
$ echo “kata keempat” > surat
$ cat surat

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/25f81b38-b6a3-4574-82a7-652918b77fa9)
Keterangan : perintah echo gi guankan untuk menulis kata pertama lalu disimpan ke file surat, kata kedua di dimpan ke file surat dan kata ke tiga lalu perintah cat digunakan untuk menampilkan isi file 


7.	Notasi here document (<<++ .... ++) digunakan sebagai pembatas input dari keyboard. Perhatikan bahwa tanda pembatas dapat digantikan dengan tanda apa saja, namun harus sama dan tanda penutup harus diberikan pada awal baris
$ cat <<++
Hallo, apa kabar?
Baik-baik saja?
Ok!
++
$ cat <<%%%
Hallo, apa kabar?
Baik-baik saja?
Ok!
%%%

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/6e2678a7-2fba-4974-8030-fa1ed28b9f66)


Keterangan :  cat <<++ Perintah ini mengaktifkan notasi here document dengan delimiter ++. Ini berarti bahwa semua teks yang dituliskan setelah perintah ini akan ditampilkan di layar hingga delimiter ++ seperti hallo, apa kabar sedangkan perintah cat <<%%% … %%% text yang berada dalam perintah tersebut akan ditampilkan di layar

8.	Notasi – (input keyboard) adalah representan input dari keyboard. Artinya menampilkan file 1, kemudian menampilkan input dari keyboard dan menampilkan file 2. Perhatikan bahwa notasi “-“ berarti menyelipkan input dari keyboard
$ cat myfile.txt – surat


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/8edc56cb-0f86-4351-b577-d88bdb4d9c55)


Keterangan : melihat isi dari myfile.txt dan surat 


Percobaan 3 : Pipa (pipeline)
1.	Operator pipa (|) digunakan untuk membuat eksekusi proses dengan melewati data langsung ke data lainnya.
$ who
$ who | sort
$ who | sort –r
$ who > tmp
$ sort tmp
$ rm tmp
$ ls –l /etc | more
$ ls –l /etc | sort | more
 


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/af19c06e-20c6-432e-b457-1a6119d4840a)
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/0906b1f5-60c3-4b33-9278-522fd8ecef77)

 
Keterangan : $ who: Menampilkan daftar pengguna yang sedang masuk ke sistem.
$ who | sort: Mengambil output dari perintah who, mengurutkannya, dan menampilkannya secara terurut.
$ who | sort –r: Kesalahan penulisan, seharusnya $ who | sort -r. Ini mengambil output dari perintah who, mengurutkannya secara terbalik (descending), dan menampilkannya.
$ who > tmp: Mengalihkan output dari perintah who ke dalam file sementara yang disebut tmp.
$ sort tmp: Mengurutkan isi dari file sementara tmp dan menampilkannya.
$ rm tmp: Menghapus file sementara tmp.
$ ls –l /etc | more: Menampilkan isi dari direktori /etc dengan format yang lebih rinci menggunakan ls -l, kemudian outputnya dialihkan ke perintah more untuk ditampilkan secara bertahap.
$ ls –l /etc | sort | more: Menampilkan isi dari direktori /etc dengan format yang lebih rinci menggunakan ls -l, mengurutkan outputnya, kemudian hasilnya dialihkan ke perintah more untuk ditampilkan secara bertahap.

2.	Untuk membelokkan standart output ke file, digunakan operator ">"
$ echo hello
$ echo hello > output
$ cat output

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/bb2ccdc8-c32e-4964-9bbb-9206b6a2d253)


Keterangan : perintah echo yaitu untuk memunculkan hello lalu  > untuk membeklokan standart output ke file outuput lalu perintah cat untuk melihat isi file output

3.	Untuk menambahkan output ke file digunakan operator ">>"
$ echo bye >> output
$ cat output

   
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/116df304-6184-42c8-8534-261ed017322c)


Keterangan : $ echo bye >> output digunakan untuk menambahkan text by ke file output
$ cat output perintah ini dikunakan untuk melihat isi file output

4.	Untuk membelokkan standart input digunakan operator "<"
$ cat < output

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/1c245840-0c41-43bf-b35b-8da7991147ab)


Keterangan : perintah tersebut digunakan untuk menampilkan isi file dari output

5.	Pembelokan standart input dan standart output dapat dikombinasikan tetapi tidak boleh menggunakan nama file yang sama sebagai standart input dan output.
$ cat < output > out
$ cat out
$ cat < output >> out
$ cat out
$ cat < output > output
$ cat output
$ cat < out >> out (Proses tidak berhenti)
[Ctrl-c]
$ cat out

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/53be2556-0b74-4963-9995-f2796c079908)


Keterangan : $ cat < output > out: Perintah ini mengambil isi dari file output dan menuliskannya ke dalam file out.
$ cat out: Perintah ini menampilkan isi dari file out.
$ cat < output >> out: Perintah ini mengambil lagi isi dari file output dan menambahkannya ke dalam file out. Dengan menggunakan operator >>, teks tambahan akan ditambahkan ke akhir file out. $ cat out: Perintah ini menampilkan isi dari file out. Sekarang, isi dari file out akan terdiri dari dua salinan dari isi file output. $ cat < output > output: Perintah ini mencoba mengambil isi dari file output dan menuliskannya kembali ke file output. Namun, karena kita mencoba menuliskan kembali ke file yang sama yang sedang dibaca, ini dapat menghasilkan perilaku yang tidak terduga dan dapat berpotensi mengakibatkan loop tak terbatas. $ cat output: Perintah ini menampilkan isi dari file output. Karena tidak ada operasi yang berhasil menuliskan ulang isi file output, isi file output tidak berubah. $ cat < out >> out: Perintah ini mencoba mengambil isi dari file out dan menambahkannya kembali ke file out. Dengan menggunakan operator >>, teks tambahan akan ditambahkan ke akhir file out. Namun, karena file out tidak berubah, proses ini akan masuk ke dalam loop tak terbatas. Dengan menekan Ctrl-c, proses tersebut dihentikan. $ cat out: Perintah ini menampilkan isi dari file out. Karena tidak ada tambahan yang ditambahkan ke file out, isi dari file out tetap sama seperti sebelumnya.

**Percobaan 4 : Filter**
1.	Pipa juga digunakan untuk mengkombinasikan utilitas sistem untuk membentuk fungsi yang lebih kompleks
 $ w –h | grep <user>
 $ grep <user> /etc/passwd
 $ ls /etc | wc
 $ ls /etc | wc –l
 $ cat > kelas1.txt
 Badu
 Zulkifli
 Yulizir
 Yudi
 Ade
 [Ctrl-d]
 $ cat > kelas2.txt
 Budi
 Gama
 Asep
 Muchlis
 [Ctrl-d]
 $ cat kelas1.txt kelas2.txt | sort
 $ cat kelas1.txt kelas2.txt > kelas.txt
 $ cat kelas.txt | sort | uniq


 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/1882006a-c68e-45d9-836f-89d1d2988979)
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/56d1d643-fed2-432f-a9ee-d09bcbdd30a1)



Keterangan : $ cat > kelas1.txt: Perintah ini membuka editor untuk membuat atau mengedit file bernama kelas1.txt

**LATIHAN**

1.	Lihat daftar secara lengkap pada direktori aktif, belokkan tampilan standard output ke file baru.

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/2fe4d9ce-619b-4079-90b2-b5747b494171)


Keterangan : Perintah ls untuk menampilkan daftar file,  perintah “>”  untuk mengarahkan output perintah ke file baru

2.	Lihat daftar secara lengkap pada direktori /etc/passwd, belokkan tampilan standard output ke file baru tanpa menghapus file baru sebelumnya.



![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/2c1a8c0d-2625-4479-a278-cc3f9427545c)



Keterangan : Perintah cat untuk menggabungkan dan menampilkan isi satu atau beberapa file secara urut di /etc/passwd.lalu  perintah “>>” untuk mengalihkan outpunya ke file baru.

3.	Urutkan file baru dengan cara membelokkan standard input.


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/de809e56-0acb-44eb-b1fe-d445477e27f2)



Keterangan :  perintah sort digunakan untuk mengurutkan masukannya, perintah “<” digunakan untuk sebagai input dari perintah sort ke file baru

4.	Urutkan file baru dengan cara membelokkan standard input dan standard output ke file baru.urut.

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/06fa58a1-7f3e-4e71-9dba-7823fb52b553)


Keterangan : perintah sort digunakan untuk mengurutkan masukannya berdasarkan urutan nomor, “< “ baru mengarahkan isi file baru sebagai input untuk perintah sort.”>” mengarahkan output dari perintah sort ke file baru dengan nama baru.urut .

5.	Buatlah direktori latihan 2 sebanyak 2 kali dan belokkan standard error ke file rmdirerror.txt.

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/35899497-0295-4707-bd23-9b38f6f2f642)


Keterangan : Menggunakan mkdir untuk membuat direktori Latihan2  sebnyak 2 kali, “2>”mengarhkan error ke file rmdirerror.txt

6.	Urutkan kalimat berikut :
Jakarta
Bandung
Surabaya
Padang
Palembang
Lampung
Dengan menggunakan notasi here document (<@@@ ...@@@) . [HINT](https://www.geeksforgeeks.org/how-to-use-here-document-in-bash-programming/)


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/ee3e493c-fc90-47b8-b095-6ce7e02f4377))


Keterangan : “<<@@@” digunakan untuk mengurutkan secara alfabet dan ditutup dengan @@@.

7.	Hitung jumlah baris, kata dan karakter dari file baru.urut dengan menggunakan filter dan tambahkan data tersebut ke file baru.


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/c321ffdf-f0b2-4784-90cd-5b0fe275c33a)

 

Keterangan : Untuk menghidung jumlah baris, kata dan karakter kita harus menggunakan perintah wc -l untuk menghitung jumlah baris, wc -w untuk menghitaung jumlah kata, dan wc -c untuk menghitung jumlah karakter kemudian menggunakan perintah pengelompokan “{}” untuk memindahkan jumlah baris, kata dan karakter, menggunakan perintah “>>” untuk memindahkan file tersebut ke file Bernama baru.

8.	Gunakan perintah di bawah ini dan perhatikan hasilnya.
$ cat > hello.txt
 dog cat
 cat duck
 dog chicken
 chicken duck
 chicken cat
 dog duck
 [Ctrl-d]
 $ cat hello.txt | sort | uniq
 $ cat hello.txt | grep “dog” | grep –v “cat”

 
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/b9e41904-e1c4-449c-a1ba-e3e6b4ce53a7)


Keterangan : Perintah “cat > hello.txt” digunakan untuk membuat atau menulis ke file hello.txt. perintah “ cat hello.txt | sort | uniq “akan mengeluarkan hasil teks yang sudah diurutkan dan tidak mengandung baris yang sama, Perintah “cat hello.txt | grep "dog" | grep -v "cat" “, akan mencari baris-baris dalam file hello.txt yang mengandung kata "dog" tetapi tidak mengandung kata "cat".


**Kesimpulan praktikum tersebut adalah kitab bisa tau tentang perintah pembelokan standart input dan standartoutput, dan tau tentang perintah dasar seperti grep, wc, sort, cut dan uniq**
