---
    status: release
    title: Input Table (Elemen Input)
    description: Input Table adalah Elemen Input pada Form untuk mengisi banyak baris data dengan tampilan tabel, dengan kolom yang diatur lewat Input Table Column.
    pageDecoration:
      tree:
        priority: 0
---
# Form Input : Input Table

>**note** Input Table merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Input|Elemen Input]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Input Table adalah Elemen Input yang dapat digunakan untuk mengisi banyak baris data dengan tampilan tabel. Binding Input Table harus berupa pivot, dan kolomnya diatur lewat [[Docs/Modul Interface/Form/Elemen Form/Input/Table Column|Input Table Column]].

Dengan Input Table, pengisi dapat menambahkan dan menghapus baris langsung di Form, sedangkan Anda menambahkan kolom lewat tombol [[^button/add|Add Column]] tanpa menulis logika tambahan.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Input Table.

## Menambahkan Input Table

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Klik [[^field|Type something here to add...]] pada Layout
3. Pilih Input Table dari daftar, atau ketik untuk mencarinya
4. Isi kolom pivot pada [[^field|Binding]]
5. Klik [[^button/add|Add Column]] untuk menambahkan kolom. Lihat [[#Mengelola Kolom]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengelola Kolom

Kolom Input Table diatur langsung di halaman kerja pada [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]].

| Aksi | Cara |
| --- | --- |
| Menambah kolom | Klik tombol [[^button/add|Add Column]]. Widget [[Docs/Modul Interface/Form/Elemen Form/Input/Table Column|Input Table Column]] langsung ditambahkan otomatis. |
| Mengonfigurasi kolom | Klik kiri widget Input Table Column untuk memfokuskannya, lalu atur lewat Properties Panel. Lihat [[Docs/Modul Interface/Form/Elemen Form/Input/Table Column|Input Table Column]]. |
| Menghapus kolom | Hapus widget Input Table Column seperti menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Input/Table Column#Menghapus Input Table Column]]. |

## Cara Pengisi Menggunakan Input Table

Pada View Mode, pengisi mengelola baris sendiri.

| Aksi | Cara |
| --- | --- |
| Menambah baris | Klik tombol [[^button/add|Add Row]]. |
| Menghapus baris | Klik tombol [[^button/delete|Delete]] pada kolom action di akhir baris. |

## Mengonfigurasi Input Table

Klik kiri Input Table di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]], [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]]. Label pivot juga tampil di atas Input Table sebagai informasi Binding.

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Input/header-table-form.png]]
Selain tombol [[^button/delete|Remove]], Header Toolbar Input Table memiliki pengaturan teks untuk Label: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks Label yang sedang dipilih.

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Input/properties-table-form.png]]
#### Binding

| Bagian | Fungsi |
| --- | --- |
| [[^field|Table]] | Table sumber data dari Layout |
| [[^field|Pivot]] | Kolom pivot tempat baris Input Table disimpan. Binding Input Table harus berupa [[Docs/Tipe Data/Column]] yang terelasi dengan Table header. |

#### State

State pada Input Table berlaku untuk semua kolom di dalamnya.

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Input Table. Jika [[^value/boolean/false]], Input Table tidak terlihat. |
| [[^field|Enable]] | Jika [[^value/boolean/false]], setiap kolom tidak di-Enable. |
| [[^field|Readonly]] | Jika [[^value/boolean/true]], setiap kolom menjadi Readonly. |

#### Validator

| Validator | Fungsi |
| --- | --- |
| [[^field|Required]] | Pengisi wajib mengisi field ini agar dapat mengirim Form. |

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Label]] | Teks judul Input Table yang tampil di atas table. |

#### Parent

Menampilkan Layout tempat Input Table berada.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* Input Table dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

## Menghapus Input Table

Langkah menghapus Input Table sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Input Table
> Menghapus Input Table akan menghapus semua Input Table Column di dalamnya. Aksi tidak bisa dikembalikan.