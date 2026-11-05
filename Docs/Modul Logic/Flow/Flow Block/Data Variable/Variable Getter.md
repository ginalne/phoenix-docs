---
status: draft
title: Variable Getter
description: Flow Block untuk mengambil Variable Data berdasarkan Name.
---
# Variable Getter

>**note** Variable Getter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Variable Getter adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk mengambil [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] dengan mengisi Name. Block ini menjadi pintu masuk bagi block Variable lain yang membutuhkan Variable Data sebagai input. Block ini memiliki satu input di sisi kiri dan dua output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/variable-getter-block-flow.png|Flow Block Variable Getter dengan satu input dan dua output]]
## Input dan Output

Input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Alias Variable Data yang dicari. Isi harus sama persis dengan Name Variable Data, termasuk huruf besar dan kecil serta karakter simbol. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang ditemukan. Bernilai [[^value/empty]] bila tidak ada Name yang cocok. |
| [[^output|Is Empty]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila Variable Data tidak ditemukan. Bernilai [[^value/boolean/false]] bila ditemukan. |

## Cara Kerja

1. Block menerima [[^field|Name]].
2. Block mencari Variable Data yang Name-nya sama persis.
3. Jika cocok, Variable Data dikirim lewat [[^output|Variable]] dan [[^output|Is Empty]] bernilai [[^value/boolean/false]].
4. Jika tidak cocok, [[^output|Variable]] bernilai [[^value/empty]] dan [[^output|Is Empty]] bernilai [[^value/boolean/true]].

Name Variable Data disimpan tanpa spasi, enter, atau karakter tak terlihat lain di awal dan akhir. Karena itu, tulis [[^field|Name]] tanpa karakter tersebut di awal dan akhir.

Input [[^field|Variable]] pada block lain berupa pilihan tetap. Gunakan Variable Getter bila Name Variable Data ditentukan saat Flow berjalan, misalnya berasal dari output block lain, atau bila Anda perlu menangani Variable Data yang tidak ditemukan. Variable Getter tidak dapat menimbulkan error. Bila Name tidak cocok, hasilnya diberitahukan lewat [[^output|Is Empty]].

## Contoh Penggunaan

| Kondisi | [[^output|Variable]] | [[^output|Is Empty]] |
| ------- | -------------------- | -------------------- |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] dan ada Variable Data dengan Name yang sama persis | Variable Data `batas_stok_minimum` | [[^value/boolean/false]] |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] tetapi tidak ada Variable Data dengan Name tersebut | [[^value/empty]] | [[^value/boolean/true]] |

Hubungkan [[^output|Variable]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] untuk membaca nilainya, ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]] untuk mengubahnya, atau ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Delete Variable|Delete Variable Block]] untuk menghapusnya. Hubungkan [[^output|Is Empty]] ke [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]] untuk memisahkan alur saat Variable Data tidak ditemukan.

## Praktik Terbaik

- **Periksa [[^output|Is Empty]] sebelum memakai [[^output|Variable]].** Dengan begitu alur tidak berlanjut membawa [[^value/empty]].
- **Tulis [[^field|Name]] persis seperti di komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]**, termasuk huruf besar dan kecil serta tanda baca.
- **Gunakan Variable Getter sebagai awal rangkaian block Variable** agar penanganan Variable Data yang tidak ditemukan cukup ditulis satu kali.

## Batasan dan Catatan

- Variable Getter hanya mengambil Variable Data dan tidak mengubahnya.
- Pencocokan [[^field|Name]] membedakan huruf besar dan kecil serta menerima karakter simbol, sehingga Name yang hanya mirip tidak dianggap cocok.
- Variable Getter adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Anggota yang tidak memiliki akses ke komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tetap dapat memakai Variable Data lewat Flow, tetapi tidak dapat melihat Value-nya di halaman kerja.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

