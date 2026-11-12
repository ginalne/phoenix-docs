---
status: draft
title: Table Column Block
description: Flow Block Data Table untuk mengambil atribut dari sebuah Column, yaitu Name, Description, Header, dan Table asalnya.
---

# Table Column Block

>**note** Table Column Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Table Column Block adalah Flow Block yang menerima [[Docs/Tipe Data/Column]] dan mengeluarkan atributnya, yaitu [[^field|Name]], [[^field|Description]], [[^field|Header]], serta [[Docs/Tipe Data/Table]] tempat Column berada. Gunakan block ini saat alur Anda perlu mengenali Column yang sedang diproses.

![[Docs/Modul Logic/Flow/Flow Block/Data Table/table-column-block-flow.png|Table Column Block pada Blueprint]]
## Input dan Output

Table Column Block memiliki satu input di sisi kiri, lima output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada aliran keluar. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Column]] | [[Docs/Tipe Data/Column]] | Column yang atributnya akan diambil. Isi dengan Column atau hubungkan dari output block lain. Dibiarkan kosong menimbulkan [[^flowstate/Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass]] | [[Docs/Tipe Data/Column]] | Meneruskan [[Docs/Tipe Data/Column]] yang diinput ke block berikutnya. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | Nama Column. |
| [[^output|Desc]] | [[Docs/Tipe Data/Text]] | Deskripsi Column. |
| [[^output|Header]] | Mengikuti tipe data Column | Header Column. Tetap meneruskan aliran dengan nilai [[^value/empty]] bila tipe data Column tidak memiliki Header. |
| [[^output|Table]] | [[Docs/Tipe Data/Table]] | Table tempat Column berada. |

Kelima output meneruskan aliran bila [[^input|Column]] terisi, dan tidak meneruskan aliran bila terjadi [[^flowstate/Fatal Error]]. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block memeriksa [[^input|Column]]. Bila kosong, block berhenti dengan [[^flowstate/Fatal Error]].
2. Block membaca atribut [[Docs/Tipe Data/Column]] yang diinput.
3. Tipe data [[^output|Header]] mengikuti tipe data Column, seperti pada tabel berikut. Column dengan tipe data lain tidak memiliki Header, sehingga [[^output|Header]] bernilai [[^value/empty]].

| Tipe data Column | Tipe data Header |
| - | - |
| [[Docs/Tipe Data/EnumData]] | [[Docs/Tipe Data/Enum]] |
| [[Docs/Tipe Data/Column]] | [[Docs/Tipe Data/Table]] |
| [[Docs/Tipe Data/Row]] | [[Docs/Tipe Data/Table]] |
| [[Docs/Tipe Data/TableData]] | [[Docs/Tipe Data/Column]] |
| [[Docs/Tipe Data/Node]] | [[Docs/Tipe Data/Tree]] |

## Contoh Penggunaan

Mengenali Column yang menjadi tujuan pengisian [[Docs/Tipe Data/TableData]] pada [[^field/table|Pesanan]].

| Kondisi | [[^output|Pass]] | [[^output|Name]] | [[^output|Desc]] | [[^output|Header]] | [[^output|Table]] | Status |
| - | - | - | - | - | - | - |
| [[^input|Column]] bertipe data yang memiliki Header | [[Docs/Tipe Data/Column]] | Nama Column | Deskripsi Column | Header sesuai tipe data | [[Docs/Tipe Data/Table]] | [[^flowstate/Succeed]] |
| [[^input|Column]] bertipe data tanpa Header | [[Docs/Tipe Data/Column]] | Nama Column | Deskripsi Column | [[^value/empty]] | [[Docs/Tipe Data/Table]] | [[^flowstate/Succeed]] |
| [[^input|Column]] dibiarkan kosong | - | - | - | - | - | [[^flowstate/Fatal Error]] |

Status  [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Periksa Header sebelum memakainya.** [[^output|Header]] bisa bernilai [[^value/empty]] pada Column tanpa Header, jadi pastikan block yang menerimanya siap menangani nilai kosong.
- **Gunakan Table untuk menelusuri asal Column.** Hubungkan [[^output|Table]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table|Table Block]] bila Anda perlu Name atau Desc dari [[Docs/Tipe Data/Table]] tempat Column berada.

## Batasan dan Catatan

- Block ini hanya membaca atribut [[Docs/Tipe Data/Column]] dan tidak mengubah Column.
- [[^output|Header]] selalu meneruskan aliran, baik berisi maupun [[^value/empty]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table|Table Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter|TableData Getter Block]]
- [[Docs/Modul Data/Table/Apa itu Table|Table]]

