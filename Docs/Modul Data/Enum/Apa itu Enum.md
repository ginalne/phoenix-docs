---
    status: release
    title: Apa itu Enum?
    description: Enum adalah komponen Master Data di modul Data untuk menyimpan daftar pilihan, menu, opsi, atau kategori yang dapat dipakai ulang oleh komponen lain.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="1 0 13 14">
    <path fill-rule="evenodd" clip-rule="evenodd" d="M7 3l1-1h6l1 1v5l-1 1h-4V8h4V3H8v3H7V3zm2 6V8L8 7H2L1 8v5l1 1h6l1-1V9zM8 8v5H2V8h6zm1.414-1L9 6.586V6h4v1H9.414zM9 4h4v1H9V4zm-2 6H3v1h4v-1z"/>
  </svg>'
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
| [[Docs/Tipe Data/EnumData|EnumData]] | Satu baris data di dalam Enum yang berisi [[^field|Name]], [[^field|Description]], [[^field|Value]], dan [[^field|Selectable]]. |
| [[#Membaca Baris EnumData|Selectable]] | Penanda apakah sebuah [[Docs/Tipe Data/EnumData]] tampil sebagai pilihan pada field berformat [[Docs/Tipe Data/EnumData]]. |
| [[#Konfigurasi Enum|Format]] | Format data yang menentukan bentuk kolom [[^field|Value]] pada setiap baris. |
| [[#Konfigurasi Enum|Header]] | Header untuk [[^field|Format]] yang membutuhkan tipe data pendamping. |
| [[Docs/Modul Data/Enum/Strict On Field|Strict On Selected]] | Atribut penting Enum yang mengatur ketegasan pilihan. Selengkapnya lihat [[Docs/Modul Data/Enum/Strict On Field]]. |

## Cara Kerja

Penjelasan cara kerja Enum lihat selengkap nya di [[Docs/Modul Data/Enum/Cara Kerja|Cara Kerja Enum]].

## Antarmuka

Penjelasan antarmuka Enum lihat selengkap nya di [[Docs/Modul Data/Enum/Antarmuka|Antarmuka Enum]].

## Mengelola Enum

Berikut adalah halaman yang menjelaskan cara untuk mengelola Table:
1. [[Docs/Modul Data/Enum/Membuat Baru]] Enum dalam halaman kerja.
2. [[Docs/Modul Data/Enum/Mengubah]] Atribut Enum seperti [[^field|Name]], [[^field|Description]].
3. [[Docs/Modul Data/Enum/Menghapus]] Enum.
4. [[Docs/Modul Data/Enum/Enum Data/Pengenalan|Mengelola Data]] seperti menambahkan, mengubah, menghapus atau menggabungkan [[Docs/Tipe Data/EnumData]].
5. [[Docs/Modul Data/Enum/Publikasi]]: mengatur publikasi Table.
6. [[Docs/Modul Data/Enum/Otomasi]]: menghubungkan Table dengan [[Docs/Event/Apa itu Event|Event]].

Anda juga dapat memperdalam tentang Tipe Data yang berhubungan dengan data yaitu: [[Docs/Tipe Data/EnumData]].

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
