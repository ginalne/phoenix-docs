---
    status: release
    title: "Space Object"
    description: 
    pageDecoration:
      tree:
        priority: 4
---
# Space Object

Object adalah data berlogika yang tampil sebagai objek 3D. Object mengambil datanya dari [[Docs/Tipe Data/Query|Query]] dengan kaidah [[Docs/Tipe Data/Query#Table Output|Table Output]], sehingga yang dirender adalah data riil, bukan hasil kalkulasi. Satu Object dapat menghasilkan banyak objek 3D, sebanyak [[Docs/Tipe Data/Row]] hasil Query.

## Atribut

| Atribut | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Object. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan Object. |
| [[^field|Origin]] | [[Docs/Format Data/Complex/3D Vector|3D Vector]] | Titik asal (*anchor*) tempat model setiap Row dirender. Origin tidak memengaruhi Row pada data sumber, dan hanya dapat diubah lewat klik kanan Object pada Outliner ➜ [[^field/edit|Edit]]. |
| [[^field|Model]] | [[Docs/Tipe Data/Model]] | Model yang menjadi wujud dan logika Object, disiapkan di komponen [[Docs/Modul Developer/Model/Apa itu Model|Model]] pada modul Developer. |
| [[^field|Query]] | [[Docs/Tipe Data/Query]] | Pengambil data dengan kaidah Table Output. Tombol [[^button/q]] hanya tersedia di modal Object dan tidak tampil langsung di antarmuka seperti pada [[Docs/Modul Interface/Space/Apa itu Space|Space]]. |

Karena logika Object yang kompleks disiapkan di komponen Model, daftar Key yang dapat diisi mengikuti Model yang dipilih pada [[^field|Model]].

## Mengelola Object

Berikut adalah aksi yang bisa dilakukan untuk mengelola data Object :

1. [[Docs/Modul Interface/Space/Environment/Menambahkan]] Data Environment
2. [[Docs/Modul Interface/Space/Environment/Mengubah]] Atribut atau Konfigurasi Environment
3. [[Docs/Modul Interface/Space/Environment/Menghapus]] Environment dari Space

