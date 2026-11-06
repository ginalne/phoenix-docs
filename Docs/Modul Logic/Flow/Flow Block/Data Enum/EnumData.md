---
    status: draft
    title: EnumData
    description: Flow Block untuk mengambil atribut sebuah EnumData, yaitu Name, Description, dan Value, agar dapat dipakai block lain.
    pageDecoration:
      icon: grid
      tree:
        priority: 4
---

# EnumData

>**note** EnumData merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData adalah Flow Block yang mengubah sebuah [[Docs/Tipe Data/EnumData]] menjadi atribut-atributnya, yaitu [[^field|Name]], [[^field|Description]], dan [[^field|Value]]. Dengan block ini, Anda dapat memakai isi EnumData sebagai data biasa pada block lain di Flow.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-block-flow.png|Flow Block EnumData dengan satu input dan empat output]]

<!--
  * [DONE] Letakkan gambar `enumdata-block-flow.png` (potongan block EnumData dari Blueprint). Anotasi yang disarankan: (1) input EnumData, (2) output Pass, (3) output Name, (4) output Description, (5) output Value.
-->

## Input dan Output

EnumData memiliki satu input di sisi kiri dan empat output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang atributnya akan diambil. Isi dengan EnumData atau hubungkan dari output block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Pass]] | [[Docs/Tipe Data/EnumData]] | EnumData yang sama dengan input, diteruskan ke block berikutnya. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | [[^field|Name]] dari EnumData. |
| [[^output|Description]] | [[Docs/Tipe Data/Text]] | [[^field|Description]] dari EnumData. |
| [[^output|Value]] | Mengikuti [[^field|Format]] Enum | [[^field|Value]] dari EnumData. Tipe data output menyesuaikan [[^field|Format]] pada Enum tempat EnumData berada. |

<!--
  * [TODO] Konfirmasi tipe data output Description (Text atau String) dan apakah Pass bertipe EnumData.
    Jawaban : Sudah ok
  * [TODO] Pengetahuan sebelumnya menyebut block ini juga mengambil atribut Selectable, tetapi screenshot hanya menampilkan Pass, Name, Description, dan Value. Halaman ini mengikuti screenshot. Konfirmasi apakah output Selectable akan ditambahkan.
    Jawaban: perlu ditambahkan
-->

## Cara Kerja

Saat dieksekusi, EnumData membaca EnumData pada input [[^field|EnumData]] lalu mengeluarkan atributnya pada masing-masing output. Block ini hanya membaca data, sehingga EnumData tidak berubah.

Output [[^output|Pass]] meneruskan EnumData yang sama agar dapat dihubungkan ke block lain yang membutuhkan EnumData, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]] atau [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Delete EnumData|Delete EnumData Block]].

## Contoh Penggunaan

Contoh berikut memakai EnumData [[^value/enumdata|Menunggu]] dengan deskripsi [[^value/text|Pesanan belum diproses]] dan [[^field|Value]] berisi angka `1` pada Enum berformat angka.

| Kondisi | [[^output|Pass]] | [[^output|Name]] | [[^output|Description]] | [[^output|Value]] | Status |
| ------- | ---------------- | ---------------- | ----------------------- | ---- | ---- |
| [[^field|EnumData]] terisi | EnumData [[^value/enumdata|Menunggu]] | [[^value/string|Menunggu]] | [[^value/text|Pesanan belum diproses]] | [[^value/number|1]] | [[^flowstate/Succeed]]  |
| [[^field|EnumData]] dibiarkan kosong | - | - | - | - | [[^flowstate/Error]] |

<!--
  * [TODO] Konfirmasi perilaku EnumData yang dibiarkan kosong: diasumsikan seluruh output bernilai empty (seperti block Variable), bukan error.
    Jawaban: Sudah saya perbaiki
  * [DONE] Nama dan nilai contoh (EnumData Menunggu, Value 1) bersifat generik. Sesuaikan bila perlu.
-->

## Praktik Terbaik

- **Pilih block sesuai kebutuhan.** Gunakan EnumData bila Anda membutuhkan lebih dari satu atribut, dan gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]] bila hanya membutuhkan [[^field|Value]].
- **Gunakan [[^output|Pass]] untuk menyambung ke block berikutnya.** Anda tidak perlu mengisi EnumData berulang kali pada setiap block di satu alur.

## Batasan dan Catatan

- EnumData adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Block ini hanya mengambil [[^field|Name]], [[^field|Description]], dan [[^field|Value]]. Atribut [[^field|Selectable]] tidak tersedia sebagai output.
- Tipe data output [[^output|Value]] tidak ditampilkan di halaman kerja dan tidak memengaruhi block yang dihubungkan. Bila tipenya tidak cocok dengan input block berikutnya, ketidakcocokan dilaporkan di [[Docs/Modul Logic/Flow/Flow Activity]] saat Flow berjalan.
- Untuk mengambil atribut Enum, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Enum|Enum Block]].

<!--
  * [DONE] Halaman baru yang ditautkan dan perlu dibuat: `Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan `Docs/Modul Logic/Flow/Flow Activity`.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Enum|Enum Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]]
- [[Docs/Modul Data/Enum/Enum Data/Pengenalan|Enum Data]]
- [[Docs/Tipe Data/EnumData]]