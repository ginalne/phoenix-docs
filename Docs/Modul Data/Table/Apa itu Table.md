---
    status: release
    title: "Apa itu Table?"
    description: Pengenalan komponen Table di modul Data Phoenix untuk menyimpan data transaksional maupun generik dalam Column, Row, dan TableData.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 18 16">
  <path d="M0 2a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2zm15 2h-4v3h4zm0 4h-4v3h4zm0 4h-4v3h3a1 1 0 0 0 1-1zm-5 3v-3H6v3zm-5 0v-3H1v2a1 1 0 0 0 1 1zm-4-4h4V8H1zm0-4h4V4H1zm5-3v3h4V4zm4 4H6v3h4z"/>
</svg>'
      tree:
        priority: 4
---
# Apa itu Table?

>**note** Table merupakan salah satu komponen dalam modul [[Docs/Modul Data/Pengenalan|Data]] di Phoenix.

Table adalah komponen penyimpan data yang dapat digunakan untuk menyimpan data secara kompleks, baik data transaksional maupun data generik.

Anda menyusun beberapa [[Docs/Tipe Data/Column|Column]] yang masing-masing memiliki format berbeda, lalu mengisi datanya melalui [[Docs/Tipe Data/Row|Row]]. Setiap Row memiliki [[Docs/Tipe Data/TableData|TableData]] sesuai kolom yang tersedia. [[Docs/Tipe Data/Expression|Expression]] juga dapat berfungsi langsung pada komponen ini.

## Mengapa Menggunakan Table?

- **Satu tempat untuk data kompleks.** Data transaksional dan data generik dapat disimpan dengan struktur yang sama.
- **Format sesuai jenis data.** Setiap Column memiliki format sendiri sehingga isian setiap kolom konsisten.
- **Mudah dikenali saat dipilih.** Alias menampilkan nilai kolom pilihan Anda pada field berformat Row, sehingga Row tidak hanya dikenali lewat angka ID.
- **Expression langsung berfungsi.** [[Docs/Tipe Data/Expression|Expression]] dapat digunakan langsung pada Table.
- **Siap terhubung ke komponen lain.** Fungsi [[^button/merge|Merge]], [[^button/publish|Publish]], dan [[^button/event|Event]] membuat data Table dapat digabungkan, dipublikasikan, dan dihubungkan ke logika otomasi.

## Konsep Utama

| Istilah                                                | Penjelasan                                                                                        |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| [[Docs/Tipe Data/Column|Column]]                       | Kolom pada Table. Setiap Column memiliki Name, Format, dan Description.                           |
| [[Docs/Tipe Data/Row|Row]]                             | Baris pada Table yang menampung satu rangkaian data.                                              |
| [[Docs/Tipe Data/TableData|TableData]]                 | Isi sel dari sebuah Row, mengikuti Column yang tersedia.                                          |
| [[Docs/Tipe Data/Expression]]               | Tipe Data untuk melakukan perhitungan dengan fungsi yang disediakan, Tipe Data ini dapat langsung digunakan pada komponen Table.                                       |
| [[Docs/Tipe Data/Column#Alias|Alias]]                  | Column pilihan yang nilainya tampil pada field berformat Row dengan pola `ID - Alias Value`.      |

## Cara Kerja

Penjelasan cara kerja Table View lihat selengkap nya di [[Docs/Modul Interface/Table View/Cara Kerja|Cara Kerja Table View]].

## Antarmuka

Penjelasan antarmuka Table View lihat selengkap nya di [[Docs/Modul Interface/Table View/Antarmuka|Antarmuka Table View]].

## Mengelola Tree

Berikut adalah halaman yang menjelaskan cara untuk mengelola Table:
1. [[Docs/Modul Data/Table/Membuat Baru]] Table dalam halaman kerja.
2. [[Docs/Modul Data/Table/Mengubah]] Atribut Table seperti [[^field|Name]], [[^field|Description]].
3. [[Docs/Modul Data/Table/Menghapus]] Table.
4. [[Docs/Modul Data/Table/Table Row/Pengenalan|Mengelola Baris]] seperti menambahkan, mengubah, menghapus atau menggabungkan [[Docs/Tipe Data/Row]].
5. [[Docs/Modul Data/Table/Mempublikasi]]: mengatur publikasi Table.
6. [[Docs/Modul Data/Table/Mengotomasi]]: menghubungkan Table dengan [[Docs/Event/Apa itu Event|Event]].

Anda juga dapat memperdalam tentang Tipe Data yang berhubungan dengan data yaitu: [[Docs/Tipe Data/Column]], [[Docs/Tipe Data/Row]], dan [[Docs/Tipe Data/TableData]].

## Praktik Terbaik

- **Rancang Column sebelum mengisi Row.** Tentukan Name dan Format setiap Column agar data konsisten sejak awal.
- **Pilih Format sesuai jenis data.** Format yang tepat membuat isian lebih rapi dan mudah diproses komponen lain.
- **Pilih Alias yang mudah dikenali.** Gunakan Column yang paling mewakili Row, misalnya nama, karena nilainya tampil pada field berformat Row.
- **Isi Description pada Column.** Penjelasan singkat membantu anggota lain memahami isi setiap Column.
- **Periksa dampaknya sebelum mengubah Column.** Perubahan Column pada Table yang sudah berisi Row dapat menghilangkan data.

## Batasan dan Catatan

- Table yang baru dibuat belum memiliki Row, dan minimal memiliki satu Column.
- Setiap Table harus memiliki satu Alias. Alias yang dipilih tampil pada field berformat Row dengan pola `ID - Alias Value`.
- ID dan Action adalah kolom tambahan pada halaman kerja, bukan Column yang Anda buat. ID terisi otomatis.
- Perubahan Column lewat [[^button/edit|Edit]] dapat menyebabkan data hilang. Phoenix menampilkan peringatan, dan Anda dapat melanjutkan dengan *force update*.
- Penggunaan [[^button/merge|Merge]], [[^button/event|Event]], dan [[^button/publish|Publish]] bergantung pada Function Access di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].
- Row yang dihapus tidak dapat dikembalikan.

## TL:DR

- Table adalah komponen di modul [[Docs/Modul Data/Pengenalan|Data]] untuk menyimpan data transaksional maupun generik.
- Table terdiri dari [[Docs/Tipe Data/Column|Column]], [[Docs/Tipe Data/Row|Row]], dan [[Docs/Tipe Data/TableData|TableData]].
- Saat membuat Table, Anda wajib memilih satu Alias dan membuat minimal satu Column.
- Halaman kerja menambahkan kolom ID di awal dan Action di akhir.
- Merge, Publish, dan Event memiliki halaman penjelasan masing-masing.
- Hati-hati saat mengubah Column dan saat menghapus Table atau Row karena data dapat hilang.
