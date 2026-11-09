---
status: draft
title: Pad Left Operator Block
description: Menambahkan Pad String di sebelah kiri String sampai mencapai panjang tertentu pada Flow Block Operator Pad Left.
---

# Pad Left Operator Block

>**note** Pad Left Block merupakan salah satu Flow Block kelompok String pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Pad Left Block adalah Flow Block Operator yang menambahkan [[^input|Pad String]] di sebelah kiri [[^input|String]] sampai panjang String sesuai dengan [[^input|Length]]. Block ini berguna untuk menyusun nomor atau kode dengan panjang tetap, misalnya nomor urut yang diawali angka nol.

![[Docs/Modul Logic/Flow/Flow Block/Operator/String/pad-left-block-flow.png|Pad Left Block pada Blueprint Flow]]

<!--
  * [DONE] Penempatan gambar: potong dari screenshot Operator, simpan sebagai `pad-left-block-flow.png` di folder yang sama dengan halaman ini.
  * [TODO] Perilaku belum diberikan penulis, mohon konfirmasi: (a) Length kosong menghasilkan Fatal Error atau dianggap 0, (b) hasil bila panjang String sudah sama atau lebih dari Length, (c) hasil bila Pad String terdiri dari lebih dari satu karakter dan tidak habis dibagi selisih panjang.
-->

## Input dan Output

Pad Left Block memiliki 3 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|String]] | [[Docs/Tipe Data/String]] | String yang akan ditambahkan di sebelah kirinya. Tidak boleh kosong. |
| [[^input|Length]] | [[Docs/Tipe Data/Number]] | Panjang String yang diinginkan setelah penambahan. |
| [[^input|Pad String]] | [[Docs/Tipe Data/String]] | String penambah yang dipakai sampai panjang tercapai. Tidak boleh kosong. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Result]] | [[Docs/Tipe Data/String]] | String hasil penambahan. Aliran diteruskan setiap kali block berhasil dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Pad Left Block menerima [[^input|String]], [[^input|Length]], dan [[^input|Pad String]].
2. Block menambahkan Pad String di sebelah kiri String sampai panjangnya sesuai dengan Length.
3. Hasilnya dikeluarkan lewat [[^output|Result]].

## Contoh Penggunaan

| String | Length | Pad String | Result | Status |
| ------ | ------ | ---------- | ------ | ------ |
| [[^value/string|42]] | [[^value/number|5]] | [[^value/string|0]] | [[^value/string|00042]] | [[^flowstate|Succeed]] |
| [[^value/string|AB]] | [[^value/number|5]] | [[^value/string|-]] | [[^value/string|---AB]] | [[^flowstate|Succeed]] |
| [[^value/empty]] | [[^value/number|5]] | [[^value/string|0]] | - | [[^flowstate|Fatal Error]] |
| [[^value/string|42]] | [[^value/number|5]] | [[^value/empty]] | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Pastikan **String** dan **Pad String** selalu terisi, misalnya dengan menghubungkannya dari block yang pasti menghasilkan nilai.
- Gabungkan dengan [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]] dan [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]] untuk menyusun kode seri dengan nomor urut berpanjang tetap.
- Gunakan [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right|Pad Right Operator Block]] bila penambahan perlu dilakukan di sebelah kanan.

## Batasan dan Catatan

- Pad Left Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|String]] atau [[^input|Pad String]] yang dibiarkan kosong menghasilkan status [[^flowstate|Fatal Error]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Pad Right|Pad Right Operator Block]]
- [[Docs/Tipe Data/String]]