# OPEN API
Dokumentasi Open API.

# Main Endpoint


Berikut ini merupakan URL utama endpoint pada Open API bukaOlshop:

`https://openapi.bukaolshop.net/v1`

Anda harus menambahkan path tambahan sesuai bagian yang ingin anda request. Contoh: jika anda ingin mendapatkan list produk, maka url akan menjadi:

`https://openapi.bukaolshop.net/v1/`<b>app/produk</b>

Walaupun Open API ini dapat diletakkan dimanapun di HTML, kami tetap mewajibkan untuk menyertakan `token` didalam tiap request untuk membedakan tiap aplikasi.

Walaupun tidak ada resiko keamanan yang berarti, kami **tidak** menyarankan anda menyebarkan link endpoint yang terdapat `token` olshop anda ke tempat publik seperti di dalam grup.

<aside class="notice">
Semua request ke endpoint Open API ini dilakukan melalui method <code>GET</code>.
</aside>

> Cara menambahkan token ke URL endpoint

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET", "https://openapi.bukaolshop.net/v1/app/produk?token=xxxxxxxx", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      //this.readyState == 4 artinya request telah selesai
      //Hasil json berada di this.responseText
      console.log(this.responseText);        
    }  
};  
xmlHttpRequest.send();

```

> Contoh URL jika ada parameter request tambahan, misal ke page selanjutnya

```javascript
https://openapi.bukaolshop.net/v1/app/produk?token=xxxxxxxx&page=2
```

<aside class="notice">
<code>Token</code> dapat didapatkan di aplikasi bukaOlshop versi terbaru, dibagian Tab <code>TOKO</code>, klik <code>API & Callback</code>, pindah kehalaman <code>API</code>, disitu anda akan mendapatkan token pada bagian Open API.
</aside>


#GET DATA APLIKASI
##***GET*** Daftar Produk

> Contoh Request dengan javascript

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET", "https://openapi.bukaolshop.net/v1/app/produk?token=xxxxxxxx&page=1", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      console.log(this.responseText);        
    }  
};  
xmlHttpRequest.send();
```

> Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "page": 1,
  "data": [
    {
      "id_produk": "2046567",
      "id_kategori": "2",
      "nama_produk": "pulsa telkom 20rb",
      "harga_produk": 21000,
      "harga_produk_asli": 0,
      "deskripsi_singkat": "",
      "deskripsi_panjang": "pulsa telkom",
      "kondisi_produk": "Ready Stock",
      "stok": 600,
      "berat": 0,
      "tanggal": "2023-07-22 00:01:38",
      "ukuran": null,
      "warna": null,
      "gambar_utama": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/112299/441903822j.jpg",
      "list_gambar": [
        "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/112299/441903822j.jpg"
      ],
      "url_produk": "https://olshopgue.bukaolshop.site/produk/omni-2046567"
    },
    {
      "id_produk": "277074",
      "id_kategori": "2",
      "nama_produk": "Baju baru",
      "harga_produk": 40000,
      "harga_produk_asli": 0,
      "deskripsi_singkat": "desk singkat",
      "deskripsi_panjang": "desk panjang",
      "kondisi_produk": "Baru",
      "stok": 23,
      "berat": 100,
      "tanggal": "2020-11-16 01:26:27",
      "ukuran": ["L","M","XL"],
      "warna": ["Ungu","Biru","Hitam"],
      "gambar_utama": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/440277426c.jpg",
      "list_gambar": [
        "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/440277426c.jpg",
        "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/512421523d.jpg"
      ],
      "url_produk": "https://olshopgue.bukaolshop.site/produk/bag-277074"
    }
  ]
}
```

**Summary**: Daftar Produk

**Description**: Endpoint ini berfungsi untuk mendapatkan daftar produk yang ada di aplikasi bukaOlshop anda. Method yang digunakan pada endpoin ini yaitu GET.

Tiap request akan mengirimkan sebanyak 10 data produk. Jika ingin mendapatkan data di halaman selanjutnya, tambahkan parameter `page` kedalam parameter url endpoint. Parameter `page` diisi dengan format angka, misal 2, 3, 4 dst.

### HTTP Request

`GET /app/produk`

### Query Parameters

Parameter | Wajib | Deskripsi | Tipe
--------- | ------- | ----------- | -----------
token | Ya | Token dapat didapatkan di aplikasi bukaOlshop. | String
page | Tidak |Posisi daftar halaman produk. | Integer



##***GET*** Daftar Kategori

> Contoh Request dengan javascript

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET", "https://openapi.bukaolshop.net/v1/app/kategori?token=xxxxxxxx", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      console.log(this.responseText);        
    }  
};  
xmlHttpRequest.send();
```
> Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "data": [
    {
      "id_kategori": "2",
      "nama_kategori": "Sepatu",
      "gambar_kategori": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/666180ka.jpg",
      "url_kategori": "https://olshopgue.bukaolshop.site/kategori/sepatu-2",
      "tipe_kategori": "utama",
      "sub_kategori": [
        {
          "id_kategori": "5387",
          "nama_kategori": "Celana",
          "gambar_kategori": "https://storage1.bukaolshop.com/images/1/kategori/902346.jpg",
          "url_kategori": "https://olshopgue.bukaolshop.site/kategori/celana-5387",
          "tipe_kategori": "sub"
        },
        {
          "id_kategori": "23533",
          "nama_kategori": "hai",
          "gambar_kategori": "https://storage1.bukaolshop.com/images/1/kategori/902346.jpg",
          "url_kategori": "https://olshopgue.bukaolshop.site/kategori/hai-23533",
          "tipe_kategori": "sub"
        }
      ]
    },
    {
      "id_kategori": "55421",
      "nama_kategori": "Pulsa Cek",
      "gambar_kategori": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/528828ka.jpg",
      "url_kategori": "https://olshopgue.bukaolshop.site/kategori/pulsa-cek-55421",
      "tipe_kategori": "utama",
      "sub_kategori": []
    }  
  ]
}
```
**Summary**: Daftar Kategori

**Description**: Endpoint ini berfungsi untuk mendapatkan daftar kategori yang ada di aplikasi bukaOlshop anda. Method yang digunakan pada endpoin ini yaitu GET. Semua data kategori akan dikirimkan tiap request.


### HTTP Request

`GET /app/kategori`

### Query Parameters

Parameter | Wajib | Deskripsi | Tipe
--------- | ------- | ----------- | -----------
token | Ya | Token dapat didapatkan di aplikasi bukaOlshop. | String
struktur | Tidak | Jika ingin tidak ada level antara kategori dan sub kategori, isi bagian ini. | Enum `flat`




##***GET*** Daftar Kostum Halaman

> Contoh Request dengan javascript

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET", "https://openapi.bukaolshop.net/v1/app/kostumpage?token=xxxxxxxx", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      console.log(this.responseText);        
    }  
};  
xmlHttpRequest.send();
```
> Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "data": [
    {
      "nama_page": "Nama Halaman",
      "icon_page": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/485323co.png",
      "url_kostum_page": "https://olshopgue.bukaolshop.site/digital/10576"
    },
    {
      "nama_page": "Test Halaman",
      "icon_page": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/698320co.png",
      "url_kostum_page": "https://olshopgue.bukaolshop.site/digital/24672"
    }
  ]
}
```
**Summary**: Daftar Kostum Halaman

**Description**: Endpoint ini berfungsi untuk mendapatkan daftar kostum halaman yang ada di aplikasi bukaOlshop anda. Method yang digunakan pada endpoin ini yaitu GET. Semua data kostum halaman akan dikirimkan tiap request.


### HTTP Request

`GET /app/kostumpage`

### Query Parameters

Parameter | Wajib | Deskripsi | Tipe
--------- | ------- | ----------- | -----------
token | Ya | Token dapat didapatkan di aplikasi bukaOlshop. | String



##***GET*** Daftar Slide

> Contoh Request dengan javascript

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET", "https://openapi.bukaolshop.net/v1/app/slide?token=xxxxxxxx", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      console.log(this.responseText);        
    }  
};  
xmlHttpRequest.send();
```
> Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "data": [
    {
      "url_gambar_slide": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/677893sl.jpg",
      "url_tujuan": "https://olshopgue.bukaolshop.site/digital/3"
    },
    {
      "url_gambar_slide": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/897133sl.jpg",
      "url_tujuan": null
    }    
  ]
}
```
**Summary**: Daftar Gambar Slide

**Description**: Endpoint ini berfungsi untuk mendapatkan daftar gambar slide yang ada di aplikasi bukaOlshop anda. Method yang digunakan pada endpoin ini yaitu GET. Semua data gambar slide akan dikirimkan tiap request.


### HTTP Request

`GET /app/slide`

### Query Parameters

Parameter | Wajib | Deskripsi | Tipe
--------- | ------- | ----------- | -----------
token | Ya | Token dapat didapatkan di aplikasi bukaOlshop. | String







#GET DATA USER
##***GET*** Informasi User

> Contoh Request dengan javascript

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET",
"https://openapi.bukaolshop.net/v1/user/info?token=xxxxxxxx&token_user={{token_user}}&id_user={{id_user}}", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      // hasil di this.responseText
    }  
};  
xmlHttpRequest.send();
```


**Summary**: Mendapatkan Informasi User

**Description**: Endpoint ini berfungsi untuk mendapatkan data tentang user yang sedang login di aplikasi. Data yang didapatkan berupa nama user, email user, catatan saldo, jumlah saldo, jumlah poin dan lain-lain.

> Contoh Respon

```json
{
	"code": 200,
	"status": "ok",
	"data": {
		"nama_user": "User name",
		"email_user": "user@gmail.com",
		"tanggal_lahir": "1998-11-08",
		"nomor_telepon": "62821288454822",
		"foto_profil": "link gambar",
		"tanggal_daftar": "2020-11-23",
		"status_akun": "aktif",
		"status_email": "belum_verifikasi",
		"nama_membership": "Basic reseller",
		"icon_membership": null,
		"block_akses_membership": "tidak_ada",
		"kode_referral": "MYREF",
		"status_nomor_hp": "belum_verifikasi",
		"jumlah_saldo": "50000",
		"jumlah_poin": "500"		
	}
}
```

<aside class="notice">
Untuk mengakses endpoint ini, apk olshop harus memiliki versi <b>patch 62.5</b>.
</aside>


<aside class="notice">
Tiap request harus menyertakan parameter <code>token_user</code> dengan nilai <code>{{token_user}}</code><br>dan <code>id_user</code> dengan nilai <code>{{id_user}}</code>
</aside>

> Contoh mengirim token_user dan id_user ke link luar

```javascript

window.location.replace("http://link_luar.com/cekuser.php?token_user={{token_user}}&id_user={{id_user}}");

```


### HTTP Request

`GET /user/info`

### Query Parameters

Parameter | Wajib | Deskripsi | Tipe
--------- | ------- | ----------- | -----------
token | Ya | Token dapat didapatkan di aplikasi bukaOlshop. | String
token_user | Ya | Isi dengan `{{token_user}}` | String
id_user | Ya | Isi dengan `{{id_user}}` | String

<aside class="success">
Shortcode <code>{{token_user}}</code> dan <code>{{id_user}}</code> akan otomatis di replace dengan nilai asil nya saat diakses di apk olshop. Shortcode ini baru akan berkerja jika anda meletakkan html langsung didalam aplikasi bukaOlshop, bukan melalui link yang mengarah ke website luar.
</aside>





<aside class="notice">
Jika anda ingin mengakses data user melalui link pihak ketiga, atau menggunakan script di server sendiri, maka bisa melalui trik redirect link, contohnya bisa dilihat disamping.
</aside>


##***GET*** Catatan Saldo/Poin

> Contoh Request dengan javascript

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET",
"https://openapi.bukaolshop.net/v1/user/catatan?token=xxxxxxxx&token_user={{token_user}}&id_user={{id_user}}&tipe=saldo", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      // hasil di this.responseText
    }  
};  
xmlHttpRequest.send();
```


**Summary**: Mendapatkan Data Catatan Saldo atau Poin

**Description**: Endpoint ini berfungsi untuk mendapatkan daftar catatan saldo/poin milik member. Tiap request akan mengirimkan sebanyak 10 data catatan. Jika ingin mendapatkan data di halaman selanjutnya, tambahkan parameter `page` kedalam parameter url endpoint. Parameter `page` diisi dengan format angka, misal 2, 3, 4 dst.

Secara default, data yang akan ditampilkan yaitu data saldo, jika ingin mendapatkan data poin,<br>tambahakan parameter ```tipe=poin``` pada request

> Contoh Respon tipe saldo

```json
{
  "code": 200,
  "status": "ok",
  "page": 1,
  "data": [
    {
      "informasi_catatan": "Pengembalian saldo dari transaksi 875169634 yang otomatis dibatalkan.",
      "jumlah_dana": "3423",            
      "tipe_jumlah": "tambah",
      "tipe_mutasi": "transaksi",
      "tanggal": "2023-07-27 15:17:11",
      "saldo_terakhir": "12114"
    },
    {
      "informasi_catatan": "Member melakukan transaksi menggunakan saldo (#875169634)",
      "jumlah_dana": "3423",    
      "tipe_jumlah": "kurang",
      "tipe_mutasi": "transaksi",      
      "tanggal": "2023-07-27 15:17:11",
      "saldo_terakhir": "8691"
    }  
  ]
}
```

> Contoh Respon tipe poin

```json
{
  "code": 200,
  "status": "ok",
  "page": 1,
  "data": [
    {
      "kategori_poin": "Transaksi Selesai, Komisi untuk upline dari fitur referral",
      "tipe_jumlah": "tambah",
      "jumlah_poin": "8",
      "tanggal_poin": "2023-03-28 03:57:01",
      "total_poin_terakhir": "123",
      "link_transaksi": "https://olshopgue.bukaolshop.site/akun/?page=transaksi&nomor=96116232910"
    },
    {
      "kategori_poin": "Transaksi Selesai, Komisi untuk upline dari fitur referral",
      "tipe_jumlah": "tambah",
      "jumlah_poin": "62",
      "tanggal_poin": "2023-03-28 03:48:02",
      "total_poin_terakhir": "115",
      "link_transaksi": "https://olshopgue.bukaolshop.site/akun/?page=transaksi&nomor=78373232879"
    }  
  ]
}
```

### HTTP Request

`GET /user/catatan`

### Query Parameters

Parameter | Wajib | Deskripsi | Tipe
--------- | ------- | ----------- | -----------
token | Ya | Token dapat didapatkan di aplikasi bukaOlshop. | String
token_user | Ya | Isi dengan `{{token_user}}` | String
id_user | Ya | Isi dengan `{{id_user}}` | String
page | Tidak |Posisi daftar halaman produk. | Integer
tipe | Tidak | Tipe catatan | Enum (```saldo``` atau ```poin```)




##***GET*** Daftar Transaksi

> Contoh Request dengan javascript

```javascript
var xmlHttpRequest = new XMLHttpRequest();  
xmlHttpRequest.open("GET",
"https://openapi.bukaolshop.net/v1/user/transaksi?token=xxxxxxxx&token_user={{token_user}}&id_user={{id_user}}", true);  
xmlHttpRequest.onreadystatechange = function () {  
    if (this.readyState == 4 && this.status == 200) {
      // hasil di this.responseText
    }  
};  
xmlHttpRequest.send();
```


**Summary**: Mendapatkan Daftar Transaksi User

**Description**: Endpoint ini berfungsi untuk mendapatkan daftar transaksi milik member. Tiap request akan mengirimkan sebanyak 10 data transaksi. Jika ingin mendapatkan data di halaman selanjutnya, tambahkan parameter `page` kedalam parameter url endpoint. Parameter `page` diisi dengan format angka, misal 2, 3, 4 dst.

> Contoh Respon

```json
{
	"code": 200,
	"status": "ok",
	"page": 1,
	"data": [
		{
			"nomor_pembayaran": "875169634",
			"status_bayar": "di batalkan",
			"status_pengiriman": "di batalkan",
			"tanggal": "2023-07-27 15:17:11",
			"nama_barang": "Testing produk",
			"url_gambar_produk": "https:\/\/bukaolshop.s3-id-jkt-1.kilatstorage.id\/1\/67912029.jpg",
			"link_transaksi": "https:\/\/olshopgue.bukaolshop.site\/akun\/?page=transaksi&nomor=875169634"
		},
		{
			"nomor_pembayaran": "274679984",
			"status_bayar": "di batalkan",
			"status_pengiriman": "di batalkan",
			"tanggal": "2023-07-27 15:14:07",
			"nama_barang": "Testing produk",
			"url_gambar_produk": "https:\/\/bukaolshop.s3-id-jkt-1.kilatstorage.id\/1\/67912029.jpg",
			"link_transaksi": "https:\/\/olshopgue.bukaolshop.site\/akun\/?page=transaksi&nomor=274679984"
		}		
	]
}
```


### HTTP Request

`GET /user/transaksi`

### Query Parameters

Parameter | Wajib | Deskripsi | Tipe
--------- | ------- | ----------- | -----------
token | Ya | Token dapat didapatkan di aplikasi bukaOlshop. | String
token_user | Ya | Isi dengan `{{token_user}}` | String
id_user | Ya | Isi dengan `{{id_user}}` | String
page | Tidak |Posisi daftar halaman produk. | Integer

<aside class="success">
Jika parameter <code>link_transaksi</code> dibuka didalam apk olshop, maka akan langsung dialihkan ke halaman detail transaksi bawaan apk olshop.
</aside>
