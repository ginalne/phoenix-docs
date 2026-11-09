---
status: draft
title: Table Row Block
description: Flow Block Data Table untuk mengambil atribut dari sebuah Row, yaitu Index dan Table asalnya.
---

# Table Row Block

>**note** Table Row Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Table Row Block adalah Flow Block yang menerima [[Docs/Tipe Data/Row]] dan mengeluarkan atributnya, yaitu [[^output|Index]] (ID Row pada tampilan [[Docs/Modul Data/Table/Apa itu Table|Table]]) serta [[Docs/Tipe Data/Table]] tempat Row berada. Gunakan block ini saat alur Anda perlu mengenali Row yang sedang diproses, misalnya Row dari [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]].

![[Docs/Modul Logic/Flow/Flow Block/Data Table/table-row-block-flow.png|Table Row Block pada Blueprint]]
## Input dan Output

Table Row Block memiliki satu input di sisi kiri, tiga output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada aliran keluar. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Row]] | [[Docs/Tipe Data/Row]] | Row yang atributnya akan diambil. Isi dengan Row atau hubungkan dari output block lain. Dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass]] | [[Docs/Tipe Data/Row]] | Meneruskan [[Docs/Tipe Data/Row]] yang diinput ke block berikutnya. |
| [[^output|Index]] | [[Docs/Tipe Data/Number]] | ID Row pada tampilan [[Docs/Modul Data/Table/Apa itu Table|Table]]. |
| [[^output|Table]] | [[Docs/Tipe Data/Table]] | Table tempat Row berada. |

Ketiga output meneruskan aliran bila [[^input|Row]] terisi, dan tidak meneruskan aliran bila terjadi [[^flowstate|Fatal Error]]. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block memeriksa [[^input|Row]]. Bila kosong, block berhenti dengan [[^flowstate|Fatal Error]].
2. Block membaca atribut [[Docs/Tipe Data/Row]] yang diinput.
3. [[^output|Pass]], [[^output|Index]], dan [[^output|Table]] diteruskan bersamaan ke block yang terhubung.

## Contoh Penggunaan

Mengenali Row pesanan yang baru ditambahkan agar nomornya dapat dipakai pada langkah berikutnya.

| Kondisi | [[^output|Pass]] | [[^output|Index]] | [[^output|Table]] | Status |
| - | - | - | - | - |
| [[^input|Row]] berisi Row dari Table pesanan | [[Docs/Tipe Data/Row]] | [[^value/number|12]] | [[Docs/Tipe Data/Table]] | [[^flowstate|Succeed]] |
| [[^input|Row]] dibiarkan kosong | - | - | - | [[^flowstate|Fatal Error]] |

Status  [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Gunakan Index sebagai rujukan Row.** Hubungkan [[^output|Index]] ke input [[^input|Row]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter|TableData Getter Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]] bila block tersebut memakai [[Docs/Tipe Data/Number]] sebagai pengganti [[Docs/Tipe Data/Row]].
- **Gunakan Pass untuk meneruskan Row.** Hubungkan [[^output|Pass]] ke block yang membutuhkan [[Docs/Tipe Data/Row]] yang sama, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row|Delete Row Block]].

## Batasan dan Catatan

- Block ini hanya membaca atribut [[Docs/Tipe Data/Row]] dan tidak mengubah Row.
- [[^output|Index]] dibuat otomatis oleh sistem saat Row ditambahkan.
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table|Table Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]]

