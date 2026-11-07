---
status: draft
title: Flow Block Operator
description: Pengenalan kategori Flow Block Operator, block yang mengolah data di Blueprint Flow berdasarkan tipe data input utamanya.
pageDecoration:
  tree:
    priority: 13
tags: flowblock-category
---
,’;;;/;# Flow Block Operator

>**note** Flow Block Operator merupakan salah satu kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Flow Block Operator adalah kategori [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] yang digunakan untuk **mengolah data** di dalam Flow, seperti aritmatika, pengolahan teks, konversi, maupun translasi data. Setiap block dikelompokkan berdasarkan tipe data input utamanya, sehingga Anda dapat menemukan block yang tepat dari tipe data yang sedang diolah.

Berbeda dengan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] yang menjadi titik awal alur, block Operator bekerja setelah menerima data dari block sebelumnya, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]. Berbeda pula dengan block yang membaca atau mengubah data pada komponen seperti [[Docs/Modul Data/Variable/Apa itu Variable|Variable]], [[Docs/Modul Data/Enum/Apa itu Enum|Enum]], [[Docs/Modul Data/Table/Apa itu Table|Table]], dan [[Docs/Modul Data/Tree/Apa itu Tree|Tree]], block Operator hanya mengolah data yang sudah mengalir di dalam Flow.

![[Docs/Modul Logic/Flow/Flow Block/Operator/operator-block-flow.png|Flow Block Operator pada Blueprint: Increment, Concatenate, Implode, Pad Left, Pad Right, TableRow Parse, Assign, Merge, Parse, Stringify, If, dan Node Parse]]

<!--
  * [TODO] Tambahkan screenshot Blueprint yang memuat seluruh Flow Block Operator dengan nama file `operator-block-flow.png`. Anotasi yang disarankan: penanda nomor pada setiap block dan pengelompokan warna atau garis per tipe data input (Number, String, Table, Object, Boolean, Tree).
-->

Block Operator umumnya ditempatkan di tengah alur, di antara block yang menghasilkan data dan block yang memakainya. Hasil olahan dapat diteruskan ke block lain untuk disimpan, dikirim ke sistem lain, atau diolah lebih lanjut.

## Jenis Flow Block Operator

Phoenix menyediakan dua belas Flow Block Operator yang dikelompokkan berdasarkan tipe data input utamanya. Setiap block memiliki fungsi yang unik, sehingga input dan output-nya berbeda-beda.

| Tipe Data Input | Block | Fungsi |
| --- | --- | --- |
| [[Docs/Tipe Data/Number]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]] | Menambah nilai [[Docs/Tipe Data/Number]], misalnya untuk penghitung atau penomoran berurutan. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]] | Menggabungkan beberapa [[Docs/Tipe Data/String]] menjadi satu [[Docs/Tipe Data/String]]. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode|Implode Operator Block]] | Menggabungkan sekumpulan nilai menjadi satu [[Docs/Tipe Data/String]] dengan pemisah tertentu. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left|Pad Left Operator Block]] | Menambahkan karakter pengisi di sisi kiri [[Docs/Tipe Data/String]] hingga mencapai panjang tertentu, misalnya nomor dengan angka nol di depan. |
| [[Docs/Tipe Data/String]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right|Pad Right Operator Block]] | Menambahkan karakter pengisi di sisi kanan [[Docs/Tipe Data/String]] hingga mencapai panjang tertentu. |
| [[Docs/Tipe Data/Table]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Table/TableRow Parse|TableRow Parse Operator Block]] | Mengurai [[Docs/Tipe Data/Row]] dari [[Docs/Tipe Data/Table]] menjadi nilai-nilai yang dapat dipakai block lain. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign|Assign Operator Block]] | Menetapkan nilai pada [[Docs/Tipe Data/Object]]. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge|Merge Operator Block]] | Menggabungkan beberapa [[Docs/Tipe Data/Object]] menjadi satu [[Docs/Tipe Data/Object]]. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse|Parse Operator Block]] | Mengubah [[Docs/Tipe Data/String]] menjadi [[Docs/Tipe Data/Object]]. |
| [[Docs/Tipe Data/Object]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify|Stringify Operator Block]] | Mengubah [[Docs/Tipe Data/Object]] menjadi [[Docs/Tipe Data/String]]. |
| [[Docs/Tipe Data/Boolean]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] | Mengevaluasi nilai [[Docs/Tipe Data/Boolean]] dan menentukan hasil berdasarkan kondisi tersebut. |
| [[Docs/Tipe Data/Tree]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Node Parse|Node Parse Operator Block]] | Mengurai [[Docs/Tipe Data/Node]] dari [[Docs/Tipe Data/Tree]] menjadi nilai-nilai yang dapat dipakai block lain. |

<!--
  * [TODO] Konfirmasi fungsi Increment Operator Block. Draf menyebut "menambah nilai Number". Apakah penambahnya dapat ditentukan (langkah tertentu), atau selalu bertambah satu?
    Jawaban: Ada langkah yang ditentukan, akan dijelaskan lebih detail dalam halamannya sendiri
  * [TODO] Konfirmasi input utama Implode Operator Block. Draf menyebut "sekumpulan nilai" karena input utamanya mungkin [[Docs/Tipe Data/Array]], padahal block ini dikelompokkan pada String.
    Jawaban: 
  * [TODO] Konfirmasi fungsi TableRow Parse dan Node Parse Operator Block, termasuk bentuk hasil urainya (apakah menghasilkan [[Docs/Tipe Data/Object]] atau output per atribut).
  * [TODO] Konfirmasi fungsi Assign Operator Block. Draf menyebut "menetapkan nilai pada Object". Apakah yang ditetapkan adalah satu atribut (key) atau seluruh isi Object?
  * [TODO] Konfirmasi fungsi If Operator Block. Draf menyebut "menentukan hasil berdasarkan kondisi". Apakah block ini memilih nilai (seperti *ternary*) atau menentukan jalur aliran? Perlu dibedakan dengan [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]].
  * [TODO] Halaman block yang diusulkan mengikuti pola `Docs/Modul Logic/Flow/Flow Block/Operator/<Tipe Data>/<Nama Block>` seperti pada tabel di atas. Apakah setiap kelompok tipe data (Number, String, Table, Object, Boolean, Tree) perlu halaman `Pengenalan` sendiri?
    Jawaban: Tidak perlu pengenalan per masing-masing kelompok. Langsung ke halaman Flow block masing. Tapi akan dilanjutkan nanti, jangan sekarang.
-->

## Memilih Flow Block Operator

| Kebutuhan Anda | Block yang dipilih |
| --- | --- |
| Menambah nilai [[Docs/Tipe Data/Number]] untuk penghitung atau penomoran berurutan. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]] |
| Menggabungkan beberapa [[Docs/Tipe Data/String]] menjadi satu. | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]] |
| Menggabungkan sekumpulan nilai menjadi satu [[Docs/Tipe Data/String]] dengan pemisah. | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode|Implode Operator Block]] |
| Membuat [[Docs/Tipe Data/String]] berpanjang tetap dengan karakter pengisi di kiri atau kanan. | [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left|Pad Left Operator Block]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right|Pad Right Operator Block]] |
| Mengurai [[Docs/Tipe Data/Row]] agar nilainya dapat dipakai block lain. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Table/TableRow Parse|TableRow Parse Operator Block]] |
| Mengisi atau menggabungkan [[Docs/Tipe Data/Object]]. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign|Assign Operator Block]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge|Merge Operator Block]] |
| Mengonversi data antara [[Docs/Tipe Data/String]] dan [[Docs/Tipe Data/Object]]. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse|Parse Operator Block]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify|Stringify Operator Block]] |
| Menentukan hasil berdasarkan kondisi [[Docs/Tipe Data/Boolean]]. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] |
| Mengurai [[Docs/Tipe Data/Node]] agar nilainya dapat dipakai block lain. | [[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Node Parse|Node Parse Operator Block]] |

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]]
- [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]
