---
    status: release
    title: Card (Elemen Layout)
    description: Card adalah Elemen Layout pada Form yang menampung Elemen lain dalam satu kartu sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Card

>**note** Card merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Card adalah Elemen Layout yang dapat digunakan untuk menampung Elemen lain dalam satu kartu, sekaligus menentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber data bagi Elemen di dalamnya.

Dengan Card, Anda tidak perlu memetakan Table pada setiap kolom isian. Cukup pilih Table pada Card, lalu Elemen Input di dalamnya tinggal memilih [[Docs/Tipe Data/Column]]. Untuk data yang berelasi, Card dapat disusun bertingkat dengan memakai pivot.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Card.

## Mengapa Menggunakan Card?

- **Pemetaan data lebih singkat.** Table cukup dipilih sekali pada Card, lalu dipakai oleh semua Elemen Input di dalamnya.
- **Tampilan lebih tertata.** Elemen Display dan Elemen Input dikelompokkan dalam satu kartu yang rapi.
- **Mendukung data berelasi.** Card anak dapat memakai pivot untuk menyimpan isian ke Table yang berelasi dengan Table pada Card induknya.
- **Mudah dikelola.** Seluruh Elemen di dalam Card dapat dilihat sebagai daftar *Children* pada Properties Panel.

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Layout]] | Kategori Elemen yang berfungsi sebagai templat tempat Elemen lain diletakkan. Card adalah salah satunya. |
| [[#Binding Card|Header]] | Table pada Layout yang menjadi acuan bagi Elemen di bawahnya. |
| [[#Binding Card|table]] | Jenis Binding yang langsung memilih Table sebagai header. |
| [[#Binding Card|pivot]] | Jenis Binding untuk Card anak yang memakai relasi dari Table pada Card induknya. |
| [[#Children|Children]] | Daftar Elemen yang berada di dalam Card. |
| [[^field|Type something here to add...]] | *Field* di dalam Card untuk menambahkan Elemen lain. Lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]]. |

## Menambahkan Card

Anda dapat menambahkan Card dengan dua cara:

- Memilih [[^field|Card Layout]] pada [[Docs/Modul Interface/Form/Apa itu Form#Start Building|Start Building]] saat membuat Page.
- Memilih Card pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Card anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Card

![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-card.png]]
Klik kiri Card di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan Properties Panel dan Header Toolbar. Label Table (berikon tabel) juga tampil di atas Card sebagai informasi Binding.

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Menentukan header Card. Lihat [[#Binding Card]]. |
| [[^field|State]] | Mengatur kondisi Card. [[^field|Visible]] menampilkan atau menyembunyikan Card. |
| [[^field|Children]] | Daftar Elemen di dalam Card, lengkap dengan kategorinya ([[^field|display]] atau [[^field|input]]) dan namanya. |
| Header Toolbar | Pada Card hanya berisi tombol [[^button/delete|Remove]]. |

### Binding Card

Setiap Layout memiliki [[^field|Type]] Binding berupa [[^value/radio|table]] dan [[^value/radio|pivot]]. Artinya, Card tersebut ditentukan sebagai header bagi Elemen di bawahnya.

| Type | Fungsi |
| --- | --- |
| [[^value/radio|table]] | Memilih Table pada field [[^field|Table]] sebagai header. Elemen Input di dalam Card kemudian memilih Column dari Table ini. |
| [[^value/radio|pivot]] | Dipakai pada Card anak ketika Card induknya sudah memiliki Table. Pivot menjadi relasi lanjutan dari Table pada Card induk. |

>**note** Pilihan pivot bisa kosong
> Table pada Card induk harus memiliki pivot dengan Table lain. Jika tidak ada, pilihan pada pivot akan kosong.

Untuk mengatur Table:

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Klik kiri Card
3. Pada [[^field|Binding]], pilih [[^value/radio|table]] pada [[^field|Type]]
4. Pilih Table pada [[^field|Table]]

Untuk mengatur pivot pada Card anak:

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Klik kiri Card anak
3. Pada [[^field|Binding]], pilih [[^value/radio|pivot]] pada [[^field|Type]]
4. Pilih relasi yang tersedia

>**warning** Dampak mengubah Binding
> Mengubah [[^field|Table]]atau [[^field|Pivot]] pada Card dapat memutus Binding Column pada Elemen Input di dalamnya, sehingga menghasilkan error _binding missmatch_.

### Children

Daftar [[^field|Children]] menampilkan setiap Elemen di dalam Card. Setiap baris diberi kategori ([[^field|display]] atau [[^field|input]]) dan nama Elemen. Tambahkan Elemen baru lewat [[^field|Type something here to add...]] di bagian bawah Card.

## Menghapus Card

Langkah menghapus Card sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Apa itu Form#Menghapus Elemen]].

>**danger** Dampak penghapusan Card
> Menghapus Card akan menghapus semua Elemen di dalamnya. Aksi tidak bisa dikembalikan.