Perbedaan Serial, Parallel, Concurent dan Concurent Parallel
Parallek
Concurent
Concurent Parallel
gambar judul
["C:\Users\rizki\Downloads\331189923-9106f52c-9d9b-4a64-8ddd-2fae76becb24.jpg"](https://private-user-images.githubusercontent.com/160557634/331189923-9106f52c-9d9b-4a64-8ddd-2fae76becb24.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTU5MzU3OTksIm5iZiI6MTcxNTkzNTQ5OSwicGF0aCI6Ii8xNjA1NTc2MzQvMzMxMTg5OTIzLTkxMDZmNTJjLTlkOWItNGE2NC04ZGRkLTJmYWU3NmJlY2IyNC5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNTE3JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDUxN1QwODQ0NTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01MmFjMjE0NGZjMDMxYjgwNjcyYTM0MDY4NDJhMjZhYjdkZDFmMWNlMGU5YWFkNmY3OGRmYWE1M2ZlZjBlNjM1JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.LRT9568BAvzs3-pTUNlBo_X67Zl3v_oM7ZGzmAvztAI)

Parallel
Parallel adalah beberapa proses / proses yang dilakukan secara bersamaan Seperti contoh pada gambar diatas dimana core1 menjalankan task 1 dan core 2 menjalankan task 2 secara bersamaan.

contoh : image


Pada gambar ini Proses A dan Proses B menjalankan proses 1, proses 2, proses 3 secara bersamaan / dalam satu waktu Ksimpulan : Proses akan lebih efisien dengan membagi kerja sehingga dapat mempercepat waktu eksekusi keseluruhan tugas.

Concurent
Concurrent adalah sebuah proses yang dijalankan secara sekaligus secara bergantian , bukan seacara bersamaan tapi secara sekaligus. pada gambar {diatas} Core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalu core 1 menjalankan task 2.2 core 2 menjalankan task 1.2 dikarenakan proses task 1.2 belum selesai maka core 1 menjslankan task 2.3 lalu core 2 setelah proses dari task 1.2 selesai maka menjalankan proses task 1.3 lalu setelah core 1 selesai makan akan menjalankan proses setelahnya.

contoh : image

dari gambar di atas Proses A menjalankan task 1 lalu ketika task 1 selesai makan akan menjalankan proses lainya

Paraller dan Concurent
Concurrent and Parallel dijalankan secara bersamaan dan bergantian pada dua core. seperti contoh pada gambar judul di atas core 1 menjalankan task 1.1 core 2 menjalankan task 2.1 lalau setelah task 1.1 proses selesai lanjut mrnjalankan task 2.2 dan dan 2.3 secara urut lalu pada core 2 selewsai menjalankan task 2.1 makan akan menjalankan task 1.2 dikarenakan task 1.1 sudah terisi oleh task 2.2 maka core 2 menjalankan task 1.2 dan 1.3 dan seterusnya
Kesimpulan : penggunaan CPU yang lebih optimal utuk menjaga responsivitas sistem.
