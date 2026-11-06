---
status: draft
title: EnumData Selectable Setter
description: Flow Block untuk mengubah Selectable pada satu atau beberapa EnumData sekaligus dari dalam Flow.
pageDecoration:
  icon: save
  tree:
    priority: 4
---

# EnumData Selectable Setter

>**note** EnumData Selectable Setter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData Selectable Setter adalah Flow Block yang memperbarui [[^field|Selectable]] pada satu atau beberapa [[Docs/Tipe Data/EnumData]] sekaligus saat Flow berjalan. Seluruh EnumData yang diberikan menerima nilai [[^field|Selectable]] yang sama, sedangkan atribut lainnya tidak berubah.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-selectable-setter-block-flow.png|Flow Block EnumData Selectable Setter dengan dua input dan satu output]]

## Input dan Output

EnumData Selectable Setter memiliki dua input di sisi kiri dan satu output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData(s)]] | [[Docs/Tipe Data/Array]] berisi [[Docs/Tipe Data/EnumData]] | Satu atau beberapa EnumData yang [[^field|Selectable]]-nya akan diubah. Isi dengan EnumData atau hubungkan dari output block lain. |
| [[^field|Selectable]] | [[Docs/Tipe Data/Boolean]] | Nilai [[^field|Selectable]] baru untuk seluruh EnumData pada input. [[^value/boolean/true]] membuat EnumData tampil sebagai pilihan pada field berformat [[Docs/Tipe Data/EnumData]], [[^value/boolean/false]] menyembunyikannya dari pilihan. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Pass]] | [[Docs/Tipe Data/Array]] berisi [[Docs/Tipe Data/EnumData]] | EnumData yang diubah, diteruskan ke block berikutnya. |

## Cara Kerja

Saat dieksekusi, EnumData Selectable Setter mengganti [[^field|Selectable]] pada setiap EnumData di input [[^field|EnumData(s)]] dengan nilai pada input [[^field|Selectable]], lalu output [[^output|Pass]] meneruskan EnumData tersebut. Satu eksekusi dapat mengubah banyak EnumData, sehingga Anda tidak perlu mengulang block ini untuk setiap EnumData.

EnumData dengan [[^field|Selectable]] bernilai [[^value/boolean/false]] tetap dapat dipakai di tempat lain. Atribut ini hanya menentukan apakah EnumData tampil sebagai pilihan pada field.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[^field|Selectable]] oleh EnumData Selectable Setter tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|update]] pada Flow mana pun.

## Contoh Penggunaan

Contoh berikut memakai tiga EnumData pada Enum [[^field/enum|Status Pesanan]] yang semuanya semula [[^field|Selectable]] bernilai [[^value/boolean/true]].

| Kondisi | [[^output|Pass]] | Status | Hasil pada EnumData |
| ------- | ---------------- | ------ | ------------------- |
| [[^field|EnumData(s)]] berisi tiga EnumData dan [[^field|Selectable]] bernilai [[^value/boolean/false]] | Tiga EnumData yang diubah | [[^flowstate/Succeed]] | Ketiganya tidak lagi tampil sebagai pilihan pada field. |
| [[^field|EnumData(s)]] berisi tiga EnumData dan [[^field|Selectable]] bernilai [[^value/boolean/true]] | Tiga EnumData yang diubah | [[^flowstate/Succeed]] | Tidak ada yang berubah karena nilainya sama. |
| [[^field|EnumData(s)]] dibiarkan kosong | - | [[^flowstate/Fatal Error]] | Tidak ada yang berubah. |
| [[^field|Selectable]] dibiarkan kosong | - | [[^flowstate/Fatal Error]] | Tidak ada yang berubah. |

Status [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Gunakan block ini untuk perubahan massal.** Misalnya menyembunyikan beberapa pilihan lama sekaligus tanpa menghapus EnumData-nya.
- **Pilih [[^value/boolean/false]] sebagai pengganti penghapusan.** EnumData tetap tersimpan dan tetap dapat dipakai di tempat lain, sehingga lebih aman dibanding [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]].

## Batasan dan Catatan

- EnumData Selectable Setter adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Seluruh EnumData pada input menerima nilai [[^field|Selectable]] yang sama. Untuk nilai berbeda per EnumData, jalankan block ini terpisah.
- Block ini hanya mengubah [[^field|Selectable]]. Untuk atribut lain, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]