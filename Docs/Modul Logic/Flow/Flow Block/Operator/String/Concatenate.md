---
    status: release
    title: Concatenate Operator Block
    description: Menghubungkan dua string input menjadi satu string pada Flow Block Operator Concatenate.
    pageDecoration:
      tree:
        priority: 0
---
# Concatenate Operator Block

>**note** Concatenate Block merupakan salah satu Flow Block kelompok String pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Concatenate Block adalah Flow Block Operator yang menghubungkan dua [[Docs/Tipe Data/String]] input menjadi satu String. Block ini tidak dapat menghasilkan error: bila salah satu input dibiarkan kosong, hasilnya adalah input yang lain.

![[Docs/Modul Logic/Flow/Flow Block/Operator/String/concatenate-block-flow.png|Concatenate Block pada Blueprint Flow]]
## Input dan Output

Concatenate Block memiliki 2 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|String]] (pertama) | [[Docs/Tipe Data/String]] | String yang menjadi bagian awal hasil. |
| [[^input|String]] (kedua) | [[Docs/Tipe Data/String]] | String yang ditambahkan setelah String pertama. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Result]] | [[Docs/Tipe Data/String]] | Hasil gabungan kedua String. Aliran diteruskan setiap kali block dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Concatenate Block menerima dua [[^input|String]].
2. Block menyambung String pertama diikuti String kedua.
3. Bila salah satu String kosong, hasilnya adalah String yang lain.
4. Hasilnya dikeluarkan lewat [[^output|Result]].

## Contoh Penggunaan

| String (pertama) | String (kedua) | Result | Status |
| ---------------- | -------------- | ------ | ------ |
| [[^value/string|PSN-]] | [[^value/string|001]] | [[^value/string|PSN-001]] | [[^flowstate/Succeed]] |
| [[^value/empty]] | [[^value/string|001]] | [[^value/string|001]] | [[^flowstate/Succeed]] |
| [[^value/string|PSN-]] | [[^value/empty]] | [[^value/string|PSN-]] | [[^flowstate/Succeed]] |
| [[^value/empty]] | [[^value/empty]] | [[^value/empty]] | [[^flowstate/Succeed]] |

## Praktik Terbaik

- Untuk menggabungkan **lebih dari dua String**, hubungkan [[^output|Result]] ke input String pada Concatenate Block berikutnya, atau gunakan [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode|Implode Operator Block]] bila datanya berupa Array.
- Cantumkan **pemisah** (misalnya spasi atau tanda hubung) sebagai bagian dari salah satu String karena block ini tidak menambahkan pemisah sendiri.
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Passer|Passer Block]] bila penyusunan hasil (misalnya kode seri) harus menunggu beberapa aliran selesai terlebih dahulu.

## Batasan dan Catatan

- Concatenate Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Block ini hanya menerima dua input. Penggabungan lebih banyak String dilakukan dengan merangkai block.
- Block ini tidak menghasilkan status [[^flowstate/Error]] maupun [[^flowstate/Fatal Error]] karena input kosong tetap menghasilkan output yang valid.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Implode|Implode Operator Block]]
- [[Docs/Tipe Data/String]]