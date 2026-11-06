---
    status: draft
    title: Enum
    description: Flow Block untuk mengambil atribut sebuah Enum, yaitu Name dan Description, agar dapat dipakai block lain.
    pageDecoration:
      icon: grid
      tree:
        priority: 5
---
# Enum

>**note** Enum merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

Enum adalah Flow Block yang mengubah sebuah [[Docs/Tipe Data/Enum]] menjadi atribut-atributnya, yaitu [[^field|Name]] dan [[^field|Description]]. Dengan block ini, Anda dapat memakai nama dan deskripsi Enum sebagai data biasa pada block lain di Flow.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enum-block-flow.png|Flow Block Enum dengan satu input dan tiga output]]
<!--
  * [DONE] Letakkan gambar `enum-block-flow.png` (potongan block Enum dari Blueprint). Anotasi yang disarankan: (1) input Enum, (2) output Pass, (3) output Name, (4) output Desc.
-->

## Input dan Output

Enum memiliki satu input di sisi kiri dan tiga output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Enum]] | [[Docs/Tipe Data/Enum]] | Enum yang atributnya akan diambil. Isi dengan Enum atau hubungkan dari output block lain. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Pass]] | [[Docs/Tipe Data/Enum]] | Enum yang sama dengan input, diteruskan ke block berikutnya. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | [[^field|Name]] dari Enum. |
| [[^output|Desc]] | [[Docs/Tipe Data/Text]] | [[^field|Description]] dari Enum. |

<!--
  * [TODO] Konfirmasi tipe data output Desc (Text atau String) dan apakah Pass bertipe Enum.
    Jawaban: Sudah benar
-->

## Cara Kerja

Saat dieksekusi, Enum membaca Enum pada input [[^field|Enum]] lalu mengeluarkan atributnya pada masing-masing output. Block ini hanya membaca data, sehingga Enum tidak berubah.

Output [[^output|Pass]] meneruskan Enum yang sama agar dapat dihubungkan ke block lain yang membutuhkan Enum, misalnya input [[^field|Enum]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Add EnumData|Add EnumData Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]].

## Contoh Penggunaan

Contoh berikut memakai Enum bernama `Status Pesanan` dengan deskripsi `Daftar status pesanan`.

| Kondisi | [[^output|Pass]] | [[^output|Name]] | [[^output|Desc]] |
| ------- | ---------------- | ---------------- | ---------------- |
| [[^field|Enum]] terisi | Enum `Status Pesanan` | [[^value/string|Status Pesanan]] | [[^value/string|Daftar status pesanan]] |
| [[^field|Enum]] dibiarkan kosong | [[^value/empty]] | [[^value/empty]] | [[^value/empty]] |

<!--
  * [TODO] Konfirmasi perilaku Enum yang dibiarkan kosong: diasumsikan seluruh output bernilai empty (seperti block Variable), bukan error.
    Jawaban: 
  * [TODO] Nama contoh (Enum Status Pesanan) bersifat generik. Sesuaikan bila perlu.
-->

## Praktik Terbaik

- **Gunakan [[^output|Pass]] untuk menyambung ke block berikutnya.** Anda tidak perlu mengisi Enum berulang kali pada setiap block di satu alur.
- **Gabungkan [[^output|Name]] dengan teks lain** memakai [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]] untuk membuat pesan yang menyebut nama Enum.

## Batasan dan Catatan

- Enum adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Block ini hanya mengambil [[^field|Name]] dan [[^field|Description]]. Atribut lain seperti [[^field|Format]], [[^field|Header]], dan [[^field|Strict On Selected]] tidak tersedia sebagai output.
- Untuk mengambil atribut EnumData, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]].

<!--
  * [TODO] Halaman baru yang ditautkan dan perlu dibuat: `Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter`, `Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate`, dan `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/Enum]]