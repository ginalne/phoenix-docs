---
    status: draft
    title: EnumData Setter
    description: Flow Block untuk mengubah Value sebuah EnumData dari dalam Flow.
    pageDecoration:
      icon: save
      tree:
        priority: 4
---

# EnumData Setter

>**note** EnumData Setter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]] di Phoenix.

EnumData Setter adalah Flow Block yang memperbarui [[^field|Value]] pada [[Docs/Tipe Data/EnumData]] yang Anda tentukan saat Flow berjalan. Satu eksekusi mengubah satu EnumData.

![[Docs/Modul Logic/Flow/Flow Block/Data Enum/enumdata-setter-block-flow.png|Flow Block EnumData Setter dengan dua input dan satu output]]
<!--
  * [DONE] Letakkan gambar `enumdata-setter-block-flow.png` (potongan block EnumData Setter dari Blueprint). Anotasi yang disarankan: (1) input EnumData, (2) input Value, (3) output Pass.
-->

## Input dan Output

EnumData Setter memiliki dua input di sisi kiri dan satu output di sisi kanan. Block ini tidak memiliki Control.

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|EnumData]] | [[Docs/Tipe Data/EnumData]] | EnumData yang [[^field|Value]]-nya akan diubah. Isi dengan EnumData atau hubungkan dari output block lain, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]. |
| [[^field|Value]] | [[^field|N/A Type]] | Nilai baru yang akan disimpan pada EnumData. Tipe data belum ditentukan sampai Anda mengaturnya, lihat [[#Menentukan Tipe Data Value]]. |

### Output

| Output | Tipe Data | Isi |
| ------ | --------- | --- |
| [[^output|Pass]] | [[Docs/Tipe Data/EnumData]] | EnumData yang diubah, diteruskan ke block berikutnya. |
| [[^output|Value Conflict]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] bila Value tidak sesuai dengan Enum tujuan, tidak ada output jika tidak ada konflik. |

### Menentukan Tipe Data Value

Teks merah [[^field|N/A Type]] pada input [[^field|Value]] berarti tipe data belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan [[^field|Format]] Enum tempat EnumData berada. Semua tipe data Phoenix tersedia pada daftar ini.

<!--
  * [TODO] Konfirmasi apakah Pass meneruskan EnumData yang diubah (diasumsikan mengikuti Pass pada Variable Setter).
    Jawaban: betul
  * [TODO] Konfirmasi perilaku Value yang tipenya tidak sesuai dengan Format Enum (diasumsikan terjadi error yang dilaporkan di Flow Activity, karena block ini tidak memiliki output Value Conflict seperti Add EnumData).
    Jawaban: Sudah diperbaiki
  * [TODO] Pengetahuan sebelumnya menyebut block ini dapat mengubah keempat atribut EnumData (Name, Description, Value, Selectable), tetapi screenshot hanya menampilkan input EnumData dan Value. Halaman ini mengikuti screenshot dan penjelasan Anda. Konfirmasi apakah input atribut lain akan ditambahkan.
    Jawaban: Saya lupa, mohon sesuaikan seperti pengetahuan sebelumnya. Sepertinya bagus juga kalau kita juga buatkan block setter lain agar lebih holistik yaitu. EnumData Value Setter (input enumdata dan value), EnumData Header Setter (input enumdata, name dan desc. outputnya ada name conflict), EnumData Selectable Setter (inputnya EnumData(s) agar dapat mengeksekusi lebih dari satu enumdata, dan nilai selectable [boolean]).
-->

## Cara Kerja

Saat dieksekusi, EnumData Setter mengganti [[^field|Value]] pada EnumData yang ditunjuk dengan nilai pada input [[^field|Value]]. Setelah perubahan tersimpan, output [[^output|Pass]] meneruskan EnumData tersebut agar dapat dipakai block berikutnya.

Block ini hanya mengubah [[^field|Value]]. Atribut lain pada EnumData, yaitu [[^field|Name]], [[^field|Description]], dan [[^field|Selectable]], tidak berubah.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Perubahan [[^field|Value]] oleh EnumData Setter tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event|Enum Data Event Block]] dengan Event [[^value/string|update]].

<!--
  * [DONE] Konfirmasi apakah callout "tidak memicu Flow kembali" berlaku untuk semua Flow atau hanya Flow yang sama.
    Jawaban : Betul
-->

## Contoh Penggunaan

Contoh berikut memakai EnumData [[^value/enumdata|Menunggu]] yang [[^field|Value]]-nya semula `1` pada Enum bertipe [[Docs/Tipe Data/Number]].

| Kondisi | [[^output|Pass]] | [[^output|Value Conflict]] | Status | Hasil pada EnumData |
| ------- | ---------------- | ------- | -----  | ------------------- |
| [[^field|Value]] berisi [[^value/number|10]] | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] | [[^field|Value]] berubah dari `1` menjadi `10`. |
| [[^field|Value]] berisi nilai yang sama dengan sebelumnya | EnumData [[^value/enumdata|Menunggu]] | - |[[^flowstate/Succeed]] | Tidak ada yang berubah.
| [[^field|Value]] dibiarkan kosong, namun tipe nya [[Docs/Tipe Data/Number]] | EnumData [[^value/enumdata|Menunggu]] | - | [[^flowstate/Succeed]] | [[^field|Value]] berubah dari `1` menjadi [[^value/empty]]. |
| [[^field|Value]] berisi [[^value/string|aktif]] bertipe [[Docs/Tipe Data/String]] | - | [[^value/boolean/true]] | [[^flowstate/Error]] | Tidak ada. |
| [[^field|EnumData]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]]  | Tidak ada. |

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].
<!--
  * [DONE] Konfirmasi perilaku EnumData yang dibiarkan kosong (diasumsikan error seperti Variable Setter) dan perilaku Value yang dibiarkan kosong (apakah Value EnumData menjadi kosong atau terjadi error). Baris terakhir tabel perlu dilengkapi atau dihapus.
    Jawaban: Sudah saya sesuaikan
    
  * [DONE] Nama dan nilai contoh (EnumData Menunggu, Value 1 dan 10) bersifat generik. Sesuaikan bila perlu.
-->

## Praktik Terbaik

- **Pastikan EnumData yang dituju benar.** Ambil EnumData lewat [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]] dan periksa [[^output|Is Empty]] sebelum menghubungkannya ke input [[^field|EnumData]].
- **Tentukan tipe data [[^field|Value]] lebih dulu.** Samakan dengan [[^field|Format]] Enum agar nilai dapat disimpan.
- **Baca hasil perubahan lewat [[^output|Pass]].** Hubungkan [[^output|Pass]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]] bila Anda ingin memakai nilai terbaru pada block berikutnya.

## Batasan dan Catatan

- EnumData Setter adalah Flow Block non-Event, sehingga baru diproses setelah memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi]].
- Satu eksekusi hanya mengubah satu EnumData, dan hanya atribut [[^field|Value]].
- Perubahan [[^field|Value]] bersifat langsung pada EnumData di Enum. Anda tidak perlu menyimpannya lagi.

<!--
  * [DONE] Halaman baru yang ditautkan dan perlu dibuat: `Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter`, `Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value`, `Docs/Modul Logic/Flow/Flow Block/Event/Enum Data Event`, `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`, dan `Docs/Modul Logic/Flow/Flow Activity`.
-->

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/Pengenalan|Flow Block Data Enum]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Getter|EnumData Getter Block]]
- [[Docs/Modul Logic/Flow/Flow Block/Data Enum/EnumData Value|EnumData Value Block]]
- [[Docs/Modul Data/Enum/Apa itu Enum|Enum]]
- [[Docs/Tipe Data/EnumData]]

