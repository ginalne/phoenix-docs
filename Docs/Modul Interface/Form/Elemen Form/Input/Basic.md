---
    status: release
    title: Basic (Elemen Input)
    description: Basic adalah Elemen Input pada Form untuk mengisi satu Column dari Table, dengan format isian yang mengikuti Column tersebut.
---
# Form Input : Basic

>**note** Basic merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Input|Elemen Input]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Basic adalah Elemen Input yang dapat digunakan untuk mengisi satu [[Docs/Tipe Data/Column]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]]. Format isiannya mengikuti Column yang diikat, sehingga pengisi hanya memasukkan data sesuai tipe yang benar.

Dengan Basic, Anda dapat mengatur isian wajib, nilai bawaan, kondisi tampil, dan kondisi aktif langsung dari Properties Panel tanpa menulis logika tambahan.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara menghapus Elemen ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Basic.

## Menambahkan Basic

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]
2. Klik [[^field|Type something here to add...]] pada Layout
3. Pilih Basic dari daftar, atau ketik untuk mencarinya
4. Pilih [[^field|Column]] pada [[^field|Binding]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Basic

Klik kiri Display Chrono di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]]

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Layout/header-form-accordion.png]]
Tidak ada perbedaan dari Elemen lain, yaitu hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Accordion]].

### Properties Panel

Selain tombol [[^button/delete|Remove]], Header Toolbar Basic memiliki pengaturan teks untuk Label: ukuran font, *bold*, *italic*, *underline*, serta rata kiri, tengah, dan kanan. Pengaturan ini berlaku pada teks Label yang sedang dipilih.

![[Docs/Modul Interface/Form/Elemen Form/Input/properties-form-input.png]]
Klik kiri Basic di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan Properties Panel dan Header Toolbar. Label Column (berikon kolom) juga tampil di atas Basic sebagai informasi Binding.

#### Binding

| Bagian | Fungsi |
| --- | --- |
| [[^field|Table]] | Table sumber data Basic. |
| [[^field|Column]] | Column tempat isian Basic disimpan. Format isian Basic mengikuti Column ini. |

#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Basic. |
| [[^field|Enable]] | Mengaktifkan Binding. Jika [[^value/boolean/false]], Binding tidak aktif dan isian tidak berpengaruh ke Row. |
| [[^field|Readonly]] | Jika [[^value/boolean/true]], isi Basic tidak dapat diubah oleh pengisi. |

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
| [[^field|Label]] | Teks judul field yang tampil di atas isian. |
| [[^field|Placeholder]] | Teks petunjuk yang tampil saat field masih kosong. |
| [[^field|Format Type]] | Format isian. Mengikuti Column pada Binding, misalnya `String` untuk teks. |
| [[^field|Default Value]] | Nilai bawaan yang sudah terisi saat pengisi baru (publik) membuka Form. |


#### Parent

Menampilkan Layout tempat Basic berada. Mengubah ukuran, *padding*, dan *margin* Basic dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Form/Apa itu Form#Layout Panel]].