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

Flow Block Query adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **membangun dan menjalankan [[Docs/Tipe Data/Query|Query]]** di dalam Flow. Dengan block Query, Anda dapat menyusun kondisi dari data yang mengalir di Flow, merangkainya menjadi [[Docs/Tipe Data/Query|Query]], lalu menjalankannya untuk mendapatkan data yang dibutuhkan oleh alur berikutnya.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Query bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Kedua block pada kategori ini saling melengkapi: Condition membangun bagian kondisi yang kemudian dirangkai menjadi [[Docs/Tipe Data/Query|Query]], dan Execute menjalankannya.

![[Docs/Modul Logic/Flow/Flow Block/Query/query-block-flow.png|Dua Flow Block Query pada Blueprint: Condition dan Execute]]

Block Query umumnya ditempatkan di tengah alur. Hasil dari Execute diteruskan ke block lain, misalnya untuk diolah oleh [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] atau dikirim ke sistem lain lewat [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Flow Block Modular]].

## Jenis Flow Block Query

Phoenix menyediakan dua Flow Block Query. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Query/Condition|Condition Query Block]] | Membangun bagian kondisi dari [[Docs/Tipe Data/Query|Query]] yang kemudian dirangkai menjadi [[Docs/Tipe Data/Query|Query]] utuh. |
| [[Docs/Modul Logic/Flow/Flow Block/Query/Execute|Execute Query Block]] | Menjalankan [[Docs/Tipe Data/Query|Query]] yang telah dirangkai. Bentuk hasilnya mengikuti cara [[Docs/Tipe Data/Query|Query]] dirangkai. |

## Memilih Flow Block Query

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menyusun bagian kondisi [[Docs/Tipe Data/Query|Query]] dari data yang mengalir di Flow. | [[Docs/Modul Logic/Flow/Flow Block/Query/Condition|Condition Query Block]] |
| Menjalankan [[Docs/Tipe Data/Query|Query]] dan memakai hasilnya di alur. | [[Docs/Modul Logic/Flow/Flow Block/Query/Execute|Execute Query Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
