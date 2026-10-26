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
        priority: 10
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
4. [[#Mengelola Data]] Space seperti menambahkan, mengubah atau memperbarui Data.

## Antarmuka

Penjelasan antarmuka lihat selengkapnya di [[Docs/Modul Interface/Space/Antarmuka|Antarmuka Space]].

## Mengelola Data

Space dapat didesain dan disesuaikan sesuai kebutuhan agar membuat tampilan 3D menjadi lebih interaktif, penyusun utama dalam Space adalah:

1. [[Docs/Modul Interface/Space/Weather/Pengenalan|Weather]]
2. [[Docs/Modul Interface/Space/Environment/Pengenalan|Environment]]
3. [[Docs/Modul Interface/Space/Object/Pengenalan|Object]]

## Hak Akses

Penjelasan tentang pengelolaan Hak Akses dalam komponen Space lihat selengkapnya di [[Docs/Modul Interface/Space/Hak Akses]].

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