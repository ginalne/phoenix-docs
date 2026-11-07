---
status: draft
title: TableData Getter Block
description: Flow Block Data Table untuk mengambil nilai TableData berdasarkan Column dan Row.
---

# TableData Getter Block

>**note** TableData Getter Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

TableData Getter Block adalah Flow Block yang mengambil nilai [[Docs/Tipe Data/TableData]] pada pertemuan sebuah [[Docs/Tipe Data/Column]] dan [[Docs/Tipe Data/Row]]. Block ini juga memberi tahu bila [[Docs/Tipe Data/TableData]] tidak berisi atau tidak ditemukan, sehingga alur Anda dapat menyiapkan penanganannya.

![[Docs/Modul Logic/Flow/Flow Block/Data Table/tabledata-getter-block-flow.png|TableData Getter Block pada Blueprint]]
## Input dan Output

TableData Getter Block memiliki dua input di sisi kiri, dua output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Column]] | [[Docs/Tipe Data/Column]] | Column tempat [[Docs/Tipe Data/TableData]] berada. Isi dengan Column atau hubungkan dari output block lain. Dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. |
| [[^input|Row]] | [[Docs/Tipe Data/Row]], [[Docs/Tipe Data/Number]], atau [[Docs/Tipe Data/String]] | Row tempat [[Docs/Tipe Data/TableData]] berada. Dapat diganti dengan [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]] yang berisi Index Row (lihat [[#Menentukan Tipe Data Row]]). Dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. |

[[^input|Column]] dan [[^input|Row]] harus berasal dari [[Docs/Modul Data/Table/Apa itu Table|Table]] yang sama.

### Menentukan Tipe Data Row

Input [[^input|Row]] bertipe [[Docs/Tipe Data/Row]]. Ganti tipenya bila Anda ingin mengisi Row dengan [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]] berisi Index Row.

1. Klik kanan pada input [[^input|Row]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]]. Untuk kembali ke [[Docs/Tipe Data/Row]], ulangi langkah ini dan pilih [[Docs/Tipe Data/Row]].

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|TableData]] | Mengikuti tipe data Column | Nilai dari [[Docs/Tipe Data/TableData]]. Meneruskan aliran hanya bila [[Docs/Tipe Data/TableData]] ditemukan dan berisi. |
| [[^output|Is Empty]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila [[Docs/Tipe Data/TableData]] tidak berisi atau tidak ditemukan. Meneruskan aliran hanya pada kasus tersebut. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block memeriksa [[^input|Column]] dan [[^input|Row]]. Bila salah satunya kosong, block berhenti dengan [[^flowstate|Fatal Error]].
2. Block mencari [[Docs/Tipe Data/TableData]] pada [[Docs/Tipe Data/Column]] dan [[Docs/Tipe Data/Row]] yang ditentukan. Bila [[^input|Row]] berupa [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]], nilainya dicocokkan dengan Index Row.
3. Bila [[Docs/Tipe Data/TableData]] ditemukan dan berisi, [[^output|TableData]] meneruskan nilainya.
4. Bila [[Docs/Tipe Data/TableData]] tidak berisi atau tidak ditemukan, [[^output|Is Empty]] meneruskan [[^value/boolean/true]]. Row yang Index-nya tidak ada, atau [[Docs/Tipe Data/Column]] dan [[Docs/Tipe Data/Row]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]] berbeda, termasuk kasus tidak ditemukan.

## Contoh Penggunaan

Membaca status dari Row pesanan yang nomornya diterima dari block sebelumnya.

| Kondisi | [[^output|TableData]] | [[^output|Is Empty]] | Status |
| - | - | - | - |
| [[Docs/Tipe Data/TableData]] berisi nilai | Nilai [[Docs/Tipe Data/TableData]] | - | [[^flowstate|Succeed]] |
| [[Docs/Tipe Data/TableData]] tidak berisi | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| Row dengan Index yang diisi tidak ditemukan | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^input|Column]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |
| [[^input|Row]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Sambungkan penanganan langsung ke Is Empty.** [[^output|TableData]] dan [[^output|Is Empty]] hanya meneruskan aliran pada kasusnya masing-masing, sehingga block yang terhubung hanya berjalan pada kasus tersebut.
- **Gunakan Index dari Table Row Block.** Hubungkan [[^output|Index]] dari [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]] ke input [[^input|Row]] setelah tipenya diganti menjadi [[Docs/Tipe Data/Number]].
- **Pastikan Column dan Row sepasang.** Ambil [[Docs/Tipe Data/Column]] dan [[Docs/Tipe Data/Row]] dari [[Docs/Modul Data/Table/Apa itu Table|Table]] yang sama agar [[Docs/Tipe Data/TableData]] dapat ditemukan.

## Batasan dan Catatan

- Block ini hanya membaca [[Docs/Tipe Data/TableData]] dan tidak mengubahnya. Untuk mengubah nilainya gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]].
- [[Docs/Tipe Data/TableData]] yang tidak berisi dan [[Docs/Tipe Data/TableData]] yang tidak ditemukan sama-sama menghasilkan [[^output|Is Empty]] [[^value/boolean/true]].
- [[^input|Column]] atau [[^input|Row]] yang dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. Pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]]
- [[Docs/Modul Data/Table/Apa itu Table#Mengelola Data Table|Mengelola Data Table]]

