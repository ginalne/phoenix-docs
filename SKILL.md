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
- Istilah asing yang bukan nama fitur ditulis miring dengan `*...*`, misalnya `*drag and drop*`, `*least privilege*`.
- Jangan mengarang perilaku produk. Jika detail fitur belum diketahui (nama menu, batasan, aturan akses), tulis tebakan terbaik dan tandai serta tambahkan usul perlunya gambar melalui Penjelasan TODO (lihat cara penulisan [[#Penulisan TODO]],  Penulis akan memperbaiki isinya sendiri.
-  Struktur yang kuat lebih penting daripada detail yang meyakinkan tapi salah.
-  Pahami konteks halaman yang diminta, silahkan buat struktur yang terbaik untuk halaman tersebut, jangan terlalu kaku, agar penulis tahu kemungkinan terbaik dalam menjelaskan konteks halaman tersebut.
- Untuk konsep yang sudah punya halaman sendiri (Komponen, Folder, Pro), jangan mendaftar contoh di tabel Konsep Utama. Cukup beri satu kalimat singkat dan tautkan ke halamannya ("Selengkapnya lihat [[...]]").
- Gunakan istilah "bilah navigasi", bukan "navbar".
- Saat penulis mengembalikan halaman yang sudah direvisi dengan jawaban pada TODO (format `* jawaban:`), perlakukan jawaban itu sebagai fakta, perbarui seluruh bagian yang terdampak, dan hapus blok TODO yang sudah terjawab.
- Jika topik komponen cukup dalam (misalnya Data Access), tulis ringkasan di halaman utama dan arahkan ke subhalaman dengan tautan, lalu tandai dengan TODO bahwa subhalaman perlu dibuat.
-  Hasilkan file `.md`, bukan teks biasa di chat, kecuali pengguna hanya meminta komentar atau review.
-  Setiap kali saya memberi informasi baru dalam penulisan dokumentasi Phoenix, tulis di akhir jawaban bagian **"Usulan update /phoenix-docs-silverbullet SKILL.md"**. Isinya alasan pembaharuannya, lalu sertakan file.md nya agar perubahan skill menjadi mudah diclaude. Jika tidak ada yang relevan, jangan tulis bagian itu.
-  Setiap kali saya memberi informasi baru dalam dokumentasi Phoenix, tulis di akhir jawaban bagian **"Usulan update skill /phoenix-docs-silverbullet KNOWLEDGE.md"**, lalu sertakan file.md nya agar perubahan skill menjadi mudah diclaude. Isinya alasan pembaharuannya. Jika tidak ada yang relevan, jangan tulis bagian itu.

## Konvensi tautan

| Halaman | Format | Variasi | Contoh |
| --- | --- | --- | --- |
| Halaman konsep umum | `[[Inisialisasi/Apa itu Pro?\|Pro]]`, `[[Docs/Apa itu Komponen?]]`, `[[Docs/Folder/Apa itu Folder?]]` | Pro, Komponen, Folder | `[[Docs/Folder/Apa itu Folder?#Informasi Data]]` |
| Event | `[[Docs/Event/Apa itu Event\|Event]]` | Menggantikan `Docs/Event/Pengenalan` | - |
| Subhalaman komponen | `[[Docs/Modul <Nama>/<Komponen>/<Subhalaman>]]` | Data Access, TimelineData | `[[Docs/Modul Developer/Workspace/Data Access]]` |
| Tipe data milik komponen | `[[Docs/Modul <Nama>/<Komponen>/<Tipe>]]` | TimelineData | `[[Docs/Modul Interface/Timeline/TimelineData]]` |
| Modul <Nama> | `[[Docs/Modul <Nama>/Pengenalan\|<Nama>]]` | Data, Interface, Logic, Developer `[[Docs/Modul Developer/Pengenalan\|Developer]]` |
| Komponen | `[[Docs/Modul <Nama>/<Komponen>/Apa itu <Komponen>]]` | Data: Variable, Enum, Table, Tree. Interface: Table View, Gallery, Canvas, Kanban, Space, Timeline, Form. Logic: Flow. Developer: Group, Workspace | `[[Docs/Modul Logic/Flow/Apa itu Flow]]` |
| Tipe Data | `[[Docs/Tipe Data/<Nama>]]` | Color, Tree, Expression, Mixed, Array, Boolean, Column, Number, Enum, EnumData, Complex, Month, Thing, Year, MonthYear, Text, Matrices, Node, Object, File, Query, Row, String, Table, TableData, Variable, Date, Time, DateTime, DateTimeZone | `[[Docs/Tipe Data/String]]` |
| Format Data | `[[Docs/Format Data/<Tipe Data>/<Nama>]]` | String: Short Text, Password, Email, Phone Number, Mobile Number, URL, Slug, Username, Full Name, First Name, Initial, Country Code, Postal Code, License Plate, National ID, Passport Number, Tax ID, Bank Account, IBAN, Credit Card, MAC Address, IPv4, IPv6, UUID, Emoji. Number: Number, Integer, Decimal, Percentage, Rating. Text: Long Text, Rich Text, Markdown, Note, Chat. Complex: Numeration Unit, Length Unit, Area Unit, Volume Unit, Quaternion Unit, 1D Vector, 2D Vector, 3D Vector, 4D Vector, Geo, Currency. File: Attachment, Document, Media, Image, Photo, Audio, Video, Icon. Array: Popup List, Checkboxes, Direct List, Multiple Select. EnumData: Dropdown, Multiple Choices. | `[[Docs/Format Data/String/Short Text]]`
| Anchor di halaman yang sama | `[[#Nama Bagian]]` | - | `[[#Flow]]` |
| Tautan dengan teks lain | tambahkan alias setelah `\|` | Tidak ada. Silahkan sarankan ide untuk penjelasan jika dibutuhkan | `[[Docs/Event/Pengenalan\|Event]]` |
| Anchor di halaman lain | `[[Docs/Antar Muka#Area Manajemen Folder]]`| [[Docs/Antarmuka#Bilah Navigasi]]` Header Navigation Phoenix. `[[#Area Manajemen Folder]]` bagian pengelolaan folder dan komponen. [[#Halaman Kerja]]` antarmuka kerja komponen | |
| Menu atau contextmenu antarmuka | `[[^field/<icon>\|<Label>]]` | icon: add, delete, edit, save, copy, paste, eye, collapse, expand, import, export, [slug komponen] | `[[^field/add\|Add]]` |
| Kolom isian antarmuka | `[[field\|<Label>]]` | - | `[[field\|Name]]`, `[[field\|Description]]`
| Tombol antarmuka | `[[^button/<icon>\|<Label>]]` atau `[[^button\|<Label>]]` | icon: edit, delete, merge, publish, refresh, save, submission. Tanpa icon untuk tombol aksi umum seperti Create, Update, Delete (konfirmasi) | `[[^button/edit\|Edit]]`, `[[^button\|Create]]` |
| Nilai Boolean | `[[^value/boolean/allow]]`, `[[^value/boolean/disallow]]`, `[[^value/boolean/true]]`, `[[^value/boolean/disallow]]` | Gunakan di dalam tabel dan kalimat, bukan teks tebal | `[[^value/boolean/false]]` |
| Nama komponen/folder/data pada baris tabel | `[[^field/<slug>\|<Nama>]]` | slug: workspace, group, folder, variable, enum, table, tableview, tree, canvas, dan slug komponen lain | `[[^field/tableview\|Daftar Pelanggan]]` |

Catatan: alias tidak boleh diawali spasi (contoh salah: [[^field/workspace| Workspace]]).

Tautkan komponen lain pada kemunculan pertamanya di sebuah halaman (misalnya Workspace di halaman Group). Label menu dan field ditulis persis seperti yang tampil di aplikasi, bukan diterjemahkan. Jika path tautan hanya tebakan, tandai dengan [[#Penjelasan TODO]].

## Penjelasan TODO

Penulisan TODO sebagai catatan untuk diperhatikan kepada penulis harus dibuat dalam bentuk comment, dengan format sebagai berikut:

<!--
  * [TODO] Deskripsi Task
-->

Pembuka `<!--` dan penutup `-->` harus dalam line nya sendiri, serta tambahkan baris kosong agar memastikan format terbaca dengan baik.

Deskripsi Task harus jelas, dan jika comment ini letak cukup jauh dari tulisan yang dimaksud, silahkan buat link dengan tagar untuk seperti ini: [[#Penjelasan TODO]].

## Templat halaman

Gunakan urutan berikut. Bagian yang tidak relevan boleh dihilangkan, tetapi jangan mengubah urutan atau nama judulnya.

````markdown
# Judul

<callout untuk Pengenalan Komponen>
>**note** _<Komponen>_ merupakan salah satu komponen dalam modul [[Docs/Modul <Modul>/Pengenalan|<Modul>]] di Phoenix.

_<Komponen>_ adalah komponen yang dapat digunakan untuk <fungsi utama>.

<penjelasan dari segi kemudahan, solusi dan keunikan komponen ini>.

## Mengapa Menggunakan <Komponen>?
- **<Manfaat singkat>.** <Penjelasan satu kalimat.>

## Konsep Utama
| Istilah | Penjelasan |
| --- | --- |
| **<Istilah>** | <Penjelasan.> |

## Cara Kerja <Komponen>
<Satu kalimat inti. Konfirmasi jika bingung.>

```mermaid
<jelaskan hubungan dalam Phoenix. Konfirmasi jika bingung.>
```

<Aturan penting tentang relasi atau batasan alur.>

## Membuat <Komponen>
<Langkah-langkah. Konfirmasi atribut jika bingung.>

## Mengubah <Komponen>
<Langkah-langkah>

## Menghapus <Komponen>
<Langkah-langkah>

<Sesi pengelolaan komponen. Konfirmasi apa saja isi komponen. Jika dirasa topik ini akan dalam, buat intro dan arahkan ke halaman lain>

## Mengatur <aspek>

## Contoh Penggunaan
**<Judul skenario>**

| ... | ... | ... |
| --- | --- | --- |

<Satu kalimat penutup tentang manfaat skenario ini.>

## Praktik Terbaik
- <Saran dengan frasa kunci dicetak **tebal**.>

## Batasan dan Catatan
- <Poin singkat.>

## TL:DR

## FAQ : Pertanyaan yang Sering Diajukan

>**faq**
>**<Pertanyaan?>**
>Jawaban.
>**<Pertanyaan?>**
>Jawaban.
````

Catatan format:
- Callout pembuka bisa memakai `>**note**` diikuti spasi dan teks.
- Blok FAQ memakai `>**faq**`, lalu setiap pertanyaan dan jawaban berada di baris `>` sendiri. Pertanyaan dicetak tebal, jawaban tidak.
- Judul FAQ ditulis persis: `## FAQ : Pertanyaan yang Sering Diajukan`.
- Langkah bernomor berisi satu tindakan per baris. Jangan menambahkan titik atau spasi ekstra setelah nomor.
- Tabel ditulis lengkap dengan pipa di awal dan akhir setiap baris.
* **Langkah Membuat.** Pola yang dipakai penulis:
    1.  `Buka folder tempat <Komponen> akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]`
    2.  `Klik kanan > [[^field/add|Add]] > [[^field|<Modul>]] > [[^field/<slug>|<Komponen>]]`
    3.  `Isi [[^field|Name]] dan [[^field|Description]]`
    4.  `Klik [[^button|Create]]`
* **Langkah Mengubah.** Buka halaman kerja, klik `[[^button/edit|Edit]]`, perbarui isian, klik `[[^button|Update]]`. Tombol Save tidak dipakai.
* **Langkah Menghapus.** Klik kanan komponen, pilih `[[^button/delete|Delete]]`, lalu konfirmasi dengan `[[^button|Delete]]`.
* **Bagian baru "Menyegarkan"** (opsional, untuk komponen yang punya Refresh), ditempatkan setelah Mengubah:
 ` *   ## Menyegarkan
  Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.`
  * **Callout peringatan.** Format baru yang dipakai penulis, ditempatkan setelah langkah Menghapus bila ada dampak:
    `* **warning** <Judul singkat>`
    `>Isi peringatan.
*   **Mermaid.** Penulis memperluas diagram saya menjadi diagram relasi, bukan hierarki lurus. Usulan: gambarkan juga jenis relasi (misalnya label `Akses` pada garis) dan gunakan garis putus-putus untuk relasi yang tidak berlaku pada semua komponen.
*   **Konsep Utama.** Judul bagian "Halaman Kerja" dan "Membaca Baris" boleh ditambahkan bila komponen memiliki halaman kerja berbentuk tabel.

  

## Cara bekerja dengan permintaan pengguna

1. **Melengkapi atau membuat halaman baru:** isi seluruh templat yang relevan, tandai asumsi dengan Penjelasan TODO.
2. **Merevisi teks yang diberikan:** kembangkan struktur dan pertahankan fakta dari penulis, perbaiki ejaan ("pengeolaaan" menjadi "pengelolaan", "antar muka" menjadi "antarmuka"), kejelasan, dan konsistensi sintaks. Jelaskan perubahan secara singkat.
3. **Menilai kekurangan:** sebutkan bagian templat yang belum ada atau masih abstrak, lalu beri usulan revisi.
4. Perlakukan fakta produk dari penulis sebagai kebenaran, termasuk koreksi atas asumsi sebelumnya. Jika penulis mengoreksi aturan (misalnya satu anggota hanya di satu Group), perbarui seluruh bagian yang terdampak.
5. Gambar dan contoh penamaan: nama folder, komponen, atau data pada gambar/screenshot yang diberikan penulis adalah kasus pribadi penulis dan tidak boleh disebut di dokumentasi. Jika perlu contoh penamaan, buat penamaan generik sendiri dan tandai dengan TODO agar penulis menyesuaikan gambarnya. Tambahkan TODO penempatan gambar beserta anotasi yang disarankan (nomor penanda untuk setiap bagian yang dijelaskan). Jika screenshot memuat salah ketik pada label aplikasi (misalnya "Pubilsh" yang seharusnya "Publish"), tulis label yang benar di dokumentasi dan sebutkan temuan itu di daftar cek penulis.
6. Akhiri balasan dengan daftar singkat hal yang perlu dicek penulis, tanpa mengulang isi file.