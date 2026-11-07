---
status: draft
title: Flow Block Modular
description: Pengenalan kategori Flow Block Modular, block yang menjalankan proses kompleks seperti permintaan HTTP dan layanan AI di Blueprint Flow.
pageDecoration:
  tree:
    priority: 14
tags: flowblock-category
---
# Flow Block Modular

>**note** Flow Block Modular merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Modular adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengeksekusi proses yang kompleks**, seperti memanggil permintaan HTTP atau menghubungi provider jasa tertentu. Dengan block Modular, Flow dapat terhubung ke sistem dan layanan di luar Phoenix, lalu hasilnya diteruskan ke block lain untuk diolah atau disimpan.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Modular bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Berbeda pula dengan [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] yang mengolah data di dalam Flow, block Modular bekerja dengan sistem atau layanan di luar Flow. Block Modular dikelompokkan berdasarkan jenis layanannya, yaitu API dan AI.

![[Docs/Modul Logic/Flow/Flow Block/Modular/modular-block-flow.png|Dua Flow Block Modular pada Blueprint: HTTP Request dan OpenAI 4]]

<!--
  * [DONE] Tambahkan screenshot Blueprint yang memuat HTTP Request dan OpenAI 4 dengan nama file `modular-block-flow.png`. Anotasi yang disarankan: nomor 1 pada HTTP Request dan nomor 2 pada OpenAI 4.
-->

Block Modular umumnya ditempatkan di tengah atau di ujung alur. Data dari block sebelumnya dikirim ke layanan yang dituju, kemudian respons layanan diteruskan ke block berikutnya, misalnya untuk diurai oleh [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] lalu disimpan ke [[Docs/Modul Data/Table/Apa itu Table|Table]].

## Jenis Flow Block Modular

Phoenix menyediakan dua Flow Block Modular. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Grup | Block | Fungsi |
| --- | --- | --- |
| API | [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]] | Mengirim permintaan HTTP ke sistem atau layanan lain dan menerima responsnya. |
| AI | [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]] | Menghubungkan Flow dengan layanan OpenAI (versi 4) agar kecerdasan buatan dapat dimanfaatkan di dalam alur. |

<!--
  * [TODO] Konfirmasi fungsi HTTP Request API Block, misalnya metode HTTP yang didukung dan bentuk respons yang dihasilkan.
    Jawaban: metode HTTP yang didukung adalah semua method seperti GET, POST, PUT dan lain-lain, bentuk respons yang dihasilkan adalah object atau text tergantung Response Type dari http, untuk application/json akan menjadi object.
  * [TODO] Konfirmasi fungsi OpenAI 4 AI Block, misalnya jenis permintaan yang dikirim (teks, gambar, dan sebagainya) dan apakah diperlukan kunci atau kredensial dari pengguna. Bila diperlukan, tambahkan callout pada halaman ini.
    Jawaban: Sepertinya jenis dan hal-hal yang spesifik tentang itu akan ditambahkan callout di halaman yang dimaksud.
  * [TODO] Halaman block yang diusulkan: `Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request` dan `Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4`. Masing-masing berisi Input dan Output, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, serta Batasan dan Catatan. Catatan: knowledge sebelumnya menyebut `Modular/HTTP Request` tanpa grup, sedangkan konvensi tautan memakai grup. Mohon konfirmasi path yang benar
    Jawaban: Yang benar adalah Moduler/API dan Modular/AI. tapi usulan akan dilanjutkan nanti, jangan sekarang.
-->

## Memilih Flow Block Modular

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Berkomunikasi dengan sistem atau layanan lain lewat permintaan HTTP. | [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]] |
| Memanfaatkan layanan OpenAI di dalam alur. | [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4|OpenAI 4 AI Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
