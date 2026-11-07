---
status: draft
title: Delete Row Block
description: Flow Block Data Table untuk menghapus Row dari Table, dengan pilihan hapus paksa untuk Row yang sudah digunakan.
---
# Delete Row Block

>**note** Delete Row Block merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Delete Row Block adalah Flow Block yang menghapus [[Docs/Tipe Data/Row]] dari [[Docs/Tipe Data/Table]]. Block ini memiliki input [[^input|Force]] untuk menghapus Row secara paksa, termasuk Row yang sudah digunakan.

![[Docs/Modul Logic/Flow/Flow Block/Data Table/delete-row-block-flow.png|Delete Row Block pada Blueprint]]
>**danger** Penghapusan Row tidak dapat dikembalikan
> Row yang dihapus beserta seluruh [[Docs/Tipe Data/TableData]]-nya hilang permanen dan tidak dapat dikembalikan.

## Input dan Output

Delete Row memiliki dua input di sisi kiri, dua output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| - | - | - |
| [[^input|Row]] | [[Docs/Tipe Data/Row]] | Row target yang akan dihapus. Isi dengan Row atau hubungkan dari output block lain. Dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. |
| [[^input|Force]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] untuk menghapus Row secara paksa walaupun Row sudah digunakan. [[^value/boolean/false]] menolak penghapusan Row yang sudah digunakan. Dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]]. |

### Output

| Output | Tipe Data | Keterangan |
| - | - | - |
| [[^output|Succeed]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Row berhasil dihapus dan aliran diteruskan. |
| [[^output|Error]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Row gagal dihapus dan aliran diteruskan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

>**note** Mengelola Error
> Hubungkan [[^output|Error]] ke block yang menangani kegagalan agar Flow dapat memberi tahu pengguna bahwa Row gagal dihapus. Block tersebut hanya dieksekusi bila penghapusan gagal.

## Cara Kerja

1. Block memeriksa [[^input|Row]] dan [[^input|Force]]. Bila salah satunya kosong, block berhenti dengan [[^flowstate|Fatal Error]].
2. [[Docs/Tipe Data/Row]] dianggap **sudah digunakan** bila sedang dipakai pada Flow atau data lain, atau tercatat di riwayat activity.
3. Row yang belum digunakan dihapus, baik [[^input|Force]] bernilai [[^value/boolean/true]] maupun [[^value/boolean/false]]. [[^output|Succeed]] meneruskan aliran.
4. Row yang sudah digunakan hanya dihapus bila [[^input|Force]] bernilai [[^value/boolean/true]]. Bila [[^value/boolean/false]], penghapusan ditolak dan [[^output|Error]] meneruskan aliran.

>**warning** Force menghapus Row yang sudah digunakan
> Dengan [[^input|Force]] bernilai [[^value/boolean/true]], Row tetap dihapus walaupun sudah digunakan. Data atau Flow yang merujuk Row tersebut dan riwayat activity terkait ikut terdampak.

>**note** Perubahan data oleh Flow tidak memicu Flow kembali
> Row yang dihapus lewat Delete Row Block tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]] pada Flow mana pun.

## Contoh Penggunaan

Menghapus Row dari [[^field/table|Pesanan]] saat sebuah pesanan dibatalkan.

| Kondisi | [[^output|Succeed]] | [[^output|Error]] | Status |
| - | - | - | - |
| Row belum digunakan, [[^input|Force]] bernilai [[^value/boolean/false]] | [[^value/boolean/true]] | - | [[^flowstate|Succeed]] |
| Row belum digunakan, [[^input|Force]] bernilai [[^value/boolean/true]] | [[^value/boolean/true]] | - | [[^flowstate|Succeed]] |
| Row sudah digunakan, [[^input|Force]] bernilai [[^value/boolean/true]] | [[^value/boolean/true]] | - | [[^flowstate|Succeed]] |
| Row sudah digunakan, [[^input|Force]] bernilai [[^value/boolean/false]] | - | [[^value/boolean/true]] | [[^flowstate|Error]] |
| [[^input|Row]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |
| [[^input|Force]] dibiarkan kosong | - | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Mulai dari Force false.** Biarkan block menolak Row yang sudah digunakan, lalu putuskan penanganannya lewat [[^output|Error]].
- **Hubungkan block penanganan langsung ke output.** [[^output|Succeed]] dan [[^output|Error]] hanya meneruskan aliran pada kasusnya masing-masing, sehingga block yang terhubung hanya berjalan pada kasus tersebut.
- **Gunakan Force true hanya bila Anda yakin.** Pastikan data, Flow, dan riwayat yang bergantung pada [[Docs/Tipe Data/Row]] memang boleh terdampak.

## Batasan dan Catatan

- Penghapusan [[Docs/Tipe Data/Row]] tidak dapat dikembalikan, termasuk [[Docs/Tipe Data/TableData]] di dalamnya.
- [[^input|Row]] atau [[^input|Force]] yang dibiarkan kosong menimbulkan [[^flowstate|Fatal Error]], sehingga [[^output|Succeed]] dan [[^output|Error]] tidak meneruskan aliran. Pesan error tampil di [[Docs/Modul Logic/Flow/Flow Activity]].
- Block ini tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Add Row|Add Row Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event|Table Row Event Block]]
- [[Docs/Modul Data/Table/Apa itu Table#Mengelola Data Table|Mengelola Data Table]]

<!--
  * [TODO] Konfirmasi: definisi Row "sudah digunakan" diasumsikan sama dengan Variable Data (dipakai pada Flow atau data lain, atau tercatat di riwayat activity), dan Force [[^value/boolean/false]] pada Row yang sudah digunakan menghasilkan [[^output|Error]].
  * [TODO] Konfirmasi: [[Docs/Tipe Data/TableData]] pada Row ikut terhapus bersama Row.
  * [TODO] Halaman yang ditautkan dan diasumsikan ada: `Data Table/Pengenalan`, `Flow Block/Syarat Eksekusi`, `Flow Block/Antarmuka#Output`, `Flow Block/Event/Table Row Event`, dan `Flow Activity`.
-->