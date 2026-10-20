---
    status: release
    title: "Template Kartu"
    description: Cara mengatur template kartu Gallery, yaitu Column yang tampil pada Header, Body, dan Footer beserta Styling-nya.
    pageDecoration:
      tree:
        priority: -2
    tags:
      draft
---
# Mengatur Templat Kartu

>**note** Bagian dari Gallery
> Template Kartu adalah pengaturan tampilan kartu pada komponen [[Docs/Modul Interface/Gallery/Apa itu Gallery|Gallery]] di modul [[Docs/Modul Interface/Pengenalan|Interface]].

Template Kartu menentukan [[Docs/Tipe Data/Column]] mana dari [[Docs/Tipe Data/Table]] sumber yang tampil pada kartu, di posisi mana, dan dengan desain apa. Setiap [[Docs/Tipe Data/Row]] pada Table tampil sebagai satu kartu, dan semua kartu di Gallery mengikuti template yang sama.

Dengan template, Anda dapat menonjolkan gambar atau konten yang paling penting dari setiap data, lalu menyesuaikan desainnya melalui [[Docs/Styling/Styling Class|Styling]].

## Konsep Utama

| Istilah | Penjelasan |
| ------- | ---------- |
| [[#Bagian Template Kartu\|Header]] | Bagian paling atas kartu. Column tersusun mendatar dari kiri ke kanan. |
| [[#Bagian Template Kartu\|Body]] | Bagian isi kartu. Column tersusun menurun dari atas ke bawah. |
| [[#Bagian Template Kartu\|Footer]] | Bagian paling bawah kartu. Column tersusun mendatar dari kiri ke kanan. |
| [[Docs/Tipe Data/Column]] | Kolom Table sumber yang dipilih untuk tampil pada kartu. |
| [[Docs/Styling/Styling Class\|Styling]] | Nama class yang menyesuaikan desain sebuah Column pada kartu. |
| [[#Mengubah Urutan Column\|Urutan]] | Posisi Column dalam sebuah bagian, yang dapat diubah dengan *drag and drop*. |
| [[#Template Kosong]] | Kondisi awal Gallery sebelum ada Column pada template. |

## Membuka Template Kartu

1. Buka halaman kerja [[Docs/Modul Interface/Gallery/Apa itu Gallery|Gallery]]
2. Klik [[^button/setting|Column]]

Modal [[^field|Setup Gallery Template]] terbuka.

![[Docs/Modul Interface/Gallery/gallery-modal.png]]

Setiap bagian memiliki tombol tambah ([[^button/add|Add Header Column]], [[^button/add|Add Body Column]], [[^button/add|Add Footer Column]]) dan tabel dengan kolom berikut:

| Kolom | Fungsi |
| ----- | ------ |
| [[^field\|No.]] | Nomor urutan Column pada bagian tersebut. |
| [[^field\|Column]] | Column dari Table sumber yang tampil pada kartu. |
| [[^field\|Styling]] | Nama class untuk menyesuaikan desain Column. |
| [[^field\|Action]] | Berisi tombol [[^button/delete\|Delete]] untuk menghapus baris dari template. |

Bagian yang belum memiliki Column menampilkan teks [[^field|No Column]].

>**note** Izin untuk mengubah template
> Mengubah template memerlukan izin Data Access di [[Docs/Modul Developer/Workspace/Data Access|Workspace]]. Tanpa izin tersebut, Anda tidak dapat menyimpan perubahan template.

## Bagian Template Kartu

Kartu memiliki tiga bagian. Column yang Anda isi tampil sesuai posisi bagiannya.

| Bagian | Posisi pada kartu | Tata letak | Urutan Column |
| ------ | ----------------- | ---------- | ------------- |
| [[^field\|Header]] | Paling atas | Mendatar (*flex-row*) | Dari kiri ke kanan |
| [[^field\|Body]] | Di antara [[^field\|Header]] dan [[^field\|Footer]] | Menurun (*flex-col*) | Dari atas ke bawah |
| [[^field\|Footer]] | Paling bawah | Mendatar (*flex-row*) | Dari kiri ke kanan |

Urutan pertama hingga terakhir pada daftar di modal mengikuti arah pada tabel di atas.

## Menyusun Template Kartu

### Menambahkan Column

1. Klik [[^button/add|Add Header Column]], [[^button/add|Add Body Column]], atau [[^button/add|Add Footer Column]] sesuai bagian yang diinginkan
2. Baris baru muncul dengan [[^field|Column]] dan [[^field|Styling]] yang masih kosong
3. Pilih [[Docs/Tipe Data/Column]] pada [[^field|Column]]
4. Isi [[^field|Styling]] jika dibutuhkan
5. Klik [[^button|Update]]

Pilihan [[^field|Column]] hanya berisi Column dari Table sumber Gallery. Satu Column dapat dipakai berkali-kali. Semua format data ditampilkan sebaik mungkin pada kartu, termasuk gambar.

Anda dapat klik [[^button|Cancel]] untuk membatalkan perubahan template. Setelah [[^button|Update]], kartu di Gallery menampilkan template terbaru.

### Mengisi Styling

[[^field|Styling]] berisi nama class styling untuk menyesuaikan desain Column, misalnya perataan teks atau ketebalan huruf. Anda dapat mengisi beberapa class sekaligus dengan memisahkannya menggunakan spasi, misalnya `text-right font-semibold`. Daftar class beserta contoh yang benar ada di [[Docs/Styling/Styling Class]].

### Mengubah Urutan Column

1. *Drag* baris Column yang ingin dipindahkan
2. *Drop* pada posisi yang diinginkan
3. Klik [[^button|Update]]

### Menghapus Column dari Template

1. Klik [[^button/delete|Delete]] pada kolom [[^field|Action]] di baris yang ingin dihapus
2. Klik [[^button|Update]]

Menghapus baris hanya menghapus Column dari template. Column dan data di Table sumber tidak terhapus.

## Template Kosong

Saat Gallery pertama kali dibuat, template masih kosong dan setiap bagian menampilkan [[^field|No Column]]. Pada kondisi ini, kartu menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]] dari Table, yang biasanya berformat [[Docs/Format Data/String/Short Text]]. Setelah Anda menambahkan Column ke template, kartu menampilkan Column sesuai template tersebut.

## Praktik Terbaik

- **Letakkan Column pengenal**, seperti nama atau judul, di [[^field|Header]], konten visual seperti gambar di [[^field|Body]], dan informasi pendukung di [[^field|Footer]].
- **Manfaatkan Column yang bisa dipakai berkali-kali** untuk menampilkan nilai yang sama pada bagian berbeda dengan [[^field|Styling]] yang berbeda.
- **Gunakan [[^field|Styling]] secukupnya** dan rujuk [[Docs/Styling/Styling Class]] agar nama class sudah benar.
- **Periksa kartu di halaman kerja** setelah klik [[^button|Update]] untuk memastikan susunan dan urutan sesuai harapan.
- **Pastikan Anda memiliki izin Data Access** di [[Docs/Modul Developer/Workspace/Data Access|Workspace]] sebelum mengubah template.

## Batasan dan Catatan

- [[^field|Column]] hanya dapat dipilih dari Column Table sumber Gallery.
- Mengubah template memerlukan izin Data Access di [[Docs/Modul Developer/Workspace/Data Access|Workspace]].
- Template berlaku untuk semua kartu di Gallery yang sama.
- Perubahan template baru tersimpan setelah klik [[^button|Update]], sedangkan [[^button|Cancel]] membatalkannya.
- [[^button/delete|Delete]] hanya menghapus Column dari template, bukan dari Table sumber.
- Template kosong menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]], bukan seluruh Column.

## TL:DR

- Template Kartu mengatur Column yang tampil pada kartu [[Docs/Modul Interface/Gallery/Apa itu Gallery|Gallery]] melalui modal [[^field|Setup Gallery Template]], yang dibuka dengan [[^button/setting|Column]].
- Kartu terdiri dari [[^field|Header]] (mendatar, kiri ke kanan), [[^field|Body]] (menurun, atas ke bawah), dan [[^field|Footer]] (mendatar, kiri ke kanan).
- Tambahkan Column dengan [[^button/add|Add Header Column]], [[^button/add|Add Body Column]], atau [[^button/add|Add Footer Column]], lalu pilih [[^field|Column]] dari Table sumber dan isi [[^field|Styling]].
- Urutan Column dapat diubah dengan *drag and drop*, dan baris dihapus dengan [[^button/delete|Delete]] pada [[^field|Action]].
- Klik [[^button|Update]] untuk menyimpan. Izin Data Access di [[Docs/Modul Developer/Workspace/Data Access|Workspace]] diperlukan.
- Template kosong membuat kartu hanya menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]].

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Column apa saja yang dapat dipilih pada template?**
> Hanya Column dari Table sumber Gallery. Satu Column dapat dipakai berkali-kali.
> **Bagaimana mengisi lebih dari satu class pada Styling?**
> Pisahkan setiap class dengan spasi, misalnya `text-right font-semibold`. Contoh class yang benar ada di [[Docs/Styling/Styling Class]].
> **Apakah menghapus baris template menghapus data?**
> Tidak. [[^button/delete|Delete]] hanya menghapus Column dari template. Column dan data di Table sumber tetap ada.
> **Mengapa saya tidak bisa menyimpan perubahan template?**
> Mengubah template memerlukan izin Data Access di [[Docs/Modul Developer/Workspace/Data Access|Workspace]]. Hubungi pengelola Workspace Anda untuk meminta izin tersebut.
> **Apa yang tampil pada kartu jika template kosong?**
> Kartu menampilkan [[Docs/Modul Data/Table/Apa itu Table#Membuat Table|Alias]] dari Table, yang biasanya berformat [[Docs/Format Data/String/Short Text]].
