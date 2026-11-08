---
status: draft
title: Flow Block Chrono
description: Pengenalan kategori Flow Block Chrono, block yang mengelola aliran berdasarkan waktu di Blueprint Flow.
pageDecoration:
  tree:
    priority: 15
tags: flowblock-category
---
# Flow Block Chrono

>**note** Flow Block Chrono merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Chrono adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengelola aliran berdasarkan waktu**, sehingga proses dalam alur dapat berjalan dalam rentang waktu yang lebih lama. Dengan block Chrono, sebuah alur tidak harus selesai seketika, tetapi dapat menunggu terlebih dahulu sebelum melanjutkan ke block berikutnya.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Chrono bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Block Chrono juga berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]] yang memulai alur pada waktu tertentu lewat [[Docs/Modul Interface/Timeline/Timeline Event/Pengenalan|Timeline Event]]: Pulser menentukan kapan alur dimulai, sedangkan block Chrono mengatur jeda di tengah alur yang sedang berjalan.

![[Docs/Modul Logic/Flow/Flow Block/Chrono/chrono-block-flow.png|Satu Flow Block Chrono pada Blueprint: Delay]]
<!--
  * [DONE] Tambahkan screenshot Blueprint yang memuat Delay dengan nama file `chrono-block-flow.png`. Anotasi yang disarankan: nomor 1 pada Delay, termasuk input di sisi kiri dan output di sisi kanan.
-->

>**note** Flow Block Chrono berbeda dengan Elemen Chrono
> Flow Block Chrono mengelola aliran berdasarkan waktu di dalam Flow. [[Docs/Modul Interface/Form/Elemen/Display/Chrono|Elemen Chrono]] pada Form adalah elemen tampilan berupa kronologi dan tidak berhubungan dengan Flow.

<!--
  * [TODO] Konfirmasi path Elemen Chrono (`Docs/Modul Interface/Form/Elemen/Display/Chrono`) dan kelayakan callout pembeda ini.
    Jawaban: Tidak perlu
-->

## Jenis Flow Block Chrono

Phoenix menyediakan satu Flow Block Chrono.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Chrono/Delay|Delay Chrono Block]] | Menunda aliran selama waktu tertentu sebelum diteruskan ke block berikutnya. |

<!--
  * [TODO] Konfirmasi fungsi Delay Chrono Block, termasuk satuan dan rentang waktu yang dapat diatur. Konfirmasi juga bagaimana proses yang sedang menunggu tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] (misalnya status waiting) dan apakah ada batas durasi.
    Jawaban: fungsinya adalah untuk melakukan penundaan pada aliran dengan waktu yang bisa ditentukan. Penundaan ini membuat state dalam blok menjadi Waiting.
  * [TODO] Halaman block yang diusulkan: `Docs/Modul Logic/Flow/Flow Block/Chrono/Delay`, berisi Input dan Output, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, serta Batasan dan Catatan.
    Jawaban: Ya, tapi akan dilanjutkan nanti, jangan sekarang.
-->

## Memilih Flow Block Chrono

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menunda sebagian alur selama waktu tertentu setelah alur berjalan. | [[Docs/Modul Logic/Flow/Flow Block/Chrono/Delay|Delay Chrono Block]] |
| Memulai alur pada jadwal tertentu. | [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]] dengan [[Docs/Modul Interface/Timeline/Timeline Event/Pengenalan|Timeline Event]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
