---
    status: release
    title: Melihat Detail Node
    description: Cara membuka detail Node untuk melihat atributnya tanpa mengubah data.
    pageDecoration:
      tree:
        priority: 6
---
# Melihat Detail Node

Detail menampilkan atribut [[Docs/Tipe Data/Node|Node]] tanpa mengubahnya. Gunakan [[^field|Detail]] untuk memeriksa Node anak dan posisi Node dalam silsilahnya, sedangkan perubahan dilakukan lewat [[^field/edit|Edit]].

## Membuka Detail

![[Docs/Modul Data/Tree/Node/detail-node.png|Detail Node]]

1. Buka halaman kerja [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].
2. Klik kanan [[Docs/Tipe Data/Node|Node]] yang akan dilihat ➜ [[^field|Detail]].

### Informasi pada Detail

| Informasi | Penjelasan |
| --------- | ---------- |
| [[^field|Name]] | Nama Node. |
| [[^field|Children]] | Daftar Node anak langsung, ditampilkan bernomor. |
| [[^field|Ancestor]] | Daftar leluhur Node. Nomor dihitung dari *anchor* hingga ancestor terdekat. Selengkapnya lihat [[#Membaca Ancestor]]. |

### Membaca Ancestor

[[^field|Ancestor]] menampilkan leluhur Node secara berurutan. Salah satu leluhur ditandai dengan label *anchor* dan menjadi nomor 1, lalu nomor berlanjut hingga ancestor terdekat. Nomor ini memudahkan Anda menghitung jarak kedalaman sebuah leluhur.

Untuk mengganti *anchor*, klik label *anchor* pada ancestor lain. Nomor dihitung ulang dari ancestor tersebut sebagai nomor 1. Penggantian ini tidak disimpan dan kembali semula ketika Detail ditutup.

Contoh: Detail Node [[^value/node|Laptop]] dengan silsilah Origin ➜ [[^value/node|Elektronik]] ➜ [[^value/node|Komputer]] menampilkan [[^field|Ancestor]] berikut.

| Anchor | Nomor 1 | Nomor 2 | Nomor 3 |
| ------ | ------- | ------- | ------- |
| Origin | Origin | [[^value/node|Elektronik]] | [[^value/node|Komputer]] |
| [[^value/node|Elektronik]] | [[^value/node|Elektronik]] | [[^value/node|Komputer]] | - |

## Membuka Detail Langsung

Anda dapat membuat klik kanan langsung membuka Detail tanpa menampilkan menu konteks.

1. Klik [[^field|Context]] di bagian bawah area kerja hingga nilainya menjadi `Detail`. Setiap klik berpindah ke nilai berikutnya, yaitu `Menu`, `Edit`, dan `Detail`.
2. Klik kanan [[Docs/Tipe Data/Node|Node]]. Detail terbuka langsung.

>**note** Perubahan Context bersifat sementara
> Penggantian [[^field|Context]] di halaman kerja hanya berlaku sementara. Untuk mengubah nilai awalnya, gunakan [[^field|Default Configuration]] pada [[Docs/Modul Data/Tree/Apa itu Tree#Mengubah Tree|Edit Tree]].

## Lihat Juga

- [[Docs/Modul Data/Tree/Node/Mengubah Nama|Mengubah Nama Node]]
- [[Docs/Modul Data/Tree/Node/Mengubah Urutan|Mengubah Urutan Node]]
- [[Docs/Modul Data/Tree/Node/Pengenalan|Tree Node]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]] untuk mengambil leluhur lewat Flow.