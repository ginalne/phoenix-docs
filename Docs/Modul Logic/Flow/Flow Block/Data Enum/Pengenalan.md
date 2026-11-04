---
status: draft
title: Flow Block Data Enum
description: Pengenalan kelompok Flow Block Data Enum, block untuk menambah, membaca, mengubah, dan menghapus EnumData lewat logika Flow.
tags: flowblock-category
---
# Flow Block Data Enum

>**note** Flow Block Data Enum merupakan salah satu kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori Data dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Data Enum adalah kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang dipakai untuk mengakses komponen [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] melalui logika [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan kelompok ini, alur Anda dapat menunjuk Enum, menambahkan, membaca, mengubah, dan menghapus [[Docs/Tipe Data/EnumData]] secara otomatis, tanpa membuka halaman kerja Enum.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur dan memiliki Control serta output yang mirip, block Data bekerja setelah menerima data dari block sebelumnya sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Setiap block pada kelompok ini juga unik sesuai fungsinya: ada yang menunjuk Enum atau EnumData, ada yang membaca atau mengubah atributnya, dan ada yang menambah atau menghapus EnumData. Karena itu Anda memilih block berdasarkan peran yang dibutuhkan di alur, bukan berdasarkan pola input dan output yang seragam.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/data-enum-block-flow.png]]
<!--

  * [DONE] Letakkan screenshot tujuh block Data Enum pada Blueprint dengan nama file `data-enum-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Enum/`. Saran anotasi: nomor penanda 1 sampai 7 mengikuti urutan baris pada tabel [[#Jenis Flow Block Data Enum]]. Sesuaikan keterangan gambar bila jumlah atau urutan block pada screenshot berbeda.

-->

Block Data Enum umumnya berada di tengah atau di ujung alur. Alur menerima pemicu dari block sebelumnya, lalu menambahkan, membaca, atau mengubah [[Docs/Tipe Data/EnumData]] pada [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] yang dituju.

<!--

  * [TODO] Konfirmasi diagram: apakah Add EnumData menerima langsung hasil dari Pulser, dan bagaimana Enum tujuan dipilih (diisi pada block Add EnumData sendiri atau lewat Enum Block).
    Jawaban : Diagram tidak relevan.

-->

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Aksi menambahkan, mengubah, atau menghapus [[Docs/Tipe Data/EnumData]] yang dilakukan oleh block Data Enum tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]]. Perubahan dari sumber lain, seperti pengisian manual di halaman kerja Enum, Import, atau Upload, tetap memicu Event.

## Jenis Flow Block Data Enum

Phoenix menyediakan tujuh Flow Block Data Enum. Selengkapnya tentang komponennya lihat [[Docs/Modul Data/Enum/Apa itu Enum|Enum]].

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]] | Menambahkan [[Docs/Tipe Data/EnumData]] baru ke sebuah [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]] | Menghapus [[Docs/Tipe Data/EnumData]] dari sebuah [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Enum|Enum Block]] | Mengambil nilai atribut [[Docs/Modul Data/Enum/Apa itu Enum|Enum]], yaitu [[^field|Name]] dan [[^field|Description]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]] | Mengambil atribut [[Docs/Tipe Data/EnumData]], yaitu [[^field|Name]], [[^field|Description]], [[^field|Value]], dan [[^field|Selectable]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] | Mengambil [[Docs/Tipe Data/EnumData]] dari [[Docs/Tipe Data/Enum]] yang ditunjuk dengan mengisi [[^field|Name]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]] | Mengubah atribut [[Docs/Tipe Data/EnumData]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]] | Menghasilkan [[^field|Value]] dari [[Docs/Tipe Data/EnumData]] sebagai nilai untuk block lain. |

<!--

  * [TODO] Konfirmasi fungsi Enum Block, EnumData Block, dan EnumData Value Block. Draf ini menebak dari nama: Enum Block dan EnumData Block menunjuk Enum atau EnumData, sedangkan EnumData Value Block menghasilkan Value-nya. Mohon jelaskan perbedaan EnumData Block, EnumData Getter Block, dan EnumData Value Block, termasuk input dan output masing-masing.
    Jawaban: Sudah saya perbaiki
  * [TODO] Konfirmasi cakupan EnumData Getter Block dan EnumData Setter Block: apakah keempat atribut (Name, Description, Value, Selectable) dapat dibaca dan diubah, dan apakah Name EnumData yang sama di dalam satu Enum menghasilkan error.
    Jawaban: Ya, dan jika ada name yang sama maka tidak menghasilkan error, melainkan output yang diekspetasikan (akan dijelaskan lebih lanjut di halaman blocknya)
  * [TODO] Konfirmasi apakah Add EnumData Block dan Delete EnumData Block perlu callout `>**warning**` (misalnya Enum yang dituju memiliki Strict On Selected atau EnumData yang dihapus sedang dipakai komponen lain).
    Jawaban: Perlu.

-->

## Memilih Flow Block Data Enum

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menambahkan [[Docs/Tipe Data/EnumData]] baru ke sebuah Enum. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]] |
| Menghapus [[Docs/Tipe Data/EnumData]] yang tidak dipakai lagi. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]] |
| Menunjuk [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] tertentu untuk dipakai block lain. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Enum|Enum Block]] |
| Menunjuk [[Docs/Tipe Data/EnumData]] tertentu untuk dipakai block lain. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]] |
| Membaca atribut [[Docs/Tipe Data/EnumData]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] |
| Mengubah atribut [[Docs/Tipe Data/EnumData]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]] |
| Memakai Value [[Docs/Tipe Data/EnumData]] sebagai nilai pada block lain. | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Modul Data/Enum/Mengotomasi|Mengotomasi Enum]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

<!--

  * [TODO] Halaman baru yang diasumsikan pada draf ini: (1) `Docs/Modul Logic/Flow/Flow Block/Data/Pengenalan` sebagai pengantar kategori Data yang memuat keempat kelompok; (2) halaman per block di `Docs/Modul Logic/Flow/Flow Block/Data Enum/<Nama Block>` (Add EnumData, Delete EnumData, Enum, EnumData, EnumData Getter, EnumData Setter, EnumData Value), mengikuti pola folder `Data Enum/Pengenalan` yang Anda berikan. Skill sebelumnya memakai pola `Data/<Grup>/<Nama>`, mohon konfirmasi pola yang dipakai. Halaman `Docs/Modul Data/Enum/Mengotomasi` mengikuti pola yang sudah ada.
    Jawaban: 1. Ganti menjadi Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan sebagai pengantar. 2. halaman per block sudah benar. pola `Data/<Grup>/<Nama>` sudah tidak berlaku, diubah menjadi `Data <Grup>/<Nama>`. Halaman Mengotomasi sudah benar.

-->