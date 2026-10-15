---
  pageDecoration:
    tree:
      priority: 
  tags:
    meta
    prompt
---
# Knowledge: Studi Kasus Sekolah (Phoenix)

File ini punya dua bagian:

1.  **Study Case**: knowledge studi kasus sekolah yang bisa ditempel ke AI Agent agar developer mencoba prompt sendiri.
2.  **Pertanyaan yang Masih Ada**: informasi yang belum ada di knowledge Phoenix. Isi kolom **Jawaban**, lalu tambahkan ke knowledge agar tutorial dapat ditulis akurat.

---

## 1\. Study Case

### Cara Memakai

Tempel bagian "Knowledge Study Case" di bawah ke AI Agent, lalu gunakan salah satu prompt contoh:

*   `Buat halaman studi kasus sekolah dari knowledge ini dalam format Silverbullet.`
*   `Buat tutorial membuat studi kasus sekolah di Phoenix, langkah demi langkah.`
*   `Buat versi ringkas studi kasus ini untuk calon pengguna non-teknis.`
*   `Review studi kasus ini: bagian mana yang berisiko tidak bisa dilakukan di Phoenix?`

Cocokkan hasilnya dengan studi kasus yang sudah disetujui, lalu catat bagian yang meleset sebagai bahan perbaikan knowledge.

### Knowledge Study Case

#### Identitas

*   **Judul:** Satu Tempat untuk Data Akademik Sekolah.
*   **Organisasi:** SMA Nusantara Mandiri. Sekolah ini **fiktif** dan angka-angkanya contoh, dan halaman wajib menyatakannya.
*   **Skala:** 600 siswa, 45 guru, 4 staf tata usaha, 1 kepala sekolah.
*   **Ringkasan:** nilai, kehadiran, kalender, dan pengumuman dipindahkan dari spreadsheet dan kertas ke satu Pro. Setiap peran hanya mengakses komponen yang menjadi bagiannya.
*   **Format halaman:** alur cerita studi kasus (bukan halaman konsep): Gambaran Singkat, Latar Belakang, Tujuan, Rancangan Solusi, Skenario Penggunaan, Sebelum dan Sesudah, Praktik Terbaik, Batasan dan Catatan, Mulai dari Mana, TL;DR.

#### Masalah

*   **Data ganda:** satu siswa tercatat di banyak file dengan penulisan nama berbeda.
*   **Akses tidak terkendali:** file nilai dibagikan lewat grup pesan dan dapat diubah siapa pun.
*   **Tindak lanjut terlambat:** siswa yang perlu remedial baru diketahui saat rapor hampir selesai.

#### Tujuan

1.  Seluruh data akademik berada di satu tempat dan dapat dicari.
2.  Setiap peran hanya mengakses komponen yang relevan.
3.  Siswa dengan nilai di bawah batas tuntas tercatat untuk tindak lanjut tanpa rekap manual.
4.  Pengumuman dibagikan lewat tautan tanpa membuka data lain.

#### Komponen Phoenix yang Dipakai

*   Workspace (satu Workspace bernama **Akademik**).
*   Group (empat peran).
*   Table View (Data Siswa, Kehadiran, Nilai, Pengumuman).
*   Timeline (Kalender Akademik).
*   Flow (Tindak Lanjut Nilai).
*   Publish (tabel Pengumuman).
*   Folder dan Pro sebagai wadah.

#### Struktur Folder

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

*   Folder dikelompokkan menurut **fungsi**, bukan nama guru atau kelas.
*   Izin diberikan per folder. Folder yang tidak boleh dilihat sebuah Group diberi `disallow` pada **Visible**.

#### Group dan Tanggung Jawab

| Group | Tanggung jawab |
| --- | --- |
| Tata Usaha | Mengelola Data Siswa dan Pengumuman |
| Guru Mata Pelajaran | Mengisi Nilai |
| Wali Kelas | Mengisi Kehadiran dan memantau Nilai kelasnya |
| Kepala Sekolah | Membaca seluruh data dan memantau Flow |

Semua Group dipetakan ke Workspace **Akademik**.

#### Matriks Akses (usulan)

| Komponen | Tata Usaha | Guru Mata Pelajaran | Wali Kelas | Kepala Sekolah |
| --- | --- | --- | --- | --- |
| Data Siswa | Visible, Add, Update, Delete | Visible | Visible | Visible |
| Kehadiran | Visible | disallow | Visible, Add, Update | Visible |
| Nilai | Visible | Visible, Add, Update | Visible | Visible |
| Kalender Akademik | Visible, Add, Update, Delete | Visible | Visible | Visible |
| Tindak Lanjut Nilai | disallow | disallow | Visible | Visible, Modify Event |
| Pengumuman | Visible, Add, Update, Publish | Visible | Visible | Visible, View Publish |

*   Nilai Comp. Access, Data Access, dan Function Access mengikuti knowledge Workspace.
*   Matriks adalah **usulan awal**, bukan aturan baku Phoenix.

#### Data per Komponen

| Komponen | Isi utama |
| --- | --- |
| Data Siswa | NIS, nama, kelas, nama wali |
| Kehadiran | Tanggal, siswa, status (hadir, izin, sakit, alpa) |
| Nilai | Siswa, mata pelajaran, jenis penilaian, skor |
| Kalender Akademik | Awal semester, ujian, libur, pembagian rapor |
| Pengumuman | Judul, isi, tanggal terbit |

#### Flow: Tindak Lanjut Nilai

1.  Sebuah Flow Block Event terpicu saat baris baru ditambahkan di tabel Nilai.
2.  Alur memeriksa apakah skor di bawah batas tuntas mata pelajaran.
3.  Jika ya, alur menambahkan catatan ke daftar tindak lanjut yang dipantau wali kelas.

*   Proses dipantau di Flow Activity.
*   **Status:** konsep. Belum dipastikan apakah Event dan Flow Block yang diperlukan tersedia (lihat Pertanyaan 5 dan 6).

#### Publish

*   Tata Usaha mem-publish tabel Pengumuman dan menyalin *publish link* untuk orang tua.
*   Konfigurasi publikasi berlaku untuk komponen tersebut saja, sehingga komponen lain tidak ikut terbuka.

#### Skenario

*   **Awal semester:** Tata Usaha mengisi Data Siswa dan Kalender Akademik.
*   **Selama semester:** Wali Kelas mengisi Kehadiran, Guru Mata Pelajaran mengisi Nilai, dan setiap skor baru memicu Flow.
*   **Menjelang rapor:** Kepala Sekolah membuka Nilai dan Kehadiran langsung dari Workspace, dan siswa remedial sudah tercatat.

#### Sebelum dan Sesudah

| Aspek | Sebelum | Sesudah |
| --- | --- | --- |
| Lokasi data | Belasan file terpisah | Satu Pro |
| Siapa bisa mengubah nilai | Siapa pun yang menerima file | Hanya Group yang diberi `allow` |
| Rekap kepala sekolah | Digabung manual | Dibuka langsung dari Workspace |
| Deteksi siswa remedial | Saat menyusun rapor | Saat skor dimasukkan |
| Berbagi pengumuman | Disalin ke grup pesan | Satu tautan Publish |

#### Praktik Terbaik

*   Mulai dari peran, bukan dari data.
*   Pisahkan folder menurut fungsi.
*   Beri **Visible** saja bila peran hanya perlu membaca.
*   Batasi **Publish** untuk satu Group.
*   Uji Flow dengan satu baris contoh sebelum dipakai seluruh guru.

#### Batasan dan Catatan

*   Akses Workspace diatur per komponen. Untuk membatasi guru ke nilai kelasnya, pisahkan tabel Nilai per kelas atau jenjang.
*   Menghapus Flow dapat menghilangkan Flow Block dan riwayat Activity.
*   Setiap Group harus tetap memiliki minimal satu Workspace agar anggotanya bisa membuka Phoenix.

#### Urutan Pembuatan (garis besar)

1.  Buat Pro dan folder Akademik.
2.  Buat Workspace dan Group sesuai tabel peran.
3.  Buat tabel Data Siswa dan isi baris contoh.
4.  Atur matriks akses pada halaman kerja Workspace.
5.  Tambahkan Nilai dan Flow Tindak Lanjut Nilai setelah alur dasar berjalan.

#### Path Wikilink (tebakan)

Path berikut mengikuti pola yang ada dan **belum dikonfirmasi**:

*   `Docs/Modul Developer/Workspace/Apa itu Workspace`
*   `Docs/Modul Developer/Group/Apa itu Group`
*   `Docs/Modul Data/Table View/Apa itu Table View`
*   `Docs/Modul Data/Timeline/Apa itu Timeline`
*   `Docs/Publish/Pengenalan`
*   `Docs/Folder/Pengenalan`
*   `Docs/Pro/Pengenalan`

Path yang sudah ada di knowledge:

*   `Docs/Modul Logic/Flow/Apa itu Flow`
*   `Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan`
*   `Docs/Modul Logic/Flow/Flow Activity`
*   `Docs/Event/Menghubungkan Event`

---

## 2\. Pertanyaan yang Masih Ada

Informasi ini belum ada di knowledge Phoenix dan dibutuhkan untuk menulis tutorial yang akurat. Isi kolom **Jawaban** dengan nama menu, tombol, dan field persis seperti di aplikasi.

| No  | Topik | Pertanyaan | Jawaban |
| --- | --- | --- | --- |
| 1   | Group dan pengguna | Bagaimana cara membuat Group dan pengguna, lalu memetakannya ke Workspace? Menu apa yang dipakai dan field apa saja yang diisi? |     |
| 2   | Table View: kolom | Bagaimana cara menambah kolom? Tipe data apa saja yang tersedia (tanggal, angka, pilihan, teks, relasi ke tabel lain)? |     |
| 3   | Table View: baris | Bagaimana cara menambah, mengubah, dan mengimpor baris (misalnya data siswa dari spreadsheet)? |     |
| 4   | Table View: pilihan | Bagaimana cara membuat kolom status dengan pilihan tetap (hadir, izin, sakit, alpa)? |     |
| 5   | Event Table View | Event apa dari Table View yang terpicu saat baris baru ditambahkan, dan bagaimana menghubungkannya ke Flow? |     |
| 6   | Flow Block | Flow Block apa yang dipakai untuk membandingkan skor dengan batas tuntas dan untuk menambah catatan ke tabel lain? Apakah ada Flow Block lain yang relevan? |     |
| 7   | Timeline | Bagaimana cara membuat Timeline dan menambah satu kegiatan, misalnya "Pembagian rapor"? Apa saja field-nya? |     |
| 8   | Publish | Menu atau tombol apa yang mengaktifkan publikasi dan menyalin *publish link*? Apa bedanya **View Publish** dan **Publish** pada tampilan sebenarnya? |     |
| 9   | Pro | Apakah tutorial dimulai dari Pro yang sudah ada, atau perlu langkah membuat Pro? Jika perlu, bagaimana caranya? |     |
| 10  | Relasi antar tabel | Bagaimana cara menghubungkan Nilai dan Kehadiran ke Data Siswa agar nama siswa tidak diketik berulang? |     |
| 11  | Akses per baris | Apakah Phoenix dapat membatasi data per baris atau per kelas? Jika tidak, apakah memisahkan tabel per kelas adalah cara yang disarankan? |     |
| 12  | Hak akses | Apakah matriks akses pada studi kasus sudah sesuai, terutama Data Access dan Function Access per Group? |     |
| 13  | Path wikilink | Apakah path pada bagian "Path Wikilink (tebakan)" benar? Jika tidak, mohon path yang sesuai. |     |
| 14  | Tangkapan layar | Layar mana yang perlu disertakan pada tutorial (Workspace, halaman kerja akses, Blueprint, Table View)? |     |

### Setelah Pertanyaan Terjawab

1.  Tambahkan jawaban sebagai bagian baru di knowledge Phoenix (per modul: Group, Table View, Timeline, Publish, dan lainnya).
2.  Ubah status "konsep" pada bagian Flow di atas menjadi langkah pasti.
3.  Minta AI Agent menulis tutorial dengan prompt: `Buat tutorial membuat studi kasus sekolah di Phoenix, langkah demi langkah, dari knowledge ini.`