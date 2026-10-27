---
    status: release
    title: "Form Display : QR"
    description: QR adalah Elemen Display pada Form untuk menampilkan kode QR yang siap di-scan, dengan isi yang diatur lewat atribut Content.
    pageDecoration:
      tree:
        priority: 0
---
# Form Display : QR

>**note** QR merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Display QR adalah [[Docs/Modul Interface/Form/Elemen Form/Display/Pengenalan|Elemen Display]] yang dapat digunakan untuk menampilkan kode QR di Form. Kode QR yang tampil siap di-scan, dan isinya diatur lewat atribut [[^field|Content]].

Dengan Display QR, Anda dapat membagikan informasi kepada pengisi lewat kode QR tanpa memengaruhi data.

>**note** Perbedaan tampilan Edit Mode dan View Mode
> Di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]], Display QR menampilkan isi QR dalam bentuk teks. Di View Mode, yang tampil adalah kode QR yang sebenarnya.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara [[Docs/Modul Interface/Form/Elemen Form/Menghapus|menghapus Elemen]] ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Display QR.

## Menambahkan Display QR

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] pada [[Docs/Modul Interface/Form/Antarmuka|halaman kerja Form]]
2. Klik [[^field|Type something here to add...]] pada [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Layout]]
3. Pilih [[^field|QR]] dari daftar, atau ketik untuk mencarinya
4. Isi [[^field|Content]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengonfigurasi Display QR

Klik kiri Display QR di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]].

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Display/toolbar-form-QR.png]]
Header Toolbar Display QR hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Display QR]].

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Display/properties-form-QR.png]]
#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan QR. |

#### Attributes

| Atribut | Fungsi |
| --- | --- |
| [[^field|Content]] | Isi kode QR. Saat ini hanya berupa teks statis dan belum dapat berisi [[Docs/Tipe Data/Expression]]. |

#### Parent

Menampilkan Layout tempat Display QR berada.

### Layout Panel

Mengubah ukuran, *padding*, dan *margin* Display QR dilakukan lewat Layout Panel (ikon kecil di bawah Elemen yang difokuskan). Lihat [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Layout Panel]].

## Menghapus Display QR

Langkah menghapus Display QR sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Display QR
> Menghapus Display QR akan menghapus kode QR beserta isinya. Aksi tidak bisa dikembalikan.