---
status: draft
title: Parse Operator Block
description: Mengubah Text menjadi Object pada Flow Block Operator Parse.
---

# Parse Operator Block

>**note** Parse Block merupakan salah satu Flow Block kelompok Object pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Parse Block adalah Flow Block Operator yang mengubah [[^input|Text]] bertipe [[Docs/Tipe Data/Text]] menjadi data bertipe [[Docs/Tipe Data/Object]] lewat [[^output|Object]]. Bila Text tidak sesuai kaidah Object (JSON), block mengeluarkan [[^output|Error]] sehingga Anda dapat menanganinya di Flow.

![[Docs/Modul Logic/Flow/Flow Block/Operator/Object/parse-block-flow.png|Parse Block pada Blueprint Flow]]

## Input dan Output

Parse Block memiliki 1 input di sisi kiri, 2 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Text]] | [[Docs/Tipe Data/Text]] | Text berformat Object (JSON) yang akan diubah. Tidak boleh kosong. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Object]] | [[Docs/Tipe Data/Object]] | Object hasil pengubahan. Aliran diteruskan bila Text sesuai kaidah Object. |
| [[^output|Error]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Text tidak sesuai kaidah Object dan aliran diteruskan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

> **note** Mengelola Error
> Hubungkan output [[^output|Error]] ke block penanganan agar Flow dapat memberi tahu pengguna bila Text tidak valid. Block tersebut hanya dieksekusi saat kegagalan terjadi.

## Cara Kerja

1. Parse Block menerima [[^input|Text]].
2. Block memeriksa apakah Text sesuai kaidah Object (JSON).
3. Bila sesuai, Text diubah menjadi Object dan dikeluarkan lewat [[^output|Object]].
4. Bila tidak sesuai, block mengeluarkan [[^output|Error]].

## Contoh Penggunaan

| Text | Object | Error | Status |
| ---- | ------ | ----- | ------ |
| [[^value/text|{ "nama": "Kopi", "harga": 15000 }]] | [[^value/object|{ "nama": "Kopi", "harga": 15000 }]] | - | [[^flowstate|Succeed]] |
| [[^value/text|{ nama: Kopi]] | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^value/empty]] | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Error]] dan [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Selalu **hubungkan output Error** ke block penanganan bila Text berasal dari sumber luar, misalnya respons [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]].
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify|Stringify Operator Block]] untuk proses kebalikannya, yaitu mengubah Object menjadi Text.

## Batasan dan Catatan

- Parse Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|Text]] yang dibiarkan kosong menghasilkan status [[^flowstate|Fatal Error]], berbeda dengan Text yang terisi tetapi tidak sesuai kaidah Object yang mengeluarkan output [[^output|Error]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify|Stringify Operator Block]]
- [[Docs/Tipe Data/Object]]