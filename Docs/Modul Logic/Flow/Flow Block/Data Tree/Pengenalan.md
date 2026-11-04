---
status: draft
title: Flow Block Data Tree
description: Pengenalan kelompok Flow Block Data Tree, block untuk menambah, menelusuri, mengubah, dan menghapus Node lewat logika Flow.
tags: flowblock-category
---
# Flow Block Data Tree

>**note** Flow Block Data Tree merupakan salah satu kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] pada kategori Data dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Data Tree adalah kelompok [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang dipakai untuk mengakses komponen [[Docs/Modul Data/Tree/Apa itu Tree|Tree]] melalui logika [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan kelompok ini, alur Anda dapat membaca atribut [[Docs/Tipe Data/Tree]] dan [[Docs/Tipe Data/Node]], menelusuri hubungan antar Node (induk, anak, dan leluhur), serta menambah, menetapkan, mengubah, dan menghapus Node secara otomatis, tanpa membuka halaman kerja Tree.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur dan memiliki Control serta output yang mirip, block Data bekerja setelah menerima data dari block sebelumnya sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Setiap block pada kelompok ini juga unik sesuai fungsinya: ada yang membaca atribut Tree atau Node, ada yang menelusuri hubungan Node, dan ada yang mengelola Node. Karena itu Anda memilih block berdasarkan peran yang dibutuhkan di alur, bukan berdasarkan pola input dan output yang seragam.

![[Docs/Modul Logic/Flow/Flow Block/Data Tree/data-tree-block-flow.png|Sepuluh Flow Block Data Tree pada Blueprint: Add Node, Assign Node, Delete Node, Node, Node Get Ancestor, Node Get Children, Node Get Parent, Node Setter, Tree, dan Tree Get Origin]]

Block Data Tree umumnya berada di tengah atau di ujung alur. Misalnya, alur mengambil [[Docs/Tipe Data/Node]] Origin dari sebuah Tree, menelusuri anak-anaknya, lalu meneruskan hasilnya ke block lain.

>**note** Tree yang baru dibuat memiliki Node Origin
> Setiap Tree yang baru dibuat otomatis memiliki satu [[Docs/Tipe Data/Node]] bernama Origin. Block Tree Get Origin mengambil Node ini sebagai titik awal penelusuran.

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Aksi menambahkan, mengubah, atau menghapus [[Docs/Tipe Data/Node]] yang dilakukan oleh block Data Tree tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event Block]]. Perubahan dari sumber lain, seperti pengisian manual di halaman kerja Tree, Import, atau Upload, tetap memicu Event.

>**warning** Perubahan lewat Flow pada Tree Merger dan External Read Only
> Block Data Tree dapat mengubah atau menghapus [[Docs/Tipe Data/Node]] pada Tree yang memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] atau [[Docs/Modul Data/Tree/Konfigurasi External Read Only|External Read Only]] aktif, termasuk Node hasil clone. Perubahan Node pada Tree Merger juga dapat memengaruhi Node di Tree non-merger, sehingga periksa dampaknya sebelum menjalankan alur.

>**warning** Menghapus Node yang memiliki anak
> [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]] menghapus [[Docs/Tipe Data/Node]] dari [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. Jika Node tersebut memiliki Node anak, hubungan induk dan anaknya ikut terdampak. Pastikan Node yang dihapus memang tidak dipakai lagi.

<!--

  * [TODO] Konfirmasi isi callout warning Delete Node Block. Draf saat ini ditulis umum: apa yang terjadi pada Node anak ketika Node induknya dihapus lewat Flow (ikut terhapus, atau lainnya), dan apakah Node Origin dapat dihapus? Mohon jelaskan agar warning dapat dibuat spesifik.

-->

## Jenis Flow Block Data Tree

Phoenix menyediakan sepuluh Flow Block Data Tree. Selengkapnya tentang komponennya lihat [[Docs/Modul Data/Tree/Apa itu Tree|Tree]].

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]] | Menambahkan [[Docs/Tipe Data/Node]] baru ke sebuah [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]] | Menetapkan [[Docs/Tipe Data/Node]] ke posisi tertentu pada Tree, misalnya di bawah Node induk yang dipilih. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]] | Menghapus [[Docs/Tipe Data/Node]] dari sebuah [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]] | Mengambil nilai atribut [[Docs/Tipe Data/Node]], yaitu [[^field|Order]], [[^field|Name]], dan [[^field|Tree]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]] | Mengambil [[Docs/Tipe Data/Node]] leluhur dari sebuah Node pada tingkat yang ditentukan. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] | Mengambil [[Docs/Tipe Data/Node]] anak langsung dari sebuah Node dengan [[^field|Order]] yang ditentukan. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]] | Mengambil [[Docs/Tipe Data/Node]] induk dari sebuah Node. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]] | Mengubah atribut [[Docs/Tipe Data/Node]], yaitu [[^field|Name]] dan [[^field|Order]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree|Tree Block]] | Mengambil nilai atribut [[Docs/Modul Data/Tree/Apa itu Tree|Tree]], yaitu [[^field|Name]], [[^field|Description]], dan [[^field|Merger Mode]]. |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] | Mengambil [[Docs/Tipe Data/Node]] Origin dari sebuah [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. |

## Memilih Flow Block Data Tree

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Membaca [[^field|Name]], [[^field|Description]], dan [[^field|Merger Mode]] sebuah [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree|Tree Block]] |
| Membaca [[^field|Order]], [[^field|Name]], dan [[^field|Tree]] sebuah [[Docs/Tipe Data/Node]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node|Node Block]] |
| Memulai penelusuran dari Node Origin. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin|Tree Get Origin Block]] |
| Mengambil Node induk. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent|Node Get Parent Block]] |
| Mengambil Node anak langsung dengan [[^field|Order]] tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children|Node Get Children Block]] |
| Mengambil Node leluhur pada tingkat tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor|Node Get Ancestor Block]] |
| Menambahkan [[Docs/Tipe Data/Node]] baru. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node|Add Node Block]] |
| Menempatkan [[Docs/Tipe Data/Node]] pada posisi tertentu di Tree. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node|Assign Node Block]] |
| Mengubah [[^field|Name]] atau [[^field|Order]] sebuah [[Docs/Tipe Data/Node]]. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter|Node Setter Block]] |
| Menghapus [[Docs/Tipe Data/Node]] yang tidak dipakai lagi. | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node|Delete Node Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Data/Tree/Apa itu Tree|Tree]]
- [[Docs/Modul Data/Tree/Mengotomasi|Mengotomasi Tree]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]