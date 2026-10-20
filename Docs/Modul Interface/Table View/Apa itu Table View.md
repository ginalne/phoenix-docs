---
    status: release
    title: "Apa itu Table View?"
    description: Table View adalah komponen modul Interface untuk menampilkan data Table dalam satu atau lebih tampilan menggunakan Query.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" height="20" width="20" fill="#aaa" viewBox="0 -960 960 960">
    <path d="M312-96q-33 0-52.5-19.5T240-168v-480q0-33 19.5-52.5T312-720h480q33 0 52.5 19.5T864-648v480q0 33-19.5 52.5T792-96H312Zm0-72h204v-132H312v132Zm276 0h204v-132H588v132ZM96-240v-552.45q0-32.55 19.5-52.05t52.05-19.5H720v72H168v552H96Zm216-132h204v-132H312v132Zm276 0h204v-132H588v132ZM312-576h480v-72H312v72Z"/>
  </svg>
  '
      tree:
        priority: 4
---
# Apa itu Table View?

>**note** Table View merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Table View (atau TableView) adalah komponen antarmuka yang dapat digunakan untuk menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] menggunakan [[Docs/Tipe Data/Query|Query]].

Satu Table View dapat memiliki lebih dari satu Data. Setiap Data menampung satu Query, sebuah nama, dan konfigurasi tampilannya sendiri, sehingga Anda dapat menyajikan beberapa tampilan Table dalam satu halaman dengan kolom dan filter yang berbeda-beda. [[Docs/Tipe Data/Row]] tetap dapat ditambah, diubah, dan dihapus langsung dari tampilan, seperti pada Table.

## Mengapa Menggunakan Table View?

- **Banyak tampilan dalam satu halaman.** Tampilkan beberapa Data sekaligus, baik dari Table yang sama maupun dari Table yang berbeda.
- **Kolom yang dapat dikontrol.** Tampilkan hanya kolom yang dibutuhkan dengan [[Docs/Tipe Data/Query#Show dan Hide|Show/Hide]] di Query.
- **Data yang dapat difilter.** Tambahkan kondisi [[Docs/Tipe Data/Query#Where|Where]] di Query agar Data hanya memuat Row yang relevan.
- **Dapat langsung dikelola.** Tambah, ubah, dan hapus Row tanpa berpindah ke halaman Table.
- **Row baru tidak hilang.** Kolom yang menjadi syarat filter akan terisi otomatis saat Row ditambahkan, sehingga Row tetap relevan dengan kondisi Query-nya.

## Konsep Utama

| Istilah | Penjelasan |
| ------- | ---------- |
| [[Docs/Modul Interface/Table View/Table View Data|Data]] | Satu unit tampilan pada Table View yang menampung nama, konfigurasi tampilan dan [[Docs/Tipe Data/Query]]. Satu Table View dapat memiliki lebih dari satu Data. |
| [[Docs/Tipe Data/Query]] | Tipe data yang merumuskan data yang tampil pada setiap Table View Data. |
| [[Docs/Tipe Data/Query#Show dan Hide|Show/Hide]] | Pengaturan di [[Docs/Tipe Data/Query]] untuk menampilkan atau menyembunyikan kolom tertentu. |
| [[Docs/Tipe Data/Query#Filter|Filter]] | Kondisi di [[Docs/Tipe Data/Query]] untuk memfilter daftar yang tampil. |

## Cara Kerja

Penjelasan cara kerja Table View lihat selengkap nya di [[Docs/Modul Interface/Table View/Cara Kerja|Cara Kerja Table View]].

## Mengelola Table View

Berikut adalah halaman yang menjelaskan cara untuk mengelola Table View:
1. [[Docs/Modul Interface/Table View/Membuat Baru]] Table View dalam halaman kerja.
2. [[Docs/Modul Interface/Table View/Mengubah]] Atribut Table View seperti [[^field|Name]], [[^field|Description]], atau [[^field|Table - Column]].
3. [[Docs/Modul Interface/Table View/Menghapus]] Table View.
4. [[Docs/Modul Interface/Table View/Table View Data|Mengelola Data]] Table View seperti menambahkan, mengubah atau memperbarui Data.

## Antarmuka

Penjelasan antarmuka Table View lihat selengkap nya di [[Docs/Modul Interface/Table View/Antarmuka|Antarmuka Table View]].

## Praktik Terbaik

- **Beri nama Data sesuai filternya**, misalnya nama yang menjelaskan kondisi [[Docs/Tipe Data/Query#Filter|Filter]], agar pembaca langsung paham isi Data.
- **Tampilkan hanya kolom yang dibutuhkan** dengan [[Docs/Tipe Data/Query#Show or Hide|Show/Hide]] agar tabel mudah dibaca.
- **Selalu gunakan kaidah [[Docs/Tipe Data/Query#Table Output]]** pada [[Docs/Tipe Data/Query|Query]] agar Data tidak menampilkan [[^field|Query table output is not valid!]].
- **Pilih porsi layar sesuai kepentingan Data**: [[^value/radio|full]] untuk Data utama, [[^value/radio|half]] atau [[^value/radio|quarter]] untuk Data pendukung.
- **Atur hak akses di dua tempat.** Pastikan [[Docs/Modul Developer/Workspace/Data Access]] Table dan konfigurasi [[Docs/Modul Interface/Table View/TableViewData|Data]] sesuai dengan siapa yang boleh mengubah baris data.

## Batasan dan Catatan

- Setiap Data hanya menampung satu [[Docs/Tipe Data/Query|Query]], dan Query wajib memakai kaidah [[Docs/Tipe Data/Query#Output Table]].
- Table View hanya menampilkan data [[Docs/Modul Data/Table/Apa itu Table|Table]] dan tidak menyimpan data baris sendiri. Baris yang Anda tambah, ubah, atau hapus adalah data ril pada sumber.
- Menghapus baris dari Table View tidak dapat dikembalikan, sedangkan menghapus Data atau Table View tidak menghapus baris pada data sumber.
- Kolom yang menjadi syarat [[Docs/Tipe Data/Query#Filter|Filter]] akan terisi otomatis saat baris ditambahkan, walaupun kolom tersebut tidak ditampilkan oleh [[Docs/Tipe Data/Query#Show or Hide|Show/Hide]].
- Hak akses Table di Workspace selalu berlaku. Jika Workspace tidak mengizinkan pengelolaan data sumber maka tetap data tersebut tidak dapat diubah dari Table View meskipun konfigurasi Data mengizinkannya.
- Hak akses pengelolaan Data (ubah nama, Query, dan konfigurasi) diatur di [[Docs/Modul Developer/Workspace/Data Access|Data Access]] di komponen Table View, bukan di konfigurasi Data.
- Mengubah nilai kolom yang menjadi syarat [[Docs/Tipe Data/Query#Filter|Filter]] dapat membuat baris data tidak tampil lagi walaupun setelah [[^button/refresh|Refresh]].

## TL:DR

- [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] menampilkan data sumber seperti [[Docs/Modul Data/Table/Apa itu Table|Table]] menggunakan [[Docs/Tipe Data/Query|Query]], dan dapat memiliki lebih dari satu [[Docs/Modul Interface/Table View/TableViewData|Data]].
- Setiap Data menampung satu [[Docs/Tipe Data/Query]], nama, dan tampilan ([[^value/radio|full]], [[^value/radio|half]], atau [[^value/radio|quarter]]), dan dapat dilipat dengan klik.
- Atur kolom dengan [[Docs/Tipe Data/Query#Show dan Hide|Show/Hide]] dan kondisi dengan [[Docs/Tipe Data/Query#Filter|Filter]]; Query wajib memakai kaidah [[Docs/Tipe Data/Query#Table Output]].
- Baris dikelola seperti pada Table, dan kolom syarat [[Docs/Tipe Data/Query#Filter|Filter]] yang tidak tampil terisi otomatis agar baris tidak hilang setelah [[^button/refresh|Refresh]].
- Pengelolaan Data diatur di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]], sedangkan baris dan sel mengikuti konfigurasi Data serta hak akses sumber.
- Menghapus baris di Table View menghapusnya dari sumber, tetapi menghapus Data tidak.

