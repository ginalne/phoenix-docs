---
status: draft
title: Add EnumData
description: Flow Block untuk menambahkan EnumData baru ke sebuah Enum dari dalam Flow.
---

# Add EnumData

>**note** Add EnumData merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

Add EnumData adalah Flow Block yang menambahkan [[Docs/Tipe Data/EnumData]] baru ke sebuah [[Docs/Tipe Data/Enum]] saat Flow berjalan. Anda menentukan Enum tujuan dan atribut EnumData baru, yaitu [[^field|Name]], [[^field|Value]], dan [[^field|Description]]. Block ini juga melaporkan apakah penambahan gagal karena Name sudah digunakan atau Value tidak sesuai dengan Enum.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/add-enumdata-block-flow.png|Flow Block Add EnumData dengan empat input dan tiga output]]

<!--
  * [DONE] Letakkan gambar `add-enumdata-block-flow.png` (potongan block Add EnumData dari Blueprint). Screenshot saat ini belum memiliki output Value Conflict, jadi mohon ambil ulang setelah output tersebut ditambahkan. Anotasi yang disarankan: (1) input Enum, (2) input Name, (3) input Value, (4) input Description, (5) output New EnumData, (6) output Name Conflict, (7) output Value Conflict.
-->

## Input dan Output

Add EnumData memiliki empat input di sisi kiri dan tiga output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Enum]] | [[Docs/Tipe Data/Enum]] | Enum tujuan penambahan EnumData. Isi dengan Enum atau hubungkan dari output block lain. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama EnumData baru. Name harus unik di dalam Enum yang sama. |
| [[^field|Value]] | [[^field|N/A Type]] | Nilai EnumData baru. Tipe data belum ditentukan sampai Anda mengaturnya, lihat [[#Menentukan Tipe Data Value]]. |
| [[^field|Description]] | [[Docs/Tipe Data/Text]] | Deskripsi EnumData baru. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|New EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang baru ditambahkan. Berisi [[^value/empty]] bila penambahan gagal karena Name atau Value bermasalah. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Name sudah digunakan EnumData lain di Enum yang sama, [[^value/boolean/false]] bila belum. |
| [[^output|Value Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Value tidak sesuai dengan Enum tujuan, [[^value/boolean/false]] bila sesuai. |

### Menentukan Tipe Data Value

Teks merah [[^field|N/A Type]] pada input [[^field|Value]] berarti tipe data belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan [[^field|Format]] Enum tujuan. Semua tipe data Phoenix tersedia pada daftar ini.

>**note** Tipe data Value harus sesuai dengan Enum
> Bila Value tidak sesuai dengan Enum tujuan, EnumData tidak ditambahkan dan output [[^output|Value Conflict]] bernilai [[^value/boolean/true]].

<!--
  * [TODO] Konfirmasi apakah Value yang masih [[^field|N/A Type]] dapat dieksekusi (pada Add Variable, Value yang masih N/A Type tetap tersimpan), atau langsung menghasilkan Value Conflict.
    Jawaban: mungkin saja, karena enum bisa menyimpan atribut type data kosong. bagian value akan menjadi N/A Type
  * [TODO] Konfirmasi kriteria "sesuai" pada Value Conflict: apakah tipe data Value harus sama dengan [[^field|Format]] Enum, atau cukup dapat dikonversi.
    Jawaban: 
-->

## Cara Kerja

Saat dieksekusi, Add EnumData memeriksa [[^field|Name]] dan [[^field|Value]] sebelum menambahkan EnumData:

1. Block memeriksa apakah [[^field|Name]] sudah digunakan EnumData lain di Enum yang sama.
2. Block memeriksa apakah [[^field|Value]] sesuai dengan Enum tujuan.
3. Bila kedua pemeriksaan lolos, EnumData ditambahkan dan [[^output|New EnumData]] berisi EnumData tersebut.
4. Bila salah satunya tidak lolos, EnumData tidak ditambahkan, [[^output|New EnumData]] berisi [[^value/empty]], dan output konflik yang bersangkutan bernilai [[^value/boolean/true]].

Name EnumData dianggap sama bila sama persis, membedakan huruf besar dan kecil, menerima karakter simbol, dan spasi, enter, atau karakter tak terlihat di awal dan akhir dihapus (di-*trim*) saat disimpan.

>**warning** Perhatikan Strict On Selected
> Penambahan EnumData lewat Flow tetap dipengaruhi pengaturan [[Docs/Modul Data/Enum/Konfigurasi Tegas|Strict On Selected]] pada Enum tujuan. Periksa pengaturan tersebut sebelum menambahkan EnumData secara otomatis.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> EnumData yang ditambahkan oleh Add EnumData tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|create]]. Bila Anda membutuhkan proses lanjutan, hubungkan output [[^output|New EnumData]] langsung ke block berikutnya.

<!--
  * [TODO] Konfirmasi dampak Strict On Selected pada EnumData yang ditambahkan lewat Flow. Isi callout warning di atas masih draf.
  * [TODO] Konfirmasi apakah aturan Name EnumData (sama persis, membedakan huruf besar dan kecil, menerima simbol, di-trim) sama dengan aturan Name Variable Data.
  * [TODO] Konfirmasi apakah bila Name dan Value sama-sama bermasalah, kedua output konflik bernilai true.
  * [TODO] Konfirmasi apakah callout "tidak memicu Flow kembali" berlaku untuk semua Flow atau hanya Flow yang sama.
-->

## Contoh Penggunaan

Contoh berikut memakai Enum untuk status pesanan yang memiliki EnumData [[^value/enumdata|Menunggu]].

| Kondisi | [[^output|New EnumData]] | [[^output|Name Conflict]] | [[^output|Value Conflict]] |
| ------- | ------------------------ | ------------------------- | -------------------------- |
| [[^field|Name]] berisi `Diproses` (belum digunakan) dan [[^field|Value]] sesuai | [[^value/enumdata|Diproses]] | [[^value/boolean/false]] | [[^value/boolean/false]] |
| [[^field|Name]] berisi `Menunggu` (sudah digunakan) dan [[^field|Value]] sesuai | [[^value/empty]] | [[^value/boolean/true]] | [[^value/boolean/false]] |
| [[^field|Name]] belum digunakan, tetapi [[^field|Value]] tidak sesuai | [[^value/empty]] | [[^value/boolean/false]] | [[^value/boolean/true]] |
| [[^field|Name]] sudah digunakan dan [[^field|Value]] tidak sesuai | [[^value/empty]] | [[^value/boolean/true]] | [[^value/boolean/true]] |
| [[^field|Enum]] atau [[^field|Name]] dibiarkan kosong | Tidak ada output, terjadi error yang dilaporkan di [[Docs/Modul Logic/Flow/Flow Activity]] | - | - |

<!--
  * [TODO] Nama contoh (Enum status pesanan, EnumData Menunggu dan Diproses) bersifat generik. Sesuaikan bila perlu.
  * [TODO] Konfirmasi perilaku Enum atau Name yang dibiarkan kosong (diasumsikan error seperti pada Add Variable).
-->

## Praktik Terbaik

- **Periksa [[^output|Name Conflict]] dan [[^output|Value Conflict]] sebelum memakai [[^output|New EnumData]].** Hubungkan keduanya ke [[Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If|If Operator Block]] agar Flow dapat bercabang saat penambahan gagal.
- **Tentukan tipe data [[^field|Value]] lebih dulu.** Samakan dengan [[^field|Format]] Enum tujuan agar [[^output|Value Conflict]] tidak bernilai [[^value/boolean/true]].
- **Gunakan [[^field|Name]] yang konsisten.** [[^field|Name]] dipakai sebagai alias oleh [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] untuk mengambil EnumData.

## Batasan dan Catatan

- Add EnumData adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Satu eksekusi hanya menambahkan satu EnumData.
- Output [[^output|Name Conflict]] dan [[^output|Value Conflict]] selalu bernilai [[^value/boolean/true]] atau [[^value/boolean/false]], tidak pernah [[^value/empty]].
- Block ini tidak memiliki input [[^field|Selectable]], sehingga atribut tersebut tidak dapat ditentukan dari Flow.

<!--
  * [TODO] Konfirmasi nilai [[^field|Selectable]] pada EnumData yang ditambahkan lewat Add EnumData (nilai bawaan) dan apakah perlu input tambahan.
  * [TODO] Halaman baru yang ditautkan dan perlu dibuat: `Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan` (pengenalan kelompok), `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter`, `Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event`, `Docs/Modul Data/Enum/Konfigurasi Tegas`, `Docs/Modul Logic/Flow/Flow Block/Operator/Boolean/If`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan `Docs/Modul Logic/Flow/Flow Activity`.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]