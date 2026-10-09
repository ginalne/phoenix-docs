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

## Variable (Modul Data)

- **Komponen Variable** mengelola **Variable Data** (tipe data Variable) di dalam sebuah Pro. Nilai yang disimpan menjadi sumber kebenaran dan dapat dirujuk dari komponen mana pun.
- **Komponen unik:** hanya ada satu per Pro, dibuat otomatis ketika Pro dimulai di folder root. Tidak dapat ditambah lewat Area Manajemen Folder, tidak dapat diduplikasi, dan tidak dapat dihapus. Boleh dipindahkan ke folder lain.
- Header "Variables" tidak dapat diganti, sehingga tidak ada tombol Edit dan tidak ada langkah mengubah atribut komponen.
- **Membuka:** klik "Variables" di Area Manajemen Folder.
- **Halaman kerja:** bilah navigasi (judul komponen, Refresh, kolom pencarian "Search Variable Data...") dan tabel Variable di bawahnya.
- **Kolom tabel:**
  - Name (unik, diisi pengguna)
  - Type (diisi pengguna)
  - Value (diisi pengguna, menyesuaikan Type)
  - Description (diisi pengguna)
  - Created At dan Updated At (terisi otomatis)
  - Action (berisi tombol Delete per baris)
- **Tombol pada area tabel:** Add Row, Save, Delete. Cancel untuk membatalkan penambahan.
- **Interaksi:** kolom di sisi kanan dilihat dengan scroll horizontal di bagian bawah tabel.
- **Mengelola Variable Data:**
  - Menambah: Add Row, isi Name, Type, Value, Description, lalu Save.
  - Mengubah: ubah isian pada baris, lalu Save.
  - Menghapus: klik Delete pada kolom Action, lalu konfirmasi dengan Delete. Data yang dihapus tidak dapat dikembalikan.
- **Cara komponen lain merujuk Variable:**
  - Field bertipe Variable: pilihannya adalah daftar Name dan Description dari Variable Data.
  - Komponen di Modul Logic: mengisi field Variable cukup dengan Alias, yaitu isi Name. Jika Alias tidak valid (tidak ada Name yang cocok), tidak ada nilai yang diterima atau terjadi error. Laporan error tampil di Flow Activity.
  - Variable Getter (Flow Block) mengambil nilai Variable dengan mengisi Name.
- **Akses:** anggota yang tidak memiliki akses komponen Variable tidak dapat mengetahui Value, tetapi tetap dapat memakainya untuk otomasi atau integrasi. Anggota yang memiliki akses melihat Value secara terbuka di halaman kerja.
- **Pemisahan halaman:** halaman komponen Variable membahas pengelolaan. Penjelasan Variable sebagai tipe data ada di halaman Tipe Data (`Docs/Tipe Data/Variable`).

Enum (Modul Data)

Menggantikan usulan sebelumnya. Sumber: halaman "Apa itu Enum?" yang sudah direvisi penulis.

Enum adalah komponen modul Data untuk deret data atau Master Data: pilihan, menu, opsi, dan kategori. Setiap Enum memiliki banyak EnumData (Docs/Tipe Data/EnumData).
Path halaman: Docs/Modul Data/Enum/Apa itu Enum. Atribut penting Strict On Selected dijelaskan di Docs/Modul Data/Enum/Konfigurasi Tegas. Fungsi Merge dan Event dijelaskan di halaman lain (Docs/Modul Data/Enum/Merge, Docs/Modul Data/Enum/Event).
Atribut Enum: Name, Description, Format, Header, Strict On Selected. Dialog Create dan Update memiliki field yang sama. Tombol dialog: Create atau Update, dan Cancel.
Name Enum: mengikuti aturan komponen lain, yaitu tidak boleh sama dengan komponen sejenis di folder yang sama. Name EnumData tidak boleh sama di dalam Enum yang sama.
Format dan Header: Format menentukan bentuk kolom Value. Pasangan Format → Header: EnumData → Enum, Column → Table, Row → Table, TableData → Column, Node → Tree. Format lainnya: Header bernilai N/A.
Mengubah Format: masih bisa setelah ada EnumData. Muncul peringatan dan field Force Update harus diisi dengan salah satu mode: loss safe (mencoba mengonversi nilai ke Format baru, jika gagal muncul peringatan yang sama) atau force (paksa, nilai yang tidak dapat dikonversi bisa hilang). Jangan memakai istilah "loss" atau "lossless".
Menghapus Enum: seluruh EnumData hilang. Relasi dari komponen lain harus dihapus terlebih dahulu. Menghapus EnumData meminta konfirmasi dengan tombol Delete.
Halaman kerja: bilah navigasi (judul Enum, Edit, Merge, Event, Refresh, kolom pencarian "Search Enum Data...") dan tabel EnumData (kolom Name, Description, Value, Selectable, Action; tombol Save dan Delete per baris; Add Row; pagination). Label kecil di atas header kolom Value adalah ikon tipe data. Pagination "Show 50 of 1 items" berarti batas 50 item per halaman. Dua tombol Add Row (di bawah baris terakhir dan di bilah bawah) fungsinya sama. Tombol Save aktif setelah ada perubahan pada baris. Tidak ada perbedaan signifikan antara desktop dan mobile.
Value: tampilan mengikuti Format. Ikon mata pada screenshot penulis hanya bagian dari Format Password, bukan fitur Enum, jadi tidak perlu dijelaskan sebagai fungsi Enum.
Selectable: field berformat EnumData hanya menampilkan EnumData dengan Selectable = Yes. Selectable hanya berlaku untuk field; EnumData dengan Selectable = No tetap dapat dipakai di tempat lain.
Add Row menambahkan baris (EnumData).
Nama Enum dan isi pada screenshot penulis adalah kasus uji pribadi dan tidak disebut di dokumentasi.

## Enum (Modul Data)

Menggantikan usulan sebelumnya. Sumber: halaman "Apa itu Enum?" yang sudah direvisi penulis.

- Enum adalah komponen modul Data untuk deret data atau *Master Data*: pilihan, menu, opsi, dan kategori. Setiap Enum memiliki banyak EnumData (`Docs/Tipe Data/EnumData`).
- Path halaman: `Docs/Modul Data/Enum/Apa itu Enum`. Atribut penting **Strict On Selected** dijelaskan di `Docs/Modul Data/Enum/Konfigurasi Tegas`. Fungsi Merge dan Event dijelaskan di halaman lain (`Docs/Modul Data/Enum/Merge`, `Docs/Modul Data/Enum/Event`).
- **Atribut Enum:** Name, Description, Format, Header, Strict On Selected. Dialog Create dan Update memiliki field yang sama. Tombol dialog: Create atau Update, dan Cancel.
- **Name Enum:** mengikuti aturan komponen lain, yaitu tidak boleh sama dengan komponen sejenis di folder yang sama. Name EnumData tidak boleh sama di dalam Enum yang sama.
- **Format dan Header:** Format menentukan bentuk kolom Value. Pasangan Format → Header: EnumData → Enum, Column → Table, Row → Table, TableData → Column, Node → Tree. Format lainnya: Header bernilai N/A.
- **Mengubah Format:** masih bisa setelah ada EnumData. Muncul peringatan dan field **Force Update** harus diisi dengan salah satu mode: *loss safe* (mencoba mengonversi nilai ke Format baru, jika gagal muncul peringatan yang sama) atau *force* (paksa, nilai yang tidak dapat dikonversi bisa hilang). Jangan memakai istilah "loss" atau "lossless".
- **Menghapus Enum:** seluruh EnumData hilang. Relasi dari komponen lain harus dihapus terlebih dahulu. Menghapus EnumData meminta konfirmasi dengan tombol Delete.
- **Halaman kerja:** bilah navigasi (judul Enum, Edit, Merge, Event, Refresh, kolom pencarian "Search Enum Data...") dan tabel EnumData (kolom Name, Description, Value, Selectable, Action; tombol Save dan Delete per baris; Add Row; pagination). Label kecil di atas header kolom Value adalah ikon tipe data. Pagination "Show 50 of 1 items" berarti batas 50 item per halaman. Dua tombol Add Row (di bawah baris terakhir dan di bilah bawah) fungsinya sama. Tombol Save aktif setelah ada perubahan pada baris. Tidak ada perbedaan signifikan antara desktop dan mobile.
- **Value:** tampilan mengikuti Format. Ikon mata pada screenshot penulis hanya bagian dari Format Password, bukan fitur Enum, jadi tidak perlu dijelaskan sebagai fungsi Enum.
- **Selectable:** field berformat EnumData hanya menampilkan EnumData dengan Selectable = Yes. Selectable hanya berlaku untuk field; EnumData dengan Selectable = No tetap dapat dipakai di tempat lain.
- **Add Row** menambahkan baris (EnumData).
- Nama Enum dan isi pada screenshot penulis adalah kasus uji pribadi dan tidak disebut di dokumentasi.

## Table (Modul Data)

- **Definisi:** Table adalah komponen modul Data untuk menyimpan data secara kompleks, baik transaksional maupun generik. Table memiliki beberapa Column (`Docs/Tipe Data/Column`) dengan format berbeda, dan Row (`Docs/Tipe Data/Row`) yang masing-masing memiliki TableData (`Docs/Tipe Data/TableData`) sesuai kolom yang tersedia. Expression (`Docs/Tipe Data/Expression`) adalah Tipe Data untuk melakukan perhitungan dengan fungsi yang disediakan, dan dapat langsung digunakan pada Table.
- **Path halaman:** `Docs/Modul Data/Table/Apa itu Table`. Judul: "Apa itu Table?". Subhalaman yang disepakati: `Docs/Modul Data/Table/Merge`, `.../Publish`, `.../Event`. Subhalaman yang diusulkan: `.../Upload` dan `.../Mengisi TableData` (cara mengisi data per Format Column).
- **Row awal:** Row pada Table yang baru dibuat masih kosong.
- **Dialog Create New Table** (gambar `add-table.png`, diletakkan di awal bagian Membuat):
  - Directory (Search Folder): terisi otomatis sesuai folder yang diklik kanan. Dikosongkan berarti letak root.
  - Name, Description, tombol Upload (membuat Table dari file), bagian Column dengan tombol Add Column, serta tombol Cancel dan Create.
  - Tabel Column berkolom Index, Name, Format (placeholder "Select Data Format..."), Header, Description, Alias (ikon bintang), dan Action (Delete). Dialog awal menampilkan dua baris Column, tetapi **minimal Column adalah 1**.
  - **Header** bernilai N/A (not applicable) bila Format tidak membutuhkannya. Bila Format membutuhkan, Header diisi: Format bertipe EnumData membutuhkan Header Enum, dan Node membutuhkan Tree.
- **Alias:** wajib dipilih satu Column saat membuat Table. Alias yang dipilih tampil pada field berformat Row dengan pola `ID - Alias Value`.
- **Mengubah Table (Edit > Update):** Name, Description, dan juga Column, Format, serta Alias dapat diubah. Bila perubahan berisiko menghilangkan data, Phoenix menampilkan peringatan data loss, dan pengguna dapat melanjutkan dengan *force update*.
- **Menghapus Table:** seluruh Column, Row, dan TableData ikut terhapus.
- **Halaman kerja:** bilah navigasi berisi judul Table (ikon Table dan Header Name), Edit, Merge, Publish, Event, Refresh, dan kolom pencarian "Search Table Data...". Tidak ada perbedaan signifikan antara tampilan desktop dan mobile.
  - Tabel data memiliki kolom tambahan **ID** di awal (terisi otomatis) dan **Action** di akhir (tombol Save dan Delete per Row). Ikon kecil pada header Column menunjukkan format (contoh: abc untuk String, T untuk Text). Nama Column ada di header, tetapi pada screenshot sebagian tertutup.
  - **Save** hanya aktif ketika ada perubahan. **Add Row** tersedia di bawah baris terakhir dan di bagian bawah halaman, keduanya berfungsi sama. Saat menambah atau mengubah Row tersedia tombol **Cancel** untuk membatalkan.
  - Menghapus Row memunculkan dialog konfirmasi, dan Row yang dihapus tidak dapat dikembalikan.
  - Bagian bawah: scroll horizontal, informasi "Show 50 of 2 items, on page" (angka 50 adalah batas data per halaman), input nomor halaman dengan Go, serta Prev dan Next.
- **Contoh Flow:** Table Row Event (`Docs/Modul Logic/Flow/Flow Block/Event/Table Row Event`) menghasilkan output bertipe Row. HTTP Request berada di `Docs/Modul Logic/Flow/Flow Block/Modular/HTTP Request`.
- **Merge, Publish, Event:** detail dijelaskan di halaman masing-masing. Ketiganya dibatasi Function Access di Workspace.
- **Penamaan pada screenshot** (nama Table, Row, dan Column pada gambar contoh penulis) adalah kasus pribadi dan tidak disebut di dokumentasi.

## Tree (Modul Data)
 
- **Definisi:** Tree adalah komponen modul Data untuk menyimpan data secara hierarki atau berbentuk pohon. Cocok untuk data relasional yang bercabang. Satu Tree memiliki banyak Node (`Docs/Tipe Data/Node`). Atribut penting: **Merger Mode** (`Docs/Modul Data/Tree/Konfigurasi Merger Mode`). Penulis menyebut Tree yang memakainya "bersifat Merger".
- **Path halaman:** `Docs/Modul Data/Tree/Apa itu Tree`. Judul: "Apa itu Tree?". Subhalaman: `Konfigurasi Merger Mode`, `Konfigurasi External Read Only` (usulan, menunggu konfirmasi), `Mengelola Node` (anchor: Menambahkan Node, Mengubah Node, Melihat Detail Node, Menghapus Node, Import Node, Export Node), `Publish`, `Event`.
- **Node awal:** Tree yang baru dibuat otomatis memiliki satu Node bernama **Origin**.
- **Merger Mode:** Tree bersifat merger dapat memanggil Node dari beberapa Tree non-merger dan menambahkannya (*clone*), dengan atau tanpa mengikuti perubahan Node asal. Tree merger juga memiliki Node sendiri (relasi: Tree Merger memiliki Node, Node dari Tree non-merger di-*clone* ke Node di Tree Merger). **Tree non-merger tidak bisa menambahkan Node dari Tree lain. Merger Mode tidak dapat diubah setelah Tree dibuat.** Merger Mode dijelaskan di halaman terpisah. Narasi motivasi (Node sulit difiltrasi atau digabungkan antar Tree) adalah makna, bukan fakta produk.
- **External Read Only (Order, Name, Children):** setiap atribut punya toggle sendiri. Non-Active: atribut Node di Tree ini ikut berubah ketika clone/origin Node dari Tree lain diperbarui. **Active: atribut terlindungi, tidak ikut berubah.** Berlaku untuk Tree merger **dan** Tree non-merger, karena perubahan Node di Tree merger juga dapat mengubah Node di Tree non-merger. Pilihan "mengikuti/tidak mengikuti perubahan" saat clone saling terkait dengan External Read Only (bentuk keterkaitannya belum dijelaskan penulis).
- **Dialog Create Tree** (gambar `add-tree.png`): Directory (placeholder Search Folder..., terisi otomatis sesuai folder yang diklik kanan, kosong berarti root), Name (Tree Name...), Description (Tree Description...), toggle Merger Mode, grup External Read Only (toggle Order, Name, Children), grup Default Configuration (toggle Horizontal Mode, dropdown Context). Semua toggle bawaannya Non-Active, Context bawaannya Menu. Tombol: Cancel dan Create.
- **Horizontal Mode:** Active = horizontal (akar kiri ke kanan), Non-Active = vertikal (akar atas ke bawah).
- **Context:** status ketika pengguna membuka menu konteks Node. Pilihan: Menu (menampilkan menu konteks), Edit (membuka pengelolaan ubah Node), Detail (membuka detail Node).
- **Default Configuration hanya nilai awal.** Di halaman kerja, context dan mode dapat diganti dengan klik, tetapi sementara. Untuk mengubah nilai awal, gunakan Edit.
- **Halaman kerja:** bilah navigasi (judul Tree dengan ikon Tree dan Header Name, Edit, Publish, Event, Refresh, kolom pencarian "Search Tree Data...") dan area kerja berisi pohon (penulis menyebutnya blueprint). Tidak ada tombol Merge pada screenshot. Bagian bawah area kerja menampilkan informasi context, mode, koordinat (x, y), dan scale.
  - **Search Tree Data** hanya mencari Name Node.
  - **Interaksi:** tekan-tahan pada bagian kosong lalu gerakkan kursor untuk menggeser tampilan (*pan*), gulir untuk zoom, klik koordinat untuk memusatkan tampilan, klik scale untuk kembali berskala 1, klik mode atau context untuk mengganti nilainya (sementara), klik kanan pada Node untuk menu konteks.
  - **Publish dan Event** dibatasi Function Access di Workspace, dan dijelaskan di halaman lain.
  - Tidak ada catatan perbedaan desktop dan mobile yang diberikan penulis.
- **Menu konteks Node** (gambar `node-menu.png`): Edit, Detail, Expand/Collapse, View, Import, Export. Edit, Detail, Import, Export dijelaskan di halaman Mengelola Node, dan format Import/Export di halaman lain.
  - Submenu View: Collapse Below Level (melipat keturunan pada level Node ini, semua Node), Expand Children Only (memperluas hanya satu keturunan di bawahnya), Collapse Descendant (*recursive collapse*), Expand Descendant (*recursive expand*), Hide Collapsed (menyembunyikan anak yang dilipat), Show Collapsed (memunculkan anak yang dilipat), Collapse and Hide (melipat dan menyembunyikan).
  - Jika Node tidak memiliki anak, Expand/Collapse dan Expand Children Only berubah menjadi "No children...".
- **Menghapus Tree:** seluruh Node hilang. Relasi dari komponen lain (Column Table yang memakai Node, Flow Block seperti Tree Node Event) terputus. Node clone di Tree merger dapat terdampak.
- **Contoh Flow (diterima penulis):** `Event/Tree Node Event`, `Operator/Node Parse`, `Modular/HTTP Request` di `Docs/Modul Logic/Flow/Flow Block/<Kategori>/<Nama Block>`.
- **Penamaan pada screenshot** (nama Tree pada judul halaman kerja dan nama pengguna di bilah atas) adalah kasus pribadi dan tidak disebut di dokumentasi. Nama Node pada screenshot menu konteks (Child A, B, C) sudah generik.
Alasan: jawaban penulis mengonfirmasi dan mengoreksi beberapa asumsi saya (Active = terlindungi, Merger Mode tidak dapat diubah, External Read Only berlaku di kedua jenis Tree, context dan mode dapat diklik tetapi sementara). Semuanya perlu tersimpan agar subhalaman Tree dan Flow Block terkait konsisten.