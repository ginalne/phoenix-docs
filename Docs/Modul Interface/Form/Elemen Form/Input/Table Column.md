---
    status: release
    title: Input Table Column (Elemen Input)
    description: Input Table Column adalah Elemen Input pada Form yang menjadi satu kolom di dalam Input Table, dengan format isian yang diatur lewat Format Type.
    pageDecoration:
      tree:
        priority: 0
---
# Form Input : Input Table Column

>**note** Input Table Column merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Input|Elemen Input]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Input Table Column adalah Elemen Input yang menjadi satu kolom di dalam [[Docs/Modul Interface/Form/Elemen Form/Input/Table|Input Table]]. Binding Input Table Column mengisi [[Docs/Tipe Data/Column]] dengan pivot dari Table yang dipilih pada Input Table.

Dengan Input Table Column, Anda dapat mengatur judul kolom, teks petunjuk, dan format hasil isian untuk setiap kolom tabel secara terpisah.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Input Table Column.

## Menambahkan Input Table Column

Input Table Column tidak ditambahkan lewat daftar Elemen. Widget ini ditambahkan otomatis saat Anda menambah kolom pada Input Table.

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Pilih [[Docs/Modul Interface/Form/Elemen Form/Input/Table|Input Table]] yang sudah memiliki pivot pada [[^field|Binding]]
3. Klik tombol [[^button/add|Add Column]] pada Input Table
4. Klik kiri widget Input Table Column yang baru muncul untuk memfokuskannya, lalu atur lewat Properties Panel
5. Pilih [[^field|Column]] pada [[^field|Binding]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Elemen Form/Input/Table#Mengelola Kolom|Mengelola Kolom]] pada halaman [[Docs/Modul Interface/Form/Elemen Form/Input/Table|Input Table]].

## Mengonfigurasi Input Table Column

Klik kiri Input Table Column di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]. Label Column (berikon kolom) juga tampil di atas Input Table Column sebagai informasi Binding.

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Input/toolbar-form-table-column.png]]
Selain tombol [[^button/delete|Remove]], Header Toolbar Input Table Column memiliki pengaturan teks untuk Label: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks Label yang sedang dipilih.

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Input/properties-form-table-column.png]]
#### Binding

| Bagian | Fungsi |
| --- | --- |
| [[^field|Table]] | Table sumber data kolom ini, yaitu Table dari pivot pada Input Table. |
| [[^field|Column]] | Column tempat isian kolom ini disimpan. |

#### State

>**note** Pengaruh State Input Table
> [[^field|Visible]], [[^field|Enable]], dan [[^field|Readonly]] pada [[Docs/Modul Interface/Form/Elemen Form/Input/Table|Input Table]] berlaku untuk semua kolomnya. Jika [[^field|Enable]] pada Input Table bernilai [[^value/boolean/false]], kolom tidak aktif. Jika [[^field|Readonly]] bernilai [[^value/boolean/true]], kolom menjadi readonly.

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Input Table Column. |
| [[^field|Enable]] | Mengaktifkan Binding. Jika [[^value/boolean/false]], Binding tidak aktif dan isian tidak berpengaruh ke Row. |
| [[^field|Readonly]] | Jika [[^value/boolean/true]], isi Input Table Column tidak dapat diubah oleh pengisi. |

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

Menampilkan [[Docs/Modul Interface/Form/Elemen Form/Input/Table|Input Table]] tempat Input Table Column berada.

## Menghapus Input Table Column

Langkah menghapus Input Table Column sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Input Table Column
> Menghapus Input Table Column akan menghapus kolom tersebut dari Input Table. Aksi tidak bisa dikembalikan.