---
status: draft
title: Variable Setter
description: Flow Block untuk memperbarui Value pada Variable Data.
---
# Variable Setter

>**note** Variable Setter merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Variable Setter adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk memperbarui [[^field|Value]] pada [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] dari dalam [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]. Dengan block ini, nilai yang menjadi sumber kebenaran dapat berubah otomatis tanpa Anda membuka halaman kerja [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]. Block ini memiliki dua input di sisi kiri dan satu output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/variable-setter-block-flow.png|Flow Block Variable Setter dengan dua input dan satu output]]
## Input dan Output

Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang akan diperbarui. Isi dengan Variable Data atau hubungkan dari output block lain, misalnya [[^output|Variable]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]. |
| [[^field|New Value]] | Mengikuti tipe data yang Anda pilih. Awalnya tampil [[^field|N/A Type]]. | Nilai baru yang akan disimpan ke [[^field|Value]] Variable Data. Tipe data yang dipilih menjadi Type baru Variable Data dan ditentukan lewat [[#Menentukan Tipe Data New Value]]. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|Pass]] | [[Docs/Tipe Data/Variable]] | Variable Data yang diinput lewat [[^field|Variable]], diteruskan apa adanya agar dapat dipakai block berikutnya. |

[[^output|Pass]] meneruskan aliran setelah [[^field|Value]] berhasil diperbarui. Bila [[^field|Variable]] dibiarkan kosong, block menghasilkan error dan [[^output|Pass]] tidak meneruskan aliran, sehingga block yang terhubung tidak dieksekusi. Lihat [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]].

### Menentukan Tipe Data New Value

Input [[^field|New Value]] pada block yang baru ditambahkan menampilkan teks merah [[^field|N/A Type]], sama seperti [[^field|Value]] pada [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Add Variable|Add Variable Block]]. Teks ini berarti tipe data input belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|New Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan nilai baru. Semua tipe data yang tersedia di Phoenix dapat dipilih.

## Cara Kerja

1. Block menerima Variable Data dari [[^field|Variable]] dan nilai dari [[^field|New Value]].
2. Block mengganti [[^field|Value]] Variable Data dengan [[^field|New Value]]. [[^field|Type]] Variable Data ikut mengikuti tipe data [[^field|New Value]].
3. Block meneruskan Variable Data yang sama lewat [[^output|Pass]].

Hanya [[^field|Value]] dan [[^field|Type]] yang berubah. [[^field|Name]] dan [[^field|Description]] Variable Data tetap sama.

>**note** Perubahan oleh Flow tidak memicu Flow kembali
> Pembaruan lewat Variable Setter tidak memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] dengan event [[^value/string|update]], sehingga tidak ada Flow yang berjalan karena pembaruan ini.

## Contoh Penggunaan

| Kondisi | Value Variable Data | [[^output|Pass]] | Status |
| ------- | ------------------- | ---------------- | ------ |
| [[^field|Variable]] berisi Variable Data [[^value/string|batas_stok_minimum]] bertipe [[Docs/Tipe Data/Number]] dengan nilai [[^value/number|50]], dan [[^field|New Value]] berisi [[^value/number|100]] bertipe [[Docs/Tipe Data/Number]] | Value berubah menjadi [[^value/number|100]] | Variable Data `batas_stok_minimum` | [[^flowstate/Succeed]] |
| [[^field|Variable]] berisi Variable Data [[^value/string|batas_stok_minimum]] bertipe [[Docs/Tipe Data/Number]], dan [[^field|New Value]] berisi [[^value/string|aktif]] bertipe [[Docs/Tipe Data/String]] | Value berubah menjadi [[^value/string|aktif]], Type berubah menjadi [[Docs/Tipe Data/String]] | Variable Data `batas_stok_minimum` | [[^flowstate/Succeed]] |
| [[^field|Variable]] dibiarkan kosong | - | - | [[^flowstate/Fatal Error]] |

Hubungkan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]] ke [[^field|Variable]] dan hasil perhitungan, misalnya dari [[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]], ke [[^field|New Value]] untuk membuat penghitung yang bertambah setiap Flow berjalan.

Status [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]].

## Praktik Terbaik

- **Tentukan tipe data [[^field|New Value]] dengan benar.** Tipe data yang Anda pilih menjadi Type Variable Data setelah diperbarui.
- **Ambil Variable Data dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** agar Anda dapat menangani Variable Data yang tidak ditemukan sebelum memperbarui nilainya.
- **Gunakan [[^output|Pass]]** untuk melanjutkan rangkaian block Variable, misalnya ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]], agar block berikutnya membaca Variable Data yang sama.

## Batasan dan Catatan

- Variable Setter hanya mengubah Variable Data yang sudah ada. Untuk membuat Variable Data baru, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Add Variable|Add Variable Block]].
- [[^field|Variable]] yang dibiarkan kosong menyebabkan error yang dilaporkan di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].
- Satu eksekusi memperbarui satu Variable Data.
- Variable Setter adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- Anggota yang tidak memiliki akses ke komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tetap dapat mengubah Value lewat Flow.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

<!--
  * [TODO] Konfirmasi dampak New Value pada Type: jawaban Anda menyebut "New Value juga memberikan new type", sehingga saya tulis Type Variable Data ikut berubah mengikuti tipe data New Value. Namun kalimat sebelumnya ("hanya Value yang berubah, Name, Type, dan Description tetap sama") Anda tandai sudah betul. Mohon pastikan mana yang berlaku.
-->