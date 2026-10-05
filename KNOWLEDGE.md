---
name: phoenix-docs-knowledge
pageDecoration:
  icon: info
description: knowledge-base phoenix untuk AI Agent selama membuat dokumentasi phoenix.
---

## Workspace (Modul Developer)

- Workspace adalah komponen untuk mengatur ruang kerja pengembangan: komponen yang dapat dilihat, dikelola, dan diubah, serta **fungsi di dalamnya** (bukan "integrasi yang digunakan", sesuai versi akhir penulis).
- Akses Workspace ke setiap anggota dikelola melalui Group. Setelah Group memetakan pengguna ke Workspace, Workspace dapat digunakan. Saat membuka Phoenix, pengguna masuk ke satu Workspace yang sudah memiliki struktur folder.
- Setiap Pro memiliki satu rangkaian folder yang berawal dari **Origin**. Jika komponen Workspace ditempatkan di folder yang lebih dalam, folder itu menjadi root.
- **Membuat:** buka folder di Area Manajemen Folder, klik kanan > Add > Developer > Workspace, isi Name dan Description, klik Create.
- **Mengubah:** tombol Edit pada bilah navigasi mengubah **atribut Workspace** (Name, Description), lalu klik Update. Tombol Edit bukan untuk mengubah sel hak akses.
- **Menyegarkan:** tombol Refresh memuat ulang tampilan.
- **Menghapus:** klik kanan Workspace > Delete, lalu konfirmasi dengan Delete. Sebelum menghapus, pastikan setiap Group masih memiliki Workspace lain agar pengguna tetap bisa memakai Phoenix.
- Bilah navigasi Workspace hanya memiliki tombol Edit dan Refresh.
- **Halaman kerja:**
  - Kolom kiri: Folder/ Component. Kolom kanan: Comp. Access, Data Access, Function Access.
  - Baris Origin = workspace. Baris Group (contoh: Administrator) hanya mengatur akses dari Workspace ke komponen Group tersebut, **bukan** akses per anggota.
  - Sel kosong berarti akses itu tidak relevan untuk komponen tersebut.
  - Arti angka dan ikon di samping nama komponen dijelaskan di halaman Folder, bagian Informasi Data.
- **Hak akses** (nilai: allow / disallow):
  - Comp. Access (level komponen/header): Visible, Add (menambah folder atau komponen baru), Update (mengubah atribut komponen), Delete.
  - Data Access (level data): Add, Update, Delete. Jenis data bergantung komponen (Table View: Row dan TableData; Timeline: TimelineData). Penjelasan lengkap ada di subhalaman Data Access.
  - Function Access: Merge (penggabungan data), Modify Event, View Publish (hanya melihat konfigurasi publikasi, misalnya menyalin Publish Link), Publish (memperbarui konfigurasi publikasi).
- **Pewarisan:** jika folder induk Visible = disallow, seluruh isinya tidak dapat diakses meski allow. Disallow juga dapat diterapkan pada komponen selain folder, misalnya komponen Workspace dan Tree.
- Nama folder pada gambar contoh penulis adalah kasus pribadi dan tidak disebut di dokumentasi.

## Flow (Modul Logic)

Sumber: halaman "Apa itu Flow" yang sudah direvisi penulis (status release).

- **Definisi (versi penulis):** Flow adalah komponen untuk mengatur logika dan proses pengelolaan data dengan pendekatan **alur komposit**, yaitu menyusun logika dengan menghubungkan blok demi blok. Setiap blok dapat dihubungkan dan dimonitor agar setiap Event yang terikat menghasilkan keluaran dan otomasi yang tepat.
- **Istilah resmi:** area kerja Flow disebut **Blueprint** (bukan "kanvas"). Block pemicu disebut **Flow Block Event**.
- **Struktur halaman:**
  - `Docs/Modul Logic/Flow/Apa itu Flow` (halaman komponen, bertindak sebagai peta).
  - `Docs/Modul Logic/Flow/Flow Block/Pengenalan` dengan anchor `#Antarmuka Flow Block` (input, output, koneksi), `#Menambahkan Flow Block`, `#Konfigurasi Flow Block`, `#Menghubungkan Koneksi`.
  - `Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan` (kategori Event; pola yang sama diperkirakan untuk kategori lain).
  - `Docs/Modul Logic/Flow/Flow Activity` (panel pemantauan proses; kolom, status, dan pencarian dijelaskan di sini).
  - `Docs/Event/Menghubungkan Event` (menghubungkan Event dari komponen).
- **Katalog Flow Block, tutorial menambah dan menghubungkan block, serta konfigurasi block tidak ditulis di halaman Apa itu Flow.** Semua itu berada di subhalaman Flow Block.
- **Membuat Flow:** buka folder di Area Manajemen Folder, klik kanan > Add > Logic > Flow, isi Name dan Description, klik Create.
- **Mengubah Flow:** tombol Edit mengubah atribut Flow (Directory, Name, Description), lalu klik Update.
- **Menyegarkan:** tombol Refresh memuat ulang halaman kerja.
- **Menghapus Flow:** buka folder, klik kanan Flow > Delete, konfirmasi dengan Delete. **Dampak:** Flow Block dan riwayat Activity dapat hilang, dan Flow Block Action yang sudah digunakan oleh komponen akan terputus.
- **Antarmuka Flow:** bilah navigasi di bagian atas dan Blueprint di bagian bawah. Bilah navigasi berisi judul Flow (ikon Flow dan Header Name), Edit, Refresh, tombol Submission (membuka bilik submission), dan kolom Search (mencari Flow Block).
  - **Mode desktop:** tombol Submission menampilkan empat informasi, yaitu total activity, done, waiting, dan failure (urutan ikon pada screenshot). Pada langkah memantau, penulis menyebut "menu Activity atau tombol di sebelah kanan Refresh (mode desktop)", jadi pada mode lain pintu masuknya berupa menu Activity.
  - **Interaksi Blueprint:** tekan dan tahan pada bagian kosong lalu gerakkan kursor (mengubah posisi panning), scroll (zoom in/zoom out), klik informasi koordinat x/y (mengembalikan posisi ke tengah), klik informasi scale (mengembalikan skala ke awal), klik kanan pada bagian kosong (membuka konteks menu).
- **Kategori menu Add** (screenshot): Event, Data, I/O, Query, Operator, Modular, Misc. JSON penulis memuat Chrono (Delay) dan Error (Error Message) yang diasumsikan berada di Misc.
  - **Event:** Pulser, Variable Event, Enum Data Event, Table Row Event, Tree Node Event. Pulser punya tombol Trigger tanpa ikon untuk eksekusi manual.
  - **Data:** Variable (Add Variable, Delete Variable, Variable, Variable Getter, Variable Setter, Variable Value), Enum (Add EnumData, Delete EnumData, Enum, EnumData, EnumData Getter, EnumData Setter, EnumData Value), Table (Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, TableData Setter), Tree (Add Node, Assign Node, Delete Node, Node, Node Get Ancestor, Node Get Children, Node Get Parent, Node Setter, Tree, Tree Get Origin).
  - **I/O:** Branch, Passer. **Query:** Condition, Execute.
  - **Operator:** Number (Increment), String (Concatenate, Implode, Pad Left, Pad Right), Table (TableRow Parse), Object (Assign, Merge, Parse, Stringify), Boolean (If), Tree (Node Parse).
  - **Modular:** API (HTTP Request), AI (OpenAI 4).
  - **Misc. (asumsi):** Chrono (Delay), Error (Error Message).
- **Menghubungkan block:** klik dan tahan (hold press) pada output, arahkan ke input, lalu lepaskan (release). Output di sisi kanan, input di sisi kiri.
- **Eksekusi manual:** lewat antarmuka Flow, gunakan tombol pada Flow Block Event (misalnya Trigger pada Pulser).
- **Event dari komponen:** Flow Block Event yang sudah dibuat dapat langsung dihubungkan melalui tombol Event pada masing-masing komponen.
- **Memantau proses:** klik tombol Activity/Submission, panel Flow Activity terbuka. Panel memiliki tombol Refresh List, kolom Search Activity, kolom ID/Name, Status/Type, Start At, Updated At, dan menampilkan "No Activity" bila kosong.

## Pola penulis (lintas komponen)
- Kolom isian dan teks informasi antarmuka memakai `[[^field|Label]]` (bukan `[[field|Label]]`), termasuk Search, No Activity, Header Name, `x _ y _`, dan `scale _`.
- Ikon tombol yang dipakai: edit, delete, refresh, submission, event, activity, empty. Tombol tanpa ikon di dalam block (Trigger) memakai `[[^button/empty|Trigger]]`.
- Callout memakai judul: `>**note** Judul` atau `>**warning** Judul`, lalu isi pada baris `>` berikutnya.
- Halaman komponen besar memuat bagian Antarmuka (gambar, penjelasan area, tabel tombol bilah navigasi, catatan perbedaan desktop/mobile) dan Interaksi Antarmuka (tabel Fungsi dan Aksi).
- Bagian aspek pengelolaan (misalnya "Membangun Logika Flow") berisi daftar tautan anchor ke subhalaman, bukan langkah rinci.
- Path komponen Data yang dipakai penulis: `Docs/Modul Data/<Komponen>/Apa itu <Komponen>` (Variable, Enum, Table, Tree).