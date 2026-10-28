---
    status: release
    title: Input List Column (Elemen Input)
    description: Input List Column adalah Elemen Input pada Form yang menjadi satu kolom di dalam Input List, dengan format isian yang diatur lewat Format Type.
    pageDecoration:
      tree:
        priority: 0
---
# Form Input : Input List Column

>**note** Input List Column merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Input|Elemen Input]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Input List Column adalah Elemen Input yang menjadi satu kolom di dalam [[Docs/Modul Interface/Form/Elemen Form/Input/List|Input List]]. Binding Input List Column mengisi [[Docs/Tipe Data/Column]] dengan pivot dari Table yang dipilih pada Input List.

Dengan Input List Column, Anda dapat mengatur judul kolom, teks petunjuk, dan format hasil isian untuk setiap kolom daftar secara terpisah.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Input List Column.

## Menambahkan Input List Column

Input List Column tidak ditambahkan lewat daftar Elemen. Widget ini ditambahkan otomatis saat Anda menambah kolom pada Input List.

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Pilih [[Docs/Modul Interface/Form/Elemen Form/Input/List|Input List]] yang sudah memiliki pivot pada [[^field|Binding]]
3. Klik tombol [[^button/add|Add Column]] pada Input List
4. Klik kiri widget Input List Column yang baru muncul untuk memfokuskannya, lalu atur lewat Properties Panel
5. Pilih [[^field|Column]] pada [[^field|Binding]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Elemen Form/Input/List#Mengelola Kolom|Mengelola Kolom]] pada halaman [[Docs/Modul Interface/Form/Elemen Form/Input/List|Input List]].

## Mengonfigurasi Input List Column

Klik kiri Input List Column di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Column (berikon kolom) juga tampil di atas Input List Column sebagai informasi Binding.

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Input/header-list-column-form.png]]
Selain tombol [[^button/delete|Remove]], Header Toolbar Input List Column memiliki pengaturan teks untuk Label: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks Label yang sedang dipilih.

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Input/properties-list-column-form.png]]
#### Binding

| Bagian | Fungsi |
| --- | --- |
| [[^field|Table]] | Table sumber data kolom ini, yaitu Table dari pivot pada Input List. |
| [[^field|Column]] | Column tempat isian kolom ini disimpan. |

#### State

>**note** Pengaruh State Input List
> [[^field|Visible]], [[^field|Enable]], dan [[^field|Readonly]] pada [[Docs/Modul Interface/Form/Elemen Form/Input/List|Input List]] berlaku untuk semua kolomnya. Jika [[^field|Enable]] pada Input List bernilai [[^value/boolean/false]], kolom tidak aktif. Jika [[^field|Readonly]] bernilai [[^value/boolean/true]], kolom menjadi readonly.

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Input List Column. |
| [[^field|Enable]] | Mengaktifkan Binding. Jika [[^value/boolean/false]], Binding tidak aktif dan isian tidak berpengaruh ke Row. |
| [[^field|Readonly]] | Jika [[^value/boolean/true]], isi Input List Column tidak dapat diubah oleh pengisi. |

#### Validator

| Validator | Fungsi |
| --- | --- |
| [[^field|Required]] | Pengisi wajib mengisi field ini agar dapat mengirim Form. |

>**note** Kapan Required tidak berlaku
> [[^field|Required]] tidak berlaku jika [[^field|Visible]] atau [[^field|Enable]] bernilai [[^value/boolean/false]].

Saat ini [[^field|Required]] adalah satu-satunya validator.

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Label]] | Judul kolom. |
| [[^field|Placeholder]] | Teks petunjuk yang tampil saat baris pada kolom ini masih kosong. |
| [[^field|Format Type]] | Format hasil isian yang diharapkan, misalnya `String` untuk teks. |

#### Parent

Menampilkan [[Docs/Modul Interface/Form/Elemen Form/Input/List|Input List]] tempat Input List Column berada.

## Menghapus Input List Column

Langkah menghapus Input List Column sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Input List Column
> Menghapus Input List Column akan menghapus kolom tersebut dari Input List. Aksi tidak bisa dikembalikan.