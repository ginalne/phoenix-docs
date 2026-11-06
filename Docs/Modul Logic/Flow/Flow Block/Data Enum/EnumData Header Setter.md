---
status: draft
title: EnumData Header Setter
description: Flow Block untuk mengubah Name dan Description sebuah EnumData dari dalam Flow.
pageDecoration:
  icon: save
  tree:
    priority: 4
---

# EnumData Header Setter

>**note** EnumData Header Setter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData Header Setter adalah Flow Block yang memperbarui atribut pengenal pada [[Docs/Tipe Data/EnumData]] yang Anda tentukan saat Flow berjalan, yaitu [[^field|Name]] dan [[^field|Description]]. Atribut [[^field|Value]] dan [[^field|Selectable]] tidak berubah. Satu eksekusi mengubah satu EnumData.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-header-setter-block-flow.png|Flow Block EnumData Header Setter dengan tiga input dan dua output]]

## Input dan Output

EnumData Header Setter memiliki tiga input di sisi kiri dan dua output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang atributnya akan diubah. Isi dengan EnumData atau hubungkan dari output block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Name baru EnumData. Name harus unik di dalam Enum yang sama. |
| [[^field|Description]] | [[Docs/Tipe Data/Text]] | Deskripsi baru EnumData. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Pass]] | [[Docs/Tipe Data/EnumData]] | EnumData yang diubah, diteruskan ke block berikutnya. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Name sudah digunakan EnumData lain di Enum yang sama, tidak ada output bila tidak ada konflik. |

## Cara Kerja

Saat dieksekusi, EnumData Header Setter memeriksa [[^field|Name]] terlebih dahulu. Bila sudah digunakan EnumData lain di Enum yang sama, perubahan dihentikan dan [[^output|Name Conflict]] bernilai [[^value/boolean/true]]. Bila belum digunakan, [[^field|Name]] dan [[^field|Description]] pada EnumData diganti, lalu output [[^output|Pass]] meneruskan EnumData tersebut. Bila [[^field|EnumData]] atau [[^field|Name]] dibiarkan kosong, block tidak dapat dijalankan.

Aturan [[^field|Name]] sama dengan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]]: dianggap sama bila sama persis, membedakan huruf besar dan kecil, menerima karakter simbol, dan di-*trim* saat disimpan.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[^field|Name]] dan [[^field|Description]] oleh EnumData Header Setter tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|update]] pada Flow mana pun.

## Contoh Penggunaan

Contoh berikut mengubah EnumData [[^value/enumdata|Menunggu]] pada Enum [[^field/enum|Status Pesanan]]. Enum yang sama juga memiliki EnumData [[^value/enumdata|Diproses]].

| Kondisi | [[^output|Pass]] | [[^output|Name Conflict]] | Status | Hasil pada EnumData |
| ------- | ---------------- | ------------------------- | ------ | ------------------- |
| [[^field|Name]] berisi [[^value/string|Antri]] (belum digunakan) dan [[^field|Description]] berisi [[^value/text|Pesanan dalam antrean]] | EnumData [[^value/enumdata|Antri]] | - | [[^flowstate/Succeed]] | [[^field|Name]] dan [[^field|Description]] berubah. |
| [[^field|Name]] berisi [[^value/string|Menunggu]] (nama EnumData itu sendiri) | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] | Hanya [[^field|Description]] yang berubah. |
| [[^field|Description]] dibiarkan kosong | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] | [[^field|Description]] menjadi [[^value/empty]]. |
| [[^field|Name]] berisi [[^value/string|Diproses]] (sudah digunakan EnumData lain) | - | [[^value/boolean/true]] | [[^flowstate/Error]] | Tidak ada yang berubah. |
| [[^field|EnumData]] atau [[^field|Name]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] | Tidak ada yang berubah. |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Siapkan alur untuk output [[^output|Name Conflict]].** Output ini hanya keluar saat konflik terjadi, jadi hubungkan ke block yang menangani kegagalan, terpisah dari alur [[^output|Pass]].
- **Gunakan block ini untuk mengganti nama tanpa menyentuh nilai.** [[^field|Value]] dan [[^field|Selectable]] tetap aman karena tidak ikut berubah.
- **Ambil EnumData lewat [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]].** Tangani output [[^output|Is Empty]] pada alur terpisah agar block ini tidak dijalankan dengan input kosong.

## Batasan dan Catatan

- EnumData Header Setter adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Satu eksekusi hanya mengubah satu EnumData, dan hanya atribut [[^field|Name]] dan [[^field|Description]].
- Output [[^output|Name Conflict]] hanya keluar bernilai [[^value/boolean/true]] saat konflik terjadi. Bila tidak ada konflik, tidak ada output.
- Untuk mengubah [[^field|Value]] atau [[^field|Selectable]], gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value Setter|EnumData Value Setter Block]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Selectable Setter|EnumData Selectable Setter Block]], atau [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]