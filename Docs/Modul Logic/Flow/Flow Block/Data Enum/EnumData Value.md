---
    status: draft
    title: EnumData Value
    description: Flow Block untuk mengambil Value sebuah EnumData sebagai data langsung.
    pageDecoration:
      icon: grid
      tree:
        priority: 3
---

# EnumData Value

>**note** EnumData Value merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData Value adalah Flow Block yang mengambil [[^field|Value]] dari sebuah [[Docs/Tipe Data/EnumData]] dan mengeluarkannya sebagai data langsung. Tipe data output mengikuti sumber nilainya, sehingga Anda dapat langsung menghubungkannya ke block lain tanpa mengambil atribut yang tidak dibutuhkan.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-value-block-flow.png|Flow Block EnumData Value dengan satu input dan satu output]]

<!--
  * [DONE] Letakkan gambar `enumdata-value-block-flow.png` (potongan block EnumData Value dari Blueprint). Anotasi yang disarankan: (1) input EnumData, (2) output Value.
-->

## Input dan Output

EnumData Value memiliki satu input di sisi kiri dan satu output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang [[^field|Value]]-nya akan diambil. Isi dengan EnumData atau hubungkan dari output block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Value]] | Mengikuti sumber nilai | [[^field|Value]] dari EnumData sebagai data langsung. Tipe data menyesuaikan [[^field|Format]] pada Enum tempat EnumData berada. |

## Cara Kerja

Saat dieksekusi, EnumData Value membaca [[^field|Value]] pada EnumData di input [[^field|EnumData]] lalu mengeluarkannya apa adanya pada output [[^output|Value]]. Block ini hanya membaca data, sehingga EnumData tidak berubah.

Perbedaannya dengan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]]: EnumData Block mengeluarkan beberapa atribut sekaligus, sedangkan EnumData Value hanya mengeluarkan [[^field|Value]].

Tipe data output [[^output|Value]] tidak ditampilkan di halaman kerja dan tidak memengaruhi block yang dihubungkan. Bila tipenya tidak cocok dengan input block berikutnya, ketidakcocokan dilaporkan di [[Docs/Modul Logic/Flow/Flow Activity]] saat Flow berjalan.

## Contoh Penggunaan

Contoh berikut memakai EnumData [[^value/enumdata|Menunggu]] pada Enum [[^field/enum|status pesanan]].

| Kondisi | [[^output|Value]] | Status |
| ------- | ----------------- | ------ |
| EnumData berada di Enum berformat angka dengan [[^field|Value]] `1` | [[^value/number|1]] | [[^flowstate/Succeed]] |
| EnumData berada di Enum berformat teks dengan [[^field|Value]] `MENUNGGU` | [[^value/string|MENUNGGU]] |[[^flowstate/Succeed]] |
| [[^field|EnumData]] dibiarkan kosong | - |[[^flowstate/Fatal Error]] |

Status [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].
<!--
  * [DONE] Konfirmasi perilaku EnumData yang dibiarkan kosong (diasumsikan error seperti Variable Value).
  * [DONE] Nama dan nilai contoh (EnumData Menunggu, Value 1 dan MENUNGGU) bersifat generik. Sesuaikan bila perlu.
-->

## Praktik Terbaik

- **Gunakan EnumData Value bila hanya butuh nilainya.** Block ini lebih ringkas dibanding [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]] yang mengeluarkan banyak atribut.
- **Periksa [[^output|Is Empty]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] terlebih dahulu.** Dengan begitu EnumData yang dibiarkan kosong tidak sampai menimbulkan error.
- **Pastikan block berikutnya menerima tipe data yang sesuai.** Samakan dengan [[^field|Format]] Enum asal EnumData.

## Batasan dan Catatan

- EnumData Value adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Block ini hanya mengambil [[^field|Value]]. Untuk atribut lain, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]].
- Block ini hanya membaca data. Untuk mengubah [[^field|Value]], gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter|EnumData Setter Block]].

<!--
  * [DONE] Halaman baru yang ditautkan dan perlu dibuat: `Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Setter`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan `Docs/Modul Logic/Flow/Flow Activity`.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData|EnumData Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]

