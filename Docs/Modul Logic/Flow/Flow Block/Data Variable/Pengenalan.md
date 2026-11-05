---
status: draft
title: Flow Block Data Variable
description: Pengenalan kelompok Flow Block Data Variable, block untuk menambah, membaca, mengubah, dan menghapus Variable Data lewat logika Flow.
tags: flowblock-category
---
# Flow Block Data Variable

>**note** Flow Block Data Variable merupakan salah satu kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori Data dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Data Variable adalah kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang dipakai untuk mengakses komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] melalui logika [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan kelompok ini, alur Anda dapat menambahkan, membaca, mengubah, dan menghapus [[Docs/Tipe Data/Variable|Variable Data]] secara otomatis, tanpa membuka halaman kerja Variable.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur dan memiliki Control serta output yang mirip, block Data bekerja setelah menerima data dari block sebelumnya sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Setiap block pada kelompok ini juga unik sesuai fungsinya: ada yang menambah atau menghapus Variable Data, ada yang membaca Value, dan ada yang mengubahnya. Karena itu Anda memilih block berdasarkan peran yang dibutuhkan di alur, bukan berdasarkan pola input dan output yang seragam.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/data-variable-block-flow.png|Enam Flow Block Data Variable pada Blueprint: Add Variable, Delete Variable, Variable, Variable Getter, Variable Setter, dan Variable Value]]

Block Data Variable umumnya berada di tengah atau di ujung alur. Alur membaca Value dari [[Docs/Tipe Data/Variable|Variable Data]], meneruskannya ke block lain untuk diolah.

>**note** Variable dirujuk lewat Name
> [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] mengambil [[Docs/Tipe Data/Variable|Variable Data]] dengan mengisi [[^field|Name]]. Jika [[^field|Name]] tidak cocok dengan Variable Data mana pun, block tidak menerima nilai atau terjadi error, dan laporannya tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Aksi menambahkan, mengubah, atau menghapus Variable Data yang dilakukan oleh block Data Variable tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]]. Perubahan dari sumber lain, seperti pengisian manual di halaman kerja Variable, tetap memicu Event.

>**note** Akses komponen Variable
> Anggota yang tidak memiliki akses ke komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tidak dapat melihat Value, tetapi tetap dapat memakai [[Docs/Tipe Data/Variable]] untuk otomasi atau integrasi melalui Flow.

>**warning** Menghapus Variable Data lewat Flow
> [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Delete Variable|Delete Variable Block]] menghapus [[Docs/Tipe Data/Variable|Variable Data]] dari komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]], dan Variable Data yang dihapus tidak dapat dikembalikan. Block yang merujuknya lewat [[^field|Name]], seperti [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]], tidak lagi menemukan Variable Data tersebut sehingga tidak menerima nilai atau terjadi error, dan laporannya tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].

## Jenis Flow Block Data Variable

Phoenix menyediakan enam Flow Block Data Variable. Selengkapnya tentang komponennya lihat [[Docs/Modul Data/Variable/Apa itu Variable|Variable]].

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Add Variable|Add Variable Block]] | Menambahkan [[Docs/Tipe Data/Variable|Variable Data]] baru ke komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Delete Variable|Delete Variable Block]] | Menghapus [[Docs/Tipe Data/Variable|Variable Data]] dari komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable|Variable Block]] | Mengonversi [[Docs/Tipe Data/Variable|Variable Data]] menjadi nilai atributnya untuk block lain. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] | Mengambil [[Docs/Tipe Data/Variable|Variable Data]] dengan mengisi [[^field|Name]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]] | Mengubah [[^field|Value]] pada [[Docs/Tipe Data/Variable|Variable Data]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] | Menghasilkan [[^field|Value]] dari [[Docs/Tipe Data/Variable|Variable Data]] sebagai nilai untuk block lain. |

## Memilih Flow Block Data Variable

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menambahkan [[Docs/Tipe Data/Variable|Variable Data]] baru. | [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Add Variable|Add Variable Block]] |
| Menghapus [[Docs/Tipe Data/Variable|Variable Data]] yang tidak dipakai lagi. | [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Delete Variable|Delete Variable Block]] |
| Mengonversi [[Docs/Tipe Data/Variable|Variable Data]] menjadi nilai atributnya. | [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable|Variable Block]] |
| Mengambil [[Docs/Tipe Data/Variable|Variable Data]] berdasarkan [[^field|Name]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] |
| Menyimpan hasil olahan sebagai [[^field|Value]] baru. | [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]] |
| Memakai [[^field|Value]] [[Docs/Tipe Data/Variable|Variable Data]] sebagai nilai pada block lain. | [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Modul Data/Variable/Mengotomasi|Mengotomasi Variable]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]

