---
name: phoenix-docs-silverbullet
pageDecoration:
  icon: info
description: Menulis, melengkapi, merevisi, atau mereview dokumentasi produk Phoenix dalam format Silverbullet berbahasa Indonesia. Gunakan skill ini setiap kali pengguna meminta konten dokumentasi Phoenix. Output selalu berupa file .md.
---

# Dokumentasi Phoenix (format Silverbullet)

Skill ini memastikan setiap halaman dokumentasi Phoenix memakai gaya penulisan, struktur, dan sintaks yang sama dengan halaman yang sudah dibuat penulisnya. Konsistensi penting karena halaman-halaman ini saling terhubung lewat wikilink dan dibaca sebagai satu kesatuan dokumentasi.

## Prinsip umum

- Tulis dalam Bahasa Indonesia baku dan sapa pembaca dengan **"Anda"** (selalu huruf kapital).
- Gunakan kalimat aktif, singkat, dan konkret. Jelaskan manfaat, bukan hanya definisi.
- Istilah asing yang bukan nama fitur ditulis miring dengan`*...*`, misalnya`*drag and drop*`, `*least privilege*`.
- **Bertanya agar memitigasi kesalahan.** Sebelum menulis halaman baru atau merevisi besar, tanyakan dulu di chat hal-hal yang belum jelas, lalu tunggu jawaban penulis sebelum membuat file. Tanyakan hal yang memengaruhi isi dokumen: perilaku produk, nama menu/field/tombol persis seperti di aplikasi, aturan akses, jalur tautan, dan konvensi yang belum pasti. Kumpulkan pertanyaan dalam satu pesan singkat dan bernomor, jangan bertanya satu per satu. Jangan menanyakan hal yang sudah ada di knowledge, di halaman yang diberikan penulis, atau di gambar. Jika penulis berkata "silakan tebak", barulah tulis tebakan dan tandai dengan TODO.
- Asumsikan detail yang terbaik sesuai konteks halamannya, jika ragu tetap lakukan dan jelaskan dalam TODO.
- Pahami konteks halaman yang diminta, silahkan buat struktur yang terbaik untuk halaman tersebut, jangan terlalu kaku, agar penulis tahu kemungkinan terbaik dalam menjelaskan konteks halaman tersebut.
- Untuk konsep yang sudah punya halaman sendiri (Komponen, Folder, Pro, Flow Block, dan sejenisnya), jangan mendaftar contoh di tabel Konsep Utama. Cukup beri satu kalimat singkat dan tautkan ke halamannya ("Selengkapnya lihat [[...]]"). Pada tabel Konsep Utama, istilahnya sendiri yang dijadikan wikilink (kolom Istilah), bukan dicetak tebal. Jika istilah sama persis dengan nama halaman tujuan, tulis wikilink tanpa alias (misalnya `[[Docs/Tipe Data/Expression]]`), dan penjelasannya mengikuti definisi di halaman Tipe Data tersebut.
- Gunakan istilah "bilah navigasi", bukan "navbar".
- Jika topik cukup dalam diluar dari kotenks, tulis ringkasan di halaman utama dan arahkan ke subhalaman dengan tautan, lalu tandai dengan TODO bahwa subhalaman perlu dibuat.
- Hasilkan file`.md`, bukan teks biasa di chat, kecuali pengguna hanya meminta komentar atau review.
- **Tautkan Tipe Data di setiap penyebutan**, bukan hanya di Konsep Utama: `[[Docs/Tipe Data/Row]]`, `[[Docs/Tipe Data/Column]]`, `[[Docs/Tipe Data/Enum]]`, `[[Docs/Tipe Data/EnumData]]` (tanpa alias bila sama persis dengan nama halaman), termasuk di Cara Kerja, TL:DR, FAQ, dan tabel. Penulis memakai `Docs/Tipe Data/Enum` untuk Enum sebagai tipe data, dan halaman komponen `Docs/Modul Data/Enum/Apa itu Enum` hanya bila membahas komponennya.
- Setiap kali saya memberi informasi baru dalam penulisan dokumentasi Phoenix, tulis di akhir jawaban bagian **"Usulan update /phoenix-docs-silverbullet"**. Isinya alasan pembaruannya, lalu sertakan file.md nya agar perubahan skill menjadi mudah. Jika tidak ada yang relevan, jangan tulis bagian ini.
- Setiap kali saya memberi informasi baru dalam dokumentasi Phoenix, tulis di akhir jawaban bagian **"Usulan update skill /phoenix-docs-knowledge"**, lalu sertakan file.md nya agar perubahan skill menjadi mudah. Isinya alasan pembaruannya. Jika tidak ada yang relevan, jangan tulis bagian ini.

## Cara berpikir yang perlu dijaga

Bagian ini merangkum pola yang berulang dari revisi penulis. Pahami alasannya agar bisa dipakai pada konteks apa pun.

1. Halaman "Apa itu <Konteks>" memuat seluruh isi konteks itu, tidak dipecah ke subhalaman. Item anak yang menjadi bagian konteks (misalnya Timeline Event dan Timeline Data pada Timeline) ditulis lengkap di halaman yang sama: atribut, langkah Menambahkan, Mengubah, Menghapus, hak akses, dan dampaknya. Tautan ke item anak memakai anchor ([[#Mengelola Timeline Event|Timeline Event]]), bukan path subhalaman tebakan. Subhalaman hanya dipakai untuk fitur yang memang sudah punya halaman sendiri (misalnya Merge, Publish, Event, Flow Block, Data Access) atau bila penulis meminta. Jika ragu, tulis lengkap. Alasan: penulis meminta semua isi ditulis di halaman yang sama dan menginginkan hal yang sama untuk konteks lain.
2. **Istilah milik produk dan penulis menang.** Pakai label persis seperti di antarmuka dan istilah yang dipakai penulis (misalnya Blueprint, Submission, Flow Block Event). Jangan menciptakan nama untuk area antarmuka yang belum diberi nama; tulis dengan sebutan paling netral dan beri TODO agar penulis menamainya. Analogi dari luar produk (misalnya "seperti composition di Blender") atau kalimat "kalau bingung maksudnya..." adalah bantuan bagi Claude untuk memahami, bukan isi dokumentasi, kecuali penulis memintanya ditulis. Pakai satu istilah yang sama di seluruh halaman. Kata Indonesia umum ("blok") boleh untuk penjelasan non-fitur, sedangkan nama fitur tetap menggunakan link.
3. **Tautkan untuk membuka jalan.** Setiap konsep, aksi, atau istilah yang punya ruang untuk tumbuh dijadikan wikilink, termasuk ke halaman yang belum ada. Wikilink tebakan adalah ide struktur dokumentasi, bukan kesalahan, jadi jangan ragu. Tebakan path mengikuti pola yang sudah ada: setiap folder memiliki halaman`Pengenalan` sebagai pintu masuk, fitur pendamping konteks bernama`<Fitur>` (misalnya`Flow Activity`), item anak berada di bawah folder kategorinya, dan bagian dalam sebuah subhalaman diakses lewat anchor (`#Menambahkan Flow Block`). Tautan berlaku di seluruh halaman, termasuk bagian ringkasan di akhir. Bagian Praktik Terbaik, Batasan dan Catatan, TL:DR, dan FAQ (isi jawaban) tidak boleh berisi teks polos untuk hal berikut : Nama field, Tombol, Nilai boolean, Istilah. Tautkan juga aksi yang melintasi konteks (misalnya menghubungkan Event dari komponen lain). Dalam contoh penggunaan, hampir setiap nama fitur atau konteks yang disebut adalah wikilink. Tandai asumsi halaman baru dengan satu TODO konsolidasi per halaman, bukan satu TODO per tautan.
4. **Screenshot adalah sinyal struktur.** Screenshot antarmuka berarti penulis ingin ada bagian "Antarmuka <Konteks>": gambar, penjelasan area, tabel tombol bilah navigasi, dan catatan perbedaan tampilan desktop dan mobile. Jika ada gestur, tambahkan "Interaksi Antarmuka" (tabel Fungsi dan Aksi). Screenshot dengan menu terbuka biasanya menunjuk ke subhalaman. Tombol, ikon, atau penghitung yang belum dijelaskan penulis ditandai TODO, bukan ditebak sebagai fakta.
5. **Contoh Penggunaan menjual nilai, bukan menguji fitur.** Pada konteks komponen, Skenario berangkat dari kebutuhan nyata dan hasil yang dirasakan pengguna, dengan menonjolkan nilai integrasi Phoenix (data, logika, dan sistem lain tersambung). Hindari contoh yang hanya membuktikan fitur bekerja (misalnya menekan tombol uji). Susunannya: kebutuhan, komponen yang terlibat, alur (diagram mermaid dan tabel langkah dengan nama block yang ditautkan), hasil yang dirasakan, lalu ide skenario lain (variasi pemicu, tujuan, atau komponen) sebagai inspirasi. Judul skenario dari penulis mengikat dan harus diisi rinci. Nama konteks memakai nama generik dan ditandai TODO. Kalimat penutup ditulis ulang untuk skenario itu dan tidak disalin dari contoh lain.
6. **Draf dulu, TODO kemudian.** TODO tidak menggantikan draf. Setiap bagian, termasuk warning dampak penghapusan, catatan perbedaan mode, dan langkah yang belum pasti, ditulis dalam bentuk terbaik, lalu ditandai untuk konfirmasi. Dampak penghapusan konteks (apa yang hilang dan apa yang terputus) selalu ditulis sebagai callout warning.
7. **Ringkasan harus mengikuti isi.** Batasan dan Catatan, TL:DR, dan FAQ adalah ringkasan. Setiap kali isi halaman berubah atau dipindah, sinkronkan keempatnya: (a) langkah yang sudah pindah ke subhalaman diganti satu tautan; (b) Batasan berisi perilaku, dampak, dan ketergantungan (warning, perbedaan mode, relasi hak akses, apa yang tidak dicakup sebuah tombol), bukan lokasi tombol atau langkah yang sudah ada di isi halaman; (c) TL:DR berisi 4 sampai 6 poin yang mengikuti peta halaman (definisi, antarmuka, membangun, menjalankan, memantau, hal yang perlu hati-hati); (d) setiap anchor`#...` harus ada di halaman tujuan atau di daftar halaman yang diusulkan.
8. **Revisi penulis adalah sumber belajar.** Bandingkan halaman yang dikembalikan dengan versi sebelumnya. Yang dihapus biasanya salah level atau bukan konten, yang diganti biasanya istilah atau struktur, dan yang ditambah biasanya bagian yang terlewat. Ubah temuan menjadi aturan di skill silverbullet.md dan knowledge.md (path, istilah, perilaku). Jadikan struktur dan istilah penulis sebagai dasar untuk halaman berikutnya.
9. **Ikon di judul halaman kerja (konteks = komponen) adalah ikon komponen.** Jangan menafsirkannya sebagai jenis atau tombol (contoh: "2D" pada Canvas). Tulis "ikon <Komponen> dan Header Name".
10. **Fitur rilis berikutnya tetap ditulis.** Jika penulis memberi informasi fitur yang belum ada pada lampiran karena baru tersedia di rilis selanjutnya (contoh: Binding Canvas), tulis drafnya lengkap, jangan menaruh letak tombol atau antarmuka sebagai fakta, dan tandai dengan satu TODO yang meminta screenshot dan verifikasi ulang setelah rilis.
11. **Contoh dalam penjelasan fitur harus generik.** Hindari inisial atau label seperti "pesanan A dan pesanan B". Tulis misalnya "nomor pesanan" dan "nomor pesanan lain". Berlaku juga di FAQ.
12. **Ikon di judul halaman kerja adalah ikon komponen.** Jangan menafsirkannya sebagai jenis atau tombol (contoh: "2D" pada Canvas). Tulis "ikon <Komponen> dan Header Name".
13. **Analogi dari penulis hanya untuk Claude.** Penjelasan seperti "anggap seperti div pada HTML" membantu memahami perilaku (Layout dapat ditumpuk), tetapi tidak ditulis di dokumentasi. Tulis perilakunya langsung.
14. **TODO yang sudah dijawab dihapus dari draf berikutnya.** Pertahankan hanya TODO baru atau yang belum terjawab, dan terapkan setiap jawaban ke seluruh bagian terdampak (isi, Batasan, TL:DR, FAQ, Praktik Terbaik).
15. **Halaman widget pendek, fitur umum ditautkan.** Penulis menghapus semua bagian yang menjelaskan hal yang berlaku untuk semua widget. Jangan menulis ulang konsep, cara kerja, hak akses, atau contoh penggunaan di halaman widget. Jangan menyebut widget sebagai "versi lite" (itu dijelaskan di halaman Canvas). Fakta "isi widget tidak dapat dimanipulasi" cukup muncul di FAQ.
16. **Tulis hanya pengaturan yang terlihat dan dijelaskan penulis.** Ikon yang belum dijelaskan, satuan, dan rentang nilai ditandai TODO, bukan ditulis sebagai fakta.


## Konvensi tautan

|Konteks|Format|Variasi|Contoh|
|-|-|-|-|
| Halaman konsep umum | - | `[[Inisialisasi/Apa itu Pro?|Pro]]`, `[[Docs/Apa itu Komponen?|Komponen]]`, `[[Docs/Folder/Apa itu Folder?]]` | - |
| Penjelasan Antarmuka Utama |`[[Docs/Antar Muka#<Anchor>]]` | Bilah Navigasi (Header Navigation Phoenix), Area Manajemen Folder (bagian pengelolaan folder dan komponen), Halaman Kerja (antarmuka kerja komponen)| `[[Docs/Antarmuka#Area Manajemen Folder]]` |
| Penjelasan Modul |`[[Docs/Modul <Nama>/Pengenalan|<Nama>]]`  | Data, Interface, Logic, Developer | `[[Docs/Modul Developer/Pengenalan|Developer]]` |
| Halaman Styling | - |`[[Docs/Styling/Styling Class]]`| - |
| Komponen | `[[Docs/Modul <Nama>/<Komponen>/Apa itu <Nama>|<Nama>]]` | Data: Variable, Enum, Table, Tree. Interface: Table View, Gallery, Canvas, Kanban, Space, Timeline, Form. Logic: Flow. Developer: Group, Workspace, Model|`[[Docs/Modul Logic/Flow/Apa itu Flow|Flow]]`|
| Data dalam Komponen | `[[Docs/Modul <Modul>/<Komponen>/<Nama>/Pengenalan|<"Alias">]]` | Data: Enum (Enum Data “Enum Data”), Table (Table Row “Table Row”), Tree (Node “Tree Node”). Interface: Canvas (Template “Canvas Template”, Widget “Canvas Widget”), Form (Elemen “Elemen Form”), Space (Weather “Space Weather”, Environment “Space Environment”, Object “Space Object”), Table View (Table View Data “Table View Data”), Timeline (Timeline Event “Timeline Event”, Timeline Data “Timeline Data”). Logic : Flow (Flow Block “Flow Block”) | `[[Docs/Modul Interface/Canvas/Template/Pengenalan|Canvas Template]]`|
| Subhalaman Komponen Variable | `[[Docs/Modul Data/Variable/<Sub Halaman>]]` | Cara Kerja, Menambahkan Data, Mengubah Data, Menghapus Data, Antarmuka, Mengotomasi, Contoh Penggunaan, FAQ | `[[Docs/Modul Data/Variable/Cara Kerja]]` |
| Subhalaman Komponen Enum | `[[Docs/Modul Data/Enum/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Strict On Field, Contoh Penggunaan, FAQ | `[[Docs/Modul Data/Enum/Cara Kerja]]` |
| Pengelolaan Enum Data | `[[Docs/Modul Data/Enum/Enum Data/<Halaman>}]]` | Menambahkan, Mengubah, Menggabungkan, Menghapus | `[[Docs/Modul Data/Enum/Enum Data/Pengenalan]]` |
| Subhalaman Komponen Table | `[[Docs/Modul Data/Table/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Mengimpor, Mengotomasi, Row Form, Contoh Penggunaan, FAQ | `[[Docs/Modul Data/Table/Cara Kerja]]` |
| Pengelolaan Table Row | `[[Docs/Modul Data/Table/Table Row/<Halaman>}]]` | Menambahkan, Mengubah, Menggabungkan, Menghapus | `[[Docs/Modul Data/Table/Table Row/Pengenalan]]` |
| Subhalaman Komponen Canvas | `[[Docs/Modul Interface/Canvas/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Binding, Layout, Mempublikasi, Hak Akses, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Canvas/Cara Kerja]]` |
| Halaman Umum Canvas Widget | `[[Docs/Modul Interface/Canvas/Widget/<Halaman>}]]` | Menambahkan, Menghapus, Mengonfigurasi | `[[Docs/Modul Data/Canvas/Template/Pengenalan]]` |
| Widget Canvas | `[[Docs/Modul Interface/Canvas/Widget/<Grup>/<Nama>|Widget <Alias>` | Basic : Button (Button), Text (Text). Chart : Bar (Chart Bar), Line (Chart Line), Linear (Chart Linear), Pie (Chart Pie), Radial (Chart Radial). Interface : Gallery (Gallery), Gantt (Gantt), Kanban (Kanban), Space (Space), Table (Table), Timeline (Timeline) | `[[Docs/Modul Interface/Form/Widget/Chart/Pie|Widget Chart Pie]]` |
| Subhalaman Komponen Form | `[[Docs/Modul Interface/Form/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Form Page, Submission, Mempublikasi, Hak Akses, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Form/Cara Kerja]]` |
| Halaman Umum Elemen Form | `[[Docs/Modul Interface/Form/Elemen Form/<Halaman>}]]` | Menambahkan, Menghapus, Mengonfigurasi | `[[Docs/Modul Data/Form/Elemen Form/Pengenalan]]` |
| Halaman pendamping Properties Panel Elemen | `[[Docs/Modul Interface/Form/Elemen Form/<Property>|Form <Property>]]` |, State, Validators, Binding | `[[Docs/Modul Interface/Form/Elemen Form/State|Form State]]`|
| Pengenalan Grup Elemen Form | `[[Docs/Modul Interface/Form/Elemen Form/<Grup>/Pengenalan|Elemen <Grup>]]` | Layout, Display, Input | `[[Docs/Modul Data/Form/Elemen Form/Layout/Pengenalan|Elemen Layout]]` |
| Elemen Form | `[[Docs/Modul Interface/Form/Elemen Form/<Grup>/<Nama>}]]` | Layout: Accordion, Card, Full, Split. Display: Chrono, QR, Table, Text, Tooltip. Input: Basic, List, List Column, Quiz, Table, Table Column | `[[Docs/Modul Interface/Form/Elemen Form/Layout/Accordion]]` |
| Subhalaman Komponen Gallery | `[[Docs/Modul Interface/Gallery/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Mengatur Templat, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Gallery/Cara Kerja]]` |
| Subhalaman Komponen Kanban | `[[Docs/Modul Interface/Kanban/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Mengatur Templat, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Kanban/Cara Kerja]]` |
| Subhalaman Komponen Space | `[[Docs/Modul Interface/Space/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Hak Akses, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Space/Cara Kerja]]` 
| Penjelasan Lanjut Data Komponen Space | `[[Docs/Modul Interface/Space/<Jenis>/<Halaman>|<Halaman> Space <Jenis>]]` | Weather: Menambahkan, Menghapus, Mengubah. Environment: Menambahkan, Menghapus, Mengubah. Object: Menambahkan, Menghapus, Mengubah. | `[[Docs/Modul Interface/Space/Weather/Menambahkan|Menambahkan Space Weather]]` |
| Subhalaman Komponen Table View | `[[Docs/Modul Interface/Table View/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Hak Akses, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Table View/Cara Kerja]]` |
| Halaman Table View Data | `[[Docs/Modul Interface/Table View/Table View Data/<Halaman>]]` | Menambahkan Data, Mengatur Tampilan, Mengatur Query, Mengelola Row, Mengubah Nama, Menghapus | `[[Docs/Modul Interface/Table View/Table View Data/Menambahkan Data]]` |
| Subhalaman Komponen Timeline | `[[Docs/Modul Interface/Timeline/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Timeline/Cara Kerja]]` |
| Halaman Data Komponen Timeline | `[[Docs/Modul Interface/Timeline/<Nama>/<Halaman>]]` | Timeline Event: Menambahkan, Mengubah, Menghapus. Timeline Data: Menambahkan, Mengatur Query, Mengganti Nama, Menghapus, Mengelola Row | `[[Docs/Modul Interface/Timeline/Timeline Event/Menambahkan]]` |
| Subhalaman Komponen Flow | `[[Docs/Modul Logic/Flow/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Flow Activity, Contoh Penggunaan, FAQ | `[[Docs/Modul Logic/Flow/Cara Kerja]]` |
| Halaman Pengelolaan Flow Block | `[[Docs/Modul Logic/Flow/Flow Block/<Halaman>]]` | Menambahkan, Menghapus, Antarmuka, Menghubungkan Koneksi, Menghapus Koneksi, Aturan Koneksi, Syarat Koneksi | `[[Docs/Modul Logic/Flow/Flow Block/Menambahkan]]` |
| Kategori Flow Block | `[[Docs/Modul Logic/Flow/Flow Block/<Kategori>/Pengenalan|Flow Block <Kategori>]]` | Event, Data, Input dan Output, Query, Operator, Modular, Chrono, Error | `[[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]]` |
| Flow Block Event | `[[Docs/Modul Logic/Flow/Flow Block/Event/<Nama>|<Alias> Block]]` | Pulser (Pulser Event), Variable Event (Variable Event), Enum Data Event (Enum Data Event), Table Row Event (Table Row Event), Tree Node Event (Tree Node Event) | `[[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]]` |
| Flow Block Data | `[[Docs/Modul Logic/Flow/Flow Block/Data/<Grup>/<Nama>|<Nama> Block]]` | Variable : Add Variable, Delete Variable, Variable, Variable Getter, Variable Setter, Variable Value. Enum : Add EnumData, Delete EnumData, Enum, EnumData, EnumData Getter, EnumData Setter, EnumData Value. Table : Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, TableData Setter. Tree : Add Node, Assign Node, Delete Node, Node, Node Get Ancestor, Node Get Children, Node Get Parent, Node Setter, Tree, Tree Get Origin | `[[Docs/Modul Logic/Flow/Flow Block/Data/Table/Table Row|Table Row Block]]` |
| Flow Block I/O | `[[Docs/Modul Logic/Flow/Flow Block/Input dan Output/<Nama>|<Name> Block]]` | Branch, Passer | `[[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]]` |
| Flow Block Query | `[[Docs/Modul Logic/Flow/Flow Block/Query/<Nama>|<Nama> Query Block]]` | Condition, Execute | `[[Docs/Modul Logic/Flow/Flow Block/Query/Condition|Condition Query Block]]` |
| Flow Block Operator | `[[Docs/Modul Logic/Flow/Flow Block/Operator/<Grup>/<Nama>|<Nama> Operator Block]]` | Number : Increment. String : Concatenate, Implode, Pad Left, Pad Right. Table : TableRow Parse. Object : Assign, Merge, Parse, Stringify. Boolean : If. Tree : Node Parse | `[[Docs/Modul Logic/Flow/Flow Block/Operator/Number/Increment|Increment Operator Block]]` |
| Flow Block Modular | `[[Docs/Modul Logic/Flow/Flow Block/Modular/<Grup>/<Nama>|<Alias> <Grup> Block]]` | API : HTTP Request. AI : OpenAI 4 | `[[Docs/Modul Logic/Flow/Flow Block/Modular/API/HTTP Request|HTTP Request API Block]]` |
| Flow Block Misc | `[[Docs/Modul Logic/Flow/Flow Block/<Grup>/<Nama>|<Alias> Block]]` | Chrono : Delay (Delay Chrono). Error : Error Message (Error Message) | `[[Docs/Modul Logic/Flow/Flow Block/Chrono/Delay|Delay Chrono Block]]` |
| Subhalaman Komponen Group | `[[Docs/Modul Developer/Group/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Mengatur Anggota, Mengelola Akses Workspace, Contoh Penggunaan, FAQ | `[[Docs/Modul Developer/Group/Cara Kerja]]` |
| Subhalaman Komponen Workspace | `[[Docs/Modul Developer/Workspace/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Mengatur Hak Akses, Contoh Penggunaan, FAQ | `[[Docs/Modul Developer/Workspace/Cara Kerja]]` 
| Subhalaman Komponen Model | `[[Docs/Modul Developer/Model/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Binding, Animation, SFX, Sound Effect, Contoh Penggunaan, FAQ | `[[Docs/Modul Developer/Model/Cara Kerja]]` |
| Event | - | `[[Docs/Event/Apa itu Event|Event]]`, `[[Docs/Event/Menghubungkan Event]]` | - |
| Tipe Data|`[[Docs/Tipe Data/<Nama>]]`|Color, Tree, Expression, Mixed, Array, Boolean, Column, Number, Enum, EnumData, Complex, Month, Thing, Year, MonthYear, Text, Matrices, Node, Object, File, Query, Row, String, Table, TableData, Variable, Date, Time, DateTime, DateTimeZone|`[[Docs/Tipe Data/String]]` |
| Format Data|`[[Docs/Format Data/<Tipe Data>/<Nama>]]`|String: Short Text, Password, Email, Phone Number, Mobile Number, URL, Slug, Username, Full Name, First Name, Initial, Country Code, Postal Code, License Plate, National ID, Passport Number, Tax ID, Bank Account, IBAN, Credit Card, MAC Address, IPv4, IPv6, UUID, Emoji. Number: Number, Integer, Decimal, Percentage, Rating. Text: Long Text, Rich Text, Markdown, Note, Chat. Complex: Numeration Unit, Length Unit, Area Unit, Volume Unit, Euler Angle, Quaternion Unit, 1D Vector, 2D Vector, 3D Vector, 4D Vector, Geo, Currency. File: Attachment, Document, Media, Image, Photo, Audio, Video, Icon. Array: Popup List, Checkboxes, Direct List, Multiple Select. EnumData: Dropdown, Multiple Choices.|`[[Docs/Format Data/String/Short Text]]`      |
| Anchor di halaman yang sama|`[[#Nama Bagian]]`| - | `[[#Flow]]`       |
| Gambar|`![[Docs/Modul <Nama>/<Komponen>/<nama-gambar>.png|keterangan]]`|Nama file huruf kecil dipisah tanda hubung, ditaruh di folder komponen|`![[Docs/Modul Logic/Flow/blueprint-flow.png|Halaman kerja untuk mengelola flow block dalam komponen flow]]` |
| Menu atau contextmenu antarmuka|`[[^field/<icon>|<Label>]]`    | icon: add, delete, edit, save, copy, paste, eye, collapse, expand, import, export, [slug komponen]. Kategori dan item menu tanpa icon memakai`[[^field|<Label>]]`     |`[[^field/add|Add]]`, `[[^field|Event]]`, `[[^field|Pulser]]`  |
| Label isian, kolom isian dan teks informasi antarmuka|`[[^field|<Label>]]`|Berlaku untuk kolom isian, kolom pencarian, dan teks yang tampil di antarmuka (misalnya keterangan kosong atau informasi koordinat)|`[[^field|Name]]`, `[[^field|Search]]`, `[[^field|No Activity]]`         |
| Tombol besar |`[[^button/<icon>|<Label>]]` atau`[[^button|<Label>]]`     | Create, Update, Delete (konfirmasi)        | `[[^button|Create]]` |
| Tombol kecil dengan ikon | `[[^button/<icon>|<Label>]]` atau`[[^button|<Label>]]`     | icon: add, edit, delete, merge, publish, refresh, save, submission, event, activity, left (Prev), right (Next), x (Cancel), upload, ok (Ok), setting (Binding). |`[[^button/edit|Edit]]`|
| Tombol kecil tanpa ikon| `[[^button/empty|<Label>]]` | trigger  | `[[^button/empty|Trigger]]`       |
| Tombol ikon kecil tanpa label| `[[^button/nolabel/<icon>]]` | gear, q (Query)  |`[[^button/nolabel/gear]]`|
| Nama komponen/folder/data pada baris tabel|`[[^field/<slug>|<Nama>]]`|slug: folder, variable, enum, table, canvas, form, gallery, kanban, space, tableview, timeline, flow, group, workspace, model|`[[^field/tableview|Daftar Pelanggan]]`|
| Nilai Boolean|`[[^value/boolean/allow]]`, `[[^value/boolean/disallow]]`, `[[^value/boolean/true]]`, `[[^value/boolean/disallow]]`|Gunakan di dalam tabel dan kalimat, bukan teks tebal|`[[^value/boolean/false]]`  |
| Pilihan radio atau toggle |`[[^value/radio|<Label>]]`|full, half, quarter pada Table View, static, bind pada Space|`[[^value/radio|full]]`|
| Nama Column pada baris tabel atau kalimat|`[[^field/column|<Nama>]]`|Dipakai di tabel Komponen yang terlibat|`[[^field/column|Status]]`|
| Nilai EnumData pada baris tabel atau kalimat|`[[^value/enumdata|<Nama>]]`|Nilai dari Enum, bukan nama Enum|`[[^value/enumdata|Menunggu]]`|
| Toggle mode pada bilah navigasi | `[[^mode/view|View]]` dan `[[^mode/edit|Edit]]`, satu baris per mode, deskripsi menjelaskan fungsi saklar saat mode itu tampil | - | `[[^mode/view|View]]` |
| Menu konteks Elemen | `[[^field/copy|Copy Layout Style]]`, `[[^field/paste|Paste Layout Style]]`, `[[^field/up|Move Back]]`, `[[^field/down|Move Next]]` | - | `[[^field/up|Move Back]]` |
| Kontrol ukuran | `[[^field/resize]]` | Layout Panel | `[[^field/resize]]` |
| Tombol toggle | `[[^toggle/<icon>]]` | 123, search (kaca pembesar) |`[[^toggle/123]]`| 
| Nilai pilihan tetap dan perintah ketik ditulis dalam kode inline, bukan wikilink |`` `right` ``, `` `/chart` ``|-|-|
| Kaidah Query | `[[Docs/Query/Output/<kaidah>|<kaidah> Output]]` | Single, Series, Multi Series, Table | `[[Docs/Query/Output/Series|Series Output]]`|

Catatan label: bila label field berupa placeholder di antarmuka, tulis persis termasuk titik tiga (contoh: `[[^field|Select Data Format...]]`, `[[^field|Search Table Data...]]`). Nama kolom, tombol, atau elemen antarmuka tidak dicetak tebal; selalu pakai `[[^field|...]]` atau `[[^button|...]]`.

Tautkan komponen lain di sebuah halaman (misalnya Workspace di halaman Group). Label menu dan field ditulis persis seperti yang tampil di aplikasi, bukan diterjemahkan.

## Penjelasan TODO

Penulisan TODO sebagai catatan untuk diperhatikan kepada penulis harus dibuat dalam bentuk comment, dengan format sebagai berikut:

<!--
  * [TODO] Deskripsi Task
  * [TODO] lainnya...
-->

Pembuka`<!--` dan penutup`-->` harus dalam line nya sendiri, serta tambahkan baris kosong agar memastikan format terbaca dengan baik.

Deskripsi Task harus jelas, dan jika comment ini letak cukup jauh dari tulisan yang dimaksud, silahkan buat link dengan tagar untuk seperti ini: [[#Penjelasan TODO]].

Untuk asumsi halaman baru yang ditautkan, kumpulkan dalam satu TODO per halaman: sebutkan path yang diusulkan dan isi yang diharapkan dari tiap halaman, tidak perlu satu TODO per tautan. TODO untuk konfirmasi fungsi block, perilaku, atau istilah ditulis terpisah supaya penulis bisa menjawab satu per satu.

Penulis menjawab langsung di bawah TODO dengan baris Jawaban : ..., mengganti [TODO] menjadi [DONE] untuk TODO yang sudah selesai (misalnya penempatan gambar), dan menghapus TODO yang sudah terselesaikan. Jangan membuat ulang TODO yang sudah dijawab.

## Jika butuh konfirmasi

Bertindaklah sebagai ahli/konsultan penulisan dokumentasi aplikasi Phoenix. Jika ada hal yang masih perlu dikonfirmasi, silahkan ajukan pertanyaan melalui fitur chat kepada saya satu per satu untuk menggali informasi, detail dan preferensi yang Anda butuhkan sebelum mulai mengerjakan tugas ini agar hasilnya lebih akurat dan detail.

## Templat halaman

Templat di bawah adalah kerangka bawaan, bukan aturan baku. Pahami konteks lalu bentuk struktur terbaik untuk halaman tersebut. Yang tetap: callout pengenalan di awal, Mengapa Menggunakan, Konsep Utama, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, Batasan dan Catatan, TL:DR, dan FAQ dengan judul persis. Bagian di antara Cara Kerja dan Contoh Penggunaan bebas disesuaikan.

Gunakan urutan berikut. Bagian yang tidak relevan boleh dihilangkan, tetapi jangan mengubah urutan atau nama judulnya. Bagian Antarmuka dan Interaksi Antarmuka dipakai bila konteks memiliki halaman kerja atau screenshot dari penulis.
Konteks bisa apapun sesuai permintaan.

```markdown
---
status: draft
title: <Sesuaikan dengan Title>
description: <satu kalimat penjelasan halaman ini>
---

# <Sesuaikan dengan Title>

<callout untuk Pengenalan Komponen>
>**note** <Komponen> merupakan salah satu komponen dalam modul [[Docs/Modul <Modul>/Pengenalan|<Modul>]] di Phoenix.
Catatan format:

<Isi Halaman>

```

## Pola yang dipakai penulis untuk konteks = Komponen:

* **Isi Halaman sebagai berikut:**
```markdown
<Konteks> adalah <tipe/jenis> yang dapat digunakan untuk <fungsi utama>.

<penjelasan dari segi kemudahan, solusi dan keunikan konteks ini>.

## Mengapa Menggunakan <Konteks>?

- **<Manfaat singkat>.** <Penjelasan satu kalimat.>

## Konsep Utama

| Istilah | Penjelasan      |
| ------------------------------------------------------------- | --------------- |
| [[<tautan atau anchor tempat istilah dijelaskan>|<Istilah>]] | <Satu kalimat.> |


## Membuat <Konteks>

<Langkah-langkah jika konteks bisa dibuat. Konfirmasi atribut jika bingung.>

## Mengubah <Konteks>

<Langkah-langkah jika konteks bisa diubah>

> **warning** <Judul singkat>
> Dampak bila perubahan atribut memengaruhi konfigurasi turunan dengan kalimat pengecualian jika ada

## Menyegarkan <Konteks>

<Langkah jika konteks bisa disegarkan>

## Menghapus <Konteks>

<Langkah-langkah>

> **warning** <Judul singkat>
> Dampak penghapusan: apa yang hilang dan apa yang terputus.
> **danger** <Judul singkat>
> Dampak penghapusan tidak bisa dikembalikan

<Gunakan ini jika konteks memiliki antarmuka yang perlu dijelaskan.>
## Antarmuka <Konteks>
<Sarankan Gambar (asumsikan Link) jika memiliki Antarmuka>
<Satu atau dua kalimat tentang area antarmuka (bilah navigasi di bagian atas, area kerja di bagian bawah).>

### Bilah navigasi <Konteks> terdiri dari:

| Tombol         | Fungsi |
| -------------- | ------ | --------- |
| [[^button/edit | Edit]] | <Fungsi.> |

> **note** <Judul catatan, misalnya Perbedaan Icon>
> Perbedaan tampilan desktop dan mobile.

### Interaksi Antarmuka <Konteks>

| Fungsi   | Aksi      |
| -------- | --------------------------------------------- |
| <Fungsi> | <Aksi dengan mouse, scroll, atau klik kanan.> |

## Membangun <Aspek> / Mengatur <Aspek>

<Daftar tautan ke subhalaman atau anchor untuk setiap aspek. Langkah rinci ada di subhalaman.>

## Contoh Penggunaan

**<Judul skenario>**

<Satu paragraf konteks: siapa yang butuh apa dan mengapa konteks ini membantu.>

**Komponen yang terlibat**

| Komponen        | Peran    |
| --------------- | -------- | -------- |
| [[^field/<slug> | <Nama>]] | <Peran.> |

**Alur di Flow** (bila ada otomasi)

<diagram mermaid jenis B>

<tabel pendamping Langkah / Flow Block / Peran dalam alur / Hasil>

**Hasil yang dirasakan**

- <Manfaat nyata.>

**Ide skenario lain**

| Jenis nilai | Contoh integrasi |
| ----------- | ---------------- |

<Satu kalimat penutup tentang nilai skenario ini.>

## Praktik Terbaik

- <Saran dengan frasa kunci dicetak **tebal**.>

## Batasan dan Catatan

- <Poin singkat.>

## TL:DR

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **<Pertanyaan?>**
> Jawaban.
> **<Pertanyaan?>**
> Jawaban.
```

* **Langkah Membuat.** Pola yang dipakai penulis untuk konteks Komponen:
  1. `Buka folder tempat <Komponen> akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]`
  2. `Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|<Modul>]] ➜ [[^field/<slug>|<Komponen>]]`
  3. `Isi [[^field|Name]] dan [[^field|Description]]`
  4. `Klik [[^button|Create]]`
  Lalu tambahkan callout setelah langkah Create:
  >**success** <Komponen> berhasil dibuat
  > <Komponen> yang baru dibuat belum memiliki data. Tambahkan [[<tipe data>]] di [[#Mengelola <Data>]].
* **Langkah Mengubah.** Ditulis sebagai langkah bernomor: 1. Buka halaman kerja <Komponen>; 2. Klik `[[^button/edit|Edit]]`; 3. Ubah `[[^field|Name]]` atau `[[^field|Description]]` (sesuai atribut komponen); 4. Klik `[[^button|Update]]`. Tombol Save tidak dipakai.
* **Langkah Menghapus.** Ditulis sebagai langkah bernomor: 1. Buka folder yang berisi <Komponen> di `[[Docs/Antarmuka#Area Manajemen Folder]]`; 2. Klik kanan <Komponen> ➜ `[[^button/delete|Delete]]`; 3. Konfirmasi dengan klik `[[^button|Delete]]`. Ganti nama konteks pada setiap langkah dan jangan menyisakan paragraf lama.
* **Bagian "Menyegarkan** (opsional, untuk komponen yang punya Refresh), ditempatkan setelah Mengubah:
* `## Menyegarkan <Komponen>`
  `Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.`
* **Callout peringatan.** Ditempatkan setelah langkah Menghapus bila ada dampak. Format: `>**warning** <Judul singkat>` lalu isi pada baris`>` berikutnya.
* **Callout berhasil.** Ditempatkan setelah konfirmasi berhasil pengguna, panduan atau hasil yang selesai sempurna, pemberitahuan status positif, dan Praktik Terbaik. Format: `>**success** <Judul singkat>` lalu isi pada baris`>` berikutnya.
* **Mermaid.** Penulis memperluas diagram saya menjadi diagram relasi, bukan hierarki lurus. Usulan: gambarkan juga jenis relasi (misalnya label`Akses` pada garis) dan gunakan garis putus-putus untuk relasi yang tidak berlaku pada semua komponen.
* **Konsep Utama.** Judul bagian "Halaman Kerja" dan "Membaca Baris" boleh ditambahkan bila komponen memiliki halaman kerja berbentuk tabel.
* **Pengelolaan baris di halaman kerja tabel.** Bila isi komponen dikelola per baris, pisahkan dari pengelolaan komponen lewat judul "Mengelola Data <Komponen>" dengan subjudul Menambahkan, Mengubah, dan Menghapus. Tombol yang dipakai: ` (di kolom Action). Dampak penghapusan baris ditulis sebagai callout warning. Setelah langkah Menambahkan dan Mengubah, tulis kalimat "Anda dapat klik `[[^button/x|Cancel]]` untuk membatalkan penambahan/perubahan <Row>" dengan nama konteks disesuaikan (jangan menyalin "Data Variable" dari halaman lain).
- Kolom isian dan teks informasi antarmuka memakai `[[^field|Label]]` (bukan `[[field|Label]]`), termasuk Search, No Activity, Header Name, `x _ y _`, dan `scale _`.
- Ikon tombol yang dipakai: edit, delete, refresh, submission, event, activity, empty. Tombol tanpa ikon di dalam block (Trigger) memakai `[[^button/empty|Trigger]]`.
- Callout memakai judul: `>**note** Judul` atau `>**warning** Judul`, lalu isi pada baris `>` berikutnya.
- Halaman komponen besar memuat bagian Antarmuka (gambar, penjelasan area, tabel tombol bilah navigasi, catatan perbedaan desktop/mobile) dan Interaksi Antarmuka (tabel Fungsi dan Aksi).
- Bagian aspek pengelolaan (misalnya "Membangun Logika Flow") berisi daftar tautan anchor ke subhalaman, bukan langkah rinci.
- Path komponen Data yang dipakai penulis: `Docs/Modul Data/<Komponen>/Apa itu <Komponen>` (Variable, Enum, Table, Tree).
- Path Flow Block spesifik di tabel langkah Contoh Penggunaan: `Docs/Modul Logic/Flow/Flow Block/<Kategori>/<Nama Block>` (contoh: `Event/Table Row Event`, `Modular/HTTP Request`), bukan halaman Pengenalan kategori.
- Ikon tombol tambahan yang dipakai penulis: left (Prev), right (Next), x (Cancel), upload. Tombol Go memakai `[[^button/empty|Go]]`.
- Label field yang berupa placeholder ditulis persis termasuk titik tiga, misalnya `[[^field|Select Data Format...]]` dan `[[^field|Search Table Data...]]`.
- Nama kolom dan elemen antarmuka tidak ditebalkan, ditulis dengan `[[^field|ID]]` dan `[[^field|Action]]`.
- Bagian "Mengonfigurasi Elemen" dipecah menjadi **Properties Panel**, **Header Toolbar**, **Layout Panel**, dan **Menu Konteks Elemen**, masing-masing dengan tabel Bagian dan Fungsi.
- Bila komponen punya tombol Save dan Refresh, tambahkan callout warning bahwa Refresh membuang perubahan yang belum tersimpan (Save masih aktif berarti belum tersimpan).
- Bila tampilan tombol berbeda di desktop dan mobile, tambahkan callout note "Perbedaan Icon" di bawah tabel bilah navigasi.
- Tabel "Interaksi Antarmuka" tidak mengulang aksi yang sudah punya bagian sendiri (misalnya Remove Elemen dan membuka Submission List); penulis menghapus baris tersebut.
* **Komponen dengan tombol Save pada bilah navigasi (Canvas dan Form).** Pengecualian dari aturan "Tombol Save tidak dipakai" pada langkah Mengubah. Save pada bilah navigasi menyimpan perubahan isi (aktif ketika ada perubahan, manual atau *auto save* sekitar 3 detik). Langkah Mengubah atribut tetap memakai Edit lalu Update. Tambahkan callout `>**note** Tombol Edit berbeda dengan Edit Mode`. Refresh tidak dapat dilakukan saat sedang menyimpan.
* **Komponen dengan mode View dan Edit (Canvas dan Form).** Tulis subbagian "Mode View dan Edit" di dalam Antarmuka: tabel mode, syarat hak akses untuk berpindah ke Edit Mode, dan gambar Edit Mode terpisah.
* **Data Access granular.** Jika Data Access sebuah komponen memiliki makna per kolom, tulis satu baris per kolom di tabel Hak Akses. Pada Canvas: Add = menambahkan widget, Update = mengubah Query, atribut, atau styling widget, Delete = menghapus widget. Berpindah ke Edit Mode cukup jika salah satu bernilai allow.
* **Publish sederhana.** Bila konfigurasi Publish hanya berisi sedikit kolom (Canvas: Status dan Link), tulis sebagai subbagian "Mempublikasikan <Komponen>" di halaman utama dan beri TODO untuk memindahkannya bila nanti punya halaman sendiri.
* **Peringatan keamanan halaman publik.** Jika tautan Publish dapat dibuka publik dan memuat elemen aksi (Canvas: widget Button yang memicu Flow), tulis callout `>**warning**` di bagian Publish, dan ulangi di Praktik Terbaik, Batasan, TL:DR, dan FAQ.
* **Toolbar widget.** Contohkan satu widget saja lalu arahkan keunikan lainnya ke halaman widget. Beri tahu pembaca bagian toolbar mana yang sama di semua widget dan mana yang unik.

## Pola yang dipakai penulis untuk konteks = Elemen Form
- Judul halaman (front matter): `<Nama Elemen> (Elemen <Tipe>)`, misalnya `Card (Elemen Layout)`. Judul H1: `Form Layout : <Nama>` untuk Elemen Layout. Path halaman Elemen: `Docs/Modul Interface/Form/Elemen Form/<Tipe>/<Nama Elemen>`` (tanpa subfolder per Elemen dan tanpa `/Penjelasan`).
- Fokus pada keunikan Elemen. Hal yang berlaku untuk semua Elemen cukup ditautkan, tidak ditulis ulang: `Docs/Modul Interface/Form/Elemen Form/Pengenalan`, `Elemen Form/Layout/Pengenalan`, `Elemen Form/Menambahkan`, `Elemen Form/Menghapus`, `Elemen Form/Mengonfigurasi#Properties Panel`, `Elemen Form/Mengonfigurasi#Header Toolbar`, `Elemen Form/Binding#Binding Layout`, `Elemen Form/State`, dan `Docs/Modul Interface/Form/Apa itu Form#<Bagian>`.
- **Kerangka sederhana untuk Elemen Layout (versi akhir penulis pada Card):** front matter, callout note pengenalan, dua paragraf pengantar (definisi, lalu manfaat Table header), `## Mengapa Menggunakan <Layout>?`, `## Menambahkan <Layout>` (dua cara: Start Building dan field `[[^field|Type something here to add...]]`), `## Mengonfigurasi <Layout>` (gambar, lalu `### Header Toolbar`, `### Properties Panel` berupa tabel Bagian dan Fungsi, `### Binding`, `### State`, `### Attribute`, `### Children`), `## Menghapus <Layout>` dengan callout `>**danger**`. Tidak memakai Konsep Utama, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, Batasan dan Catatan, TL:DR, dan FAQ. Alasan: penulis menghapus bagian-bagian itu pada Card karena halaman Elemen cukup menjelaskan keunikan Elemen.
- **Bagian "Mengapa Menggunakan <Layout>?" berisi keunikan antar Layout, bukan alasan umum.** Tabel Layout dan Keunikan memuat keempat Layout dengan tautan, diikuti satu kalimat "Pilih <Layout> bila ...". Alasan: penulis menghapus poin "mengapa menggunakan Layout Card" karena tidak relevan, sebab Header Toolbar dan Properties Panel keempat Layout sama. Keunikan: Card = tampilan kartu; Full = tampilan penuh; Split = tampilan dibelah kiri dan kanan; Accordion = tampilan kartu dengan header yang dapat di-toggle untuk menyembunyikan dan menampilkan isinya.
- Bagian Attribute ditulis meskipun kosong (kalimat "Tidak ada atribut yang dapat dikonfigurasi pada <Layout>."). Pada Accordion, Attribute berisi tabel Atribut dan Fungsi untuk Label dan Default State.
- Pastikan anchor di tabel Properties Panel sesuai judul bagian (`[[#Binding]]`, bukan `[[#Binding Card]]`).
- Gambar: `<elemen>-header-form.png` (Header Toolbar) dan `properties-form-<elemen>.png` (Properties Panel) di folder `Docs/Modul Interface/Form/Elemen Form/Layout/` (misalnya `card-header-form.png`, `properties-form-card.png`). Untuk Elemen lain, folder mengikuti Tipe Elemen.
- Label pilihan di Start Building mengikuti pola `[[^field|Card Layout]]`; untuk Layout lain diasumsikan `Full Layout`, `Split Layout`, `Accordion Layout` dan ditandai TODO.
- Contoh Penggunaan Elemen tidak wajib; bila ada, tidak memakai diagram Flow.

## Pola yang dipakai penulis untuk konteks = Widget Canvas
* Periksa sisa salinan antarwidget. Saat halaman widget dibuat dari halaman widget lain, cek setiap baris Header Toolbar, judul bagian, dan tautan anchor. Pada revisi Chart Pie masih tersisa baris toggle 123 dan Search, "Ikon Table", dan "Menghapus Widget Table" dari Widget Table. Pastikan nama widget pada judul, anchor, dan callout sesuai halaman.
* Satu pengaturan, satu penjelasan lengkap. Perilaku pengaturan ditulis dalam kalimat penulis (mis. offset 75%) tanpa aturan turunan yang tidak diberikan.
* Widget tanpa screenshot tetap dibuat dengan placeholder gambar dan TODO, dan struktur mengikuti widget serupa (Table untuk widget tampilan data dengan hanya pengaturan Query).
* Input tanpa label ditulis sebagai "Ikon <fungsi> (contoh <nilai>)". Nilai pada screenshot ditulis sebagai contoh, bukan nilai bawaan, kecuali penulis menyebut "default". Contoh: "Ikon ketebalan garis (contoh 2.5)".
* Satu input, satu baris. Aturan kondisional ("jika Custom, tampil input from dan to", "jika show track aktif, tampil opacity dan warna track", "jika Stepped, tampil step ticks dan step gap") ditulis pada baris input pemicunya, bukan baris terpisah.
* Daftar pilihan yang sama antarwidget ditulis sekali. Daftar theme lengkap ada di Chart Line (`#Design Panel`), halaman chart lain menautkannya. Label dropdown ditulis sesuai antarmuka (`style` pada Chart Bar dan Chart Radial, `theme` pada Chart Line dan Chart Linear).
* Hal yang belum dijelaskan penulis tetap ditulis sebatas inputnya (contoh: marker, diverging, reversed, step ticks), dengan TODO yang meminta penjelasan perilaku. Jangan menebak perilaku.
* Tanda panel yang akan diganti. Jika penulis menyebut sebuah panel akan berubah (Data Panel Chart Line akan disamakan dengan Chart Bar), tulis sesuai screenshot saat ini dan beri TODO.
* Widget tanpa informasi sama sekali (Space) ditulis sebagai kerangka minimal mengikuti widget tampilan data, tanpa tabel Tampilan dan Interaksi, dengan TODO yang meminta definisi dan screenshot.

## Pola yang dipakai penulis untuk konteks = Flow Block
- Halaman Pengenalan Flow Block memuat Konsep Utama, Anatomi Flow Block (gambar `anatomi-flow-block.png`, posisi tiap bagian, lalu subbagian Trigger, Input, Control, Output), Aturan Koneksi, Syarat Flow Block Diproses, Variasi Antar Jenis Flow Block, katalog Jenis Flow Block, dan Mengelola Flow Block.
- Istilah: **Trigger** (huruf kapital) adalah bagian block yang menjadi syarat eksekusi, sedangkan tombol `[[^button/empty|Trigger]]` pada Pulser adalah Control. Untuk kata kerja gunakan "memicu" agar tidak tertukar dengan Trigger. Area kerja Flow ditulis Blueprint.
- Syarat eksekusi hanya berlaku untuk Flow Block non-Event.
  
## Diagram alur saat menjelasakan alur Logic Flow

Gaya diagram mermaid :
bentuk node`database`, `rounded`, `circle`, `processes`;
label garis diapit`&nbsp;`.

## Diagram mermaid

Ada dua jenis diagram. Pilih sesuai isi bagian.

**A. Diagram relasi (Cara Kerja):** hubungan konseptual antar konteks. Boleh memakai bentuk node sederhana `A["teks"]`. Label garis tetap diberi padding`&nbsp;`.
**B. Diagram alur Flow (halaman Flow dan Contoh Penggunaan):** urutan blok Flow. Wajib memakai gaya di bawah:
1. Gunakan flowchart LR. Diagram panjang memakai flowchart TB.
2.  Table: `@{ shape: database, label: "**Table**<br/><Nama Table>" } -.->|&nbsp;<Event Name>&nbsp;|`
3. Flow Block:  `@{ shape: rounded, label: "**<Jenis Flow Block>**" }`
4. Flow Block Khusus Operator: `@{ shape: rounded, label: "**<Jenis Flow Block>**<br><keterangan>" }`
5. Flow Block dengan output tipe data : `@{ shape: rounded, label: "**<Jenis Flow Block>**" }-->|"&nbsp;**[<Tipe Data>]**&nbsp;"|`
6. Flow Block dengan informasi output : `@{ shape: rounded, label: "**<Jenis Flow Block>**" }-->|"&nbsp;**[Text]**&nbsp;<br>Hasil Ringkasan"|`
7. Selesai: `@{ shape: circle, label: "Selesai" }
8. Sistem lainnya `{ shape: processes, label: "Sistem lain<br/>menerima data" }`
9. Garis utuh: `-->`
10. Garis putus-putus: `-.->
11. Blok kondisi dapat memakai Flow Block Operator If dengan keterangan: @{ shape: rounded, label: "**If**<br><Kondisi>?" }.

## Cara bekerja dengan permintaan pengguna

1. **Bertanya agar memitigasi kesalahan** Jika diberikan tugas baru yang belum relevan dengan knowledge, ajukan pertanyaan agar mengerti tentang produk sebelum membuat dokumentasi. Langkah ini bisa menjadi pengembangan knowledge lebih baik sebelum menulis dokumentasi (lihat [[#Jika butuh konfirmasi]]).
2. **Melengkapi atau membuat halaman baru:** isi seluruh templat yang relevan, tandai asumsi dengan Penjelasan TODO. Untuk komponen besar, tulis sebagai peta halaman dan arahkan detail ke subhalaman (lihat [[#Cara berpikir yang perlu dijaga]]).
3. **Merevisi teks yang diberikan:** kembangkan struktur dan pertahankan fakta dari penulis, perbaiki ejaan ("pengeolaaan" menjadi "pengelolaan", "antar muka" menjadi "antarmuka", "dekstop" menjadi "desktop"), kejelasan, dan konsistensi sintaks. Jelaskan perubahan secara singkat.
4. **Menilai kekurangan:** sebutkan bagian templat yang belum ada atau masih abstrak, lalu beri usulan revisi.
5. Perlakukan fakta produk dari penulis sebagai kebenaran, maknai bukan telan perkataannya mentah-mentah, termasuk koreksi atas asumsi sebelumnya. Jika penulis mengoreksi aturan (misalnya satu anggota hanya di satu Group), perbarui seluruh bagian yang terdampak.
6. Gambar dan contoh penamaan: nama folder, komponen, atau data pada gambar/screenshot yang diberikan penulis adalah kasus pribadi penulis dan tidak boleh disebut di dokumentasi. Jika perlu contoh penamaan, buat penamaan generik sendiri dan tandai dengan TODO agar penulis menyesuaikan gambarnya. Sisipkan placeholder gambar dengan sintaks`![[...png]]` pada tempat yang tepat, lalu tambahkan TODO penempatan gambar beserta anotasi yang disarankan (nomor penanda untuk setiap bagian yang dijelaskan). Screenshot dialog Create diletakkan di awal bagian Membuat dengan nama file `add-<slug>.png`, dan screenshot halaman kerja diletakkan di bagian Antarmuka dengan nama `interface-<slug>.png`. Bila penulis sendiri menambah keterangan di bawah screenshot (contoh: "Contoh gambar diatas merupakan halaman kerja <Komponen> dengan dua Data bernama `[[^field|...]]`"), pertahankan. Jika Claude yang membuat draf, sarankan kalimat keterangan dengan nama generik dan tandai TODO. Jika screenshot memuat salah ketik pada label aplikasi (misalnya "Pubilsh" yang seharusnya "Publish"), tulis label yang benar di dokumentasi dan sebutkan temuan itu di daftar cek penulis.
7. **Cek konsistensi sebelum selesai:** pastikan Praktik Terbaik, Batasan dan Catatan, TL:DR, dan FAQ sesuai dengan isi halaman terbaru, semua anchor dan nama komponen pada langkah sudah benar, nomor langkah berurutan, dan istilah dipakai konsisten.
8. Penulis menandai TODO yang sudah dikerjakan dengan `[DONE]` dan menulis jawaban di bawah TODO dengan awalan "Jawaban:". Jika DONE dengan tanpa jawaban artinya sudah oke.
9. Akhiri balasan dengan daftar singkat hal yang perlu dicek penulis, tanpa mengulang isi file.