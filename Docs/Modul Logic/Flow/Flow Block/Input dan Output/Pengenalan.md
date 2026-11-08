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
<!--
  * [DONE] Tambahkan screenshot Blueprint yang memuat Branch dan Passer dengan nama file `io-block-flow.png`. Anotasi yang disarankan: nomor 1 pada Branch dan nomor 2 pada Passer, termasuk input di sisi kiri dan output di sisi kanan masing-masing.
-->

Block Input dan Output umumnya ditempatkan di tengah alur, di antara block yang menghasilkan data dan block yang memakainya. Dengan begitu, satu hasil dapat dipakai oleh beberapa jalur, atau beberapa jalur yang tidak diketahui urutannya bisa diatur kembali, tanpa mengubah data yang mengalir.

## Jenis Flow Block Input dan Output

Phoenix menyediakan dua Flow Block Input dan Output. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]] | Mencabangkan aliran sehingga data dapat diteruskan ke jalur yang berbeda. |
| [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]] | Meneruskan data yang diterima ke block berikutnya tanpa mengubahnya. |

<!--
  * [TODO] Konfirmasi fungsi Branch Block. Draf menyebut "mencabangkan aliran ke jalur yang berbeda". Apakah pencabangan ditentukan oleh kondisi (misalnya nilai [[Docs/Tipe Data/Boolean]]), atau data diteruskan ke seluruh jalur sekaligus?
    Jawaban: Branch Block hanya menerima satu input dan mengeluarkan output lebih dari satu, sehingga batasan dari aturan "output hanya ke satu input" dapat ditolong oleh block ini. Input ketika dalam bentuk field juga berguna untuk mendefinisikan data yang dapat digunakan ke banyak block (seperti local variable).
  * [TODO] Konfirmasi fungsi Passer Block. Draf menyebut "meneruskan data tanpa mengubahnya". Apakah ada kegunaan lain, misalnya menyatukan beberapa jalur atau merapikan koneksi di Blueprint?
    Jawaban: Urutan eksekusi aliran bisa saja tidak terprediksi dan tidak ada yang menjamin aliran besar harus tereksekusi jika semua block lainnya tereksekusi. Passer Block berfungsi dengan memanfaatkan aturan syarat eksekusi block dimana setiap input dari output sebelumnya harus tereksekusi, jadi ketika aliran besar (aliran lebih dari satu) ingin dipastikan selesai semua tereksekusi atau memastikan urutan aliran besar benar (semisal ingin membuat kode seri dengan bantuan Concatenate) dapat terjamin. Input ketika dalam bentuk field juga berguna untuk mendefinisikan daftar data dalam satu block (seperti local variable)
  * [TODO] Konfirmasi kalimat pembeda dengan Flow Block Operator ("berfokus pada jalur aliran data, bukan pada isi data") dan kalimat penutup peran di bawah gambar.
    Jawaban: Sudah oke untuk pembeda, tapi kurang oke untuk menjelaskan kenapa kategori ini harus ada dan penting dalam Flow.
  * [TODO] Halaman block yang diusulkan: `Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch` dan `Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer`. Masing-masing berisi Input dan Output, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, serta Batasan dan Catatan.
    Jawaban: Ya, tapi akan dilanjutkan nanti, jangan sekarang.
-->

## Memilih Flow Block Input dan Output

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Memecah alur menjadi beberapa jalur atau Mendefinisikan data yang digunakan banyak block  | [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]] |
| Mendefinisikan, Meneruskan atau mengurutkan data ke block lain tanpa mengubahnya. | [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
