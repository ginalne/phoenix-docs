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
  - Data Access (level data): Add, Update, Delete. Jenis data bergantung komponen (Table: Row dan TableData; Table View: Data TableView; Timeline: Timeline Data). Untuk Table View, Data Access hanya mengatur pengelolaan Data (ubah nama, ubah Query, ubah konfigurasi), bukan Row atau cell. Penjelasan lengkap ada di subhalaman Data Access.
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
- **Path halaman:** `Docs/Modul Data/Table/Apa itu Table`. Judul: "Apa itu Table?". Subhalaman yang disepakati: `Docs/Modul Data/Table/Merge`, `.../Publish`, `.../Event`. Subhalaman yang diusulkan: `.../Upload`. Cara mengisi data per Format Column dirujuk penulis ke anchor `Docs/Modul Data/Table/Apa itu Table#Mengelola Data Table` (bukan subhalaman `Mengisi TableData`).
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

## Table View (Modul Interface)

- **Definisi:** Table View (boleh juga ditulis TableView) adalah komponen modul Interface untuk menampilkan data Table menggunakan Query. Satu Table View memiliki lebih dari satu **Data**, dan setiap Data menampung satu Query, satu nama, dan konfigurasi tampilan.
- **Path:** `Docs/Modul Interface/Table View/Apa itu Table View`.
- **Data memiliki konfigurasi mode `editable` atau `readonly`**.
- **Query pada Table View:**
  - Wajib mengikuti **kaidah Table Output** (`Docs/Tipe Data/Query#Table Output`).
  - Istilah penulis di halaman Query: **Filter**, **Show or Hide**, **Table Output**, **Error**. Anchor yang dipakai: `#Filter`, `#Show or Hide`, `#Table Output`, `#Error`.
  - Query kosong ditandai teks "Empty". Kesalahan Query ditandai "Error" dan penjelasannya ada di `Docs/Tipe Data/Query#Error`. Teks pesan di aplikasi ditulis penulis sebagai "Query table output is not valid!".
- **Kegunaan:** menampilkan lebih dari satu data Table dalam satu halaman, yang dapat dikontrol kolomnya (Show or Hide) dan difiltrasi (Filter).
- **Mengelola baris:** setiap field dapat diisi dan ditambahkan seperti pada komponen Table (rujukan: `Docs/Modul Data/Table/Apa itu Table#Mengelola Data Table`). Kolom yang menjadi syarat Filter tetapi tidak ditampilkan Query (artinya tidak bisa diisi lewat Data Table View) **terisi otomatis** saat baris ditambahkan, agar baris tetap memenuhi Query dan tidak hilang bahkan setelah Refresh.
- **Dampak penghapusan:** menghapus Data atau Table View hanya menghapus Query dan konfigurasi, baris di data sumber tidak terhapus. Menghapus baris dari Table View menghapusnya dari sumber dan tidak dapat dikembalikan.
- **Hak akses (berlapis):**
  - Data Access Table View di Workspace mengatur pengelolaan Data: ubah nama, ubah Query, ubah konfigurasi.
  - Baris dan isi sel hanya dapat dikelola bila **dua syarat** terpenuhi: konfigurasi Data `editable` dan Data Access data sumber di Workspace mengizinkan. Jika salah satu tidak terpenuhi, baris dan sel tidak dapat dikelola.
  - **Aturan umum:** prinsip ini berlaku untuk semua komponen Interface yang dapat memanipulasi data di komponen Modul Data.
- **Membuat:** dialog Create memiliki Directory (terisi otomatis sesuai folder yang diklik kanan, dapat diganti, kosong berarti letak root), Name, Description.
- **Halaman kerja**: bilah navigasi (judul dengan ikon Table View dan Header Name, Edit, Refresh, kolom pencarian "Search TableView Data...") dan area Data.
  - Judul Data: ikon panah, nama Data, dan angka jumlah baris dalam kurung. Arti `(3) ()` pada Data berQuery kosong belum terkonfirmasi.
  - Pilihan tampilan `full`, `half`, `quarter` berupa pilihan radio (`^value/radio`) yang menentukan porsi layar.
  - Tombol Q (icon `q`) membuka popup konfigurasi Query. Perubahan Query **tersimpan otomatis** saat popup ditutup dengan klik di luar popup, tidak ada tombol Save.
  - Kolom Data: kolom hasil Query ditambah Action. Baris Data: baris hasil Query dengan Save dan Delete. Add Row dan pagination seperti Table.
  - Tombol Add Data ada di bagian bawah halaman. Data baru tampil dengan Query kosong (Empty). Nama awal Data baru belum terkonfirmasi.
- **Interaksi:** klik judul Data untuk collapse atau expand. Klik kanan judul Data membuka menu konteks: Rename (dialog dengan tombol Ok), Add Row, Add Data, Delete Data (dengan konfirmasi Delete). Search di bilah navigasi mencari kata kunci di semua kolom pada Data.
- **Nama awal Data baru** adalah New Data (n) <- jika ada nama yang sama, n dari 1 sampai tak terhingga.
- **arti (x) setelah nama ** adalah total baris hasil Query.
- **Efek penghapusan Table View atau Data** tidak mempengaruhi komponen lain.

## Kanban (Modul Interface)

*   **Definisi:** Kanban adalah komponen modul Interface yang menampilkan data dalam bentuk kolom-kolom berdasarkan status atau kategori. Setiap data (Row Table) direpresentasikan sebagai kartu yang dapat dipindahkan antar kolom. **Kanban bersifat generik**: cocok untuk data apa pun yang memiliki tahapan atau kategori, tidak khusus untuk tugas. Penulis menulis "memvisualisasikan data secara segmentatif".
*   **Path:** `Docs/Modul Interface/Kanban/Apa itu Kanban`. Subhalaman: `Docs/Modul Interface/Kanban/Template Kartu` (langkah rinci Add Column, Class, urutan, Delete; sudah ditandai DONE oleh penulis).
*   **Table - Column (wajib):** saat membuat Kanban, field Table - Column wajib diisi. Daftar pilihannya hanya berisi Column berformat EnumData. EnumData dari Enum Column tersebut menjadi kolom Kanban. Contoh: Enum Status dengan 4 EnumData menghasilkan 4 kolom.
*   **Mengubah Kanban (Edit > Update):** Name, Description, dan Table - Column dapat diubah. **Mengganti Table pada Table - Column otomatis menghapus template kartu.** Row di Table sumber tidak terhapus karena Kanban hanya menampilkan data. Peringatan diabaikan bila perubahan hanya pada Column di Table yang sama (diasumsikan template tetap; belum terkonfirmasi untuk Column dengan Enum berbeda).
*   **Dialog Create Kanban** (gambar `add-kanban.png`): baris Name berisi bagian kiri tanda `/` (tampaknya folder tujuan) dan kolom Name, lalu Description, Table - Column (placeholder "Empty"), tombol Cancel dan Create.
*   **Kartu:** setiap Row pada Table tampil sebagai kartu di kolom sesuai nilai Column EnumData-nya.
*   **Halaman kerja** (gambar `interface-kanban.png`): bilah navigasi (judul Kanban dengan ikon Kanban dan Header Name, Edit, Refresh, kolom pencarian "Search Kanban Data...") dan area kolom.
*   **Header kolom:** jumlah item (angka dengan ikon kartu), Name - Description EnumData, dan tombol Setting (ikon roda gigi). Pada screenshot, kolom terakhir tidak menampilkan Setting (belum terkonfirmasi penyebabnya).
*   **Interaksi (jawaban penulis):**
    *   Memindahkan kartu: *drag and drop*, atau klik kanan kartu lalu **Move To**.
    *   Klik kiri kartu menampilkan **Form Table** (Row dalam bentuk form) untuk mengubah isi Row langsung.
    *   Menu konteks kartu: **Detail** (hasilnya sama seperti klik kiri), **Add Row** (Row baru dengan nilai EnumData langsung terisi sesuai kolom tempat kursor), **Delete Row**, **Move To** (menampilkan daftar kolom yang tersedia, kecuali kolom nilai EnumData saat ini).
    *   Menggulir daftar kartu: kursor pada satu kolom, gulir atas/bawah, berlaku bila tinggi kartu melebihi layar.
    *   Menggulir kolom: kursor pada halaman kerja, gulir kiri/kanan, berlaku bila lebar kolom melebihi layar.
    *   Memindahkan kartu mengubah nilai EnumData pada Row sumber.
*   **Hak akses:** memindahkan kartu mengubah data Table sumber sehingga memerlukan izin Data Access data sumber (diterima penulis tanpa koreksi). Berlaku juga untuk Add Row dan Delete Row (asumsi).
*   **Setting kolom:** klik Setting membuka modal "Setup Kanban Template" (gambar `setup-kanban.png`) untuk EnumData tersebut. Isi modal: Enum Data, Column Template (toggle), bagian Header, Body, Footer dengan tombol Add Header/Body/Footer Column dan tabel No., Column, Class, Action (Delete per baris), serta tombol Cancel dan Update.
*   **Global dan Local:** toggle Column Template mati = Global (bawaan), toggle aktif = Local. Global: perubahan template memengaruhi EnumData lain **dalam Kanban yang sama** (tidak lintas Kanban). Local: hanya EnumData tersebut.
*   **Template kartu:**
    *   Column yang diisi tampil sesuai posisi template. Class berisi nama class styling; dijelaskan di `Docs/Styling/Styling Class`. Action berisi tombol Delete di setiap baris template.
    *   Header: tata letak flex-row, di bagian paling atas kartu, urutan kiri ke kanan. Body: flex-col, urutan atas ke bawah. Footer: flex-row, di bagian paling bawah kartu, urutan kiri ke kanan.
    *   **Informasi teknis Tailwind** (paket dan versi yang dipakai Angular) hanya untuk pemahaman Claude. Dokumentasi pengguna tidak menyebut Tailwind dan tidak memakai tautan eksternal, cukup arahkan ke `Docs/Styling/Styling Class`.
*   **Template kosong:** kartu menampilkan Kolom Alias pada Table (biasanya berformat Short Text).
*   **Menghapus Kanban:** Kanban dan template kartunya terhapus, Row di Table sumber tidak terhapus (asumsi, tidak dikoreksi penulis).
*   **Belum terkonfirmasi:** cakupan Search, perbedaan desktop dan mobile, penyebab kolom terakhir tanpa Setting, tempat Add Row bisa dipicu (klik kanan kartu atau juga area kosong kolom), dampak Delete Row (diasumsikan menghapus Row dari Table dan tidak bisa dikembalikan), letak halaman penjelasan Form Table.
*   **Penamaan pada screenshot** (nama folder di dialog Create, judul Kanban, nama EnumData, dan isi kartu) adalah kasus pribadi dan tidak disebut di dokumentasi.

## Gallery (Modul Interface)

*   **Definisi:** Gallery adalah komponen modul Interface yang menyajikan data dalam bentuk kartu visual yang menonjolkan gambar atau konten dari setiap data. Cocok untuk koleksi visual seperti katalog, portofolio, atau daftar aset, agar data mudah dikenali sekilas. Setiap Row pada Table tampil sebagai satu kartu.
*   **Path:** `Docs/Modul Interface/Gallery/Apa itu Gallery`. Subhalaman yang diusulkan: `Docs/Modul Interface/Gallery/Template Kartu` (menunggu konfirmasi).
*   **Dialog Create Gallery** (gambar `add-gallery.png`): baris Name berisi bagian kiri tanda `/` (folder tempat Gallery ditempatkan, terisi sesuai folder tempat Gallery ditambahkan, dapat dikosongkan sehingga berada di root) dan kolom Name, lalu Description, Table (placeholder "Select..."), tombol Cancel dan Create. Filter belum tergambar dan akan diperbarui penulis.
*   **Table (wajib)** dan **Filter (jika dibutuhkan).** Filter adalah daftar field kondisi seperti Query: kolom, operator, operand. **Table tidak dapat diubah** setelah Gallery dibuat.
*   **Mengubah Gallery (Edit > Update):** semua isian dapat diubah kecuali Table.
*   **Halaman kerja** (gambar `interface-gallery.png`): bilah navigasi (judul Gallery dengan ikon Gallery dan Header Name, Edit, Column, Refresh, kolom pencarian "Search Gallery Data...") dan area kartu. Tombol **Column** (ikon roda gigi, slug `setting`) disebut penulis sebagai "setting" dan membuka modal "Setup Gallery Template".
*   **Modal Setup Gallery Template** (gambar `setup-gallery.png`): bagian Header, Body, Footer dengan tombol Add Header/Body/Footer Column (ikon plus), tabel No., Column, **Styling**, Action, serta tombol Cancel dan Update. Tidak ada toggle Global/Local seperti Kanban.
*   **Template kartu:**
    *   Column yang diisi tampil sesuai posisi template. Styling berisi nama class styling untuk menyesuaikan desain (contoh dari penulis: `text-right`, `font-semibold`; penulis juga menyebut object-fit untuk gambar, nama class persisnya belum pasti). Dijelaskan di `Docs/Styling/Styling Class`.
    *   Header: flex-row, paling atas kartu, urutan kiri ke kanan. Body: flex-col, urutan atas ke bawah. Footer: flex-row, paling bawah kartu, urutan kiri ke kanan.
    *   Semua format data ditampilkan sebaik mungkin, termasuk gambar.
    *   **Template kosong** (kondisi awal): kartu menampilkan Kolom Alias pada Table (biasanya berformat Short Text).
*   **Interaksi kartu (keterangan penulis):** klik kanan kartu membuka Row dalam bentuk Form untuk diperbarui, berlaku jika Data Access Table di Workspace mengizinkan. Klik kiri kartu menampilkan menu Detail, Add Row, Delete. Pembagian ini berkebalikan dengan Kanban dan belum diverifikasi ulang.
*   **Belum terkonfirmasi:** isi Detail, form Add Row, konfirmasi Delete, apakah Add Row dan Delete memerlukan Data Access, cakupan Search, perbedaan desktop dan mobile, jumlah kartu per baris, gestur gulir, dampak menghapus Gallery (diasumsikan Row sumber tidak terhapus), serta label bagian kiri tanda `/` pada Name.
*   **Penamaan pada screenshot** (nama folder di dialog Create, judul Gallery, dan isi kartu) adalah kasus pribadi dan tidak disebut di dokumentasi.

## Timeline (Modul Interface)

*   **Definisi:** Timeline adalah komponen modul Interface yang menampilkan data dalam urutan waktu untuk memantau jadwal, riwayat aktivitas, dan progres proses. Cocok untuk perencanaan, pelacakan progres, dan melihat hubungan antar peristiwa dalam satu rentang waktu. Isinya ada dua: **Timeline Event** dan **Timeline Data**.
*   **Path dan struktur:** `Docs/Modul Interface/Timeline/Apa itu Timeline`. **Seluruh isi Timeline Event dan Timeline Data ditulis lengkap di halaman ini, tanpa subhalaman** (permintaan penulis). Tautan ke keduanya memakai anchor (`#Mengelola Timeline Event`, `#Mengelola Timeline Data`, `#Hak Akses Timeline Data`), bukan path subhalaman.
*   **Dialog Create Timeline** (`add-timeline.png`): baris Name berisi bagian kiri tanda `/` (tampil "root", diasumsikan folder tujuan), kolom Name, Description, tombol Cancel dan Create.
*   **Timeline Event:** membuat trigger Event ke Flow Block **Pulser**, dengan atau tanpa pengulangan.
    *   Dialog Create New Timeline Event (`add-timeline-event.png`): Name, Pulser Event (Select...), Start (tanggal-waktu), Repeat (toggle, bawaan aktif), End (tanggal-waktu), Interval, Active (toggle, bawaan aktif), Cancel dan Create.
    *   **Jika Repeat = Non-Active, field End dan Interval hilang** dan Timeline Event hanya memicu satu kali pada Start.
    *   **Pilihan Interval:** Custom, Minutely, Hourly, Daily, Weekly, Monthly, Quarterly, Yearly. Custom berisi isian angka dengan satuan Minute.
    *   **Active** mematikan atau menyalakan jadwal tanpa menghapus Timeline Event.
    *   **Hak akses:** Function Access **Modify Event** di Workspace.
    *   **Menu konteks blok Timeline Event:** Edit, Add Data, Add Event, Zoom, Delete Event. **Delete Event hanya menghapus Timeline Event, bukan Pulser.**
*   **Timeline Data:** membuka data sumber di sumbu waktu dengan bantuan **Query**. Query memakai **kaidah Timeline Output** (anchor `Docs/Tipe Data/Query#Timeline Output`) dengan error khusus. Pada bagian Show ada label **Name, Start, End** untuk menunjukkan kolom yang dipakai.
    *   **Kolom wajib (jawaban penulis): hanya Name dan End** (tertulis demikian, kemungkinan perlu dikonfirmasi apakah maksudnya Name dan Start). **Start dan End harus berformat waktu: DateTime, Date, DateTimeZone.**
    *   Query kosong ditandai "Empty" dan baris "Error" dengan pesan "Query must atleast have 2 showed column!" (salah ketik di aplikasi; dokumentasi memakai "Query must at least have 2 showed columns!").
    *   Tombol Q (icon `q`) membuka popup Query. **Query tersimpan otomatis saat popup ditutup**, lalu isi Row menyesuaikan.
    *   Nama awal Data baru berpola `New Data (n)`. Angka jumlah di judul Data adalah jumlah Row hasil Query.
    *   **Menu konteks judul Timeline Data:** Rename Data, Add Data, Add Event, Zoom, Delete Data. **Delete Data hanya menghapus konfigurasi dan Query**, Row sumber aman. (Jawaban penulis atas konfirmasi daftar menu ini berbunyi "itu bukan menu tapi balok yang ada di baris row" dan maknanya belum pasti.)
    *   **Menu konteks Row:** Edit (membuka form edit), View (hanya popup preview), Add Row, Add Data, Add Event, Zoom, Delete Row. **Delete Row menghapus Row pada sumber dan tidak dapat dikembalikan.** Add Row dipakai dari menu Row.
    *   **Mode `editable` / `readonly` dan hak akses mengikuti Table View:** Row dan isinya hanya dapat dikelola (termasuk menggeser blok) bila Timeline Data `editable` dan Data Access data sumber di Workspace mengizinkan. Data Access Timeline di Workspace mengatur pengelolaan Timeline Data. Tempat mode diatur belum diketahui.
*   **Menu konteks bagian kosong:** Add Data, Add Event, Zoom. **Cabang Zoom:** Zoom In, Zoom Out, Quarter - Month, Month - Week, Week - Date, Week - Dayweek, Date - Hour, Time - 30 Minute, Time - 10 Minute, Time - 1 Minute, Minute - Second. Header waktu menyesuaikan tingkat Zoom.
*   **Halaman kerja** (`interface-timeline.png`): bilah navigasi (judul dengan ikon Timeline dan Header Name, Edit, Refresh, kolom pencarian "Search Timeline Data..." yang **mencari Timeline Data dan Timeline Event**) dan area kerja: kolom "Item List", header waktu (contoh MonthYear/Week/Date atau MonthYear/DateDayweek/Hour), garis dan penanda "now", grup "Event (n)" (ikon jam hanya penanda grup/item Timeline Event; pesan "Event is empty" dan tombol Add Event bila kosong), grup Timeline Data (judul, jumlah Row, tombol Q; pesan "Data is empty" dan tombol Add Data bila kosong). Panah di judul grup melipat atau membuka grup. Ada celah antara header waktu dan blok data.
*   **Preview Row** (`preview-example.png`, nama file dari penulis): klik kiri Row atau View. Isi: judul, Start, End, Duration, Status (**Upcoming, On Going, Finished**), Calendar, Relative (keterangan relatif terhadap sekarang, contoh: sudah berakhir 180 hari lalu), **Progress (hanya tampil saat Status On Going)**, change time, dan Edit Row (membuka modal form edit; akses mengikuti Data Access sumber). Kontrol change time dibuka/ditutup dengan ikon di kiri bawah popup (dua ikon satu kesatuan, panah mengarah ke atas saat terbuka). Fungsi panah ganda dan tunggal pada kontrol belum terkonfirmasi.
*   **Interaksi:** gulir horizontal (berpindah waktu; pada mobile geser pada halaman kerja), geser vertikal (bila Event dan Data banyak), *wheel* (scale factor rentang waktu), klik dan geser blok (kiri = Start, kanan = End/finish, tengah = keduanya; akses sama seperti Table View), dan **Select** (klik dan geser pada celah antara header dan data; Ctrl + Shift lalu klik blok; Shift lalu klik dan geser pada area kerja). **Hasil Select: menu dan Zoom tetap sama, tetapi saat Add Row, Start dan End terisi otomatis sesuai rentang Select.**
*   **Belum terkonfirmasi:** arti End pada Timeline Event (diasumsikan batas akhir pengulangan) dan bentuk blok bila Repeat non-aktif, tempat mode `editable`/`readonly` diatur, tampilan blok bila Start tidak dipakai, cara label Name/Start/End ditentukan pada Show, nama tombol simpan pada form Add Row dan Edit Row, konfirmasi hapus untuk Event/Data/Row, dan fungsi panah ganda pada change time.
*   **Penamaan pada screenshot** (nama Timeline, Data, Row, serta judul dan tanggal pada popup preview) adalah kasus pribadi dan tidak disebut di dokumentasi.

## Form (Modul Interface)

*   **Istilah:** objek penyusun isi Form disebut **Elemen** (bukan Node, agar tidak konflik dengan Node sebagai tipe data). Kategori: **Layout** (Card, Full, Split, Accordion), **Display** (Text, Table, Tooltip, Qr, Chrono), **Input** (Basic, Quiz, Table, List). Halaman Elemen: `Docs/Modul Interface/Form/Elemen Form/<Tipe>/<Nama Elemen>` (contoh `Docs/Modul Interface/Form/Elemen Form/Layout/Card`). Halaman pendamping Elemen: `Elemen Form/Pengenalan`, `Elemen Form/Layout/Pengenalan`, `Elemen Form/Menambahkan`, `Elemen Form/Menghapus`, `Elemen Form/Mengonfigurasi#Properties Panel`, `Elemen Form/Mengonfigurasi#Header Toolbar`, `Elemen Form/Binding#Binding Layout`, `Elemen Form/State`.
*   **Form Flow:** panel "form flow" di bawah halaman kerja = alur Form. Halaman paling kiri tampil pertama, dan Form baru dapat disubmit setelah mencapai halaman terakhir.
*   **Templat Form** = Page dan Elemen, termasuk binding yang sudah dipetakan. Menghapus Form menghapus templat dan riwayat Submission; data yang sudah tersimpan tidak langsung terhapus; tautan publish menjadi tidak valid; publik yang sedang mengisi akan error saat mengirim.
*   **Menghapus Elemen:** menghapus Layout menghapus semua Elemen di dalamnya, dan ada konfirmasi.
*   **Pilih Elemen:** klik field "Type something here to add..." (hanya ada di Layout) lalu pilih dari dropdown; dapat mengetik untuk mencari Elemen.
*   **Panel Elemen (klik kiri di Edit Mode):**
    *   *Properties Panel:* Binding, State, Validators, Attributes, Children, Parent (isi berbeda per Elemen).
    *   *Header Toolbar:* pintasan aksi; selalu ada Remove. Pada Elemen teks (Text, Basic) juga ada ukuran font, Bold, Italic, Underline, dan rata kiri, tengah, kanan.
    *   *Layout Panel:* min. layout (persentase minimum terhadap layar), resize, padding, margin; dimiliki semua Elemen.
*   **Menu konteks Elemen (klik kanan):** Copy Layout Style, Paste Layout Style, Move Back, Move Next.
*   **Label binding** tampil di atas Elemen pada Edit Mode: label Table (ungu) pada Layout bertipe table, label pivot (biru), dan label Column (ikon kolom, oranye) di atas Elemen Input.
*   **Layout (Card, dst.):** setiap Layout punya Binding Type table atau pivot, artinya Layout menjadi header bagi Elemen di bawahnya. table = pilih Table sebagai header. pivot = untuk Layout anak bila Layout parent sudah punya table, sebagai relasi lanjutan; header table harus punya pivot dengan tabel lain, kalau tidak ada pilihan pivot kosong. Card: State Visible; Children (daftar Elemen di dalamnya, bertanda display atau input); header toolbar hanya Remove; punya field "Type something here to add...".
*   **Perbedaan Layout (Card, Full, Split, Accordion):** Header Toolbar (hanya Remove) dan Properties Panel (Binding, State Visible, Children) sama di keempatnya, dan semua Layout dapat menentukan Table header (Binding Type table atau pivot). Perbedaannya pada tampilan: **Card** = tampilan kartu; **Full** = tampilan penuh (detail visual belum dijelaskan penulis); **Split** = tampilan dibelah menjadi sisi **kiri dan kanan**, setiap sisi adalah **Layout Full** sehingga fungsi Add (field `Type something here to add...`) sama dengan Full, dan di **mobile** Split menjadi potongan **atas dan bawah**; **Accordion** = tampilan kartu dengan **header yang dapat di-toggle** untuk menyembunyikan dan menampilkan isinya. Accordion punya dua Attribute: **Label** (teks statis untuk title header, tidak dapat memakai expression) dan **Default State** (pilihan `Expanded` atau `Collapsed`, kondisi bawaan saat Form dibuka). Halaman Layout memakai kerangka sederhana dengan bagian "Mengapa Menggunakan <Layout>?" berisi keunikan antar Layout (poin "mengapa" generik dihapus penulis karena tidak relevan).
*   **Basic (Input):** Binding Table dan Column; State Visible, Enable, Readonly (toggle); Validators Required; Attributes Label, Placeholder, Format Type (mengikuti column binding, contoh String), Default Value (nilai bawaan saat pengisi baru/publik membuka Form); Parent (layout). Enable false = binding tidak aktif (tidak berpengaruh ke row). Readonly = isi tidak bisa diubah. Required = pengisi wajib mengisi agar bisa submit, tidak berlaku bila Visible atau Enable false; saat ini satu-satunya validator. Header toolbar teks (ukuran font, Bold, Italic, Underline, rata) memformat teks Label.
*   **Elemen Display (Text, Table, Tooltip, Qr, Chrono):** semua hanya punya State Visible dan Parent (Layout), tanpa Binding. Header toolbar hanya Remove, kecuali Text yang juga punya pengaturan teks. **Table:** pertama dibuat berukuran 2x2 (dua kolom dua baris), tombol "+" di setiap border untuk menambah kolom atau baris, klik kanan lalu Remove Row atau Remove Column untuk menghapus, baris pertama adalah header, isi sel teks biasa (tanpa binding dan expression), tidak ada Attributes; berbeda dengan Table pada Modul Data. **Tooltip:** kotak informasi yang selalu tampil (bukan muncul saat hover), Attributes Label dan Content. **Qr:** menampilkan kode QR yang siap di-scan; Edit Mode menampilkan isi QR sebagai teks, View Mode menampilkan kode QR sebenarnya; Attribute Content (teks statis). **Chrono:** kronologi berupa alur step, tampilan menurun berbentuk daftar, isi diatur langsung di halaman dengan tombol tambah dan hapus step, tidak ada input di Properties Panel; usulan isian per step: Title, Description, Time (opsional), fitur belum dibuat sehingga detailnya perlu dikonfirmasi ulang. Chrono Display berbeda dengan block Chrono (Delay) di Flow.
*   **Text (Display):** State Visible; Attributes Content (hanya teks statis, belum bisa berisi expression); Parent (layout); tanpa Binding pada panel. Header toolbar teks memformat Content.
*   **State dan Validators (halaman pendamping `Docs/Modul Interface/Form/Elemen Form/State` dan `Docs/Modul Interface/Form/Elemen Form/Validators`):** State ada 3, yaitu Visible, Enable, dan Readonly, ketiganya hanya pada Elemen input; Elemen display dan layout hanya punya Visible. Validators saat ini hanya Required, hanya pada Elemen input. Nilai awal Elemen input baru selalu Visible aktif, Enable aktif, Readonly nonaktif, Required nonaktif. Visible = false pada Layout menyembunyikan semua Elemen di dalamnya. Elemen input menyimpan ke Row saat submit hanya bila Enable = true, dan State lain tidak memengaruhi penyimpanan. Setiap field State dan Validators punya ikon saklar kecil di sebelah kanan label untuk beralih antara nilai statis dan expression. Statis = saklar (hijau true, abu-abu false) dan tidak berubah selama pengisi mengisi Form. Expression = kolom isian teks dengan autocomplete dan checker, dihitung ulang saat pengisian. Hasil expression harus Boolean (diperiksa checker). **Parameter expression memakai Alias Elemen input, bukan Label** (koreksi penulis). Contoh: `inputA not empty`.
*   **Binding (halaman pendamping `Docs/Modul Interface/Form/Elemen Form/Binding`):** Layout memakai Binding Type table atau pivot. Elemen input tidak memiliki pilihan Binding Type dan langsung mengisi field Column; field Table terisi otomatis dari Layout dan pengisi memilih Column dari Table header yang sudah diinformasikan Phoenix. Pivot pada Layout berfungsi bila Table header memiliki relasi: Table header punya Column bertipe Row, atau Table lain punya Column bertipe Row dengan Header = Table header. Elemen input multi row (Table dan List) mengisi Column dari Table lain yang punya Column bertipe Row dengan Header = Table header. Label field pivot hanya Column (dengan informasi Table yang dimaksud). Pengisian pada Layout anak ber-pivot menambah Row di Table relasi yang otomatis terhubung ke Row Table header.
*   **Alias dan title Submission pada Binding:** Alias bersifat opsional pada Elemen input, tampil sebagai checkbox Alias dan kolom teks (muncul saat checkbox true), fungsinya mendaftarkan Elemen sebagai parameter bagi Elemen lain. Nama Alias harus unik dan boleh karakter ASCII apa pun. Title Submission diatur lewat label `As Title` di bagian Binding dengan toggle Yes atau No; bintang di samping Column menandai isian title (biasanya nama pengisi) agar mudah dicari di Submission List. Bintang ini tidak terkait Alias pada Table.
*   **Submission dan update:** setiap pengisian Form yang baru menambah Row baru. Update isian yang sudah dikirim butuh Submission ID (tombol copy di Submission List pada halaman kerja). Tampilan pengisi punya menu untuk mengakses tautan itu, yang secara teknis tersimpan di local cache. Tautan hanya tersedia di perangkat yang sama dan hilang bila cache dihapus; admin dapat mengirim ulang tautan lewat tombol copy. Pengisi tidak butuh pengaturan akses tambahan, karena akses menambah Row dianggap sudah diizinkan saat pembuat Form memilih Table dan relasinya pada Binding.
*   **Binding checker:** menampilkan pesan di layar. Ejaan pesan asli dari aplikasi yang diberikan penulis: "Selected column and it's header is not match", "There is layout binded by pivot, but is not defined yet", "There is input binded by column, but header is not defined yet", dan "There is input binded by column, but column type and overrided type is not match". Saran ejaan yang dipakai di dokumentasi (aplikasi akan mengikuti): "The selected column and its header do not match", "There is a layout bound by a pivot, but the pivot is not defined yet", "There is an input bound by a column, but the header is not defined yet", dan "There is an input bound by a column, but the column type and the Format Type do not match". "Overrided type" adalah Format Type di Attributes. Pesan tidak menghalangi Save maupun Publish. Kunci internal checker tidak terlihat pengguna dan tidak boleh disertakan di dokumentasi. Mengganti Table pada Layout menghasilkan pesan header belum ditentukan atau kolom dan header tidak cocok pada Elemen input di dalamnya.
*   **Penamaan pada screenshot Form** (Table "Pesanan", Column "Pemesan") adalah kasus pribadi dan tidak disebut di dokumentasi.
*   **Layout Panel:** ikon kecil di bawah Elemen yang difokuskan membuka Layout Panel.
*   **Submission List:** panah di kiri baris membuka rincian submission (data yang ditambahkan, ID, atau error); pencarian mencakup ID dan Name.
*   **Belum terkonfirmasi:** pilihan Format Type selain String, nilai awal Label dan Default State pada Accordion, cara men-toggle header Accordion, apakah Elemen di Accordion Collapsed tetap tersimpan saat submit, arti visual tampilan penuh pada Full, urutan atas-bawah Split di mobile, tampilan daftar Children pada Split, fungsi ikon `T` pada toolbar Text, apakah Text ikut dikirim sebagai Submission, tampilan Elemen saat Enable = false, nilai awal Visible pada Elemen layout dan display, apakah Default Value Elemen yang tersembunyi ikut tersimpan, daftar operator dan fungsi expression, apakah bintang muncul saat As Title bernilai Yes, apakah hanya satu Elemen per Form yang boleh As Title Yes, tampilan title di Submission List, letak tampil pesan binding checker, nama resmi ikon saklar dan kolom isian expression, bentuk pesan checker expression, umpan balik saat Required belum terisi, perilaku Required pada Elemen Readonly, dan rencana Validators lain.

## Canvas (Modul Interface)

*   **Definisi:** Canvas adalah komponen modul Interface untuk menyusun, menghubungkan, dan memetakan data atau presentasi secara visual. Memberi fleksibilitas membuat diagram, tabel, maupun proyeksi tanpa dibatasi struktur baris dan kolom.
*   **Path:** `Docs/Modul Interface/Canvas/Apa itu Canvas` (dikonfirmasi). Seluruh isi ditulis lengkap di halaman yang sama.
*   **Widget:** Text, Chart Pie, Chart Line, Chart Bar, Chart Radial, Chart Linear, Table, Kanban, Gantt, Timeline, Gallery, Space, Button. **Nama widget ditulis Title Case dengan spasi**; slug (`chart_pie`, dst.) hanya informasi data key di kode dan tidak dipakai di dokumentasi. Pengelompokan di halaman: Teks, Grafik, Tampilan data, Aksi (disetujui penulis).
*   **Halaman widget:** `Docs/Modul Interface/Form/Widget/<Nama Widget>/Penjelasan` (contoh `Chart Pie`). Keunikan setiap widget dijelaskan di sana, bukan di halaman Apa itu Canvas. Semua widget akan punya halaman sendiri.
*   **Widget versi lite:** beberapa widget bekerja seperti komponen Interface lain dalam versi lite. Contoh penulis: komponen Timeline punya Event dan banyak data, sedangkan widget Timeline pada Canvas hanya menyajikan satu data. Pemetaan widget lain belum terkonfirmasi.
*   **Query pada widget:** diatur lewat tombol Q (Edit Mode). **Isi widget = data hasil Query, tidak dapat dimanipulasi dari Canvas.**
*   **Button:** dapat memicu Flow (Flow Block Event yang menerima adalah **Pulser**) atau membuka komponen apa pun. Button pada Canvas yang dipublikasikan dapat dipakai publik, sehingga developer harus berhati-hati.
*   **Layout:** Canvas hanya punya **satu jenis Layout**, tetapi Layout dapat ditambahkan di dalam Layout lain (bertingkat). Tipe horizontal atau vertical diubah lewat toggle di **header toolbar** Layout. Styling memakai layout dan styling yang tersedia (design toolbar, `Docs/Styling/Styling Class`).
*   **Template:** gabungan banyak widget yang sudah didesain dan siap pakai, ditambahkan lewat `/template`. Akan dijelaskan di halaman sendiri (usulan `Docs/Modul Interface/Canvas/Template`).
*   **Dialog Create Canvas** (`add-canvas.png`): baris Name berisi bagian kiri tanda `/` (folder tujuan, **terisi otomatis sesuai folder yang diklik kanan dan dapat dikosongkan sehingga berada di root**) dan kolom Name, lalu Description, tombol Cancel dan Create. Jalur menu: Add ➜ Interface ➜ Canvas. Canvas baru terbuka di View Mode.
*   **Mengubah:** tombol Edit mengubah atribut Canvas (Name dan Description), lalu Update, seperti komponen lain. **Tidak sama dengan toggle mode.**
*   **Mode:** toggle `mode` berpindah antara **View** dan **Edit**. View Mode = read only (ketika bukan Edit Mode). Pesan "preview mode" dan "Editing has been disabled" muncul karena mode, bukan karena akses.
*   **Data Access Canvas:** **Add = menambahkan widget, Update = mengubah Query, atribut, atau styling widget, Delete = menghapus widget.** Jika salah satu bernilai allow, toggle Edit Mode dapat dipindahkan. Jika ketiganya disallow, tidak dapat. Data Access = setiap perubahan Widget dan atributnya di dalam Canvas.
*   **Save:** tombol Save aktif ketika ada perubahan. Dapat ditekan manual atau menunggu sekitar 3 detik (*auto save*). **Refresh tidak dapat dilakukan ketika sedang saving.**
*   **Halaman kerja** (`interface-canvas.png` View Mode, `edit-canvas.png` Edit Mode): bilah navigasi berisi judul (**ikon Canvas** dan Header Name; "2D" adalah ikon interface Canvas), Edit, Publish, toggle mode, Save, Refresh. Tidak ada kolom pencarian. **Tidak ada perbedaan desktop dan mobile.**
    *   **View Mode, Canvas kosong:** "<Header Name> is Empty", "This canvas is in preview mode and cannot be edited.", badge "Read Only", "Editing has been disabled for this canvas."
    *   **Edit Mode, Canvas kosong:** "Start Building Canvas <Header Name>", "Add your first layout or widget to begin designing your interface.", field "Type something here to add...", daftar "Try:" `/layout` (Search Layout), `/template` (Search Template), `/chart` (Search chart), `/text` (Add text), `/table` (Add table).
    *   **Menambah:** ketik di field lalu pilih dari **dropdown**. Semua widget lain juga muncul di dropdown.
*   **Interaksi Edit Mode:** klik kiri widget untuk fokus. **Setiap aksi select pada widget menampilkan header toolbar dan design toolbar.**
*   **Toolbar** (`toolbar-canvas.png`, contoh Chart Pie):
    *   *Header toolbar (unik per widget):* ikon jenis widget, **ikon pegangan ⋮⋮ untuk memindahkan widget ke posisi atau Layout lain**, Data (Table sumber), tombol Q, Limit, **Remove (menghapus widget)**.
    *   *Design toolbar, panel tata letak (sama di semua widget):* min. (w dan h, persen), padding dan margin (4 sisi), ikon perbesar.
    *   *Design toolbar, panel tampilan (unik per widget):* pada Chart Pie: hole, gap, theme, gradient, offset, label, min, legends, total, size.
*   **Publish:** modal konfigurasi untuk mengubah Canvas menjadi dipublikasikan. **Hanya dua kolom: Status (Active atau Non-Active) dan Link (dibuat otomatis; link, copy, open new tab).** Link dapat dibuka **publik, hanya View Mode**. Non-Active: tautan tidak dapat dibuka karena Canvas tidak dalam status dipublikasikan. Label tombol penyimpan di modal belum terkonfirmasi.
*   **Binding:** dikonfigurasikan melalui tombol Binding (ikon `setting`, diasumsikan), berupa modal. **Pada bagian nilai Query (misalnya Filter) dapat diisi dengan key Binding; saat parameter Canvas berubah, nilai Query ikut berubah.** Canvas dapat dibuka dengan parameter lewat tautan Publish, Button yang sudah disetup, atau komponen lain yang dapat memanggil Canvas dengan parameter. Contoh di dokumentasi harus generik (nomor pesanan, bukan inisial). **Baru tersedia di rilis selanjutnya**, belum ada di screenshot.
*   **Modal Binding:** tabel dengan kolom Name (harus unik), Format dan Header (hanya pada format tertentu, mirip konfigurasi Column di Table; **Header bernilai N/A bila Format tidak membutuhkannya**), Default Value (nilai bawaan ketika parameter tidak ditentukan).
*   **Menghapus Canvas:** hanya menghapus template dan properti termasuk Query. Data sumber aman. Tautan yang sudah dishare menjadi tidak valid.
*   **Hak akses:** mengikuti Comp. Access, Data Access, dan Function Access (View Publish dan Publish) seperti komponen lain. View Publish hanya menyalin atau membuka Link tanpa mengubah Status.
*   **Belum terkonfirmasi:** apakah Layout dan Template mengikuti Data Access Add, Update, Delete yang sama dengan widget, widget lain yang tergolong "versi lite", label tombol penyimpan di modal Publish, tombol di modal Binding, dan letak tombol Binding pada bilah navigasi.
*   **Penamaan pada screenshot** (nama Canvas "Test", nama Data pada Chart Pie, serta nama dan nilai pada grafik) adalah kasus pribadi dan tidak disebut di dokumentasi.

## Widget Canvas (struktur halaman)

*   **Path:** `Docs/Modul Interface/Form/Widget/<Nama Widget>/Penjelasan`, nama folder Title Case (`Table`, `Chart Pie`). **Penulis menyebut halamannya "Widget Table" dan "Widget Pie".** Draf memakai judul "Widget Chart Pie" mengikuti keputusan nama widget sebelumnya (Chart Pie). Mohon konfirmasi.
*   **Struktur** akan diikuti widget lain (Text, Chart Line, Chart Bar, Chart Radial, Chart Linear, Kanban, Gantt, Timeline, Gallery, Space, Button).
*   **Panel tata letak** sama di semua widget: min. (w, h persen), tombol Expand (ikon panah diagonal, fungsi belum terkonfirmasi), padding dan margin (4 sisi), panah ▼ di sisi kiri panel.

## Widget Table

*   **Definisi:** menampilkan data Table sebagai tabel di Canvas. Versi lite Table View: hanya satu data, tanpa kolom Action, tanpa Add Row, isi tidak dapat dimanipulasi.
*   **Header toolbar** (`interface-widget-table.png`): ikon Table (jenis widget), ikon pegangan ⋮⋮ (memindahkan), ikon tabel kecil di kiri tombol 123 (**belum dijelaskan**), tombol **123 = toggle pagination**, tombol **kaca pembesar = toggle toolbar search**, Data (ikon Table dan nama Table), tombol Q, Remove. Toggle aktif ditandai latar berwarna.
*   **Design toolbar:** hanya panel tata letak (tidak ada panel tampilan pada screenshot). Pada screenshot min. w 0% dan h 40%, Expand aktif.
*   **Tampilan:** toolbar search di atas (tombol **Refresh List**, kolom **Search Data...**), tabel (kolom ID, kolom hasil Query dengan ikon tipe data di samping nama, cell kosong menampilkan "Empty"), pagination di bawah ("Show 50 of 8 items, on page", input nomor halaman, Go, Prev, nomor halaman, Next). 50 adalah batas data per halaman.
*   **Query:** diatur lewat Q. Kaidah (**asumsi: Table Output**, belum terkonfirmasi).
*   **Belum terkonfirmasi:** fungsi ikon tabel di kiri 123, fungsi Expand, cakupan Search Data..., apakah search dan pagination tampil di View Mode dan tautan Publish, perilaku Refresh List, kaidah Query, cara memilih Data, tampilan sebelum Data dipilih.

## Widget Chart Pie

*   **Definisi:** menampilkan data Table sebagai diagram pie di Canvas.
*   **Header toolbar** (`interface-widget-chart-pie.png`): ikon pie (jenis widget), ikon pegangan ⋮⋮, **Data (input Query dengan kaidah Series Output; ikon Table dan nama Table)**, tombol Q, **Limit = jumlah maksimal data yang muncul** (menampilkan "Empty" bila belum diisi), Remove.
*   **Design toolbar:** dua panel. Panel tata letak (sama di semua widget) dan **panel tampilan** (ikon palet, ▼, serta satu ikon di sisi kanan baris hole dan gap yang belum dijelaskan).
*   **Panel tampilan (penjelasan penulis):**
    *   **hole:** berapa lubang pada pie (persen, contoh 45%)
    *   **gap:** gap antar data (contoh 6)
    *   **theme:** tema warna (dropdown, contoh `fun`)
    *   **gradient:** gradasi warna dari tengah ke pinggir (transparent to color), persen (contoh 0%)
    *   **offset:** batas akhir gradasi. Jika 75%, gradasi dari tengah sampai sekitar 75% ke ujung lingkaran (contoh 0%)
    *   **label:** label dalam pie. Pilihan: `none`, `label`, `value`, `percent`, `all` (label - value). Contoh `none`
    *   **min:** derajat minimum pie untuk menampilkan label (contoh 20)
    *   **legends:** posisi legenda. Pilihan: `right`, `bottom`, `hidden` (contoh `right`)
    *   **total:** toggle, menampilkan total di tengah (contoh aktif, Σ)
    *   **size:** font size dari tampilan total di tengah (contoh 22)
*   **Tampilan:** irisan per data, total di tengah, legenda "label (persen)".
*   **Belum terkonfirmasi:** definisi kaidah **Series Output** (anchor `Docs/Tipe Data/Query#Series Output`: kolom, contoh, Error), satuan gap dan size, arti nilai persen gradient, daftar theme, apakah `all` memuat percent, arti Limit kosong, ikon tanpa nama pada panel tampilan, cara memilih Data.
*   **Penamaan pada screenshot** (Table "Pesanan" dan "Barang pesanan", nama barang dan kolom) adalah data pribadi dan tidak disebut di dokumentasi.

## Space (Modul Interface)

*   **Definisi:** Space adalah komponen modul Interface yang menaungi dan mengorganisasi data dalam bentuk 3D (tiga dimensi). Data dan hubungan antar data divisualisasikan dalam ruang tiga dimensi dan dapat dijelajahi dari berbagai sudut pandang, sehingga pola dan keterkaitan yang sulit terlihat pada tampilan tabel menjadi lebih mudah dipahami.
*   **Path dan struktur:** `Docs/Modul Interface/Space/Apa itu Space`. **Seluruh isi Weather, Environment, dan Object ditulis lengkap di halaman ini, tanpa subhalaman**, ditautkan lewat anchor (`#Mengelola Weather`, `#Mengelola Environment`, `#Mengelola Object`, `#Mengatur Model Attribute`, `#Panel Properti`, `#Hak Akses Space`).
*   **Dialog Create Space** (`add-space.png`): Name (bagian kiri tanda `/` = folder tujuan, tampil "root", boleh dikosongkan; lalu kolom Name) dan Description, tombol Cancel dan Create. Slug ikon menu: `space`.
*   **Halaman kerja** (`interface-space.png`): bilah navigasi (ikon Space dan Header Name, Edit, Refresh, "Search Space Data...") dan area kerja: view 3D (grid lantai, penanda sumbu di titik pusat: **x merah, y hijau, z biru**), panel **Outliner** di kiri (kelompok Weather, Environment, Object, angka = jumlah data, panah membuka/menutup daftar), dan panel properti di kanan ("No selection" bila tidak ada data yang difokuskan). Judul Space dan folder pada screenshot adalah kasus pribadi, tidak disebut di dokumentasi.
*   **Edit** hanya mengubah Name dan Description. **Search Space Data...** mencari data di Outliner berdasarkan Name, termasuk data milik Object yang banyak.
*   **Menambah dan menghapus data:** klik kanan pada panel Outliner membuka menu **Add Weather, Add Environment, Add Object**. Data yang sudah ada punya menu **Delete** dan **Edit**. Modal Edit Object berisi isian yang sama dengan Add dan **semua atribut bisa diubah** (Origin hanya bisa diubah lewat Edit).
*   **Fokus data:** klik data pada Outliner, atau klik langsung objek pada view 3D (keduanya bisa).
*   **Interaksi view 3D:** klik kiri memutar, Shift + klik kiri menggeser, wheel zoom, mobile memakai gestur sentuh standar (sudah dikonfirmasi penulis: satu jari memutar, dua jari menggeser, cubit untuk zoom). Data yang difokuskan punya alat bantu pemindah, **belum ada pergantian mode**. Memindahkan objek 3D Object dengan alat bantu **memperbarui Row sumber jika atributnya bind**. **Environment tidak bisa dipindahkan dengan alat bantu**, hanya lewat panel properti. Dokumentasi menjelaskan perilaku sesuai halaman kerja Phoenix, **tanpa menyebut nama pustaka atau kontrol 3D yang mendasarinya.**
*   **Tiga jenis data:**
    *   **Weather:** tampil sebagai *world effect* (berlaku pada seluruh ruang). Atribut: Priority [Number], Name [String], Description [String], **Type** (label field berbahasa Inggris, bukan "Jenis"), Status [Boolean]. Pilihan Type (titlecase): **Earth Sky** (properti Time [DateTime / DateTimeZone]) dan **Sea** (properti Level [Number] dan Wave Rate [Number]). Jika ada banyak Weather dengan Type yang sama, yang menang adalah **Priority terkecil dengan Status true**. Setiap properti punya **toggle** pada field nilainya untuk memilih nilai langsung atau Query **kaidah Single Output** (hasil kalkulasi).
    *   **Environment:** objek **statis tanpa logika**, pengguna cukup meng-upload file 3D. Atribut: Name, Description, Position (3D Vector), Scale (Volume Unit, 3 nilai x, y, z), Rotation (Euler Angle), Model (**upload file 3D**, bukan komponen Model). File 3D **ikut terhapus** saat Environment dihapus.
    *   **Object:** berlogika kompleks, disiapkan di **komponen Model modul Developer**. Atribut: Name, Description, Origin (3D Vector), Model (**komponen Model**, tipe data Model), Query **kaidah Table Output** (data riil). **Origin** = titik asal tiap Row, berfungsi sebagai *anchor* untuk merender model, **tidak memengaruhi Row**, dan hanya bisa diubah lewat klik kanan > Edit di Outliner. Tombol **Q** hanya ada di modal Object (tidak tampil langsung di antarmuka seperti Table View). Saat Query diisi tampil tabel **Model Attribute** (kolom **Key, Static, Value**). **Static dan bind adalah radio:** static = Value bebas dan sama untuk semua objek 3D yang dirender (contoh: atribut `on` pada model lampu diubah ke true, semua lampu menyala), bind = pilih kolom Query (berbeda tiap Row). **Daftar Key disiapkan di komponen Model.** Satu Object dapat menghasilkan banyak objek 3D (sebanyak Row hasil Query). Dihapus: Row sumber tidak ikut terhapus.
*   **Panel properti:** tidak ada tombol simpan, **perubahan langsung diterapkan** (field teks ada debounce sekitar 300 ms, toggle dan option seketika). **Perubahan memengaruhi Row sumber hanya pada Object.** Perubahan pada Weather dan Environment hanya mengubah konfigurasi data di Space. Pengaruh ke sumber tetap mengikuti Data Access sumber.
*   **Hak akses:** satu Data Access Space mewakili semua kategori (Weather, Environment, Object). Add = Add Weather/Environment/Object, Update = mengubah nilai, Delete = menghapus data.
*   **Dampak hapus Space:** seluruh data dan konfigurasi Space hilang, Row sumber tidak terhapus.
*   **Halaman yang akan ditambahkan penulis:** tipe data **Model** (`Docs/Tipe Data/Model`) dan format data **Euler Angle** (`Docs/Format Data/Complex/Euler Angle`).
*   **Belum terkonfirmasi:** arti Level dan Wave Rate, serta tipe data atau format data untuk field upload Model pada Environment (dan format file 3D yang didukung).