---
      status: draft
      title: Apa itu Space?
      description: Space adalah komponen untuk menaungi dan mengorganisasi data dalam bentuk 3D (tiga dimensi) sehingga data dan hubungan antar data dapat dijelajahi dari berbagai sudut pandang.
---

# Apa itu Space?

>**note** Space merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Space adalah komponen yang menaungi dan mengorganisasi data dalam bentuk 3D (tiga dimensi).

Dengan Space, Anda dapat memvisualisasikan data beserta hubungan antar data dalam ruang tiga dimensi dan menjelajahinya dari berbagai sudut pandang, sehingga pola dan keterkaitan yang sulit terlihat pada tampilan tabel menjadi lebih mudah dipahami. Isi Space dibangun dari tiga jenis data, yaitu [[#Mengelola Weather|Weather]] untuk suasana ruang, [[#Mengelola Environment|Environment]] untuk benda statis, dan [[#Mengelola Object|Object]] untuk data riil yang tampil sebagai objek 3D.

## Mengapa Menggunakan Space?

- **Melihat pola yang tersembunyi di tabel.** Data dan hubungan antar data ditampilkan dalam ruang 3D, sehingga keterkaitan yang sulit terlihat pada [[Docs/Tipe Data/Table]] menjadi lebih mudah dipahami.
- **Menjelajah dari berbagai sudut pandang.** Anda dapat memutar, menggeser, dan memperbesar tampilan untuk melihat data dari sisi mana pun.
- **Terhubung langsung dengan data riil.** [[#Mengelola Object|Object]] memakai [[Docs/Tipe Data/Query|Query]] dengan kaidah Table Output, sehingga setiap [[Docs/Tipe Data/Row]] pada data sumber dapat tampil sebagai objek 3D.
- **Ruang yang dapat dirancang sesuai kebutuhan.** [[#Mengelola Weather|Weather]], [[#Mengelola Environment|Environment]], dan [[#Mengelola Object|Object]] dapat digabungkan dalam satu ruang untuk membentuk suasana, latar, dan data yang dipantau.
- **Mengubah nilai langsung dari panel.** Nilai pada [[#Panel Properti|Panel Properti]] dapat diubah dan, untuk Object, memengaruhi Row sebenarnya pada data sumber.

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[#Antarmuka Space|Outliner]] | Panel di sisi kiri halaman kerja yang mengelompokkan data Space menjadi Weather, Environment, dan Object beserta jumlah datanya. |
| [[#Mengelola Weather|Weather]] | Data yang tampil sebagai *world effect*, yaitu efek yang berlaku pada seluruh ruang 3D. |
| [[#Mengelola Environment|Environment]] | Data berupa benda statis tanpa logika yang dibuat dari file 3D. |
| [[#Mengelola Object|Object]] | Data berlogika yang dirender sebagai objek 3D sesuai jumlah Row hasil Query. |
| [[Docs/Tipe Data/Query]] | Pengambil data untuk Weather (kaidah Single Output) dan Object (kaidah Table Output). |
| [[Docs/Modul Developer/Model/Apa itu Model|Model]] | Komponen di modul Developer yang menyiapkan wujud dan logika Object, termasuk daftar Key. |
| [[#Mengatur Model Attribute|Model Attribute]] | Tabel yang menentukan nilai setiap Key Model pada Object, secara static atau bind. |
| [[#Panel Properti]] | Panel di sisi kanan halaman kerja untuk melihat dan mengubah nilai data yang difokuskan. |
| [[Docs/Modul Developer/Workspace/Data Access|Data Access]] | Pengaturan di Workspace yang menentukan siapa yang dapat menambah, mengubah, dan menghapus data. |

## Cara Kerja Space

Space menaungi data Weather, Environment, dan Object lalu menampilkannya bersama dalam satu ruang 3D, dengan Weather dan Object mengambil nilainya dari [[Docs/Tipe Data/Query]] sedangkan Environment memakai file 3D.

```mermaid
flowchart LR
  W["Workspace"] -->|"&nbsp;Data Access&nbsp;"| S["Space"]
  S --> A["Weather"]
  S --> B["Environment"]
  S --> C["Object"]
  T["Table"] -.->|"&nbsp;Query Single Output&nbsp;"| A
  T -.->|"&nbsp;Query Table Output&nbsp;"| C
  M["Model<br/>(modul Developer)"] -->|"&nbsp;Model&nbsp;"| C
  F["File 3D"] -->|"&nbsp;Upload&nbsp;"| B
```

## Membuat Space

![[Docs/Modul Interface/Space/add-space.png]]
1. Buka folder tempat Space akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Interface]] ➜ [[^field/space|Space]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Klik [[^button|Create]]

Bagian di kiri tanda `/` pada [[^field|Name]] menunjukkan folder tempat Space ditempatkan, dan dapat dikosongkan agar Space berada di root.

>**success** Space berhasil dibuat
> Space yang baru dibuat belum memiliki data. Tambahkan [[#Mengelola Weather|Weather]], [[#Mengelola Environment|Environment]], atau [[#Mengelola Object|Object]] melalui [[#Antarmuka Space|Outliner]].

## Mengubah Space

1. Buka halaman kerja Space
2. Klik [[^button/edit|Edit]]
3. Ubah [[^field|Name]] atau [[^field|Description]]
4. Klik [[^button|Update]]

Anda dapat klik [[^button/x|Cancel]] untuk membatalkan perubahan Space. Tombol [[^button/edit|Edit]] hanya mengubah atribut Space; untuk mengubah nilai Weather, Environment, dan Object gunakan [[#Panel Properti]].

## Menyegarkan Space

Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.

## Menghapus Space

1. Buka folder yang berisi Space di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan Space ➜ [[^button/delete|Delete]]
3. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Seluruh isi Space ikut terhapus
> Seluruh data [[#Mengelola Weather|Weather]], [[#Mengelola Environment|Environment]], dan [[#Mengelola Object|Object]] beserta konfigurasi [[Docs/Tipe Data/Query|Query]] dan [[#Mengatur Model Attribute|Model Attribute]] akan hilang. [[Docs/Tipe Data/Row]] pada data sumber tidak ikut terhapus.

## Antarmuka Space

![[Docs/Modul Interface/Space/interface-space.png]]
Halaman kerja Space terdiri dari bilah navigasi di bagian atas dan area kerja di bagian bawah. Bilah navigasi menampilkan ikon Space dan [[^field|Header Name]] di sisi kiri.

### Bilah navigasi Space terdiri dari:

| Tombol | Fungsi |
| --- | --- |
| [[^button/edit|Edit]] | Mengubah [[^field|Name]] dan [[^field|Description]] Space. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan halaman kerja. |
| [[^field|Search Space Data...]] | Mencari data pada Outliner berdasarkan Name, termasuk data milik Object yang jumlahnya banyak. |

### Area kerja Space

Area kerja berisi tiga bagian:

1. **View 3D** menampilkan ruang berupa grid lantai dengan penanda sumbu berwarna di titik pusat: x berwarna merah, y berwarna hijau, dan z berwarna biru. Di sinilah Weather, Environment, dan Object ditampilkan.
2. **Outliner** di sisi kiri mengelompokkan data menjadi [[^field|Weather]], [[^field|Environment]], dan [[^field|Object]]. Angka di samping nama kelompok, misalnya `(0)`, adalah jumlah data pada kelompok tersebut. Klik panah di samping nama kelompok untuk membuka atau menutup daftar data.
3. **Panel Properti** di sisi kanan menampilkan nilai data yang difokuskan. Jika belum ada data yang difokuskan, panel menampilkan [[^field|No selection]]. Selengkapnya lihat [[#Panel Properti]].

>**note** Perbedaan tampilan desktop dan mobile
> Pada desktop, view 3D dikendalikan dengan mouse dan keyboard. Pada mobile, view 3D dikendalikan dengan gestur sentuh.

### Interaksi Antarmuka Space

| Fungsi | Aksi |
| --- | --- |
| Memutar sudut pandang | Tekan dan tahan klik kiri pada view 3D, lalu gerakkan kursor. |
| Menggeser tampilan | Tahan tombol Shift, lalu tekan dan tahan klik kiri pada view 3D dan gerakkan kursor. |
| Memperbesar atau memperkecil tampilan | Putar roda mouse (*wheel*) pada view 3D. |
| Memfokuskan data | Klik data pada Outliner, atau klik langsung objek pada view 3D. |
| Memindahkan objek 3D yang difokuskan | Gunakan alat bantu pemindah yang muncul pada objek 3D yang difokuskan. Perubahan nilai hasil pemindahan memperbarui Row sumber jika atributnya di-*bind*. Tidak berlaku untuk Environment, yang diubah lewat [[#Panel Properti]]. |
| Mengubah Origin | Klik kanan Object pada Outliner ➜ [[^field/edit|Edit]]. |
| Menambah data | Klik kanan pada Outliner ➜ [[^field/add|Add Weather]], [[^field/add|Add Environment]], atau [[^field/add|Add Object]]. |
| Menghapus data | Klik kanan data pada Outliner ➜ [[^button/delete|Delete]]. |
| Mengendalikan view 3D di mobile | Geser satu jari untuk memutar, geser dua jari untuk menggeser, dan cubit dengan dua jari untuk memperbesar atau memperkecil tampilan. |

## Mengelola Weather

Weather adalah data yang tampil sebagai *world effect*, yaitu efek yang berlaku pada seluruh ruang 3D dan bukan pada satu benda tertentu.

| Atribut | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Priority]] | [[Docs/Tipe Data/Number]] | Urutan prioritas Weather. Bila ada banyak Weather dengan [[^field|Type]] yang sama, yang dipakai adalah Priority terkecil. |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Weather. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan Weather. |
| [[^field|Type]] | - | Jenis efek yang menentukan properti uniknya. Pilihannya [[^value/radio|Earth Sky]] dan [[^value/radio|Sea]]. |
| [[^field|Status]] | [[Docs/Tipe Data/Boolean]] | [[^value/boolean/true]] berarti Weather ikut dipertimbangkan, [[^value/boolean/false]] berarti diabaikan. |

[[^field|Type]] Weather yang dapat digunakan saat ini:

| [[^field|Type]] | Properti | Tipe Data | Penjelasan |
| --- | --- | --- | --- |
| [[^value/radio|Earth Sky]] | [[^field|Time]] | [[Docs/Tipe Data/DateTime]] atau [[Docs/Tipe Data/DateTimeZone]] | Waktu yang digunakan untuk langit. |
| [[^value/radio|Sea]] | [[^field|Level]] | [[Docs/Tipe Data/Number]] | Level laut. |
| [[^value/radio|Sea]] | [[^field|Wave Rate]] | [[Docs/Tipe Data/Number]] | Laju gelombang laut. |

Setiap properti pada [[^field|Type]] memiliki *toggle* pada field nilainya untuk memilih pengisian dengan nilai langsung (statis) atau [[Docs/Tipe Data/Query|Query]] dengan kaidah [[Docs/Tipe Data/Query#Single Output|Single Output]]. Karena Query Single Output menghasilkan satu nilai hasil kalkulasi, nilai tersebut mengikuti data sumbernya.

>**note** Aturan Priority dan Status
> Hanya satu Weather untuk setiap [[^field|Type]] yang berlaku, yaitu Weather dengan [[^field|Status]] [[^value/boolean/true]] dan [[^field|Priority]] terkecil. Weather dengan [[^field|Status]] [[^value/boolean/false]] tidak ikut dihitung.

### Menambahkan Weather

1. Buka halaman kerja Space
2. Klik kanan pada [[#Antarmuka Space|Outliner]] ➜ [[^field/add|Add Weather]]
3. Isi [[^field|Name]], [[^field|Description]], [[^field|Priority]], [[^field|Type]], dan [[^field|Status]]
4. Isi properti sesuai [[^field|Type]] dengan nilai langsung atau [[Docs/Tipe Data/Query|Query]], dipilih lewat *toggle* pada field nilainya

### Mengubah Weather

1. Fokuskan Weather yang akan diubah
2. Ubah nilai pada [[#Panel Properti]]

Perubahan [[^field|Priority]] atau [[^field|Status]] dapat mengubah Weather mana yang berlaku untuk [[^field|Type]] yang sama.

### Menghapus Weather

1. Klik kanan Weather pada [[#Antarmuka Space|Outliner]]
2. Klik [[^button/delete|Delete]]

>**warning** Efek Weather hilang dari ruang
> Efek Weather tidak lagi tampil di ruang 3D. Jika masih ada Weather lain dengan [[^field|Type]] yang sama dan [[^field|Status]] [[^value/boolean/true]], Weather dengan [[^field|Priority]] terkecil berikutnya yang akan dipakai.

## Mengelola Environment

Environment adalah data yang tampil sebagai objek 3D statis tanpa logika. Anda cukup meng-*upload* file 3D untuk menjadikannya benda di dalam ruang, misalnya bangunan, lantai, atau perabot.

| Atribut | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Environment. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan Environment. |
| [[^field|Position]] | [[Docs/Format Data/Complex/3D Vector|3D Vector]] | Posisi Environment di ruang 3D. |
| [[^field|Scale]] | [[Docs/Format Data/Complex/Volume Unit|Volume Unit]] | Ukuran (skala) Environment pada sumbu x, y, dan z. |
| [[^field|Rotation]] | [[Docs/Format Data/Complex/Euler Angle|Euler Angle]] | Rotasi Environment. |
| [[^field|Model]] | File 3D | File 3D yang di-*upload* sebagai wujud Environment. |

### Menambahkan Environment

1. Buka halaman kerja Space
2. Klik kanan pada [[#Antarmuka Space|Outliner]] ➜ [[^field/add|Add Environment]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Upload file 3D pada [[^field|Model]]
5. Atur [[^field|Position]], [[^field|Scale]], dan [[^field|Rotation]]

### Mengubah Environment

1. Fokuskan Environment yang akan diubah
2. Ubah nilai pada [[#Panel Properti]]

Environment hanya berisi data statis, sehingga perubahan nilai tidak memengaruhi data sumber lain. Environment tidak dapat dipindahkan dengan alat bantu pemindah, ubah [[^field|Position]], [[^field|Rotation]], dan [[^field|Scale]] lewat [[#Panel Properti]].

### Menghapus Environment

1. Klik kanan Environment pada [[#Antarmuka Space|Outliner]]
2. Klik [[^button/delete|Delete]]

>**warning** Benda hilang dari ruang
> Environment yang dihapus tidak lagi tampil di ruang 3D. File 3D yang di-*upload* ikut terhapus.


## Mengelola Object

Object adalah data berlogika yang tampil sebagai objek 3D. Object mengambil datanya dari [[Docs/Tipe Data/Query|Query]] dengan kaidah [[Docs/Tipe Data/Query#Table Output|Table Output]], sehingga yang dirender adalah data riil, bukan hasil kalkulasi. Satu Object dapat menghasilkan banyak objek 3D, sebanyak [[Docs/Tipe Data/Row]] hasil Query.

| Atribut | Tipe Data | Penjelasan |
| --- | --- | --- |
| [[^field|Name]] | [[Docs/Tipe Data/String]] | Nama Object. |
| [[^field|Description]] | [[Docs/Tipe Data/String]] | Keterangan Object. |
| [[^field|Origin]] | [[Docs/Format Data/Complex/3D Vector|3D Vector]] | Titik asal (*anchor*) tempat model setiap Row dirender. Origin tidak memengaruhi Row pada data sumber, dan hanya dapat diubah lewat klik kanan Object pada Outliner ➜ [[^field/edit|Edit]]. |
| [[^field|Model]] | [[Docs/Tipe Data/Model]] | Model yang menjadi wujud dan logika Object, disiapkan di komponen [[Docs/Modul Developer/Model/Apa itu Model|Model]] pada modul Developer. |
| [[^field|Query]] | [[Docs/Tipe Data/Query]] | Pengambil data dengan kaidah Table Output. Tombol [[^button/q]] hanya tersedia di modal Object dan tidak tampil langsung di antarmuka seperti pada [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]]. |

Karena logika Object yang kompleks disiapkan di komponen Model, daftar Key yang dapat diisi mengikuti Model yang dipilih pada [[^field|Model]].

### Mengatur Model Attribute

Ketika [[^field|Query]] sudah diisi, tabel [[^field|Model Attribute]] akan tampil dengan kolom [[^field|Key]], [[^field|Static]], dan [[^field|Value]]. Kolom [[^field|Static]] berisi pilihan radio yang menentukan cara nilai atribut diisi:

| Pilihan | Value yang diisi | Hasil pada objek 3D |
| --- | --- | --- |
| [[^value/radio|static]] | Nilai bebas sesuai kebutuhan. | Seluruh objek 3D yang dirender memiliki nilai atribut yang sama. |
| [[^value/radio|bind]] | Kolom yang tersedia pada [[Docs/Tipe Data/Query|Query]]. | Nilai atribut tiap objek 3D mengikuti [[Docs/Tipe Data/Row]] masing-masing. |

Perlu diketahui bahwa Query dapat memanggil banyak data. Jika atribut bernilai [[^value/radio|static]], semua objek 3D yang dirender akan memiliki nilai atribut yang sama, sedangkan atribut [[^value/radio|bind]] dapat berbeda pada setiap objek 3D.

### Menambahkan Object

1. Buka halaman kerja Space
2. Klik kanan pada [[#Antarmuka Space|Outliner]] ➜ [[^field/add|Add Object]]
3. Isi [[^field|Name]], [[^field|Description]], dan [[^field|Origin]]
4. Pilih [[^field|Model]]
5. Isi [[^field|Query]] dengan klik [[^button/q]]
6. Atur [[^field|Model Attribute]] pada kolom [[^field|Static]] dan [[^field|Value]]

### Mengubah Object

1. Fokuskan Object yang akan diubah
2. Ubah nilai pada [[#Panel Properti]]

Untuk mengubah atribut seperti [[^field|Name]], [[^field|Description]], [[^field|Origin]], [[^field|Model]], atau [[^field|Query]], klik kanan Object pada [[#Antarmuka Space|Outliner]] ➜ [[^field/edit|Edit]]. Isian pada modal Edit sama seperti saat menambahkan Object, dan semua atributnya dapat diubah.

Anda juga dapat memindahkan objek 3D dengan alat bantu pemindah. Jika atributnya di-*bind*, perubahan nilainya memperbarui Row sumber.

Nilai yang diubah pada Object memengaruhi [[Docs/Tipe Data/Row]] sebenarnya pada data sumber, selama [[#Hak Akses Space|hak akses]] mengizinkan.

### Menghapus Object

1. Klik kanan Object pada [[#Antarmuka Space|Outliner]]
2. Klik [[^button/delete|Delete]]

>**warning** Objek 3D hilang dari ruang
> Seluruh objek 3D milik Object tidak lagi tampil di ruang, dan konfigurasi [[^field|Query]] serta [[^field|Model Attribute]] ikut terhapus. [[Docs/Tipe Data/Row]] pada data sumber tidak ikut terhapus.

## Panel Properti

Panel Properti tampil di sisi kanan halaman kerja. Selama belum ada data yang difokuskan, panel menampilkan [[^field|No selection]]. Ketika Anda memfokuskan data, baik dengan klik pada Outliner maupun klik langsung pada view 3D, panel menampilkan propertinya dan nilai tersebut dapat diubah.

Tidak ada tombol penyimpanan: perubahan langsung diterapkan. Pada field teks ada jeda (*debounce*) sekitar 300 ms, sedangkan *toggle* dan pilihan berlaku seketika.

Pengaruh perubahan nilai berbeda untuk tiap jenis data:

| Jenis Data | Sumber nilai | Pengaruh perubahan di panel |
| --- | --- | --- |
| [[#Mengelola Weather|Weather]] | Nilai statis atau [[Docs/Tipe Data/Query#Single Output|Single Output]] (hasil kalkulasi) | Hanya mengubah konfigurasi data di Space, tidak memengaruhi Row pada data sumber. |
| [[#Mengelola Environment|Environment]] | Data statis | Hanya mengubah konfigurasi data di Space, tidak memengaruhi Row pada data sumber. |
| [[#Mengelola Object|Object]] | [[Docs/Tipe Data/Query#Table Output|Table Output]] (data riil) | Memengaruhi [[Docs/Tipe Data/Row]] sebenarnya pada data sumber. |

Pada Object, mengubah atribut menjadi [[^value/radio|static]] berlaku untuk seluruh objek 3D yang dirender. Misalnya atribut `on` pada Model lampu yang diubah menjadi true akan menyalakan semua lampu pada tampilan, sedangkan atribut [[^value/radio|bind]] mengikuti Row masing-masing.

>**warning** Perubahan pada Object mengubah data sumber
> Nilai yang diubah pada Object tersimpan ke data sumber dan terlihat oleh komponen lain yang memakai Row yang sama. Perubahan hanya berhasil bila [[#Hak Akses Space|Data Access]] sumber mengizinkan.

## Hak Akses Space

Space mengikuti pengaturan di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]]:

| Hak Akses | Pengaruh pada Space |
| --- | --- |
| Comp. Access | Mengatur apakah Space terlihat ([[^field|Visible]]), serta dapat diubah ([[^field|Update]]) atau dihapus ([[^field|Delete]]). |
| Data Access | Satu pengaturan [[Docs/Modul Developer/Workspace/Data Access|Data Access]] mewakili ketiga jenis data (Weather, Environment, dan Object) untuk menambah ([[^field|Add]]), mengubah ([[^field|Update]]), dan menghapus ([[^field|Delete]]) data. |
| Data Access sumber | Pada Object, perubahan yang memengaruhi Row sumber hanya berhasil bila Data Access data sumber (misalnya [[Docs/Tipe Data/Table]]) juga mengizinkan. |

## Contoh Penggunaan

**Memantau Kondisi Unit Operasional di Area Gudang secara 3D**

Tim operasional ingin melihat posisi dan kondisi seluruh unit di sebuah area gudang sekaligus, tanpa membaca baris demi baris di tabel. Dengan Space, data unit tampil sebagai objek 3D di dalam denah gudang, sehingga unit yang menumpuk atau bermasalah langsung terlihat dari sudut pandang mana pun.

**Komponen yang terlibat**

| Komponen | Peran |
| --- | --- |
| [[^field/table|Data Unit]] | Menyimpan data setiap unit: identitas, posisi, dan status. |
| [[^field/model|Model Unit]] | Menyiapkan wujud dan logika unit, termasuk daftar Key. |
| [[^field/space|Denah Gudang]] | Menampilkan gedung, suasana, dan unit dalam satu ruang 3D. |
| [[^field/tableview|Daftar Unit]] | Menampilkan data yang sama dalam bentuk tabel untuk dicek bersama. |

**Alur penggunaan**

```mermaid
flowchart LR
  A["Table<br/>Data Unit"] -.->|"&nbsp;Table Output&nbsp;"| B["Space<br/>Object"]
  C["Model<br/>Model Unit"] -->|"&nbsp;Model&nbsp;"| B
  D["File 3D<br/>Gedung"] -->|"&nbsp;Upload&nbsp;"| E["Space<br/>Environment"]
  B --> F["View 3D"]
  E --> F
  B -.->|"&nbsp;Ubah di Panel Properti&nbsp;"| A
```

| Langkah | Komponen | Peran dalam alur | Hasil |
| --- | --- | --- | --- |
| 1 | [[^field/table|Data Unit]] | Menyiapkan data unit sebagai sumber. | Data riil siap dipakai. |
| 2 | [[Docs/Modul Developer/Model/Apa itu Model|Model]] | Menyiapkan wujud unit dan daftar Key. | Object memiliki wujud 3D. |
| 3 | [[#Mengelola Environment|Environment]] | Meng-upload file 3D gedung. | Denah gudang tampil sebagai latar. |
| 4 | [[#Mengelola Object|Object]] | Mengisi [[^field|Query]] dan memilih [[^value/radio|bind]] pada [[^field|Model Attribute]]. | Satu objek 3D tampil untuk setiap unit dengan kondisi masing-masing. |
| 5 | [[#Mengelola Weather|Weather]] | Menambahkan Weather dengan [[^field|Type]] [[^value/radio|Earth Sky]] dan [[^field|Time]] dari [[Docs/Tipe Data/Query#Single Output|Single Output]]. | Suasana langit mengikuti waktu dari data sumber. |
| 6 | [[#Panel Properti]] | Fokus pada satu unit lalu ubah nilainya. | Row unit pada sumber ikut diperbarui. |

**Hasil yang dirasakan**

- Tim melihat sebaran dan kondisi seluruh unit dalam satu pandangan, lalu memutar dan memperbesar tampilan untuk memeriksa area tertentu.
- Perubahan status unit dari [[#Panel Properti]] langsung tersimpan ke data sumber, sehingga [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] yang menampilkan data yang sama ikut menyesuaikan.
- Data yang sama bisa dibaca sebagai tabel maupun sebagai ruang, tergantung kebutuhan.

**Ide skenario lain**

| Jenis nilai | Contoh integrasi |
| --- | --- |
| Lokasi aset | Object menampilkan setiap aset pada denah, dengan posisi dari kolom [[Docs/Tipe Data/Table|Table]] yang di-*bind*. |
| Status mesin | Object menampilkan status tiap mesin pada Model, dengan atribut status di-*bind* ke kolom Query. |
| Kondisi lingkungan | Weather [[^value/radio|Sea]] memakai [[^field|Level]] dan [[^field|Wave Rate]] dari Query Single Output untuk memantau kondisi perairan. |
| Tata ruang | Environment menampilkan bangunan atau perabot statis sebagai latar data yang dipantau. |

Dengan menggabungkan Environment, Object, dan Weather, Space mengubah data tabel menjadi ruang yang dapat dijelajahi dan langsung terhubung dengan sumber datanya.

## Praktik Terbaik

- **Pisahkan benda tetap dan data yang berubah.** Gunakan [[#Mengelola Environment|Environment]] untuk benda statis seperti bangunan, dan [[#Mengelola Object|Object]] untuk data riil yang perlu dipantau.
- **Beri [[^field|Priority]] yang berurutan pada Weather.** Dengan begitu Anda mudah menentukan Weather mana yang berlaku untuk setiap [[^field|Type]], dan mudah menyiapkan cadangan bila [[^field|Status]] diubah menjadi [[^value/boolean/false]].
- **Pilih [[^value/radio|bind]] untuk nilai yang berbeda tiap data** dan [[^value/radio|static]] untuk nilai yang sama bagi semua objek 3D pada [[#Mengatur Model Attribute|Model Attribute]].
- **Siapkan [[Docs/Modul Developer/Model/Apa itu Model|Model]] terlebih dahulu** sebelum membuat Object, karena daftar [[^field|Key]] mengikuti Model yang dipilih.
- **Batasi [[Docs/Modul Developer/Workspace/Data Access|Data Access]]** bagi pengguna yang hanya perlu melihat, agar perubahan di [[#Panel Properti]] tidak mengubah Row sumber secara tidak sengaja.

>**success** Mulai dari yang sederhana
> Mulailah dengan satu [[#Mengelola Environment|Environment]] sebagai latar dan satu [[#Mengelola Object|Object]] dengan [[Docs/Tipe Data/Query|Query]] kecil, lalu tambahkan [[#Mengelola Weather|Weather]] setelah ruang terasa pas.

## Batasan dan Catatan

- [[#Mengelola Weather|Weather]] dengan [[^field|Type]] yang sama hanya diambil satu: [[^field|Status]] [[^value/boolean/true]] dengan [[^field|Priority]] terkecil.
- [[#Mengelola Environment|Environment]] bersifat statis tanpa logika. Untuk logika, gunakan [[#Mengelola Object|Object]] dengan [[Docs/Modul Developer/Model/Apa itu Model|Model]].
- Perubahan di [[#Panel Properti]] hanya memengaruhi Row pada data sumber untuk Object. Weather memakai Query Single Output (hasil kalkulasi) dan Environment berisi data statis.
- Atribut [[^value/radio|static]] bernilai sama untuk seluruh objek 3D, sedangkan [[^value/radio|bind]] mengikuti Row masing-masing.
- Satu pengaturan [[Docs/Modul Developer/Workspace/Data Access|Data Access]] di Workspace mewakili Weather, Environment, dan Object.
- Alat bantu pemindah belum memiliki pergantian mode. [[#Mengelola Environment|Environment]] hanya dapat diubah lewat [[#Panel Properti]], dan [[^field|Origin]] hanya lewat [[^field/edit|Edit]] pada Outliner.
- [[^field|Search Space Data...]] mencari berdasarkan Name data pada Outliner.

## TL:DR

- **Definisi:** Space menaungi dan mengorganisasi data dalam bentuk 3D agar pola dan keterkaitan lebih mudah dipahami.
- **Antarmuka:** halaman kerja berisi view 3D, Outliner di kiri, dan [[#Panel Properti]] di kanan. Putar dengan klik kiri, geser dengan Shift + klik kiri, dan zoom dengan *wheel*.
- **Membangun:** tambahkan [[#Mengelola Weather|Weather]], [[#Mengelola Environment|Environment]], dan [[#Mengelola Object|Object]] lewat klik kanan pada Outliner.
- **Mengisi data:** Weather memakai nilai statis atau Query Single Output, Environment memakai file 3D, dan Object memakai Query Table Output dengan [[#Mengatur Model Attribute|Model Attribute]].
- **Mengubah:** nilai diubah di [[#Panel Properti]], dan hanya perubahan pada Object yang memengaruhi Row sumber sesuai [[#Hak Akses Space|hak akses]].
- **Hati-hati:** menghapus Space atau data menghilangkan konfigurasinya, dan [[^field|Priority]] serta [[^field|Status]] menentukan Weather yang berlaku.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apa perbedaan Environment dan Object?**
> [[#Mengelola Environment|Environment]] adalah benda statis tanpa logika yang dibuat dari file 3D. [[#Mengelola Object|Object]] memiliki logika yang disiapkan di [[Docs/Modul Developer/Model/Apa itu Model|Model]] dan mengambil data riil lewat [[Docs/Tipe Data/Query|Query]] Table Output.
> **Mengapa Weather yang saya tambahkan tidak berlaku?**
> Hanya satu Weather untuk setiap [[^field|Type]] yang berlaku. Pastikan [[^field|Status]] bernilai [[^value/boolean/true]] dan [[^field|Priority]]-nya paling kecil dibanding Weather lain dengan [[^field|Type]] yang sama.
> **Mengapa semua objek 3D pada Object tampil sama?**
> Periksa kolom [[^field|Static]] pada [[#Mengatur Model Attribute|Model Attribute]]. Atribut [[^value/radio|static]] bernilai sama untuk semua objek 3D, pilih [[^value/radio|bind]] agar nilainya mengikuti kolom [[Docs/Tipe Data/Query|Query]].
> **Apakah mengubah nilai di Panel Properti mengubah data sumber?**
> Hanya untuk [[#Mengelola Object|Object]]. Perubahan memengaruhi [[Docs/Tipe Data/Row]] sebenarnya selama [[Docs/Modul Developer/Workspace/Data Access|Data Access]] sumber mengizinkan. Untuk [[#Mengelola Weather|Weather]] dan [[#Mengelola Environment|Environment]], perubahan tidak memengaruhi Row sumber.
> **Mengapa saya tidak bisa menambah atau menghapus data di Outliner?**
> Penambahan dan penghapusan data mengikuti [[Docs/Modul Developer/Workspace/Data Access|Data Access]] Space di Workspace. Hubungi pengelola Workspace Anda untuk memeriksa pengaturannya.
> **Bagaimana cara mencari data di Space?**
> Gunakan [[^field|Search Space Data...]] pada bilah navigasi untuk mencari data di Outliner berdasarkan Name, termasuk data yang jumlahnya banyak pada [[#Mengelola Object|Object]].