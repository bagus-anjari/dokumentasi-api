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
fetch('https://openapi.bukaolshop.net/v1/app/produk?token=xxxxxxxx')
.then(
  response => response.json()
).then(jsonResponse => {
  console.log(jsonResponse);
});

```

> Contoh parameter request tambahan, misal ke page selanjutnya

```javascript
fetch('https://openapi.bukaolshop.net/v1/app/produk?token=xxxxxxxx&page=2')
.then(
  response => response.json()
).then(jsonResponse => {
  console.log(jsonResponse);
});

```

Berikut ini merupakan URL utama endpoint pada Open API bukaOlshop:

`https://openapi.bukaolshop.net/v1/app`

Anda harus menambahkan path tambahan sesuai bagian yang ingin anda request. Contoh: jika anda ingin mendapatkan list produk, maka url akan menjadi:

`https://openapi.bukaolshop.net/v1/app/produk`

Walaupun Open API ini dapat diletakkan dimanapun di HTML, kami tetap mewajibkan untuk menyertakan `token` didalam tiap request untuk membedakan tiap aplikasi.

Walaupun tidak ada resiko keamanan yang berarti, kami tidak menyarankan anda menyebarkan link endpoint yang terdapat `token` olshop anda ke tempat publik seperti di dalam grup.

<aside class="notice">
Semua request ke endpoint Open API ini dilakukan melalui method <code>GET</code>.
</aside>

<aside class="notice">
<code>Token</code> dapat didapatkan di aplikasi bukaOlshop versi terbaru, dibagian Tab <code>TOKO</code>, klik <code>API & Callback</code>, pindah kehalaman <code>API</code>, disitu anda akan mendapatkan token pada bagian Open API.
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
