---
status: draft
title: Flow Block Query
description: Pengenalan kategori Flow Block Query, block yang membangun dan menjalankan Query di Blueprint Flow.
pageDecoration:
  tree:
    priority: 12
tags: flowblock-category
---
# Flow Block Query

>**note** Flow Block Query merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Query adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **membangun dan menjalankan [[Docs/Tipe Data/Query|Query]]** di dalam Flow. Dengan block Query, Anda dapat menyusun kondisi dari data yang mengalir di Flow, lalu menjalankannya untuk mendapatkan data yang dibutuhkan oleh alur berikutnya.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Query bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Kedua block pada kategori ini saling melengkapi: satu block menyusun [[Docs/Tipe Data/Query|Query]], dan block lainnya menjalankannya.

![[Docs/Modul Logic/Flow/Flow Block/Query/query-block-flow.png|Dua Flow Block Query pada Blueprint: Condition dan Execute]]

<!--
  * [DONE] Tambahkan screenshot Blueprint yang memuat Condition dan Execute dengan nama file `query-block-flow.png`. Anotasi yang disarankan: nomor 1 pada Condition dan nomor 2 pada Execute, termasuk koneksi antarkeduanya bila saling terhubung.
-->

Block Query umumnya ditempatkan di tengah alur. Hasil dari block ini kemudian diteruskan ke block lain, misalnya untuk diolah oleh [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] atau dikirim ke sistem lain lewat [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Flow Block Modular]].

## Jenis Flow Block Query

Phoenix menyediakan dua Flow Block Query. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Query/Condition|Condition Query Block]] | Membangun kondisi [[Docs/Tipe Data/Query|Query]] dari data yang mengalir di Flow. |
| [[Docs/Modul Logic/Flow/Flow Block/Query/Execute|Execute Query Block]] | Menjalankan [[Docs/Tipe Data/Query|Query]] dan menghasilkan data untuk diteruskan ke block berikutnya. |

<!--
  * [TODO] Konfirmasi fungsi Condition Query Block. Draf menyebut "membangun kondisi Query". Apakah block ini menghasilkan Query utuh, atau hanya bagian kondisi yang kemudian dirangkai?
    Jawaban: Hanya bagian kondisi yang kemudian dirangkai
  * [TODO] Konfirmasi fungsi Execute Query Block, termasuk bentuk hasilnya. Apakah hasilnya mengikuti [[Docs/Query/Output/Table|Table Output]] atau kaidah Output lain (Single, Series, Multi Series)? Bila ya, tambahkan penjelasan singkat di tabel.
  * [TODO] Halaman block yang diusulkan: `Docs/Modul Logic/Flow/Flow Block/Query/Condition` dan `Docs/Modul Logic/Flow/Flow Block/Query/Execute`. Masing-masing berisi Input dan Output, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, serta Batasan dan Catatan.
-->

## Memilih Flow Block Query

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menyusun kondisi [[Docs/Tipe Data/Query|Query]] dari data yang mengalir di Flow. | [[Docs/Modul Logic/Flow/Flow Block/Query/Condition|Condition Query Block]] |
| Menjalankan [[Docs/Tipe Data/Query|Query]] dan memakai hasilnya di alur. | [[Docs/Modul Logic/Flow/Flow Block/Query/Execute|Execute Query Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
