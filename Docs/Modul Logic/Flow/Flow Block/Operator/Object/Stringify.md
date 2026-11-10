---
status: draft
title: Stringify Operator Block
description: Mengubah Object menjadi Text pada Flow Block Operator Stringify.
---

# Stringify Operator Block

>**note** Stringify Block merupakan salah satu Flow Block kelompok Object pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Stringify Block adalah Flow Block Operator yang mengubah [[^input|Object]] bertipe [[Docs/Tipe Data/Object]] menjadi [[Docs/Tipe Data/Text]] lewat [[^output|Text]]. Block ini tidak menghasilkan error pada format Object karena Object yang valid pasti sesuai kaidah Object (JSON).

![[Docs/Modul Logic/Flow/Flow Block/Operator/Object/stringify-block-flow.png|Stringify Block pada Blueprint Flow]]

<!--
  * [DONE] Penempatan gambar: potong dari screenshot Operator, simpan sebagai `stringify-block-flow.png` di folder yang sama dengan halaman ini.
    Jawaban: Sudah benar
-->

## Input dan Output

Stringify Block memiliki 1 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Object]] | [[Docs/Tipe Data/Object]] | Object yang akan diubah menjadi Text. Tidak boleh kosong. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Text]] | [[Docs/Tipe Data/Text]] | Object dalam bentuk Text. Aliran diteruskan setiap kali block berhasil dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Stringify Block menerima [[^input|Object]].
2. Block mengubah Object menjadi Text berformat Object (JSON).
3. Hasilnya dikeluarkan lewat [[^output|Text]].

## Contoh Penggunaan

| Object | Text | Status |
| ------ | ---- | ------ |
| [[^value/object|{ "nama": "Kopi", "harga": 15000 }]] | [[^value/text|{ "nama": "Kopi", "harga": 15000 }]] | [[^flowstate|Succeed]] |
| [[^value/empty]] | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Gunakan Stringify bila data Object perlu **dikirim atau ditampilkan sebagai teks**, misalnya sebagai isi permintaan pada [[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]].
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse|Parse Operator Block]] untuk proses kebalikannya, yaitu mengubah Text menjadi Object.

## Batasan dan Catatan

- Stringify Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|Object]] yang dibiarkan kosong menghasilkan status [[^flowstate|Fatal Error]].
- Block ini tidak memiliki output Error karena Object selalu sesuai kaidah Object (JSON).

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse|Parse Operator Block]]
- [[Docs/Tipe Data/Text]]