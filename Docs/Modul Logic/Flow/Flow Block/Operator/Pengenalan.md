---
status: draft
title: Flow Block Operator
description: Pengenalan kategori Flow Block Operator, block yang mengolah data di Blueprint Flow berdasarkan tipe data input utamanya.
pageDecoration:
  tree:
    priority: 13
tags: flowblock-category
---
# Flow Block Operator

>**note** Flow Block Operator merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Operator adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengolah data** di dalam Flow, seperti aritmatika, pengolahan teks, konversi, maupun translasi data. Setiap block dikelompokkan berdasarkan tipe data input utamanya, sehingga Anda dapat menemukan block yang tepat dari tipe data yang sedang diolah.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Operator bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Berbeda pula dengan block yang membaca atau mengubah data pada komponen seperti [[Docs/Modul Data/Variable/Apa itu Variable|Variable]], [[Docs/Modul Data/Enum/Apa itu Enum|Enum]], [[Docs/Modul Data/Table/Apa itu Table|Table]], dan [[Docs/Modul Data/Tree/Apa itu Tree|Tree]], block Operator hanya mengolah data yang sudah mengalir di dalam Flow.

![[Docs/Modul Logic/Flow/Flow Block/Operator/operator-block-flow.png|Flow Block Operator pada Blueprint: Increment, Concatenate, Implode, Pad Left, Pad Right, TableRow Parse, Assign, Merge, Parse, Stringify, If, dan Node Parse]]

Block Operator umumnya ditempatkan di tengah alur, di antara block yang menghasilkan data dan block yang memakainya. Hasil olahan dapat diteruskan ke block lain untuk disimpan, dikirim ke sistem lain, atau diolah lebih lanjut.

## Jenis Flow Block Operator

Phoenix menyediakan dua belas Flow Block Operator yang dikelompokkan berdasarkan tipe data input utamanya. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Tipe Data Input | Block | Fungsi |
| --- | --- | --- |
| [[Docs/Tipe Data/Number]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]] | Menambah nilai [[Docs/Tipe Data/Number]] sesuai langkah yang ditentukan, misalnya untuk penghitung atau penomoran berurutan. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]] | Menggabungkan beberapa [[Docs/Tipe Data/String]] menjadi satu [[Docs/Tipe Data/String]]. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode|Implode Operator Block]] | Menggabungkan kumpulan [[Docs/Tipe Data/String]] menjadi satu [[Docs/Tipe Data/String]] dengan pemisah tertentu. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left|Pad Left Operator Block]] | Menambahkan karakter pengisi di sisi kiri [[Docs/Tipe Data/String]] hingga mencapai panjang tertentu, misalnya nomor dengan angka nol di depan. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right|Pad Right Operator Block]] | Menambahkan karakter pengisi di sisi kanan [[Docs/Tipe Data/String]] hingga mencapai panjang tertentu. |
| [[Docs/Tipe Data/Table]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Table/TableRow Parse|TableRow Parse Operator Block]] | Mengurai [[Docs/Tipe Data/Row]] dari [[Docs/Tipe Data/Table]] menjadi [[Docs/Tipe Data/Object]]. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign|Assign Operator Block]] | Menetapkan nilai pada satu atribut [[Docs/Tipe Data/Object]]. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge|Merge Operator Block]] | Menggabungkan beberapa [[Docs/Tipe Data/Object]] menjadi satu [[Docs/Tipe Data/Object]]. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse|Parse Operator Block]] | Mengubah [[Docs/Tipe Data/String]] menjadi [[Docs/Tipe Data/Object]]. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify|Stringify Operator Block]] | Mengubah [[Docs/Tipe Data/Object]] menjadi [[Docs/Tipe Data/String]]. |
| [[Docs/Tipe Data/Boolean]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] | Mengevaluasi nilai [[Docs/Tipe Data/Boolean]] dari kondisi yang ditentukan. |
| [[Docs/Tipe Data/Tree]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Node Parse|Node Parse Operator Block]] | Mengurai [[Docs/Tipe Data/Node]] dari [[Docs/Tipe Data/Tree]] menjadi [[Docs/Tipe Data/Object]]. |

## Memilih Flow Block Operator

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menambah nilai [[Docs/Tipe Data/Number]] sesuai langkah tertentu, misalnya untuk penghitung atau penomoran berurutan. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]] |
| Menggabungkan beberapa [[Docs/Tipe Data/String]] menjadi satu. | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]] |
| Menggabungkan kumpulan [[Docs/Tipe Data/String]] menjadi satu dengan pemisah. | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode|Implode Operator Block]] |
| Membuat [[Docs/Tipe Data/String]] berpanjang tetap dengan karakter pengisi di kiri atau kanan. | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left|Pad Left Operator Block]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right|Pad Right Operator Block]] |
| Mengurai [[Docs/Tipe Data/Row]] menjadi [[Docs/Tipe Data/Object]] agar nilainya dapat dipakai block lain. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Table/TableRow Parse|TableRow Parse Operator Block]] |
| Mengisi satu atribut atau menggabungkan beberapa [[Docs/Tipe Data/Object]]. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign|Assign Operator Block]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge|Merge Operator Block]] |
| Mengonversi data antara [[Docs/Tipe Data/String]] dan [[Docs/Tipe Data/Object]]. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse|Parse Operator Block]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify|Stringify Operator Block]] |
| Menentukan hasil berdasarkan kondisi [[Docs/Tipe Data/Boolean]]. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] |
| Mengurai [[Docs/Tipe Data/Node]] menjadi [[Docs/Tipe Data/Object]] agar nilainya dapat dipakai block lain. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Node Parse|Node Parse Operator Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
