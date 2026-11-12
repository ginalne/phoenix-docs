---
status: draft
title: TableData Setter Block
description: Flow Block Data Table untuk mengubah satu nilai TableData berdasarkan Column dan Row.
---

# TableData Setter Block

>**note** TableData Setter Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

TableData Setter Block adalah Flow Block yang mengisi atau mengubah satu nilai [[Docs/Tipe Data/TableData]] pada pertemuan sebuah [[Docs/Tipe Data/Column]] dan [[Docs/Tipe Data/Row]]. Block ini memeriksa kesesuaian nilai dengan tipe data Column, sehingga data pada [[Docs/Modul Data/Table/Apa itu Table|Table]] tetap konsisten.

![[Docs/Modul Logic/Flow/Flow Block/Data Table/tabledata-setter-block-flow.png|TableData Setter Block pada Blueprint]]
>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Perubahan [[Docs/Tipe Data/TableData]] lewat TableData Setter Block tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]] pada Flow mana pun.

## Input dan Output

TableData Setter Block memiliki tiga input di sisi kiri, dua output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada aliran keluar. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Column]] | [[Docs/Tipe Data/Column]] | Column tempat [[Docs/Tipe Data/TableData]] berada. Isi dengan Column atau hubungkan dari output block lain. Dibiarkan kosong menimbulkan [[^flowstate/Fatal Error]]. |
| [[^input|Row]] | [[Docs/Tipe Data/Row]], [[Docs/Tipe Data/Number]], atau [[Docs/Tipe Data/String]] | Row tempat [[Docs/Tipe Data/TableData]] berada. Dapat diganti dengan [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]] yang berisi Index Row (lihat [[#Menentukan Tipe Data Row]]). Dibiarkan kosong menimbulkan [[^flowstate/Fatal Error]]. |
| [[^input|Value]] | [[^field|N/A Type]] sampai tipe ditentukan | Nilai baru untuk [[Docs/Tipe Data/TableData]]. Tipe data harus ditentukan lebih dulu (lihat [[#Menentukan Tipe Data Value]]). Value yang masih [[^field|N/A Type]] menimbulkan [[^flowstate/Fatal Error]]. |

[[^input|Column]] dan [[^input|Row]] harus berasal dari [[Docs/Modul Data/Table/Apa itu Table|Table]] yang sama.

### Menentukan Tipe Data Row

Input [[^input|Row]] bertipe [[Docs/Tipe Data/Row]]. Ganti tipenya bila Anda ingin mengisi Row dengan [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]] berisi Index Row.

1. Klik kanan pada input [[^input|Row]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]]. Untuk kembali ke [[Docs/Tipe Data/Row]], ulangi langkah ini dan pilih [[Docs/Tipe Data/Row]].

### Menentukan Tipe Data Value

Teks merah [[^field|N/A Type]] pada [[^input|Value]] berarti tipe data belum didefinisikan. Karena setiap Column memiliki tipe data yang pasti, tentukan tipe data [[^input|Value]] agar sesuai dengan Column.

1. Klik kanan pada input [[^input|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan tipe data Column.

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Pass]] | Mengikuti tipe data [[^input|Value]] | Meneruskan [[^input|Value]] yang diinput. Meneruskan aliran hanya bila nilai berhasil disimpan. |
| [[^output|Value Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila [[^input|Value]] tidak sesuai dengan tipe data Column. Meneruskan aliran hanya pada kasus tersebut. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block memeriksa [[^input|Column]], [[^input|Row]], dan [[^input|Value]]. Bila [[^input|Column]] atau [[^input|Row]] kosong, atau [[^input|Value]] masih [[^field|N/A Type]], block berhenti dengan [[^flowstate/Fatal Error]].
2. Block mencari [[Docs/Tipe Data/TableData]] pada [[Docs/Tipe Data/Column]] dan [[Docs/Tipe Data/Row]] yang ditentukan. Bila [[^input|Row]] berupa [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]], nilainya dicocokkan dengan Index Row. Bila tidak ditemukan, block berstatus [[^flowstate/Error]].
3. Bila [[^input|Value]] berisi, block membandingkan tipe datanya dengan tipe data Column. Bila tidak sesuai, [[^output|Value Conflict]] meneruskan [[^value/boolean/true]] dan [[Docs/Tipe Data/TableData]] tidak berubah.
4. Bila [[^input|Value]] sesuai, nilai disimpan dan [[^output|Pass]] meneruskan [[^input|Value]].
5. Bila [[^input|Value]] kosong, block tidak memeriksa tipe datanya. Nilai kosong selalu valid, sehingga [[Docs/Tipe Data/TableData]] menjadi kosong dan [[^output|Pass]] meneruskan nilai [[^value/empty]].

Block ini hanya mengubah satu [[Docs/Tipe Data/TableData]] per eksekusi.

## Contoh Penggunaan

Mengisi status pada Row pesanan yang baru ditambahkan.

| Kondisi | [[^output|Pass]] | [[^output|Value Conflict]] | Status |
| - | - | - | - |
| [[^input|Value]] sesuai tipe data Column | [[^input|Value]] yang diinput | - | [[^flowstate/Succeed]] |
| [[^input|Value]] kosong, tipe data sudah ditentukan | [[^value/empty]] | - | [[^flowstate/Succeed]] |
| [[^input|Value]] berisi tetapi tipenya tidak sesuai tipe data Column | - | [[^value/boolean/true]] | [[^flowstate/Error]] |
| Row dengan Index yang diisi tidak ditemukan | - | - | [[^flowstate/Error]] |
| [[^input|Column]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] |
| [[^input|Row]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] |
| [[^input|Value]] masih [[^field|N/A Type]] | - | - | [[^flowstate/Fatal Error]] |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Tentukan tipe data Value sesuai Column.** Cek tipe data Column di [[Docs/Modul Data/Table/Apa itu Table#Mengelola Data Table|Mengelola Data Table]] sebelum memilih tipe pada [[^field|Change Type]].
- **Sambungkan penanganan langsung ke Value Conflict.** [[^output|Pass]] dan [[^output|Value Conflict]] hanya meneruskan aliran pada kasusnya masing-masing, sehingga block yang terhubung hanya berjalan pada kasus tersebut.
- **Gunakan satu Setter untuk satu kolom.** Untuk mengisi beberapa Column pada Row yang sama, pakai beberapa TableData Setter Block, misalnya setelah [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]].

## Batasan dan Catatan

- Satu eksekusi hanya mengubah satu [[Docs/Tipe Data/TableData]].
- [[^input|Value]] kosong selalu valid dan mengosongkan [[Docs/Tipe Data/TableData]], tetapi [[^field|N/A Type]] tetap menimbulkan [[^flowstate/Fatal Error]] walaupun kosong.
- [[^output|Value Conflict]] tidak mengubah [[Docs/Tipe Data/TableData]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Getter|TableData Getter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Column|Table Column Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]]

