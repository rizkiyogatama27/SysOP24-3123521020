4.1 Berikan tiga contoh pemrograman di mana multithreading memberikan kinerja yang lebih baik daripada solusi single-threaded.

Jawaban:

a. Server web yang melayani setiap permintaan dalam thread terpisah.
b. Aplikasi paralel seperti perkalian matriks di mana bagian-bagian matriks yang berbeda dapat dikerjakan secara paralel.
c. Program GUI interaktif seperti debugger di mana satu thread digunakan untuk memantau input pengguna, thread lain mewakili aplikasi yang berjalan, 
   dan thread ketiga memantau kinerja.

4.2 Apa dua perbedaan antara user-level threads dan kernel-level threads? Dalam kondisi apa salah satu jenis lebih baik daripada yang lain?

Jawaban:

a. User-level threads tidak dikenal oleh kernel, sedangkan kernel mengenal kernel threads.
b. Pada sistem yang menggunakan pemetaan M:1 atau M:N, user threads dijadwalkan oleh perpustakaan thread dan kernel menjadwalkan kernel threads.
c. Kernel threads tidak perlu dikaitkan dengan suatu proses sedangkan setiap user thread milik suatu proses. 
   Kernel threads umumnya lebih mahal untuk dipelihara daripada user threads karena harus diwakili dengan struktur data kernel.

4.3 Jelaskan tindakan yang diambil oleh kernel untuk melakukan context-switch antara kernel-level threads.

Jawaban:

Pergantian konteks antara kernel threads biasanya memerlukan penyimpanan nilai dari register CPU dari thread yang sedang diganti dan pemulihan 
register CPU dari thread baru yang akan dijadwalkan.

4.4 Sumber daya apa yang digunakan saat thread dibuat? Bagaimana perbedaannya dengan yang digunakan saat proses dibuat?

Jawaban:

Karena thread lebih kecil daripada proses, pembuatan thread biasanya menggunakan sumber daya yang lebih sedikit dibandingkan pembuatan proses. 
Membuat proses memerlukan alokasi blok kontrol proses (PCB), yaitu struktur data yang cukup besar. PCB mencakup peta memori, daftar file terbuka, dan variabel lingkungan. Mengalokasikan dan mengelola peta memori biasanya merupakan aktivitas yang paling memakan waktu. Membuat thread, baik user thread maupun kernel thread, melibatkan alokasi struktur data kecil untuk menyimpan set register, stack, dan prioritas.

4.5 Misalkan sebuah sistem operasi memetakan user-level threads ke kernel menggunakan model many-to-many dan pemetaan dilakukan melalui LWPs. 
Selain itu, sistem memungkinkan pengembang membuat real-time threads untuk digunakan dalam sistem real-time. Apakah perlu mengikat real-time thread ke LWP? Jelaskan.

Jawaban:

Ya. Waktu sangat penting untuk aplikasi real-time. Jika sebuah thread ditandai sebagai real-time tetapi tidak terikat ke LWP, 
thread tersebut mungkin harus menunggu untuk dihubungkan ke LWP sebelum berjalan. Pertimbangkan jika sebuah real-time thread sedang berjalan (terhubung ke LWP) dan kemudian diblokir (misalnya harus melakukan I/O, telah digantikan oleh thread real-time dengan prioritas lebih tinggi, atau sedang menunggu kunci eksklusi bersama). Saat real-time thread diblokir, LWP yang terhubung dengannya telah dialokasikan ke thread lain. Ketika real-time thread dijadwalkan untuk berjalan lagi, ia harus menunggu untuk dihubungkan ke LWP. Dengan mengikat LWP ke real-time thread, Anda memastikan bahwa thread tersebut dapat berjalan dengan penundaan minimal setelah dijadwalkan.
