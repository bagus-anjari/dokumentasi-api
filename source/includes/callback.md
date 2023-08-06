# Callback bukaOlshop
## Apa itu Callback?
Dalam istilah API, Callback merupakan sebuah proses dimana sebuah service mengirim data ke service lainnya, baik itu diluar ruang lingkup aplikasi maupun di dalam internal aplikasi.

Jika dalam API, anda melakukan pemanggilan ke API bukaOlshop, lalu server bukaOlshop akan merespon dengan data yang anda minta. Sedangkan, Callback merupakan kebalikan dari hal tersebut.

Server bukaOlshop akan mengirimkan data ke URL endpoint yang sudah anda inputkan. Data-data tersebut akan dikirim jika ada event tertentu yang terjadi didalam aplikasi, yang kemungkinan anda butuhkan untuk memproses suatu event secara mandiri.

Contoh, jika member melakukan pemesanan didalam aplikasi, maka server bukaOlshop akan mengirimkan data ke URL anda mengenai data pesanan yang baru saja terjadi. Atau bisa juga member telah melakukan konfirmasi pembayaran, anda dapat mendapatkan data konfirmasi tersebut secara langsung dengan adanya callback.

Lihat skema dibawah ini:

![Callback API bukaolshop](/images/callback.png "Callback API bukaolshop")

Dengan adanya callback, anda dapat mengetahui jika ada pesanan baru yang masuk dan memutuskan sendiri, apa yang anda ingin lakukan dengan data tersebut. Contohnya:

* Melakukan pemesanan produk digital pada layanan lain, jika status transaksi telah lunas.

* Melakukan pengecekan rekening agar pembayaran dapat dikonfirmasi otomatis.

* Menyimpan data transaksi di database pribadi untuk keperluan pendataan.

## Alur kerja Callback pada bukaOlshop

Berikut ini akan dijelaskan alur teknis cara kerja callback pada aplikasi bukaOlshop.

**Callback transaksi baru**
Pada bagian ini, server bukaOlshop akan mengirim data jika ada transaksi baru yang telah dibuat oleh member anda. Data tersebut akan dikirim ke URL yang telah anda inputkan di aplikasi bukaOlshop.

Disamping ini contoh data **transaksi baru** yang dikirimkan oleh server bukaOlshop ke URL anda:

* ```tipe_callback``` dapat berisi dua nilai, yaitu ```transaksi_baru``` , dan ```perubahan_status_transaksi```. Disini anda bisa cek apakah callback merupakan *transaksi baru atau* perubahan *status transaksi*. Namun, untuk meminimalisir kesalahan, ada baiknya anda memasukkan dua URL yang berbeda antara *transaksi baru* dan *perubahan status transaksi*.
* ```secret_key_callback``` merupakan sebuah kode rahasia yang bisa anda dapatkan pada aplikasi android bukaOlshop. Kode ini akan dikirimkan tiap server mengirim data ke URL anda. Anda harus membandingkan kode yang dikirim server, dengan kode yang anda terima di aplikasi bukaOlshop, jika kode nya sama, artinya callback tersebut dikirim oleh server bukaOlshop, dan jika berbeda, artinya kode tersebut telah berubah atau ada pihak lain yang mencoba mengirimkan data palsu ke URL anda.
* ```nomor_pembayaran``` merupakan id pada transaksi yang telah dilakukan member. Anda bisa mengecek data lengkapnya API bukaOlshop di endpoint ```detail_transaksi```.
* ```status_transaksi``` akan menampilkan data status pembayaran/pengiriman pada transaksi. Dengan data ini, anda bisa cek apakah ingin meneruskan proses atau tidak. Contoh jika status transaksi telah lunas, maka anda bisa melanjutkan proses untuk pembelian produk digital pada layanan yang lain.
* ```tipe_transaksi``` merupakan tipe untuk mengecek apakah transaksi ini dapat anda langsung proses secara otomatis atau tidak. ```tipe_transaksi``` ini memiliki 7 nilai yaitu:

<code>COD MANUAL</code> , <code>COD JNT</code> , <code>DELIVERY COD</code> , <code>DELIVERY</code> , <code>PRODUK DIGITAL</code> , <code>EKSPEDISI</code> <code>MULTI_PENGIRIMAN</code>


Berikut ini merupakan Sequence Diagram yang bisa anda gunakan untuk dalam memproses data callback:
![Sequence Diagram Transaksi baru](/images/TransaksiBaru.svg "Sequence Diagram Transaksi baru")

Misal anda ingin mengotomatisasi proses pembelian PPOB, anda bisa mendapatkan data yang di inputkan member pada field "catatan". Disarankan untuk tidak menggunakan fitur varian pada produk digital agar lebih mudah mengetahui informasi produk melalui id_barang.

<aside class="notice">
Perlu diingat, anda perlu memvalidasi terlebih dulu data catatan apakah sudah sesuai atau belum. Contoh, jika anda ingin mengotomatisasi pembelian pulsa, anda perlu mengecek apakah data pada catatan sudah benar merupakan nomor Hp atau bukan.
</aside>
