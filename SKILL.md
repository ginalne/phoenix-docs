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
- Untuk konsep yang sudah punya halaman sendiri (Komponen, Folder, Pro, Flow Block, dan sejenisnya), jangan mendaftar contoh di tabel Konsep Utama. Cukup beri satu kalimat singkat dan tautkan ke halamannya ("Selengkapnya lihat [[...]]"). Pada tabel Konsep Utama, istilahnya sendiri yang dijadikan wikilink (kolom Istilah), bukan dicetak tebal.
- Gunakan istilah "bilah navigasi", bukan "navbar".
- Jika topik komponen cukup dalam (misalnya Data Access, Flow Block), tulis ringkasan di halaman utama dan arahkan ke subhalaman dengan tautan, lalu tandai dengan TODO bahwa subhalaman perlu dibuat.
- Hasilkan file`.md`, bukan teks biasa di chat, kecuali pengguna hanya meminta komentar atau review.
- Setiap kali saya memberi informasi baru dalam penulisan dokumentasi Phoenix, tulis di akhir jawaban bagian **"Usulan update /phoenix-docs-silverbullet"**. Isinya alasan pembaruannya, lalu sertakan file.md nya agar perubahan skill menjadi mudah. Jika tidak ada yang relevan, jangan tulis bagian ini.
- Setiap kali saya memberi informasi baru dalam dokumentasi Phoenix, tulis di akhir jawaban bagian **"Usulan update skill /phoenix-docs-knowledge"**, lalu sertakan file.md nya agar perubahan skill menjadi mudah. Isinya alasan pembaruannya. Jika tidak ada yang relevan, jangan tulis bagian ini.

## Cara berpikir yang perlu dijaga

Bagian ini merangkum pola yang berulang dari revisi penulis. Pahami alasannya agar bisa dipakai pada komponen apa pun, bukan hanya komponen yang pernah dibahas.

1. **Halaman komponen adalah peta, bukan manual.** Halaman "Apa itu <Komponen>" memberi orientasi: definisi, manfaat, konsep (sebagai tautan), pengelolaan komponen itu sendiri (Membuat, Mengubah, Menyegarkan, Menghapus), Antarmuka, lalu daftar aspek yang mengarah ke subhalaman. Langkah rinci, katalog opsi menu, tabel isi panel, dan konfigurasi item anak dipindahkan ke subhalaman. Uji sederhana: jika sebuah bagian punya langkah atau tabel sendiri dan bisa dibaca terpisah, bagian itu adalah subhalaman, dan halaman utama hanya menyisakan satu kalimat atau satu daftar tautan (misalnya bagian "Membangun Logika Flow" berisi tautan anchor ke subhalaman). Pembaca halaman pengantar mencari orientasi, dan detail yang menumpuk membuat halaman dalam serta sulit dirawat. Jika ragu, tulis lebih ringkas dan usulkan subhalaman, karena menambah detail lebih mudah daripada memangkasnya.
2. **Istilah milik produk dan penulis menang.** Pakai label persis seperti di antarmuka dan istilah yang dipakai penulis (misalnya Blueprint, Submission, Flow Block Event). Jangan menciptakan nama untuk area antarmuka yang belum diberi nama; tulis dengan sebutan paling netral dan beri TODO agar penulis menamainya. Analogi dari luar produk (misalnya "seperti composition di Blender") atau kalimat "kalau bingung maksudnya..." adalah bantuan bagi Claude untuk memahami, bukan isi dokumentasi, kecuali penulis memintanya ditulis. Pakai satu istilah yang sama di seluruh halaman. Kata Indonesia umum ("blok") boleh untuk penjelasan non-fitur, sedangkan nama fitur tetap sesuai antarmuka.
3. **Tautkan untuk membuka jalan.** Setiap konsep, aksi, atau istilah yang punya ruang untuk tumbuh dijadikan wikilink, termasuk ke halaman yang belum ada. Wikilink tebakan adalah ide struktur dokumentasi, bukan kesalahan, jadi jangan ragu. Tebakan path mengikuti pola yang sudah ada: setiap folder memiliki halaman`Pengenalan` sebagai pintu masuk, fitur pendamping komponen bernama`<Komponen> <Fitur>` (misalnya`Flow Activity`), item anak berada di bawah folder kategorinya, dan bagian dalam sebuah subhalaman diakses lewat anchor (`#Menambahkan Flow Block`). Tautkan juga aksi yang melintasi komponen (misalnya menghubungkan Event dari komponen lain). Dalam contoh penggunaan, hampir setiap nama block atau komponen yang disebut adalah wikilink. Tandai asumsi halaman baru dengan satu TODO konsolidasi per halaman, bukan satu TODO per tautan.
4. **Screenshot adalah sinyal struktur.** Screenshot antarmuka berarti penulis ingin ada bagian "Antarmuka <Komponen>": gambar, penjelasan area, tabel tombol bilah navigasi, dan catatan perbedaan tampilan desktop dan mobile. Jika ada gestur, tambahkan "Interaksi Antarmuka" (tabel Fungsi dan Aksi). Screenshot dengan menu terbuka biasanya menunjuk ke subhalaman. Tombol, ikon, atau penghitung yang belum dijelaskan penulis ditandai TODO, bukan ditebak sebagai fakta.
5. **Contoh Penggunaan menjual nilai, bukan menguji fitur.** Skenario berangkat dari kebutuhan nyata dan hasil yang dirasakan pengguna, dengan menonjolkan nilai integrasi Phoenix (data, logika, dan sistem lain tersambung). Hindari contoh yang hanya membuktikan fitur bekerja (misalnya menekan tombol uji). Susunannya: kebutuhan, komponen yang terlibat, alur (diagram mermaid dan tabel langkah dengan nama block yang ditautkan), hasil yang dirasakan, lalu ide skenario lain (variasi pemicu, tujuan, atau komponen) sebagai inspirasi. Judul skenario dari penulis mengikat dan harus diisi rinci. Nama komponen memakai nama generik dan ditandai TODO. Kalimat penutup ditulis ulang untuk skenario itu dan tidak disalin dari contoh lain.
6. **Draf dulu, TODO kemudian.** TODO tidak menggantikan draf. Setiap bagian, termasuk warning dampak penghapusan, catatan perbedaan mode, dan langkah yang belum pasti, ditulis dalam bentuk terbaik, lalu ditandai untuk konfirmasi. Dampak penghapusan komponen (apa yang hilang dan apa yang terputus) selalu ditulis sebagai callout warning.
7. **Ringkasan harus mengikuti isi.** Batasan dan Catatan, TL:DR, dan FAQ adalah ringkasan. Setiap kali isi halaman berubah atau dipindah, sinkronkan keempatnya: (a) langkah yang sudah pindah ke subhalaman diganti satu tautan; (b) Batasan berisi perilaku, dampak, dan ketergantungan (warning, perbedaan mode, relasi hak akses, apa yang tidak dicakup sebuah tombol), bukan lokasi tombol atau langkah yang sudah ada di isi halaman; (c) TL:DR berisi 4 sampai 6 poin yang mengikuti peta halaman (definisi, antarmuka, membangun, menjalankan, memantau, hal yang perlu hati-hati); (d) setiap anchor`#...` harus ada di halaman tujuan atau di daftar halaman yang diusulkan.
8. **Revisi penulis adalah sumber belajar.** Bandingkan halaman yang dikembalikan dengan versi sebelumnya. Yang dihapus biasanya salah level atau bukan konten, yang diganti biasanya istilah atau struktur, dan yang ditambah biasanya bagian yang terlewat. Ubah temuan menjadi aturan di SKILL.md dan fakta di KNOWLEDGE.md (path, istilah, perilaku). Jadikan struktur dan istilah penulis sebagai dasar untuk halaman berikutnya.

## Konvensi tautan

|Halaman|Format|Variasi|Contoh|
|-|-|-|-|
|Halaman konsep umum|`[[Inisialisasi/Apa itu Pro?\|Pro]]`, `[[Docs/Apa itu Komponen?]]`, `[[Docs/Folder/Apa itu Folder?]]`|Pro, Komponen, Folder|`[[Docs/Folder/Apa itu Folder?#Informasi Data]]`                                                                                  |
|Event|`[[Docs/Event/Apa itu Event\|Event]]`, `[[Docs/Event/Menghubungkan Event]]`                                                                                                                             | Menggantikan`Docs/Event/Pengenalan`|-|
|Subhalaman komponen|`[[Docs/Modul <Nama>/<Komponen>/<Subhalaman>]]`|Data Access, TimelineData, Flow Activity|`[[Docs/Modul Developer/Workspace/Data Access]]`, `[[Docs/Modul Logic/Flow/Flow Activity]]`                                       |
|Item anak komponen (misalnya Flow Block)|`[[Docs/Modul <Nama>/<Komponen>/<Item>/Pengenalan]]` untuk halaman pintu masuk, `[[Docs/Modul <Nama>/<Komponen>/<Item>/<Kategori>/Pengenalan]]` untuk kategori, `...#<Bagian>` untuk bagian di dalamnya|Flow Block: kategori Event, Data, Operator, Modular, dan seterusnya|`[[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan]]`, `[[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menambahkan Flow Block]]` |
|Tipe data milik komponen|`[[Docs/Modul <Nama>/<Komponen>/<Tipe>]]`|TimelineData|`[[Docs/Modul Interface/Timeline/TimelineData]]`                                                                                  |
|Modul <Nama>|`[[Docs/Modul <Nama>/Pengenalan\|<Nama>]]`                                                                                                                                                              | Data, Interface, Logic, Developer`[[Docs/Modul Developer/Pengenalan\|Developer]]`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|Komponen|`[[Docs/Modul <Nama>/<Komponen>/Apa itu <Komponen>]]`|Data: Variable, Enum, Table, Tree. Interface: Table View, Gallery, Canvas, Kanban, Space, Timeline, Form. Logic: Flow. Developer: Group, Workspace|`[[Docs/Modul Logic/Flow/Apa itu Flow]]`                                                                                          |
|Tipe Data|`[[Docs/Tipe Data/<Nama>]]`|Color, Tree, Expression, Mixed, Array, Boolean, Column, Number, Enum, EnumData, Complex, Month, Thing, Year, MonthYear, Text, Matrices, Node, Object, File, Query, Row, String, Table, TableData, Variable, Date, Time, DateTime, DateTimeZone|`[[Docs/Tipe Data/String]]`                                                                                                       |
|Format Data|`[[Docs/Format Data/<Tipe Data>/<Nama>]]`|String: Short Text, Password, Email, Phone Number, Mobile Number, URL, Slug, Username, Full Name, First Name, Initial, Country Code, Postal Code, License Plate, National ID, Passport Number, Tax ID, Bank Account, IBAN, Credit Card, MAC Address, IPv4, IPv6, UUID, Emoji. Number: Number, Integer, Decimal, Percentage, Rating. Text: Long Text, Rich Text, Markdown, Note, Chat. Complex: Numeration Unit, Length Unit, Area Unit, Volume Unit, Quaternion Unit, 1D Vector, 2D Vector, 3D Vector, 4D Vector, Geo, Currency. File: Attachment, Document, Media, Image, Photo, Audio, Video, Icon. Array: Popup List, Checkboxes, Direct List, Multiple Select. EnumData: Dropdown, Multiple Choices.|`[[Docs/Format Data/String/Short Text]]`                                                                                          |
|Anchor di halaman yang sama|`[[#Nama Bagian]]`|-|`[[#Flow]]`                                                                                                                       |
|Tautan dengan teks lain|tambahkan alias setelah`\|`. Alias tidak diawali spasi. Di dalam sel tabel, pipa alias ditulis`\|`|Tidak ada. Silahkan sarankan ide untuk penjelasan jika dibutuhkan|`[[Docs/Event/Pengenalan\|Event]]`                                                                                                |
|Anchor di halaman lain|`[[Docs/Antar Muka#Area Manajemen Folder]]`                                                                                                                                                             | [[Docs/Antarmuka#Bilah Navigasi]]`Header Navigation Phoenix.`[[#Area Manajemen Folder]]` bagian pengelolaan folder dan komponen. [[#Halaman Kerja]]` antarmuka kerja komponen||
|Gambar|`![[Docs/Modul <Nama>/<Komponen>/<nama-gambar>.png]]`|Nama file huruf kecil dipisah tanda hubung, ditaruh di folder komponen|`![[Docs/Modul Logic/Flow/blueprint-flow.png]]`                                                                                   |
|Menu atau contextmenu antarmuka|`[[^field/<icon>\|<Label>]]`                                                                                                                                                                            | icon: add, delete, edit, save, copy, paste, eye, collapse, expand, import, export, [slug komponen]. Kategori dan item menu tanpa icon memakai`[[^field\|<Label>]]`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |`[[^field/add\|Add]]`, `[[^field\|Event]]`, `[[^field\|Pulser]]`                                                                  |
|Kolom isian dan teks informasi antarmuka|`[[^field\|<Label>]]`|Berlaku untuk kolom isian, kolom pencarian, dan teks yang tampil di antarmuka (misalnya keterangan kosong atau informasi koordinat)|`[[^field\|Name]]`, `[[^field\|Search]]`, `[[^field\|No Activity]]`                                                               |
|Tombol antarmuka|`[[^button/<icon>\|<Label>]]` atau`[[^button\|<Label>]]`                                                                                                                                               | icon: add (berbentu plus), edit, delete, merge, publish, refresh, save, submission, event, activity, empty (tidak ada ikon). Tanpa icon (`[[^button\|...]]`) untuk tombol aksi umum seperti Create, Update, Delete (konfirmasi)                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |`[[^button/edit\|Edit]]`, `[[^button\|Create]]`, `[[^button/empty\|Trigger]]`                                                     |
|Nilai Boolean|`[[^value/boolean/allow]]`, `[[^value/boolean/disallow]]`, `[[^value/boolean/true]]`, `[[^value/boolean/disallow]]`|Gunakan di dalam tabel dan kalimat, bukan teks tebal|`[[^value/boolean/false]]`                                                                                                        |
|Nama komponen/folder/data pada baris tabel|`[[^field/<slug>\|<Nama>]]`|slug: workspace, group, folder, variable, enum, table, tableview, tree, canvas, flow, dan slug komponen lain|`[[^field/tableview\|Daftar Pelanggan]]`                                                                                          |

Catatan: alias tidak boleh diawali spasi (contoh salah: [[^field/workspace| Workspace]]).

Tautkan komponen lain pada kemunculan pertamanya di sebuah halaman (misalnya Workspace di halaman Group). Label menu dan field ditulis persis seperti yang tampil di aplikasi, bukan diterjemahkan. Jika path tautan hanya tebakan, jangan ragu memakainya, lalu catat dalam satu TODO konsolidasi (lihat [[#Penjelasan TODO]]).

## Penjelasan TODO

Penulisan TODO sebagai catatan untuk diperhatikan kepada penulis harus dibuat dalam bentuk comment, dengan format sebagai berikut:

<!--
  * [TODO] Deskripsi Task
-->

Pembuka`<!--` dan penutup`-->` harus dalam line nya sendiri, serta tambahkan baris kosong agar memastikan format terbaca dengan baik.

Deskripsi Task harus jelas, dan jika comment ini letak cukup jauh dari tulisan yang dimaksud, silahkan buat link dengan tagar untuk seperti ini: [[#Penjelasan TODO]].

Untuk asumsi halaman baru yang ditautkan, kumpulkan dalam satu TODO per halaman: sebutkan path yang diusulkan dan isi yang diharapkan dari tiap halaman, tidak perlu satu TODO per tautan. TODO untuk konfirmasi fungsi block, perilaku, atau istilah ditulis terpisah supaya penulis bisa menjawab satu per satu.

## Jika butuh konfirmasi

Bertindaklah sebagai ahli/konsultan penulisan dokumentasi aplikasi Phoenix. Jika ada hal yang masih perlu dikonfirmasi, silahkan ajukan pertanyaan melalui fitur claude kepada saya satu per satu untuk menggali informasi, detail dan preferensi yang Anda butuhkan sebelum mulai mengerjakan tugas ini agar hasilnya lebih akurat dan detail.

## Templat halaman

Templat di bawah adalah kerangka bawaan, bukan aturan baku. Pahami sifat komponen lalu bentuk struktur terbaik untuk halaman tersebut. Yang tetap: callout pengenalan di awal, Mengapa Menggunakan, Konsep Utama, Cara Kerja, Contoh Penggunaan, Praktik Terbaik, Batasan dan Catatan, TL:DR, dan FAQ dengan judul persis. Bagian di antara Cara Kerja dan Contoh Penggunaan bebas disesuaikan.

Gunakan urutan berikut. Bagian yang tidak relevan boleh dihilangkan, tetapi jangan mengubah urutan atau nama judulnya. Bagian Antarmuka dan Interaksi Antarmuka dipakai bila komponen memiliki halaman kerja atau screenshot dari penulis.
Konteks bisa apapun sesuai permintaan.

```markdown
---
status: draft
title: <Sesuaikan dengan Title>
description: <satu kalimat fungsi komponen>
---

# <Sesuaikan dengan Title>

<callout untuk Pengenalan Komponen>
>**note** _<Komponen>_ merupakan salah satu komponen dalam modul [[Docs/Modul <Modul>/Pengenalan|<Modul>]] di Phoenix.

<Komponen> adalah komponen yang dapat digunakan untuk <fungsi utama>.

<penjelasan dari segi kemudahan, solusi dan keunikan komponen ini>.

## Mengapa Menggunakan <Konteks>?

- **<Manfaat singkat>.** <Penjelasan satu kalimat.>

## Konsep Utama

| Istilah                                                       | Penjelasan      |
| ------------------------------------------------------------- | --------------- |
| [[<tautan atau anchor tempat istilah dijelaskan>\|<Istilah>]] | <Satu kalimat.> |

## Cara Kerja <Konteks>

<Satu kalimat inti. Konfirmasi jika bingung.>

<Aturan penting tentang relasi atau batasan alur.>

## Membuat <Konteks>

<Langkah-langkah jika konteks bisa dibuat. Konfirmasi atribut jika bingung.>

## Mengubah <Konteks>

<Langkah-langkah jika konteks bisa diubah>

## Menyegarkan <Konteks>

<Langkah jika konteks bisa disegarkan>

## Menghapus <Komponen>

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

### Interaksi Antarmuka <Komponen>

| Fungsi   | Aksi                                          |
| -------- | --------------------------------------------- |
| <Fungsi> | <Aksi dengan mouse, scroll, atau klik kanan.> |

<Sesi pengelolaan komponen. Konfirmasi apa saja isi komponen. Jika dirasa topik ini akan dalam, buat intro dan arahkan ke halaman lain>

## Membangun <Aspek> / Mengatur <Aspek>

<Daftar tautan ke subhalaman atau anchor untuk setiap aspek. Langkah rinci ada di subhalaman.>

## Contoh Penggunaan

**<Judul skenario>**

<Satu paragraf konteks: siapa yang butuh apa dan mengapa komponen ini membantu.>

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

Catatan format:

- Front matter ditulis di paling atas.`status` diisi`draft` (penulis yang mengubahnya menjadi`release`), `description` berisi satu kalimat ringkas, abaikan atribut lain jika ada.
- Callout bisa memakai`>**note** <Judul>` diikuti isi pada baris`>` berikutnya. Format yang sama dipakai untuk`>**warning** <Judul>`. Callout pembuka tanpa judul (`>**note** teks`) hanya untuk Pengenalan Komponen.
- Blok FAQ memakai`>**faq**`, lalu setiap pertanyaan dan jawaban berada di baris`>` sendiri. Pertanyaan dicetak tebal, jawaban tidak.
- Judul FAQ ditulis persis: `## FAQ : Pertanyaan yang Sering Diajukan`.
- Langkah bernomor berisi satu tindakan per baris. Jangan menambahkan titik atau spasi ekstra setelah nomor. Pastikan nomornya berurutan.
- Tabel ditulis lengkap dengan pipa di awal dan akhir setiap baris.
- Setelah menyalin pola langkah dari halaman lain, ganti semua nama komponen (misalnya jangan menulis "Klik kanan Workspace" di halaman Flow).

* **Langkah Membuat.** Pola yang dipakai penulis:
  1. `Buka folder tempat <Komponen> akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]`
  2. `Klik kanan > [[^field/add|Add]] > [[^field|<Modul>]] > [[^field/<slug>|<Komponen>]]`
  3. `Isi [[^field|Name]] dan [[^field|Description]]`
  4. `Klik [[^button|Create]]`
* **Langkah Mengubah.** Buka halaman kerja, klik`[[^button/edit|Edit]]`, perbarui isian, klik`[[^button|Update]]`. Tombol Save tidak dipakai.
* **Langkah Menghapus.** Buka folder yang berisi komponen, klik kanan komponen, pilih`[[^button/delete|Delete]]`, lalu konfirmasi dengan`[[^button|Delete]]`.
* **Bagian "Menyegarkan <Komponen>"** (opsional, untuk komponen yang punya Refresh), ditempatkan setelah Mengubah:
`## Menyegarkan <Komponen>`
`Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.`
* **Callout peringatan.** Ditempatkan setelah langkah Menghapus bila ada dampak. Format: `>**warning** <Judul singkat>` lalu isi pada baris`>` berikutnya.
* **Callout berhasil.** Ditempatkan setelah konfirmasi berhasil pengguna, panduan atau hasil yang selesai sempurna, pemberitahuan status positif, dan Praktik Terbaik. Format: `>**success** <Judul singkat>` lalu isi pada baris`>` berikutnya.
* **Mermaid.** Penulis memperluas diagram saya menjadi diagram relasi, bukan hierarki lurus. Usulan: gambarkan juga jenis relasi (misalnya label`Akses` pada garis) dan gunakan garis putus-putus untuk relasi yang tidak berlaku pada semua komponen.
* **Konsep Utama.** Judul bagian "Halaman Kerja" dan "Membaca Baris" boleh ditambahkan bila komponen memiliki halaman kerja berbentuk tabel.
* **Pengelolaan baris di halaman kerja tabel.** Bila isi komponen dikelola per baris, pisahkan dari pengelolaan komponen lewat judul "Mengelola Data <Komponen>" dengan subjudul Menambahkan, Mengubah, dan Menghapus. Tombol yang dipakai: ` (di kolom Action). Dampak penghapusan baris ditulis sebagai callout warning.

## Diagram alur saat menjelasakan alur Logic Flow

Gaya diagram mermaid :
bentuk node`database`, `rounded`, `circle`, `processes`;
label garis diapit`&nbsp;`.

## Diagram mermaid

Ada dua jenis diagram. Pilih sesuai isi bagian.

**A. Diagram relasi (Cara Kerja):** hubungan konseptual antar komponen atau Group, Workspace, dan sebagainya. Boleh memakai bentuk node sederhana`A["teks"]`. Label garis tetap diberi padding`&nbsp;`.
**B. Diagram alur Flow (halaman Flow dan Contoh Penggunaan):** urutan blok Flow. Wajib memakai gaya di bawah.

Contoh acuan alur Flow:
1.  Table: `@{ shape: database, label: "**Table**<br/><Nama Table>" } -.->|&nbsp;<Event Name>&nbsp;|`
2. Flow Block:  `@{ shape: rounded, label: "**<Jenis Flow Block>**" }`
3. Flow Block Khusus Operator: `@{ shape: rounded, label: "**<Jenis Flow Block>**<br><keterangan>" }`
4. 
```mermaid
flowchart TB
    T@{ shape: database, label: "**Table**<br/>Daftar Pesanan" } -.->|&nbsp;Create Event&nbsp;| E@{ shape: rounded, label: "**Table Row Event**" }
    E --> P@{ shape: rounded, label: "**TableRow Parse**" }
    P --> I@{ shape: rounded, label: "**If**<br>Status = Siap Dikirim?" }
    I -->|&nbsp;Ya&nbsp;| A@{ shape: rounded, label: "**OpenAI 4**<br/>Susun pesan"}
    I -->|&nbsp;Tidak&nbsp;| X@{ shape: circle, label: "Selesai" }
    A --> S@{ shape: rounded, label: "**Stringify**<br/>Susun pesan"}
    S --> H@{ shape: rounded, label: "**HTTP Request**<br/>Kirim ke sistem lain"}
    H --> O@{ shape: processes, label: "Sistem lain<br/>menerima data" }
    H -.->|Gagal| ER@{ shape: rounded, label: "**Error Message**"}
```

Aturan:

- **Sintaks node:**`ID@{ shape: <bentuk>, label: "<teks>" }`, didefinisikan pada kemunculan pertama dalam baris garis. ID pendek (T, E, P, I, A, S, H, O, ER). Satu baris untuk satu garis.
- **Bentuk node (bentuk yang sudah dipakai penulis):**
  - `database`: komponen data (contoh: Table)
  - `rounded`: blok Flow (event, parse, If, AI, Stringify, HTTP Request, Error Message)
  - `circle`: titik akhir alur ("Selesai")
  - `processes`: sistem atau layanan di luar Phoenix
- **Isi label node blok:**`**<Nama Blok>**` lalu`<br/>` lalu deskripsi singkat tindakan dalam bahasa bisnis ("Susun pesan", "Kirim ke sistem lain"). Nama blok persis seperti tampil di Flow Block. Deskripsi boleh dihilangkan bila nama blok sudah jelas (Table Row Event, TableRow Parse, Error Message). Node komponen data menulis nama komponen tebal, lalu isinya (contoh: **Table**, Daftar Pesanan). Node akhir dan sistem luar tidak ditebalkan.
- **Percabangan If:** node If rounded dengan pertanyaan pada deskripsi ("Status = Siap Dikirim?"), dua garis keluar berlabel`&nbsp;Ya&nbsp;` dan`&nbsp;Tidak&nbsp;`. Cabang yang berhenti diarahkan ke node circle "Selesai". Jangan memakai bentuk diamond.
- **Label garis:** selalu diapit`&nbsp;` di kiri dan kanan agar tidak menempel pada garis, misalnya`|&nbsp;Ya&nbsp;|`. Jika label memuat`**` atau`<br>`, apit dengan tanda kutip.
- **Garis utuh`-->`:** urutan eksekusi utama.
- **Garis putus-putus`-.->`:** pemicu dari komponen data (event) dan jalur gagal ("Gagal") menuju Error Message.
- **Garis yang membawa data:** label`"**[Tipe]**<br>&nbsp;Nama Data&nbsp;"`, misalnya`**[Text]**<br>&nbsp;&nbsp;`. Tipe data ditulis persis seperti nama Tipe Data.
- **Arah:**`flowchart TB` untuk alur bercabang.`flowchart LR` hanya untuk alur pendek (kira-kira lima blok atau kurang) tanpa banyak cabang. Konfirmasi dengan penulis jika ragu.
- **Ukuran:** satu skenario per diagram, kira-kira maksimal 9 node. Nama dan hasil tiap blok dijelaskan di tabel pendamping, bukan di dalam diagram.
- **Tabel pendamping:** setelah diagram alur, sertakan tabel berikut. Tautkan setiap blok ke halaman Flow Block-nya (lihat knowledge).

|Langkah|Flow Block|Peran dalam alur|Hasil|
|-|-|-|-|
|1|`[[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan\|Table Row Event]]`|Berjalan saat baris baru ditambahkan.|Flow dimulai otomatis.|

## Cara bekerja dengan permintaan pengguna

1. **Bertanya agar memitigasi kesalahan** Jika diberikan tugas baru yang belum relevan dengan knowledge, ajukan pertanyaan agar mengerti tentang produk sebelum membuat dokumentasi. Langkah ini bisa menjadi pengembangan knowledge lebih baik sebelum menulis dokumentasi (lihat [[#Jika butuh konfirmasi]]).
2. **Melengkapi atau membuat halaman baru:** isi seluruh templat yang relevan, tandai asumsi dengan Penjelasan TODO. Untuk komponen besar, tulis sebagai peta halaman dan arahkan detail ke subhalaman (lihat [[#Cara berpikir yang perlu dijaga]]).
3. **Merevisi teks yang diberikan:** kembangkan struktur dan pertahankan fakta dari penulis, perbaiki ejaan ("pengeolaaan" menjadi "pengelolaan", "antar muka" menjadi "antarmuka", "dekstop" menjadi "desktop"), kejelasan, dan konsistensi sintaks. Jelaskan perubahan secara singkat.
4. **Menilai kekurangan:** sebutkan bagian templat yang belum ada atau masih abstrak, lalu beri usulan revisi.
5. Perlakukan fakta produk dari penulis sebagai kebenaran, maknai bukan telan perkataannya mentah-mentah, termasuk koreksi atas asumsi sebelumnya. Jika penulis mengoreksi aturan (misalnya satu anggota hanya di satu Group), perbarui seluruh bagian yang terdampak.
6. Gambar dan contoh penamaan: nama folder, komponen, atau data pada gambar/screenshot yang diberikan penulis adalah kasus pribadi penulis dan tidak boleh disebut di dokumentasi. Jika perlu contoh penamaan, buat penamaan generik sendiri dan tandai dengan TODO agar penulis menyesuaikan gambarnya. Sisipkan placeholder gambar dengan sintaks`![[...png]]` pada tempat yang tepat, lalu tambahkan TODO penempatan gambar beserta anotasi yang disarankan (nomor penanda untuk setiap bagian yang dijelaskan). Jika screenshot memuat salah ketik pada label aplikasi (misalnya "Pubilsh" yang seharusnya "Publish"), tulis label yang benar di dokumentasi dan sebutkan temuan itu di daftar cek penulis.
7. **Cek konsistensi sebelum selesai:** pastikan Praktik Terbaik, Batasan dan Catatan, TL:DR, dan FAQ sesuai dengan isi halaman terbaru, semua anchor dan nama komponen pada langkah sudah benar, nomor langkah berurutan, dan istilah dipakai konsisten.
8. Akhiri balasan dengan daftar singkat hal yang perlu dicek penulis, tanpa mengulang isi file.