---
    status: release
    title: "Apa itu Space?"
    description: Space adalah komponen untuk menaungi dan mengorganisasi data dalam bentuk 3D (tiga dimensi) sehingga data dan hubungan antar data dapat dijelajahi dari berbagai sudut pandang.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" height="20" width="20" fill="#aaa" viewBox="0 -960 960 960">
    <path d="M312-96q-33 0-52.5-19.5T240-168v-480q0-33 19.5-52.5T312-720h480q33 0 52.5 19.5T864-648v480q0 33-19.5 52.5T792-96H312Zm0-72h204v-132H312v132Zm276 0h204v-132H588v132ZM96-240v-552.45q0-32.55 19.5-52.05t52.05-19.5H720v72H168v552H96Zm216-132h204v-132H312v132Zm276 0h204v-132H588v132ZM312-576h480v-72H312v72Z"/>
  </svg>
  '
      tree:
        priority: 4
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

## Cara Kerja

Penjelasan cara kerja Space lihat selengkap nya di [[Docs/Modul Interface/Space/Cara Kerja|Cara Kerja Space]].

## Mengelola Space

Berikut adalah halaman yang menjelaskan cara untuk mengelola Space:

1. [[Docs/Modul Interface/Space/Membuat Baru]] Space dalam halaman kerja.
2. [[Docs/Modul Interface/Space/Mengubah]] Atribut Space seperti [[^field|Name]], [[^field|Description]], atau [[^field|Table - Column]].
3. [[Docs/Modul Interface/Space/Menghapus]] Space.
4. [[Docs/Modul Interface/Space/Space Data|Mengelola Data]] Space seperti menambahkan, mengubah atau memperbarui Data.

## Antarmuka

Penjelasan antarmuka lihat selengkapnya di [[Docs/Modul Interface/Space/Antarmuka|Antarmuka Space]].

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
| [[^field|Query]] | [[Docs/Tipe Data/Query]] | Pengambil data dengan kaidah Table Output. Tombol [[^button/q]] hanya tersedia di modal Object dan tidak tampil langsung di antarmuka seperti pada [[Docs/Modul Interface/Space/Apa itu Space|Space]]. |

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

## Praktik Terbaik

- **Pisahkan benda tetap dan data yang berubah.** Gunakan [[#Mengelola Environment|Environment]] untuk benda statis seperti bangunan, dan [[#Mengelola Object|Object]] untuk data riil yang perlu dipantau.
- **Beri [[^field|Priority]] yang berurutan pada Weather.** Dengan begitu Anda mudah menentukan Weather mana yang berlaku untuk setiap [[^field|Type]], dan mudah menyiapkan cadangan bila [[^field|Status]] diubah menjadi [[^value/boolean/false]].
- **Pilih [[^value/radio|bind]] untuk nilai yang berbeda tiap data** dan [[^value/radio|static]] untuk nilai yang sama bagi semua objek 3D pada [[#Mengatur Model Attribute|Model Attribute]].
- **Siapkan [[Docs/Modul Developer/Model/Apa itu Model|Model]] terlebih dahulu** sebelum membuat Object, karena daftar [[^field|Key]] mengikuti Model yang dipilih.
- **Batasi [[Docs/Modul Developer/Workspace/Data Access|Data Access]]** bagi pengguna yang hanya perlu melihat, agar perubahan di [[#Panel Properti]] tidak mengubah Row sumber secara tidak sengaja.
* **Mulai dari yang sederhana** dengan satu [[#Mengelola Environment|Environment]] sebagai latar dan satu [[#Mengelola Object|Object]] dengan [[Docs/Tipe Data/Query|Query]] kecil, lalu tambahkan [[#Mengelola Weather|Weather]] setelah ruang terasa pas.

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