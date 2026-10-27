---
    status: draft
    title: "Form Display : Chrono"
    description: Chrono adalah Elemen Display pada Form untuk menampilkan kronologi dalam bentuk alur step yang tersusun menurun.
---
# Form Display : Chrono

>**note** Chrono merupakan salah satu [[Docs/Modul Interface/Form/Apa itu Form#Elemen Display|Elemen Display]] dalam [[Docs/Modul Interface/Form/Apa itu Form|Form]] di Phoenix.

Display Chrono adalah [[Docs/Modul Interface/Form/Elemen Form/Display/Pengenalan|Elemen Display]] yang dapat digunakan untuk menampilkan kronologi di Form dalam bentuk alur step. Step tersusun menurun dalam bentuk daftar, dan setiap step memiliki judul serta keterangan.

Dengan Display Chrono, Anda dapat menunjukkan urutan tahapan atau peristiwa kepada pengisi tanpa memengaruhi data. Isi kronologi diatur langsung di halaman, bukan lewat Properties Panel.

Penjelasan umum tentang Elemen, Header Toolbar, Layout Panel, Menu Konteks Elemen, dan cara [[Docs/Modul Interface/Form/Elemen Form/Menghapus|menghapus Elemen]] ada di [[Docs/Modul Interface/Form/Apa itu Form#Mengelola Elemen Form|Apa itu Form?]]. Halaman ini fokus pada keunikan Display Chrono.

## Menambahkan Display Chrono

1. Aktifkan [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] pada [[Docs/Modul Interface/Form/Antarmuka|halaman kerja Form]]
2. Klik [[^field|Type something here to add...]] pada [[Docs/Modul Interface/Form/Elemen Form/Layout/Pengenalan|Layout]]
3. Pilih [[^field|Chrono]] dari daftar, atau ketik untuk mencarinya
4. Tambahkan step dan isi kronologinya. Lihat [[#Mengelola Step]]

Selengkapnya lihat [[Docs/Modul Interface/Form/Apa itu Form#Menambahkan Elemen]].

## Mengelola Step

Step diatur langsung pada Display Chrono di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]]. Setiap step memiliki tiga isian:

| Isian | Fungsi |
| --- | --- |
| [[^field|Title]] | Judul step. |
| [[^field|Description]] | Keterangan step. |
| [[^field|Time]] | Waktu step. Bersifat opsional. |

| Aksi | Cara |
| --- | --- |
| Menambah step | Klik tombol [[^button/add]]. |
| Menghapus step | Klik tombol [[^button/delete]] pada step yang ingin dihapus. |

<!--
  * [TODO] Fitur Display Chrono belum dibuat. Nama isian (Title, Description, Time), tombol tambah dan hapus step, serta tampilan menurun pada halaman ini adalah usulan. Sesuaikan dengan tampilan akhir setelah fitur selesai.
  * [TODO] Konfirmasi posisi tombol [[^button/add]] dan [[^button/delete]], cara mengubah urutan step, dan tipe isian Time (teks bebas atau tanggal dan waktu).
  * [TODO] Konfirmasi apakah Title wajib diisi dan apakah jumlah step memiliki batas minimum atau maksimum.
-->

## Mengonfigurasi Display Chrono

Klik kiri Display Chrono di [[Docs/Modul Interface/Form/Apa itu Form#Mode View dan Edit Mode|Edit Mode]] untuk menampilkan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Properties Panel]] dan [[Docs/Modul Interface/Form/Elemen Form/Mengonfigurasi#Header Toolbar]].

### Header Toolbar

![[Docs/Modul Interface/Form/Elemen Form/Display/toolbar-form-chrono.png]]
Header Toolbar Display Chrono hanya memiliki tombol [[^button/delete|Remove]] untuk [[#Menghapus Display Chrono]].

### Properties Panel

![[Docs/Modul Interface/Form/Elemen Form/Display/properties-form-chrono.png]]
#### State

| State | Fungsi |
| --- | --- |
| [[^field|Visible]] | Menampilkan atau menyembunyikan Chrono. |

#### Attributes

Tidak ada atribut yang dapat diisi pada Properties Panel Display Chrono. Isi kronologi diatur langsung di halaman. Lihat [[#Mengelola Step]].

#### Parent

Menampilkan Layout tempat Display Chrono berada. Ukuran, *padding*, dan *margin* Display Chrono diatur lewat Layout Panel. Lihat [[Docs/Modul Interface/Form/Apa itu Form#Layout Panel]].

<!--
  * [TODO] Tempatkan screenshot Header Toolbar (toolbar-form-chrono.png) dan Properties Panel (properties-form-chrono.png) di folder Display. Anotasi yang disarankan: nomor 1 pada tombol Remove, nomor 2 pada State dan Parent, nomor 3 pada daftar step beserta tombol tambah dan hapus.
-->

## Menghapus Display Chrono

Langkah menghapus Display Chrono sama dengan menghapus Elemen lain. Lihat [[Docs/Modul Interface/Form/Elemen Form/Menghapus|Menghapus Elemen]].

>**danger** Dampak penghapusan Display Chrono
> Menghapus Display Chrono akan menghapus seluruh step di dalamnya. Aksi tidak bisa dikembalikan.