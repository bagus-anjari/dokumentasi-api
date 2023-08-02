---
title: API bukaOlshop

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - javascript
  - php



toc_footers:
  - <a href='https://play.google.com/store/apps/details?id=com.bukaolshop'>Download bukaOlshop</a>


includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Welcome Developer

Selamat datang di dokumentasi API bukaOlshop. Anda bisa menggunakan API bukaOlshop untuk mengelola berbagai fitur utama pada aplikasi bukaOlshop seperti produk, transaksi, member dan kategori.

Version 1.1

<aside class="notice">
<b>Pembagian Endpoint</b><br>
Pada API bukaOlshop, terdapat dua tipe API, yaitu Open API dan Closed API. Penjelasan keduanya bisa <a href="#penjelasan-open-api">dilihat disini</a>.
</aside>
##Penjelasan Open API
Open API merupakan endpoint yang dapat pemilik olshop gunakan untuk mengakses data-data pada server bukaOlshop tanpa resiko di sisi keamanan akun. Open API ini dapat anda gunakan pada html di apk olshop langsung untuk keperluan mendapatkan data produk, kategori, transaksi, dan lain-lain.

Open API memungkinkan penyedia jasa desain halaman HTML untuk mengkostum tampilan sesuai permintaan client tanpa perlu meminta API key yang digunakan di Closed API, sehingga menghilangkan potensi peretasan pada akun pemilik olshop.

Open API dapat diakses secara unlimited pada paket PRO dan BISNIS, untuk paket LITE dan FREE terbatas hanya 100 request perhari.

##Penjelasan Closed API
Closed API merupakan endpoint yang memerlukan API key untuk mengakses data dan mengubah data di server bukaOlshop. API Key yang digunakan untuk mengakses Closed API ini sangat rentan dan harus di jaga dengan baik dan tidak diberikan ke siapapun karena endpoint ini dapat digunakan untuk menambah saldo member. Gunakan Closed API ini jika anda paham pemograman dan implementasi API, tidak disarankan untuk memberikan API key ke layanan pihak ketiga.

Closed API memiliki rate limit yang bisa dilihat disini  

# OPEN API
Dokumentasi Open API.

# Main Endpoint

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

Berikut ini merupakan URL utama endpoint pada Open API bukaOlshop:

`https://openapi.bukaolshop.net/v1`

Anda harus menambahkan path tambahan sesuai bagian yang ingin anda request. Contoh: jika anda ingin mendapatkan list produk, maka url akan menjadi:

`https://openapi.bukaolshop.net/v1/`<b>app/produk</b>

Walaupun Open API ini dapat diletakkan dimanapun di HTML, kami tetap mewajibkan untuk menyertakan `token` didalam tiap request untuk membedakan tiap aplikasi.

Walaupun tidak ada resiko keamanan yang berarti, kami **tidak** menyarankan anda menyebarkan link endpoint yang terdapat `token` olshop anda ke tempat publik seperti di dalam grup.

<aside class="notice">
Semua request ke endpoint Open API ini dilakukan melalui method <code>GET</code>.
</aside>

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
      "nama_produk": "omni",
      "harga_produk": 0,
      "harga_produk_asli": 0,
      "deskripsi_singkat": "",
      "deskripsi_panjang": "omni",
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
      "nama_produk": "Bag",
      "harga_produk": 343,
      "harga_produk_asli": 0,
      "deskripsi_singkat": "",
      "deskripsi_panjang": "dsadsa",
      "kondisi_produk": "Baru",
      "stok": 23,
      "berat": 34,
      "tanggal": "2020-11-16 01:26:27",
      "ukuran": ["4","5","6"],
      "warna": ["A","B","C"],
      "gambar_utama": "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/440277426c.jpg",
      "list_gambar": [
        "https://bukaolshop.s3-id-jkt-1.kilatstorage.id/1/440277426c.jpg"
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
		"jumlah_poin": "500",
		"catatan_saldo": [
			{
				"informasi_catatan": "Pengembalian saldo dari transaksi 875169634 yang otomatis dibatalkan.",
				"jumlah_dana": "3423",
				"saldo_terakhir": "12114",
				"tanggal": "2023-07-27 15:17:11",
				"tipe_jumlah": "tambah",
				"tipe_mutasi": "transaksi"
			},
			{
				"informasi_catatan": "Member melakukan transaksi menggunakan saldo (#875169634)",
				"jumlah_dana": "3423",
				"saldo_terakhir": "8691",
				"tanggal": "2023-07-27 15:17:11",
				"tipe_jumlah": "kurang",
				"tipe_mutasi": "transaksi"
			}
		]
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


# CLOSED API
# Main Endpoint
# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
