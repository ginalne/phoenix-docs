---
status: draft
title: Flow Block Input dan Output
description: Pengenalan kategori Flow Block Input dan Output, block yang membantu mengelola aliran data di Blueprint Flow.
pageDecoration:
  tree:
    priority: 11
tags: flowblock-category
---
# Flow Block Input dan Output

>**note** Flow Block Input dan Output merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Input dan Output adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang membantu mengelola **aliran data** di dalam Flow. Block pada kategori ini mengatur bagaimana data diteruskan dan ke jalur mana data mengalir, sehingga alur di Blueprint dapat dibuat bercabang atau disambungkan sesuai kebutuhan.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Input dan Output bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Berbeda pula dengan [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] yang mengolah isi data, block Input dan Output berfokus pada jalur aliran data, bukan pada isi data itu sendiri.

![[Docs/Modul Logic/Flow/Flow Block/Input dan Output/io-block-flow.png|Dua Flow Block Input dan Output pada Blueprint: Branch dan Passer]]

Kategori ini penting karena dua aturan dasar pada Flow. Pertama, satu output hanya dapat terhubung ke satu input, sehingga data yang dibutuhkan banyak block tidak dapat disambungkan langsung dari satu output. Kedua, urutan eksekusi aliran yang bercabang tidak dapat diprediksi, sedangkan sebuah block baru diproses setelah setiap block yang terhubung ke inputnya selesai tereksekusi. Block Input dan Output menjawab kedua kebutuhan tersebut: membagikan satu data ke banyak block, serta memastikan beberapa aliran selesai atau berurutan sebelum alur dilanjutkan, tanpa mengubah data yang mengalir.

## Jenis Flow Block Input dan Output

Phoenix menyediakan dua Flow Block Input dan Output. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]] | Menerima satu input dan meneruskannya ke beberapa output, sehingga satu data dapat dipakai oleh banyak block. Input berupa *field* juga dapat dipakai untuk mendefinisikan data, seperti *local variable*. |
| [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]] | Meneruskan data ke block berikutnya tanpa mengubahnya, sekaligus memastikan seluruh aliran yang terhubung ke inputnya selesai tereksekusi sehingga urutan aliran terjamin. Input berupa *field* juga dapat dipakai untuk mendefinisikan daftar data dalam satu block. |

## Memilih Flow Block Input dan Output

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Memecah alur menjadi beberapa jalur, atau mendefinisikan data yang dipakai banyak block. | [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]] |
| Mendefinisikan, meneruskan, atau mengurutkan data ke block lain tanpa mengubahnya. | [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
