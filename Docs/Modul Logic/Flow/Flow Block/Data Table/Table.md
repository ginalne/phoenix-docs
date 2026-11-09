---
status: draft
title: Table Block
description: Flow Block Data Table untuk mengambil atribut dari sebuah Table, yaitu Name dan Description.
---
# Table Block

>**note** Table Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Table Block adalah Flow Block yang menerima [[Docs/Tipe Data/Table]] dan mengeluarkan atributnya, yaitu [[^field|Name]] dan [[^field|Description]]. Gunakan block ini saat alur Anda membutuhkan identitas [[Docs/Tipe Data/Table]], misalnya untuk menyusun pesan atau menentukan tujuan proses berikutnya.

![[Docs/Modul Logic/Flow/Flow Block/Data Table/table-block-flow.png|Table Block pada Blueprint]]
## Input dan Output

Table Block memiliki satu input di sisi kiri, tiga output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada aliran keluar. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Table]] | [[Docs/Tipe Data/Table]] | Table yang atributnya akan diambil. Isi dengan Table atau hubungkan dari output block lain. Dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass]] | [[Docs/Tipe Data/Table]] | Meneruskan [[Docs/Tipe Data/Table]] yang diinput ke block berikutnya. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | Nama Table. |
| [[^output|Desc]] | [[Docs/Tipe Data/Text]] | Deskripsi Table. Tetap meneruskan aliran dengan nilai [[^value/empty]] bila Description Table kosong. |

Ketiga output meneruskan aliran bila [[^input|Table]] terisi, dan tidak meneruskan aliran bila terjadi [[^flowstate|Fatal Error]]. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block memeriksa [[^input|Table]]. Bila kosong, block berhenti dengan [[^flowstate|Fatal Error]].
2. Block membaca atribut [[Docs/Tipe Data/Table]] yang diinput.
3. [[^output|Pass]], [[^output|Name]], dan [[^output|Desc]] diteruskan bersamaan ke block yang terhubung.

## Contoh Penggunaan

Mengambil nama dan deskripsi [[^field/table|Pesanan]] untuk dicantumkan pada catatan proses.

| Kondisi | [[^output|Pass]] | [[^output|Name]] | [[^output|Desc]] | Status |
| - | - | - | - | - |
| [[^input|Table]] berisi Table pesanan yang memiliki deskripsi | [[Docs/Tipe Data/Table]] | Nama Table | Deskripsi Table | [[^flowstate|Succeed]] |
| [[^input|Table]] berisi Table pesanan tanpa deskripsi | [[Docs/Tipe Data/Table]] | Nama Table | [[^value/empty]] | [[^flowstate|Succeed]] |
| [[^input|Table]] dibiarkan kosong | - | - | - | [[^flowstate|Fatal Error]] |

Status  [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Gunakan Pass untuk meneruskan Table.** Hubungkan [[^output|Pass]] ke block yang membutuhkan [[Docs/Tipe Data/Table]] yang sama, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]].
- **Ambil atribut yang dibutuhkan saja.** Hubungkan hanya output [[^output|Name]] atau [[^output|Desc]] yang dipakai oleh block berikutnya.

## Batasan dan Catatan

- Block ini hanya membaca atribut [[Docs/Tipe Data/Table]] dan tidak mengubah Table.
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]]
- [[Docs/Modul Data/Table/Apa itu Table|Table]]

