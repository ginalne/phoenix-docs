---
  pageDecoration:
    tree:
      priority: 
  tags:
    meta
    prompt
---
# Tutorial: Membuat Sistem Data Akademik Sekolah

Tutorial ini membawa Anda membangun [[Example/Studi Kasus/Sekolah|studi kasus sekolah]] di Phoenix dari nol sampai bisa dipakai. Di akhir, Anda memiliki satu Pro dengan data siswa, kehadiran, nilai, kalender, pengumuman, akses sesuai peran, dan otomasi yang mencatat siswa yang perlu remedial.

> Sekolah dan datanya fiktif. Semua nama dan angka pada tutorial ini adalah contoh.

## Sebelum Mulai

- Anda memiliki akses untuk menambah komponen pada [[Docs/Pro/Pengenalan|Pro]] Anda.
- Anda memahami dasar [[Docs/Folder/Pengenalan|Folder]] dan Area Manajemen Folder.
- Waktu pengerjaan: sekitar 45 menit.

## Hasil Akhir

```
Origin
├── Akademik
│   ├── Data Siswa          (Table View)
│   ├── Kehadiran           (Table View)
│   ├── Nilai               (Table View)
│   └── Kalender Akademik   (Timeline)
├── Otomasi
│   ├── Daftar Remedial     (Table View)
│   └── Tindak Lanjut Nilai (Flow)
└── Informasi
    └── Pengumuman          (Table View, dipublikasikan)
```

## Alur Pengerjaan

| Tahap | Langkah | Hasil |
|---|---|---|
| Fondasi | 1 | Folder siap |
| Data | 2 sampai 7 | Tabel dan Timeline terisi |
| Akses | 8 sampai 9 | Group dan Workspace berjalan |
| Otomasi | 10 | Flow mencatat siswa remedial |
| Berbagi | 11 | Pengumuman dapat dibuka lewat tautan |
| Uji | 12 | Setiap peran diuji |

Kerjakan berurutan. Data dibuat lebih dulu karena Workspace dan Flow membutuhkan komponen yang sudah ada.

---

## Langkah 1: Siapkan Folder

1. Buka [[Docs/Folder/Pengenalan|Area Manajemen Folder]] pada Pro Anda.
2. Klik kanan **Origin**, lalu pilih **Add > Folder**.
3. Isi **Name** dengan `Akademik`, lalu klik **Create**.
4. Ulangi untuk folder `Otomasi` dan `Informasi`.

> **Tips.** Beri nama folder menurut fungsi, bukan menurut guru atau kelas, agar pengaturan akses nanti lebih sederhana.

## Langkah 2: Buat Tabel Data Siswa

1. Klik kanan folder **Akademik**, lalu pilih **Add > Data > Table View**.
2. Isi **Name** dengan `Data Siswa` dan **Description** dengan `Data induk siswa`, lalu klik **Create**.
3. Buka tabel, lalu tambahkan kolom berikut. Cara menambah kolom dan daftar tipe data ada di [[Docs/Modul Data/Table View/Menambahkan Kolom|Menambahkan Kolom]].

| Kolom | Tipe | Keterangan |
|---|---|---|
| NIS | Teks | Nomor induk siswa, unik |
| Nama | Teks | Nama lengkap |
| Kelas | Pilihan | `X-1`, `X-2`, `XI-1`, dan seterusnya |
| Nama Wali | Teks | Orang tua atau wali |

4. Tambahkan tiga baris contoh, misalnya `1001 | Alya Putri | X-1 | Bapak Rudi`.

> **Tips.** Untuk data siswa yang sudah ada di spreadsheet, gunakan [[Docs/Modul Data/Table View/Mengimpor Data|impor data]] agar tidak mengetik ulang.

## Langkah 3: Buat Tabel Kehadiran

1. Klik kanan folder **Akademik**, lalu pilih **Add > Data > Table View**.
2. Isi **Name** dengan `Kehadiran`, lalu klik **Create**.
3. Tambahkan kolom:

| Kolom | Tipe | Keterangan |
|---|---|---|
| Tanggal | Tanggal | Tanggal pertemuan |
| Siswa | Relasi ke **Data Siswa** | Memilih siswa tanpa mengetik nama |
| Status | Pilihan | `Hadir`, `Izin`, `Sakit`, `Alpa` |

Kolom **Siswa** bertipe relasi agar nama siswa selalu konsisten dan tidak ganda. Selengkapnya lihat [[Docs/Modul Data/Table View/Relasi Antar Tabel|Relasi Antar Tabel]].

## Langkah 4: Buat Tabel Nilai

1. Klik kanan folder **Akademik**, lalu pilih **Add > Data > Table View**.
2. Isi **Name** dengan `Nilai`, lalu klik **Create**.
3. Tambahkan kolom:

| Kolom | Tipe | Keterangan |
|---|---|---|
| Siswa | Relasi ke **Data Siswa** | |
| Mata Pelajaran | Pilihan | `Matematika`, `Bahasa Indonesia`, dan seterusnya |
| Jenis Penilaian | Pilihan | `Harian`, `UTS`, `UAS` |
| Skor | Angka | 0 sampai 100 |
| Batas Tuntas | Angka | Isi default `75` |

Kolom **Batas Tuntas** disimpan di setiap baris agar Flow pada Langkah 10 dapat membandingkan **Skor** tanpa konfigurasi tambahan.

## Langkah 5: Buat Daftar Remedial

Tabel ini diisi otomatis oleh Flow dan dipantau Wali Kelas.

1. Klik kanan folder **Otomasi**, lalu pilih **Add > Data > Table View**.
2. Isi **Name** dengan `Daftar Remedial`, lalu klik **Create**.
3. Tambahkan kolom:

| Kolom | Tipe | Keterangan |
|---|---|---|
| Siswa | Relasi ke **Data Siswa** | |
| Mata Pelajaran | Teks | Disalin dari tabel **Nilai** |
| Skor | Angka | Disalin dari tabel **Nilai** |
| Status | Pilihan | `Menunggu`, `Dalam Proses`, `Selesai` |

## Langkah 6: Buat Kalender Akademik

1. Klik kanan folder **Akademik**, lalu pilih **Add > Data > Timeline**.
2. Isi **Name** dengan `Kalender Akademik`, lalu klik **Create**.
3. Tambahkan satu kegiatan, misalnya:

| Field | Isi |
|---|---|
| Name | Pembagian Rapor |
| Mulai | 19 Desember |
| Selesai | 19 Desember |

4. Tambahkan kegiatan lain: awal semester, ujian, dan libur. Selengkapnya lihat [[Docs/Modul Data/Timeline/Apa itu Timeline|Timeline]].

## Langkah 7: Buat Tabel Pengumuman

1. Klik kanan folder **Informasi**, lalu pilih **Add > Data > Table View**.
2. Isi **Name** dengan `Pengumuman`, lalu klik **Create**.
3. Tambahkan kolom:

| Kolom | Tipe |
|---|---|
| Judul | Teks |
| Isi | Teks panjang |
| Tanggal Terbit | Tanggal |

4. Tambahkan satu pengumuman contoh.

## Langkah 8: Buat Group dan Pengguna

Anda membuat satu [[Docs/Modul Developer/Group/Apa itu Group|Group]] untuk setiap peran.

1. Buka halaman pengelolaan Group, lalu klik **Add**.
2. Buat empat Group: `Tata Usaha`, `Guru Mata Pelajaran`, `Wali Kelas`, dan `Kepala Sekolah`.
3. Tambahkan pengguna ke masing-masing Group. Cara membuat pengguna ada di [[Docs/Modul Developer/Group/Menambahkan Pengguna|Menambahkan Pengguna]].

## Langkah 9: Buat Workspace dan Atur Akses

1. Klik kanan **Origin**, lalu pilih **Add > Developer > Workspace**.
2. Isi **Name** dengan `Akademik` dan **Description** dengan `Ruang kerja data akademik`, lalu klik **Create**.
3. Buka [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] tersebut. Pada halaman kerja, baris **Group** menampilkan setiap Group yang sudah dipetakan, sedangkan kolom kanan berisi **Comp. Access**, **Data Access**, dan **Function Access**.
4. Atur nilai `allow` dan `disallow` untuk setiap Group sesuai matriks berikut. Sel kosong berarti akses itu tidak relevan.

| Komponen | Tata Usaha | Guru Mata Pelajaran | Wali Kelas | Kepala Sekolah |
|---|---|---|---|---|
| Data Siswa | Visible, Add, Update, Delete | Visible | Visible | Visible |
| Kehadiran | Visible | `disallow` | Visible, Add, Update | Visible |
| Nilai | Visible | Visible, Add, Update | Visible | Visible |
| Kalender Akademik | Visible, Add, Update, Delete | Visible | Visible | Visible |
| Daftar Remedial | `disallow` | `disallow` | Visible, Update | Visible |
| Tindak Lanjut Nilai | `disallow` | `disallow` | Visible | Visible, Modify Event |
| Pengumuman | Visible, Add, Update, Publish | Visible | Visible | Visible, View Publish |

> **Penting.** Jika sebuah folder bernilai `disallow` pada **Visible**, seluruh isinya tidak dapat diakses meski komponen di dalamnya bernilai `allow`. Atur folder lebih dulu, lalu komponen.

Matriks ini mengatur akses per komponen. Untuk membatasi guru ke nilai kelasnya sendiri, pisahkan tabel **Nilai** per kelas atau jenjang.

## Langkah 10: Bangun Flow Tindak Lanjut Nilai

### Buat Flow

1. Klik kanan folder **Otomasi**, lalu pilih **Add > Logic > Flow**.
2. Isi **Name** dengan `Tindak Lanjut Nilai` dan **Description** dengan `Mencatat siswa di bawah batas tuntas`, lalu klik **Create**.

### Susun Blueprint

Buka Flow. Pada Blueprint, klik kanan di bagian kosong untuk membuka menu **Add**, lalu susun tiga blok berikut.

| Urutan | Kategori | Fungsi |
|---|---|---|
| 1 | Event | Terpicu saat baris baru ditambahkan di tabel **Nilai** |
| 2 | Operator | Memeriksa apakah **Skor** lebih kecil dari **Batas Tuntas** |
| 3 | Data | Menambahkan baris ke tabel **Daftar Remedial** |

1. Tambahkan [[Docs/Modul Logic/Flow/Flow Block/Event/Pengenalan|Flow Block Event]] dan pilih tabel **Nilai** sebagai sumbernya.
2. Tambahkan blok Operator perbandingan. Hubungkan keluaran Event ke masukan blok ini, lalu atur kondisi **Skor** < **Batas Tuntas**.
3. Tambahkan blok Data untuk menambah baris. Hubungkan ke keluaran Operator saat kondisi benar, lalu petakan kolom **Siswa**, **Mata Pelajaran**, dan **Skor** ke tabel **Daftar Remedial**. Isi **Status** dengan `Menunggu`.

Cara menambah, menghubungkan, dan mengonfigurasi blok ada di [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menambahkan Flow Block|Menambahkan Flow Block]] dan [[Docs/Modul Logic/Flow/Flow Block/Pengenalan#Menghubungkan Koneksi|Menghubungkan Koneksi]].

### Hubungkan Event dari Tabel

Hubungkan Event penambahan baris pada tabel **Nilai** ke Flow ini. Langkahnya ada di [[Docs/Event/Menghubungkan Event]].

## Langkah 11: Publikasikan Pengumuman

1. Buka tabel **Pengumuman**.
2. Aktifkan publikasi lewat [[Docs/Publish/Pengenalan|Publish]].
3. Salin *Publish Link*, lalu bagikan ke orang tua.

Hanya Group dengan **Publish** `allow` yang dapat mengubah konfigurasi ini. Group dengan **View Publish** hanya dapat melihat dan menyalin tautan.

## Langkah 12: Uji Coba

Masuk dengan satu pengguna dari setiap Group, lalu pastikan hal berikut.

| Peran | Yang diuji | Hasil yang benar |
|---|---|---|
| Guru Mata Pelajaran | Menambah skor `60` di **Nilai** | Berhasil, dan **Kehadiran** tidak terlihat |
| Wali Kelas | Membuka **Daftar Remedial** | Baris siswa tadi muncul dengan **Status** `Menunggu` |
| Tata Usaha | Mengubah **Data Siswa** | Berhasil, dan **Nilai** hanya dapat dilihat |
| Kepala Sekolah | Membuka seluruh komponen | Semua terlihat, tidak ada yang dapat diubah kecuali Event |
| Orang tua | Membuka *Publish Link* | Hanya pengumuman yang terlihat |

Pantau proses Flow pada [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]]. Tombol **Submission** pada bilah navigasi Flow menampilkan total *activity*, *done*, *waiting*, dan *failure*.

---

## Pemecahan Masalah

| Gejala | Kemungkinan penyebab | Solusi |
|---|---|---|
| Komponen tidak terlihat oleh sebuah Group | **Visible** pada folder induk bernilai `disallow` | Ubah nilai pada folder induk menjadi `allow` |
| Flow tidak berjalan saat skor ditambahkan | Event belum dihubungkan ke Flow | Ulangi [[Docs/Event/Menghubungkan Event]] |
| Baris tidak masuk ke **Daftar Remedial** | Pemetaan kolom pada blok Data belum lengkap | Periksa konfigurasi blok dan lihat status di [[Docs/Modul Logic/Flow/Flow Activity|Flow Activity]] |
| Pengguna tidak dapat membuka Phoenix | Group tidak memiliki Workspace | Petakan Group ke satu Workspace |
| Tombol **Publish** tidak muncul | Group hanya memiliki **View Publish** | Beri **Publish** `allow` pada Group Tata Usaha |

## Praktik Terbaik

- Kerjakan data lebih dulu, lalu [[Docs/Modul Developer/Group/Apa itu Group|Group]] dan [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]], terakhir [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].
- Gunakan relasi pada kolom **Siswa** agar nama tidak ganda.
- Uji Flow dengan satu baris contoh sebelum dipakai seluruh guru.
- Beri **Visible** saja bila peran hanya perlu membaca.

## Batasan dan Catatan

- [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] mengatur akses per komponen, bukan per baris. Pisahkan tabel **Nilai** per kelas bila perlu.
- Menghapus [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] dapat menghilangkan Flow Block dan riwayat [[Docs/Modul Logic/Flow/Flow Activity|Activity]].
- Pastikan setiap Group tetap memiliki minimal satu Workspace.

## Langkah Selanjutnya

- Tambahkan Flow yang memberi tanda otomatis pada siswa dengan **Status** `Alpa` berulang.
- Buat tabel **Nilai** terpisah per kelas untuk pembatasan akses yang lebih ketat.
- Tambahkan Flow untuk mengisi **Tanggal Terbit** pengumuman secara otomatis.

## TL;DR

Buat [[Docs/Folder/Pengenalan|Folder]] dan tabel [[Docs/Modul Data/Table View/Apa itu Table View|Table View]] lebih dulu, lalu [[Docs/Modul Developer/Group/Apa itu Group|Group]] dan [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] untuk mengatur **Visible**, **Add**, **Update**, dan **Delete**. Bangun [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] agar skor di bawah **Batas Tuntas** masuk ke **Daftar Remedial**, dan bagikan pengumuman lewat [[Docs/Publish/Pengenalan|Publish]].

* [ ] TODO (konsolidasi): Halaman ini ditulis dengan asumsi. Mohon dicek: (1) menu **Add > Folder**, **Add > Data > Table View**, **Add > Data > Timeline**, dan **Add > Developer > Group**; (2) nama dan tipe kolom, termasuk Relasi, Pilihan, dan Teks panjang; (3) langkah impor data; (4) pemilihan Event penambahan baris pada Table View dan kategori Flow Block (Event, Operator, Data) beserta pemetaan kolomnya; (5) langkah Publish dan penyalinan *Publish Link*; (6) path wikilink, termasuk subhalaman yang perlu dibuat (Menambahkan Kolom, Mengimpor Data, Relasi Antar Tabel, Menambahkan Pengguna).
* [ ] TODO: Tabel **Daftar Remedial** ditambahkan pada tutorial ini dan belum ada di studi kasus awal. Perbarui struktur folder studi kasus bila disetujui.
* [ ] TODO: Tambahkan tangkapan layar untuk Langkah 2, 9, dan 10 (Table View, halaman kerja Workspace, Blueprint).
 