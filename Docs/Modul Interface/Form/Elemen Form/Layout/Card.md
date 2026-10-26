---
    status: release
    title: Card (Elemen Layout)
    description: Card adalah Elemen Layout pada Form yang menampung Elemen lain dalam satu kartu sekaligus menjadi header Table bagi Elemen di dalamnya.
---
# Form Layout : Card

>**note** Card merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Layout|Elemen Layout]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Card adalah [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]] yang dapat digunakan untuk menampung [[Docs/Modul Interface/Form/Elemen Form/Pengenalan|Elemen]] lain dalam satu kartu, sekaligus menentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber data bagi Elemen di dalamnya.

Dengan Card, Anda tidak perlu memetakan Table pada setiap kolom isian. Cukup pilih Table pada Card, lalu Elemen Input di dalamnya tinggal memilih [[Docs/Tipe Data/Column]]. Untuk data yang berelasi, Card dapat disusun bertingkat dengan memakai pivot.

## Menambahkan Layout Card

Anda dapat menambahkan Card dengan dua cara:

- Memilih [[^field|Card Layout]] pada [[Docs/Modul Interface/Form/Form Page#Start Building|Start Building]] saat membuat Page.
- Memilih Card pada [[^field|Type something here to add...]] di dalam Layout lain (menjadi Layout anak).

Langkah lengkapnya ada di [[Docs/Modul Interface/Form/Elemen Form/Menambahkan|Menambahkan Elemen]].

## Mengonfigurasi Layout Card

![[Docs/Modul Interface/Form/Elemen Form/Layout/card-header-form.png]]
![[Docs/Modul Interface/Form/Elemen Form/Layout/properties-form-card.png]]
Klik kiri Card di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Table (berikon tabel) juga tampil di atas Card sebagai informasi Binding.

### Header Toolbar

Tidak ada perbedaan dari Elemen lain, yaitu hanya memiliki tombol [[^button/delete|Remove]]  untuk [[#Menghapus Card]].

### Properties Panel

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Menentukan header Card. Lihat [[#Binding Card]]. |
| [[^field|State]] | Mengatur kondisi Card. [[^field|Visible]] menampilkan atau menyembunyikan Card. |
| [[^field|Children]] | Daftar Elemen di dalam Card, lengkap dengan kategorinya ([[^field|display]] atau [[^field|input]]) dan namanya. |

### Binding

Binding dalam Card sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/Binding#Binding Layout]].

### State

State dalam Card sama dengan Elemen Layout lainnya. Lihat [[Docs/Modul Interface/Form/Elemen Form/State]].

### Attribute

Tidak ada atribut yang dapat dikonfigrasi pada Card.

### Children

Daftar [[^field|Children]] menampilkan setiap Elemen di dalam Card. Setiap baris diberi kategori ([[^field|layout]], [[^field|display]] atau [[^field|input]]) dan nama Elemen. Tambahkan Elemen baru lewat [[^field|Type something here to add...]] di bagian bawah Card.

## Menghapus Layout Card

Langkah menghapus Card sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Card
> Menghapus Card akan menghapus semua Elemen di dalamnya. Aksi tidak bisa dikembalikan.