# Rate Limit
bukaOlshop menerapkan rate limit pada API untuk mencegah penyalahgunaan API yang dapat terjadi. Rate limit merupakan batasan anda melakukan request ke API bukaOlshop setelah anda melakukannya dalam jumlah tertentu. Rate limit ini akan di reset setiap hari, jadi jika anda telah mencapai limit yang telah ditentukan, anda dapat melakukan request pada hari berikutnya.

Jika anda telah mencapat limit yang telah ditentukan, maka server akan merespon dengan kode **429 - Too Many Requests**. Sebaiknya anda melakukan pengecekan pada server anda apakah code yang di terima merupakan kode **429** atau tidak.

Gambar dibawah ini merupakan daftar rate limit yang diterapkan pada API bukaOlshop:

![Rate Limit API bukaOlshop](/images/jumlahrequest.png "Rate Limit API bukaOlshop")
