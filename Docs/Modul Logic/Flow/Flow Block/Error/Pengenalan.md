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

Flow Block Error adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengelola atau menangani error**, atau sekadar mengatur bagaimana error ditampilkan. Ketika proses dalam alur gagal, error dicatat di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] dengan status [[^flowstate|Error]] atau [[^flowstate|Fatal Error]]. Dengan block Error, Anda dapat menimbulkan error secara sengaja dengan pesan yang ditentukan sendiri, sehingga penyebab kegagalan lebih mudah dipahami.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Error bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Block Error tidak mengolah data bisnis, melainkan berfokus pada penghentian alur dan penyampaian informasi kegagalan.

![[Docs/Modul Logic/Flow/Flow Block/Error/error-block-flow.png|Satu Flow Block Error pada Blueprint: Error Message]]

Block Error umumnya ditempatkan di titik alur yang perlu dihentikan secara sengaja ketika terjadi kondisi yang tidak diinginkan, misalnya data yang tidak valid. Saat block ini tereksekusi, seluruh aliran dihentikan dan pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].

## Jenis Flow Block Error

Phoenix menyediakan satu Flow Block Error.

| Block | Fungsi |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] | Menimbulkan error baru dengan pesan yang dapat ditentukan sendiri. Saat dijalankan, seluruh aliran dihentikan dan pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]. |

## Memilih Flow Block Error

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menghentikan alur dengan pesan error yang jelas bagi pembaca [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] atau Anda yang memicu Flow. | [[Docs/Modul Logic/Flow/Flow Block/Error/Error Message|Error Message Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
