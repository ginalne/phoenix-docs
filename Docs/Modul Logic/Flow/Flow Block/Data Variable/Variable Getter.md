---
status: draft
title: Variable Getter
description: Flow Block untuk mengambil Variable Data berdasarkan Name.
---
# Variable Getter

>**note** Variable Getter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Variable Getter adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk mengambil [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] dengan mengisi Name. Block ini menjadi pintu masuk bagi block Variable lain yang membutuhkan Variable Data sebagai input. Block ini memiliki satu input di sisi kiri dan dua output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/variable-getter-block-flow.png|Flow Block Variable Getter dengan satu input dan dua output]]
## Input dan Output

Variable Getter memiliki satu input di sisi kiri dan dua output di sisi kanan. Block ini tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Alias Variable Data yang dicari. Isi harus sama persis dengan Name Variable Data, termasuk huruf besar dan kecil serta karakter simbol. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Variable]] | [[Docs/Tipe Data/Variable]] | Meneruskan aliran dengan Variable Data yang ditemukan. Tidak meneruskan aliran bila tidak ada Name yang cocok. |
| [[^output|Is Empty]] | [[Docs/Tipe Data/Boolean]] | Meneruskan aliran dengan nilai [[^value/boolean/true]] bila Variable Data tidak ditemukan. Tidak meneruskan aliran bila ditemukan. |

Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

## Cara Kerja

1. Block menerima [[^field|Name]].
2. Block mencari Variable Data yang Name-nya sama persis.
3. Jika cocok, aliran diteruskan lewat [[^output|Variable]] dengan Variable Data yang ditemukan. [[^output|Is Empty]] tidak meneruskan aliran.
4. Jika tidak cocok, aliran diteruskan lewat [[^output|Is Empty]] dengan nilai [[^value/boolean/true]]. [[^output|Variable]] tidak meneruskan aliran.

Name Variable Data disimpan tanpa spasi, enter, atau karakter tak terlihat lain di awal dan akhir. Karena itu, tulis [[^field|Name]] tanpa karakter tersebut di awal dan akhir.

Input [[^field|Variable]] pada block lain berupa pilihan tetap. Gunakan Variable Getter bila Name Variable Data ditentukan saat Flow berjalan, misalnya berasal dari output block lain, atau bila Anda perlu menangani Variable Data yang tidak ditemukan. Variable Getter tidak dapat menimbulkan error. Bila Name tidak cocok, hasilnya diberitahukan lewat [[^output|Is Empty]].

## Contoh Penggunaan

| Kondisi | [[^output|Variable]] | [[^output|Is Empty]] | Status |
| ------- | -------------------- | -------------------- | ------ |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] dan ada Variable Data dengan Name yang sama persis | Variable Data `batas_stok_minimum` | - | [[^flowstate/Succeed]] |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] tetapi tidak ada Variable Data dengan Name tersebut | - | [[^value/boolean/true]] | [[^flowstate/Error]] |
| [[^field|Name]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] |

Hubungkan [[^output|Variable]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] untuk membaca nilainya, ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]] untuk mengubahnya, atau ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Delete Variable|Delete Variable Block]] untuk menghapusnya. Hubungkan [[^output|Is Empty]] ke block yang menangani kasus Variable Data tidak ditemukan. Block tersebut hanya dieksekusi bila Variable Data tidak ditemukan, sedangkan block yang terhubung ke [[^output|Variable]] hanya dieksekusi bila Variable Data ditemukan.

Status [[^flowstate/Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Pisahkan alur berdasarkan output.** Hubungkan block lanjutan ke [[^output|Variable]] untuk kasus ditemukan dan block penanganan ke [[^output|Is Empty]] untuk kasus tidak ditemukan. Masing-masing hanya dieksekusi pada kasusnya.
- **Tulis [[^field|Name]] persis seperti di komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]**, termasuk huruf besar dan kecil serta tanda baca.
- **Gunakan Variable Getter sebagai awal rangkaian block Variable** agar penanganan Variable Data yang tidak ditemukan cukup ditulis satu kali.

## Batasan dan Catatan

- Variable Getter hanya mengambil Variable Data dan tidak mengubahnya.
- Pencocokan [[^field|Name]] membedakan huruf besar dan kecil serta menerima karakter simbol, sehingga Name yang hanya mirip tidak dianggap cocok.
- Variable Getter adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Anggota yang tidak memiliki akses ke komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tetap dapat memakai Variable Data lewat Flow, tetapi tidak dapat melihat Value-nya di halaman kerja.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]
