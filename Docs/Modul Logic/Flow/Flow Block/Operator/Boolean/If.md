---
status: draft
title: If Operator Block
description: Membandingkan dua nilai dengan operator dan melanjutkan aliran sesuai hasilnya pada Flow Block Operator If.
---

# If Operator Block

>**note** If Block merupakan salah satu Flow Block kelompok Boolean pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

If Block adalah Flow Block Operator yang membandingkan [[^input|A]] dan [[^input|B]] dengan [[^input|Operator]], lalu melanjutkan aliran lewat [[^output|True]] atau [[^output|False]] sesuai hasil perbandingannya. Hasil tersebut juga dapat dikeluarkan sebagai nilai [[Docs/Tipe Data/Boolean]] lewat [[^output|Boolean]].

![[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/if-block-flow.png|If Block pada Blueprint Flow]]

<!--
  * [DONE] Penempatan gambar: potong dari screenshot Operator, simpan sebagai `if-block-flow.png` di folder yang sama dengan halaman ini.
  * [TODO] Konfirmasi: tipe data input Operator (diasumsikan String) dan simbol operator pada contoh (memakai `>`). Daftar simbol lengkap mengikuti [[Docs/Expression/Operator]].
  * [TODO] Perbedaan If dengan Branch Block belum terkonfirmasi (knowledge), jadi tidak dibahas di halaman ini.
-->

## Input dan Output

If Block memiliki 3 input di sisi kiri, 3 output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|A]] | Tipe apa pun | Nilai pertama yang dibandingkan. Tampil [[^field|N/A Type]] sampai tipenya ditentukan (lihat [[#Menentukan Tipe Data A dan B]]). |
| [[^input|Operator]] | [[Docs/Tipe Data/String]] | Simbol operator yang valid. Selengkapnya lihat [[Docs/Expression/Operator]]. Tidak boleh kosong. |
| [[^input|B]] | Tipe apa pun | Nilai kedua yang dibandingkan. Tampil [[^field|N/A Type]] sampai tipenya ditentukan. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Boolean]] | [[Docs/Tipe Data/Boolean]] | Hasil perbandingan ([[^value/boolean/true]] atau [[^value/boolean/false]]). Keluar bila output terhubung ke block lain. |
| [[^output|True]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila hasil perbandingan benar dan aliran diteruskan. |
| [[^output|False]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/false]] bila hasil perbandingan salah dan aliran diteruskan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

### Menentukan Tipe Data A dan B

1. Klik kanan pada input [[^input|A]] atau [[^input|B]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan nilai yang dibandingkan.

## Cara Kerja

1. If Block menerima [[^input|A]], [[^input|Operator]], dan [[^input|B]].
2. Block membandingkan A dan B dengan Operator.
3. Bila hasilnya benar, aliran dilanjutkan lewat [[^output|True]]. Bila salah, aliran dilanjutkan lewat [[^output|False]].
4. Output [[^output|Boolean]] mengeluarkan hasil perbandingan bila terhubung.

## Contoh Penggunaan

| A | Operator | B | Boolean | True | False | Status |
| - | -------- | - | ------- | ---- | ----- | ------ |
| [[^value/number|10]] | `>` | [[^value/number|5]] | [[^value/boolean/true]] | [[^value/boolean/true]] | - | [[^flowstate|Succeed]] |
| [[^value/number|3]] | `>` | [[^value/number|5]] | [[^value/boolean/false]] | - | [[^value/boolean/false]] | [[^flowstate|Succeed]] |
| [[^value/number|10]] | [[^value/empty]] | [[^value/number|5]] | - | - | - | [[^flowstate|Fatal Error]] |
| [[^field|N/A Type]] | `>` | [[^value/number|5]] | - | - | - | [[^flowstate|Fatal Error]] |
| [[^value/number|10]] | `>` | [[^field|N/A Type]] | - | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Hubungkan **block penanganan langsung** ke output [[^output|True]] dan [[^output|False]] sesuai tindakan yang diinginkan pada tiap hasil.
- **Tentukan tipe data** A dan B sebelum menjalankan Flow, terutama bila nilainya tidak berasal dari koneksi.
- Gunakan [[^output|Boolean]] bila hasil perbandingan perlu disimpan atau diteruskan sebagai nilai, misalnya ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].

## Batasan dan Catatan

- If Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|Operator]] yang dibiarkan kosong, atau [[^input|A]] atau [[^input|B]] yang masih [[^field|N/A Type]], menghasilkan status [[^flowstate|Fatal Error]].
- Hanya salah satu dari output [[^output|True]] atau [[^output|False]] yang meneruskan aliran pada setiap eksekusi.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Expression/Operator]]
- [[Docs/Tipe Data/Boolean]]