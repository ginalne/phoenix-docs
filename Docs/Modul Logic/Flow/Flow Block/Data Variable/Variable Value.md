---
status: draft
title: Variable Value
description: Flow Block untuk mengambil Value dari Variable Data secara langsung.
---
# Variable Value

>**note** Variable Value merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Variable Value adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk mengambil Value dari [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] secara langsung, sehingga nilainya dapat dipakai oleh block berikutnya. Block ini memiliki satu input di sisi kiri dan satu output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/variable-value-block-flow.png|Flow Block Variable Value dengan satu input dan satu output]]
## Input dan Output

Variable Value memiliki satu input di sisi kiri dan satu output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang Value-nya akan diambil. Isi dengan Variable Data atau hubungkan dari output block lain, misalnya [[^output|Variable]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Value]] | Mengikuti Type Variable Data | Value dari Variable Data. Tipe data output mengikuti sumber nilainya. |

[[^output|Value]] meneruskan aliran bila [[^field|Variable]] terisi. Bila [[^field|Variable]] dibiarkan kosong, block menghasilkan error dan [[^output|Value]] tidak meneruskan aliran, sehingga block yang terhubung tidak dieksekusi. Lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block menerima Variable Data lewat [[^field|Variable]].
2. Block mengirim Value Variable Data langsung lewat [[^output|Value]], tanpa mengubah tipe datanya.

Jika Variable Data bertipe [[Docs/Tipe Data/Number]], [[^output|Value]] berupa [[Docs/Tipe Data/Number]]. Jika bertipe [[Docs/Tipe Data/String]], [[^output|Value]] berupa [[Docs/Tipe Data/String]].

Tipe data [[^output|Value]] tidak ditampilkan pada block di halaman kerja dan tidak memengaruhi block yang dikoneksikan. Bila tipe data tidak cocok dengan block penerima, ketidakcocokan dilaporkan di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] saat Flow berjalan.

Gunakan Variable Value bila Anda hanya membutuhkan nilainya. Bila Anda juga membutuhkan Name atau Description, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable|Variable Block]].

## Contoh Penggunaan

| Kondisi | [[^output|Value]] | Status |
| ------- | ----------------- | ------ |
| [[^field|Variable]] berisi Variable Data [[^value/string|batas_stok_minimum]] bertipe [[Docs/Tipe Data/Number]] dengan nilai [[^value/number|50]] | [[^value/number|50]] | [[^flowstate/Succeed]] |
| [[^field|Variable]] berisi Variable Data bertipe [[Docs/Tipe Data/String]] dengan nilai [[^value/string|aktif]] | [[^value/string|aktif]] | [[^flowstate/Succeed]] |
| [[^field|Variable]] dibiarkan kosong | - | [[^flowstate/Fatal Error]] |

Hubungkan [[^output|Value]] ke block yang membutuhkan nilai tersebut, misalnya [[Docs/Modul Logic/Flow/Flow Block/Query/Condition|Condition Query Block]] untuk menjadikan Variable Data sebagai batas keputusan Flow, tanpa menuliskan angka yang sama di banyak tempat.

Status [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Pasangkan dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** agar Variable Data yang tidak ditemukan dapat ditangani lewat [[^output|Is Empty]] sebelum nilainya dipakai.
- **Pastikan block penerima mendukung tipe data [[^output|Value]].** Tipe data output berbeda untuk setiap Variable Data dan tidak terlihat di halaman kerja.
- **Simpan nilai yang dipakai di banyak Flow sebagai Variable Data**, lalu baca dengan Variable Value agar perubahan nilai cukup dilakukan satu kali.

## Batasan dan Catatan

- Variable Value hanya membaca nilai dan tidak mengubah Variable Data. Untuk mengubahnya, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].
- [[^field|Variable]] yang dibiarkan kosong menyebabkan error.
- Variable Value adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Anggota yang tidak memiliki akses ke komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tetap dapat memakai Value lewat Flow, tetapi tidak dapat melihatnya di halaman kerja.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]