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

EnumData Getter adalah Flow Block yang mengambil [[Docs/Tipe Data/EnumData]] dari sebuah [[Docs/Tipe Data/Enum]] dengan mengisi [[^field|Name]] sebagai alias. Block ini juga memberi tahu apakah EnumData ditemukan, sehingga Flow dapat bercabang bila Name tidak cocok.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-getter-block-flow.png|Flow Block EnumData Getter dengan dua input dan dua output]]

<!--
  * [TODO] Letakkan gambar `enumdata-getter-block-flow.png` (potongan block EnumData Getter dari Blueprint). Anotasi yang disarankan: (1) input Enum, (2) input Name, (3) output EnumData, (4) output Is Empty.
-->

## Input dan Output

EnumData Getter memiliki dua input di sisi kiri dan dua output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Enum]] | [[Docs/Tipe Data/Enum]] | Enum tempat EnumData dicari. Isi dengan Enum atau hubungkan dari output block lain. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Name EnumData yang dicari, berfungsi sebagai alias. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang ditemukan. Berisi [[^value/empty]] bila tidak ada [[^field|Name]] yang cocok. |
| [[^output|Is Empty]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila EnumData tidak ditemukan, [[^value/boolean/false]] bila ditemukan. |

## Cara Kerja

Saat dieksekusi, EnumData Getter mencari EnumData pada Enum yang Anda tentukan dengan [[^field|Name]] yang sama:

1. Bila ada EnumData dengan [[^field|Name]] yang cocok, [[^output|EnumData]] berisi EnumData tersebut dan [[^output|Is Empty]] bernilai [[^value/boolean/false]].
2. Bila tidak ada yang cocok, [[^output|EnumData]] berisi [[^value/empty]] dan [[^output|Is Empty]] bernilai [[^value/boolean/true]].

[[^field|Name]] dianggap cocok bila sama persis dan membedakan huruf besar dan kecil. Block ini hanya mencari EnumData di Enum yang ditentukan pada input [[^field|Enum]], sehingga EnumData dengan nama yang sama di Enum lain tidak ikut terambil.

<!--
  * [TODO] Konfirmasi aturan pencocokan Name: sama persis, membedakan huruf besar dan kecil, dan apakah Name pada input di-trim sebelum dicocokkan.
-->

## Contoh Penggunaan

Contoh berikut memakai Enum status pesanan yang memiliki EnumData [[^value/enumdata|Menunggu]].

| Kondisi | [[^output|EnumData]] | [[^output|Is Empty]] |
| ------- | -------------------- | -------------------- |
| [[^field|Name]] berisi `Menunggu` (ada di Enum) | EnumData [[^value/enumdata|Menunggu]] | [[^value/boolean/false]] |
| [[^field|Name]] berisi `Dibatalkan` (tidak ada di Enum) | [[^value/empty]] | [[^value/boolean/true]] |
| [[^field|Name]] berisi `menunggu` (huruf kecil semua) | [[^value/empty]] | [[^value/boolean/true]] |
| [[^field|Name]] dibiarkan kosong | [[^value/empty]] | [[^value/boolean/true]] |
| [[^field|Enum]] dibiarkan kosong | [[^value/empty]] | [[^value/boolean/true]] |

<!--
  * [TODO] Konfirmasi perilaku Enum atau Name yang dibiarkan kosong: diasumsikan tidak error dan menghasilkan EnumData empty dengan Is Empty true (seperti Variable Getter yang secara teknis tidak dapat error).
  * [TODO] Nama contoh (Enum status pesanan, EnumData Menunggu dan Dibatalkan) bersifat generik. Sesuaikan bila perlu.
-->

## Praktik Terbaik

- **Periksa [[^output|Is Empty]] sebelum memakai [[^output|EnumData]].** Hubungkan [[^output|Is Empty]] ke [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] agar Flow tidak melanjutkan block yang membutuhkan EnumData ketika hasilnya kosong.
- **Samakan penulisan [[^field|Name]] dengan data di Enum.** Perbedaan huruf besar dan kecil membuat EnumData tidak ditemukan.
- **Lanjutkan ke block yang tepat.** Hubungkan [[^output|EnumData]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]] untuk membaca atributnya, [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]] untuk mengubah [[^field|Value]], atau [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]] untuk menghapusnya.

## Batasan dan Catatan

- EnumData Getter adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Output [[^output|Is Empty]] selalu bernilai [[^value/boolean/true]] atau [[^value/boolean/false]], tidak pernah [[^value/empty]].
- Block ini hanya mengambil satu EnumData per eksekusi.
- Block ini hanya membaca data, sehingga Enum dan EnumData tidak berubah.

<!--
  * [TODO] Halaman baru yang ditautkan dan perlu dibuat: `Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData`, `Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If`, dan `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]