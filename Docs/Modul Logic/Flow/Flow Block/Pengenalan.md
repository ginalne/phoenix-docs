---
status: draft
title: "Apa itu Flow Block?"
description: Flow Block adalah unit terkecil penyusun Flow yang tersusun dari Trigger, Input, Control, dan Output untuk membangun logika.
pageDecoration:
  tree:
    priority: 10
---
# Apa itu Flow Block?

>**note** Flow Block merupakan bagian dari komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] dalam modul [[Docs/Modul Logic/Pengenalan|Logic]] di Phoenix.

Flow Block adalah unit terkecil penyusun Flow. Setiap block memiliki fungsi, masukan, proses, dan keluaran yang berbeda-beda, dan dapat dihubungkan dengan block lain di [[Docs/Modul Logic/Flow/Apa itu Flow#Antarmuka Flow|Blueprint]] untuk membentuk logika.

Setiap Flow Block tersusun dari [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Trigger]], [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Input]], [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Control]], dan [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output]]. Prinsip pada halaman ini berlaku untuk semua jenis Flow Block, sehingga halaman setiap jenis hanya menjelaskan bagian yang khas bagi block tersebut.

## Jenis Flow Block

Pengkategorian Flow Block berfungsi agar memudahkan pencarian block. Selengkapnya bisa klik tautan per masing-masing kategori atau isinya.
 
| Kategori | Jenis Flow Block |
| --- | --- |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Event]] | [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser]], [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event]], [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event]] |
| [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Data Variable]] | [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Add Variable]], [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Delete Variable]], [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable]], [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter]], [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter]], [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value]] |
| [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Data Enum]] | [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Enum]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value]] |
| [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Data Table]] | [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row]], [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row]], [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table]], [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column]], [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row]], [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter]], [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter]] |
| [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Pengenalan|Data Tree]] | [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Add Node]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Assign Node]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Delete Node]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Ancestor]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Children]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Get Parent]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Node Setter]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree]], [[Docs/Modul Logic/Flow/Flow Block/Data Tree/Tree Get Origin]] |
| [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Pengenalan|I/O]] | [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch]], [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer]] |
| [[Docs/Modul Logic/Flow/Flow Block/Query/Pengenalan|Query]] | [[Docs/Modul Logic/Flow/Flow Block/Query/Condition]], [[Docs/Modul Logic/Flow/Flow Block/Query/Execute]] |
| [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Operator]] | [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Pengenalan|Number]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pengenalan|String]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left]], [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Table/Pengenalan|Table]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Table/TableRow Parse]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Pengenalan|Object]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Parse]], [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Stringify]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/Pengenalan|Boolean]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If]]); [[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Pengenalan|Tree]] ([[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Node Parse]]) |
| [[Docs/Modul Logic/Flow/Flow Block/Modular/Pengenalan|Modular]] | [[Docs/Modul Logic/Flow/Flow Block/Modular/API/Pengenalan|API]] ([[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request]]); [[Docs/Modul Logic/Flow/Flow Block/Modular/AI/Pengenalan|AI]] ([[Docs/Modul Logic/Flow/Flow Block/Modular/AI/OpenAI 4]]) |
| Misc | [[Docs/Modul Logic/Flow/Flow Block/Chrono/Pengenalan|Chrono]] ([[Docs/Modul Logic/Flow/Flow Block/Chrono/Delay]]); [[Docs/Modul Logic/Flow/Flow Block/Error/Pengenalan|Error]] ([[Docs/Modul Logic/Flow/Flow Block/Error/Error Message]]) |

## Mengelola Flow Block

Berikut adalah cara mengelola Flow Block didalam Flow:

1. [[Docs/Modul Logic/Flow/Flow Block/Menambahkan]]
2. [[Docs/Modul Logic/Flow/Flow Block/Menghapus]]
3. [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi]]
4. [[Docs/Modul Logic/Flow/Flow Block/Menghapus Koneksi]]

## Antarmuka

Penjelasan antarmuka Flow Block lihat selengkap nya di [[Docs/Modul Logic/Flow/Flow Block/Antarmuka|Antarmuka Flow Block]].

## Aturan Koneksi

Penjelasan aturan koneksi lihat selengkap nya di [[Docs/Modul Logic/Flow/Flow Block/Aturan Koneksi]].

## Syarat Eksekusi

Penjelasan syarat agar Flow Block dapat dieksekusi lihat selengkap nya di [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].

## TL:DR

- Flow Block adalah unit terkecil penyusun Flow yang tersusun dari [[#Trigger]], [[#Input]], [[#Control]], dan [[#Output]]. Tidak semua jenis memiliki keempatnya.
- Setiap [[#Output]] hanya terhubung ke satu [[#Input]] atau [[#Trigger]], sedangkan Input dan Trigger dapat menerima koneksi sebanyak mungkin ([[#Aturan Koneksi]]).
- Flow Block non-Event diproses bila setiap Input yang terhubung sudah berisi data dan Trigger berisi data setidaknya satu. Trigger yang tidak terhubung selalu aktif ([[#Syarat Flow Block Diproses]]).
- Input yang tidak terhubung menampilkan field isian, dan banyak koneksi pada satu Input dibaca sebagai [[Docs/Tipe Data/Array]].
- [[#Control]] dapat memengaruhi proses block atau memicu Activity baru.
- Error karena Input wajib kosong atau tipe data tidak cocok tampil di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apa bedanya Trigger dan Input?**
> [[#Trigger]] menjadi syarat agar block dijalankan, sedangkan [[#Input]] adalah masukan data yang diproses block.
> **Mengapa Flow Block saya tidak berjalan?**
> Periksa [[#Syarat Flow Block Diproses]]: setiap Input yang terhubung harus sudah berisi data dan Trigger harus berisi data setidaknya satu. Flow Block non-Event yang tidak terhubung pada Trigger maupun Input juga tidak akan aktif dalam Activity.
> **Dapatkah satu Output dihubungkan ke beberapa block?**
> Tidak. Setiap [[#Output]] hanya dapat terhubung dengan satu Input atau Trigger block lain, lihat [[#Aturan Koneksi]].
> **Apa yang terjadi jika beberapa Output dihubungkan ke satu Input?**
> Data dari seluruh koneksi dibaca sebagai [[Docs/Tipe Data/Array]]. Pengecualian berlaku bila ada koneksi rekursif, lihat [[#Input]].
> **Mengapa field isian pada Input hilang?**
> Field isian hanya tampil pada [[#Input]] yang tidak terhubung. Ketika Input terhubung ke Output block lain, nilainya berasal dari koneksi tersebut.

