---
    status: draft
    title: "Form Display : Qr"
    description: Qr adalah Elemen Display pada Form untuk menampilkan kode QR yang siap di-scan, dengan isi yang diatur lewat atribut Content.
---
# Form Display : Qr

>**note** Qr merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Display Qr adalah [[Docs/Modul Interface/Form/Elemen Form/Display/Pengenalan|Elemen Display]] yang dapat digunakan untuk menampilkan kode QR di Form. Kode QR yang tampil siap di-scan, dan isinya diatur lewat atribut [[^field|Content]].

Dengan Display Qr, Anda dapat membagikan informasi kepada pengisi lewat kode QR tanpa memengaruhi data.

>**note** Perbedaan tampilan Edit Mode dan View Mode
> Di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]], Display Qr menampilkan isi QR dalam bentuk teks. Di View Mode, yang tampil adalah kode QR yang sebenarnya.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara [[Docs/Modul Interface/Form/Elemen Form/Menghapus|menghapus Elemen]] ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Display Qr.

## Menambahkan Display Qr

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] pada [[Docs/Modul Interface/Form/Antarmuka|halaman kerja Form]]
2. Klik [[^field|Type something here to add...]] pada [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Layout]]
3. Pilih [[^field|Qr]] dari daftar, atau ketik untuk mencarinya
4. Isi [[^field|Content]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Display Qr

Klik kiri Display Qr di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]].

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Display/toolbar-form-qr.png]]
Header Toolbar Display Qr hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Display Qr]].

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Display/properties-form-qr.png]]
#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Qr. |

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Content]] | Isi kode QR. Saat ini hanya berupa teks statis dan belum dapat berisi [[Docs/Tipe Data/Expression]]. |

#### Parent

Menampilkan Layout tempat Display Qr berada. Ukuran, *padding*, dan *margin* Display Qr diatur lewat Layout Panel. Lihat [[Docs/Modul Interface/Form/Apa itu Form#Layout Panel]].

<!--
  * [TODO] Tempatkan screenshot Header Toolbar (toolbar-form-qr.png) dan Properties Panel (properties-form-qr.png) di folder Display. Anotasi yang disarankan: nomor 1 pada tombol Remove, nomor 2 pada Content. Tambahkan juga gambar View Mode yang menampilkan kode QR sebenarnya.
  * [TODO] Konfirmasi penulisan nama Elemen di UI: "Qr" (mengikuti path) atau "QR".
-->

## Menghapus Display Qr

Langkah menghapus Display Qr sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Display Qr
> Menghapus Display Qr akan menghapus kode QR beserta isinya. Aksi tidak bisa dikembalikan.