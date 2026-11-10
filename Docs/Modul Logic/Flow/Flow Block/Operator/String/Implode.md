---
status: draft
title: Implode Operator Block
description: Menggabungkan String atau Array berisi String menjadi satu String dengan pemisah pada Flow Block Operator Implode.
---

# Implode Operator Block

>**note** Implode Block merupakan salah satu Flow Block kelompok String pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Implode Block adalah Flow Block Operator yang menggabungkan input bertipe [[Docs/Tipe Data/String]] atau [[Docs/Tipe Data/Array]] dengan isi String menjadi satu String, dengan [[^input|Separator]] sebagai pemisah di antara setiap isinya.

![[Docs/Modul Logic/Flow/Flow Block/Operator/String/implode-block-flow.png|Implode Block pada Blueprint Flow]]

<!--
  * [DONE] Penempatan gambar: potong dari screenshot Operator, simpan sebagai `implode-block-flow.png` di folder yang sama dengan halaman ini.
  * [TODO] Perilaku belum diberikan penulis, mohon konfirmasi: (a) Strings atau Separator kosong menghasilkan Fatal Error atau tidak, (b) hasil bila Strings bertipe String tunggal, (c) hasil bila Array hanya berisi satu String.
    Jawaban: Sudah benar
-->

## Input dan Output

Implode Block memiliki 2 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Strings]] | [[Docs/Tipe Data/String]] atau [[Docs/Tipe Data/Array]] berisi String | Data yang akan digabungkan. |
| [[^input|Separator]] | [[Docs/Tipe Data/String]] | Pemisah yang disisipkan di antara setiap isi Strings. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Result]] | [[Docs/Tipe Data/String]] | Hasil gabungan seluruh isi Strings. Aliran diteruskan setiap kali block berhasil dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Implode Block menerima [[^input|Strings]] dan [[^input|Separator]].
2. Block menyambung setiap isi Strings sesuai urutannya dan menyisipkan Separator di antara dua isi yang berurutan.
3. Hasilnya dikeluarkan lewat [[^output|Result]].

## Contoh Penggunaan

| Strings | Separator | Result | Status |
| ------- | --------- | ------ | ------ |
| `["merah", "hijau", "biru"]` | [[^value/string|/]] | [[^value/string|merah/hijau/biru]] | [[^flowstate|Succeed]] |
| `["merah", "hijau", "biru"]` | [[^value/string|-]] | [[^value/string|merah-hijau-biru]] | [[^flowstate|Succeed]] |

## Praktik Terbaik

- Gunakan **Implode** untuk menggabungkan banyak String sekaligus dan [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]] bila hanya menggabungkan dua String.
- Pilih **Separator** yang tidak muncul di dalam isi Strings agar hasil gabungan mudah dipisahkan kembali.

## Batasan dan Catatan

- Implode Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Isi Array pada [[^input|Strings]] harus bertipe [[Docs/Tipe Data/String]].

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/String/Concatenate|Concatenate Operator Block]]
- [[Docs/Tipe Data/Array]]