---
status: draft
title: Flow Block Data Table
description: Pengenalan kelompok Flow Block Data Table, block untuk menambah, membaca, mengubah, dan menghapus Row serta TableData lewat logika Flow.
tags: flowblock-category
---
# Flow Block Data Table

>**note** Flow Block Data Table merupakan salah satu kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori Data dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Data Table adalah kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang dipakai untuk mengakses komponen [[Docs/Modul Data/Table/Apa itu Table|Table]] melalui logika [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan kelompok ini, alur Anda dapat menunjuk [[Docs/Tipe Data/Table]], [[Docs/Tipe Data/Column]], dan [[Docs/Tipe Data/Row]], membaca atau mengubah [[Docs/Tipe Data/TableData]], serta menambah dan menghapus Row secara otomatis, tanpa membuka halaman kerja Table.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur dan memiliki Control serta output yang mirip, block Data bekerja setelah menerima data dari block sebelumnya sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Setiap block pada kelompok ini juga unik sesuai fungsinya: ada yang menunjuk Table, Column, atau Row, ada yang membaca dan mengubah TableData, dan ada yang menambah atau menghapus Row. Karena itu Anda memilih block berdasarkan peran yang dibutuhkan di alur, bukan berdasarkan pola input dan output yang seragam.
![[Docs/Modul Logic/Flow/Flow Block/Data Table/data-table-block-flow.png|Tujuh Flow Block Data Table pada Blueprint: Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, dan TableData Setter]]
<!--

  * [DONE] Letakkan screenshot tujuh block Data Table pada Blueprint dengan nama file `data-table-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Table/`. Saran anotasi: nomor penanda 1 sampai 7 mengikuti urutan baris pada tabel [[#Jenis Flow Block Data Table]]. Sesuaikan keterangan gambar bila jumlah atau urutan block pada screenshot berbeda.

-->

Block Data Table umumnya berada di tengah atau di ujung alur. Misalnya, alur dimulai dari perubahan [[Docs/Tipe Data/Row]] pada sebuah Table, membaca [[Docs/Tipe Data/TableData]] dari Row tersebut, mengolahnya, lalu menambahkan Row baru ke Table lain.

<!--

  * [TODO] Konfirmasi diagram: apakah TableData Getter menerima Row langsung dari Table Row Event, bagaimana tipe data output TableData Getter (dikosongkan pada diagram), dan bagaimana Table tujuan dipilih pada Add Row.
    Jawaban : Diagram tidak relevan.

-->

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Aksi menambahkan, mengubah, atau menghapus [[Docs/Tipe Data/Row]] yang dilakukan oleh block Data Table tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]]. Perubahan dari sumber lain, seperti pengisian manual di halaman kerja Table, Import, atau Upload, tetap memicu Event.

## Jenis Flow Block Data Table

Phoenix menyediakan tujuh Flow Block Data Table. Selengkapnya tentang komponennya lihat [[Docs/Modul Data/Table/Apa itu Table|Table]].

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]] | Menambahkan [[Docs/Tipe Data/Row]] baru ke sebuah [[Docs/Modul Data/Table/Apa itu Table|Table]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row|Delete Row Block]] | Menghapus [[Docs/Tipe Data/Row]] dari sebuah [[Docs/Modul Data/Table/Apa itu Table|Table]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table|Table Block]] | Mengambil nilai atribut [[Docs/Modul Data/Table/Apa itu Table|Table]], yaitu [[^field|Name]] dan [[^field|Description]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]] | Mengambil nilai atribut [[Docs/Tipe Data/Column]] pada sebuah [[Docs/Tipe Data/Table]], yaitu [[^field|Name]], [[^field|Description]], [[^field|Header]] dan [[^field|Table]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]] | Mengambil nilai atribut [[Docs/Tipe Data/Row]] pada sebuah [[Docs/Tipe Data/Table]], yaitu [[^field|Index]] dan [[^field|Name]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter|TableData Getter Block]] | Mengambil [[Docs/Tipe Data/TableData]] dari sebuah [[Docs/Tipe Data/Row]] pada [[Docs/Tipe Data/Column]] tertentu. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]] | Mengubah [[Docs/Tipe Data/TableData]] pada sebuah [[Docs/Tipe Data/Row]] di [[Docs/Tipe Data/Column]] tertentu. |

<!--

  * [TODO] Konfirmasi fungsi Table Block, Table Column Block, dan Table Row Block. Draf ini menebak dari nama: ketiganya menunjuk Table, Column, atau Row agar dapat dipakai block lain. Mohon konfirmasi apakah Table Row Block hanya menunjuk Row atau juga mencarinya (misalnya lewat ID atau Query), serta input dan output masing-masing.
    Jawaban: Sudah saya perbaiki
  * [TODO] Konfirmasi cakupan TableData Getter Block dan TableData Setter Block: bagaimana Row dan Column ditentukan (dari output block lain atau diisi di block sendiri), dan apakah Setter hanya dapat mengubah satu TableData per eksekusi.
    Jawaban : Bisa keduanya, dan Setter hanya mengubah satu TableData per eksekusi.
  * [TODO] Konfirmasi apakah Add Row Block dan Delete Row Block perlu callout `>**warning**` (misalnya Row yang dihapus tidak dapat dikembalikan, seperti pada halaman kerja Table).
    Jawaban: Ya

-->

## Memilih Flow Block Data Table

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menambahkan [[Docs/Tipe Data/Row]] baru ke sebuah Table. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]] |
| Menghapus [[Docs/Tipe Data/Row]] yang tidak dipakai lagi. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row|Delete Row Block]] |
| Menunjuk [[Docs/Modul Data/Table/Apa itu Table|Table]] tertentu untuk dipakai block lain. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table|Table Block]] |
| Menunjuk [[Docs/Tipe Data/Column]] tertentu pada sebuah Table. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]] |
| Menunjuk [[Docs/Tipe Data/Row]] tertentu pada sebuah Table. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]] |
| Membaca isi sel pada Row dan Column tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter|TableData Getter Block]] |
| Mengubah isi sel pada Row dan Column tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Data/Table/Apa itu Table|Table]]
- [[Docs/Modul Data/Table/Mengotomasi|Mengotomasi Table]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

<!--

  * [TODO] Halaman baru yang diasumsikan pada draf ini: (1) `Docs/Modul Logic/Flow/Flow Block/Data/Pengenalan` sebagai pengantar kategori Data yang memuat keempat kelompok; (2) halaman per block di `Docs/Modul Logic/Flow/Flow Block/Data Table/<Nama Block>` (Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, TableData Setter), mengikuti pola folder `Data Table/Pengenalan` yang Anda berikan. Skill sebelumnya memakai pola `Data/<Grup>/<Nama>`, mohon konfirmasi pola yang dipakai. Halaman `Docs/Modul Data/Table/Mengotomasi` mengikuti pola yang sudah ada.
    Jawaban: 1. Ganti menjadi Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan sebagai pengantar. 2. halaman per block sudah benar. pola `Data/<Grup>/<Nama>` sudah tidak berlaku, diubah menjadi `Data <Grup>/<Nama>`. Halaman Mengotomasi sudah benar.

-->