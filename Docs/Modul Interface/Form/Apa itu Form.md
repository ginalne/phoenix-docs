---
    status: release
    title: "Apa itu Form?"
    description: "Form adalah komponen untuk menginput, melihat, dan mengubah data secara terstruktur, serta dapat dibagikan kepada publik untuk mengumpulkan data."
    pageDecoration: 
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
  <path
    d="M7 2.5a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-7a.5.5 0 0 1-.5-.5zM2 1a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2a2 2 0 0 0 2-2V3a2 2 0 0 0-2-2zm0 8a2 2 0 0 0-2 2v2a2 2 0 0 0 2 2h2a2 2 0 0 0 2-2v-2a2 2 0 0 0-2-2zm.854-3.646a.5.5 0 0 1-.708 0l-1-1a.5.5 0 1 1 .708-.708l.646.647 1.646-1.647a.5.5 0 1 1 .708.708zm0 8a.5.5 0 0 1-.708 0l-1-1a.5.5 0 0 1 .708-.708l.646.647 1.646-1.647a.5.5 0 0 1 .708.708zM7 10.5a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-7a.5.5 0 0 1-.5-.5zm0-5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5m0 8a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5" />
</svg>'
      tree:
        priority: 10
    icon: assets/icons/type/-f.svg
---
# Apa itu Form?

>**note** Form merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Form adalah komponen yang dapat digunakan untuk menginput, melihat, dan mengubah data secara terstruktur. Setiap kolom ditampilkan sebagai *field* yang jelas dan terarah, sehingga proses pengisian data menjadi lebih rapi, konsisten, dan minim kesalahan.

Anda dapat menyusun tampilan Form sendiri dari beberapa [[#Memahami Elemen|Elemen]], mengikatnya ke data di [[Docs/Modul Data/Table/Apa itu Table|Table]], lalu membagikannya kepada publik lewat [[#Mempublikasikan Form|Publish]] agar proses pengumpulan data menjadi lebih cepat dan efektif.

## Mengapa Menggunakan Form?

- **Pengisian data lebih rapi.** Setiap kolom tampil sebagai *field* yang jelas, sehingga pengisi tahu persis apa yang harus diisi.
- **Data konsisten dan minim kesalahan.** Setiap *field* terikat ke [[Docs/Tipe Data/Column]] pada [[Docs/Tipe Data/Row]] yang tepat lewat [[#Binding Form|Binding]], sehingga hasil isian masuk ke tempat yang benar.
- **Pengumpulan data lebih cepat.** Form dapat dibagikan kepada publik lewat tautan, tanpa pengisi perlu masuk ke Phoenix.
- **Tampilan dapat disesuaikan.** Anda menyusun Form dari [[#Memahami Elemen|Elemen]] dan mengatur gayanya sesuai kebutuhan.
- **Pengiriman mudah dipantau.** Setiap pengiriman tercatat sebagai Submission, lengkap dengan status dan grafiknya di [[#Mengelola Submission|Submission List]].

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[#Mengelola Page Form|Page]] | Satu halaman di dalam Form. Satu Form dapat memiliki beberapa Page. |
| [[#Mengelola Page Form|Form Flow]] | Alur Page pada Form. Page paling kiri tampil pertama, dan Form dapat disubmit setelah pengisi mencapai Page terakhir. |
| [[#Memahami Elemen|Elemen]] | Satu objek penyusun isi Form, misalnya teks, tabel, atau kolom isian. |
| [[#Elemen Layout|Layout]] | Kategori Elemen yang berfungsi sebagai templat tempat Elemen lain diletakkan. |
| [[#Elemen Display|Display]] | Kategori Elemen yang menampilkan informasi, baik statis maupun hasil dari nilai Binding. |
| [[#Elemen Input|Input]] | Kategori Elemen untuk mengisi atau menampilkan informasi yang berlaku pada Binding. |
| [[#Binding Form|Binding]] | Ikatan antara Elemen dan data di [[Docs/Modul Data/Table/Apa itu Table|Table]] agar isian dan hasil akhirnya sesuai. |
| [[#Mode View dan Edit Mode|Edit Mode]] | Mode untuk menyusun Form, termasuk melihat informasi Binding dan konfigurasi Elemen. |
| [[#Mempublikasikan Form|Publish]] | Konfigurasi untuk membagikan Form kepada publik. |
| [[#Mengelola Submission|Submission]] | Catatan setiap pengiriman Form, dengan status sukses, menunggu, atau gagal. |

Selengkapnya tentang penjelasan khusus setiap Elemen dapat dilihat pada halaman masing-masing di [[#Memahami Elemen]].


### Elemen Display

Display berfungsi menampilkan informasi. Informasi yang ditampilkan dapat berupa isi statis (misalnya judul atau keterangan), atau hasil dari [[Docs/Tipe Data/Expression]] terhadap nilai Binding (misalnya nilai total).

### Elemen Input

Input berfungsi untuk mengisi atau menampilkan informasi yang berlaku pada Binding. Pada Form yang dipublikasikan, Elemen Input inilah yang diisi oleh pengguna dan dikirim sebagai Submission.

### Menambahkan Elemen

1. Aktifkan [[#Mode View dan Edit Mode|Edit Mode]]
2. Buka Page yang akan diisi
3. Klik [[^field|Type something here to add...]] pada Elemen Layout
4. Pilih Elemen pada dropdown yang muncul, atau ketik untuk mencari Elemen yang diinginkan

### Mengonfigurasi Elemen

![[Docs/Modul Interface/Form/panel-form.png]]

Klik kiri pada Elemen di [[#Mode View dan Edit Mode|Edit Mode]] untuk memfokuskannya. Setelah itu muncul [[#Properties Panel]] dan [[#Header Toolbar]]. Selain itu, [[#Layout Panel]] dapat dibuka lewat ikon kecil di bawah Elemen yang difokuskan.

#### Properties Panel

Panel untuk mengatur properti Elemen secara rinci, seperti [[^field|Binding]], [[^field|State]], [[^field|Validators]], [[^field|Attributes]], [[^field|Children]], dan [[^field|Parent]]. Isinya berbeda-beda pada setiap Elemen.

| Bagian | Fungsi |
| --- | --- |
| [[^field|Binding]] | Mengikat Elemen ke data. Lihat [[#Binding Form]]. |
| [[^field|State]] | Mengatur kondisi Elemen, misalnya [[^field|Visible]] untuk menampilkan atau menyembunyikan Elemen. |
| [[^field|Validators]] | Aturan yang harus dipenuhi pengisi agar dapat mengirim Form, misalnya [[^field|Required]]. |
| [[^field|Attributes]] | Mengatur pengaturan khusus Elemen, termasuk gayanya. Isinya berbeda-beda pada setiap Elemen. |
| [[^field|Children]] atau [[^field|Parent]] | Menampilkan Elemen yang berada di dalam Elemen ini (*children*), atau Elemen tempat Elemen ini berada (*parent*). |

#### Header Toolbar

Bilah pintasan aksi yang selalu memiliki tombol [[^button/delete|Remove]] untuk menghapus Elemen.

#### Layout Panel

Panel untuk mengatur ukuran, *padding*, *margin*, dan beberapa *styling* Elemen. Setiap Elemen memiliki pengaturan ini, dan panel dibuka lewat ikon kecil di bawah Elemen yang difokuskan.

| Bagian | Fungsi |
| --- | --- |
| [[^field|min.]] layout | Ukuran persentase minimum Elemen terhadap layar. |
| [[^field/resize]] | Kontrol tambahan terkait ukuran atau tampilan pengaturan dimensi. |
| [[^field|padding]] | Mengatur jarak di bagian dalam Elemen, yaitu antara batas Elemen dan kontennya. |
| [[^field|margin]] | Mengatur jarak di luar Elemen, yaitu ruang antara Elemen tersebut dan Elemen lain di sekitarnya. |

### Menu Konteks Elemen

Klik kanan pada Elemen untuk membuka menu konteks.

| Menu | Fungsi |
| --- | --- |
| [[^field/copy|Copy Layout Style]] | Menyalin konfigurasi *styling* Elemen. |
| [[^field/paste|Paste Layout Style]] | Menerapkan salinan konfigurasi *styling* Elemen. |
| [[^field/up|Move Back]] | Memindahkan posisi dengan Elemen sebelumnya (tidak berpengaruh jika Elemen berada di barisan pertama). |
| [[^field/down|Move Next]] | Memindahkan posisi dengan Elemen setelahnya (tidak berpengaruh jika Elemen berada di barisan akhir). |

### Menghapus Elemen

1. Aktifkan [[#Mode View dan Edit Mode|Edit Mode]]
2. Klik kiri Elemen yang akan dihapus
3. Klik [[^button/delete|Remove]] pada [[#Header Toolbar]]
4. Konfirmasi penghapusan Elemen

>**warning** Dampak penghapusan Elemen
> Menghapus Elemen Layout akan menghapus semua Elemen yang berada di dalamnya. Binding yang dipakai Elemen tersebut juga terputus dari Form.

## Binding Form

Binding adalah ikatan berjenjang yang menghubungkan Elemen dengan data. Tujuannya agar isian pengguna dan hasil akhirnya tersimpan pada [[Docs/Tipe Data/Row]] dan relasi yang tepat di [[Docs/Modul Data/Table/Apa itu Table|Table]].

Setiap Elemen Layout memiliki [[^field|Type]] Binding berupa [[^value/radio|table]] dan [[^value/radio|pivot]]. Artinya, Layout tersebut ditentukan sebagai header bagi Elemen di bawahnya.

| Type | Fungsi |
| --- | --- |
| [[^value/radio|table]] | Memilih [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai header Layout. |
| [[^value/radio|pivot]] | Dipakai pada Layout anak bila Layout induknya sudah memiliki Table. Pivot menjadi relasi lanjutan dari Table tersebut. |

>**note** Pilihan pivot bisa kosong
> Table pada header harus memiliki pivot dengan Table lain. Jika tidak ada, pilihan pada pivot akan kosong.

Secara umum, urutannya seperti ini:

1. Layout paling atas diikat ke [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber datanya lewat Type [[^value/radio|table]].
2. Elemen Input di dalamnya diikat ke [[Docs/Tipe Data/Column]] pada Table tersebut, sehingga setiap *field* tahu ke kolom mana isiannya disimpan.
3. Layout anak yang mewakili data turunan diikat lewat Type [[^value/radio|pivot]] sebagai relasi lanjutan dari Table pada Layout induknya.

Informasi Binding dapat dilihat di [[#Mode View dan Edit Mode|Edit Mode]] sebagai label pada Elemen. Klik kiri Elemen untuk memfokuskannya dan melihat pengaturan [[^field|Binding]] pada [[#Properties Panel]]. Selengkapnya lihat [[Docs/Modul Interface/Form/Layout/Card/Penjelasan#Binding Card|Binding Card]].

## Mengelola Submission

Setiap kali Form dikirim, Phoenix mencatatnya sebagai Submission dengan status sukses (*Submitted*), menunggu (*Waiting*), atau gagal (*Failure*). Ringkasan jumlahnya ada pada [[^button/submission|Informasi Submission]] di bilah navigasi.

Klik [[^button/submission|Informasi Submission]] untuk membuka **Submission List** di sebelah kanan.

![[Docs/Modul Interface/Form/submission-form.png]]

| Bagian | Fungsi |
| --- | --- |
| Grafik | Menampilkan jumlah Submission dari waktu ke waktu untuk status Submitted, Waiting, dan Failure. Arahkan kursor ke grafik untuk melihat rinciannya pada tanggal tertentu. |
| Daftar | Menampilkan setiap Submission dengan kolom [[^field|ID/Name]], [[^field|Status/ID]], [[^field|Start At]], dan [[^field|Updated At]]. |
| Rincian Submission | Klik panah di kiri baris untuk membuka rincian Submission, seperti data yang ditambahkan, ID, atau error yang terjadi. |
| Tombol salin ID Submission | Klik [[^ubtton/copy]] di baris untukmenyalin ID dari submission. |
| Filter waktu | Memfilter data dengan pilihan [[^value/radio|All Time]], [[^value/radio|This Month]], [[^value/radio|This Week]], dan [[^value/radio|Today]]. |
| [[^field|Search Submission...]] | Mencari Submission berdasarkan ID dan Name. |
| [[^button/refresh|Refresh List]] | Memuat ulang daftar Submission. |


## Mempublikasikan Form

Publish adalah konfigurasi untuk mengubah Form menjadi dipublikasikan, sehingga dapat dibuka dan diisi oleh publik lewat sebuah tautan.

1. Buka halaman kerja Form
2. Klik [[^button/publish|Publish]]
3. Atur konfigurasi publikasi
4. Klik [[^button|Update]]

![[Docs/Modul Interface/Form/publish-form.png]]

| Konfigurasi | Fungsi |
| --- | --- |
| [[^field|Status]] | Mengaktifkan atau menonaktifkan publikasi. Jika berstatus Non-Active, Form hanya dapat dilihat dan tidak dapat dikirim. |
| [[^field|Link]] | Tautan Form publik. Klik [[^button|Copy]] untuk menyalin, atau [[^button|Open New Tab]] untuk membukanya di tab baru. |
| [[^field|Language]] | Bahasa tampilan Form publik. |
| [[^field|Single Submission]] | Jika aktif, setiap perangkat hanya dapat mengirim Form satu kali. |

>**note** Perubahan konfigurasi tidak memengaruhi Submission yang sudah masuk
> Mengubah [[^field|Status]] atau [[^field|Single Submission]] hanya berlaku untuk pengiriman berikutnya.

## Praktik Terbaik

- **Mulai dari Binding.** Tentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] dan [[Docs/Tipe Data/Column]] tujuan sebelum menyusun [[#Memahami Elemen|Elemen]], agar setiap Elemen Input terikat ke kolom yang tepat.
- **Gunakan Layout untuk tata letak.** Letakkan Elemen Display dan Elemen Input di dalam [[#Elemen Layout|Layout]] agar susunan Form rapi dan mudah dikelola.
- **Gunakan Page untuk memecah isian panjang.** Bagi Form yang panjang ke beberapa [[#Mengelola Page Form|Page]] agar pengisi tidak kewalahan.
- **Uji sebelum dibagikan.** Periksa tampilan di [[#Mode View dan Edit Mode|View]], lalu aktifkan [[^field|Status]] dan salin [[^field|Link]] di [[#Mempublikasikan Form|Publish]] hanya setelah Form siap.
- **Pantau Submission secara berkala.** Gunakan [[#Mengelola Submission|Submission List]] untuk memeriksa Submission berstatus Failure.

## Batasan dan Catatan

- [[#Mode View dan Edit Mode|Edit Mode]] hanya dapat diaktifkan bila [[^field|Data Access]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mengizinkan.
- Menghapus Form menghapus templat (Page, Elemen, dan Binding) beserta riwayat Submission, tetapi data yang sudah tersimpan di [[Docs/Modul Data/Table/Apa itu Table|Table]] tidak langsung terhapus.
- Tautan Publish menjadi tidak valid setelah Form dihapus, dan pengisi yang sedang mengisi Form publik akan mengalami *error* saat mengirim.
- Form hanya dapat disubmit setelah pengisi mencapai Page terakhir pada [[#Mengelola Page Form|Form Flow]].
- Menghapus Elemen Layout menghapus semua Elemen di dalamnya.
- Jika [[^field|Status]] berstatus Non-Active, Form publik hanya dapat dilihat dan tidak dapat dikirim.
- [[^field|Single Submission]] membatasi pengiriman per perangkat, bukan per orang.
- Tombol [[^button/edit|Edit]] hanya mengubah atribut Form, bukan isi Form.
- Start Building dan informasi Binding hanya tampil di [[#Mode View dan Edit Mode|Edit Mode]].

## TL:DR

- **Definisi.** [[#Apa itu Form?|Form]] adalah komponen untuk menginput, melihat, dan mengubah data secara terstruktur, serta dapat dibagikan kepada publik.
- **Antarmuka.** [[#Antarmuka Form|Bilah navigasi]] berisi [[^button/edit|Edit]], [[^button/publish|Publish]], toggle [[^field|mode]], [[^button/save|Save]], [[^button/refresh|Refresh]], dan [[^button/submission|Informasi Submission]].
- **Menyusun.** Tambahkan [[#Mengelola Page Form|Page]], lalu susun isinya dari [[#Memahami Elemen|Elemen]] Layout, Display, dan Input di [[#Mode View dan Edit Mode|Edit Mode]].
- **Menghubungkan data.** [[#Binding Form|Binding]] mengikat Elemen ke [[Docs/Modul Data/Table/Apa itu Table|Table]], [[Docs/Tipe Data/Column]], dan [[Docs/Tipe Data/Row]] agar isian tersimpan di tempat yang tepat.
- **Membagikan dan memantau.** [[#Mempublikasikan Form|Publish]] membagikan Form lewat tautan, dan [[#Mengelola Submission|Submission List]] memantau pengiriman.
- **Hati-hati.** Menghapus Form menghapus templat (Page, Elemen, dan Binding) beserta riwayat Submission, tautan Publish menjadi tidak valid, dan publik yang sedang mengisi akan *error* saat mengirim.
