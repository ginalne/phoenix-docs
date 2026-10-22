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
        priority: 4
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
| [[#Memahami Elemen|Elemen]] | Satu objek penyusun isi Form, misalnya teks, tabel, atau kolom isian. |
| [[#Elemen Layout|Layout]] | Kategori Elemen yang berfungsi sebagai templat tempat Elemen lain diletakkan. |
| [[#Elemen Display|Display]] | Kategori Elemen yang menampilkan informasi, baik statis maupun hasil dari nilai Binding. |
| [[#Elemen Input|Input]] | Kategori Elemen untuk mengisi atau menampilkan informasi yang berlaku pada Binding. |
| [[#Binding Form|Binding]] | Ikatan antara Elemen dan data di [[Docs/Modul Data/Table/Apa itu Table|Table]] agar isian dan hasil akhirnya sesuai. |
| [[#Mode View dan Edit Mode|Edit Mode]] | Mode untuk menyusun Form, termasuk melihat informasi Binding dan konfigurasi Elemen. |
| [[#Mempublikasikan Form|Publish]] | Konfigurasi untuk membagikan Form kepada publik. |
| [[#Mengelola Submission|Submission]] | Catatan setiap pengiriman Form, dengan status sukses, menunggu, atau gagal. |

Selengkapnya tentang penjelasan khusus setiap Elemen dapat dilihat pada halaman masing-masing di [[#Memahami Elemen]].

## Cara Kerja Form

Form tersusun dari [[#Mengelola Page Form|Page]], setiap Page tersusun dari [[#Memahami Elemen|Elemen]], dan Elemen yang diikat lewat [[#Binding Form|Binding]] menghubungkan isian Form ke [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]].

```mermaid
flowchart LR
  A["Form"] -->|&nbsp;Memiliki&nbsp;| B["Page"]
  B -->|&nbsp;Tersusun dari&nbsp;| C["Elemen"]
  C -.->|&nbsp;Binding&nbsp;| D["Row"]
  A -.->|&nbsp;Publish&nbsp;| E["Pengguna publik"]
  E -->|&nbsp;Submission&nbsp;| D
```

## Membuat Form

![[Docs/Modul Interface/Form/add-form.png]]
1. Buka folder tempat Form akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Interface]] ➜ [[^field/form|Form]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Klik [[^button|Create]]

>**success** Form berhasil dibuat
> Form yang baru dibuat belum memiliki Page. Tambahkan Page di [[#Mengelola Page Form]], lalu susun isinya dengan [[#Mengelola Elemen Form|Elemen]].

## Mengubah Form

1. Buka halaman kerja Form
2. Klik [[^button/edit|Edit]]
3. Ubah [[^field|Name]] atau [[^field|Description]]
4. Klik [[^button|Update]]

Tombol [[^button/edit|Edit]] di sini hanya mengubah atribut Form. Untuk mengubah isi Form (Page dan Elemen), gunakan [[#Mode View dan Edit Mode|Edit Mode]].

## Menyegarkan Form

Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.

## Menghapus Form

1. Buka folder yang berisi Form di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan Form ➜ [[^button/delete|Delete]]
3. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Dampak penghapusan Form
> Menghapus Form akan menghapus templat Form dan riwayat Submission-nya. Data yang sudah tersimpan di [[Docs/Modul Data/Table/Apa itu Table|Table]] tidak langsung terhapus.
> Jika publik sedang mengisi Form yang dipublikasikan, mereka akan mengalami *error* saat mencoba mengirim.

<!--
  * [TODO] Konfirmasi arti "templat Form" pada dampak penghapusan: apakah maksudnya susunan Page dan Elemen? Konfirmasi juga apakah tautan Publish langsung tidak dapat dibuka setelah Form dihapus.
    Jawaban : Templat form adalah page dan Elemen, termasuk binding yang sudah dipetakan. tautan publish akan invalid ketika form dihapus.
-->

## Antarmuka Form

![[Docs/Modul Interface/Form/interface-form.png]]
Halaman kerja Form terdiri dari bilah navigasi di bagian atas, area kerja di bagian tengah, dan panel [[^field|form flow]] di bagian bawah yang menampilkan daftar [[#Mengelola Page Form|Page]].

### Bilah navigasi Form terdiri dari:

| Tombol | Fungsi |
| --- | --- |
| Judul Form | Menampilkan ikon Form dan nama Form. |
| [[^button/edit|Edit]] | Mengubah atribut Form ([[^field|Name]] dan [[^field|Description]]). Lihat [[#Mengubah Form]]. |
| [[^button/publish|Publish]] | Membuka konfigurasi publikasi Form. Lihat [[#Mempublikasikan Form]]. |
| [[^field|mode]] | Berpindah antara [[^value/radio|View]] dan [[^value/radio|Edit]]. Lihat [[#Mode View dan Edit Mode]]. |
| [[^button/save|Save]] | Menyimpan perubahan isi Form. Aktif saat ada perubahan, dan perubahan juga tersimpan otomatis (*auto save*) setelah sekitar 3 detik. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan Form. |
| [[^button/submission|Informasi Submission]] | Menampilkan jumlah Submission sukses, menunggu, dan gagal. Klik untuk membuka [[#Mengelola Submission|Submission List]]. |

>**note** Perbedaan Icon
>Dalam mode dekstop tombol [[button/submission|Submission]]sedikit berbeda, tombol terlihat dengan susunan informasi submission yaitu submitted, waiting dan failure

> **warning** Harap hati-hati
> Saat melakukan[[button/refresh|Refresh]] halaman, pastikan bahwa perubahan Anda saat ini sudah disimpan. Jika tombol [[button/save|Save]]masih aktif, berarti perubahan belum disimpan.

### Mode View dan Edit Mode

Form memiliki dua mode yang dipilih lewat toggle [[^field|mode]]:

| Mode | Fungsi |
| --- | --- |
| [[^value/radio|View]] | Melihat Form tanpa dapat mengubah isinya. Pada mode ini Form tampil sebagai *Read Only*. |
| [[^value/radio|Edit]] | Menyusun Form: menambah [[#Mengelola Page Form|Page]], mengelola [[#Mengelola Elemen Form|Elemen]], dan melihat informasi [[#Binding Form|Binding]]. |

>**note** Syarat beralih ke Edit Mode
> Anda hanya dapat beralih ke Edit Mode jika [[^field|Data Access]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mengizinkan perubahan Form (lihat [[#Hak Akses Form]]).

### Interaksi Antarmuka Form

| Fungsi | Aksi |
| --- | --- |
| Memfokuskan Elemen (Edit Mode) | Klik kiri pada Elemen. _Card_ konfigurasi dan _header_ elemen akan tampil. |

## Mengelola Page Form

Form dapat memiliki beberapa Page. Daftar Page tampil pada panel [[^field|form flow]] di bagian bawah halaman kerja. Form baru yang belum memiliki Page menampilkan keterangan [[^field|No Page]].

### Start Building

Pada setiap Page yang masih kosong, Edit Mode menampilkan informasi **Start Building**. Informasi ini hanya tampil di [[#Mode View dan Edit Mode|Edit Mode]].

![[Docs/Modul Interface/Form/fresh-form.png]]

| Bagian | Fungsi |
| --- | --- |
| [[^field|Page Name]] | Nama Page. Bawaannya `Page 1`. |
| Basic | Pilihan layout dasar: [[^field|Card Layout]], [[^field|Full Layout]], [[^field|Split Layout]], dan [[^field|Accordion Layout]]. Layout adalah [[#Elemen Layout|Elemen Layout]] yang menjadi fondasi isi Page. |
| Template | Bagian untuk mempermudah *styling*, sama halnya dengan memakai Elemen yang tersedia lalu mengubah konfigurasi gayanya. Saat ini masih kosong ([[^field|Template is empty]]). |

### Menambahkan Page

1. Aktifkan [[#Mode View dan Edit Mode|Edit Mode]]
2. Klik [[^button/add|Add Page]] pada panel [[^field|form flow]]
3. Isi [[^field|Page Name]]
4. Pilih salah satu layout pada bagian Basic

<!--
  * [TODO] Konfirmasi langkah Menambahkan Page di atas (apakah Add Page langsung menampilkan Start Building). Konfirmasi juga cara mengganti nama, menghapus, dan mengurutkan Page, serta arti nama panel [[^field|form flow]] dan arti ikon peringatan pada tab Page.
    Jawaban : Form Flow artinya alur form, halaman paling kiri adalah halaman yang pertama kali tampil, sedangkan form dapat disubmit ketika sudah mencapai halaman akhir.
-->

## Mengelola Elemen Form

### Memahami Elemen

Elemen adalah satu objek penyusun isi Form. Setiap bagian yang Anda lihat di Form, mulai dari judul, kolom isian, hingga tabel, adalah sebuah Elemen. Anda menyusun Form dengan menambahkan Elemen, mengaturnya, lalu mengikatnya ke data lewat [[#Binding Form|Binding]].

Elemen dikelompokkan dalam tiga kategori:

| Kategori | Fungsi | Elemen |
| --- | --- | --- |
| [[#Elemen Layout|Layout]] | Menjadi templat tempat Elemen lain diletakkan. | [[Docs/Modul Interface/Form/Layout/Card/Penjelasan|Card]], [[Docs/Modul Interface/Form/Layout/Full/Penjelasan|Full]], [[Docs/Modul Interface/Form/Layout/Split/Penjelasan|Split]], [[Docs/Modul Interface/Form/Layout/Accordion/Penjelasan|Accordion]] |
| [[#Elemen Display|Display]] | Menampilkan informasi. | [[Docs/Modul Interface/Form/Display/Text/Penjelasan|Text]], [[Docs/Modul Interface/Form/Display/Table/Penjelasan|Table]], [[Docs/Modul Interface/Form/Display/Tooltip/Penjelasan|Tooltip]], [[Docs/Modul Interface/Form/Display/Qr/Penjelasan|Qr]], [[Docs/Modul Interface/Form/Display/Chrono/Penjelasan|Chrono]] |
| [[#Elemen Input|Input]] | Mengisi atau menampilkan informasi yang berlaku pada Binding. | [[Docs/Modul Interface/Form/Input/Basic/Penjelasan|Basic]], [[Docs/Modul Interface/Form/Input/Quiz/Penjelasan|Quiz]], [[Docs/Modul Interface/Form/Input/Table/Penjelasan|Table]], [[Docs/Modul Interface/Form/Input/List/Penjelasan|List]] |

Penjelasan keunikan masing-masing Elemen ada di halaman Elemen tersebut.

### Elemen Layout

Layout berfungsi sebagai templat. Elemen Layout adalah satu-satunya kategori yang memiliki *field* [[^field|Type something here to add...]], yaitu tempat Anda menambahkan Elemen lain ke dalamnya. Dengan begitu, Layout mengatur tata letak, sedangkan isinya diisi oleh Elemen Display dan Elemen Input.

### Elemen Display

Display berfungsi menampilkan informasi. Informasi yang ditampilkan dapat berupa isi statis (misalnya judul atau keterangan), atau hasil dari [[Docs/Tipe Data/Expression]] terhadap nilai Binding (misalnya nilai total).

### Elemen Input

Input berfungsi untuk mengisi atau menampilkan informasi yang berlaku pada Binding. Pada Form yang dipublikasikan, Elemen Input inilah yang diisi oleh pengguna dan dikirim sebagai Submission.

### Menambahkan Elemen

1. Aktifkan [[#Mode View dan Edit Mode|Edit Mode]]
2. Buka Page yang akan diisi
3. Klik [[^field|Type something here to add...]] pada Elemen Layout
4. Pilih Elemen yang akan ditambahkan

<!--
  * [TODO] Konfirmasi cara memilih Elemen pada langkah Menambahkan Elemen (apakah mengetik nama Elemen, memilih dari daftar, atau cara lain).
    Jawaban : Cara memilih elemen adalah dengan memilih dalam dropdown (ketika focus input “type something here to add...”), user juga dapat mengetik untuk mencari elemen yang diinginkan.
-->

### Mengonfigurasi Elemen

Klik kiri pada Elemen di [[#Mode View dan Edit Mode|Edit Mode]] untuk memfokuskannya. Setelah itu muncul dua hal:

- **Properties Panel**, yang panel untuk mengatur properti elemen secara rinci, seperti Binding, State, Validators, Attributes, Children dan Parent.
- **Header Toolbar**, yaitu bilah pintasan aksi yang selalu memiliki tombol [[^button/delete|Remove]] untuk menghapus Elemen.
- **Layout Panel**, yaitu Panel untuk mengatur ukuran, padding, margin dan beberapa _styling_ elemen.

![[Docs/Modul Interface/Form/Elemen-config-form.png]]

<!--
  * [TODO] Letakkan gambar card konfigurasi dan header Elemen (Elemen-config-form.png) di sini. Anotasi yang disarankan: (1) card konfigurasi, (2) bagian Binding, (3) bagian State, (4) daftar Children, (5) header Elemen dan tombol Remove.
  * [TODO] Gambar contoh memuat nama Elemen milik penulis. Ganti dengan penamaan generik.
-->

| Bagian card | Fungsi |
| --- | --- |
| [[^field|Binding]] | Mengikat Elemen ke data. Lihat [[#Binding Form]]. |
| [[^field|State]] | Mengatur kondisi Elemen, misalnya [[^field|Visible]] untuk menampilkan atau menyembunyikan Elemen. |
| Attribute | Mengatur pengaturan khusus Elemen, termasuk gayanya. Isinya berbeda-beda pada setiap Elemen. |
| Children atau Parent | Menampilkan Elemen yang berada di dalam Elemen ini (*children*), atau Elemen tempat Elemen ini berada (*parent*). |

<!--
  * [TODO] Konfirmasi isi bagian Attribute (apakah gaya memakai nama class seperti [[Docs/Styling/Styling Class]]) dan penjelasan pilihan Type pada Binding ([[^value/radio|table]] dan [[^value/radio|pivot]]).
-->

### Menghapus Elemen

1. Aktifkan [[#Mode View dan Edit Mode|Edit Mode]]
2. Klik kiri Elemen yang akan dihapus
3. Klik [[^button/delete|Remove]] pada header Elemen

>**warning** Dampak penghapusan Elemen
> Menghapus Elemen Layout dapat ikut menghapus Elemen yang berada di dalamnya. Binding yang dipakai Elemen tersebut juga terputus dari Form.

<!--
  * [TODO] Konfirmasi apakah Elemen di dalam Layout ikut terhapus saat Layout dihapus, dan apakah ada konfirmasi sebelum Remove.
-->

## Binding Form

Binding adalah ikatan berjenjang yang menghubungkan Elemen dengan data. Tujuannya agar isian pengguna dan hasil akhirnya tersimpan pada [[Docs/Tipe Data/Row]] dan relasi yang tepat di [[Docs/Modul Data/Table/Apa itu Table|Table]].

Secara umum, urutannya seperti ini:

1. Elemen paling atas diikat ke [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber datanya.
2. Elemen di dalamnya diikat ke [[Docs/Tipe Data/Column]] pada Table tersebut, sehingga setiap *field* tahu ke kolom mana isiannya disimpan.
3. Elemen yang mewakili data turunan diikat ke relasi dari Row induknya.

Informasi Binding dapat dilihat di [[#Mode View dan Edit Mode|Edit Mode]] sebagai label pada Elemen. Klik kiri Elemen untuk memfokuskannya dan melihat pengaturan [[^field|Binding]] pada card konfigurasi.

<!--
  * [TODO] Konfirmasi urutan Binding di atas, terutama pengikatan ke relasi Row induk dan arti pilihan Type [[^value/radio|table]] dan [[^value/radio|pivot]]. Pertimbangkan membuat subhalaman `Docs/Modul Interface/Form/Binding` bila pembahasannya makin panjang.
-->

## Mengelola Submission

Setiap kali Form dikirim, Phoenix mencatatnya sebagai Submission dengan status sukses (*Submitted*), menunggu (*Waiting*), atau gagal (*Failure*). Ringkasan jumlahnya ada pada [[^button/submission|Informasi Submission]] di bilah navigasi.

Klik [[^button/submission|Informasi Submission]] untuk membuka **Submission List** di sebelah kanan.

![[Docs/Modul Interface/Form/submission-list-form.png]]

<!--
  * [TODO] Letakkan gambar Submission List (submission-list-form.png) di sini. Anotasi yang disarankan: (1) filter waktu, (2) [[^button/refresh|Refresh List]], (3) kolom pencarian, (4) grafik, (5) daftar Submission.
  * [TODO] Gambar contoh memuat nama pengisi yang sebenarnya. Ganti dengan data contoh atau sensor sebelum dipublikasikan.
-->

| Bagian | Fungsi |
| --- | --- |
| Grafik | Menampilkan jumlah Submission dari waktu ke waktu untuk status Submitted, Waiting, dan Failure. Arahkan kursor ke grafik untuk melihat rinciannya pada tanggal tertentu. |
| Daftar | Menampilkan setiap Submission dengan kolom [[^field|ID/Name]], [[^field|Status/ID]], [[^field|Start At]], dan [[^field|Updated At]]. |
| Filter waktu | Memfilter data dengan pilihan [[^value/radio|All Time]], [[^value/radio|This Month]], [[^value/radio|This Week]], dan [[^value/radio|Today]]. |
| [[^field|Search Submission...]] | Mencari Submission. |
| [[^button/refresh|Refresh List]] | Memuat ulang daftar Submission. |

<!--
  * [TODO] Konfirmasi isi baris Submission saat dibuka (ikon panah di kiri baris), fungsi tombol salin di samping ID, dan fungsi ikon panel di kiri judul Submission List.
  * [TODO] Konfirmasi cakupan [[^field|Search Submission...]] (kolom apa saja yang dicari).
-->

## Mempublikasikan Form

Publish adalah konfigurasi untuk mengubah Form menjadi dipublikasikan, sehingga dapat dibuka dan diisi oleh publik lewat sebuah tautan.

1. Buka halaman kerja Form
2. Klik [[^button/publish|Publish]]
3. Atur konfigurasi publikasi
4. Klik [[^button|Update]]

![[Docs/Modul Interface/Form/publish-form.png]]

<!--
  * [TODO] Letakkan gambar dialog Publish (publish-form.png) di sini. Anotasi yang disarankan: (1) [[^field|Status]], (2) [[^field|Link]], (3) [[^field|Language]], (4) [[^field|Single Submission]].
  * [TODO] Gambar contoh memuat nama Form milik penulis. Ganti dengan penamaan generik.
-->

| Konfigurasi | Fungsi |
| --- | --- |
| [[^field|Status]] | Mengaktifkan atau menonaktifkan publikasi. Jika berstatus Non-Active, Form hanya dapat dilihat dan tidak dapat dikirim. |
| [[^field|Link]] | Tautan Form publik. Klik [[^button|Copy]] untuk menyalin, atau [[^button|Open New Tab]] untuk membukanya di tab baru. |
| [[^field|Language]] | Bahasa tampilan Form publik. |
| [[^field|Single Submission]] | Jika aktif, setiap perangkat hanya dapat mengirim Form satu kali. |

>**note** Perubahan konfigurasi tidak memengaruhi Submission yang sudah masuk
> Mengubah [[^field|Status]] atau [[^field|Single Submission]] hanya berlaku untuk pengiriman berikutnya.

<!--
  * [TODO] Konfirmasi catatan di atas (pengaruh perubahan konfigurasi Publish terhadap Submission yang sudah masuk). Konfirmasi juga pilihan lain pada [[^field|Language]] dan apakah dialog Publish perlu dipindah menjadi subhalaman `Docs/Modul Interface/Form/Publish`.
-->

## Hak Akses Form

Akses Form di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mengikuti tiga jenis akses berikut:

| Jenis akses | Cakupan pada Form |
| --- | --- |
| [[^field|Comp. Access]] | Melihat ([[^field|Visible]]), menambah ([[^field|Add]]), mengubah atribut ([[^field|Update]]), dan menghapus ([[^field|Delete]]) komponen Form. |
| [[^field|Data Access]] | Setiap perubahan Elemen dan atributnya di dalam Form, termasuk beralih ke [[#Mode View dan Edit Mode|Edit Mode]]. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Data Access]]. |
| [[^field|Function Access]] | [[^field|View Publish]] untuk melihat konfigurasi publikasi (misalnya menyalin tautan), dan [[^field|Publish]] untuk memperbarui konfigurasi publikasi. |

<!--
  * [TODO] Konfirmasi pemetaan Data Access (Add, Update, Delete) ke aksi di Form: aksi apa yang membutuhkan [[^field|Add]], [[^field|Update]], dan [[^field|Delete]] (misalnya Edit Mode dan Remove Elemen).
-->

## Contoh Penggunaan

**Pendaftaran peserta kegiatan secara daring**

Panitia sebuah kegiatan ingin peserta mendaftar sendiri lewat tautan, tanpa harus mencatat data satu per satu. Dengan Form, pendaftar mengisi data di perangkat mereka, data langsung masuk ke Table, dan panitia mendapat pemberitahuan otomatis setiap ada pendaftar baru.

**Komponen yang terlibat**

| Komponen | Peran |
| --- | --- |
| [[^field/form|Form Pendaftaran]] | Tempat pendaftar mengisi data lewat tautan publik. |
| [[^field/table|Data Pendaftar]] | Menyimpan setiap pendaftaran sebagai Row lewat Binding. |
| [[^field/flow|Notifikasi Pendaftaran]] | Mengirim pemberitahuan ke panitia saat ada Row baru. |

<!--
  * [TODO] Nama Form, Table, dan Flow pada contoh ini hanya penamaan generik. Sesuaikan dengan gambar yang Anda buat.
  * [TODO] Konfirmasi asumsi bahwa Submission Form menambahkan Row baru di Table sehingga dapat memicu Flow Block Table Row Event, dan konfirmasi nama Event yang dipakai pada diagram.
-->

**Alur di Flow**

```mermaid
flowchart LR
  A@{ shape: database, label: "**Table**<br/>Data Pendaftar" } -.->|&nbsp;Row Baru&nbsp;| B@{ shape: rounded, label: "**Table Row Event**" }
  B -->|"&nbsp;**[Row]**&nbsp;"| C@{ shape: rounded, label: "**HTTP Request**" }
  C --> D@{ shape: processes, label: "Panitia menerima<br/>pemberitahuan" }
  D --> E@{ shape: circle, label: "Selesai" }
```

| Langkah | Flow Block | Peran dalam alur | Hasil |
| --- | --- | --- | --- |
| 1 | [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event]] | Memicu alur saat ada Row baru di [[Docs/Modul Data/Table/Apa itu Table|Table]]. | Alur berjalan dengan data Row pendaftar. |
| 2 | [[Docs/Modul Logic/Flow/Flow Block/Modular/HTTP Request|HTTP Request]] | Mengirim data pendaftar ke sistem pemberitahuan. | Panitia menerima pemberitahuan. |

**Hasil yang dirasakan**

- Pendaftar cukup membuka tautan dan mengisi Form, tanpa perlu akun.
- Data pendaftar tersimpan rapi di [[Docs/Modul Data/Table/Apa itu Table|Table]] tanpa input ulang oleh panitia.
- Panitia langsung tahu setiap ada pendaftar baru lewat [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

**Ide skenario lain**

| Jenis kebutuhan | Contoh integrasi |
| --- | --- |
| Pengumpulan data | Survei kepuasan yang hasilnya dirangkum di [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]]. |
| Permintaan layanan | Form permintaan yang otomatis membuat tugas bagi tim lewat [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. |
| Kuis | Form dengan Elemen [[Docs/Modul Interface/Form/Input/Quiz/Penjelasan|Quiz]] untuk menguji pemahaman peserta pelatihan. |
| Pelaporan | Form laporan lapangan yang datanya tampil di [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]] sesuai statusnya. |

Dengan Form, pengumpulan data dari publik tersambung langsung ke data dan otomasi di Phoenix, sehingga pendaftaran tidak berhenti di formulir, tetapi langsung ditindaklanjuti.

## Praktik Terbaik

- **Mulai dari Binding.** Tentukan [[Docs/Modul Data/Table/Apa itu Table|Table]] dan [[Docs/Tipe Data/Column]] tujuan sebelum menyusun [[#Memahami Elemen|Elemen]], agar setiap Elemen Input terikat ke kolom yang tepat.
- **Gunakan Layout untuk tata letak.** Letakkan Elemen Display dan Elemen Input di dalam [[#Elemen Layout|Layout]] agar susunan Form rapi dan mudah dikelola.
- **Gunakan Page untuk memecah isian panjang.** Bagi Form yang panjang ke beberapa [[#Mengelola Page Form|Page]] agar pengisi tidak kewalahan.
- **Uji sebelum dibagikan.** Periksa tampilan di [[#Mode View dan Edit Mode|View]], lalu aktifkan [[^field|Status]] dan salin [[^field|Link]] di [[#Mempublikasikan Form|Publish]] hanya setelah Form siap.
- **Pantau Submission secara berkala.** Gunakan [[#Mengelola Submission|Submission List]] untuk memeriksa Submission berstatus Failure.

>**success** Form siap dibagikan
> Setelah semua [[#Memahami Elemen|Elemen]] terikat dan [[^field|Status]] aktif, tautan [[^field|Link]] dapat dibagikan kepada publik.

## Batasan dan Catatan

- [[#Mode View dan Edit Mode|Edit Mode]] hanya dapat diaktifkan bila [[^field|Data Access]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mengizinkan.
- Menghapus Form menghapus templat dan riwayat Submission, tetapi data yang sudah tersimpan di [[Docs/Modul Data/Table/Apa itu Table|Table]] tidak langsung terhapus.
- Pengisi yang sedang mengisi Form publik akan mengalami *error* saat mengirim jika Form dihapus.
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
- **Hati-hati.** Menghapus Form menghapus templat dan riwayat Submission, dan publik yang sedang mengisi akan *error* saat mengirim.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apa bedanya tombol Edit dan toggle mode?**
> Tombol [[^button/edit|Edit]] mengubah atribut Form ([[^field|Name]] dan [[^field|Description]]), sedangkan toggle [[^field|mode]] berpindah antara [[^value/radio|View]] dan [[^value/radio|Edit]] untuk menyusun isi Form.
> **Mengapa saya tidak bisa beralih ke Edit Mode?**
> Beralih ke Edit Mode membutuhkan [[^field|Data Access]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] yang mengizinkan perubahan Form. Hubungi pengelola Workspace Anda.
> **Apakah saya harus menekan Save setiap kali mengubah Form?**
> Tidak harus. Perubahan tersimpan otomatis setelah sekitar 3 detik, dan Anda juga dapat menekan [[^button/save|Save]] secara manual.
> **Apakah satu orang hanya bisa mengirim Form sekali?**
> Hanya bila [[^field|Single Submission]] aktif, dan pembatasannya berlaku per perangkat.
> **Apa yang terjadi pada data jika Form dihapus?**
> Templat dan riwayat Submission terhapus, tetapi data yang sudah tersimpan di [[Docs/Modul Data/Table/Apa itu Table|Table]] tidak langsung terhapus.
> **Di mana penjelasan setiap Elemen?**
> Setiap Elemen punya halaman sendiri, misalnya [[Docs/Modul Interface/Form/Layout/Card/Penjelasan|Card]] dan [[Docs/Modul Interface/Form/Input/Basic/Penjelasan|Basic]]. Lihat daftarnya di [[#Memahami Elemen]].

<!--
  * [TODO] Halaman yang diusulkan dan belum ada: `Docs/Modul Interface/Pengenalan`, `Docs/Modul Interface/Form/<Tipe>/<Nama Elemen>/Penjelasan` (13 Elemen), `Docs/Modul Interface/Table View/Apa itu Table View`, `Docs/Modul Interface/Kanban/Apa itu Kanban`, dan `Docs/Modul Developer/Workspace/Data Access`. Pastikan path-nya sesuai struktur Anda.
-->


## Antar Muka

Berikut adalah tampilan form saat pertama kali dibuat:

![[Docs/Modul Interface/Form/form-new.png]]
Berikut penjelasan terkait beberapa fungsi halaman kerja Form:

| | |
|-------------------|---------------------------------------------------------------------------------------------------|
|[[field/form|Judul Form]]| Ikon Form dalam phoenix serta [[field|Header Name]] Form.  
| [[button/edit|Edit]]  | Tombol yang berfungsi untuk membuka modal Edit Form untuk memperbarui nama dan deskripsi Form. |
| [[button/publish|Publish]]  | Tombol yang berfungsi untuk membuka modal Publish Form untuk memperbarui konfigurasi publish Form. |
|  [[mode/view|View]] | Saklar dengan mode View agar konten Form dapat di sunting. |
|  [[mode/edit|Edit]] | Saklar dengan mode Edit agar  konten Form hanya bisa dilihat |
| [[button/save|Save]]  | Tombol yang berfungsi untuk menyimpan perubahan Form. |
| [[button/refresh|Refresh]]  | Tombol yang berfungsi untuk menyegarkan lagi halaman Form. |
|[[button/submission|Submission]]| Tombol yang berfungsi untuk membuka bilik submission.
