---
status: draft
title: Add Row Block
description: Flow Block Data Table untuk menambahkan Row baru yang masih kosong ke sebuah Table.
---

# Add Row Block

>**note** Add Row Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Add Row Block adalah Flow Block yang menambahkan [[Docs/Tipe Data/Row]] baru ke sebuah [[Docs/Tipe Data/Table]]. Row yang dihasilkan belum memiliki [[Docs/Tipe Data/TableData]], sehingga seluruh kolomnya kosong dan siap diisi oleh block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]].

![[Docs/Modul Logic/Flow/Flow Block/Data Table/add-row-block-flow.png|Add Row Block pada Blueprint]]
## Input dan Output

Add Row Block tidak memiliki Control. Block ini memiliki satu input di sisi kiri dan satu output di sisi kanan.

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Table]] | [[Docs/Tipe Data/Table]] | Table tujuan penambahan Row. Isi dengan Table atau hubungkan dari output block lain. Dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|New Row]] | [[Docs/Tipe Data/Row]] | Row baru yang kosong, tanpa [[Docs/Tipe Data/TableData]]. Meneruskan aliran hanya bila Row berhasil ditambahkan. Tidak meneruskan aliran (`-`) bila terjadi [[^flowstate|Fatal Error]]. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block memeriksa [[^input|Table]]. Bila kosong, block berhenti dengan [[^flowstate|Fatal Error]].
2. Sistem menambahkan satu [[Docs/Tipe Data/Row]] baru ke [[Docs/Tipe Data/Table]] tersebut. [[^output|Index]] Row dibuat otomatis oleh sistem sebagai ID Row pada tampilan [[Docs/Modul Data/Table/Apa itu Table|Table]].
3. Row baru tidak memiliki [[Docs/Tipe Data/TableData]]. Row diteruskan melalui output [[^output|New Row]] agar dapat diisi atau diproses oleh block berikutnya.

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Row yang ditambahkan lewat Add Row Block tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]] pada Flow mana pun.

## Contoh Penggunaan

Menambahkan Row ke [[^field/table|Pesanan]] saat sebuah proses dimulai.

| Kondisi | [[^output|New Row]] | Status |
| - | - | - |
| [[^input|Table]] berisi Table pesanan | Row baru dengan Index otomatis dan [[Docs/Tipe Data/TableData]] kosong | [[^flowstate|Succeed]] |
| [[^input|Table]] dibiarkan kosong | - | [[^flowstate|Fatal Error]] |

## Praktik Terbaik

- **Isi Row baru segera.** Hubungkan [[^output|New Row]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]] agar [[Docs/Tipe Data/TableData]] pada Row tidak dibiarkan kosong.
- **Hubungkan block lanjutan langsung ke New Row.** Output ini hanya meneruskan aliran saat Row berhasil ditambahkan, sehingga block yang terhubung hanya berjalan pada kasus berhasil.
- **Gunakan Index sebagai rujukan Row.** Ambil [[^output|Index]] dari [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]] bila Anda perlu menyimpan atau meneruskan identitas Row yang baru dibuat.

## Batasan dan Catatan

- Row baru tidak memiliki [[Docs/Tipe Data/TableData]], sehingga semua kolomnya kosong sampai diisi.
- [[^output|Index]] dibuat otomatis oleh sistem dan tidak dapat ditentukan lewat block ini.
- Bila [[^input|Table]] kosong, [[^output|New Row]] tidak meneruskan aliran dan pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Delete Row|Delete Row Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/TableData Setter|TableData Setter Block]]
- [[Docs/Modul Data/Table/Apa itu Table#Mengelola Data Table|Mengelola Data Table]]

<!--
  * [DONE] Konfirmasi: [[^input|Table]] kosong diasumsikan [[^flowstate|Fatal Error]] mengikuti pola block Table lain.
  * [DONE] Halaman yang ditautkan dan diasumsikan ada: `Data Table/Pengenalan`, `Flow Block/Syarat Eksekusi`, `Flow Block/Antarmuka#Output`, `Flow Block/Event/Table Row Event`, dan `Flow Activity`.
-->