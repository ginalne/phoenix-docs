---
    status: draft
    title: Add Variable
    description: Flow Block untuk menambahkan Variable Data baru dari dalam Flow.
    pageDecoration:
      icon: plus
      tree:
        priority: 1
---
# Add Variable

>**note** Add Variable merupakan salah satu Flow Block pada kelompok [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix.

Add Variable adalah [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] untuk menambahkan [[Docs/Modul Data/Variable/Apa itu Variable|Variable Data]] baru dari dalam Flow, tanpa membuka halaman kerja [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]. Block ini memiliki tiga input di sisi kiri dan dua output di sisi kanan.

![[Docs/Modul Logic/Flow/Flow Block/Data Variable/add-variable-block-flow.png|Flow Block Add Variable dengan tiga input dan dua output]]
## Input dan Output

Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]].

### Input

| Input | Tipe Data | Fungsi |
| ----- | --------- | ------ |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Variable Data yang akan dibuat. Name harus unik karena menjadi alias untuk merujuk Variable Data dari komponen Logic. Name membedakan huruf besar dan kecil serta boleh memuat karakter simbol. Spasi, enter, dan karakter tak terlihat lain di awal dan akhir dihapus saat Name disimpan. |
| [[^field|Value]] | Mengikuti tipe data yang Anda pilih. Awalnya tampil [[^field|N/A Type]]. | Nilai awal Variable Data. Tipe data input ini ditentukan lewat [[#Menentukan Tipe Data Value]]. |
| [[^field|Description]] | [[Docs/Tipe Data/Text]] | Keterangan tentang kegunaan Variable Data. |

### Output

| Output | Tipe Data | Fungsi |
| ------ | --------- | ------ |
| [[^output|New Variable]] | [[Docs/Tipe Data/Variable]] | Variable Data yang berhasil dibuat. Tidak meneruskan aliran bila terjadi konflik nama dengan variable yang sudah ada. |
| [[^output|Name Conflict]] | [[Docs/Tipe Data/Boolean]] | Bernilai [[^value/boolean/true]] bila [[^field|Name]] sudah dipakai Variable Data lain. Tidak meneruskan aliran bila Variable Data berhasil dibuat. |

### Menentukan Tipe Data Value

Input [[^field|Value]] pada block yang baru ditambahkan menampilkan teks merah [[^field|N/A Type]]. Teks ini berarti tipe data input belum didefinisikan. Tentukan tipe datanya dengan langkah berikut:

1. Klik kanan pada input [[^field|Value]].
2. Pilih [[^field|Change Type]].
3. Pilih tipe data yang sesuai dengan nilai yang akan disimpan. Semua tipe data yang tersedia di Phoenix dapat dipilih, misalnya [[Docs/Tipe Data/Number]] atau [[Docs/Tipe Data/String]].

>**note** Tipe data Value menentukan Type Variable Data
> Tipe data yang Anda pilih pada [[^field|Value]] menjadi Type dari Variable Data yang dibuat. Tipe ini juga menentukan tipe data output block lain yang membaca Variable Data tersebut, seperti [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]].

## Cara Kerja

1. Block menerima [[^field|Name]], [[^field|Value]], dan [[^field|Description]].
2. Block memeriksa apakah [[^field|Name]] sudah dipakai Variable Data lain.
3. Jika belum dipakai, Variable Data baru dibuat dan dikirim lewat [[^output|New Variable]], sedangkan [[^output|Name Conflict]] bernilai [[^value/boolean/false]].
4. Jika sudah dipakai, tidak ada Variable Data yang dibuat. [[^output|New Variable]] bernilai [[^value/empty]] dan [[^output|Name Conflict]] bernilai [[^value/boolean/true]].

## Contoh Penggunaan

| Kondisi | [[^output|New Variable]] | [[^output|Name Conflict]] |
| ------- | ------------------------ | ------------------------- |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] dan belum dipakai Variable Data lain | Variable Data `batas_stok_minimum` yang baru dibuat | [[^value/boolean/false]] |
| [[^field|Name]] berisi [[^value/string|batas_stok_minimum]] dan sudah dipakai Variable Data lain | [[^value/empty]] | [[^value/boolean/true]] |

Hubungkan [[^output|New Variable]] ke [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Value|Variable Value Block]] bila Anda ingin langsung memakai nilai awalnya pada block berikutnya. Hubungkan [[^output|Name Conflict]] ke block yang menangani kegagalan, misalnya [[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]].

## Praktik Terbaik

- **Tentukan tipe data [[^field|Value]] lebih dulu.** Bila [[^field|Value]] masih [[^field|N/A Type]], Variable Data tetap dibuat dan tersimpan dengan tipe data yang belum didefinisikan.
- **Periksa [[^output|Name Conflict]] di alur lanjutan.** Output ini memberi tahu Anda bahwa Variable Data tidak dibuat, sehingga alur tidak berlanjut dengan [[^output|New Variable]] yang [[^value/empty]].
- **Cek keberadaan Name dengan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Getter|Variable Getter Block]]** bila Anda ingin memutuskan sendiri apa yang dilakukan ketika Variable Data sudah ada.
- **Gunakan Name yang konsisten**, karena Name menjadi alias yang dipakai komponen Logic untuk merujuk Variable Data.

## Batasan dan Catatan

- Add Variable tidak menimpa Variable Data yang sudah ada. Untuk mengubah nilainya, gunakan [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Variable Setter|Variable Setter Block]].
- [[^field|Name]] yang kosong menyebabkan error, dan Variable Data tidak dibuat. Error ini dilaporkan di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]].
- Pencocokan [[^field|Name]] membedakan huruf besar dan kecil, sehingga [[^value/string|batas_stok_minimum]] dan [[^value/string|Batas_Stok_Minimum]] dianggap dua Name yang berbeda.
- Add Variable adalah block non-Event, sehingga tunduk pada [[Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi|Syarat Flow Block Diproses]].
- [[Docs/Modul Logic/Flow/Flow Block/Event/Variable Event|Variable Event Block]] hanya memiliki event [[^value/string|update]] dan [[^value/string|delete]], sehingga penambahan Variable Data tidak memicu Variable Event.

## Lihat Juga

- [[Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan|Flow Block Data Variable]]
- [[Docs/Modul Data/Variable/Apa itu Variable|Variable]]
- [[Docs/Tipe Data/Variable]]

