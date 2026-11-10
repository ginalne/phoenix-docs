---
status: draft
title: Merge Operator Block
description: Menggabungkan beberapa Object menjadi satu Object pada Flow Block Operator Merge.
---

# Merge Operator Block

>**note** Merge Block merupakan salah satu Flow Block kelompok Object pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Merge Block adalah Flow Block Operator yang menggabungkan [[^input|Objects]], yaitu input bertipe [[Docs/Tipe Data/Array]] dengan isi [[Docs/Tipe Data/Object]], menjadi satu Object lewat [[^output|Result]]. Data yang berada lebih akhir menimpa data sebelumnya hanya pada atribut yang sama persis, sehingga data yang saling melengkapi tidak saling menghapus.

![[Docs/Modul Logic/Flow/Flow Block/Operator/Object/merge-block-flow.png|Merge Block pada Blueprint Flow]]

<!--
  * [DONE] Penempatan gambar: potong dari screenshot Operator, simpan sebagai `merge-block-flow.png` di folder yang sama dengan halaman ini.
  * [TODO] Konfirmasi: hasil bila Objects berisi satu Object, dan bila Array kosong (selain input kosong).
    Jawaban: Sudah benar
-->

## Input dan Output

Merge Block memiliki 1 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Objects]] | [[Docs/Tipe Data/Array]] berisi [[Docs/Tipe Data/Object]] | Kumpulan Object yang akan digabungkan. Tidak boleh kosong. |

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Result]] | [[Docs/Tipe Data/Object]] | Object hasil penggabungan. Aliran diteruskan setiap kali block berhasil dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Merge Block menerima [[^input|Objects]].
2. Block menggabungkan Object sesuai urutannya, dimulai dari Object pertama.
3. Bila atribut yang sama dimiliki lebih dari satu Object, nilai dari Object yang lebih akhir menimpa nilai sebelumnya.
4. Bila Object saling mengisi atribut pada kedalaman tertentu, tidak ada data yang ditimpa dan seluruh atributnya digabung.
5. Hasilnya dikeluarkan lewat [[^output|Result]].

## Contoh Penggunaan

| Objects | Result | Status |
| ------- | ------ | ------ |
| `[{ "produk": "Kopi", "harga": 15000 }, { "harga": 18000, "stok": 20 }]` | [[^value/object|{ "produk": "Kopi", "harga": 18000, "stok": 20 }]] | [[^flowstate|Succeed]] |
| `[{ "job": { "judul": "staf" } }, { "job": { "level": "2" } }]` | [[^value/object|{ "job": { "judul": "staf", "level": "2" } }]] | [[^flowstate|Succeed]] |
| [[^value/empty]] | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Urutkan **Objects** dengan hati-hati: Object yang berada lebih akhir akan menimpa atribut yang sama pada Object sebelumnya, jadi letakkan data yang paling diutamakan di posisi terakhir.
- Gunakan Merge bersama [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign|Assign Operator Block]] untuk menyusun Object dari beberapa atribut.

## Batasan dan Catatan

- Merge Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[^input|Objects]] yang dibiarkan kosong menghasilkan status [[^flowstate|Fatal Error]].
- Penimpaan hanya terjadi pada atribut yang sama persis. Atribut yang berbeda pada kedalaman mana pun tetap dipertahankan.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Assign|Assign Operator Block]]
- [[Docs/Tipe Data/Object]]