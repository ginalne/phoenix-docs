---
status: draft
title: Flow Block Error
description: Pengenalan kategori Flow Block Error, block yang mengelola dan mengatur tampilan error di Blueprint Flow.
pageDecoration:
  tree:
    priority: 16
tags: flowblock-category
---
# Flow Block Error

>**note** Flow Block Error merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

<!--
  * [TODO] Nilai `pageDecoration.tree.priority` (16) adalah usulan berdasarkan urutan kategori pada menu Add setelah Event (6) dan empat kelompok Flow Block Data. Mohon sesuaikan urutan tampil pada pohon dokumentasi.
-->

Flow Block Error adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengelola atau menangani error**, atau sekadar mengatur bagaimana error ditampilkan. Ketika proses dalam alur gagal, error dicatat di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] dengan status [[^flowstate|Error]] atau [[^flowstate|Fatal Error]]. Dengan block Error, Anda dapat menentukan pesan yang muncul agar penyebab kegagalan lebih mudah dipahami.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Error bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Block Error tidak mengolah data bisnis, melainkan berfokus pada penanganan dan penyampaian informasi kegagalan.

![[Docs/Modul Logic/Flow/Flow Block/Error/error-block-flow.png|Satu Flow Block Error pada Blueprint: Error Message]]

<!--
  * [TODO] Tambahkan screenshot Blueprint yang memuat Error Message dengan nama file `error-block-flow.png`. Anotasi yang disarankan: nomor 1 pada Error Message, termasuk input di sisi kiri dan output (bila ada) di sisi kanan.
-->

Block Error umumnya ditempatkan pada jalur penanganan, yaitu setelah block yang dapat menghasilkan kegagalan, misalnya block yang mengirim permintaan ke sistem lain atau block yang mengubah data.

## Jenis Flow Block Error

Phoenix menyediakan satu Flow Block Error.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] | Mengatur pesan error yang ditampilkan ketika alur mengalami kegagalan. |

<!--
  * [TODO] Konfirmasi fungsi Error Message Block. Draf menyebut "mengatur pesan error yang ditampilkan". Apakah block ini menimbulkan error baru dengan pesan buatan sendiri, atau mengganti pesan dari error yang sudah terjadi? Apakah pesannya tampil di Flow Activity saja?
  * [TODO] Konfirmasi kalimat tentang status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] pada paragraf pembuka, terutama apakah Error Message Block memengaruhi status tersebut.
  * [TODO] Halaman block yang diusulkan: `Docs/Modul Logic/Flow/Flow Block/Error/Error Message`, berisi Input dan Output, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, serta Batasan dan Catatan.
-->

## Memilih Flow Block Error

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Mengatur pesan error agar lebih jelas bagi pembaca [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]. | [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
