---
status: draft
title: EnumData Setter
description: Flow Block untuk mengubah seluruh atribut sebuah EnumData, yaitu Name, Description, Value, dan Selectable, dari dalam Flow.
pageDecoration:
  icon: save
  tree:
    priority: 4
---

# EnumData Setter

>**note** EnumData Setter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData Setter adalah Flow Block yang memperbarui seluruh atribut pada [[Docs/Tipe Data/EnumData]] yang Anda tentukan saat Flow berjalan, yaitu [[^field|Name]], [[^field|Value]], [[^field|Description]], dan [[^field|Selectable]]. Satu eksekusi mengubah satu EnumData.

Gunakan block ini bila Anda ingin mengubah beberapa atribut sekaligus. Bila hanya satu kelompok atribut yang berubah, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value Setter|EnumData Value Setter Block]], [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Header Setter|EnumData Header Setter Block]], atau [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Selectable Setter|EnumData Selectable Setter Block]].

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-setter-block-flow.png|Flow Block EnumData Setter dengan lima input dan tiga output]]
## Input dan Output

EnumData Setter memiliki lima input di sisi kiri dan tiga output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang atributnya akan diubah. Isi dengan EnumData atau hubungkan dari output block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Name baru EnumData. Name harus unik di dalam Enum yang sama. |
| [[^field|Value]] | [[^field|N/A Type]] | Nilai baru EnumData. Tipe data belum ditentukan sampai Anda mengaturnya, lihat [[#Menentukan Tipe Data Value]]. |
| [[^field|Description]] | [[Docs/Tipe Data/Text]] | Deskripsi baru EnumData. |
| [[^field|Selectable]] | [[Docs/Tipe Data/Boolean]] | Menentukan apakah EnumData tampil sebagai pilihan pada field berformat [[Docs/Tipe Data/EnumData]]. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Pass]] | [[Docs/Tipe Data/EnumData]] | EnumData yang diubah, diteruskan ke block berikutnya. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Name sudah digunakan EnumData lain di Enum yang sama, tidak ada output bila tidak ada konflik. |
| [[^output|Value Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Value tidak sesuai dengan Enum tempat EnumData berada, tidak ada output bila tidak ada konflik. |

### Menentukan Tipe Data Value

Teks merah [[^field|N/A Type]] pada input [[^field|Value]] berarti tipe data belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan [[^field|Format]] Enum tempat EnumData berada. Semua tipe data Phoenix tersedia pada daftar ini.

## Cara Kerja

Saat dieksekusi, EnumData Setter memeriksa input secara berurutan sebelum mengubah EnumData:

1. Block memeriksa [[^field|Name]]. Bila sudah digunakan EnumData lain di Enum yang sama, perubahan dihentikan dan [[^output|Name Conflict]] bernilai [[^value/boolean/true]]. [[^field|Value]] tidak diperiksa.
2. Bila [[^field|Name]] lolos, block memeriksa [[^field|Value]]. Bila tipe datanya tidak sama dengan [[^field|Format]] Enum, perubahan dihentikan dan [[^output|Value Conflict]] bernilai [[^value/boolean/true]]. Block ini tidak mengonversi tipe data.
3. Bila [[^field|Enum]], [[^field|Name]], [[^field|Selectable]] dibiarkan kosong, block tidak dapat dijalankan.
4. Bila ketiga pemeriksaan lolos, seluruh atribut EnumData diganti dengan nilai pada input, lalu output [[^output|Pass]] meneruskan EnumData tersebut.

Aturan [[^field|Name]] sama dengan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]]: dianggap sama bila sama persis, membedakan huruf besar dan kecil, menerima karakter simbol, dan di-*trim* saat disimpan.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan atribut oleh EnumData Setter tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|update]] pada Flow mana pun.


## Contoh Penggunaan

Contoh berikut mengubah EnumData [[^value/enumdata|Menunggu]] pada Enum [[^field/enum|Status Pesanan]] yang bertipe [[Docs/Tipe Data/Number]]. Enum yang sama juga memiliki EnumData [[^value/enumdata|Diproses]].

| Kondisi | [[^output|Pass]] | [[^output|Name Conflict]] | [[^output|Value Conflict]] | Status | Hasil pada EnumData |
| ------- | ---------------- | ------------------------- | -------------------------- | ------ | ------------------- |
| [[^field|Name]] berisi [[^value/string|Antri]] (belum digunakan) dan [[^field|Value]] berisi [[^value/number|10]] | EnumData [[^value/enumdata|Antri]] | - | - | [[^flowstate/Succeed]] | Seluruh atribut diganti dengan nilai input. |
| [[^field|Name]] berisi [[^value/string|Menunggu]] (nama EnumData itu sendiri) | EnumData [[^value/enumdata|Menunggu]] | - | - | [[^flowstate/Succeed]] | [[^field|Name]] tidak berubah, atribut lain diganti. |
| [[^field|Name]] berisi [[^value/string|Diproses]] (sudah digunakan EnumData lain) | - | [[^value/boolean/true]] | - | [[^flowstate/Error]] | Tidak ada yang berubah. |
| [[^field|Name]] belum digunakan, [[^field|Value]] berisi [[^value/string|aktif]] bertipe [[Docs/Tipe Data/String]] | - | - | [[^value/boolean/true]] | [[^flowstate/Error]] | Tidak ada yang berubah. |
| [[^field|Name]] sudah digunakan dan [[^field|Value]] tidak sesuai | - | [[^value/boolean/true]] | - | [[^flowstate/Error]] | Tidak ada yang berubah. |
| [[^field|EnumData]] atau [[^field|Name]] dibiarkan kosong | - | - | - | [[^flowstate/Fatal Error]] | Tidak ada yang berubah. |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Pilih Setter yang sesuai kebutuhan.** Bila hanya satu kelompok atribut yang berubah, block Setter khusus lebih aman karena atribut lain tidak ikut tergantikan.
- **Siapkan alur untuk setiap output konflik.** [[^output|Name Conflict]] dan [[^output|Value Conflict]] hanya keluar saat konflik terjadi, jadi hubungkan keduanya ke block yang menangani kegagalan, terpisah dari alur [[^output|Pass]].
- **Tentukan tipe data [[^field|Value]] lebih dulu.** Samakan dengan [[^field|Format]] Enum agar [[^output|Value Conflict]] tidak keluar.

## Batasan dan Catatan

- EnumData Setter adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Satu eksekusi hanya mengubah satu EnumData.
- Pemeriksaan berurutan dari [[^field|Name]] lalu [[^field|Value]], sehingga hanya satu output konflik yang keluar dalam satu eksekusi.
- Output [[^output|Name Conflict]] dan [[^output|Value Conflict]] hanya keluar bernilai [[^value/boolean/true]] saat konflik terjadi. Bila tidak ada konflik, tidak ada output.
- Perubahan bersifat langsung pada EnumData di Enum. Anda tidak perlu menyimpannya lagi.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value Setter|EnumData Value Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Header Setter|EnumData Header Setter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Selectable Setter|EnumData Selectable Setter Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]