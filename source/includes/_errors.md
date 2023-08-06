# Errors Code

<aside class="notice">
Lihat penjelasan mengenai HTTP Request di <a href="https://en.wikipedia.org/wiki/List_of_HTTP_status_codes">Wikipedia</a>
</aside>

API bukaOlshop menggunakan kode respons HTTP standart, berikut ini beberapa respon yang mungkin akan anda terima:


Error Code | Meaning
---------- | -------
400 |	Bad Request -- Data yang anda input salah, pastikan anda menginput data yang wajib di isi dengan benar.
401	| Unauthorized -- API key anda salah, atau Authorization header tidak dikirim dengan benar.
403	| Forbidden -- Autentikasi berhasil, namun anda tidak memiliki hak untuk melihat data.
404	| Not Found -- Data yang anda cari tidak ditemukan.
405	| Method Not Allowed -- Anda mencoba mengakses endpoint dengan method yang salah.
429	| Too Many Requests -- Anda melakukan terlalu banyak request saat bersamaan, atau kuota request perhari anda telah habis.
500	| Internal Server Error -- sedang terjadi masalah pada server, silahkan coba lagi nanti.
503	| Service Unavailable -- Server bukaOlshop sedang offline atau maintenance, silahkan coba lagi nanti.
