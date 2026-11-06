---
status: draft
title: EnumData Value Setter
description: Flow Block untuk mengubah Value sebuah EnumData dari dalam Flow.
pageDecoration:
  icon: save
  tree:
    priority: 4
---

# EnumData Value Setter

>**note** EnumData Value Setter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData Value Setter adalah Flow Block yang memperbarui [[^field|Value]] pada [[Docs/Tipe Data/EnumData]] yang Anda tentukan saat Flow berjalan. Atribut lain pada EnumData, yaitu [[^field|Name]], [[^field|Description]], dan [[^field|Selectable]], tidak berubah. Satu eksekusi mengubah satu EnumData.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-value-setter-block-flow.png|Flow Block EnumData Value Setter dengan dua input dan dua output]]
## Input dan Output

EnumData Value Setter memiliki dua input di sisi kiri dan dua output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang [[^field|Value]]-nya akan diubah. Isi dengan EnumData atau hubungkan dari output block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]. |
| [[^field|Value]] | [[^field|N/A Type]] | Nilai baru yang akan disimpan pada EnumData. Tipe data belum ditentukan sampai Anda mengaturnya, lihat [[#Menentukan Tipe Data Value]]. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Pass]] | [[Docs/Tipe Data/EnumData]] | EnumData yang diubah, diteruskan ke block berikutnya. |
| [[^output|Value Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Value tidak sesuai dengan Enum tempat EnumData berada, tidak ada output bila tidak ada konflik. |

### Menentukan Tipe Data Value

Teks merah [[^field|N/A Type]] pada input [[^field|Value]] berarti tipe data belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan [[^field|Format]] Enum tempat EnumData berada. Semua tipe data Phoenix tersedia pada daftar ini.

## Cara Kerja

Saat dieksekusi, EnumData Value Setter memeriksa tipe data [[^field|Value]] terhadap [[^field|Format]] Enum tempat EnumData berada. Bila sama, [[^field|Value]] pada EnumData diganti dan output [[^output|Pass]] meneruskan EnumData tersebut. Bila tidak sama, [[^field|Value]] tidak berubah dan [[^output|Value Conflict]] bernilai [[^value/boolean/true]]. Block ini tidak mengonversi tipe data.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[^field|Value]] oleh EnumData Value Setter tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|update]] pada Flow mana pun.

## Contoh Penggunaan

Contoh berikut memakai EnumData [[^value/enumdata|Menunggu]] yang [[^field|Value]]-nya semula `1` pada Enum [[^field/enum|Status Pesanan]] bertipe [[Docs/Tipe Data/Number]].

| Kondisi | [[^output|Pass]] | [[^output|Value Conflict]] | Status | Hasil pada EnumData |
| ------- | ---------------- | -------------------------- | ------ | ------------------- |
| [[^field|Value]] berisi [[^value/number|10]] | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] | [[^field|Value]] berubah dari `1` menjadi `10`. |
| [[^field|Value]] berisi nilai yang sama dengan sebelumnya | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] | Tidak ada yang berubah. |
| [[^field|Value]] dibiarkan kosong, namun tipenya [[Docs/Tipe Data/Number]] | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] | [[^field|Value]] berubah dari `1` menjadi [[^value/empty]]. |
| [[^field|Value]] berisi [[^value/string|aktif]] bertipe [[Docs/Tipe Data/String]] | - | [[^value/boolean/true]] | [[^flowstate/Error]] | Tidak ada yang berubah. |
| [[^field|EnumData]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] | Tidak ada yang berubah. |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Pastikan EnumData yang dituju benar.** Ambil EnumData lewat [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] dan tangani output [[^output|Is Empty]] pada alur terpisah agar block ini tidak dijalankan dengan input kosong.
- **Tentukan tipe data [[^field|Value]] lebih dulu.** Samakan dengan [[^field|Format]] Enum agar [[^output|Value Conflict]] tidak keluar.
- **Siapkan alur untuk output [[^output|Value Conflict]].** Output ini hanya keluar saat konflik terjadi, jadi hubungkan ke block yang menangani kegagalan, terpisah dari alur [[^output|Pass]].
- **Baca hasil perubahan lewat [[^output|Pass]].** Hubungkan [[^output|Pass]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]] bila Anda ingin memakai nilai terbaru pada block berikutnya.

## Batasan dan Catatan

- EnumData Value Setter adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Satu eksekusi hanya mengubah satu EnumData, dan hanya atribut [[^field|Value]].
- Output [[^output|Value Conflict]] hanya keluar bernilai [[^value/boolean/true]] saat konflik terjadi. Bila tidak ada konflik, tidak ada output.
- Perubahan [[^field|Value]] bersifat langsung pada EnumData di Enum. Anda tidak perlu menyimpannya lagi.
- Untuk mengubah beberapa atribut sekaligus, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]