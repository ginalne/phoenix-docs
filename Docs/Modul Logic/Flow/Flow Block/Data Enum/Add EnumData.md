---
status: draft
title: Add EnumData
description: Flow Block untuk menambahkan EnumData baru ke sebuah Enum dari dalam Flow.
pageDecoration:
  icon: plus
  tree:
    priority: 7
---

# Add EnumData

>**note** Add EnumData merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

Add EnumData adalah Flow Block yang menambahkan [[Docs/Tipe Data/EnumData]] baru ke sebuah [[Docs/Tipe Data/Enum]] saat Flow berjalan. Anda menentukan Enum tujuan dan atribut EnumData baru, yaitu [[^field|Name]], [[^field|Value]], [[^field|Description]], dan [[^field|Selectable]]. Block ini juga melaporkan apakah penambahan gagal karena Name sudah digunakan atau Value tidak sesuai dengan Enum.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/add-enumdata-block-flow.png|Flow Block Add EnumData dengan lima input dan tiga output]]

<!--
  * [TODO] Perbarui gambar `add-enumdata-block-flow.png` agar memuat input Selectable. Anotasi yang disarankan: (1) input Enum, (2) input Name, (3) input Value, (4) input Description, (5) input Selectable, (6) output New EnumData, (7) output Name Conflict, (8) output Value Conflict.
-->

## Input dan Output

Add EnumData memiliki lima input di sisi kiri dan tiga output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Enum]] | [[Docs/Tipe Data/Enum]] | Enum tujuan penambahan EnumData. Isi dengan Enum atau hubungkan dari output block lain. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama EnumData baru. Name harus unik di dalam Enum yang sama. |
| [[^field|Value]] | [[^field|N/A Type]] | Nilai EnumData baru. Tipe data belum ditentukan sampai Anda mengaturnya, lihat [[#Menentukan Tipe Data Value]]. |
| [[^field|Description]] | [[Docs/Tipe Data/Text]] | Deskripsi EnumData baru. |
| [[^field|Selectable]] | [[Docs/Tipe Data/Boolean]] | Menentukan apakah EnumData baru tampil sebagai pilihan pada field berformat [[Docs/Tipe Data/EnumData]]. EnumData yang tidak selectable tetap dapat dipakai di tempat lain. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|New EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang baru ditambahkan. Tidak ada output bila penambahan gagal karena Name atau Value bermasalah. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Name sudah digunakan EnumData lain di Enum yang sama, tidak ada output bila tidak ada konflik. |
| [[^output|Value Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Value tidak sesuai dengan Enum tujuan, tidak ada output bila tidak ada konflik. |

### Menentukan Tipe Data Value

Teks merah [[^field|N/A Type]] pada input [[^field|Value]] berarti tipe data belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan [[^field|Format]] Enum tujuan. Semua tipe data Phoenix tersedia pada daftar ini.

>**note** Tipe data Value harus sama dengan Format Enum
> Value dianggap sesuai bila tipe datanya sama dengan [[^field|Format]] Enum tujuan. Block ini tidak mengonversi tipe data. Bila tidak sesuai, EnumData tidak ditambahkan dan output [[^output|Value Conflict]] bernilai [[^value/boolean/true]].

## Cara Kerja

Saat dieksekusi, Add EnumData memeriksa input secara berurutan sebelum menambahkan EnumData:

1. Block memeriksa [[^field|Name]]. Bila sudah digunakan EnumData lain di Enum yang sama, penambahan dihentikan dan [[^output|Name Conflict]] bernilai [[^value/boolean/true]]. [[^field|Value]] tidak diperiksa.
2. Bila [[^field|Name]] belum digunakan, block memeriksa [[^field|Value]]. Bila tidak sesuai dengan Enum tujuan, penambahan dihentikan dan [[^output|Value Conflict]] bernilai [[^value/boolean/true]].
3. Bila kedua pemeriksaan lolos, EnumData ditambahkan dan [[^output|New EnumData]] berisi EnumData tersebut.
4. Bila [[^field|Enum]] atau [[^field|Name]] dibiarkan kosong, block tidak dapat dijalankan.

Name EnumData dianggap sama bila sama persis, membedakan huruf besar dan kecil, menerima karakter simbol, dan spasi, enter, atau karakter tak terlihat di awal dan akhir dihapus (di-*trim*) saat disimpan.

[[^field|Value]] yang masih [[^field|N/A Type]] tetap dapat dieksekusi. EnumData tetap ditambahkan dan [[^field|Value]] pada EnumData menjadi [[^field|N/A Type]].

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> EnumData yang ditambahkan oleh Add EnumData tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|create]] pada Flow mana pun. Bila Anda membutuhkan proses lanjutan, hubungkan output [[^output|New EnumData]] langsung ke block berikutnya.

<!--
  * [TODO] Jawaban sebelumnya untuk Value yang masih N/A Type adalah "mungkin saja". Konfirmasi final: EnumData tetap ditambahkan tanpa Value Conflict, dan Value pada EnumData menjadi N/A Type.
  * [TODO] Konfirmasi perilaku input Selectable yang dibiarkan kosong (nilai bawaan EnumData baru).
-->

## Contoh Penggunaan

Contoh berikut memakai Enum [[^field/enum|Status Pesanan]] yang sudah memiliki EnumData [[^value/enumdata|Menunggu]] dan bertipe [[Docs/Tipe Data/Number]].

| Kondisi | [[^output|New EnumData]] | [[^output|Name Conflict]] | [[^output|Value Conflict]] | Status |
| ------- | ------------------------ | ------------------------- | -------------------------- | ------ |
| [[^field|Name]] berisi [[^value/string|Diproses]] (belum digunakan) dan [[^field|Value]] sesuai | EnumData baru [[^value/enumdata|Diproses]] | - | - | [[^flowstate/Succeed]] |
| [[^field|Name]] berisi [[^value/string|Menunggu]] (sudah digunakan) dan [[^field|Value]] sesuai | - | [[^value/boolean/true]] | - | [[^flowstate/Error]] |
| [[^field|Name]] belum digunakan, tetapi [[^field|Value]] tidak sesuai | - | - | [[^value/boolean/true]] | [[^flowstate/Error]] |
| [[^field|Name]] sudah digunakan dan [[^field|Value]] tidak sesuai | - | [[^value/boolean/true]] | - | [[^flowstate/Error]] |
| [[^field|Name]] belum digunakan dan [[^field|Value]] masih [[^field|N/A Type]] | EnumData baru [[^value/enumdata|Diproses]] dengan [[^field|Value]] [[^field|N/A Type]] | - | - | [[^flowstate/Succeed]] |
| [[^field|Enum]] atau [[^field|Name]] dibiarkan kosong | - | - | - | [[^flowstate/Fatal Error]] |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Siapkan alur penanganan untuk setiap output konflik.** [[^output|Name Conflict]] dan [[^output|Value Conflict]] hanya keluar saat konflik terjadi, jadi hubungkan keduanya ke block yang menangani kegagalan, terpisah dari alur [[^output|New EnumData]].
- **Tentukan tipe data [[^field|Value]] lebih dulu.** Samakan dengan [[^field|Format]] Enum tujuan agar [[^output|Value Conflict]] tidak keluar.
- **Gunakan [[^field|Name]] yang konsisten.** [[^field|Name]] dipakai sebagai alias oleh [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] untuk mengambil EnumData.

## Batasan dan Catatan

- Add EnumData adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Satu eksekusi hanya menambahkan satu EnumData.
- Pemeriksaan berurutan dari [[^field|Name]] lalu [[^field|Value]], sehingga hanya satu output konflik yang keluar dalam satu eksekusi.
- Output [[^output|Name Conflict]] dan [[^output|Value Conflict]] hanya keluar bernilai [[^value/boolean/true]] saat konflik terjadi. Bila tidak ada konflik, tidak ada output.
- Penambahan lewat block ini tidak mengikuti [[Docs/Modul Data/Enum/Konfigurasi Tegas|Strict On Selected]], karena aturan tersebut hanya berlaku saat EnumData dipilih pada field atau komponen data.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]

