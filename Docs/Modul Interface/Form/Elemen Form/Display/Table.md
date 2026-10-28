---
    status: release
    title: "Form Display : Table"
    description: Table adalah Elemen Display pada Form untuk menampilkan tabel berisi teks biasa, dengan kolom dan baris yang dapat ditambah dan dihapus.
    pageDecoration:
      tree:
        priority: 0
---
# Form Display : Table

>**note** Table merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Display Table adalah [[Docs/Modul Interface/Form/Elemen Form/Display/Pengenalan|Elemen Display]] yang dapat digunakan untuk menampilkan tabel di Form. Saat pertama kali ditambahkan, tabel tampil dengan ukuran 2x2, yaitu dua kolom dan dua baris.

Isi setiap sel berupa teks biasa, tanpa binding dan tanpa expression, sehingga Display Table dapat memberi informasi kepada pengisi tanpa memengaruhi data.

>**note** Display Table berbeda dengan [[Docs/Modul Data/Table/Apa itu Table|Table]] pada Modul Data
> Display Table tidak terhubung ke Table mana pun. Isinya hanya teks yang Anda ketik langsung di halaman.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara [[Docs/Modul Interface/Form/Elemen Form/Menghapus|menghapus Elemen]] ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Display Table.

## Menambahkan Display Table

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] pada [[Docs/Modul Interface/Form/Antarmuka|halaman kerja Form]]
2. Klik [[^field|Type something here to add...]] pada [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Layout]]
3. Pilih [[^field|Table]] dari daftar, atau ketik untuk mencarinya
4. Isi sel tabel, lalu tambahkan kolom atau baris bila perlu. Lihat [[#Mengelola Kolom dan Baris]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengelola Kolom dan Baris

Kolom dan baris diatur langsung pada tabel di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]. Baris pertama berfungsi sebagai header tabel.

| Aksi | Cara |
| --- | --- |
| Mengisi sel | Klik sel, lalu ketik teks. Isi sel hanya teks biasa. |
| Menambah kolom atau baris | Klik tombol [[^button/add]] pada border tabel. |
| Menghapus baris | Klik kanan sel pada baris tersebut, lalu pilih [[^field/delete|Remove Row]]. |
| Menghapus kolom | Klik kanan sel pada kolom tersebut, lalu pilih [[^field/delete|Remove Column]]. |

## Mengonfigurasi Display Table

Klik kiri Display Table di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]], [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Display/header-table-form.png]]
Header Toolbar Display Table hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Display Table]].

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Display/properites-table-form.png]]
#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Table. |

#### Attributes

Tidak ada atribut yang dapat dikonfigurasi pada Display Table. Isi tabel diatur langsung di halaman. Lihat [[#Mengelola Kolom dan Baris]].

#### Parent

Menampilkan Layout tempat Display Table berada.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* Display Table dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

## Menghapus Display Table

Langkah menghapus Display Table sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Display Table
> Menghapus Display Table akan menghapus tabel beserta seluruh isinya. Aksi tidak bisa dikembalikan.