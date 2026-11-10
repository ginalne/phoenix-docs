---
    status: release
    title: Pad Right Operator Block
    description: Menambahkan Pad String di sebelah kanan String sampai mencapai panjang tertentu pada Flow Block Operator Pad Right.
    pageDecoration:
      tree:
        priority: 0
---
# Pad Right Operator Block

>**note** Pad Right Block merupakan salah satu Flow Block kelompok String pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Pad Right Block adalah Flow Block Operator yang menambahkan [[^input|Pad String]] di sebelah kanan [[^input|String]] sampai panjang String sesuai dengan [[^input|Length]]. Block ini berguna untuk menyusun teks dengan panjang tetap, misalnya kode yang diakhiri tanda pengisi.

![[Docs/Modul Logic/Flow/Flow Block/Operator/String/pad-right-block-flow.png|Pad Right Block pada Blueprint Flow]]
## Input dan Output

Pad Right Block memiliki 3 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|String]] | [[Docs/Tipe Data/String]] | String yang akan ditambahkan di sebelah kanannya. Tidak boleh kosong. |
| [[^input|Length]] | [[Docs/Tipe Data/Number]] | Panjang String yang diinginkan setelah penambahan. |
| [[^input|Pad String]] | [[Docs/Tipe Data/String]] | String penambah yang dipakai sampai panjang tercapai. Tidak boleh kosong. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Result]] | [[Docs/Tipe Data/String]] | String hasil penambahan. Aliran diteruskan setiap kali block berhasil dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Pad Right Block menerima [[^input|String]], [[^input|Length]], dan [[^input|Pad String]].
2. Block menambahkan Pad String di sebelah kanan String sampai panjangnya sesuai dengan Length.
3. Hasilnya dikeluarkan lewat [[^output|Result]].

## Contoh Penggunaan

| String | Length | Pad String | Result | Status |
| ------ | ------ | ---------- | ------ | ------ |
| [[^value/string|AB]] | [[^value/number|5]] | [[^value/string|-]] | [[^value/string|AB---]] | [[^flowstate|Succeed]] |
| [[^value/string|42]] | [[^value/number|5]] | [[^value/string|0]] | [[^value/string|42000]] | [[^flowstate|Succeed]] |
| [[^value/empty]] | [[^value/number|5]] | [[^value/string|-]] | - | [[^flowstate|Fatal Error]] |
| [[^value/string|AB]] | [[^value/number|5]] | [[^value/empty]] | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Pastikan **String** dan **Pad String** selalu terisi, misalnya dengan menghubungkannya dari block yang pasti menghasilkan nilai.
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left|Pad Left Operator Block]] bila penambahan perlu dilakukan di sebelah kiri, misalnya untuk nomor yang diawali angka nol.

## Batasan dan Catatan

- Pad Right Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|String]] atau [[^input|Pad String]] yang dibiarkan kosong menghasilkan status [[^flowstate|Fatal Error]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left|Pad Left Operator Block]]
- [[Docs/Tipe Data/String]]