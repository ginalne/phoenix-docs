---
status: draft
title: Add Variable
description: Flow Block untuk menambahkan Variable Data baru dari dalam Flow.
pageDecoration:
  icon: zap
  tree:
    priority: 1
---
# Add Variable

>**note** Add Variable merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Add Variable adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk menambahkan [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] baru dari dalam Flow, tanpa membuka halaman kerja [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]. Block ini memiliki tiga input di sisi kiri dan dua output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/add-variable-block-flow.png|Flow Block Add Variable dengan tiga input dan dua output]]

## Input dan Output

Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Variable Data yang akan dibuat. Name harus unik karena menjadi alias untuk merujuk Variable Data dari komponen Logic. |
| [[^field|Value]] | Mengikuti tipe data yang Anda pilih. Awalnya tampil [[^field|N/A Type]]. | Nilai awal Variable Data. Tipe data yang dipilih untuk input ini ditentukan lewat [[#Menentukan Tipe Data Value]]. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan singkat tentang kegunaan Variable Data. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|New Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang berhasil dibuat. Bernilai [[^value/empty]] bila terjadi Name Conflict. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila [[^field|Name]] sudah dipakai Variable Data lain. Bernilai [[^value/empty]] bila Variable Data berhasil dibuat. |

### Menentukan Tipe Data Value

Input [[^field|Value]] pada block yang baru ditambahkan menampilkan teks merah [[^field|N/A Type]]. Teks ini berarti tipe data input belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan nilai yang akan disimpan, misalnya [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]].

>**note** Tipe data Value menentukan Type Variable Data
> Tipe data yang Anda pilih pada [[^field|Value]] menjadi Type dari Variable Data yang dibuat. Tipe ini juga menentukan tipe data output block lain yang membaca Variable Data tersebut, seperti [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]].

## Cara Kerja

1. Block menerima [[^field|Name]], [[^field|Value]], dan [[^field|Description]].
2. Block memeriksa apakah [[^field|Name]] sudah dipakai Variable Data lain.
3. Jika belum dipakai, Variable Data baru dibuat dan dikirim lewat [[^output|New Variable]], sedangkan [[^output|Name Conflict]] bernilai [[^value/empty]].
4. Jika sudah dipakai, tidak ada Variable Data yang dibuat. [[^output|New Variable]] bernilai [[^value/empty]] dan [[^output|Name Conflict]] bernilai [[^value/boolean/true]].

## Contoh Penggunaan

| Kondisi | [[^output|New Variable]] | [[^output|Name Conflict]] |
| ------- | ------------------------ | ------------------------- |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] dan belum dipakai Variable Data lain | Variable Data `batas_stok_minimum` yang baru dibuat | [[^value/empty]] |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] dan sudah dipakai Variable Data lain | [[^value/empty]] | [[^value/boolean/true]] |

Hubungkan [[^output|New Variable]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] bila Anda ingin langsung memakai nilai awalnya pada block berikutnya. Hubungkan [[^output|Name Conflict]] ke block yang menangani kegagalan, misalnya [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]].

## Praktik Terbaik

- **Tentukan tipe data [[^field|Value]] lebih dulu.** Pastikan [[^field|N/A Type]] sudah berganti menjadi tipe data yang Anda perlukan sebelum Flow dijalankan.
- **Periksa [[^output|Name Conflict]] di alur lanjutan.** Output ini memberi tahu Anda bahwa Variable Data tidak dibuat, sehingga alur tidak berlanjut dengan [[^output|New Variable]] yang [[^value/empty]].
- **Cek keberadaan Name dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** bila Anda ingin memutuskan sendiri apa yang dilakukan ketika Variable Data sudah ada.
- **Gunakan Name yang konsisten**, karena Name menjadi alias yang dipakai komponen Logic untuk merujuk Variable Data.

## Batasan dan Catatan

- Add Variable tidak menimpa Variable Data yang sudah ada. Untuk mengubah nilainya, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].
- Add Variable adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] hanya memiliki event [[^value/string|update]] dan [[^value/string|delete]], sehingga penambahan Variable Data tidak memicu Variable Event.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

<!--
  * [TODO] Letakkan screenshot block Add Variable (potong dari gambar yang Anda berikan) sebagai `add-variable-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Variable/`. Anotasi yang disarankan: nomor 1 sampai 3 untuk input Name, Value, Description dan nomor 4 sampai 5 untuk output New Variable dan Name Conflict.
  * [TODO] Konfirmasi pola halaman block Data: judul bagian saya tulis "Input dan Output" (bukan "Input, Control dan Output") karena block Data tidak memiliki Control. Bagian TL:DR dan FAQ sengaja tidak dibuat agar halaman block tetap ringkas. Beri tahu saya bila ingin ditambahkan.
  * [TODO] Konfirmasi perilaku Add Variable: (a) [[^output|Name Conflict]] saat berhasil saya tulis [[^value/empty]] mengikuti pola Variable Getter, (b) tipe data yang dipilih pada Value menjadi Type Variable Data, (c) apakah pencocokan Name membedakan huruf besar dan kecil, (d) apa yang terjadi bila Name kosong atau Value masih N/A Type, (e) apakah Description bertipe String atau Text.
  * [TODO] Daftar tipe data yang muncul pada Change Type dan target klik kanan (input Value atau seluruh block) belum terkonfirmasi.
  * [TODO] Halaman baru yang saya tautkan sebagai usulan: `Flow Block/Data Variable/Pengenalan`, `Flow Block/Menghubungkan Koneksi`, `Flow Block/Syarat Eksekusi`, dan `Flow Block/Event/Variable Event`. Isi yang diharapkan mengikuti pola halaman Flow Block lain.
  * [TODO] Nama contoh `batas_stok_minimum` saya ambil dari contoh Variable yang sudah ada. Sesuaikan bila perlu.
  * [TODO] Nilai `tree.priority` (1 sampai 6) mengikuti urutan block pada permintaan Anda. Sesuaikan dengan urutan di sidebar.
-->
