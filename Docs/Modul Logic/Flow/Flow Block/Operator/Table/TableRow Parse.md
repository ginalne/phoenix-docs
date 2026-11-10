---
status: draft
title: TableRow Parse Operator Block
description: Mengubah Row menjadi Object dan Text dengan penelusuran relasi sesuai Rel. Depth pada Flow Block Operator TableRow Parse.
---

# TableRow Parse Operator Block

>**note** TableRow Parse Block merupakan salah satu Flow Block kelompok Table pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

TableRow Parse Block adalah Flow Block Operator yang mengubah [[^input|Row]] ([[Docs/Tipe Data/Row]]) menjadi data [[Docs/Tipe Data/Object]] dan [[Docs/Tipe Data/Text]]. [[^input|Rel. Depth]] menentukan kedalaman relasi: bila kolom pada Row memiliki relasi ke data lain, hasil kolom tersebut ditelusuri sehingga data menjadi semakin rinci.

![[Docs/Modul Logic/Flow/Flow Block/Operator/Table/tablerow-parse-block-flow.png|TableRow Parse Block pada Blueprint Flow]]

<!--
  * [DONE] Penempatan gambar: potong dari screenshot Operator, simpan sebagai `tablerow-parse-block-flow.png` di folder yang sama dengan halaman ini.
  * [TODO] Teks penulis berbunyi "Fatal Error jika Row dibiarkan error". Ditulis sebagai "dibiarkan kosong" (diduga salah ketik). Mohon konfirmasi.
  * [TODO] Konfirmasi: (a) bentuk Text hasil (diasumsikan teks JSON dari Object), (b) Rel. Depth 1 berarti menelusuri satu tingkat relasi, (c) kolom berelasi yang tidak ditelusuri tampil sebagai nilai aslinya (diasumsikan ID/Index Row terkait).
    Jawaban: Sudah benar, namun pada Contoh Penggunaan tambahkan isi dari Row Pesanan. semisal pada depth = 0 adalah { “penerima”: “1 : Anna”, Total: 1200 }, namun pada depth = 1 adalah { “penerima” : {“id”: 1,  “nama”: “Anna”, “kelamin”:“Perempuan”, “no telp”: “123456”}, “Total”: 1200 }
-->

## Input dan Output

TableRow Parse Block memiliki 2 input di sisi kiri, 2 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila terhubung ke block lain. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Row]] | [[Docs/Tipe Data/Row]] | Row yang akan diubah. Tidak boleh kosong. Dapat diambil dari output [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]]. |
| [[^input|Rel. Depth]] | [[Docs/Tipe Data/Number]] | Kedalaman penelusuran relasi kolom. Bila dibiarkan kosong, dianggap bernilai [[^value/number|0]]. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Object]] | [[Docs/Tipe Data/Object]] | Data Row dalam bentuk Object. Aliran diteruskan bila output terhubung. |
| [[^output|Text]] | [[Docs/Tipe Data/Text]] | Data Row dalam bentuk Text. Aliran diteruskan bila output terhubung. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. TableRow Parse Block menerima [[^input|Row]] dan [[^input|Rel. Depth]].
2. Block mengubah isi Row menjadi data berpasangan kolom dan nilainya.
3. Bila kolom pada Row berelasi ke data lain, block menelusurinya sesuai Rel. Depth sehingga hasilnya memuat data relasi yang lebih rinci.
4. Hasilnya dikeluarkan lewat [[^output|Object]] atau [[^output|Text]] sesuai output yang terhubung.

## Contoh Penggunaan

| Row | Rel. Depth | Hasil | Status |
| --- | ---------- | ----- | ------ |
| [[^value/row|Row pesanan]] | [[^value/empty]] | Row diubah tanpa menelusuri relasi (sama seperti Rel. Depth [[^value/number|0]]). | [[^flowstate|Succeed]] |
| [[^value/row|Row pesanan]] | [[^value/number|0]] | Row diubah tanpa menelusuri relasi. | [[^flowstate|Succeed]] |
| [[^value/row|Row pesanan]] | [[^value/number|1]] | Kolom berelasi ditelusuri sehingga data relasinya ikut tersaji. | [[^flowstate|Succeed]] |
| [[^value/empty]] | [[^value/number|1]] | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Mulailah dengan **Rel. Depth** kecil, lalu naikkan hanya bila data relasi memang dibutuhkan, agar hasil tidak lebih besar dari kebutuhan.
- Hubungkan hanya output yang dipakai: [[^output|Object]] untuk diolah lebih lanjut (misalnya dengan [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign|Assign Operator Block]]) dan [[^output|Text]] untuk dikirim atau ditampilkan sebagai teks.

## Batasan dan Catatan

- TableRow Parse Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|Row]] yang dibiarkan kosong menghasilkan status [[^flowstate|Fatal Error]].
- [[^input|Rel. Depth]] yang dibiarkan kosong dianggap bernilai [[^value/number|0]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/Tree/Node Parse|Node Parse Operator Block]]
- [[Docs/Tipe Data/Row]]