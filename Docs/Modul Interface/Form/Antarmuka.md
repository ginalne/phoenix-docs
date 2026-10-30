---
    status: release
    title: "Antarmuka Form"
    description: Penjelasan antarmuka di halaman kerja komponen Form
    pageDecoration:
      tree:
        priority: 1
---
# Antarmuka Form

![[Docs/Modul Interface/Form/interface-form.png]]

Halaman kerja Form terdiri dari bilah navigasi di bagian atas, area kerja di bagian tengah, dan panel [[^field|form flow]] di bagian bawah yang menampilkan daftar [[#Mengelola Page Form|Page]].

### Bilah navigasi Form terdiri dari:

Berikut penjelasan terkait beberapa fungsi halaman kerja Form:

| Tombol | Fungsi |
| --- | --- |
| Judul Form | Menampilkan ikon Form dan nama Form. |
| [[^button/edit|Edit]] | Mengubah atribut Form ([[^field|Name]] dan [[^field|Description]]). Lihat [[#Mengubah Form]]. |
| [[^button/publish|Publish]] | Membuka konfigurasi publikasi Form. Lihat [[#Mempublikasikan Form]]. |
| [[mode/view|View]] | Saklar saat Form berada di mode View. Klik untuk beralih ke Edit Mode agar isi Form dapat disunting. Lihat [[#Mode View dan Edit Mode]]. |
| [[mode/edit|Edit]] | Saklar saat Form berada di Edit Mode. Klik untuk beralih ke mode View agar isi Form hanya dapat dilihat. Lihat [[#Mode View dan Edit Mode]]. |
| [[^button/save|Save]] | Menyimpan perubahan isi Form. Aktif saat ada perubahan, dan perubahan juga tersimpan otomatis (*auto save*) setelah sekitar 3 detik. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan Form. |
| [[^button/submission|Informasi Submission]] | Menampilkan jumlah Submission sukses, menunggu, dan gagal. Klik untuk membuka [[#Mengelola Submission|Submission List]]. |

>**note** Perbedaan Icon
> Pada tampilan desktop, tombol [[^button/submission|Submission]] menampilkan susunan informasi Submission sekaligus, yaitu Submitted, Waiting, dan Failure.
> Pada tampilan mobile, tombol [[^button/submission|Submission]] didalam menu navigasi.

> **warning** Harap hati-hati
> Saat melakukan [[^button/refresh|Refresh]] halaman, pastikan bahwa perubahan Anda saat ini sudah disimpan. Jika tombol [[^button/save|Save]] masih aktif, berarti perubahan belum disimpan.

### Mode View dan Edit Mode

Form memiliki dua mode yang dipilih lewat toggle [[^field|mode]]:

| Mode | Fungsi |
| --- | --- |
| [[^value/radio|View]] | Melihat Form tanpa dapat mengubah isinya. Pada mode ini Form tampil sebagai [[^field|Read Only]]. |
| [[^value/radio|Edit]] | Menyusun Form: menambah [[#Mengelola Page Form|Page]], mengelola [[#Mengelola Elemen Form|Elemen]], dan melihat informasi [[#Binding Form|Binding]]. |

>**note** Syarat beralih ke Edit Mode
> Anda hanya dapat beralih ke Edit Mode jika [[^field|Data Access]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mengizinkan perubahan Form (lihat [[#Hak Akses Form]]).

### Interaksi Antarmuka Form

| Fungsi | Aksi |
| --- | --- |
| Memfokuskan Elemen (Edit Mode) | Klik kiri pada Elemen. [[#Properties Panel]] dan [[#Header Toolbar]] akan tampil. |
| Membuka Layout Panel (Edit Mode) | Klik ikon kecil di bawah Elemen yang difokuskan. Lihat [[#Layout Panel]]. |
| Membuka menu konteks Elemen (Edit Mode) | Klik kanan pada Elemen. Lihat [[#Menu Konteks Elemen]]. |
