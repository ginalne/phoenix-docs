---
  pageDecoration:
    tree:
      priority: 
  tags:
    meta
    prompt
---
# Studi Kasus: Satu Tempat untuk Data Akademik Sekolah

> **Ringkasan.** Sekolah menengah dengan 600 siswa memindahkan nilai, kehadiran, kalender, dan pengumuman dari spreadsheet dan kertas ke satu Pro di Phoenix. Setiap guru, wali kelas, tata usaha, dan kepala sekolah hanya melihat dan mengubah data yang menjadi bagiannya.

> Sekolah dalam studi kasus ini fiktif dan dibuat sebagai ilustrasi. Angka-angka adalah contoh, bukan hasil pengukuran.

## Gambaran Singkat

| | |
|---|---|
| **Organisasi** | SMA Nusantara Mandiri (fiktif) |
| **Skala** | 600 siswa, 45 guru, 4 staf tata usaha, 1 kepala sekolah |
| **Masalah utama** | Data tersebar di banyak file dan tidak ada kontrol akses |
| **Komponen yang dipakai** | [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]], [[Docs/Modul Developer/Group/Apa itu Group|Group]], [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]], [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]], [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]], [[Docs/Publish/Pengenalan|Publish]] |
| **Hasil yang dituju** | Satu sumber data, akses sesuai peran, pengingat berjalan otomatis |

## Latar Belakang

Setiap awal semester, guru mata pelajaran membuat spreadsheet nilai sendiri. Wali kelas mencatat kehadiran di buku, lalu tata usaha mengetik ulang ke file lain. Menjelang rapor, kepala sekolah meminta rekap, dan staf menggabungkan belasan file secara manual.

Tiga hal membuat situasi ini sulit dibiarkan:

- **Data ganda.** Satu siswa tercatat di banyak file dengan penulisan nama yang berbeda.
- **Akses tidak terkendali.** File nilai dibagikan lewat grup pesan, sehingga siapa pun yang menerimanya bisa mengubah isinya.
- **Tindak lanjut terlambat.** Siswa yang perlu remedial baru diketahui setelah rapor hampir selesai.

## Tujuan

1. Seluruh data akademik berada di satu tempat dan dapat dicari.
2. Setiap peran hanya mengakses komponen yang relevan.
3. Siswa yang nilainya di bawah batas tuntas tercatat untuk tindak lanjut tanpa menunggu rekap manual.
4. Pengumuman sekolah dapat dibagikan lewat tautan tanpa membuka data lain.

## Rancangan Solusi

### Struktur Folder

Seluruh komponen ditempatkan dalam satu rangkaian [[Docs/Folder/Pengenalan|Folder]] di bawah Origin, dikelompokkan menurut fungsi, bukan menurut nama guru atau kelas.

```
Origin
├── Akademik
│   ├── Data Siswa          (Table View)
│   ├── Kehadiran           (Table View)
│   ├── Nilai               (Table View)
│   └── Kalender Akademik   (Timeline)
├── Otomasi
│   └── Tindak Lanjut Nilai (Flow)
└── Informasi
    └── Pengumuman          (Table View, dipublikasikan)
```

Pola ini memudahkan pengaturan akses: izin diberikan per folder, dan folder yang tidak boleh dilihat sebuah Group cukup diberi `disallow` pada **Visible**.

### Peran dan Group

Setiap peran dibuat sebagai [[Docs/Modul Developer/Group/Apa itu Group|Group]], lalu dipetakan ke satu [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] bernama **Akademik**.

| Group | Tanggung jawab di Phoenix |
|---|---|
| Tata Usaha | Mengelola Data Siswa dan Pengumuman |
| Guru Mata Pelajaran | Mengisi Nilai |
| Wali Kelas | Mengisi Kehadiran dan memantau Nilai kelasnya |
| Kepala Sekolah | Membaca seluruh data dan memantau Flow |

### Matriks Akses

Matriks berikut adalah titik awal. Nilai `allow` dan `disallow` diatur pada halaman kerja Workspace, di kolom **Comp. Access**, **Data Access**, dan **Function Access**.

| Komponen | Tata Usaha | Guru Mata Pelajaran | Wali Kelas | Kepala Sekolah |
|---|---|---|---|---|
| Data Siswa | Visible, Add, Update, Delete | Visible | Visible | Visible |
| Kehadiran | Visible | disallow | Visible, Add, Update | Visible |
| Nilai | Visible | Visible, Add, Update | Visible | Visible |
| Kalender Akademik | Visible, Add, Update, Delete | Visible | Visible | Visible |
| Tindak Lanjut Nilai | disallow | disallow | Visible | Visible, Modify Event |
| Pengumuman | Visible, Add, Update, Publish | Visible | Visible | Visible, View Publish |

Pengaturan **Visible** pada folder induk berlaku untuk seluruh isinya, jadi rancang `disallow` dari folder terlebih dahulu sebelum menyetel komponen satu per satu.

### Data yang Disimpan

| Komponen | Isi utama |
|---|---|
| Data Siswa | NIS, nama, kelas, nama wali |
| Kehadiran | Tanggal, siswa, status (hadir, izin, sakit, alpa) |
| Nilai | Siswa, mata pelajaran, jenis penilaian, skor |
| Kalender Akademik | Awal semester, ujian, libur, pembagian rapor |
| Pengumuman | Judul, isi, tanggal terbit |

Selengkapnya tentang membuat tabel dan menentukan tipe kolom lihat [[Docs/Modul Data/Table View/Apa itu Table View|Table View]].

### Otomasi dengan Flow

[[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] **Tindak Lanjut Nilai** menyusun alur komposit pada Blueprint:

1. Sebuah [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] terpicu saat baris baru ditambahkan di tabel Nilai.
2. Alur memeriksa apakah skor berada di bawah batas tuntas mata pelajaran.
3. Jika ya, alur menambahkan catatan ke daftar tindak lanjut yang dipantau wali kelas.

Pantau jalannya proses pada [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]. Cara menghubungkan Event dari tabel ke Flow dijelaskan di [[Docs/Event/Menghubungkan Event]].

### Berbagi Pengumuman

Tata Usaha memakai [[Docs/Publish/Pengenalan|Publish]] pada tabel **Pengumuman**, lalu menyalin *publish link* untuk dibagikan ke orang tua. Komponen lain tidak ikut terbuka karena konfigurasi publikasi berlaku untuk komponen tersebut saja.

## Skenario Penggunaan

### Awal Semester

Tata Usaha mengisi **Data Siswa** dan menambahkan jadwal ujian serta libur di **Kalender Akademik**. Karena Guru dan Wali Kelas hanya memiliki akses **Visible**, data induk tidak berubah tanpa sepengetahuan Tata Usaha.

### Selama Semester

Wali Kelas mengisi **Kehadiran** setiap pagi. Guru Mata Pelajaran menambahkan skor di **Nilai** setelah tiap penilaian. Setiap skor baru memicu Flow **Tindak Lanjut Nilai**.

### Menjelang Rapor

Kepala Sekolah membuka **Nilai** dan **Kehadiran** langsung dari Workspace, tanpa menunggu rekap. Siswa yang perlu remedial sudah tercatat sejak skor pertama masuk.

## Sebelum dan Sesudah

| Aspek | Sebelum | Sesudah |
|---|---|---|
| Lokasi data | Belasan file terpisah | Satu Pro |
| Siapa bisa mengubah nilai | Siapa pun yang menerima file | Hanya Group yang diberi `allow` |
| Rekap untuk kepala sekolah | Digabung manual | Dibuka langsung dari Workspace |
| Deteksi siswa remedial | Saat menyusun rapor | Saat skor dimasukkan |
| Berbagi pengumuman | Disalin ke grup pesan | Satu tautan Publish |

## Praktik Terbaik

- Mulai dari **peran**, bukan dari data. Daftarkan siapa mengisi apa, baru buat [[Docs/Modul Developer/Group/Apa itu Group|Group]].
- Pisahkan folder menurut fungsi agar aturan [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mudah dibaca.
- Berikan **Visible** saja bila sebuah peran hanya perlu membaca.
- Batasi **Publish** hanya untuk satu Group.
- Uji Flow dengan satu baris contoh sebelum dipakai seluruh guru.

## Batasan dan Catatan

- Akses di Workspace diatur per komponen. Bila guru hanya boleh melihat nilai kelasnya sendiri, pisahkan tabel Nilai per kelas atau per jenjang.
- Hapus komponen dengan hati-hati. Menghapus Flow dapat menghilangkan Flow Block dan riwayat Activity.
- Pastikan setiap Group tetap memiliki minimal satu Workspace agar anggotanya bisa membuka Phoenix.

## Mulai dari Mana

1. Buat [[Docs/Pro/Pengenalan|Pro]] dan folder **Akademik**.
2. Buat Workspace dan Group sesuai tabel peran.
3. Buat tabel **Data Siswa**, lalu isi beberapa baris contoh.
4. Atur matriks akses pada halaman kerja Workspace.
5. Tambahkan **Nilai** dan Flow **Tindak Lanjut Nilai** setelah alur dasar berjalan.

## TL;DR

Satu [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] dengan empat [[Docs/Modul Developer/Group/Apa itu Group|Group]] menjaga akses sesuai peran. [[Docs/Modul Data/Table View/Apa itu Table View|Table View]] dan [[Docs/Modul Data/Timeline/Apa itu Timeline|Timeline]] menyimpan data akademik. [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] menandai siswa yang perlu tindak lanjut, dan [[Docs/Publish/Pengenalan|Publish]] membagikan pengumuman lewat tautan.

* [ ] TODO (konsolidasi): Path wikilink untuk Workspace, Group, Table View, Timeline, Publish, Folder, dan Pro adalah tebakan mengikuti pola yang ada. Mohon dicek dan disesuaikan.
* [ ] TODO: Pastikan Flow dapat dipicu oleh penambahan baris pada Table View dan dapat memeriksa kondisi skor. Penjelasan Flow di atas masih tingkat konsep.
* [ ] TODO: Pastikan kebutuhan pembatasan data per kelas. Matriks akses diasumsikan per komponen.
* [ ] TODO: Matriks akses (Data Access dan Function Access) diasumsikan. Cek nilai per Group.
* [ ] TODO: Tambahkan tangkapan layar Workspace, folder, dan Blueprint jika tersedia.