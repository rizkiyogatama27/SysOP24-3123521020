PERBEDAAN RISC DAN CISC
Arsitektur komputer dengan kumpulan perintah yang sederhana (Reduced Instruction Set
Computer = RISC)
Arsitektur komputer dengan kumpulan perintah yang rumit (Complex Instruction Set
Computer = CISC)

**Pengertian**
CISC adalah singkatan dari Complex Intruction Set Computer dimana prosesor tersebut
memiliki set instruksi yang kompleks dan lengkap. Sedangkan RISC adalah singkatan
dari Reduced Instruction Set Computer yang artinya prosesor tersebut memiliki set
instruksi program yang lebih sedikit





**Fork : Parent - Child Process
Buat tulisan tentang konsep fork dan implementasinya dengan menggunakan bahasa pemrograman C! (minimal 2 paragraf disertai dengan gambar)
Akses dan clonning repo : https://github.com/ferryastika/operatingsystem.git
Deskripsikan dan visualisasikan pohon proses hasil eksekusi dari kode program fork01.c, fork02.c, fork03.c**

![Cuplikan layar 2024-04-22 111345](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/84b997bb-fe43-429f-a8f4-bdaa84dcbfc7)
![Cuplikan layar 2024-04-22 192205](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/8f2b018d-f164-48e5-86aa-4fb87e03551e)

**Sebelum menjalankan fork , lakukan instalasi compiler dengan cara mengetikkan apt install gcc g++.
perintah tersebut untuk menginstall compiler bahasa C dan bahasa C++**

**gcc adalah compiler untuk bahasa C
g++ adalah compiler untuk bahasa C++**

![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/c827f1fc-78b4-402b-9ea2-21c3126efbc3)
karena saya sudah menginstall compiler nya maka tampilan dari screenshot tersebut menampilkan gcc dan g++ sudah terinstall.

untuk menjalankan fork01.cpp , ketikkan perintah g++ fork01.cpp -o fork01.exe
![Cuplikan layar 2024-04-22 200852](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/0ba023d6-0755-446e-957f-49f8c15b41cf)
**perintah tersebut digunakan untuk mengkompilasi program C++ yang disebut dengan fork01.cpp menggunakan compiler g++ dan menghasilkan output fork01.exe**
**kemudian ketikan nano fork01.cpp untuk menampilkan program**
![Cuplikan layar 2024-04-22 201124](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/a0948e2d-75bd-43bc-ba57-b0c9515845b3)
**kemudian ketikkan ./fork01.exe untuk menjalankannya**
![Cuplikan layar 2024-04-22 200953](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/1287ac4f-5609-4748-8e72-60e16f757762)

Analisa : Output program ini menampilkan PID, PPID, dan UID. Setiap kali program mencetak informasi, program akan berhenti selama 3 detik sebelum mencetak informasi lagi. Program ini melakukaan perulangan sebanyak 3 kali

**Kemudian untuk menjalankan fork02.cpp dan juga fork03.cpp caranya sama seperti menjalankan fork01.cpp**



**fork02**
**kemudian ketikkan ./fork02.exe untuk menjalankannya**
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/51e61fc6-38be-408d-923e-a08205abb0af)
**kemudian ketikan nano fork02.cpp untuk menampilkan program**
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/14d033d1-8ac5-47e0-b6e3-35b7eefd32c9)
Analisa:
Output dari program tersebut adalah melakukan proses forking secara berulang sebanyak 5 kali, yang menghasilakn proses baru dengan pesan yang mencatat PID masing-masing.


**fork03**
**kemudian ketikkan ./fork03.exe untuk menjalankannya**
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/f5e4b584-757a-46be-871d-086d7899a49d)
**kemudian ketikan nano fork03.cpp untuk menampilkan program**
![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/12ce714e-b658-45a6-bc4b-b3ff0ff3728f)

Analisa:
Output dari program tersebut adalah menampilkan PID mereka sendiri dan nilai variabel x dalam loop tak terbatas. Program menggunakan system call fork() untuk membuat proses saat ini, dan menciptakan child process.




 
**Fork : Parent - Child Process
Buat tulisan tentang konsep fork dan implementasinya dengan menggunakan bahasa pemrograman C! (minimal 2 paragraf disertai dengan gambar)
Akses dan clonning repo : https://github.com/ferryastika/operatingsystem.git
Deskripsikan dan visualisasikan pohon proses hasil eksekusi dari kode program fork01.c, fork02.c, fork03.c**


![Cuplikan layar 2024-04-22 111345](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/84b997bb-fe43-429f-a8f4-bdaa84dcbfc7)
![Cuplikan layar 2024-04-22 192205](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/8f2b018d-f164-48e5-86aa-4fb87e03551e)



**Sebelum menjalankan fork , lakukan instalasi compiler dengan cara mengetikkan apt install gcc g++.
perintah tersebut untuk menginstall compiler bahasa C dan bahasa C++**

**gcc adalah compiler untuk bahasa C
g++ adalah compiler untuk bahasa C++**


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/c827f1fc-78b4-402b-9ea2-21c3126efbc3)


karena saya sudah menginstall compiler nya maka tampilan dari screenshot tersebut menampilkan gcc dan g++ sudah terinstall.

untuk menjalankan fork01.cpp , ketikkan perintah g++ fork01.cpp -o fork01.exe


![Cuplikan layar 2024-04-22 200852](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/0ba023d6-0755-446e-957f-49f8c15b41cf)


**perintah tersebut digunakan untuk mengkompilasi program C++ yang disebut dengan fork01.cpp menggunakan compiler g++ dan menghasilkan output fork01.exe**
**kemudian ketikan nano fork01.cpp untuk menampilkan program**


![Cuplikan layar 2024-04-22 201124](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/a0948e2d-75bd-43bc-ba57-b0c9515845b3)


**kemudian ketikkan ./fork01.exe untuk menjalankannya**


![Cuplikan layar 2024-04-22 200953](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/1287ac4f-5609-4748-8e72-60e16f757762)


Analisa : Output program ini menampilkan PID, PPID, dan UID. Setiap kali program mencetak informasi, program akan berhenti selama 3 detik sebelum mencetak informasi lagi. Program ini melakukaan perulangan sebanyak 3 kali

**Kemudian untuk menjalankan fork02.cpp dan juga fork03.cpp caranya sama seperti menjalankan fork01.cpp**



**fork02**
**kemudian ketikkan ./fork02.exe untuk menjalankannya**


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/51e61fc6-38be-408d-923e-a08205abb0af)


**kemudian ketikan nano fork02.cpp untuk menampilkan program**


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/14d033d1-8ac5-47e0-b6e3-35b7eefd32c9)


Analisa:
Output dari program tersebut adalah melakukan proses forking secara berulang sebanyak 5 kali, yang menghasilakn proses baru dengan pesan yang mencatat PID masing-masing.


**fork03**
**kemudian ketikkan ./fork03.exe untuk menjalankannya**


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/f5e4b584-757a-46be-871d-086d7899a49d)


**kemudian ketikan nano fork03.cpp untuk menampilkan program**


![image](https://github.com/rizkiyogatama27/SysOP24-3123521020/assets/160556478/12ce714e-b658-45a6-bc4b-b3ff0ff3728f)


Analisa:
Output dari program tersebut adalah menampilkan PID mereka sendiri dan nilai variabel x dalam loop tak terbatas. Program menggunakan system call fork() untuk membuat proses saat ini, dan menciptakan child process.












































