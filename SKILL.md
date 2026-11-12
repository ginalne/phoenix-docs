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
| Halaman konsep umum | - | `[[Docs/Dasar/Apa itu Pro|Pro]]`, `[[Docs/Dasar/Apa itu Komponen|Komponen]]`, `[[Docs/Dasar/Apa itu Folder|Folder]]` | - |
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
| Halaman Pengelolaan Node | `[[Docs/Modul Data/Tree/Node/<Halaman>]]` | Menambahkan, Mengubah Nama, Mengubah Urutan, Menghapus, Melihat Detail, Mengatur Tampilan, Mengekspor, Mengimpor, Format Import dan Export | `[[Docs/Modul Data/Tree/Node/Menambahkan]]` |
| Subhalaman Komponen Canvas | `[[Docs/Modul Interface/Canvas/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Binding, Layout, Mempublikasi, Hak Akses, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Canvas/Cara Kerja]]` |
| Halaman Umum Canvas Widget | `[[Docs/Modul Interface/Canvas/Widget/<Halaman>}]]` | Menambahkan, Menghapus, Mengonfigurasi | `[[Docs/Modul Data/Canvas/Template/Pengenalan]]` |
| Widget Canvas | `[[Docs/Modul Interface/Canvas/Widget/<Grup>/<Nama>|Widget <Alias>` | Basic : Button (Button), Text (Text). Chart : Bar (Chart Bar), Line (Chart Line), Linear (Chart Linear), Pie (Chart Pie), Radial (Chart Radial). Interface : Gallery (Gallery), Gantt (Gantt), Kanban (Kanban), Space (Space), Table (Table), Timeline (Timeline) | `[[Docs/Modul Interface/Form/Widget/Chart/Pie|Widget Chart Pie]]` |
| Subhalaman Komponen Form | `[[Docs/Modul Interface/Form/<Sub Halaman>]]` | Cara Kerja, Membuat Baru, Mengubah, Menghapus, Antarmuka, Form Page, Submission, Mempublikasi, Hak Akses, Contoh Penggunaan, FAQ | `[[Docs/Modul Interface/Form/Cara Kerja]]` |
| Halaman Umum Elemen Form | `[[Docs/Modul Interface/Form/Elemen/<Halaman>}]]` | Menambahkan, Menghapus, Mengonfigurasi | `[[Docs/Modul Data/Form/Elemen/Pengenalan]]` |
| Halaman pendamping Properties Panel Elemen | `[[Docs/Modul Interface/Form/Elemen/<Property>|Form <Property>]]` |, State, Validators, Binding | `[[Docs/Modul Interface/Form/Elemen/State|Form State]]`|
| Pengenalan Grup Elemen Form | `[[Docs/Modul Interface/Form/Elemen/<Grup>/Pengenalan|Elemen <Grup>]]` | Layout, Display, Input | `[[Docs/Modul Data/Form/Elemen/Layout/Pengenalan|Elemen Layout]]` |
| Elemen Form | `[[Docs/Modul Interface/Form/Elemen/<Grup>/<Nama>}]]` | Layout: Accordion, Card, Full, Split. Display: Chrono, QR, Table, Text, Tooltip. Input: Basic, List, List Column, Quiz, Table, Table Column | `[[Docs/Modul Interface/Form/Elemen/Layout/Accordion]]` |
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
| Pengenalan kelompok Flow Block | `[[Docs/Modul Logic/Flow/Flow Block/<Grup>/Pengenalan|Flow Block <Grup>]]` | Event, Input dan Output, Query, Operator, Modular, Chrono, Error | `[[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]]` |
| Pengenalan kelompok Flow Block Data | `[[Docs/Modul Logic/Flow/Flow Block/Data <Grup>/Pengenalan|Flow Block Data <Grup>]]` | Variable, Enum, Table, Tree | `[[Docs/Modul Logic/Flow/Flow Block/Data Table/Pengenalan|Flow Block Data Table]]` |
| Flow Block Event | `[[Docs/Modul Logic/Flow/Flow Block/Event/<Nama>|<Alias> Block]]` | Pulser (Pulser Event), Variable Event (Variable Event), Enum Data Event (Enum Data Event), Table Row Event (Table Row Event), Tree Node Event (Tree Node Event) | `[[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser Event Block]]` |
| Flow Block Data | `[[Docs/Modul Logic/Flow/Flow Block/Data <Grup>/<Nama>|<Nama> Block]]` | Variable : Add Variable, Delete Variable, Variable, Variable Getter, Variable Setter, Variable Value. Enum : Add EnumData, Delete EnumData, Enum, EnumData, EnumData Getter, EnumData Setter, EnumData Value. Table : Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, TableData Setter. Tree : Add Node, Assign Node, Delete Node, Node, Node Get Ancestor, Node Get Children, Node Get Parent, Node Setter, Tree, Tree Get Origin | `[[Docs/Modul Logic/Flow/Flow Block/Data Table/Table Row|Table Row Block]]` |
| Flow Block I/O | `[[Docs/Modul Logic/Flow/Flow Block/Input dan Output/<Nama>|<Name> Block]]` | Branch, Passer | `[[Docs/Modul Logic/Flow/Flow Block/Input dan Output/Branch|Branch Block]]` |
| Flow Block Query | `[[Docs/Modul Logic/Flow/Flow Block/Query/<Grup>/<Nama>|Query <Nama> Block]]` | Condition : Add Table Filter. Execute : Table Output | `[[Docs/Modul Logic/Flow/Flow Block/Query/Condition/Add Table Filter|Query Add Table Filter Block]]` |
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
| Tombol besar |`[[^button|<Label>]]`     | Create, Update, Delete (konfirmasi)        | `[[^button|Create]]` |
| Tombol kecil dengan ikon | `[[^button/<icon>|<Label>]]` | icon: add, edit, delete, merge, publish, refresh, save, submission, event, activity, left (Prev), right (Next), x (Cancel), upload, ok (Ok), setting (Binding). | `[[^button/edit|Edit]]` |
| Tombol kecil tanpa ikon| `[[^button/empty|<Label>]]` | trigger  | `[[^button/empty|Trigger]]` |
| Tombol ikon kecil tanpa label| `[[^button/nolabel/<icon>]]` | gear, q (Query)  | `[[^button/nolabel/gear]]` |
| Nama komponen/folder/data pada baris tabel|`[[^field/<slug>|<Nama>]]`|slug: folder, variable, enum, table, canvas, form, gallery, kanban, space, tableview, timeline, flow, group, workspace, model|`[[^field/tableview|Daftar Pelanggan]]`|
| Nilai Boolean|`[[^value/boolean/allow]]`, `[[^value/boolean/disallow]]`, `[[^value/boolean/true]]`, `[[^value/boolean/disallow]]`|Gunakan di dalam tabel dan kalimat, bukan teks tebal|`[[^value/boolean/false]]`  |
| Pilihan radio atau toggle | `[[^value/radio|<Label>]]`|full, half, quarter pada Table View, static, bind pada Space, move pada Area Manajemen Folder|`[[^value/radio|full]]`|
| Nama Column pada baris tabel atau kalimat| `[[^field/column|<Nama>]]`|Dipakai di tabel Komponen yang terlibat|`[[^field/column|Status]]`|
| Nilai EnumData pada baris tabel atau kalimat| `[[^value/enumdata|<Nama>]]`|Nilai dari Enum, bukan nama Enum|`[[^value/enumdata|Menunggu]]`|
| Nilai Contoh bertipedata | `[[^value/<Tipe>|<Nama atau Nilai>]]`|boolean, color, column, complex, date, datetime, datetimezone, enum, enumdata, expression, file, matrices, month, monthyear, node, number, object, query, row, string, table, tabledata, text, thing, time, tree, variable, year |`[[^value/enumdata|Menunggu]]`|
| Toggle mode pada bilah navigasi | `[[^mode/view|View]]` dan `[[^mode/edit|Edit]]`, satu baris per mode, deskripsi menjelaskan fungsi saklar saat mode itu tampil | - | `[[^mode/view|View]]` |
| Menu konteks Elemen | `[[^field/copy|Copy Layout Style]]`, `[[^field/paste|Paste Layout Style]]`, `[[^field/up|Move Back]]`, `[[^field/down|Move Next]]` | - | `[[^field/up|Move Back]]` |
| Kontrol ukuran | `[[^field/resize]]` | Layout Panel | `[[^field/resize]]` |
| Tombol toggle | `[[^toggle/<icon>]]` | 123, search (kaca pembesar) |`[[^toggle/123]]`| 
| Nilai pilihan tetap dan perintah ketik ditulis dalam kode inline, bukan wikilink |`` `right` ``, `` `/chart` ``|-|-|
| Kaidah Query | `[[Docs/Query/Output/<kaidah>|<kaidah> Output]]` | Single, Series, Multi Series, Table | `[[Docs/Query/Output/Series|Series Output]]`|
| Label input dalam Flow Block | `[[^input|<Label>]]` | Nama label dalam input antarmuka Flow Block | `[[^output|Conflict Name]]`|
| Label output dalam Flow Block | `[[^output|<Label>]]` | Nama label dalam output antarmuka Flow Block | `[[^output|Conflict Name]]`|
| Status Activity | `[[^flowstate/<Status>]]` | Succeed, Error, Fatal Error, Waiting, Abort | `[[^flowstate/Succeed]]`|

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
- Judul halaman (front matter): `<Nama Elemen> (Elemen <Tipe>)`, misalnya `Card (Elemen Layout)`. Judul H1: `Form Layout : <Nama>` untuk Elemen Layout. Path halaman Elemen: `Docs/Modul Interface/Form/Elemen/<Tipe>/<Nama Elemen>`` (tanpa subfolder per Elemen dan tanpa `/Penjelasan`).
- Fokus pada keunikan Elemen. Hal yang berlaku untuk semua Elemen cukup ditautkan, tidak ditulis ulang: `Docs/Modul Interface/Form/Elemen/Pengenalan`, `Elemen Form/Layout/Pengenalan`, `Elemen Form/Menambahkan`, `Elemen Form/Menghapus`, `Elemen Form/Mengonfigurasi#Properties Panel`, `Elemen Form/Mengonfigurasi#Header Toolbar`, `Elemen Form/Binding#Binding Layout`, `Elemen Form/State`, dan `Docs/Modul Interface/Form/Apa itu Form#<Bagian>`.
- **Kerangka sederhana untuk Elemen Layout (versi akhir penulis pada Card):** front matter, callout note pengenalan, dua paragraf pengantar (definisi, lalu manfaat Table header), `## Mengapa Menggunakan <Layout>?`, `## Menambahkan <Layout>` (dua cara: Start Building dan field `[[^field|Type something here to add...]]`), `## Mengonfigurasi <Layout>` (gambar, lalu `### Header Toolbar`, `### Properties Panel` berupa tabel Bagian dan Fungsi, `### Binding`, `### State`, `### Attribute`, `### Children`), `## Menghapus <Layout>` dengan callout `>**danger**`. Tidak memakai Konsep Utama, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, Batasan dan Catatan, TL:DR, dan FAQ. Alasan: penulis menghapus bagian-bagian itu pada Card karena halaman Elemen cukup menjelaskan keunikan Elemen.
- **Bagian "Mengapa Menggunakan <Layout>?" berisi keunikan antar Layout, bukan alasan umum.** Tabel Layout dan Keunikan memuat keempat Layout dengan tautan, diikuti satu kalimat "Pilih <Layout> bila ...". Alasan: penulis menghapus poin "mengapa menggunakan Layout Card" karena tidak relevan, sebab Header Toolbar dan Properties Panel keempat Layout sama. Keunikan: Card = tampilan kartu; Full = tampilan penuh; Split = tampilan dibelah kiri dan kanan; Accordion = tampilan kartu dengan header yang dapat di-toggle untuk menyembunyikan dan menampilkan isinya.
- Bagian Attribute ditulis meskipun kosong (kalimat "Tidak ada atribut yang dapat dikonfigurasi pada <Layout>."). Pada Accordion, Attribute berisi tabel Atribut dan Fungsi untuk Label dan Default State.
- Pastikan anchor di tabel Properties Panel sesuai judul bagian (`[[#Binding]]`, bukan `[[#Binding Card]]`).
- Gambar: `<elemen>-header-form.png` (Header Toolbar) dan `properties-form-<elemen>.png` (Properties Panel) di folder `Docs/Modul Interface/Form/Elemen/Layout/` (misalnya `card-header-form.png`, `properties-form-card.png`). Untuk Elemen lain, folder mengikuti Tipe Elemen.
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

## Pola yang dipakai penulis untuk konteks = Halaman Pengelolaan Data (contoh: Node pada Tree)

Sumber: delapan halaman `Docs/Modul Data/Tree/Node/<Halaman>`. Penulis meminta halaman pendek, spesifik pada cara, dan boleh memakai asumsi yang direvisi kemudian.

- **Satu halaman satu aksi.** Struktur yang dipertahankan penulis tanpa perubahan: front matter, paragraf pembuka, langkah bernomor, callout `success`, `warning`, `danger`, catatan `note` Hak akses dan Event, lalu Lihat Juga. Tidak memakai Konsep Utama, Cara Kerja, Praktik Terbaik, TL:DR, dan FAQ.
- **Front matter.** Penulis menambahkan `pageDecoration` dengan `icon: x` dan `tree.priority` yang menurun sesuai urutan halaman (Menambahkan 9, Mengubah Nama 8, Mengubah Urutan 8, Menghapus 7, Melihat Detail 6, Mengatur Tampilan 5, Mengekspor 4, Mengimpor 3). Tulis tanpa indentasi di awal baris. Larangan menulis `pageDecoration` hanya berlaku untuk halaman block Data. Prioritas 8 muncul dua kali dan perlu dikonfirmasi.
- **Gambar.** Beri baris kosong antara baris gambar dan daftar bernomor. Penulis mengganti `node-menu.png` menjadi `tree-context.png` pada halaman Mengatur Tampilan.
- **Aksi yang tidak ada di menu konteks.** Bila menu konteks tidak memuat aksi (misalnya Add dan Delete pada Node), asumsikan aksi lewat Edit pada Node induk dan tandai TODO. Penulis mengonfirmasi asumsi ini benar.
- **Label tombol mengikuti antarmuka.** Penulis mengganti `Add` menjadi `Add Children` pada langkah menambahkan Node dari Tree lain.
- **Pesan Error.** Bila penulis meminta pesan kesalahan diasumsikan, tulis teksnya sebagai `[[^field|<teks pesan>]]` tanpa TODO karena sistem akan mengikuti.
- **Tipe JSON bukan tipe data Phoenix.** Pada halaman yang menjelaskan atribut file JSON (contoh: Format Import dan Export), kolom Tipe ditulis polos (Number, String, Array) tanpa tautan ke `Docs/Tipe Data`. Nama atribut tetap ditautkan dengan `[[^field|...]]`.
- **TODO yang sudah dijawab dihapus.** Bagian yang belum terjawab atau jawabannya hanya menjawab sebagian dibiarkan sebagai TODO baru yang menyebut bagian yang belum terjawab.


## Pola yang dipakai penulis untuk konteks = Flow Block dan Halaman per Block

- Halaman Pengenalan Flow Block memuat Konsep Utama, Anatomi Flow Block (gambar `anatomi-flow-block.png`, posisi tiap bagian, lalu subbagian Trigger, Input, Control, Output), Aturan Koneksi, Syarat Flow Block Diproses, Variasi Antar Jenis Flow Block, katalog Jenis Flow Block, dan Mengelola Flow Block.
- Istilah: **Trigger** (huruf kapital) adalah bagian block yang menjadi syarat eksekusi, sedangkan tombol `[[^button/empty|Trigger]]` pada Pulser adalah Control. Untuk kata kerja gunakan "memicu" agar tidak tertukar dengan Trigger. Area kerja Flow ditulis Blueprint.
- Syarat eksekusi hanya berlaku untuk Flow Block non-Event.

### Pengenalan kategori (`Flow Block/<Kategori>/Pengenalan`)

- Front matter: `status`, `title`, `description`, `pageDecoration.tree.priority`, dan `tags: flowblock-category`. Tidak memakai ikon.
- Isi dipangkas. Susunan akhir penulis: callout note, definisi kategori, perbandingan dengan kategori lain **dalam satu paragraf** (bukan tabel), gambar semua block, peran dalam Flow **sebagai lanjutan paragraf**, Jenis Flow Block (tabel Block, Terpicu ketika, Output), Memilih Flow Block, Lihat Juga.
- Penulis **menghapus**: tabel Perbandingan dengan Kategori Lain, Anatomi, Output Event dan Old (aturan bersama), dan Menggunakan. Jangan dibuat lagi. Aturan yang berlaku lintas block ditulis di halaman block, bukan di Pengenalan.
- Callout perilaku yang berlaku untuk seluruh kategori boleh ada di Pengenalan (contoh: perubahan oleh Flow tidak memicu Flow kembali).

### Pengenalan kelompok Data (`Flow Block/Data <Grup>/Pengenalan`)

*   Callout pembuka: "salah satu kelompok Flow Block pada kategori Data dalam komponen Flow di Phoenix" (tanpa tautan ke halaman kategori Data).
*   Berbeda dengan Event, block Data **tidak memiliki Control dan output yang mirip**. Tiap block unik sesuai fungsinya. Tabel Jenis Flow Block memakai kolom **Block** dan **Fungsi** (bukan Terpicu ketika dan Output), dan Memilih Flow Block disusun berdasarkan kebutuhan.
*   Susunan: front matter, callout note, definisi kelompok, paragraf perbandingan dengan Event (Event menjadi titik awal alur, block Data bekerja setelah menerima data dari block sebelumnya sehingga tunduk pada Syarat Flow Block Diproses), gambar semua block (`data-<grup>-block-flow.png` dengan keterangan menyebut seluruh block), satu paragraf peran, callout, Jenis Flow Block Data <Grup>, Memilih Flow Block Data <Grup>, Lihat Juga.
*   **Tanpa diagram mermaid dan tanpa judul "Peran ... dalam Flow".** Penulis menilai diagram tidak relevan untuk block Data karena alurnya berbeda-beda per block.
*   Kolom Fungsi menyebut atribut yang diambil atau diubah dengan `[[^field|<Nama>]]`, misalnya "Mengambil nilai atribut Table, yaitu Name dan Description." Block "Getter" mengambil data dengan mengisi Name atau menentukan Row dan Column (bisa diisi di block sendiri atau dari output block lain). Block "Setter" mengubah satu data per eksekusi.
*   Isi tabel Memilih Flow Block, paragraf definisi, dan paragraf perbandingan harus disinkronkan dengan kolom Fungsi setiap kali Fungsi berubah.
*   Callout "Perubahan data oleh Flow tidak memicu Flow kembali" ditulis di setiap kelompok dan menautkan Event Block yang relevan (Variable Event, Enum Data Event, Table Row Event, Tree Node Event).
*   Callout warning ditulis untuk block Delete (dan Add bila ada dampak) di setiap kelompok. Khusus Tree: warning bahwa Flow dapat mengubah atau menghapus Node pada Tree dengan Merger Mode atau External Read Only aktif, termasuk Node hasil clone.
*   Callout khusus komponen yang terkonfirmasi boleh ditambahkan (Variable: dirujuk lewat Name dan akses komponen; Tree: Node Origin).
*   Front matter mengikuti halaman Event versi penulis: `status`, `title`, `description`, `tags: flowblock-category`, tanpa `pageDecoration.tree.priority` (aturan lama di skill menyebutnya). Mohon konfirmasi apakah aturan lama itu diganti.
- Heading **Input dan Output** (bukan "Input, Control dan Output") karena block Data tidak memiliki Control. Hanya judul bagian yang relevan yang ditulis. TL:DR dan FAQ tidak dipakai pada halaman block.
- Urutan bagian: callout note kelompok, paragraf definisi, gambar `<nama-block>-block-flow.png`, Input dan Output (tabel Input dan tabel Output), Cara Kerja, Contoh Penggunaan (tabel kombinasi kondisi dan output), Praktik Terbaik, Batasan dan Catatan, Lihat Juga.
- **Jangan menulis atribut `pageDecoration` di front matter.** Front matter hanya berisi `status`, `title`, dan `description`. Tetap ikuti format frontmatter dari hasil revisi, bukan untuk dipelajari.
- Output yang tidak relevan dengan suatu kasus tidak meneruskan aliran dengan ditulis "-" pada tabel (bukan `[[^value/empty]]` dan bukan `[[^value/boolean/false]]`). Output flag (Is ..., Succeed, Error, Name Conflict) ditulis "`[[^value/boolean/true]]`" pada kasusnya. Output yang tetap meneruskan aliran tetapi bernilai kosong (contoh: Header pada Table Column untuk Column tanpa Header, Pass pada TableData Setter dengan Value kosong) ditulis `[[^value/empty]]`, bukan "-".
- Setiap tabel Output dan tabel Contoh Penggunaan menjelaskan kapan output meneruskan aliran dan kapan tidak. Setelah tabel Output, tautkan aturannya dengan `[[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]]`.
- Karena output tunggal hanya meneruskan aliran pada kasusnya, jangan menyarankan Branch Block untuk memisahkan alur dari output flag. Sarankan menghubungkan block penanganan langsung ke output tersebut.
- Field bertipe Variable adalah pilihan (select option). Tulis "Isi dengan Variable Data atau hubungkan dari output block lain", bukan "isi dengan Name atau alias".
- Hindari istilah teknis seperti *exact match*. Jelaskan dengan konteks umum: sama persis, membedakan huruf besar dan kecil, menerima karakter simbol, dan di-trim saat disimpan.
- Kondisi yang tidak mungkin terjadi karena input berupa pilihan (misalnya "Variable tidak valid") tidak ditulis di tabel Contoh Penggunaan. Tulis hanya kondisi "dibiarkan kosong".
- Untuk Variable Data yang berelasi, gunakan istilah "sudah digunakan" (sedang dipakai pada Flow atau data lain, atau tercatat di riwayat activity) alih-alih "relasi atau histori".
- Block non-Event selalu menautkan `Flow Block/Syarat Eksekusi` pada Batasan dan Catatan.
- Callout "Perubahan oleh Flow tidak memicu Flow kembali" ditulis pada block yang mengubah atau menghapus data (Delete, Setter). Pada Add Variable tidak ditulis karena Variable Event tidak memiliki event create. Pada Add Row ditulis karena Table Row Event memiliki event create.
- Callout `>**danger**` untuk penghapusan yang tidak dapat dikembalikan dan `>**warning**` untuk hapus paksa ditulis pada block Delete.

### Deskripsi Input dan Output serta Contoh Penggunaan (block Data)
Koreksi penulis pada halaman Data Table: draf pertama kekurangan deskripsi pada dua bagian ini. Wajib ada pada setiap halaman block Data, termasuk Setter.
- **Paragraf pembuka Input dan Output** (tepat setelah heading, sebelum subbagian Input), satu paragraf: "<Nama> Block memiliki <n> input di sisi kiri, <m> output di sisi kanan dan tidak memiliki Control. Output hanya keluar bila kondisinya terpenuhi, dan tanda `-` pada tabel berarti tidak ada output. Setiap input dapat diisi langsung pada block atau diisi dari output block lain lewat [[Docs/Modul Logic/Flow/Flow Block/Menghubungkan Koneksi|koneksi]]." Jangan memecahnya menjadi "tidak memiliki Control" dan "Block ini memiliki ..." sebagai dua kalimat. Nama block selalu ditulis "<Nama> Block".
- **Tabel Output:** sel Keterangan menjelaskan dengan kalimat kapan output meneruskan aliran (contoh: "[[^value/boolean/true]] bila Row berhasil dihapus dan aliran diteruskan"). Jangan menulis "(`-`)" atau ", selain itu `-`" di dalam sel karena arti "-" sudah dijelaskan di paragraf pembuka.
- **Setelah tabel Output** pada block yang memiliki output kondisi (Succeed, Error, Is Empty, Value Conflict): "Tidak semua output meneruskan aliran Flow. Block yang terhubung ke output yang tidak meneruskan aliran tidak akan dieksekusi, sesuai [[Docs/Modul Logic/Flow/Flow Block/Antarmuka#Output|aturan Output Flow Block]]." Block tanpa output kondisi cukup memakai "Selengkapnya lihat [[...|aturan Output Flow Block]]".
- **Callout `>**note** Mengelola Error`** setelah penjelasan output pada block yang memiliki output Error (Delete Row): hubungkan output Error ke block penanganan agar Flow dapat memberi tahu pengguna, dan block itu hanya dieksekusi bila kegagalan terjadi. Penulis belum menentukan callout serupa untuk Value Conflict (Setter) dan Is Empty (Getter); tanyakan sebelum menambahkan.
- **Contoh Penggunaan:** setelah tabel kombinasi, tulis satu kalimat: "Status [[^flowstate.Error]] dan [[^flowstate/Fatal Error]] akan menghasilkan error yang pesannya tampil di [[Docs/Modul Logic/Flow/Flow Activity]]." Sebut hanya status yang ada pada tabel. Tulis `[[^flowstate/<Status>]]` dengan pipa (bukan `[[^flowstate/<Status>]]`) dan dengan satu spasi setelah kata "Status".
- **Format:** setelah TODO dihapus, tetap beri baris kosong antara gambar dan heading atau callout berikutnya.
- **Terkonfirmasi penulis:** semua asumsi yang ditandai TODO pada tujuh halaman Data Table tepat dan boleh dihapus dari versi final.

### Halaman block Data Table
- Path: `Docs/Modul Logic/Flow/Flow Block/Data Table/<Nama Block>`. Gambar: `<nama-block>-block-flow.png` di folder yang sama (contoh `add-row-block-flow.png`, `tabledata-getter-block-flow.png`).
- Block: Add Row, Delete Row, Table, Table Column, Table Row, TableData Getter, TableData Setter. Tanpa Control.
- Tabel Contoh Penggunaan block Data memakai kolom tambahan **Status** dengan `[[^flowstate/Succeed]]`, `[[^flowstate/Error]]`, atau `[[^flowstate/Fatal Error]]`.
- Delete Row: Force yang dibiarkan kosong adalah Fatal Error (berbeda dengan Delete EnumData yang memperlakukan Force kosong sebagai false). Row "sudah digunakan" memakai definisi yang sama seperti Variable Data.
- Table Column: output Header mengikuti tipe data Column dan tetap meneruskan aliran bernilai `[[^value/empty]]` bila Column tidak memiliki Header. Table Row: output Pass, Index (Number, ID Row pada tampilan Table), Table.
- TableData Getter dan Setter: Column dan Row harus berasal dari Table yang sama. Getter mengeluarkan Is Empty true bila TableData kosong atau tidak ditemukan. Setter berstatus Error bila Row atau Column tidak ditemukan, Value Conflict true bila Value berisi tetapi tipenya tidak sesuai Column, dan Value kosong selalu valid tanpa memeriksa tipe.
### N/A Type
- Teks merah **N/A Type** pada input block berarti tipe data belum didefinisikan. Ditulis dengan `[[^field|N/A Type]]`.
- Langkah mendefinisikan: klik kanan pada input ➜ `[[^field|Change Type]]` ➜ pilih tipe data (semua tipe data Phoenix tersedia). Tulis sebagai subbagian bernomor "Menentukan Tipe Data <Nama Input>" pada setiap block yang input-nya memiliki N/A Type (Add Variable dan Variable Setter).
- Input yang tipenya dapat diganti tetapi bukan N/A Type memakai langkah yang sama. Contoh: input `[[^input|Row]]` pada TableData Getter dan TableData Setter (tampil "Empty", tipe dapat diganti ke Number atau String berisi Index Row; subbagian "Menentukan Tipe Data Row"). Pada TableData Setter, input `[[^input|Value]]` yang masih N/A Type menghasilkan Fatal Error.


### Halaman block Data Tree
- Path: `Docs/Modul Logic/Flow/Flow Block/Data Tree/<Nama Block>`. Gambar: `<nama-block>-block-flow.png` di folder yang sama (contoh `add-node-block-flow.png`, `tree-get-origin-block-flow.png`). Screenshot penulis memuat banyak block dalam satu gambar, jadi beri TODO agar penulis memotong gambar per block.
- Block: Tree, Node, Node Setter, Add Node, Assign Node, Delete Node, Tree Get Origin, Node Get Parent, Node Get Children, Node Get Ancestor. Tanpa Control. Struktur sama dengan halaman Data Table (callout note kelompok, definisi, gambar, Input dan Output, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, Batasan dan Catatan, Lihat Juga).
- Istilah: gunakan **saudara kandung** (Node lain dengan parent yang sama) dan **keturunan**. Jangan memakai analogi keluarga seperti "ayah" atau "kakek" untuk menjelaskan Depth. Tulis "parent langsung" dan "parent dari parent".
- Tulis label antarmuka persis, termasuk "(Node)" pada output: `[[^output|The Parent (Node)]]`, `[[^output|The Origin (Node)]]`, `[[^output|The Children (Node)]]`, `[[^output|The Ancestor (Node)]]`. Input ketiga Assign Node berlabel `[[^input|Children]]` (bukan "Node children").
- Output flag Tree: `Name Conflict`, `Order Conflict` (Add Node, Node Setter, Assign Node) dan `Relation Conflict` (Assign Node), semuanya `[[^value/boolean/true]]` pada kasusnya dan `-` pada kasus lain, berstatus Error. Output Not Found pada Node Get Parent, Node Get Children, dan Node Get Ancestor juga memakai pola ini.
- Input Order pada Add Node, Node Setter, dan Assign Node bertipe Number (bukan N/A Type), jadi tidak ada subbagian "Menentukan Tipe Data". Order minimal `[[^value/number|0]]`.
- Contoh Penggunaan memakai Tree Kategori Produk dengan silsilah Origin ➜ Elektronik ➜ Komputer ➜ Laptop, Elektronik juga memiliki anak Ponsel (Order 1), dan Aksesori berada di bawah Origin. Pertahankan nama ini di seluruh halaman Data Tree.
- Anc. Level: Level 1 = Origin, dihitung dari Origin ke Node. Node Get Parent dihitung dari Node ke atas. Jelaskan perbedaan keduanya di Praktik Terbaik kedua halaman.
- Callout: Delete Node memakai `>**danger**` (tidak dapat dikembalikan, anak ikut terhapus), `>**warning**` hapus paksa, `>**warning**` Tree dengan Merger Mode atau External Read Only, `>**note** Mengelola Error`, dan `>**note**` perubahan oleh Flow tidak memicu Flow kembali. Node Setter dan Assign Node memakai dua callout terakhir selain Error. Add Node hanya memakai callout Flow tidak memicu Flow kembali, dengan menyebut Tree Node Event memiliki event create. Block Get, Tree, Node, dan Tree Get Origin tidak memakai callout.
- Callout Mengelola Error pada Delete Node tidak diperluas ke Conflict dan Not Found sebelum penulis menentukan.
- Order negatif ditulis sebagai Fatal Error (bukan Error) pada input Order Add Node, Node Setter, dan Assign Node, dan bila perlu ditambah baris pada tabel Contoh Penggunaan. Prinsipnya: block berstatus Error hanya bila ada output yang menandai kegagalan itu, kasus tanpa output menjadi Fatal Error.
- Delete Node: menghapus Origin = Fatal Error, tulis di Batasan dan Catatan serta baris Contoh Penggunaan. Assign Node: Children = Origin menghasilkan Relation Conflict.
- Batasan dan Catatan: frasa "Flow Block Event" ditautkan ke `Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event` (terlihat pada Node Setter, jadikan pola di halaman block non-Event lain).
- Komentar TODO yang sudah dijawab penulis (baris `Jawaban:`) dihapus setelah jawabannya dimasukkan ke halaman, kecuali penulis meminta dipertahankan.

## Halaman block Operator (tambahkan di bagian "Pola yang dipakai penulis untuk konteks = Flow Block dan Halaman per Block")

### Halaman block Operator
- Path: `Docs/Modul Logic/Flow/Flow Block/Operator/<Tipe Data>/<Nama Block>` (Number, String, Table, Object, Boolean, Tree). Tidak ada Pengenalan per kelompok tipe data. Gambar: `<nama-block>-block-flow.png` di folder yang sama (contoh `tablerow-parse-block-flow.png`, `node-parse-block-flow.png`).
- Block Operator tidak memiliki Control. Heading **Input dan Output**, paragraf pembuka mengikuti pola block Data. Kalimat "tanda `-` berarti tidak ada output" hanya ditulis bila block punya output yang tidak selalu meneruskan aliran (If, Parse).
- Callout pembuka: "salah satu Flow Block kelompok <Tipe Data> pada kategori [[.../Operator/Pengenalan|Flow Block Operator]] dalam komponen [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] di Phoenix."
- Output yang bergantung koneksi (TableRow Parse: Object dan Text; Node Parse: Object dan Text; If: Boolean) ditulis "Aliran diteruskan bila output terhubung."
- Input yang tipenya dapat diganti (Assign: Value berawal Object dan dapat diganti ke String; If: A dan B berawal N/A Type) memakai subbagian "Menentukan Tipe Data <Input>" dengan langkah klik kanan ➜ Change Type.
- Input Number berupa kedalaman (Rel. Depth, Anc. Depth, Child Depth) yang dibiarkan kosong dianggap bernilai 0 dan **bukan** Fatal Error. Ditulis di tabel Input, Contoh Penggunaan, dan Batasan dan Catatan.
- Output Error pada Parse (Text tidak sesuai kaidah Object) diperlakukan seperti output flag: callout "Mengelola Error" dan nilai `[[^value/boolean/true]]` pada kasusnya (asumsi, menunggu konfirmasi penulis).
- Nama input yang kembar pada satu block (Concatenate: dua input String) dibedakan dengan "(pertama)" dan "(kedua)" pada tabel.
- Contoh nilai Array dan Object dalam tabel ditulis dengan kode inline atau `[[^value/object|...]]` dengan kutip lurus. Jangan menaruh kurung siku Array di dalam wikilink `^value` (slug `array` tidak ada pada daftar).
- Praktik Terbaik boleh menautkan block pendamping yang saling melengkapi: Increment dengan Variable Getter dan Setter, Pad Left dengan Concatenate, Parse dengan Stringify, Assign dengan Merge.

## Tambahan dari hasil review (Contoh Penggunaan dan siklus TODO)

- **Contoh Penggunaan untuk block yang memproses isi data (TableRow Parse, Node Parse, dan sejenisnya)** harus memperlihatkan isi data masukan dan hasil JSON-nya, bukan hanya deskripsi kata. Awali dengan satu paragraf setelan contoh (tabel Pesanan dan Penerima, Tree kategori produk), lalu tabel kombinasi dengan kolom hasil berisi Object.
- Untuk menunjukkan perbedaan dua input kedalaman (Anc. Depth dan Child Depth), sertakan ilustrasi struktur Tree dalam blok kode dan satu paragraf penutup yang menyebut arah masing-masing (ke atas menghasilkan `parent`, ke bawah menghasilkan `children`). Contoh dipilih agar intuitif, dengan nama yang mudah dipahami (Elektronik, Komputer, Laptop).
- **Siklus komentar TODO yang dipakai penulis:** penulis menandai `[DONE]` pada item yang beres dan menulis `Jawaban: ...` di baris bawah item pertanyaan. Item yang dijawab dan sudah diproses penulis ke halaman diubah menjadi `[DONE]`. Jawaban "Sudah benar" pada pertanyaan terbuka (misalnya "apakah A atau B") tidak menjelaskan perilaku sebenarnya, jadi tanyakan ulang bila perilaku itu perlu ditulis.
- Pada penjelasan perbedaan If dengan Branch, kategori Operator ditentukan oleh komputasi yang mengubah input menjadi data baru, bukan oleh adanya Control atau output flag.


### Halaman per block
- Front matter: `status`, `title`, `description`, `pageDecoration.icon: zap`, `pageDecoration.tree.priority`. Tulis tanpa indentasi di awal baris.
- Heading: **Input, Control dan Output** (bukan "Input dan Output"). Kalimat pembuka: "memiliki satu Control berupa tombol dan <n> output di sisi kanan".
- Nama output ditulis `[[^output|Nama]]`, bukan kode inline. Nilai ditulis dengan `[[^value/string|create]]`, `[[^value/number|150000]]`, `[[^value/boolean/true]]`, `[[^value/boolean/false]]`, `[[^value/empty]]`, `[[^value/object|{ "Status": "Menunggu" }]]`, `[[^value/enumdata|Menunggu]]`. Ikuti sesuai slug tipedata sebagai berikut: 
- Isi Object memakai tanda kutip lurus (sintaks JSON), bukan kutip melengkung.
- Pipa alias wikilink di dalam sel tabel **tidak di-escape** (`[[^button/empty|Trigger]]`, bukan `\|`).
- Tautan antarblock yang sejenis memakai anchor ke halaman block yang menjadi acuan (`Table Row Event#Isi Output Berdasarkan Event`). Jangan menautkan ke anchor di halaman yang bagiannya sudah dihapus penulis (kesalahan saya: tautan `Pengenalan#Output Event dan Old` menjadi rusak setelah bagiannya dihapus).
- Contoh Penggunaan berisi tabel kombinasi (Peristiwa, lalu satu kolom per output). Baris yang bertentangan dengan perilaku produk tidak boleh ada (contoh: baris "ditambahkan lewat Flow" dan "disimpan tanpa perubahan" harus dibuang setelah penulis menjawab bahwa keduanya tidak memicu Event).
- Nama contoh (Table pesanan, Enum kategori, Tree kategori, Variable `batas_stok_minimum`) boleh dipertahankan setelah penulis menandai DONE.

### Path baru yang dipakai penulis
- `Docs/Modul Data/<Komponen>/Mengotomasi` untuk cara menghubungkan Event dari komponen (Variable, Table, Enum, Tree), menggantikan tebakan `.../Event`.
- `Docs/Modul Interface/Timeline/Timeline Event/Pengenalan` (bukan anchor `Apa itu Timeline#Mengelola Timeline Event`).
- `Docs/Modul Interface/Canvas/Widget/Basic/Button` (tanpa alias, ditulis "Widget Button").
- `Docs/Modul Logic/Flow/Flow Block/Syarat Eksekusi` untuk Syarat Flow Block Diproses.

### Proses
- Sinkronkan semua halaman terkait setiap kali satu halaman berubah. Setelah penulis mengubah jumlah output (Variable Event dari satu menjadi tiga), perbarui juga callout, tabel, diagram, dan Pengenalan yang menyebut output tersebut.
- TODO yang sudah dijawab (`Jawaban:`) atau ditandai `[DONE]` dihapus dari versi final.
  
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