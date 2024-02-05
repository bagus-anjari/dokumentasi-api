---
title: API bukaOlshop (Dokumentasi)

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - javascript
  - php



toc_footers:
  - <a href='https://play.google.com/store/apps/details?id=com.bukaolshop'>Download bukaOlshop</a>


includes:
  - open
  - closed
  - callback
  - ratelimit
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Dokumentasi API bukaOlshop
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

Closed API memiliki rate limit yang bisa dilihat [disini](#rate-limit)  
