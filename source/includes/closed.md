# CLOSED API

Dokumentasi Closed API.

# Main Endpoint

Berikut ini merupakan URL utama endpoint pada API bukaOlshop:

`https://bukaolshop.net/api/v1`

Anda harus menambahkan path tambahan sesuai bagian yang ingin anda request. Contoh: jika anda ingin mendapatkan detail produk, maka url akan menjadi:

`https://bukaolshop.net/api/v1/produk/id`

# Authentication

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"URL Endpoint API");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

Tipe autentikasi yang digunakan pada API bukaOlshop yaitu : bearer

Anda perlu mengirim header Authorization setiap kali ingin mengakses API bukaOlshop, jika terdapat kesalahan pada autentikasi ini, maka server bukaOlshop akan mengirim respon 401 Unauthorized. Anda bisa mendapatkan API key di aplikasi android bukaOlshop dengan melakukan generate API key.

Berikut ini bentuk autentikasi yang harus dikirim pada header:

Authorization: `Bearer API_KEY_ANDA_DISINI`

<aside class="notice">
Harap menjaga baik-baik API key anda, API key bisa dikatakan password yang digunakan untuk mengakses data olshop anda.
</aside>



# INFORMASI APLIKASI
## GET Informasi Aplikasi
>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,
"https://bukaolshop.net/api/v1/aplikasi/info");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "nama_toko": "OlshopTest",
  "nama_aplikasi": "OlshopTest",
  "nama_package": "com.olshopgue",
  "icon_aplikasi": "https://xxxxxxxx/xxx/xxx/xxx/xxx.png",
  "masa_aktif_premium": "2021-09-16",
  "status_premium": "lite",
  "tanggal_daftar_aplikasi": "2019-11-08 20:29:30",
  "telah_verifikasi_identitas": false,
  "email_pemilik_olshop": "cek@gmail.com",
  "nama_pemilik_olshop": "testing user",
  "hp_pemilik_olshop": "082234327658",

}
```

**Summary**: Informasi Aplikasi Olshop

**Description**: Endpoint ini berfungsi untuk menampilkan detail informasi aplikasi olshop anda. Tidak ada parameter yang wajib dikirim pada endpoint ini.

### HTTP Request

`GET /aplikasi/info`

### Query Parameters

Tidak ada parameter

### Responses

Code | Description
--------- | -------
200 | ok

# PRODUK
## GET Daftar List Produk

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$query=http_build_query(
  array("page"=>'1')
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,
"https://bukaolshop.net/api/v1/produk/list?".$query);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "page": 1,
  "data": [
    {
      "id_barang": "509369",
      "id_kategori": "35023",
      "nama_barang": "Judul produk 1",
      "harga_barang": 5000,
      "kondisi_barang": "Baru",
      "stok_barang": 7,
      "berat": 80,
      "tanggal": "2021-02-18 21:09:57",
      "url_gambar_barang": "url gambar"
    },
    {
      "id_barang": "439075",
      "id_kategori": "35023",
      "nama_barang": "Judul produk 2",
      "harga_barang": 6000,
      "kondisi_barang": "Baru",
      "stok_barang": 4,
      "berat": 46,
      "tanggal": "2021-01-14 19:33:19",
      "url_gambar_barang": "url gambar"
    }
  ]
}
```

**Summary**: Daftar Produk

**Description**: Endpoin ini berfungsi untuk mendapatkan daftar produk yang ada di aplikasi bukaOlshop anda. Method yang digunakan pada endpoin ini yaitu GET, dengan parameter yang wajib di isi yaitu page.

Parameter page ini merupakan halaman data produk, tiap halaman akan menampilkan 10 produk. Anda bisa mengisi parameter ini dengan angka 1 untuk mendapatkan 10 produk terbaru. Untuk melihat daftar produk selanjutnya, anda tinggal mengisi dengan angka 2, 3, 4 dan seterusnya.

### HTTP Request

`GET /produk/list`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
page | query | Posisi daftar halaman produk | Yes | Integer

### Responses

Code | Description
--------- | -------
200 | ok
400 | Bad Request, Pastikan anda memasukkan parameter page, isi parameter page tidak boleh 0 atau dibawah 0, dan tidak lebih dari 600.



## GET Detail Produk

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

// Ganti 1234567 dengan id_barang
$query=http_build_query(
  array("id_barang"=>'1234567')
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,
"https://bukaolshop.net/api/v1/produk/id?".$query);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "id_barang": "176941",
  "nama_barang": "Produk 2",
  "harga_barang": 34344,
  "harga_barang_asli": 0,
  "kondisi_barang": "Baru",
  "stok_barang": 43,
  "berat": 54,
  "tanggal": "2020-08-08 04:58:48",
  "merek": "",
  "sku": "",
  "ukuran": "",
  "warna": "",
  "id_kategori": "65258",
  "data_kategori": {
    "nama_kategori": "judul kategori",
    "gambar_kategori": "url gambar kategori"
  },
  "harga_grosir": [
    {
      "jumlah": "5",
      "harga": "60000"
    },
    {
      "jumlah": "6",
      "harga": "60000"
    }
  ],
  "lokasi_barang": {
    "id_origin": "43726",
    "nama_pengirim": "Nama pengirim",
    "provinsi": "Bali",
    "kota": "Badung",
    "kecamatan": "Abiansemal",
    "kode_pos": "",
    "no_hp": "082242235573"
  },
  "url_gambar": [
    "url gambar 1",
    "url gambar 2",
    "url gambar 3"
  ]
}
```

**Summary**: Detail Produk

**Description**: Endpoint ini berfungsi untuk mendapatkan detail produk anda. Method yang digunakan adalah GET dan parameter yang wajib di isi adalah id_barang. Anda dapat menemukan id_barang pada endpoint Daftar Produk atau pada Detail Transaksi.

### HTTP Request

`GET /produk/id`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_barang | query | id_barang untuk mendapatkan detail produk | Yes | String

### Responses

Code | Description
--------- | -------
200 | OK, Data produk ditemukan
400 | Not Found, Data produk tidak ditemukan, pastikan id_barang yang anda input sudah benar



## PATCH Edit Produk

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "id_barang"=>"563226",
  "nama_barang"=>"nama barang baru"
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/produk/id");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'PATCH');
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($post_body));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
  "code": 200,
  "status": "ok - Data berhasil diubah",
  "id_barang": "563226"
}
```

**Summary**: Edit Produk

**Description**: Endpoint ini berfungsi untuk mengubah data produk anda. Method yang digunakan adalah PATCH dan parameter yang wajib di-isi adalah id_barang. Anda dapat menemukan id_barang pada endpoint Daftar Produk atau pada Detail Transaksi.

Setelah anda memasukkan parameter id_barang, selanjutnya Anda cukup memasukkan parameter yang ingin diubah saja.

### HTTP Request

`PATCH /produk/id`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_barang	| Body |	id_barang wajib diisi	| Yes |	String
nama_barang	| Body |	| No |	String
deskripsi_panjang	| Body | | No |	String
deskripsi_singkat	| Body| |	No |	String
berat|	Body	|	|No |	Integer
jumlah_stok	|Body	||	No|	Integer
kondisi	|Body	||	No|	String
merek	|Body	||	No|	String
dalam_kotak	|Body	||	No|	String
garansi	|Body	||	No|	String
harga_barang|	Body	|	|No	|Integer
harga_barang_asli|	Body|	|	No|	Integer
sku|	Body	|	|No	|String



### Responses

Code | Description
--------- | -------
200 | OK, Produk berhasil diupdate
400 | Bad Request, Pastikan id_barang telah di isi dengan benar, dan pastikan anda memasukkan minimal 1 parameter tambahan yang ingin diubah





## DELETE Hapus Produk

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "id_barang"=>"551305",
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/produk/id");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'DELETE');
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($post_body));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
   "code": 200,
   "status": "ok - Data berhasil dihapus",
   "id_barang": "551305"
 }
```

**Summary**: Hapus Produk

**Description**: Endpoint ini berfungsi untuk menghapus produk anda. Method yang digunakan adalah DELETE dan parameter yang wajib di-isi adalah id_barang. Anda dapat menemukan id_barang pada endpoint Daftar Produk atau pada Detail Transaksi.

### HTTP Request

`DELETE /produk/id`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_barang	| Body |	id_barang wajib diisi	| Yes |	String




### Responses

Code | Description
--------- | -------
200 | OK, Data berhasil dihapus
400 | Not Found, Data id_barang yang ada input tidak ditemukan.



# MEMBER
## GET Daftar List Member

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$query=http_build_query(
  array("page"=>'1')
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/member/list?".$query);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
   "code": 200,
   "status": "ok",
   "page": 1,
   "data": [
     {
       "id_user": "289821",
       "email_user": "cek5@gmail.com",
       "nama_user": "Cek5",
       "nomor_telepon": "082366489912",
       "foto_profil": "Url foto profil",
       "status_akun": "aktif",
       "tanggal_daftar": "2020-10-05 05:25:44"
     },
     {
       "id_user": "289820",
       "email_user": "cek4@gmail.com",
       "nama_user": "Cek4",
       "nomor_telepon": "082234327658",
       "foto_profil": "Url foto profil",
       "status_akun": "aktif",
       "tanggal_daftar": "2020-10-05 05:24:54"
     }
   ]
 }
```

**Summary**: Daftar List Member

**Description**: Endpoin ini berfungsi untuk mendapatkan daftar member yang ada di aplikasi bukaOlshop anda. Method yang digunakan pada endpoin ini yaitu GET, dengan parameter yang wajib di isi yaitu page.

Anda bisa mengisi parameter ini dengan angka 1 untuk mendapatkan 10 member terbaru. Untuk melihat daftar member selanjutnya, anda tinggal mengisi dengan angka 2, 3, 4 dan seterusnya.

### HTTP Request

`GET /member/list`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
page	| query |	Posisi daftar halaman member	| Yes |	Integer


### Responses

Code | Description
--------- | -------
200 | OK


## GET Detail Member

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$query=http_build_query(
  array("email_user"=>'email_user@gmail.com')
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/member/id?".$query);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
   "code": 200,
   "status": "ok",
   "id_user": "130173",
   "email_user": "email@gmail.com",
   "nama_user": "Nama user",
   "tanggal_lahir": "2000-01-01",
   "jenis_kelamin": "Laki-laki",
   "nomor_telepon": "0822882432535",
   "foto_profil": "",
   "status_akun": "verified",
   "kode_referral": "MYTANPA",
   "tanggal_daftar": "2020-09-26 02:16:33",
   "data_alamat": [
     {
       "nama_penerima": "Nama user",
       "kecamatan": "Abiansemal",
       "kota": "Badung",
       "provinsi": "Bali",
       "nomor_telepon": "4949",
       "kode_pos": "80351",
       "alamat_lengkap": "Alamat lengkap user"
     }
   ]
 }
```

**Summary**: Detail Member

**Description**: Endpoint ini berfungsi untuk mendapatkan detail member anda. Method yang digunakan adalah GET. Terdapat 2 cara untuk mendapatkan detail member anda, yaitu melalui email atau melalui id_user.

Anda dapat mengisi parameter id_user atau email_user, silahkan pilih salah satu.

Anda dapat menemukan id_user pada endpoint List Member ataupun pada endpoint transaksi.

### HTTP Request

`GET /member/id`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_user	| query |	isi dengan id_user member	| No |	String
email_user	| query |	isi dengan email_user	| No |	String


### Responses

Code | Description
--------- | -------
200 | OK, Data ditemukan
400 | Bad Request, Pastikan anda telah mengisi parameter id_user atau email_user, pilih salah satu.
404 | Not Found, data tidak ditemukan


## GET Saldo Member

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$query=http_build_query(
  array("id_user"=>'xxxxx')
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/member/saldo?".$query);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "id_user": "289820",
  "email_user": "cek4@gmail.com",
  "nama_user": "Nama member",
  "transaksi_terakhir": "2021-04-06 01:58:39",
  "jumlah_saldo": 90000,
  "riwayat_saldo": [
    {
      "informasi_catatan": "Member mendapatkan komisi referral sebagai Downline",
      "jumlah_dana": 10000,
      "tanggal": "2020-10-05 05:14:10"
    }
  ]
}
```

**Summary**: Informasi Saldo Member

**Description**: Endpoint ini berfungsi untuk mendapatkan detail saldo yang dimiliki member anda. Method yang digunakan adalah GET. Terdapat 2 cara untuk mendapatkan detail member anda, yaitu melalui email atau melalui id_user.

Anda dapat mengisi parameter id_user atau email_user, silahkan pilih salah satu.

### HTTP Request

`GET  /member/saldo`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_user	| query |	isi dengan id_user member	| No |	String
email_user	| query |	isi dengan email_user	| No |	String


### Responses

Code | Description
--------- | -------
200 | OK, Data ditemukan
400 | Bad Request, Pastikan anda telah mengisi parameter id_user atau email_user, pilih salah satu.
404 | Not Found, data tidak ditemukan




## POST Ubah Saldo Member

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "email_user"=>"blabla@gmail.com",
  "tipe"=>"tambah",
  "jumlah"=>20000
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/member/saldo");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, $post_body);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
   "code": 200,
   "status": "ok - Saldo berhasil ditambah",
   "id_user": "289820",
   "email_user": "emailuser@gmail.com",
   "nama_user": "Nama user",
   "jumlah": 30000,
   "tipe": "tambah",
   "id_perubahan": "456406"
 }
```

**Summary**: Ubah Saldo Member

**Description**: Endpoint ini berfungsi untuk mengubah jumlah saldo yang dimiliki member anda. Method yang digunakan adalah POST.

Parameter yang wajib di-isi yaitu id_user atau email_user (pilih salah satu), tipe, dan jumlah.

### HTTP Request

`POST  /member/saldo`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_user	| body |	isi dengan id_user member	| No |	String
email_user	| body |	isi dengan email_user	| No |	String
tipe	| body |		isi dengan <code>tambah</code> atau <code>kurang</code>	| Yes |	Enum <code>tambah</code>/<code>kurang</code>
jumlah	| body |	isi dengan jumlah saldo yang ingin ditambah	| No |	Integer
pin	| body |	Jika ingin memvalidasi perubahan saldo dengan pin member, tambahkan parameter pin yang berisi PIN yang diinputkan oleh member	| No |	String 6 digit PIN
catatan_saldo	| body |	Catatan/informasi mengenai perubahan saldo	| No |	String


<aside class="warning">
Jika pengurangan jumlah saldo lebih besar dari pada saldo member sekarang, maka pengurangan akan ditolak, dan anda akan mendapatkan respon 403 - Forbidden.
</aside>

<aside class="notice">
Pilih salah satu antara id_user atau email_user, tidak perlu isi kedua parameter tersebut.
</aside>

### Responses

Code | Description
--------- | -------
200 | OK, data saldo berhasil diubah
400 | Bad Request, Pastikan anda telah mengisi parameter id_user atau email_user, pilih salah satu.
403 | Forbidden, Pengurangan lebih besar dari jumlah saldo member
404 | Not Found, data tidak ditemukan




## POST Konfirmasi TopUp Member

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "token_topup"=>"xxxxxxxxxxxxxxxxxxxx",
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/member/topup");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, $post_body);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
   "code": 200,
   "status": "ok - Saldo berhasil ditambah",
   "id_user": "289820",
   "email_user": "emailuser@gmail.com",
   "nama_user": "Nama user",
   "jumlah": 30000,
   "tipe": "tambah",
   "id_perubahan": "456406"
 }
```

**Summary**: Konfirmasi Penambahan topup saldo member

**Description**: Endpoint ini berfungsi untuk melakukan konfirmasi topup saldo member anda, anda memerlukan parameter <code>token_topup</code> yang hanya bisa didapatkan dengan melakukan override halaman topup saldo. Method yang digunakan adalah POST.

Parameter yang wajib di-isi yaitu <code>token_topup</code>.

### HTTP Request

`POST  /member/topup`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
token_topup	| body |	Isi dengan <code>token_topup</code>. Nilai <code>token_topup</code> hanya bisa anda dapatkan jika melakukan override halaman topup.	| Yes |	String



<aside class="notice">
 Jumlah topup yang akan masuk ke member anda yaitu dari perhitungan jumlah topup + kode unik.
</aside>

### Responses

Code | Description
--------- | -------
200 | OK, data saldo berhasil diubah
400 | Bad Request, Parameter <code>token_topup</code> belum di isi
404 | Not Found, data tidak ditemukan




## POST Ubah Saldo Member

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "email_user"=>"blabla@gmail.com",
  "tipe"=>"tambah",
  "jumlah"=>20000
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/member/saldo");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, $post_body);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
   "code": 200,
   "status": "ok - Saldo berhasil ditambah",
   "id_user": "289820",
   "email_user": "emailuser@gmail.com",
   "nama_user": "Nama user",
   "jumlah": 30000,
   "tipe": "tambah",
   "id_perubahan": "456406"
 }
```

**Summary**: Ubah Saldo Member

**Description**: Endpoint ini berfungsi untuk mengubah jumlah saldo yang dimiliki member anda. Method yang digunakan adalah POST.

Parameter yang wajib di-isi yaitu id_user atau email_user (pilih salah satu), tipe, dan jumlah.

### HTTP Request

`POST  /member/saldo`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_user	| body |	isi dengan id_user member	| No |	String
email_user	| body |	isi dengan email_user	| No |	String
tipe	| body |		isi dengan <code>tambah</code> atau <code>kurang</code>	| Yes |	Enum <code>tambah</code>/<code>kurang</code>
jumlah	| body |	isi dengan jumlah saldo yang ingin ditambah	| No |	Integer
pin	| body |	Jika ingin memvalidasi perubahan saldo dengan pin member, tambahkan parameter pin yang berisi PIN yang diinputkan oleh member	| No |	String 6 digit PIN


<aside class="warning">
Jika pengurangan jumlah saldo lebih besar dari pada saldo member sekarang, maka pengurangan akan ditolak, dan anda akan mendapatkan respon 403 - Forbidden.
</aside>

<aside class="notice">
Pilih salah satu antara id_user atau email_user, tidak perlu isi kedua parameter tersebut.
</aside>

### Responses

Code | Description
--------- | -------
200 | OK, data saldo berhasil diubah
400 | Bad Request, Pastikan anda telah mengisi parameter id_user atau email_user, pilih salah satu.
403 | Forbidden, Pengurangan lebih besar dari jumlah saldo member
404 | Not Found, data tidak ditemukan



#CHAT
## POST Kirim pesan

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "id_user"=>"xxxx",
  "pesan_teks"=>"ini adalah pesan anda"
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/chat/create");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, $post_body);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
    "code": 200,
    "status": "ok - Pesan berhasil dikirim",
    "id_user": "130173",
    "email_user": "emailuser@gmail.com",
    "nama_user": "Nama User",
    "id_barang": "257304",
    "pesan_teks": "Assalamualaikum, Apa kabar?"
  }
```

**Summary**: Kirim pesan ke member

**Description**: Endpoint ini berfungsi untuk mengirim pesan ke member anda.

Parameter yang wajib di-isi yaitu id_user atau email_user (pilih salah satu), dan parameter pesan_teks.

Parameter yang wajib di-isi yaitu <code>token_topup</code>.

<aside class="notice">
 Secara default, pesan akan dikirim sebagai chat umum. Jika anda ingin mengirim sebagai chat produk, maka anda perlu memasukkan parameter id_barang.
</aside>

### HTTP Request

`POST  /chat/create`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_user |	body	| isi dengan id_user member |	Yes |	String
pesan_teks |	body	| Masukkan pesan anda disini |	Yes |	String
id_barang |	body	| Masukkan ```id_barang``` jika anda ingin mengirim sebagai chat produk. |	No |	String





### Responses

Code | Description
--------- | -------
200 | OK, Pesan berhasil dikirim
400 | Bad Request, Pastikan anda telah mengisi parameter id_user. Pastikan anda juga sudah mengisi parameter pesan_teks.
404 | Not Found, data tidak ditemukan





#TRANSAKSI
## GET Daftar List Transaksi

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$query=http_build_query(
  array("page"=>'1')
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/transaksi/list?".$query);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
    "code": 200,
    "status": "ok",
    "data": [
      {
        "nomor_pembayaran": "2853130173354",
        "id_user": "130173",
        "status_bayar": "pending",
        "status_pengiriman": "belum diproses",
        "tanggal": "2020-10-12 01:15:04"
      },
      {
        "nomor_pembayaran": "81168130173359",
        "id_user": "130173",
        "status_bayar": "lunas",
        "status_pengiriman": "selesai",
        "tanggal": "2020-10-05 05:31:56"
      }
    ]
  }
```

**Summary**: Daftar Transaksi

**Description**: Endpoint ini berfungsi untuk menampilkan daftar transaksi pada aplikasi olshop anda. Method yang digunakan pada endpoint ini yaitu GET.

Parameter yang wajib di-isi adalah parameter page. Tiap page akan menampilkan 10 transaksi dengan urutan waktu terbaru. Anda dapat mengisi parameter page ini dengan angka (dimulai dari angka 1).

### HTTP Request

`GET  /transaksi/list`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
page |	query	| Posisi daftar halaman transaksi |	Yes |	Integer
id_user |	body	| isi dengan id_user member |	Yes |	String
filter_status |	query	| Filter berdasarkan status ```transaksi```, ```pending```,```diproses```,atau ```lunas``` |	No |	String





### Responses

Code | Description
--------- | -------
200 | OK, data berhasil ditemukan.
400 |	Bad Request, Pastikan anda telah mengisi parameter page, nilai parameter tidak boleh dibawah 1 dan tidak lebih dari 600




## GET Detail Transaksi

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$query=http_build_query(
  array("nomor_pembayaran"=>'xxxxxxxxxxxxx')
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/transaksi/id?".$query);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
   "code": 200,
   "status": "ok",
   "nomor_pembayaran": "74879326",
   "id_user": "2343",
   "status_bayar": "lunas",
   "status_pengiriman": "diproses",
   "bank_penerima": "BCA",
   "terakhir_update": "2021-02-27 19:48:38",
   "tanggal_buat": "2021-02-24 04:16:11",
   "potongan": 0,
   "kode_unik": 0,
   "total_membership": 15500,
   "total_transaksi": 1079949,
   "data_pesanan": [
     {
       "ekspedisi": "JNE OKE",
       "ongkos_kirim": 43000,
       "nama_pengirim": "Nama saya 1",
       "provinsi": "Riau",
       "kota": "Pekanbaru",
       "kecamatan": "Bukit Raya",
       "no_hp": "085279462345",
       "kode_pos": "28112",
       "data_produk": [
         {
           "id_transaksi": "xxxxx",
           "id_barang": "513039",
           "nama_barang": "barang 1",
           "jumlah_barang": 1,
           "total_harga": 10000,
           "catatan": "catatan pesanan",
           "nomor_resi": "xxxxxxxxxxxxxxxxxxxx",
           "catatan_tambahan": {
             "nama_varian": "Varian 123",
             "opsi": [
                 "UNGU","MERAH","BIRU"
               ]
             }
         }
       ]
     },
     {
       "ekspedisi": "JNE OKE",
       "ongkos_kirim": 12000,
       "nama_pengirim": "Nama saya 2",
       "provinsi": "Bali",
       "kota": "Badung",
       "kecamatan": "Abiansemal",
       "no_hp": "085723453462",
       "kode_pos": "80351",
       "data_produk": [
         {
           "id_transaksi": "xxxxx",
           "id_barang": "196552",
           "nama_barang": "barang 2",
           "jumlah_barang": 1,
           "total_harga": 50000,
           "catatan": " \nVarian : Vairan 1\n",
             "nomor_resi": ""
         },
         {
           "id_transaksi": "xxxxx",
           "id_barang": "196552",
           "nama_barang": "barang 3",
           "jumlah_barang": 1,
           "total_harga": 949449,
           "catatan": " \nVarian : Varian 3\n",
           "nomor_resi": "123456789"
         }
       ]
     }
   ]
 }
```

**Summary**: Detail Transaksi

**Description**: Endpoint ini berfungsi untuk mendapatkan detail transaksi pada olshop anda. Method yang digunakan pada endpoint ini yaitu GET.

Anda wajib memasukkan parameter nomor_pembayaran. Nomor pembayaran dapat anda temukan di endpoint list transaksi atau di aplikasi bukaOlshop anda.

### HTTP Request

`GET  /transaksi/id`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
nomor_pembayaran |	query	| Nomor pembayaran transaksi |	Yes |	String






### Responses

Code | Description
--------- | -------
200 | OK, data berhasil ditemukan.
400 | Bad request, pastikan anda telah memasukkan parameter nomor_pembayaran dengan benar
404 | Not Found, data nomor pembayaran yang anda masukkan tidak ditemukan







## PATCH Edit Status Transaksi

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "nomor_pembayaran"=>"xxxxxxxxxxxxx",
  "status_transaksi"=>"lanjut"
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/transaksi/id");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'PATCH');
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($post_body));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
  "code": 200,
  "status": "ok",
  "nomor_pembayaran": "74879326",
  "statu_bayar_awal": "lunas",
  "status_pengiriman_awal": "diproses",
  "status_bayar_terbaru": "lunas",
  "status_pengiriman_terbaru": "dikirim"
}
```

**Summary**: Edit Status Transaksi

**Description**: Endpoint ini berfungsi untuk mengubah status transaksi pada olshop anda.

### HTTP Request

`PATCH  /transaksi/id`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
nomor_pembayaran |	body	| Nomor pembayaran transaksi |	Yes |	String
status_transaksi |	body	| Isi dengan nilai ```lanjut```,```kembali```,```selesai```,```diproses```, ```batal```, ```batal_dan_refund``` atau ```lunas``` |	Yes |	String

**Penjelasan Parameter**

Untuk mengubah status transaksi, Anda cukup memasukkan 2 parameter yaitu:

1. nomor_pembayaran
2. status_transaksi

<aside class="notice">
Parameter status_transaksi memiliki 7 nilai yang telah ditetapkan, yaitu <code>lanjut</code>, <code>kembali</code>, <code>lunas</code>, <code>selesai</code>,<code>diproses</code>, <code>batal</code> dan <code>batal_dan_refund</code>.
</aside>

Berikut penjelasan kelima nilai tersebut:

1. ``lanjut``, nilai ini berfungsi untuk melanjutkan status transaksi ke tahap selanjutnya. Contoh, jika metode bayar transaksi menggunakan transfer bank dan memiliki status bayar pending, maka jika anda memasukkan nilai lanjut akan membuat transaksi berubah menjadi lunas, setelah lunas status akan menjadi diproses, dan setelah diproses status akan berubah menjadi dikirim dan seterusnya sampai status pengiriman selesai.

2. ``kembali``, nilai ini merupakan kebalikan dari nilai lanjut. Jika anda memasukkan nilai ini, maka status transaksi akan dikembalikan ke tahap sebelumnya. Contoh, jika status transaksi sekarang adalah dikirim, maka status akan berubah menjadi diproses, dan dari status diproses akan dirubah menjadi lunas dan seterusnya.

3. ``lunas``, nilai ini merupakan jalan pintas untuk membuat status pembayaran menjadi lunas.

4. ``diproses``, nilai ini merupakan jalan pintas untuk membuat status transaksi menjadi diproses.

5. ``selesai``, nilai ini merupakan jalan pintas untuk menyelesaikan sebuah transaksi (status pembayaran menjadi lunas dan status pengiriman menjadi selesai.

6. ``batal``, nilai ini untuk membuat status transaksi menjadi dibatalkan

7. ``batal_dan_refund``, nilai ini untuk membuat status transaksi menjadi dibatalkan dan secara otomatis mengembalikan uang ke saldo member. Refund hanya berlaku jika status bayar transaksi bukan "di batalkan"

Nilai-nilai pada parameter status_transaksi diatas dibuat agar tidak terjadi kesalahan pada input yang anda lakukan.


### Responses

Code | Description
--------- | -------
200 | OK, perubahan berhasil dilakukan.
400 | Bad Request, pastikan ada telah mengisi parameter ```nomor_pembayaran``` dan ```status_transaksi```
404 | Not Found, data tidak ditemukan

<aside class="notice">
    Parameter <code>status_bayar_awal</code> dan <code>status_pengiriman_awal</code> merupakan status transaksi sebelum adanya perubahan. Parameter <code>status_bayar_terbaru</code> dan status <code>status_pengiriman_terbaru</code> merupakan status transaksi terbaru yang mana perubahan telah dilakukan.
</aside>





## PATCH Edit Resi Transaksi

>Contoh request dengan PHP

```php
$token="API KEY ANDA";
$header=  array("Authorization: Bearer ".$token );

$post_body=array(
  "id_transaksi"=>"xxxx",
  "nomor_resi"=>"xxxxxxxxxxxxxxxxxxxx"
);
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL,"https://bukaolshop.net/api/v1/transaksi/id");
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'PATCH');
curl_setopt($ch, CURLOPT_POST, TRUE);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($post_body));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

$hasil = curl_exec($ch);
curl_close ($ch);
echo $hasil;
```

>Contoh Respon

```json
{
  "code": 200,
  "status": "ok - nomor resi berhasil diubah",
}
```

**Summary**: Edit Resi Transaksi

**Description**: Endpoint ini berfungsi untuk mengubah nomor resi transaksi pada olshop anda.

### HTTP Request

`PATCH  /transaksi/id`

### Query Parameters

Name | Located in | Description | Required | Type
--------- | ------- | ----------- | ----------- | -----------
id_transaksi |	body	| Nomor id_transaksi |	Yes |	String
nomor_resi |	body	| Isi dengan nomor resi anda |	Yes |	String
harga_modal | body | Isi dengan harga modal produk	| No | Integer/Number

<aside class="notice">
 Parameter id_transaksi dapat anda temukan di endpoint <a href="#get-detail-transaksi">GET Detail Transaksi</a>
</aside>

### Responses

Code | Description
--------- | -------
200 | OK, perubahan berhasil dilakukan.
400 | Bad Request, pastikan ada telah mengisi parameter ```id_transaksi``` dan ```nomor_resi```
404 | Not Found, data tidak ditemukan
