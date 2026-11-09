---
status: draft
title: Assign Operator Block
description: Menambahkan satu atribut pada Object dengan Key dan Value pada Flow Block Operator Assign.
---

# Assign Operator Block

>**note** Assign Block merupakan salah satu Flow Block kelompok Object pada kategori [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Assign Block adalah Flow Block Operator yang menambahkan atribut pada [[Docs/Tipe Data/Object]]. [[^input|Key]] menjadi nama atribut dan [[^input|Value]] menjadi isinya. Block ini hanya mengisi satu atribut pada setiap eksekusi, dan hasilnya dikeluarkan lewat [[^output|Object]].

![[Docs/Modul Logic/Flow/Flow Block/Operator/Object/assign-block-flow.png|Assign Block pada Blueprint Flow]]

<!--
  * [DONE] Penempatan gambar: potong dari screenshot Operator, simpan sebagai `assign-block-flow.png` di folder yang sama dengan halaman ini.
  * [DONE] Teks penulis "Fatal Erro" ditulis sebagai "Fatal Error".
  * [TODO] Konfirmasi: block ini tidak memiliki input Object. Draf mengasumsikan Object hasil dibentuk baru dari Key dan Value. Mohon jelaskan data sebelumnya apa yang ditimpa (sifat override) bila tidak ada Object masukan, misalnya apakah override terjadi pada eksekusi berikutnya atau bila Key menunjuk atribut yang sama pada Value bertipe Object.
-->

## Input dan Output

Assign Block memiliki 2 input di sisi kiri, 1 output di sisi kanan dan tidak memiliki Control. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Keterangan |
| ----- | --------- | ---------- |
| [[^input|Key]] | [[Docs/Tipe Data/String]] | Nama atribut yang diisi. Gunakan simbol `.` untuk mengisi atribut pada kedalaman tertentu. Tidak boleh kosong. |
| [[^input|Value]] | [[Docs/Tipe Data/Object]] atau [[Docs/Tipe Data/String]] | Isi atribut. Bawaannya bertipe Object dan tipenya dapat diganti ke String (lihat [[#Menentukan Tipe Data Value]]). Tidak boleh kosong. |

Key ditulis dengan simbol `.` untuk mengisi Object di kedalaman. Contohnya, Key [[^value/string|job.status.level]] mengisi atribut `job` ➜ `status` ➜ `level`.

### Output

| Output | Tipe Data | Keterangan |
| ------ | --------- | ---------- |
| [[^output|Object]] | [[Docs/Tipe Data/Object]] | Object hasil pengisian atribut. Aliran diteruskan setiap kali block berhasil dieksekusi. |

Selengkapnya lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

### Menentukan Tipe Data Value

1. Klik kanan pada input [[^input|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data [[Docs/Tipe Data/Object]] atau [[Docs/Tipe Data/String]].

## Cara Kerja

1. Assign Block menerima [[^input|Key]] dan [[^input|Value]].
2. Block mengisi atribut sesuai Key dengan Value. Bila Key memuat simbol `.`, atribut dibuat bertingkat sesuai kedalamannya.
3. Assign bersifat *override*: bila sebelumnya sudah ada data pada Key tersebut, data itu ditimpa.
4. Object hasilnya dikeluarkan lewat [[^output|Object]].

## Contoh Penggunaan

| Key | Value | Object | Status |
| --- | ----- | ------ | ------ |
| [[^value/string|nama]] | [[^value/string|Kopi]] | [[^value/object|{ "nama": "Kopi" }]] | [[^flowstate|Succeed]] |
| [[^value/string|job.status.level]] | [[^value/string|senior]] | [[^value/object|{ "job": { "status": { "level": "senior" } } }]] | [[^flowstate|Succeed]] |
| [[^value/string|status]] | [[^value/object|{ "aktif": true }]] | [[^value/object|{ "status": { "aktif": true } }]] | [[^flowstate|Succeed]] |
| [[^value/empty]] | [[^value/string|Kopi]] | - | [[^flowstate|Fatal Error]] |
| [[^value/string|nama]] | [[^value/empty]] | - | [[^flowstate|Fatal Error]] |

Status [[^flowstate|Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- Gunakan **simbol titik** pada Key untuk membentuk struktur bertingkat dalam satu block, tanpa perlu merangkai banyak block.
- Untuk mengisi **lebih dari satu atribut**, gunakan beberapa Assign Block lalu gabungkan hasilnya dengan [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge|Merge Operator Block]].

## Batasan dan Catatan

- Assign Block adalah Flow Block non-Event sehingga hanya diproses bila memenuhi [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Assign Block hanya mengisi satu atribut pada setiap eksekusi.
- [[^input|Key]] atau [[^input|Value]] yang dibiarkan kosong menghasilkan status [[^flowstate|Fatal Error]].
- Assign bersifat *override*, sehingga data sebelumnya pada Key yang sama akan ditimpa.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Operator/Pengenalan|Flow Block Operator]]
- [[Docs/Modul Logic/Flow/Flow Block/Operator/Object/Merge|Merge Operator Block]]
- [[Docs/Tipe Data/Object]]