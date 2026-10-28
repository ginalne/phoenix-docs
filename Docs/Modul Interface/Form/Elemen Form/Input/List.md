---
    status: release
    title: Input List (Elemen Input)
    description: Input List adalah Elemen Input pada Form untuk mengisi banyak baris data dengan tampilan daftar blok, dengan kolom yang diatur lewat Input List Column.
    pageDecoration:
      tree:
        priority: 0
---
# Form Input : Input List

>**note** Input List merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Input|Elemen Input]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Input List adalah Elemen Input yang dapat digunakan untuk mengisi banyak baris data dengan tampilan daftar blok. Binding Input List harus berupa pivot, dan kolomnya diatur lewat [[Docs/Modul Interface/Form/Elemen Form/Input/List Column|Input List Column]].

Dengan Input List, pengisi dapat menambahkan dan menghapus baris langsung di Form, sedangkan Anda menambahkan kolom lewat tombol [[^button/add|Add Column]] tanpa menulis logika tambahan.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Input List.

## Menambahkan Input List

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Klik [[^field|Type something here to add...]] pada Layout
3. Pilih Input List dari daftar, atau ketik untuk mencarinya
4. Isi kolom pivot pada [[^field|Binding]]
5. Klik [[^button/add|Add Column]] untuk menambahkan kolom. Lihat [[#Mengelola Kolom]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengelola Kolom

Kolom Input List diatur langsung di halaman kerja pada [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]].

| Aksi | Cara |
| --- | --- |
| Menambah kolom | Klik tombol [[^button/add|Add Column]]. Widget [[Docs/Modul Interface/Form/Elemen Form/Input/List Column|Input List Column]] langsung ditambahkan otomatis. |
| Mengonfigurasi kolom | Klik kiri widget Input List Column untuk memfokuskannya, lalu atur lewat Properties Panel. Lihat [[Docs/Modul Interface/Form/Elemen Form/Input/List Column|Input List Column]]. |
| Menghapus kolom | Hapus widget Input List Column seperti menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Input/List Column#Menghapus Input List Column]]. |

## Cara Pengisi Menggunakan Input List

Pada View Mode, pengisi mengelola baris sendiri.

| Aksi | Cara |
| --- | --- |
| Menambah baris | Klik tombol [[^button/add|Add Row]]. |
| Menghapus baris | Klik tombol berikon sampah [[^button/delete]] di ujung kanan atas blok baris. |

Setiap baris pada Input List tampil sebagai satu blok yang berisi kolom-kolomnya.

## Mengonfigurasi Input List

Klik kiri Input List di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]], [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]]. Label pivot juga tampil di atas Input List sebagai informasi Binding.

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Input/header-list-form.png]]
Selain tombol [[^button/delete|Remove]], Header Toolbar Input List memiliki pengaturan teks untuk Label: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks Label yang sedang dipilih.

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Input/properties-list-form.png]]
#### Binding

| Bagian | Fungsi |
| --- | --- |
| [[^field|Table]] | Table sumber data dari Layout |
| [[^field|Pivot]] | Kolom pivot tempat baris Input Table disimpan. Binding Input Table harus berupa [[Docs/Tipe Data/Column]] yang terelasi dengan Table header. |

#### State

State pada Input List berlaku untuk semua kolom di dalamnya.

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Input List. Jika [[^value/boolean/false]], Input List tidak terlihat. |
| [[^field|Enable]] | Jika [[^value/boolean/false]], setiap kolom tidak di-Enable. |
| [[^field|Readonly]] | Jika [[^value/boolean/true]], setiap kolom menjadi Readonly. |

#### Validator

| Validator | Fungsi |
| --- | --- |
| [[^field|Required]] | Pengisi wajib mengisi field ini agar dapat mengirim Form. |

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Label]] | Teks judul Input List yang tampil di atas list. |

#### Parent

Menampilkan Layout tempat Input List berada.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* Input List dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

## Menghapus Input List

Langkah menghapus Input List sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Input List
> Menghapus Input List akan menghapus semua Input List Column di dalamnya. Aksi tidak bisa dikembalikan.