---
    status: draft
    title: Variable
    description: Flow Block untuk mengurai Variable Data menjadi nilai atributnya.
    pageDecoration:
      icon: grid
      tree:
        priority: 4
---
# Variable

>**note** Variable merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Variable adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk mengubah satu [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] menjadi nilai atributnya, yaitu [[^field|Name]], [[^field|Description]], dan [[^field|Value]]. Block ini memiliki satu input di sisi kiri dan empat output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/variable-block-flow.png|Flow Block Variable dengan satu input dan empat output]]

## Input dan Output

Variable memiliki satu input di sisi kiri dan empat output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang akan diurai. Isi dengan Variable Data atau hubungkan dari output block lain, misalnya [[^output|Variable]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Pass]] | [[Docs/Tipe Data/Variable]] | Variable Data yang diinput lewat [[^field|Variable]], diteruskan apa adanya agar dapat dipakai block berikutnya. |
| [[^output|Name]] | [[Docs/Tipe Data/String]] | Name dari Variable Data. |
| [[^output|Description]] | [[Docs/Tipe Data/Text]] | Description dari Variable Data. |
| [[^output|Value]] | Mengikuti Type Variable Data | Value dari Variable Data. |

## Cara Kerja

1. Block menerima Variable Data lewat [[^field|Variable]].
2. Block membaca atribut Variable Data dan mengirimkannya lewat [[^output|Name]], [[^output|Description]], dan [[^output|Value]]. Variable Data yang sama juga diteruskan lewat [[^output|Pass]].
3. Tipe data [[^output|Value]] mengikuti Type Variable Data. Jika Variable Data bertipe [[Docs/Tipe Data/Number]], [[^output|Value]] berupa [[Docs/Tipe Data/Number]].

Gunakan Variable bila Anda membutuhkan lebih dari satu atribut. Bila hanya membutuhkan nilainya, [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] lebih ringkas.

## Contoh Penggunaan

| Kondisi | [[^output|Pass]] | [[^output|Name]] | [[^output|Description]] | [[^output|Value]] | Status |
| ------- | ---------------- | ---------------- | ----------------------- | ----------------- | ---- |
| [[^field|Variable]] berisi Variable Data [[^value/string|batas_stok_minimum]] bertipe [[Docs/Tipe Data/Number]] dengan nilai [[^value/number|50]] | Variable Data `batas_stok_minimum` | [[^value/string|batas_stok_minimum]] | Description Variable Data | [[^value/number|50]] | [[^flowstate/Succeed ]] |
| [[^field|Variable]] dibiarkan kosong | - | - | - | - | [[^flowstate/Fatal Error]] |

Hubungkan [[^output|Name]] dan [[^output|Description]] ke block yang menyusun pesan, misalnya [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]], dan hubungkan [[^output|Value]] ke block yang membandingkan atau menghitung.

## Praktik Terbaik

- **Pasangkan dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** agar Variable Data diambil lewat Name dan kegagalannya dapat ditangani lewat [[^output|Is Empty]].
- **Gunakan [[^output|Pass]]** untuk meneruskan Variable Data yang sama ke block Variable berikutnya, misalnya [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].

## Batasan dan Catatan

- Variable hanya membaca data dan tidak mengubah Variable Data. Untuk mengubah nilainya, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].
- Variable adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Tipe data [[^output|Value]] tidak ditampilkan pada block di halaman kerja dan berbeda untuk setiap Variable Data. Bila tidak cocok dengan block penerima, ketidakcocokan dilaporkan di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] saat Flow berjalan.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

