---
    status: release
    title: "Antarmuka Enum"
    description: Penjelasan antarmuka di halaman kerja komponen Enum
    pageDecoration:
      tree:
        priority: 0.5
---
# Antarmuka Enum

![[Docs/Modul Data/Enum/halaman-kerja-enum.png]]

Halaman kerja Enum terdiri dari bilah navigasi di bagian atas dan tabel data di bagian bawah.

### Bilah navigasi Enum terdiri dari:

| Tombol | Fungsi |
| --- | --- |
| Judul Enum ([[^field/enum|Pelayan]] di gambar) | Menampilkan ikon Enum dan [[^field|Header Name]]. |
| [[^button/edit|Edit]] | Mengubah atribut Enum (lihat [[#Mengubah Enum]]). |
| [[^button/merge|Merge]] | Menggabungkan data. Selengkapnya lihat [[Docs/Modul Data/Enum/Enum Data/Menggabungkan]]. |
| [[^button/event|Event]] | Menghubungkan [[Docs/Event/Apa itu Event|Event]] dari Enum. Selengkapnya lihat [[Docs/Modul Data/Enum/Mengotomasi]]. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan halaman kerja. |
| [[^field|Search Enum Data...]] | Mencari [[Docs/Tipe Data/EnumData]] di dalam Enum. |

### Membaca Tabel Data

| Kolom | Penjelasan |
| --- | --- |
| [[^field|Name]] | Nama [[Docs/Tipe Data/EnumData]]. Tidak boleh sama dengan [[Docs/Tipe Data/EnumData]] lain di dalam Enum yang sama. |
| [[^field|Description]] | Keterangan [[Docs/Tipe Data/EnumData]]. |
| [[^field|Value]] | Nilai [[Docs/Tipe Data/EnumData]]. Bentuknya mengikuti [[^field|Format]] pada konfigurasi Enum. Ikon di header kolom menunjukkan tipe data dari [[^field|Format]]. |
| [[^field|Selectable]] | Menentukan apakah [[Docs/Tipe Data/EnumData]] tampil sebagai pilihan pada field. Hanya berlaku untuk field. |
| [[^field|Action]] | Berisi tombol [[^button/save|Save]] dan [[^button/delete|Delete]] untuk baris tersebut. |

>**note** Tampilan [[^field|Value]] Mengikuti [[^field|Format]]
> Tampilan kolom [[^field|Value]] dapat berbeda untuk setiap [[^field|Format]]. Pada Format Password, misalnya, Value tersamarkan.

### Interaksi Antarmuka Enum

| Fungsi | Aksi |
| --- | --- |
| Menambah baris | Klik [[^button/add|Add Row]] pada bagian bawah tabel atau pada bilah di bawahnya. Keduanya memiliki fungsi yang sama. |
| Mengubah [[^field|Selectable]] | Klik toggle pada kolom [[^field|Selectable]]. |
| Berpindah halaman | Gunakan [[^button/left|Prev]], [[^button/right|Next]], atau isi nomor halaman lalu klik [[^button/empty|Go]]. |
| Membaca batas halaman | Teks "Show 50 of 1 items" menunjukkan batas 50 item per halaman dan jumlah item yang ada. |

