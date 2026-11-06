---
status: draft
title: EnumData Getter
description: Flow Block untuk mengambil EnumData dari sebuah Enum berdasarkan Name.
pageDecoration:
  icon: search
  tree:
    priority: 4
---

# EnumData Getter

>**note** EnumData Getter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData Getter adalah Flow Block yang mengambil [[Docs/Tipe Data/EnumData]] dari sebuah [[Docs/Tipe Data/Enum]] dengan mengisi [[^field|Name]] sebagai alias. Block ini juga memberi tahu bila EnumData tidak ditemukan, sehingga Flow dapat menangani kondisi tersebut.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-getter-block-flow.png|Flow Block EnumData Getter dengan dua input dan dua output]]

## Input dan Output

EnumData Getter memiliki dua input di sisi kiri dan dua output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Enum]] | [[Docs/Tipe Data/Enum]] | Enum tempat EnumData dicari. Isi dengan Enum atau hubungkan dari output block lain. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Name EnumData yang dicari, berfungsi sebagai alias. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang ditemukan. Tidak ada output bila tidak ada [[^field|Name]] yang cocok. |
| [[^output|Is Empty]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila EnumData tidak ditemukan, tidak ada output bila ditemukan. |

## Cara Kerja

Saat dieksekusi, EnumData Getter mencari EnumData pada Enum yang Anda tentukan dengan [[^field|Name]] yang sama:

1. Bila ada EnumData dengan [[^field|Name]] yang cocok, output [[^output|EnumData]] keluar berisi EnumData tersebut.
2. Bila tidak ada yang cocok, output [[^output|Is Empty]] keluar bernilai [[^value/boolean/true]].
3. Bila [[^field|Enum]] atau [[^field|Name]] dibiarkan kosong, block tidak dapat dijalankan dan tidak ada output.

[[^field|Name]] dianggap cocok bila sama persis dan membedakan huruf besar dan kecil. Block ini hanya mencari EnumData di Enum yang ditentukan pada input [[^field|Enum]], sehingga EnumData dengan nama yang sama di Enum lain tidak ikut terambil.

## Contoh Penggunaan

Contoh berikut memakai Enum [[^field/enum|Status Pesanan]] yang memiliki EnumData [[^value/enumdata|Menunggu]].

| Kondisi | [[^output|EnumData]] | [[^output|Is Empty]] | Status |
| ------- | -------------------- | -------------------- | ------ |
| [[^field|Name]] berisi [[^value/string|Menunggu]] (ada di Enum) | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] |
| [[^field|Name]] berisi [[^value/string|Dibatalkan]] (tidak ada di Enum) | - | [[^value/boolean/true]] | [[^flowstate/Error]] |
| [[^field|Name]] berisi [[^value/string|menunggu]] (huruf kecil semua) | - | [[^value/boolean/true]] | [[^flowstate/Error]] |
| [[^field|Name]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] |
| [[^field|Enum]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Siapkan alur untuk output [[^output|Is Empty]].** Output ini hanya keluar saat EnumData tidak ditemukan, jadi hubungkan ke block yang menangani kondisi tersebut, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]], terpisah dari alur [[^output|EnumData]].
- **Samakan penulisan [[^field|Name]] dengan data di Enum.** Perbedaan huruf besar dan kecil membuat EnumData tidak ditemukan.
- **Lanjutkan ke block yang tepat.** Hubungkan [[^output|EnumData]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]] untuk membaca atributnya, ke block Setter untuk mengubahnya, atau ke [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]] untuk menghapusnya.

## Batasan dan Catatan

- EnumData Getter adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Output [[^output|Is Empty]] hanya keluar bernilai [[^value/boolean/true]] saat EnumData tidak ditemukan. Bila ditemukan, tidak ada output.
- Block ini hanya mengambil satu EnumData per eksekusi.
- Block ini hanya membaca data, sehingga Enum dan EnumData tidak berubah.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]