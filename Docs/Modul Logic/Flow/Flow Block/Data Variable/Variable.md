---
status: draft
title: Variable
description: Flow Block untuk mengurai Variable Data menjadi nilai atributnya.
pageDecoration:
  icon: zap
  tree:
    priority: 3
---
# Variable

>**note** Variable merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Variable adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk mengubah satu [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] menjadi nilai atributnya, yaitu Name, Description, dan Value. Block ini memiliki satu input di sisi kiri dan empat output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/variable-block-flow.png|Flow Block Variable dengan satu input dan empat output]]

## Input dan Output

Input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang akan diurai. Isi dengan Name Variable Data (alias) atau hubungkan dari output block lain, misalnya [[^output|Variable]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Pass]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila Variable Data berhasil diurai. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | Name dari Variable Data. |
| [[^output|Description]] | [[Docs/Tipe Data/String]] | Description dari Variable Data. |
| [[^output|Value]] | Mengikuti Type Variable Data | Value dari Variable Data. |

## Cara Kerja

1. Block menerima Variable Data lewat [[^field|Variable]].
2. Block membaca atribut Variable Data dan mengirimkannya lewat [[^output|Name]], [[^output|Description]], dan [[^output|Value]].
3. Tipe data [[^output|Value]] mengikuti Type Variable Data. Jika Variable Data bertipe [[Docs/Tipe Data/Number]], [[^output|Value]] berupa [[Docs/Tipe Data/Number]].

Gunakan Variable bila Anda membutuhkan lebih dari satu atribut. Bila hanya membutuhkan nilainya, [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] lebih ringkas.

## Contoh Penggunaan

| Kondisi | [[^output|Pass]] | [[^output|Name]] | [[^output|Description]] | [[^output|Value]] |
| ------- | ---------------- | ---------------- | ----------------------- | ----------------- |
| [[^field|Variable]] berisi Variable Data [[^value/string|batas_stok_minimum]] bertipe [[Docs/Tipe Data/Number]] dengan nilai [[^value/number|50]] | [[^value/boolean/true]] | [[^value/string|batas_stok_minimum]] | Description Variable Data | [[^value/number|50]] |
| [[^field|Variable]] kosong atau tidak valid | [[^value/empty]] | [[^value/empty]] | [[^value/empty]] | [[^value/empty]] |

Hubungkan [[^output|Name]] dan [[^output|Description]] ke block yang menyusun pesan, misalnya [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]], dan hubungkan [[^output|Value]] ke block yang membandingkan atau menghitung.

## Praktik Terbaik

- **Pasangkan dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** agar Variable Data diambil lewat Name dan kegagalannya dapat ditangani lewat [[^output|Is Empty]].
- **Gunakan [[^output|Pass]]** untuk memastikan Variable Data berhasil diurai sebelum memakai [[^output|Name]], [[^output|Description]], atau [[^output|Value]].

## Batasan dan Catatan

- Variable hanya membaca data dan tidak mengubah Variable Data. Untuk mengubah nilainya, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].
- Variable adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Tipe data [[^output|Value]] berbeda untuk setiap Variable Data, sehingga block penerima harus mendukung tipe data tersebut.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

<!--
  * [TODO] Letakkan screenshot block Variable sebagai `variable-block-flow.png` di folder `Docs/Modul Logic/Flow/Flow Block/Data Variable/`. Anotasi yang disarankan: nomor 1 untuk input Variable dan nomor 2 sampai 5 untuk output Pass, Name, Description, Value.
  * [TODO] Konfirmasi arti output Pass. Saya tulis sebagai Boolean true bila Variable Data berhasil diurai, dan empty bila gagal. Mohon konfirmasi nilai dan tipe datanya.
  * [TODO] Konfirmasi tipe data output Name dan Description (saya asumsikan String) dan apakah tipe data Value benar mengikuti Type Variable Data.
  * [TODO] Baris tabel Contoh Penggunaan untuk Variable kosong atau tidak valid (seluruh output empty) adalah asumsi saya.
  * [TODO] Tautan `Flow Block/Operator/String/Concatenate` adalah halaman yang sudah ada pada daftar path. Ganti bila Anda lebih memilih contoh block lain.
-->
