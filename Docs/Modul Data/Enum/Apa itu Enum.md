---
    status: release
    title: Apa itu Enum?
    description: Enum adalah komponen Master Data di modul Data untuk menyimpan daftar pilihan, menu, opsi, atau kategori yang dapat dipakai ulang oleh komponen lain.
    pageDecoration:
      tree:
        priority: 4
---
# Apa itu Enum?

>**note** Enum merupakan salah satu komponen dalam modul [[Docs/Modul Data/Pengenalan|Data]] di Phoenix.

Enum adalah komponen yang dapat digunakan sebagai deret data atau yang sering dikenal dengan *Master Data*. Data ini berfungsi sebagai pilihan, menu, opsi, ataupun kategori. Setiap Enum memiliki banyak [[Docs/Tipe Data/EnumData|EnumData]] di dalamnya.

Dengan Enum, Anda mengelola daftar pilihan di satu tempat saja. Field di komponen lain tinggal merujuk ke Enum tersebut, sehingga pilihan selalu seragam dan perubahan cukup dilakukan satu kali.


## Mengapa Menggunakan Enum?

- **Satu sumber pilihan.** Daftar opsi, menu, atau kategori dikelola di satu komponen dan dipakai ulang oleh banyak field.
- **Pilihan yang seragam.** [[^field|Name]] tidak boleh sama di dalam satu Enum, sehingga tidak ada pilihan ganda yang membingungkan.
- **Kontrol per baris.** Anda menentukan [[Docs/Tipe Data/EnumData]] mana yang tampil sebagai pilihan dengan kolom [[^field|Selectable]].
- **Value fleksibel.** Kolom [[^field|Value]] mengikuti [[^field|Format]] yang Anda pilih pada konfigurasi Enum.
- **Siap terhubung.** Enum dapat dihubungkan dengan [[Docs/Event/Apa itu Event|Event]] dan logika di [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] sehingga perubahan pilihan dapat memicu otomasi.

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[Docs/Tipe Data/EnumData\|EnumData]] | Satu baris data di dalam Enum yang berisi [[^field\|Name]], [[^field\|Description]], [[^field\|Value]], dan [[^field\|Selectable]]. |
| [[#Membaca Baris EnumData\|Selectable]] | Penanda apakah sebuah [[Docs/Tipe Data/EnumData]] tampil sebagai pilihan pada field berformat [[Docs/Tipe Data/EnumData]]. |
| [[#Konfigurasi Enum\|Format]] | Format data yang menentukan bentuk kolom [[^field\|Value]] pada setiap baris. |
| [[#Konfigurasi Enum\|Header]] | Header untuk [[^field\|Format]] yang membutuhkan tipe data pendamping. |
| [[Docs/Modul Data/Enum/Konfigurasi Tegas\|Strict On Selected]] | Atribut penting Enum yang mengatur ketegasan pilihan. Selengkapnya lihat [[Docs/Modul Data/Enum/Konfigurasi Tegas]]. |

## Cara Kerja Enum

Enum menyimpan banyak [[Docs/Tipe Data/EnumData]], lalu field berformat [[Docs/Tipe Data/EnumData]] di komponen lain menampilkan [[Docs/Tipe Data/EnumData]] tersebut sebagai daftar pilihan.

```mermaid
flowchart LR
  A["Enum"] -->|"&nbsp;berisi banyak&nbsp;"| B["EnumData"]
  C["Field berformat EnumData"] -.->|"&nbsp;merujuk ke&nbsp;"| A
  B -->|"&nbsp;tampil sebagai pilihan&nbsp;<br>&nbsp;(Selectable = Yes)&nbsp;"| C
```

Hanya [[Docs/Tipe Data/EnumData]] dengan [[^field|Selectable]] bernilai [[^value/boolean/true]] yang tampil pada daftar pilihan. [[Docs/Tipe Data/EnumData]] dengan nilai [[^value/boolean/false]] tidak tampil sebagai pilihan di field, tetapi tetap dapat dipakai di tempat lain.

## Konfigurasi Enum

Setiap Enum memiliki atribut berikut:

| Atribut | Penjelasan |
| --- | --- |
| [[^field\|Name]] | Nama Enum. Tidak boleh sama dengan komponen sejenis di folder yang sama. |
| [[^field\|Description]] | Keterangan singkat tentang kegunaan Enum. |
| [[^field\|Format]] | Format data untuk kolom [[^field\|Value]] pada setiap baris. Format dapat diubah setelah Enum dibuat (lihat [[#Mengubah Enum]]). |
| [[^field\|Header]] | Header untuk [[^field\|Format]] dengan tipe data yang membutuhkan header. Bernilai N/A jika [[^field\|Format]] tidak membutuhkannya. |
| [[^field\|Strict On Selected]] | Pengaturan ketegasan pilihan. Selengkapnya lihat [[Docs/Modul Data/Enum/Konfigurasi Tegas]]. |

Pasangan tipe data [[^field|Format]] dan [[^field|Header]]:

| Tipe data Format | Tipe data Header |
| --- | --- |
| [[Docs/Tipe Data/EnumData\|EnumData]] | [[Docs/Tipe Data/Enum\|Enum]] |
| [[Docs/Tipe Data/Column\|Column]] | [[Docs/Tipe Data/Table\|Table]] |
| [[Docs/Tipe Data/Row\|Row]] | [[Docs/Tipe Data/Table\|Table]] |
| [[Docs/Tipe Data/TableData\|TableData]] | [[Docs/Tipe Data/Column\|Column]] |
| [[Docs/Tipe Data/Node\|Node]] | [[Docs/Tipe Data/Tree\|Tree]] |
| Lainnya | N/A |

## Membuat Enum

![[Docs/Modul Data/Enum/add-enum.png]]
1. Buka folder tempat Enum akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan > [[^field/add|Add]] > [[^field|Data]] > [[^field/enum|Enum]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Pilih [[^field|Format]] dan atur [[^field|Strict On Selected]] sesuai kebutuhan
5. Klik [[^button|Create]]

>**success** Enum berhasil dibuat
> Enum yang baru dibuat belum memiliki data. Tambahkan [[Docs/Tipe Data/EnumData]] di [[#Mengelola EnumData]].

## Mengubah Enum

1. Buka halaman kerja Enum
2. Klik [[^button/edit|Edit]]
3. Ubah [[^field|Name]], [[^field|Description]], [[^field|Format]], atau [[^field|Strict On Selected]]
4. Klik [[^button|Update]]

>**warning** Mengubah [[^field|Format]]
> [[^field|Format]] masih dapat diubah meskipun Enum sudah memiliki [[Docs/Tipe Data/EnumData]]. Phoenix menampilkan peringatan terlebih dahulu, dan Anda perlu mengisi [[^field|Force Update]] untuk melanjutkan. Hasilnya dapat berupa *loss safe* (akan mencoba mengonversi nilai ke [[^field|Format]] baru, jika gagal akan muncul peringatan yang sama) atau *force* (paksa, nilai yang tidak dapat dikonversi bisa hilang). Mohon periksa [[^field|Value]] yang sudah ada sebelum melanjutkan.


## Menyegarkan Enum

Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan halaman kerja Enum.

## Menghapus Enum

1. Buka folder yang berisi Enum di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan Enum > [[^button/delete|Delete]]
3. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Dampak Menghapus Enum
> Seluruh [[Docs/Tipe Data/EnumData]] di dalam Enum ikut hilang. Sebelum menghapus, hapus terlebih dahulu relasi dari komponen lain yang menggunakan Enum ini, misalnya field berformat [[Docs/Tipe Data/EnumData]] dan [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

## Antarmuka Enum

![[Docs/Modul Data/Enum/halaman-kerja-enum.png]]

Halaman kerja Enum terdiri dari bilah navigasi di bagian atas dan tabel [[Docs/Tipe Data/EnumData]] di bagian bawah.

### Bilah navigasi Enum terdiri dari:

| Tombol | Fungsi |
| --- | --- |
| Judul Enum | Menampilkan ikon Enum dan [[^field\|Header Name]]. |
| [[^button/edit\|Edit]] | Mengubah atribut Enum (lihat [[#Mengubah Enum]]). |
| [[^button/merge\|Merge]] | Menggabungkan data. Selengkapnya lihat [[Docs/Modul Data/Enum/Merge]]. |
| [[^button/event\|Event]] | Menghubungkan [[Docs/Event/Apa itu Event\|Event]] dari Enum. Selengkapnya lihat [[Docs/Modul Data/Enum/Event]]. |
| [[^button/refresh\|Refresh]] | Memuat ulang tampilan halaman kerja. |
| [[^field\|Search Enum Data...]] | Mencari [[Docs/Tipe Data/EnumData]] di dalam Enum. |

### Membaca Baris EnumData

| Kolom | Penjelasan |
| --- | --- |
| [[^field\|Name]] | Nama [[Docs/Tipe Data/EnumData]]. Tidak boleh sama dengan [[Docs/Tipe Data/EnumData]] lain di dalam Enum yang sama. |
| [[^field\|Description]] | Keterangan [[Docs/Tipe Data/EnumData]]. |
| [[^field\|Value]] | Nilai [[Docs/Tipe Data/EnumData]]. Bentuknya mengikuti [[^field\|Format]] pada konfigurasi Enum. Ikon di header kolom menunjukkan tipe data dari [[^field\|Format]]. |
| [[^field\|Selectable]] | Menentukan apakah [[Docs/Tipe Data/EnumData]] tampil sebagai pilihan pada field. Hanya berlaku untuk field. |
| [[^field\|Action]] | Berisi tombol [[^button/save\|Save]] dan [[^button/delete\|Delete]] untuk baris tersebut. |

>**note** Tampilan [[^field|Value]] Mengikuti [[^field|Format]]
> Tampilan kolom [[^field|Value]] dapat berbeda untuk setiap [[^field|Format]]. Pada Format Password, misalnya, Value tersamarkan.

### Interaksi Antarmuka Enum

| Fungsi | Aksi |
| --- | --- |
| Menambah baris | Klik [[^button/add\|Add Row]] pada bagian bawah tabel atau pada bilah di bawahnya. Keduanya memiliki fungsi yang sama. |
| Mengubah [[^field\|Selectable]] | Klik toggle pada kolom [[^field\|Selectable]]. |
| Berpindah halaman | Gunakan [[^button\|Prev]], [[^button\|Next]], atau isi nomor halaman lalu klik [[^button\|Go]]. |
| Membaca batas halaman | Teks "Show 50 of 1 items" menunjukkan batas 50 item per halaman dan jumlah item yang ada. |

## Mengelola EnumData

### Menambahkan EnumData

1. Buka halaman kerja Enum
2. Klik [[^button/add|Add Row]]
3. Isi [[^field|Name]], [[^field|Description]], dan [[^field|Value]]
4. Atur [[^field|Selectable]]
5. Klik [[^button/save|Save]]

>**note** [[^field|Name]] Harus Unik
> [[^field|Name]] tidak boleh sama dengan [[Docs/Tipe Data/EnumData]] lain di dalam Enum yang sama.

### Mengubah EnumData

1. Ubah isian pada baris yang diinginkan
2. Klik [[^button/save|Save]] pada kolom [[^field|Action]]

Tombol [[^button/save|Save]] aktif setelah ada perubahan pada baris.

### Menghapus EnumData

1. Klik [[^button/delete|Delete]] pada kolom [[^field|Action]] di baris yang diinginkan
2. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Dampak Menghapus EnumData
> [[Docs/Tipe Data/EnumData]] yang dihapus hilang dari Enum dan tidak tampil lagi sebagai pilihan. Jika hanya ingin menyembunyikannya dari field, ubah [[^field|Selectable]] menjadi [[^value/boolean/false]] alih-alih menghapus.

## Contoh Penggunaan

**Kategori pengaduan yang seragam dan memicu tindak lanjut otomatis**

Tim layanan pelanggan menerima pengaduan dari banyak orang. Agar laporan mudah dikelompokkan dan yang mendesak segera ditangani, kategori pengaduan disimpan sebagai Master Data di Enum, lalu dipakai ulang di form dan tabel pengaduan.

**Komponen yang terlibat**

| Komponen | Peran |
| --- | --- |
| [[^field/enum\|Kategori Pengaduan]] | Menyimpan daftar kategori sebagai [[Docs/Tipe Data/EnumData]]. |
| [[^field/table\|Pengaduan]] | Menyimpan data pengaduan dengan field kategori berformat [[Docs/Tipe Data/EnumData]]. |
| [[^field/flow\|Tindak Lanjut Pengaduan]] | Menjalankan otomasi ketika pengaduan baru masuk. |

**Alur di Flow**

```mermaid
flowchart TB
  T@{ shape: database, label: "**Table**<br/>Pengaduan" } -.->|"&nbsp;Add Row&nbsp;"| E@{ shape: rounded, label: "**Table Row Event**" }
  E -->|"&nbsp;**[Row]**&nbsp;"| B@{ shape: rounded, label: "**If**<br>Kategori = Mendesak?" }
  B -->|"&nbsp;true&nbsp;"| H@{ shape: rounded, label: "**HTTP Request**" }
  H --> S@{ shape: processes, label: "Sistem lain<br/>menerima data" }
  S --> F@{ shape: circle, label: "Selesai" }
  B -.->|"&nbsp;false&nbsp;"| F
```

| Langkah | Flow Block | Peran dalam alur | Hasil |
| --- | --- | --- | --- |
| 1 | [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan\|Table Row Event]] | Aktif ketika pengaduan baru ditambahkan. | Baris pengaduan diteruskan ke alur. |
| 2 | [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan\|If]] | Memeriksa apakah kategori pengaduan adalah yang mendesak. | Alur terbagi menjadi jalur true dan false. |
| 3 | [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan\|HTTP Request]] | Mengirim data pengaduan ke sistem lain. | Sistem lain menerima data. |

<!--
  * [TODO] Mohon konfirmasi path halaman Flow Block Operator untuk tautan If pada langkah 2 (path usulan: Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan).
-->

**Hasil yang dirasakan**

- Petugas memilih kategori dari daftar yang seragam, tanpa mengetik ulang dan tanpa salah ejaan.
- Pengaduan mendesak langsung diteruskan ke sistem lain tanpa menunggu dicek manual.
- Menambah atau menonaktifkan kategori cukup dilakukan di Enum, dan semua field yang merujuk ikut diperbarui.

**Ide skenario lain**

| Jenis nilai | Contoh integrasi |
| --- | --- |
| Status pesanan | Menjadi kolom pengelompokan pada [[Docs/Modul Interface/Kanban/Apa itu Kanban\|Kanban]] dan pemicu notifikasi di [[Docs/Modul Logic/Flow/Apa itu Flow\|Flow]]. |
| Kategori produk | Menjadi pilihan di [[Docs/Modul Interface/Form/Apa itu Form\|Form]] input produk dan penyaring pada [[Docs/Modul Interface/Table View/Apa itu Table View\|Table View]]. |
| Tingkat prioritas | Menjadi dasar percabangan alur penanganan di [[Docs/Modul Logic/Flow/Apa itu Flow\|Flow]]. |
| Wilayah layanan | Menjadi pilihan seragam di berbagai Table sehingga laporan antarwilayah konsisten. |

Dengan satu daftar yang terhubung ke data dan logika, Enum membuat pilihan yang sama dapat dipakai konsisten di seluruh Phoenix.

## Praktik Terbaik

- **Pilih Format sejak awal.** Mengubah [[^field|Format]] setelah ada [[Docs/Tipe Data/EnumData]] memerlukan [[^field|Force Update]] dan berisiko kehilangan nilai.
- **Beri [[^field|Name]] yang jelas dan konsisten.** [[^field|Name]] harus unik di dalam Enum dan menjadi label yang dilihat pengguna pada pilihan.
- **Gunakan [[^field|Selectable]], bukan [[^button/delete|Delete]],** untuk menyembunyikan pilihan lama dari field tanpa kehilangan datanya.
- **Bersihkan relasi sebelum menghapus Enum.** Lepas field dan komponen lain yang memakai Enum agar tidak ada yang terputus.
- **Satu Enum untuk satu tema pilihan.** Pisahkan daftar yang berbeda maksud, misalnya status dan kategori, agar mudah dirawat.

## Batasan dan Catatan

- [[^field|Name]] [[Docs/Tipe Data/EnumData]] harus unik di dalam satu Enum.
- [[^field|Selectable]] hanya memengaruhi daftar pilihan pada field. [[Docs/Tipe Data/EnumData]] dengan [[^field|Selectable]] [[^value/boolean/false]] tetap dapat dipakai di tempat lain.
- [[^field|Format]] dapat diubah, tetapi harus melalui [[^field|Force Update]] dengan hasil *loss safe* atau *force*.
- Menghapus Enum menghilangkan seluruh [[Docs/Tipe Data/EnumData]] di dalamnya, dan relasi dari komponen lain harus dihapus terlebih dahulu.
- [[^field|Header]] hanya dipakai oleh [[^field|Format]] dengan tipe data [[Docs/Tipe Data/EnumData]], [[Docs/Tipe Data/Column]], [[Docs/Tipe Data/Row]], [[Docs/Tipe Data/TableData]], dan [[Docs/Tipe Data/Node]].

## TL:DR

- Enum adalah komponen *Master Data* di modul [[Docs/Modul Data/Pengenalan|Data]] untuk pilihan, menu, opsi, atau kategori.
- Setiap Enum berisi banyak [[Docs/Tipe Data/EnumData|EnumData]] dengan [[^field|Name]] unik.
- Field berformat [[Docs/Tipe Data/EnumData]] hanya menampilkan baris dengan [[^field|Selectable]] bernilai [[^value/boolean/true]].
- [[^field|Value]] mengikuti [[^field|Format]] Enum, dan [[^field|Header]] dipakai untuk [[^field|Format]] tertentu.
- Kelola Enum lewat [[^button/edit|Edit]], [[^button/refresh|Refresh]], dan hapus dari [[Docs/Antarmuka#Area Manajemen Folder]], serta kelola baris dengan [[^button/add|Add Row]].
- Hati-hati saat mengubah [[^field|Format]] dan menghapus Enum karena dapat menghilangkan data.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apa bedanya Enum dengan EnumData?**
> Enum adalah komponen yang menyimpan daftar, sedangkan [[Docs/Tipe Data/EnumData]] adalah setiap baris di dalamnya.
> **Mengapa pilihan saya tidak muncul di field?**
> Pastikan [[^field|Selectable]] pada [[Docs/Tipe Data/EnumData]] bernilai [[^value/boolean/true]]. Hanya [[Docs/Tipe Data/EnumData]] dengan [[^field|Selectable]] bernilai [[^value/boolean/true]] yang tampil sebagai pilihan.
> **Apakah EnumData dengan Selectable No masih bisa dipakai?**
> Bisa. [[^field|Selectable]] hanya memengaruhi daftar pilihan pada field, bukan pemakaian di tempat lain.
> **Bolehkah dua EnumData memiliki Name yang sama?**
> Tidak, selama keduanya berada di Enum yang sama.
> **Mengapa Enum saya tidak bisa dihapus?**
> Hapus terlebih dahulu relasi dari komponen lain yang masih memakai Enum tersebut, lalu ulangi penghapusan.