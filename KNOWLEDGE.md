---
name: phoenix-docs-knowledge
pageDecoration:
  icon: info
description: knowledge-base phoenix untuk AI Agent selama membuat dokumentasi phoenix.
---

# Konsep Dasar: Pro, Folder, Komponen

- **Path:** `Docs/Dasar/Apa itu Pro`, `Docs/Dasar/Apa itu Folder`, `Docs/Dasar/Apa itu Komponen`. Judul memakai tanda tanya, path tidak. Halaman Dasar tidak memiliki Contoh Penggunaan (contoh ada di halaman rinci tiap komponen).
- **Hubungan:** Pro adalah wadah, Folder menata, Komponen menjadi isi.
- **Pro:**
  - Definisi "wadah utama" sudah benar menurut penulis.
  - Saat dimulai otomatis ada Group Administrator, Workspace Origin, dan komponen Variable. Pengguna baru memperoleh akses penuh (Administrator terhubung ke Origin yang seluruhnya allow). Terkonfirmasi.
  - Halaman Inisialisasi (`Inisialisasi/Pengenalan`) dan halaman pengenalan modul, Tipe Data, Format Data, serta Antarmuka sudah ada.
- **Folder:**
  - Menu klik kanan di Area Manajemen Folder: **New Folder** (membuat folder, isian Name, tombol Create) dan **Rename** (mengubah nama, tombol Update). Menu komponen tetap Add ➜ Modul ➜ Komponen.
  - Memindahkan folder atau komponen juga bisa di Area Manajemen Folder dengan menyalakan **toggle Move** di bagian atas, selain di halaman kerja Workspace.
  - **Relasi komponen tetap terhubung** setelah dipindahkan.
  - Tidak ada pembatasan jenis komponen per folder.
  - Pemindahan komponen tidak mengubah isi dan fungsinya.
  - Memindahkan ke folder *root* di Area Manajemen Folder: seret ke barisan di level root (menyisipkan di antara komponen atau folder yang sudah ada) atau ke bagian kosong, biasanya di bawah kolom manajemen folder.
  - Dampak hapus folder: isi folder terdampak (komponen dan folder di dalamnya) dan **penghapusan folder beserta isinya tidak dapat dikembalikan**.
  - Penulisan toggle Move: `[[^field/move]]`.
  - Rekomendasi pola penataan folder (per area bisnis, per tim, per sistem, per jenis komponen, arsip, dan folder "Bersama") sudah disetujui penulis.
  - Belum terkonfirmasi: apakah toggle Move perlu dimatikan setelah memindahkan, dan cara memindahkan ke root di halaman kerja Workspace.
- **Komponen:**
  - Daftar komponen Interface sudah lengkap (Table View, Gallery, Kanban, Timeline, Canvas, Space, Form). Gantt belum ada sebagai komponen.
  - Definisi Form sudah benar. Model: komponen kompleks yang menyimpan konfigurasi aset 3D beserta animasi dan logikanya. Definisi lengkap akan ditulis penulis di halaman Model.
  - Label modul pada menu Add: Data, Interface, Logic, Developer.
  - Kolom pencarian bilah navigasi berpola `Search <Nama Komponen> Data...`. Tombol Submission juga ada pada Form.
  - **Penghapusan komponen saat ini tidak dapat dikembalikan.**
  - Dampak hapus Timeline: hanya konfigurasi hilang, data sumber aman. Dampak hapus Model: seluruh data yang tersimpan di Model hilang dan Space Object yang memakai Model tersebut ikut terdampak. Row sumber Kanban dan Gallery tidak terhapus.
  - Event dari komponen Data dijelaskan di `Docs/Modul Data/<Komponen>/Mengotomasi`.

# Group (Modul Developer)

*   **Definisi (versi penulis):** Group adalah komponen untuk mengatur komposisi tim dan akses Workspace yang diberikan kepada setiap anggota. Akses tidak diatur per orang, melainkan anggota dikelompokkan ke Group lalu ditentukan Workspace yang dapat diakses Group tersebut.
*   **Path:** `Docs/Modul Developer/Group/Apa itu Group`. Gambar: `add-group.png` (dialog Create Group) dan `interface-group.png` (halaman kerja). Slug komponen: `group`.
*   **Dialog Create Group** (`add-group.png`): baris Name berisi bagian kiri tanda `/` (tampil "root", **terkonfirmasi sebagai direktori tujuan**), kolom Name, Description, Parent (Select...), tombol Cancel dan Create.
*   **Dua pintu pembuatan:**
    *   **Area Manajemen Folder** (klik kanan > Add > Developer > Group): menambahkan Group sebagai komponen di folder, **Parent wajib diisi**.
    *   **Halaman kerja Group (tombol Add Group):** form sama tanpa bagian direktori, **Parent terisi otomatis** dengan Group tempat tombol diklik, dan Group tidak otomatis menjadi komponen di folder.
*   **Tombol Add Group** ada di bagian akhir **setiap** Group (setelah daftar anaknya) saat Group dibuka (expand).
*   **Group berstatus default:** saat inisiasi Pro baru, otomatis ada Group bernama **Administrator** yang menjadi default. User baru ditempatkan sistem ke sini.
*   **Aturan keanggotaan:** **satu User hanya dapat berada dalam satu Group.** Memindahkan User dengan *drag and drop* dari Group lama ke Group tujuan.
*   **Pewarisan:** **Group anak tidak mewarisi Workspace dari Group induk.** Workspace harus diisi ulang di setiap Group.
*   **Halaman kerja:** bilah navigasi berisi judul (ikon Group dan Header Name), Edit, Refresh, dan kolom "Search Group Data..." (**mencari nama dan deskripsi Group saja**). Tidak ada perbedaan desktop dan mobile pada bilah navigasi. Area kerja menampilkan Group beserta Group anak bertingkat; setiap Group memiliki judul, deskripsi, kolom Workspace (kiri), dan kolom User (kanan). Pesan kolom User kosong: "(User Is Empty)". Panah di kiri judul Group membuka dan menutup daftar anak.
*   **Edit:** tombol Edit pada header hanya mengubah Name dan Description. Menu Edit pada Group anak berbeda (atribut yang dapat diubah belum terkonfirmasi).
*   **Menu konteks Group anak (klik kanan):** Edit, Add Children, Place to Directory, Delete.
    *   **Place to Directory:** menempatkan Group anak (yang juga komponen) ke Area Manajemen Folder di **root dari Workspace yang aktif saat itu**. Ada dialog konfirmasi (label dan isi belum terkonfirmasi).
*   **Workspace pada Group:** tambah lewat kolom "Search workspace to add..." lalu pilih (otomatis masuk daftar). Hapus dengan klik Workspace pada daftar lalu konfirmasi **Remove**.
*   **Menghapus Group:** yang hilang hanya daftar Workspace-nya. **Group anak ikut terhapus, dan Group yang dihapus (beserta anaknya) tidak boleh masih memiliki User**, jadi semua User harus dipindahkan dulu.
*   **Belum terkonfirmasi:** atribut yang dapat diubah lewat Edit Group anak, label dan isi dialog Place to Directory, apakah status default dapat dipindahkan ke Group lain, tombol konfirmasi hapus Group anak (diasumsikan Delete), dan apakah Parent pada Add Children terisi otomatis.
*   **Penamaan pada screenshot** (nama Group anak, Workspace, dan User) adalah kasus pribadi dan tidak disebut di dokumentasi. Group Administrator adalah bawaan sistem sehingga boleh disebut.
  
# Workspace (Modul Developer)

- Workspace adalah komponen untuk mengatur ruang kerja pengembangan: komponen yang dapat dilihat, dikelola, dan diubah, serta **fungsi di dalamnya**. Pada kalimat pembuka halaman, nama "Workspace" ditulis biasa, tanpa huruf miring. Istilah umum "field" (bukan label antarmuka) ditulis miring: *field*.
- **Empat halaman:** `Docs/Modul Developer/Workspace/Apa itu Workspace` (halaman utama, memuat ringkasan), serta tiga subhalaman terpisah **tanpa "Apa itu"** pada judulnya: `Docs/Modul Developer/Workspace/Data Access`, `Docs/Modul Developer/Workspace/Component Access`, dan `Docs/Modul Developer/Workspace/Function Access`. Halaman utama hanya memuat definisi, tabel hak akses singkat, dan tautan ke subhalaman. Gambar halaman kerja bernama `antarmuka-workspace.png` (bukan `interface-workspace.png`) di folder `Docs/Modul Developer/Workspace/`.
- **Anchor penting:** Data Access: `#Data yang Diatur pada Setiap Komponen`, `#Akses Berlapis pada Komponen Interface`. Component Access: `#Visible pada Folder dan Komponen`, `#Memindahkan Folder atau Komponen`, `#Mengenali Ikon Kunci`. Function Access: `#Publish dan View Publish`.
- Akses Workspace ke anggota dikelola lewat Group. Satu pengguna hanya di satu Group. Group anak tidak mewarisi Workspace dari Group induk. Satu Group dapat memiliki beberapa Workspace.
- **Workspace aktif:** saat membuka Phoenix, pengguna masuk ke Workspace yang **terakhir dipakai**. Jika Workspace itu sudah tidak valid (misalnya Workspace pada Group berubah), pengguna otomatis dipindahkan ke Workspace **pertama pada daftar Group**. Pengguna berpindah Workspace lewat tombol berisi nama Workspace aktif di Area Manajemen Folder (`Docs/Antarmuka#Area Manajemen Folder`), yang membuka popup ganti Workspace berisi Workspace yang dipetakan ke Group pengguna. Place to Directory pada Group anak memakai root dari Workspace aktif.
- **Origin:** Workspace pertama dan bawaan di setiap Pro, seluruh hak aksesnya **allow**, dan otomatis terhubung ke Group bawaan **Administrator** (bukan "Administration"). Jika komponen Workspace ditempatkan di folder yang lebih dalam, folder itu menjadi root.
- **Relasi (diagram penulis):** Pengguna → Group → Workspace → Folder dan Komponen; Folder berisi Komponen; Folder dan Komponen punya Component Access; hanya Komponen yang punya Data Access (folder tidak menyimpan data); Function Access putus-putus karena hanya ada pada komponen yang memiliki fungsi terkait.
- **Membuat:** buka folder di Area Manajemen Folder, klik kanan ➜ Add ➜ Developer ➜ Workspace, isi Name dan Description, klik Create. **Nilai awal hak akses mengikuti Workspace yang aktif saat Workspace dibuat.** Workspace baru belum dapat dipakai anggota sampai dipetakan ke Group.
- **Mengubah:** tombol Edit hanya mengubah atribut Workspace (Name, Description), bukan hak akses.
- **Menghapus:** klik kanan Workspace ➜ Delete, lalu konfirmasi dengan Delete. Pengaturan akses ikut hilang dan pemetaan pada Group terputus, tetapi komponen dan data tidak terhapus. Pastikan setiap Group masih memiliki Workspace lain. **Sistem mencegah penghapusan Workspace root jika setelahnya tidak ada Workspace di posisi root yang terhubung ke Group**, sehingga Origin tidak dapat dihapus selama belum ada Workspace root lain yang terhubung ke Group.
- Bilah navigasi Workspace hanya memiliki Edit dan Refresh. Tidak ada perbedaan tampilan desktop dan mobile.
- **Halaman kerja:**
  - Kolom kiri: Folder/ Component. Kolom kanan: Component Access, Data Access, Function Access. Setiap sel memiliki **tombol toggle** allow atau disallow. Data Access memiliki tiga kolom: Add, Update, Delete.
  - **Perubahan toggle tersimpan langsung dan langsung berlaku** bagi anggota yang sedang membuka Phoenix, tanpa muat ulang.
  - Baris Group (Administrator) hanya mengatur akses dari Workspace ke komponen Group tersebut, bukan akses per anggota.
  - Sel kosong berarti akses tidak relevan untuk komponen tersebut.
  - Klik folder untuk memperluas atau melipat. **Drag and drop** memindahkan folder **dan** komponen, baik mengubah urutan maupun ke folder lain.
  - **Pemindahan mengubah struktur folder Pro** (struktur folder Pro dan Workspace saling berkesinambungan), bukan hanya tampilan halaman kerja.
- **Hak akses yang disallow (efek di antarmuka):** fungsi terkait **hilang**: tombol hilang dan menu pada konteks menu hilang. Pada halaman komponen muncul **ikon kunci di samping judul (nama komponen)**; saat di-hover muncul popup tooltip berisi hak akses apa saja yang diizinkan oleh Workspace. **[asumsi]** Ikon hanya muncul jika ada hak akses yang disallow, dan tooltip memuat ketiga jenis hak akses. **[asumsi]** Add = menu Add pada konteks menu folder, Update = tombol Edit, Delete = menu Delete.
- **Component Access:**
  - **Visible:** pada komponen, disallow = komponen tidak tampil di Area Manajemen Folder dan tidak tampil dalam *field* (Query, membuat komponen Interface). Pada folder, disallow = folder beserta isinya tidak tampil di Area Manajemen Folder.
  - **Add:** penambahan folder atau komponen baru, **termasuk menempatkan folder atau komponen dari folder lain**. **[asumsi]** Add hanya ada pada baris folder.
  - **Update:** perubahan atribut pada folder atau komponen.
  - **Delete:** penghapusan folder atau komponen, **termasuk memindahkannya ke folder lain**. Folder tujuan harus mengizinkan Component Access Add.
  - **Memindahkan ke folder lain: Delete pada yang dipindahkan + Add pada folder tujuan.** Akibatnya, anggota yang boleh memindahkan ke folder lain juga boleh menghapus komponen itu. **Mengubah urutan di dalam folder yang sama tidak memerlukan Add maupun Delete.** **[asumsi]** Tidak memerlukan Update juga.
  - Penafsiran lama "Update pada folder = memindahkan komponen di dalam folder" **salah dan sudah dihapus**.
- **Visible tidak berjenjang:** folder disallow membuat isinya tidak tampil di Area Manajemen Folder (tidak dapat dibuka), tetapi komponen dengan Visible allow **tetap muncul pada pilihan *field* atau Query** (misalnya memilih data Table). Untuk menutup komponen sepenuhnya, Visible komponen itu sendiri harus disallow. Jangan menulis "hak akses berjenjang" atau "pewarisan akses".
- **Variable:** jika Visible komponen Variable disallow, halaman Variable tidak dapat dibuka (Value tidak terlihat) dan komponen Variable tidak dapat dipilih saat Query, tetapi **daftar Variable Data tetap muncul dan dapat dipilih** untuk otomasi atau integrasi.
- **Data Access:** Add, Update, Delete pada level data. Jenis data: **Table: Row dan TableData; Table View: Table View Data (hanya pengelolaan Data: nama, Query, konfigurasi, bukan Row atau cell); Timeline: Timeline Data**. Enum: EnumData, Tree: Node, Variable: Variable Data, Flow: Flow Block. Canvas: widget (Add = tambah, Update = ubah Query/atribut/styling, Delete = hapus). Form: Elemen dan atributnya. Space: satu Data Access untuk Weather, Environment, Object. Kanban dan Gallery: **kartu adalah data level Row/EnumData sehingga mengikuti Data Access sumber; template kartu mengikuti Data Access komponen Kanban atau Gallery.** Halaman Data Access memuat diagram efek Add, Update, Delete per kelompok komponen (bukan gambar kolom). **[asumsi]** Add dan Delete pada Table View dan Timeline berarti menambah dan menghapus Data, dan template kartu hanya terkait Update.
- **Akses berlapis:** baris dan isi sel di komponen Interface hanya dapat dikelola jika Data `editable` **dan** Data Access data sumber mengizinkan. Visible komponen sumber hanya dibutuhkan saat **mengisi Query**; setelah Query terisi tidak perlu lagi allow. Mode Edit Canvas dan Form hanya dapat dipakai jika salah satu Data Access allow (aturannya sama untuk keduanya).
- **Function Access:** Merge, Modify Event (termasuk tombol Event untuk menghubungkan Flow Block Event), View Publish (melihat konfigurasi, menyalin atau membuka Publish Link tanpa mengubah status), Publish. Komponen yang memilikinya: Merge = Table, Enum. Event = Table, Enum, Tree, Timeline Event. Publish = Table, Tree, Canvas, Form. Function Access tidak bergantung pada Data Access maupun Component Access. **[asumsi]** Tombol yang hilang saat disallow adalah Merge, Publish, dan Event.
- **Keamanan:** tautan Publish dapat dibuka publik. Pada Canvas, widget Button yang memicu Flow dapat dipakai publik. Pengisi Form dan pengunjung tautan publik **tidak dibatasi** Workspace.
- **Tidak ada pengaman bawaan** untuk pengaturan hak akses: menonaktifkan Visible atau Update pada komponen Workspace dan Group yang dipakai administrator dapat mengunci pengelolaan akses. Satu-satunya pengaman adalah larangan menghapus Workspace root terakhir yang terhubung ke Group.
- Nama folder dan komponen pada gambar contoh penulis adalah kasus pribadi dan tidak disebut di dokumentasi. Nama generik (Keuangan, Penjualan, Daftar Pelanggan, Role, Employee, Organizational Structures) sudah diterima penulis.

# Flow (Modul Logic)

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
  - **I/O:** Branch, Passer. **Query:** Condition (Add Table Filter), Execute (Table Output).
  - **Operator:** Number (Increment), String (Concatenate, Implode, Pad Left, Pad Right), Table (TableRow Parse), Object (Assign, Merge, Parse, Stringify), Boolean (If), Tree (Node Parse).
  - **Modular:** API (HTTP Request), AI (OpenAI 4).
  - **Misc.:** Chrono (Delay), Error (Error Message).
- **Menghubungkan block:** klik dan tahan (hold press) pada output, arahkan ke input, lalu lepaskan (release). Output di sisi kanan, input di sisi kiri.
- **Eksekusi manual:** lewat antarmuka Flow, gunakan tombol pada Flow Block Event (misalnya Trigger pada Pulser).
- **Event dari komponen:** Flow Block Event yang sudah dibuat dapat langsung dihubungkan melalui tombol Event pada masing-masing komponen.
- **Memantau proses:** klik tombol Activity/Submission, panel Flow Activity terbuka. Panel memiliki tombol Refresh List, kolom Search Activity, kolom ID/Name, Status/Type, Start At, Updated At, dan menampilkan "No Activity" bila kosong.

## Aturan dasar koneksi dan eksekusi Flow Block
 
* **Satu output hanya dapat terhubung ke satu input.** Batasan ini diatasi dengan Branch Block.
* Urutan eksekusi aliran yang bercabang **sulit diprediksi bila banyak koneksi dari beberapa block bertemu pada satu input** (misalnya menyusun Array dari banyak output). Pada Branch Block sendiri, eksekusi Output mengikuti penomoran. Sebuah block diproses setelah setiap block yang terhubung ke inputnya selesai tereksekusi (`Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`). Passer Block memanfaatkan aturan ini untuk memastikan beberapa aliran selesai atau berurutan.
  
## Flow state pada eksekusi block

*   **Succeed:** block selesai sesuai tujuan.
*   **Abort:** dihasilkan Error Message Block. Menghentikan aliran hanya pada Activity yang sedang berjalan, perubahan data yang sudah dilakukan block sebelumnya di-rollback, dan pesan error tampil di Flow Activity. Berbeda dari Fatal Error.
*   **Error:** block berjalan tetapi hasilnya gagal sebagai kondisi yang dapat ditangani (Name atau Value konflik, EnumData tidak ditemukan, penghapusan ditolak). Pesan error tampil di Flow Activity.
*   **Fatal Error:** block tidak dapat dijalankan karena input wajib kosong (Enum, EnumData, atau Name), semua output tidak ada. Pesan error tampil di Flow Activity.

## Flow Block Event

- **Lima block:** Pulser, Variable Event, Enum Data Event, Table Row Event, Tree Node Event. Semua memiliki satu Control (tombol Trigger, tanpa ikon) dan tidak memiliki input koneksi.
- **Output per block:**
  - Pulser: `Result` (Boolean, selalu `true`).
  - Variable Event: `Variable`, `Event`, `Old`.
  - Enum Data Event: `EnumData`, `Event`, `Old`.
  - Table Row Event: `Row`, `Event`, `Old`.
  - Tree Node Event: `Node`, `Event`, `Old`.
- **Aturan `Event` dan `Old` (Table, Enum, Tree):** `Event` bertipe String (`create`, `update`, `delete`). `Old` bertipe Object. create: Empty. update: hanya field yang diubah (satu field berubah, hanya field itu). delete: seluruh field.
- **Variable Event berbeda:** hanya `update` dan `delete` (tidak ada `create`). `update` hanya terpicu bila Value berubah. `Old` pada update berisi Value sebelumnya (tipe sesuai Type), pada delete berisi seluruh atribut Variable Data. Dihubungkan per Variable Data lewat tombol Event pada baris Variable, atau klik kanan daftar Variable ➜ Setup Event.
- **Field per tipe:** EnumData: Name, Description, Value, Selectable. Node: Name, Order, Parent, Children. Variable Data: Name, Type, Value, Description (Type pada Old delete belum terkonfirmasi).
- **Perilaku pemicu:**
  - Menyimpan Row tanpa perubahan **tidak** memicu Table Row Event. Hal yang sama diterapkan pada Enum dan Tree (belum terkonfirmasi eksplisit).
  - Aksi create, update, atau delete pada data apa pun oleh Flow **tidak memicu Flow kembali**. Import dan Upload tetap memicu `create`. Cakupan (semua Flow atau Flow yang sama) belum terkonfirmasi.
  - `Row` atau `EnumData` pada delete berisi nilai terakhir sebelum dihapus.
- **Tree Node Event:** memindahkan Node ke induk lain menghasilkan `update` hanya pada Node yang dipindahkan (Old berisi Parent lama), bukan pada anaknya. Menghapus Node yang punya anak menghasilkan satu `delete` pada Node itu, dengan Children lengkap di Old. Node hasil clone pada Tree Merger juga memicu Event, sehingga satu perubahan dapat menghasilkan Event di beberapa Tree jika tidak read only.
- **Pulser:** Trigger berulang membuat Activity baru, dan Activity pada Flow yang sama dapat berjalan paralel. Dipicu dari Trigger, Timeline Event (field Pulser Event), atau Widget Button Canvas.
- **Koreksi atas knowledge sebelumnya:** komponen Variable **memiliki** cara menghubungkan Event (tombol Event pada setiap baris Variable, dan Setup Event lewat klik kanan daftar). Halaman cara menghubungkan Event dari komponen bernama `Mengotomasi` (Variable, Table, Enum, Tree).
- **Path:** Timeline Event `Docs/Modul Interface/Timeline/Timeline Event/Pengenalan`, Widget Button `Docs/Modul Interface/Canvas/Widget/Basic/Button`, Syarat Eksekusi `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi`.
- **Belum terkonfirmasi:** bentuk nilai Parent pada `Old` Tree, Type pada `Old` delete Variable, perilaku Trigger manual selain Pulser, fungsi segitiga biru di kiri judul block, dan tipe data yang tepat untuk `Old` Variable Event pada diagram.

## Flow Block Data

- **Struktur dan path:** kategori Data terdiri atas empat kelompok. Halaman Pengenalan: `Docs/Modul Logic/Flow/Flow Block/Data Variable/Pengenalan`, `Data Enum/Pengenalan`, `Data Table/Pengenalan`, `Data Tree/Pengenalan`. Halaman per block: `Docs/Modul Logic/Flow/Flow Block/Data <Grup>/<Nama Block>`. Pola lama `Data/<Grup>/<Nama>` tidak berlaku. Tidak ada halaman `Data/Pengenalan`.

### Flow Block Data Variable

*   **Tidak memiliki Control.** Block hanya memiliki input di kiri dan output di kanan.
*   **Field Variable adalah select option.** Pengguna memilih Variable Data dari daftar (bukan mengetik alias), atau menghubungkannya dari output block lain. Karena itu "Variable tidak valid" tidak mungkin terjadi, tetapi Variable yang dibiarkan kosong menimbulkan error.
*   **Tidak semua output meneruskan aliran Flow** Output yang tidak relevan dengan hasil tidak meneruskan aliran, sehingga block yang terhubung dengannya tidak dieksekusi. Output flag (Is ..., Succeed, Error, Name Conflict) hanya meneruskan aliran dengan nilai Boolean true pada kasusnya, dan tidak meneruskan aliran pada kasus lain.
*   **Output Pass** pada Variable dan Variable Setter meneruskan data yang diinput. Pada kelompok Variable, tipenya Variable.
*   **N/A Type:** teks merah pada input yang tipe datanya belum didefinisikan. Cara mendefinisikan: klik kanan ➜ Change Type ➜ pilih tipe data. Semua tipe data yang tersedia di Phoenix dapat dipilih. Berlaku pada Value (Add Variable) dan New Value (Variable Setter).
*   **Input dan output per block:**
    *   **Add Variable:** input Name, Value (awalnya N/A Type), Description. Output New Variable dan Name Conflict. Name conflict: hanya Name Conflict yang meneruskan aliran (true). Berhasil: hanya New Variable yang meneruskan aliran (Variable Data baru). Name kosong menimbulkan error. Value yang masih N/A Type tetap tersimpan.
    *   **Delete Variable:** input Variable dan Force (Boolean). Output Succeed dan Error: berhasil, hanya Succeed meneruskan aliran (true). Gagal, hanya Error meneruskan aliran (true). Variable Data "sudah digunakan" bila sedang dipakai pada Flow atau data lain (relasi), atau riwayat activity mencatat pemakaiannya (histori). Menghapus Variable Data yang sudah digunakan memerlukan Force true.
    *   **Variable:** input Variable. Output Pass, Name (String), Description (Text), Value (mengikuti Type Variable Data). Variable kosong: tidak ada output yang meneruskan aliran.
    *   **Variable Getter:** input Name (String, alias). Output Variable dan Is Empty. Cocok: hanya Variable yang meneruskan aliran. Tidak cocok: hanya Is Empty yang meneruskan aliran (true). Secara teknis block ini tidak dapat error.
    *   **Variable Setter:** input Variable dan New Value (N/A Type, perlu Change Type; New Value juga memberi Type baru sehingga tidak mungkin terjadi ketidakcocokan tipe). Output Pass. Variable kosong menimbulkan error dan Pass tidak meneruskan aliran.
    *   **Variable Value:** input Variable. Output Value berupa data langsung dengan tipe mengikuti sumber. Tipe output tidak ditampilkan di halaman kerja dan tidak memengaruhi block yang dikoneksikan. Ketidakcocokan dilaporkan di activity saat Flow berjalan. Variable kosong menimbulkan error.
*   **Name Variable Data:** unik, membedakan huruf besar dan kecil, boleh memuat karakter simbol, dan di-trim (spasi, enter, karakter tak terlihat di awal dan akhir dihapus) saat disimpan.
*   **Description Variable Data** bertipe Text. Type Variable Data ditentukan oleh tipe data yang dipilih pada Value.
*   **Is Empty dan Name Conflict** benar-benar tidak meneruskan aliran pada kasus keberhasilan (jawaban sebelumnya menyebut output berawalan Is selalu true atau false dan Name Conflict false saat berhasil)
*   **Output Description atau Value** yang isinya kosong tetap meneruskan aliran
*   **Type Variable Data ikut berubah** saat Variable Setter memperbarui Value (jawaban "New Value juga memberikan new type" dan "hanya Value yang berubah" perlu dipastikan), dan tipe data output Description pada block Variable (Text).

### Flow Block Data Enum

*   **10 block, tanpa Control.** Path: `Docs/Modul Logic/Flow/Flow Block/Data Enum/<Nama Block>`, pengenalan kelompok di `Data Enum/Pengenalan`. Blok: Add EnumData, Delete EnumData, Enum, EnumData, EnumData Getter, EnumData Setter, EnumData Value, EnumData Value Setter, EnumData Header Setter, EnumData Selectable Setter. Pengenalan kelompok perlu memuat ketiga Setter baru.
*   **Konsep output: "tidak ada output".** Output kondisi (Name Conflict, Value Conflict, Succeed, Error, Is Empty) hanya keluar bernilai true saat kondisinya terpenuhi. Pada kondisi lain, tidak ada output (bukan false, bukan empty). Output data (New EnumData, EnumData pada Getter) juga tidak keluar saat gagal.
*   **Input dan output per block:**
    *   **Add EnumData:** input Enum, Name (String), Value (N/A Type), Description (Text), Selectable (Boolean). Output New EnumData, Name Conflict, Value Conflict. Pemeriksaan berurutan Name lalu Value, Value tidak diperiksa bila Name konflik. Value harus bertipe sama dengan Format Enum (tidak ada konversi). Value yang masih N/A Type tetap dapat dieksekusi (EnumData dengan Value N/A Type). Tidak terpengaruh Strict On Selected.
    *   **Delete EnumData:** input EnumData, Force (Boolean). Output Succeed, Error. Force kosong diperlakukan sama dengan false. EnumData kosong: Error true dan error tampil di Flow Activity.
    *   **Enum:** input Enum. Output Pass (Enum), Name (String), Desc (Text). Enum kosong: Fatal Error.
    *   **EnumData:** input EnumData. Output Pass, Name, Description, Value (mengikuti Format Enum), **Selectable (Boolean, ditambahkan)**. EnumData kosong: Fatal Error.
    *   **EnumData Getter:** input Enum, Name (String, alias, sama persis dan membedakan huruf besar dan kecil). Output EnumData (hanya keluar bila ditemukan) dan Is Empty (true hanya bila tidak ditemukan, berstatus Error). Enum atau Name kosong: Fatal Error.
    *   **EnumData Setter:** mengubah **keempat atribut** sekaligus. Input EnumData, Name, Value (N/A Type), Description, Selectable. Output Pass (EnumData), Name Conflict, Value Conflict. Pemeriksaan Name lalu Value.
    *   **EnumData Value Setter:** input EnumData, Value (N/A Type). Output Pass (EnumData), Value Conflict. Value kosong pada tipe yang sesuai berstatus Succeed dan Value menjadi empty. EnumData kosong: Fatal Error.
    *   **EnumData Header Setter:** input EnumData, Name, Description. Output Pass (EnumData), Name Conflict. "Header" = atribut pengenal Name dan Description.
    *   **EnumData Selectable Setter:** input EnumData(s) (beberapa EnumData sekaligus yaitu  Array) dan Selectable (Boolean). Output Pass (Array).
    *   **EnumData Value:** input EnumData, output Value (data langsung, tipe mengikuti sumber). EnumData kosong: Fatal Error.
*   **Name EnumData:** aturan sama dengan Name Variable Data (sama persis, membedakan huruf besar dan kecil, menerima simbol, di-trim).
*   **Koreksi atas knowledge sebelumnya:** (a) Callout warning Strict On Selected pada Add EnumData tidak diperlukan karena Strict On Selected hanya berlaku saat memilih EnumData pada field atau komponen data. (b) Aksi oleh Flow tidak memicu Flow mana pun (semua Flow, bukan hanya Flow yang sama). (c) EnumData Setter mengubah keempat atribut (screenshot awal hanya menampilkan sebagian input).
*   **Selectable kosong pada Add EnumData dan Selectable Setter** akan menghasilkan Fatal Error;
*   **EnumData Setter mengganti keempat atribut sekaligus**, atribut yang tidak ingin diubah harus diisi nilai saat ini.
*   **Name kosong pada Setter adalah Fatal Error**
*   **Description kosong menjadi empty**
*   **Name yang sama dengan Name EnumData itu sendiri bukan konflik**

### Flow Block Data Table

*   **7 block, tanpa Control.** Path: `Docs/Modul Logic/Flow/Flow Block/Data Table/<Nama Block>`, pengenalan kelompok di `Data Table/Pengenalan`. Block: Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, TableData Setter. Semua asumsi pada versi draf sudah **dikonfirmasi benar oleh penulis**.
*   **Input dan output per block:**
    *   **Add Row:** input Table. Output New Row (Row baru kosong, tanpa TableData). Index dibuat otomatis. Table kosong: Fatal Error.
    *   **Delete Row:** input Row dan Force (Boolean, true = hapus paksa yang berdampak pada relasi dan histori yang ada). Berhasil: Succeed true dan Error "-". Gagal: Error true dan Succeed "-". Row atau Force kosong: Fatal Error (berbeda dengan Delete EnumData yang memperlakukan Force kosong sebagai false). Row "sudah digunakan" didefinisikan seperti Variable Data; Force false pada Row yang sudah digunakan menghasilkan Error; TableData ikut terhapus bersama Row.
    *   **Table:** input Table. Output Pass (Table), Name (String), Desc (Text; tetap meneruskan aliran bernilai Empty bila kosong). Table kosong: Fatal Error.
    *   **Table Column:** input Column. Output Pass (Column), Name, Desc, Header, Table. Tipe Header mengikuti tipe data Column (EnumData → Enum, Column → Table, Row → Table, TableData → Column, Node → Tree). Bila Column tidak memiliki Header, Header tetap meneruskan aliran bernilai Empty. Column kosong: Fatal Error.
    *   **Table Row:** input Row. Output Pass (Row), Index (Number, ID Row pada tampilan Table), Table. Row kosong: Fatal Error.
    *   **TableData Getter:** input Column dan Row (Row dapat diganti ke Number atau String berisi Index Row lewat klik kanan ➜ Change Type). Output TableData (Value dari TableData, tipe mengikuti Column) dan Is Empty (true bila TableData kosong atau tidak ditemukan, berstatus Error). Column atau Row kosong: Fatal Error.
    *   **TableData Setter:** input Column, Row (sama seperti Getter), Value (N/A Type sampai tipe ditentukan). Output Pass (Value yang diinput) dan Value Conflict (true bila Value berisi tetapi tipenya tidak sesuai Column, berstatus Error). Value kosong selalu valid tanpa memeriksa tipe. Column atau Row kosong, atau Value masih N/A Type: Fatal Error. Row atau Column tidak ditemukan: Error. Hanya mengubah satu TableData per eksekusi. Perubahan lewat Setter tidak memicu Table Row Event.
*   **Column dan Row harus berasal dari Table yang sama.** Field Row pada screenshot tampil "NULL" dan akan diganti menjadi "Empty".
*   **Add Row dan Delete Row tidak memicu Table Row Event** (aksi Flow tidak memicu Flow kembali).

### Flow Block Data Tree

*   **10 block, tanpa Control.** Path: `Docs/Modul Logic/Flow/Flow Block/Data Tree/<Nama Block>`, pengenalan kelompok di `Data Tree/Pengenalan`. Block: Tree, Node, Node Setter, Add Node, Assign Node, Delete Node, Tree Get Origin, Node Get Parent, Node Get Children, Node Get Ancestor.
*   **Aturan Tree:** **Order** Node minimal 0 (tidak boleh negatif) dan **harus unik di antara saudara kandung** (Node lain dengan parent yang sama). **Name** Node juga **harus unik di antara saudara kandung**. Konflik ditandai output flag **Order Conflict** dan **Name Conflict** (hanya keluar bernilai true pada kasusnya, status Error). Pemeriksaan pada Add Node, Node Setter, dan Assign Node berurutan Name lalu Order, dan output konflik keluar satu per satu dimulai dari Name. Name dan Order milik Node itu sendiri bukan konflik. **Order negatif = Fatal Error** (prinsip penulis: Error hanya dipakai bila ada output yang menandainya, kasus tanpa output menjadi Fatal Error). Status Not Found pada block Get = Error.
*   **Input dan output per block:**
    *   **Tree:** input Tree. Output Pass (Tree), Name (String), Desc (Text), Merger Mode (Boolean). Tree kosong: Fatal Error.
    *   **Node:** input Node. Output Pass (Node), Tree (Tree), Order (Number), Name (String). Node kosong: Fatal Error.
    *   **Node Setter:** input Node, Order (Number), Name (String). Output Pass (Node), Name Conflict, Order Conflict. Node, Order, atau Name kosong: Fatal Error. Mengubah Name dan Order sekaligus. Name dan Order Origin dapat diubah, tetapi mengubah Order Origin tidak berpengaruh.
    *   **Add Node:** input Parent (Node, pilihan memuat semua Node dari semua Tree), Order (Number), Name (String). Output New Node (Node), Name Conflict, Order Conflict. Parent, Order, atau Name kosong: Fatal Error.
    *   **Assign Node:** input Parent (Node), Order (Number, **bukan N/A Type**), **Children** (label di antarmuka; Node yang ditempatkan di bawah Parent). Output Pass Children (Node), Name Conflict, Order Conflict, **Relation Conflict**. Children dipindahkan **beserta seluruh keturunannya**. Parent dan Children harus dalam Tree yang sama, bila tidak block berstatus Error (tanpa output). Relation Conflict true bila Children ditempatkan pada Node keturunannya sendiri, **termasuk bila Children adalah Origin** (Origin selalu di titik pertama). Menempatkan Children pada Parent yang sudah menjadi parent-nya bukan Relation Conflict, hanya tidak berpengaruh. Name Conflict memang ada pada block ini. Parent, Order, atau Children kosong: Fatal Error.
    *   **Delete Node:** input Node dan Force (Boolean). Output Succeed dan Error. **Node anak ikut terhapus.** Penghapusan ditolak (Error) bila Node anak digunakan oleh komponen lain, dan Force true diperlukan untuk memaksa. Node atau Force kosong: Fatal Error. **Menghapus Node Origin = Fatal Error.** "Sudah digunakan" memakai definisi yang sama dengan Row. Hapus paksa (Force true) memutus relasi komponen yang memakai Node.
    *   **Tree Get Origin:** input Tree. Output The Origin (Node). Tree kosong: Fatal Error.
    *   **Node Get Parent:** input Node dan Depth (Number). Output The Parent (Node) dan Not Found. Depth 1 = parent langsung, 2 = parent dari parent. Not Found bila Depth < 1, Depth melebihi kedalaman Node, atau Node adalah Origin. Input kosong: Fatal Error.
    *   **Node Get Children:** input Node dan Child Order (Number). Output The Children (Node) dan Not Found. Hanya anak langsung. Input kosong: Fatal Error.
    *   **Node Get Ancestor:** input Node dan Anc. Level (Number). Output The Ancestor (Node) dan Not Found. **Level 1 = Origin**, dihitung dari Origin menuju Node. Level yang menunjuk Node itu sendiri (misalnya level 4 pada silsilah Origin ➜ dua leluhur ➜ Node) menghasilkan Not Found. Not Found juga bila Anc. Level < 1. Input kosong: Fatal Error.
*   **Label antarmuka yang ditulis persis:** output `The Origin (Node)`, `The Parent (Node)`, `The Children (Node)`, `The Ancestor (Node)` (termasuk "(Node)"), input `Children` pada Assign Node, input `Child Order`, `Anc. Level`, output `Pass Children`.
*   **Warning Tree:** Add Node tidak memerlukan warning Merger Mode atau External Read Only. Node Setter, Assign Node, dan Delete Node memerlukannya.
*   **Belum terkonfirmasi:** apakah Assign Node pada Tree yang berbeda berstatus Error (draf) atau Fatal Error mengikuti prinsip "tanpa output = Fatal Error" di atas, dan apakah Parent yang sama dengan Children itu sendiri (bukan parent-nya) termasuk Relation Conflict.

## Flow Block Operator

Seluruh halaman block Operator berada di `Docs/Modul Logic/Flow/Flow Block/Operator/<Tipe Data>/<Nama Block>` (Number, String, Table, Object, Boolean, Tree), alias tautan `<Nama> Operator Block`, dan tidak ada yang memiliki Control. Fatal Error pada semua block di bawah menampilkan pesannya di Flow Activity.
- **Prinsip kategori:** Flow Block Operator melakukan komputasi yang mengubah data input menjadi data baru. Kategori Input dan Output hanya untuk block yang memanipulasi aliran tanpa mengkonversi data menjadi data baru. If tetap termasuk Operator karena mengevaluasi A, Operator, dan B menjadi Boolean sekaligus meneruskan aliran sesuai hasilnya.
- **Increment (Number):** input Data dan Adders (Number), output Result = Data + Adders. Terkonfirmasi benar. Data atau Adders kosong dicatat sebagai Fatal Error pada draf.
- **Concatenate (String):** dua input String, output Result. **Tidak dapat error.** Satu input kosong menghasilkan input yang lain, kedua input kosong menghasilkan kosong.
- **Implode (String):** Strings (String atau Array berisi String) dan Separator, output Result.
- **Pad Left dan Pad Right (String):** input String, Length (Number), Pad String, output Result. Fatal Error jika String atau Pad String kosong.
- **TableRow Parse (Table):** input Row dan Rel. Depth (Number), output Object dan Text (keluar sesuai koneksi). Fatal Error jika Row kosong (teks asli "dibiarkan error" ternyata salah ketik, ditulis "kosong"). Rel. Depth kosong dianggap 0. Contoh baku: Row Pesanan `{ "penerima": "1 : Anna", "Total": 1200 }` pada depth 0 menjadi `{ "penerima": { "id": 1, "nama": "Anna", "kelamin": "Perempuan", "no telp": "123456" }, "Total": 1200 }` pada depth 1. Kolom relasi pada depth 0 tampil sebagai ringkasan `"<id> : <label>"`.
- **Assign (Object):** input Key (String) dan Value (Object atau String, bawaan Object, dapat Change Type), output Object. Key memakai simbol `.` untuk kedalaman (contoh `job.status.level`). Fatal Error jika Key atau Value kosong. Bersifat override.
- **Merge (Object):** input Objects (Array berisi Object), output Result (Object). Object yang lebih akhir menimpa atribut yang sama persis, atribut yang saling mengisi pada kedalaman tertentu digabung. Fatal Error jika Objects kosong.
- **Parse (Object):** input Text, output Object dan Error. Error keluar bila Text tidak sesuai kaidah Object (JSON), bertipe Boolean `true` pada kasusnya. Fatal Error jika Text kosong.
- **Stringify (Object):** input Object, output Text. Fatal Error jika Object kosong. Tidak memiliki output Error.
- **If (Boolean):** input A dan B (tipe apa pun, awalnya N/A Type), Operator (String, simbol operator valid, rujuk `Docs/Expression/Operator`), output Boolean (keluar bila terhubung), True, dan False (meneruskan aliran sesuai hasil). Fatal Error jika Operator kosong atau A atau B masih N/A Type.
- **Node Parse (Tree):** input Node, Anc. Depth, Child Depth (Number), output Object dan Text (sesuai koneksi). Struktur Node: `{ "order": number, "name": string, "parent": Node | null, "children": Node[] }`. Anc. Depth menghasilkan `parent` bersarang ke atas, Child Depth menghasilkan `children` ke bawah. Fatal Error jika Node kosong. Anc. Depth dan Child Depth kosong dianggap 0 (tanpa `parent` dan `children`).

**Masih belum jelas** (jawaban review "Sudah benar" tidak menentukan perilakunya, jadi jangan dianggap fakta):
- Implode: hasil bila Strings atau Separator kosong, bila Strings bertipe String tunggal, dan bila Array hanya berisi satu String.
- Pad Left dan Pad Right: hasil bila Length kosong, bila String sudah sama atau lebih panjang dari Length, dan bila Pad String lebih dari satu karakter.
- Assign: data apa yang ditimpa oleh sifat override, karena block tidak punya input Object.
- Merge: hasil bila Objects berisi satu Object atau Array kosong.
- Increment: apakah Adders boleh negatif atau desimal, dan alasan label berbentuk jamak.
- Node Parse: isi Node pada kedalaman terjauh, serta `"parent": null` dan `"children": []` pada Node tanpa leluhur atau anak.

## Flow Block kategori lain
 
* **Halaman:** `Docs/Modul Logic/Flow/Flow Block/<Kategori>/Pengenalan` untuk `Input dan Output`, `Query`, `Operator`, `Modular`, `Chrono`, `Error`. Front matter `status: draft`, `priority` 11 sampai 16 (urut sesuai daftar itu), `tags: flowblock-category`.
* **I/O:** membantu pengelolaan aliran data.
  * **Branch:** satu input, beberapa output. Bukan block bersyarat. Input berupa *field* dapat mendefinisikan data yang dipakai banyak block (seperti *local variable*).
  * **Passer:** meneruskan data tanpa mengubahnya dan memastikan seluruh aliran terhubung selesai atau berurutan (contoh: kode seri dengan Concatenate). Input berupa *field* dapat mendefinisikan daftar data dalam satu block.
* **Query:** membangun dan menjalankan Query.
  * Condition: **Add Table Filter** menambahkan kondisi untuk Table.
  * Execute: **Table Output** menjalankan Query kaidah output table.
* **Operator:** pengolahan data (aritmatika, teks, konversi, translasi), dikelompokkan berdasarkan tipe data input utama, tanpa Pengenalan per kelompok.
  * Number: **Increment** (ada langkah yang ditentukan).
  * String: **Concatenate**, **Implode** (array yang digabung bertipe String), **Pad Left**, **Pad Right**.
  * Table: **TableRow Parse** (hasil Object). Tree: **Node Parse** (hasil Object).
  * Object: **Assign** (hanya satu atribut), **Merge**, **Parse**, **Stringify**.
  * Boolean: **If** (fungsi rinci dan bedanya dengan Branch belum terkonfirmasi).
* **Modular:** proses kompleks (HTTP, provider jasa). Path memakai grup: `Modular/API/HTTP Request`, `Modular/AI/OpenAI 4`.
  * **HTTP Request:** semua metode HTTP. Respons Object atau teks sesuai Response Type (`application/json` menjadi Object).
  * **OpenAI 4:** detail permintaan dan kredensial akan dijelaskan di halamannya (termasuk callout).
* **Chrono:** **Delay** menunda aliran dengan waktu yang dapat ditentukan, state block menjadi Waiting.
* **Error:** **Error Message** membuat error baru dengan pesan yang dimodifikasi. Saat tereksekusi, seluruh aliran dihentikan dan pesan error menjadi output di Flow Activity. Memengaruhi status Error/Fatal Error.

## Flow Block Input dan Output, Query, Modular, Chrono, Error (halaman per block)

* **Delapan halaman block** (terkonfirmasi penulis), semua di `Docs/Modul Logic/Flow/Flow Block/`: `Input dan Output/Branch`, `Input dan Output/Passer`, `Query/Condition/Add Table Filter`, `Query/Execute/Table Output`, `Modular/API/HTTP Request`, `Modular/AI/OpenAI 4`, `Chrono/Delay`, `Error/Error Message`. Alias tautan: Branch Block, Passer Block, Query Add Table Filter Block, Query Table Output Block, HTTP Request API Block, OpenAI 4 AI Block, Delay Chrono Block, Error Message Block. Pola Query memakai subfolder Condition dan Execute.
* **Varian:** Branch 2 sampai 5 (jumlah Output) dan Passer 1 sampai 5 (jumlah pasangan Data dan Pass) dijelaskan dalam satu halaman masing-masing. Pada screenshot judul block tertulis "Data Branch N" dan "Data Passer N" (belum terkonfirmasi apakah halaman memakai "Branch" atau "Data Branch").
* **Branch:** satu Input berupa field bertipe N/A Type (data apa pun, tipe diubah lewat Change Type). Setiap Output mengalirkan data Input. Output yang memiliki koneksi ke block lain yang mengeluarkan data; Output tanpa koneksi (termasuk yang berada di tengah) tidak mengeluarkan data. Tidak pernah Error. Fatal Error bila Input dibiarkan N/A Type. Bukan block bersyarat. Input berupa field dapat mendefinisikan data yang dipakai banyak block. **Terkonfirmasi:** urutan eksekusi Output sesuai penomoran (teks penulis semula "mulai dari Output 2"; titik awal diasumsikan Output 1 sesuai screenshot). Ketidakterprediksian eksekusi hanya muncul bila banyak koneksi dari beberapa block bertemu pada satu input (mis. menyusun Array dari banyak output). Fatal Error bila Input N/A Type berlaku selalu, tidak bergantung koneksi Output. Satu halaman Branch menjelaskan semua varian (judul di screenshot "Data Branch N" tidak dipersoalkan penulis).
* **Passer:** Output Pass n sesuai Data n (tipe sama), aturan Output seperti Branch. Data bisa tidak berguna bila Pass pasangannya tanpa koneksi. Bila Pass terhubung tetapi Data dibiarkan N/A Type = Fatal Error. Passer meneruskan data tanpa mengubahnya dan dapat memastikan beberapa aliran selesai atau berurutan. **Terkonfirmasi:** Data yang terhubung dari block lain tetap menjadi syarat eksekusi walau Pass-nya tanpa koneksi. Satu halaman Passer menjelaskan semua varian.
* **Add Table Filter:** input Query, AND (Boolean, true = AND, false = OR), Column (Column), Operator (String, simbol operator valid, lihat `Docs/Query/Filter/Operator`), Operand (N/A Type, pembanding nilai Column dengan tipe data valid, lihat `Docs/Query/Filter/Operand`). Output Query (tipe Query) = Query input yang ditambah filter. Fatal Error bila ada nilai kosong: Operand N/A Type dan operator mewajibkannya (beberapa operator tidak perlu Operand), sedangkan Operand kosong dengan tipe data dianggap valid. **Fatal Error (terkonfirmasi; penulis semula menyebut Error)** bila aturan pengisian Operator atau Operand tidak sesuai, atau Query input berbasis data selain Table. Block ini tidak memiliki status Error karena tidak memiliki output Error. Contoh simbol operator dan Column Total diterima penulis. Block hanya membangun Query. **Terkonfirmasi:** tombol Q pada field bertipe Query menampilkan konfigurasi Query (setiap field Query memilikinya), dan AND true = AND, false = OR.
* **Table Output:** input Query yang harus berkaidah `Docs/Query/Output/Table`; kosong = Fatal Error. Output Rows (Array berisi Row, setidaknya 1 Row) dan Is Empty (Boolean, true bila hasil kosong). **Terkonfirmasi:** Is Empty bernilai "-" saat hasil berisi, Query yang bukan kaidah Table Output = Fatal Error, dan tombol Q pada field Query menampilkan konfigurasi Query.
* **HTTP Request:** input Method (String, metode HTTP valid), Endpoint (String), Header (Object), Payload (Object). Fatal Error bila Method atau Endpoint kosong; Header dan Payload **boleh kosong** (terkonfirmasi), tetapi request yang gagal tetap keluar lewat Error. Output Success (Object bila respons JSON, **File bila respons berupa file**, Text untuk bentuk lain seperti HTML; terkonfirmasi) dan Error (**Object berisi `status` dan `body`**). Output Error keluar untuk **status code selain 2xx (terkonfirmasi) dan juga kegagalan koneksi** (implementasi memakai try catch sehingga semua error diarahkan ke output ini). Saat koneksi gagal (tidak ada respons), Object Error berisi pesan default berbahasa Inggris: asumsi Claude `status` 0 dan `body` "Failed to connect to the endpoint.", yang akan diterapkan penulis di sistem.
* **OpenAI 4:** input API Key (String), Model (String), Input (Text), Messages (Object), Tools (Object), Tool Choice (Object), Max Output (Number), Temperature (Number). Output Text (Text), Function (JSON, hanya bila Tools diisi), Error (**Object**, terkonfirmasi, keluar bila OpenAI mengembalikan respons error). Fatal Error hanya bila API Key, Model, Max Output, atau Temperature kosong. **Input dan Messages sama-sama kosong tidak menjadi Fatal Error:** OpenAI mengembalikan error yang keluar lewat output Error (terkonfirmasi). Deskripsi Messages, Tools, Tool Choice, Max Output, Temperature sebatas input dan tipe data diterima penulis. Belum terkonfirmasi: format Messages, Tools, Tool Choice, satuan Max Output, rentang Temperature.
* **Delay:** input Duration (Number, satuan detik), output Finish (Boolean, true bila delay selesai). Selama menunggu status Activity terlihat Waiting. Fatal Error bila Duration kosong. **Terkonfirmasi:** Duration harus lebih dari 0, nol atau negatif = Fatal Error. Tidak ada batas maksimum dan angka pecahan diperbolehkan (akurasi milidetik).
* **Error Message:** input Message (Text), tidak memiliki output. Saat tereksekusi menghentikan aliran **hanya pada Activity yang sedang berjalan** dan pesan error tampil di Flow Activity. Status yang dihasilkan adalah **Abort** (status baru, disetujui masuk daftar flowstate; bukan Fatal Error). **Tidak ada rollback:** perubahan block sebelumnya yang sudah berhasil tereksekusi tidak dapat dikembalikan. Message kosong = Fatal Error.
* **Keamanan nilai rahasia:** API Key (OpenAI 4) dan nilai rahasia pada Header atau Payload (HTTP Request) sebaiknya disimpan pada Variable lalu diambil lewat Variable Getter Block, karena Value Variable tersamarkan bagi anggota tanpa akses tetapi tetap dapat dipakai untuk otomasi. **Terkonfirmasi penulis:** callout warning pada HTTP Request dan OpenAI 4 sudah tepat.

# Variable (Modul Data)

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
  
# Enum (Modul Data)

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

# Table (Modul Data)

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

# Tree (Modul Data)
 
- **Definisi:** Tree adalah komponen modul Data untuk menyimpan data secara hierarki atau berbentuk pohon. Cocok untuk data relasional yang bercabang. Satu Tree memiliki banyak Node (`Docs/Tipe Data/Node`). Atribut penting: **Merger Mode** (`Docs/Modul Data/Tree/Konfigurasi Merger Mode`). Penulis menyebut Tree yang memakainya "bersifat Merger".
- **Path halaman:** `Docs/Modul Data/Tree/Apa itu Tree`. Judul: "Apa itu Tree?". Subhalaman: `Konfigurasi Merger Mode`, `Konfigurasi External Read Only` (usulan, menunggu konfirmasi), halaman pengelolaan Node di `Docs/Modul Data/Tree/Node/<Halaman>` (Menambahkan, Mengubah Nama, Mengubah Urutan, Menghapus, Melihat Detail, Mengatur Tampilan, Mengekspor, Mengimpor), menggantikan rencana satu halaman `Mengelola Node`, `Publish`, `Event`.
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
- **Menu konteks Node** (gambar `node-menu.png`): Edit, Detail, Expand/Collapse, View, Import, Export. Edit, Detail, Import, Export dijelaskan di halaman pengelolaan Node (`Docs/Modul Data/Tree/Node/<Halaman>`), dan format Import/Export di halaman `Format Import dan Export`. Gambar menu konteks yang dipakai di halaman Mengatur Tampilan adalah `tree-context.png`.
  - Submenu View: Collapse Below Level (melipat keturunan pada level Node ini, semua Node), Expand Children Only (memperluas hanya satu keturunan di bawahnya), Collapse Descendant (*recursive collapse*), Expand Descendant (*recursive expand*), Hide Collapsed (menyembunyikan anak yang dilipat), Show Collapsed (memunculkan anak yang dilipat), Collapse and Hide (melipat dan menyembunyikan).
  - Jika Node tidak memiliki anak, Expand/Collapse dan Expand Children Only berubah menjadi "No children...".
- **Menghapus Tree:** seluruh Node hilang. Relasi dari komponen lain (Column Table yang memakai Node, Flow Block seperti Tree Node Event) terputus. Node clone di Tree merger dapat terdampak.
- **Contoh Flow (diterima penulis):** `Event/Tree Node Event`, `Operator/Node Parse`, `Modular/HTTP Request` di `Docs/Modul Logic/Flow/Flow Block/<Kategori>/<Nama Block>`.
- **Penamaan pada screenshot** (nama Tree pada judul halaman kerja dan nama pengguna di bilah atas) adalah kasus pribadi dan tidak disebut di dokumentasi. Nama Node pada screenshot menu konteks (Child A, B, C) sudah generik.
- **Menambah dan menghapus Node:** lewat Edit pada Node induk, bagian Children: Add untuk menambah, Delete lalu konfirmasi Delete untuk menghapus. Pada Tree merger, menambahkan Node dari Tree non-merger memakai tombol Add Children dan pilihan mengikuti perubahan Node asal. Menambah atau menghapus Node clone di Tree merger tidak memengaruhi Tree sumber. Menghapus Node sumber ikut menghapus Node clone di Tree merger. Name atau Order yang bentrok menampilkan pesan Error.
- **Mengubah Node:** Edit pada Node, ubah Name atau Order, lalu Update. Order lebih kecil tampil lebih dulu. Order juga dapat diubah dengan drag and drop pada ikon `::` di sebelah kiri Node. Pesan Error bentrok Name yang disepakati: "Name sudah digunakan oleh Node lain pada parent yang sama" (penulis meminta sistem mengikuti).
- **Detail Node:** berisi Name, Children (daftar bernomor), dan Ancestor. Pada Ancestor ada label anchor yang dapat diklik untuk mengganti anchor. Nomor dihitung dari anchor (1) hingga ancestor terdekat untuk menghitung jarak kedalaman. Penggantian tidak disimpan dan hilang saat Detail ditutup. Klik Context di bagian bawah area kerja berpindah ke nilai berikutnya.
- **Tampilan:** Collapse Below Level melipat keturunan pada level Node yang dipilih sehingga level itu menjadi keturunan terakhir yang tampil, karena semua Node di bawahnya masuk dalam lipatan. Hide Collapsed menyembunyikan Node yang dilipat. Status lipat tidak tersimpan dan kembali semula setelah Refresh. Search Tree Data menyorot Node dan memindahkan tampilan ke Node.
- **Export dan Import:** Export langsung mengunduh file JSON tanpa dialog (hanya format JSON tersedia) dan tidak dibatasi hak akses Workspace. Import menambah Node baru (bukan clone, termasuk pada Tree merger) dan ditolak seluruhnya bila ada Name atau Order yang bentrok.
- **Format file Import dan Export:** halaman `Docs/Modul Data/Tree/Node/Format Import dan Export`. JSON bersarang dengan tiga atribut per Node: order, name, children. children adalah array Node dengan atribut yang sama. Node terluar berbentuk satu objek. children wajib ada walau berupa array kosong. Atribut tidak dikenal diabaikan saat Import. Tidak ada atribut parent, hubungan induk dan anak ditentukan posisi dalam children. Tipe atribut pada halaman format adalah tipe JSON, sehingga tidak ditautkan ke `Docs/Tipe Data`.
- **Front matter halaman Node:** `pageDecoration` dengan `icon: x` dan `tree.priority` 9 hingga 3 sesuai urutan halaman.
- **[asumsi] Belum terkonfirmasi:** hasil drag and drop (Order saudara bertukar atau bergeser, drop pada Node lain memindahkan parent atau tidak, Origin dapat diseret atau tidak, event update dan Data Access Update), nilai awal anchor dan tampilan leluhur di atas anchor, perlakuan Import terhadap file hasil ekspor Origin (diasumsikan menjadi Node biasa bernama Origin di bawah Node terpilih).
Alasan: jawaban penulis mengonfirmasi dan mengoreksi beberapa asumsi saya (Active = terlindungi, Merger Mode tidak dapat diubah, External Read Only berlaku di kedua jenis Tree, context dan mode dapat diklik tetapi sementara). Semuanya perlu tersimpan agar subhalaman Tree dan Flow Block terkait konsisten.

# Table View (Modul Interface)

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

# Kanban (Modul Interface)

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

# Gallery (Modul Interface)

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

# Timeline (Modul Interface)

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

# Form (Modul Interface)

*   **Istilah:** objek penyusun isi Form disebut **Elemen** (bukan Node, agar tidak konflik dengan Node sebagai tipe data). Kategori: **Layout** (Card, Full, Split, Accordion), **Display** (Text, Table, Tooltip, Qr, Chrono), **Input** (Basic, Quiz, Table, List). Halaman Elemen: `Docs/Modul Interface/Form/Elemen/<Tipe>/<Nama Elemen>` (contoh `Docs/Modul Interface/Form/Elemen/Layout/Card`). Halaman pendamping Elemen: `Elemen Form/Pengenalan`, `Elemen Form/Layout/Pengenalan`, `Elemen Form/Menambahkan`, `Elemen Form/Menghapus`, `Elemen Form/Mengonfigurasi#Properties Panel`, `Elemen Form/Mengonfigurasi#Header Toolbar`, `Elemen Form/Binding#Binding Layout`, `Elemen Form/State`.
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
*   **Elemen Input (Basic, Quiz, Table, Table Column, List, List Column):** halaman di `Docs/Modul Interface/Form/Elemen/Input/<Nama>`, nama di UI memakai awalan "Input" (Input Basic dst.). Header Toolbar: Remove ditambah pengaturan teks untuk Label. **Quiz:** Binding seperti Basic (Table dan Column), Attributes Label, Format Type, Default Value; tampil sebagai radio button, hanya satu jawaban; opsi diatur di halaman kerja (Add Option, Delete per baris, teks jawaban, value bebas sesuai Format Type); Default Value dipilih dari jawaban opsi. **Table dan List:** wadah multi baris, Binding harus pivot (isi kolom pivot), Attributes hanya Label; Table tampil sebagai tabel, List sebagai daftar blok; State dan Validator ada pada wadah dan memengaruhi semua kolom (Visible false = wadah tidak terlihat, Enable false = setiap kolom tidak di-Enable, Readonly true = setiap kolom Readonly); tombol Add Column menambah widget Table Column atau List Column secara otomatis; pengisi menambah baris dengan Add Row, menghapus lewat tombol Delete di kolom action akhir baris (Table) atau tombol ikon sampah di ujung kanan atas blok (List). **Table Column dan List Column** (sama persis): Binding mengisi Column dengan pivot dari wadah; Attributes Label (judul kolom), Placeholder (saat baris kolom kosong), Format Type; State dan Validator sama dengan Basic; belum terkonfirmasi: nama field Binding wadah, arti Required pada wadah, Layout Panel untuk kolom.
*   **Elemen Display (Text, Table, Tooltip, Qr, Chrono):** semua hanya punya State Visible dan Parent (Layout), tanpa Binding. Header toolbar hanya Remove, kecuali Text yang juga punya pengaturan teks. **Table:** pertama dibuat berukuran 2x2 (dua kolom dua baris), tombol "+" di setiap border untuk menambah kolom atau baris, klik kanan lalu Remove Row atau Remove Column untuk menghapus, baris pertama adalah header, isi sel teks biasa (tanpa binding dan expression), tidak ada Attributes; berbeda dengan Table pada Modul Data. **Tooltip:** kotak informasi yang selalu tampil (bukan muncul saat hover), Attributes Label dan Content. **Qr:** menampilkan kode QR yang siap di-scan; Edit Mode menampilkan isi QR sebagai teks, View Mode menampilkan kode QR sebenarnya; Attribute Content (teks statis). **Chrono:** kronologi berupa alur step, tampilan menurun berbentuk daftar, isi diatur langsung di halaman dengan tombol tambah dan hapus step, tidak ada input di Properties Panel; usulan isian per step: Title, Description, Time (opsional), fitur belum dibuat sehingga detailnya perlu dikonfirmasi ulang. Chrono Display berbeda dengan block Chrono (Delay) di Flow.
*   **Text (Display):** State Visible; Attributes Content (hanya teks statis, belum bisa berisi expression); Parent (layout); tanpa Binding pada panel. Header toolbar teks memformat Content.
*   **State dan Validators (halaman pendamping `Docs/Modul Interface/Form/Elemen/State` dan `Docs/Modul Interface/Form/Elemen/Validators`):** State ada 3, yaitu Visible, Enable, dan Readonly, ketiganya hanya pada Elemen input; Elemen display dan layout hanya punya Visible. Validators saat ini hanya Required, hanya pada Elemen input. Nilai awal Elemen input baru selalu Visible aktif, Enable aktif, Readonly nonaktif, Required nonaktif. Visible = false pada Layout menyembunyikan semua Elemen di dalamnya. Elemen input menyimpan ke Row saat submit hanya bila Enable = true, dan State lain tidak memengaruhi penyimpanan. Setiap field State dan Validators punya ikon saklar kecil di sebelah kanan label untuk beralih antara nilai statis dan expression. Statis = saklar (hijau true, abu-abu false) dan tidak berubah selama pengisi mengisi Form. Expression = kolom isian teks dengan autocomplete dan checker, dihitung ulang saat pengisian. Hasil expression harus Boolean (diperiksa checker). **Parameter expression memakai Alias Elemen input, bukan Label** (koreksi penulis). Contoh: `inputA not empty`.
*   **Binding (halaman pendamping `Docs/Modul Interface/Form/Elemen/Binding`):** Layout memakai Binding Type table atau pivot. Elemen input tidak memiliki pilihan Binding Type dan langsung mengisi field Column; field Table terisi otomatis dari Layout dan pengisi memilih Column dari Table header yang sudah diinformasikan Phoenix. Pivot pada Layout berfungsi bila Table header memiliki relasi: Table header punya Column bertipe Row, atau Table lain punya Column bertipe Row dengan Header = Table header. Elemen input multi row (Table dan List) mengisi Column dari Table lain yang punya Column bertipe Row dengan Header = Table header. Label field pivot hanya Column (dengan informasi Table yang dimaksud). Pengisian pada Layout anak ber-pivot menambah Row di Table relasi yang otomatis terhubung ke Row Table header.
*   **Alias dan title Submission pada Binding:** Alias bersifat opsional pada Elemen input, tampil sebagai checkbox Alias dan kolom teks (muncul saat checkbox true), fungsinya mendaftarkan Elemen sebagai parameter bagi Elemen lain. Nama Alias harus unik dan boleh karakter ASCII apa pun. Title Submission diatur lewat label `As Title` di bagian Binding dengan toggle Yes atau No; bintang di samping Column menandai isian title (biasanya nama pengisi) agar mudah dicari di Submission List. Bintang ini tidak terkait Alias pada Table.
*   **Submission dan update:** setiap pengisian Form yang baru menambah Row baru. Update isian yang sudah dikirim butuh Submission ID (tombol copy di Submission List pada halaman kerja). Tampilan pengisi punya menu untuk mengakses tautan itu, yang secara teknis tersimpan di local cache. Tautan hanya tersedia di perangkat yang sama dan hilang bila cache dihapus; admin dapat mengirim ulang tautan lewat tombol copy. Pengisi tidak butuh pengaturan akses tambahan, karena akses menambah Row dianggap sudah diizinkan saat pembuat Form memilih Table dan relasinya pada Binding.
*   **Binding checker:** menampilkan pesan di layar. Ejaan pesan asli dari aplikasi yang diberikan penulis: "Selected column and it's header is not match", "There is layout binded by pivot, but is not defined yet", "There is input binded by column, but header is not defined yet", dan "There is input binded by column, but column type and overrided type is not match". Saran ejaan yang dipakai di dokumentasi (aplikasi akan mengikuti): "The selected column and its header do not match", "There is a layout bound by a pivot, but the pivot is not defined yet", "There is an input bound by a column, but the header is not defined yet", dan "There is an input bound by a column, but the column type and the Format Type do not match". "Overrided type" adalah Format Type di Attributes. Pesan tidak menghalangi Save maupun Publish. Kunci internal checker tidak terlihat pengguna dan tidak boleh disertakan di dokumentasi. Mengganti Table pada Layout menghasilkan pesan header belum ditentukan atau kolom dan header tidak cocok pada Elemen input di dalamnya.
*   **Penamaan pada screenshot Form** (Table "Pesanan", Column "Pemesan") adalah kasus pribadi dan tidak disebut di dokumentasi.
*   **Layout Panel:** ikon kecil di bawah Elemen yang difokuskan membuka Layout Panel.
*   **Submission List:** panah di kiri baris membuka rincian submission (data yang ditambahkan, ID, atau error); pencarian mencakup ID dan Name.
*   **Belum terkonfirmasi:** pilihan Format Type selain String, nilai awal Label dan Default State pada Accordion, cara men-toggle header Accordion, apakah Elemen di Accordion Collapsed tetap tersimpan saat submit, arti visual tampilan penuh pada Full, urutan atas-bawah Split di mobile, tampilan daftar Children pada Split, fungsi ikon `T` pada toolbar Text, apakah Text ikut dikirim sebagai Submission, tampilan Elemen saat Enable = false, nilai awal Visible pada Elemen layout dan display, apakah Default Value Elemen yang tersembunyi ikut tersimpan, daftar operator dan fungsi expression, apakah bintang muncul saat As Title bernilai Yes, apakah hanya satu Elemen per Form yang boleh As Title Yes, tampilan title di Submission List, letak tampil pesan binding checker, nama resmi ikon saklar dan kolom isian expression, bentuk pesan checker expression, umpan balik saat Required belum terisi, perilaku Required pada Elemen Readonly, dan rencana Validators lain.

# Canvas (Modul Interface)
 
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
*   **Hak akses:** mengikuti Component Access, Data Access, dan Function Access (View Publish dan Publish) seperti komponen lain. View Publish hanya menyalin atau membuka Link tanpa mengubah Status.
*   **Belum terkonfirmasi:** apakah Layout dan Template mengikuti Data Access Add, Update, Delete yang sama dengan widget, widget lain yang tergolong "versi lite", label tombol penyimpan di modal Publish, tombol di modal Binding, dan letak tombol Binding pada bilah navigasi.
*   **Penamaan pada screenshot** (nama Canvas "Test", nama Data pada Chart Pie, serta nama dan nilai pada grafik) adalah kasus pribadi dan tidak disebut di dokumentasi.

## Widget Canvas (struktur dan istilah)
 
*   **Path:** `Docs/Modul Interface/Canvas/Widget/<Nama Widget>` (contoh `Table`, `Chart Pie`, `Kanban`). Halaman pendukung: `.../Widget/Pengenalan`, `.../Widget/Menambahkan`, `.../Widget/Mengonfigurasi` (anchor `#Header Toolbar`, `#Layout Panel`, `#Design Panel`). Menghapus widget ditautkan ke `Docs/Modul Interface/Form/Elemen/Menghapus`.
*   **Istilah toolbar (mengikuti Form):** **Header Toolbar** (di atas widget), **Layout Panel** (di bawah widget, ukuran, padding, margin, sama di semua widget), **Design Panel** (di bawah widget, pengaturan tampilan khusus widget, mis. Chart Pie). Bukan "design toolbar".
*   **Field Data di Header Toolbar** adalah **Query untuk data yang ditampilkan widget**, dengan tombol Q di dalamnya. Kaidah Query per widget: Table = **Table Output**, Chart Pie = **Series Output**, Timeline = **Timeline Output** (belum terkonfirmasi untuk Kanban, Gantt, Gallery).
*   **Menambahkan:** ketik perintah (`/table`, `/chart pie`) dalam field "Type something here to add..." untuk menampilkan variasi lalu pilih salah satunya.
*   **Widget tampilan data (Table, Kanban, Gantt, Timeline, Gallery)** hanya memiliki pengaturan Query di Header Toolbar dan hanya Layout Panel (tanpa Design Panel).
*   **Isi widget (data hasil Query) tidak dapat dimanipulasi dari Canvas.** Pengelolaan data dilakukan di komponen aslinya (Table View, Kanban, Timeline, Gallery).
*   **Menghapus widget:** callout danger. Menghapus konfigurasi termasuk Query, data sumber dan barisnya aman, tidak bisa dikembalikan.
*   **Struktur halaman widget ringkas:** note, definisi, Menambahkan, Antarmuka (Header Toolbar, Layout Panel, Design Panel bila ada, Tampilan, Interaksi), Menghapus, Praktik Terbaik, TL:DR (hanya Chart Pie), FAQ. Tidak ada Mengapa, Konsep Utama, Cara Kerja, Hak Akses, Contoh Penggunaan, Batasan.

## Widget Table
 
*   **Header Toolbar** (`interface-widget-table.png`): ikon Table, ikon pegangan ⋮⋮ (memindahkan), **toggle 123 = pagination**, **toggle kaca pembesar = toolbar search**, Data (Query, kaidah Table Output), tombol Q, Remove. Toggle aktif ditandai latar berwarna. Ikon tabel kecil di kiri 123 belum dijelaskan.
*   **Layout Panel** saja. Tombol Expand dan panah ▼ belum dijelaskan.
*   **Tampilan:** kolom ID dan kolom hasil Query (ikon tipe data di samping nama), cell kosong "Empty", toolbar search (Refresh List, Search Data...), pagination ("Show 50 of 8 items, on page", Go, Prev, Next; 50 adalah batas data per halaman).

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
   
## Widget Kanban, Gantt, Timeline, Gallery
 
*   **Penjelasan penulis:** semuanya "hanya memiliki pengaturan Query di header dan hanya memiliki panel layout" seperti Widget Table. Path: `Docs/Modul Interface/Canvas/Widget/Kanban`, `.../Gantt`, `.../Timeline`, `.../Gallery`. Screenshot belum ada.
*   **Kanban:** kolom dan kartu berdasarkan status atau kategori. **Gantt:** bilah jadwal pada sumbu waktu (**belum ada di knowledge, isi umum**). **Timeline:** data dalam urutan waktu, **widget hanya menyajikan satu data** (komponen punya Timeline Event dan banyak Timeline Data); kaidah Timeline Output (Name, Start, End; Start dan End berformat DateTime, Date, DateTimeZone). **Gallery:** kartu visual yang menonjolkan gambar atau konten.
*   **Belum terkonfirmasi:** kaidah Query Kanban, Gantt, Gallery (anchor tebakan `#Kanban Output`, `#Gantt Output`, `#Gallery Output`), isi tampilan dan interaksi pada widget (diambil dari komponen aslinya), cara isi kartu ditentukan pada widget Kanban dan Gallery, kolom Query untuk Gantt.
*   **Penamaan pada screenshot** (nama Table "Pesanan" dan "Barang pesanan", nama barang, dan kolom) adalah data pribadi dan tidak disebut di dokumentasi.
*   
## Widget Space
*   **Belum ada informasi.** Space disebut ketinggalan dalam daftar widget tampilan data. Halaman berupa kerangka minimal (Header Toolbar dengan Data dan Q, Layout Panel). Perlu: definisi Space, sumber data, kaidah Query (`Space Output`?), dan screenshot.
*   **Belum terkonfirmasi untuk semua chart:** kaidah Query selain Pie, arti diverging, reversed, marker, step ticks, step gap, Split, Multi, Stacked, fungsi Y2 (toggle sumbu kedua), gestur zoom, arti angka dan filter pada Data Chart Radial, dan nama slug ikon toggle.
*   **Penamaan pada screenshot** (Table "Catatan Raven" dan "Catatan Phoenix", nama status) adalah data pribadi dan tidak disebut di dokumentasi.
 
## Aturan umum Widget Chart
 
*   **Panel di bawah widget:** Layout Panel (ikon layout), **Data Panel** (ikon database), Design Panel (ikon palet). Header Toolbar: ikon, pegangan, Data (Query dengan Q), Remove. Kaidah Query Data: **Series Output** (Pie sudah terkonfirmasi, chart lain diasumsikan).
*   **Perintah tambah:** `/chart line`, `/chart bar`, `/chart radial`, `/chart linear`.
*   **Theme** (daftar lengkap): monochrome, phoenix, fun, classy, futuristic, elegant, aurora, forest, royal, obsidian, celestial, volcanic, lotus, cyberpunk, desert. Label dropdown: `theme` (Line, Linear), `style` (Bar, Radial).
*   **legends** (Line, Bar): right, bottom, left, top, hidden. Pada Radial legends adalah toggle.
*   **Threshold** (Radial, Linear): tombol + threshold, tiap titik punya `at` (persen) dan warna. Nilai di atas persentase threshold berubah menjadi warna yang ditentukan.
*   **min/max:** toggle Auto (otomatis). Jika nonaktif mengikuti from dan until. Pada Chart Line, kolom yang dikosongkan berarti auto.
* 
## Widget Chart Line
 
*   **Data Panel:** tiga sumbu X, Y, Y2, masing-masing min/max dengan toggle **A**, ikon tag (toggle label), tick (banyak label), format (kosong = default). **Penulis menyebut panel ini kemungkinan diganti seperti Chart Bar.**
*   **Design Panel:** ketebalan garis (contoh 2.5), jenis garis (`smooth`, `sharp`, `step`), dot radius (contoh 4), toggle zoom (kaca pembesar, interaksi zoom in dan out), toggle grid, theme, area (persen opacity area line), legends.
*   **Tampilan:** tooltip pada titik (waktu dan nilai series), legend di bawah.
  
## Widget Chart Bar
 
*   **Data Panel:** X (label), Y dan Y2 (min/max dengan toggle Auto, label, tick, format). Y2 tampil sebagai sumbu kanan saat aktif.
*   **Design Panel:** mode (toggle **diverging**, **reversed**, **orientasi**: nonaktif = vertikal; radio **Grouped**, **Stacked**, **Full**), style (theme), bar opacity (contoh 90%), bar border radius (contoh 4), bar padding (contoh 0.25%), marker (warna, length contoh 70%, width contoh 3), **pattern** (`off`, `basic` = garis-garis, `all` = satu pola ke semua dengan pilihan Hatch, Dots, Cross, ZigZag, `series` = pola per urutan series dengan tombol + untuk tambah urutan), legends, toggle zoom, toggle grid, toggle **123** (label nilai di atas bar), size (font label nilai, contoh 11).
  
## Widget Chart Radial
 
*   **Header Toolbar:** **Needle** (Query kaidah **Single Output** untuk nilai arah needle, "Empty" bila belum diisi, dengan Q), Data (Query Series Output dengan Q). Angka dan ikon filter di samping nama Table pada Data belum dijelaskan.
*   **Data Panel:** ruler (toggle), ticks (banyak tick dan warna), min/max (toggle Auto), label (label nilai needle), value (`Value`, `Percent`, `Ratio`, `None`), ukuran (0 sampai 100%) dan warna label.
*   **Design Panel:** mode (`Multi`, `Stacked`), bentuk lengkungan (`Full`, `Semi`, `Horseshoe`, `Fan`, `Custom`; Custom menampilkan input from° dan until°), thickness (bawaan 25), arc (`Round`, `Square`, `Butt`), style (theme), opacity bar (contoh 100%), arc gap (contoh 17), + threshold, track (warna, opacity contoh 15%), needle (warna, panjang contoh 120%, 120% = mengenai bar), toggle legends, toggle **animation at start** (animasi needle saat pertama dibuka).
*   **Ejaan antarmuka:** tombol tertulis "treshold".
  
## Widget Chart Linear
 
*   **Data Panel:** min/max (toggle Auto), value (`Inside`, `End`, `Above`, `Below`, `None`), format (`Value`, `Percent`, `Custom`), size (contoh 13).
*   **Design Panel:** mode (`Bars`, `Multi`, `Stacked`), shape (`Plain`, `Split`, `Stepped`), toggle diverging, toggle orientasi (aktif = horizontal), toggle show track (menampilkan track opacity contoh 20% dan warna), toggle show marker (menampilkan marker width contoh 2, height contoh 14%, dan warna), theme, bar opacity (contoh 100%), bar border radius (contoh 3), + threshold (setelah ada: toggle legend threshold dan titik at % dan warna), step ticks (contoh 10) dan step gap (contoh 3) **hanya saat Stepped**, label (`start`, `end`, `above`, `below`, `none`), label size (contoh 12), bar gap (contoh 11), toggle **count up** (animasi saat pertama dibuka).

## Widget Text

  * perintah tambah `/text` ("Add text"). Kelompok widget: Teks. **Belum ada informasi** tentang editor, format, Design Panel, atau hubungan dengan Binding dan Query.
  *   **Header Toolbar:** ikon Text, ikon pegangan, tombol − dan + dengan kolom ukuran font (contoh 22), toggle **Bold**, **Italic**, **Underline**, tiga pilihan rata teks (kiri, tengah, kanan; yang aktif ditandai latar berwarna), dan ikon tempat sampah (Remove).
  *   **Layout Panel:** min. w dan h (contoh 0%), tombol Expand, padding, margin.
  *   **Data Panel** (ikon kode `</>`): **daftar binding untuk mengganti teks dengan Query berkaidah Single Output**. Tombol **+ Parse Query** menambah item. **Tombol + Parse Column akan dihapus** (jangan ditulis).
  *   **Belum terkonfirmasi:** cara binding direferensikan dalam teks, kolom item binding, cakupan Bold dan sebagainya (seluruh teks atau seleksi), satuan ukuran font, ada tidaknya Design Panel, cara mengisi teks.
    
## Widget Button

*   Perintah tambah `/button`. Kelompok widget: Aksi. Terkonfirmasi: **memicu Flow lewat Flow Block Pulser**, **membuka komponen apa pun**, dan **dapat ditekan publik** pada Canvas yang dipublikasikan (developer harus berhati-hati). Button juga dapat membuka Canvas dengan parameter Binding (rilis berikutnya).
*   **Belum terkonfirmasi:** cara mengatur aksi Button, tampilan dan variasi tombol, Header Toolbar dan Design Panel pada Text dan Button, serta apakah keduanya memiliki Query.
    *   **Header Toolbar memiliki field Action** (Tipe Data **Action**, akan ditambahkan penulis: `Docs/Tipe Data/Action`). Fungsi Tipe Data Action: **mendefinisikan aksi terhadap Row Table, membuka suatu halaman, atau membuka popup Interface**.
    *   Terkonfirmasi sebelumnya: memicu Flow lewat Flow Block **Pulser**, membuka komponen apa pun, dapat ditekan **publik** pada Canvas yang dipublikasikan. Hubungan Action dengan hal ini belum dijelaskan.
    *   **Belum terkonfirmasi:** cara mengisi Action, tampilan dan variasi tombol, Data Panel dan Design Panel, screenshot.

# Space (Modul Interface)

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