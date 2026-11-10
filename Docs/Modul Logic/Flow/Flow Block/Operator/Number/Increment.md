---
status: draft
title: Increment Operator Block
description: Menambahkan nilai Number dengan langkah yang ditentukan dan mengeluarkan hasilnya.
---

# Increment Operator Block

>**note** Increment Block merupakan salah satu Flow Block kelompok Number pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Increment Block adalah Flow Block Operator yang menambahkan [[^input|Data]] dengan langkah yang ditentukan pada [[^input|Adders]], lalu mengeluarkan hasilnya lewat [[^output|Result]]. Block ini berguna untuk menghitung nomor urut, penghitung, atau nilai yang bertambah pada setiap eksekusi Flow.

![[Docs/Modul Logic/Flow/Flow Block/Operator/Number/increment-block-flow.png|Increment Block pada Blueprint Flow]]

## Input dan Output

Increment Block memiliki 2 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Data]] | [[Docs/Tipe Data/Number]] | Nilai awal yang akan ditambahkan. |
| [[^input|Adders]] | [[Docs/Tipe Data/Number]] | Langkah yang ditambahkan pada Data. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Result]] | [[Docs/Tipe Data/Number]] | Hasil penjumlahan Data dengan Adders. Aliran diteruskan setiap kali block berhasil dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Increment Block menerima [[^input|Data]] dan [[^input|Adders]].
2. Block menambahkan Data dengan Adders.
3. Hasilnya dikeluarkan lewat [[^output|Result]] dan diteruskan ke block yang terhubung.

## Contoh Penggunaan

| Data | Adders | Result | Status |
| ---- | ------ | ------ | ------ |
| [[^value/number|10]] | [[^value/number|1]] | [[^value/number|11]] | [[^flowstate|Succeed]] |
| [[^value/number|100]] | [[^value/number|25]] | [[^value/number|125]] | [[^flowstate|Succeed]] |
| [[^value/empty]] | [[^value/number|1]] | - | [[^flowstate|Fatal Error]] |
| [[^value/number|10]] | [[^value/empty]] | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Ambil nilai penghitung dari **Variable Getter Block** dan simpan kembali hasilnya dengan **Variable Setter Block** agar nilainya bertambah di setiap eksekusi Flow. Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] dan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].
- Gabungkan [[^output|Result]] dengan [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Left|Pad Left Operator Block]] bila nomor urut perlu ditampilkan dengan panjang tetap.

## Batasan dan Catatan

- Increment Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Block ini tidak menyimpan hasilnya. Nilai hanya dikeluarkan lewat [[^output|Result]] pada eksekusi tersebut.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Tipe Data/Number]]
- [[Docs/Modul Logic/Flow/Flow Activity]]