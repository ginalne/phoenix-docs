# PROPOSAL JASA

## Technical & Financial Service Proposal

**Phoenix — Digital Ecosystem & Workflow Solutions**

---

**Ditujukan Kepada:** Komunitas Parsibo

**Disusun Oleh:** Harbi

|     |     |
| --- | --- |
| **Nomor Dokumen** | PHX-SP-2026-0001 |
| **Tanggal** | 11 November 2026 |
| **Berlaku Sampai** | 30 hari sejak tanggal dokumen \[ASUMSI\] |
| **Confidentiality** | Confidential |

## Kontrol Dokumen

| Elemen | Keterangan |
| --- | --- |
| Judul dokumen | Proposal Penawaran Jasa — Pilot Project Sistem Data Silsilah dan Pendataan Anggota Komunitas Parsibo |
| Nomor dokumen | PHX-SP-2026-\[XXX\] |
| Versi / tanggal revisi | v0.2 / 26 November 2026 |
| Disusun oleh | \[NAMA, JABATAN\], Phoenix — Ginalne |
| Ditujukan kepada | \[NAMA PENGURUS, JABATAN\], Komunitas Parsibo |
| Status dokumen | Untuk ditinjau |
| Klasifikasi | Confidential |

### Riwayat Perubahan

| Versi | Tanggal | Bagian yang diubah | Disusun oleh | Persetujuan |
| --- | --- | --- | --- | --- |
| v0.1 | 11 Nov 2026 | Penyusunan awal dan revisi Bagian 1-3 | \[NAMA\] | \[NAMA / STATUS\] |
| v0.2 | 26 Nov 2026 | Konversi ke Markdown, penyesuaian pilot project, Bagian 4-11, asumsi biaya | \[NAMA\] | \[NAMA / STATUS\] |

## 1\. Ringkasan Eksekutif

Parsibo membutuhkan solusi untuk mengatur dan mengelola seluruh data silsilah keturunan dari Parsibo sebagai marga.

Phoenix menawarkan solusi melalui platform teknologi yang memungkinkan organisasi membangun sistem data silsilah terintegrasi, mengelola data silsilah sesuai kebutuhan, merancang workflow data silsilah mulai dari pendaftaran sampai kategori kelompok, dan menghubungkan berbagai proses pendataan silsilah dalam satu ekosistem.

Melalui proposal ini, Phoenix mengajukan layanan Digital Platform yang bertujuan untuk membantu Parsibo mencapai:

*   Keutuhan data silsilah keturunan Himpunan Parsibo.
*   Himpunan data yang terorganisir sesuai kebutuhan.

Solusi ini akan dirancang berdasarkan kebutuhan dan kondisi operasional, dengan mempertimbangkan skalabilitas serta kemungkinan pengembangan di masa mendatang.

## 2\. Pemahaman Kebutuhan

Berdasarkan diskusi dan kebutuhan awal, kami memahami beberapa kondisi berikut:

*   Pencatatan silsilah yang masih tersebar.
*   Pencatatan biodata anggota yang masih manual.
*   Kebutuhan sistem pengumpulan, pemeliharaan, dan akses data.

## 3\. Tujuan

Proyek ini memiliki beberapa tujuan utama:

*   Memusatkan data Komunitas Parsibo pada satu platform yang terstruktur.
*   Menyatukan pengelolaan data dan workflow Komunitas Parsibo.
*   Mengurangi pekerjaan manual dan repetitif.
*   Memberikan pondasi basis data yang dapat dikembangkan sesuai pertumbuhan organisasi.

## 4\. Proposed Solution

### 4.1 Solution Overview

Phoenix akan membantu Komunitas Parsibo membangun ekosistem digital yang disesuaikan dengan kebutuhan pendataan silsilah dan anggota. Solusi dirancang agar tidak hanya menyimpan data, tetapi juga menjaga kualitasnya melalui aturan validasi dan alur verifikasi.

| Area | Proposed Solution | Description |
| --- | --- | --- |
| Data Management | Tree untuk silsilah, Table untuk biodata anggota, Enum untuk data rujukan | Setiap individu menjadi Node pada Tree sehingga hubungan orang tua dan anak terjaga. Biodata lengkap disimpan di Table dan terhubung ke Node. Enum menyeragamkan pilihan seperti status, wilayah, dan jenis hubungan. |
| Interface | Form pendaftaran, Table View, dan Canvas dashboard | Form untuk pendaftaran dan pembaruan data, Table View untuk pencarian dan penyaringan anggota, Canvas untuk ringkasan jumlah anggota dan status verifikasi. |
| Workflow & Automation | Flow untuk validasi dan alur verifikasi | Data yang masuk diperiksa otomatis (kelengkapan, duplikasi, kewajaran tanggal), diarahkan ke verifikator, lalu ditempatkan ke posisi yang benar pada silsilah setelah disetujui. |
| Integration | Opsional, di luar paket inti pilot | Koneksi ke layanan eksternal, misalnya pengiriman notifikasi, melalui HTTP Request pada Flow. Lihat Bagian 8.1 (Opsi Tambahan). |
| Access Management | Group dan Workspace per peran | Admin pusat, verifikator, dan pengurus memiliki ruang kerja dan hak akses (Data, Component, Function) yang berbed
### 4.2 Phoenix Platform

Phoenix merupakan platform teknologi untuk membangun ekosistem operasional yang fleksibel dan terintegrasi.

Platform ini memiliki empat kelompok kemampuan utama:

*   **Data:** Mengatur struktur, relasi, dan pengelolaan data.
*   **Interface:** Menyediakan berbagai cara untuk berinteraksi dengan data.
*   **Logic:** Menghubungkan proses melalui workflow dan otomatisasi.
*   **Developer:** Mengelola akses, workspace, dan pengembangan sistem.
### 4.3 Pilot Scope

Agar nilai solusi dapat dibuktikan dengan risiko dan biaya yang terukur, pilot dibatasi sebagai berikut: \[ASUMSI\]

| Parameter | Batas Pilot |
| --- | --- |
| Cakupan data | Satu kelompok keluarga besar atau garis keturunan terpilih |
| Jumlah data awal | Hingga 500 anggota |
| Kedalaman silsilah | Hingga 7 generasi |
| Pengguna aktif | Hingga 20 pengguna (admin, verifikator, pengurus) |
| Peran pengguna | 3 peran: Admin Pusat, Verifikator, Pengurus |
| Durasi operasional pilot | 30 hari setelah go-live (termasuk masa dukungan) |

Pengembangan lebih luas, seperti penambahan kelompok keluarga lain, dilakukan setelah evaluasi pilot sebagai tahap lanjutan dengan proposal tersendiri.

### 4.4 Aturan Bisnis Pilot

Berikut aturan awal yang akan diterapkan pada sistem. Aturan ini bersifat asumsi dan akan dikonfirmasi pada tahap Requirement Analysis. \[ASUMSI\]

| No. | Aturan | Cara Ditangani |
| --- | --- | --- |
| 1   | Setiap anggota hanya memiliki satu orang tua (garis keturunan) pada silsilah | Struktur Tree |
| 2   | Pendaftar wajib memilih orang tua dari data yang sudah terverifikasi | Form dan Query pada pilihan data |
| 3   | Jika orang tua belum ada di sistem, pendaftaran diberi status "Perlu Penelusuran" | Flow dan Branch |
| 4   | Data yang berpotensi duplikat (nama, tanggal lahir, nama orang tua) ditandai sebelum diverifikasi | Flow dan Query |
| 5   | Tanggal lahir anak harus setelah tanggal lahir orang tua dengan selisih wajar | Flow dan validasi |
| 6   | Status data: Draft, Menunggu Verifikasi, Perlu Perbaikan, Terverifikasi, Ditolak | Enum dan Flow |
| 7   | Hanya data berstatus Terverifikasi yang ditempatkan ke silsilah | Flow (Assign Node) |
| 8   | Generasi anggota dihitung otomatis dari posisinya pada silsilah | Flow (Node Get Ancestor) |
| 9   | Perubahan data tertentu (misalnya hubungan keluarga) hanya dapat dilakukan verifikator atau admin | Group, Workspace, dan Data Access |

## 5\. Scope of Services

Layanan yang akan diberikan dalam proyek ini meliputi:

| No. | Service | Description | Deliverables | Dalam Paket Pilot |
| --- | --- | --- | --- | --- |
| 1   | Requirement Analysis | Analisis kebutuhan, proses pendataan, dan penyepakatan aturan bisnis | Requirement Document | Ya  |
| 2   | System Planning | Perancangan struktur data, alur kerja, dan hak akses | System Design | Ya  |
| 3   | System Configuration | Konfigurasi Tree, Table, Enum, Form, Table View, Canvas, serta Group dan Workspace | Configured System | Ya  |
| 4   | Workflow Development | Pengembangan alur validasi, verifikasi, dan penempatan silsilah | Workflow Implementation | Ya  |
| 5   | Data Migration | Pemindahan data awal (hingga 500 anggota) dari catatan yang ada | Migrated Data | Ya  |
| 6   | Testing | Pengujian sistem dan uji penerimaan pengguna (UAT) | Testing Report | Ya  |
| 7   | Training & Deployment | Pelatihan pengguna dan administrator, serta implementasi ke lingkungan operasional | Training Session, Production Deployment | Ya  |
| 8   | Project Management & Documentation | Koordinasi proyek, pelaporan progres, dan dokumentasi | Progress Report, Dokumentasi | Ya  |
| 9   | Integration | Integrasi dengan sistem eksternal (misalnya notifikasi) | Integration Setup | Opsional |

Item yang tidak termasuk dalam kesepakatan proyek akan diperlakukan sebagai pekerjaan tambahan.

## 6\. Project Deliverables

Pada akhir proyek, klien akan menerima:

*   Struktur data silsilah (Tree) dan data anggota (Table, Enum) yang telah dikonfigurasi.
*   Form pendaftaran anggota, Table View pencarian anggota, dan Canvas dashboard ringkasan.
*   Alur kerja otomatis untuk pendaftaran, validasi, verifikasi, dan penempatan pada silsilah.
*   Pengaturan Group dan Workspace sesuai peran pengguna.
*   Data awal yang telah dimigrasikan (hingga 500 anggota).
*   Dokumentasi penggunaan sistem.
*   Dokumentasi konfigurasi atau implementasi yang disepakati.
*   Sesi pelatihan dan serah terima.
*   Laporan evaluasi pilot beserta rekomendasi tahap lanjutan.

### Kriteria Keberhasilan Pilot \[ASUMSI\]

*   Seluruh data awal yang disepakati berhasil dimigrasikan dan tampil pada silsilah.
*   Alur pendaftaran sampai penempatan silsilah berjalan sesuai aturan bisnis pada Bagian 4.4.
*   Minimal 1 siklus pendaftaran anggota baru berhasil diverifikasi dan ditempatkan melalui sistem.
*   Admin dan verifikator mampu mengoperasikan sistem secara mandiri setelah pelatihan.

## 7\. Project Timeline

Estimasi pelaksanaan proyek: \[ASUMSI\]

| Phase | Activities | Duration |
| --- | --- | --- |
| Phase 1 | Requirement Analysis | 1 minggu |
| Phase 2 | System Planning | 1 minggu |
| Phase 3 | Development & Configuration | 3 minggu |
| Phase 4 | Testing & Revision | 1 minggu |
| Phase 5 | Deployment & Training | 1 minggu |

**Estimated Project Duration:** 7 minggu, ditambah 30 hari masa dukungan setelah go-live.

Timeline dapat berubah berdasarkan kompleksitas kebutuhan, ketersediaan data, dan persetujuan dari kedua belah pihak.

## 8\. Investment & Pricing

> Seluruh nilai pada bagian ini adalah asumsi untuk keperluan diskusi. Estimasi didasarkan pada 38 hari kerja (man-days) dengan tarif normal Rp 2.000.000 per hari dan diskon pilot 25% (Rp 1.500.000 per hari). \[ASUMSI\]

### 8.1 Service Fees

| No. | Description | Estimasi Usaha | Amount |
| --- | --- | --- | --- |
| 1   | Requirement Analysis | 4 hari | Rp 6.000.000 |
| 2   | System Planning | 4 hari | Rp 6.000.000 |
| 3   | System Configuration | 10 hari | Rp 15.000.000 |
| 4   | Workflow Development | 8 hari | Rp 12.000.000 |
| 5   | Data Migration (hingga 500 anggota) | 3 hari | Rp 4.500.000 |
| 6   | Testing & UAT | 3 hari | Rp 4.500.000 |
| 7   | Training & Deployment | 3 hari | Rp 4.500.000 |
| 8   | Project Management & Documentation | 3 hari | Rp 4.500.000 |
|     | **Nilai normal (38 hari x Rp 2.000.000)** |     | Rp 76.000.000 |
|     | Diskon pilot project 25% |     | (Rp 19.000.000) |
|     | **Subtotal** |     | **Rp 57.000.000** |
|     | Pajak (PPN 11%, jika berlaku) |     | Rp 6.270.000 |
|     | **Total Investment (termasuk PPN)** |     | **Rp 63.270.000** |

Jika pajak tidak berlaku, Total Investment adalah Rp 57.000.000.

**Opsi tambahan (tidak termasuk dalam total di atas):**

| Opsi | Description | Amount |
| --- | --- | --- |
| Integration | Integrasi notifikasi melalui layanan eksternal (HTTP Request pada Flow) | Rp 4.500.000 (3 hari) |
| Dukungan lanjutan | Dukungan teknis dan pemeliharaan setelah masa dukungan pilot | Rp 3.000.000 per bulan |

Biaya lisensi platform dan hosting selama pilot: \[ISI: ditanggung Phoenix / ditagihkan terpisah\]. Hal ini perlu ditentukan sebelum proposal dikirim.

### 8.2 Payment Terms

| Milestone | Payment | Amount (belum termasuk pajak) |
| --- | --- | --- |
| Project Confirmation | 40% | Rp 22.800.000 |
| Development Completion | 30% | Rp 17.100.000 |
| Final Delivery | 30% | Rp 17.100.000 |

Pembayaran dilakukan sesuai milestone yang disepakati dan ketentuan faktur.

### 8.3 Additional Costs

Item berikut tidak termasuk kecuali disebutkan secara eksplisit dalam proposal ini:

*   Langganan perangkat lunak dan layanan pihak ketiga.
*   Biaya infrastruktur cloud dan hosting.
*   Pengembangan tambahan di luar ruang lingkup yang disepakati.
*   Migrasi data melebihi volume atau kompleksitas yang disepakati (di atas 500 anggota).
*   Penambahan kelompok keluarga, peran, atau pengguna di luar batas pilot.
*   Biaya perjalanan dan akomodasi, jika diperlukan.

## 9\. Support & Maintenance

Phoenix memberikan dukungan pasca-implementasi sesuai perjanjian layanan yang dipilih.

| Support Area | Description |
| --- | --- |
| Technical Support | Bantuan untuk kendala teknis |
| System Maintenance | Pemeliharaan sistem yang telah diimplementasikan |
| Bug Fixes | Perbaikan cacat yang berkaitan dengan implementasi |
| Consultation | Panduan penggunaan dan optimalisasi sistem |
| Enhancement | Fitur dan peningkatan tambahan (di luar ruang lingkup, dihitung terpisah) |

**Support Period:** 30 hari setelah go-live \[ASUMSI\]

**Support Arrangement:** Email dan online meeting \[ASUMSI\]

## 10\. Terms & Conditions

### 10.1 Asumsi dan Ketergantungan

*   Komunitas Parsibo menunjuk satu penanggung jawab yang berwenang mengambil keputusan.
*   Data silsilah awal diserahkan dalam bentuk yang dapat diolah sesuai jadwal yang disepakati.
*   Umpan balik pada setiap tahap diberikan dalam 3 hari kerja. \[ASUMSI\]
*   Data anggota adalah data pribadi. Komunitas Parsibo selaku pemilik data bertanggung jawab memperoleh persetujuan anggota dan memastikan pengelolaannya sesuai peraturan pelindungan data pribadi yang berlaku (UU No. 27 Tahun 2022).
*   Tautan pendaftaran publik hanya digunakan untuk pengisian data pendaftaran. Data yang masuk melalui tautan tersebut wajib melalui verifikasi sebelum menjadi bagian dari silsilah.

### 10.2 Ketentuan

1.  Proposal ini berlaku sampai tanggal yang tercantum pada sampul.
2.  Pekerjaan dimulai setelah proposal disetujui dan pembayaran awal diterima, jika berlaku.
3.  Perubahan ruang lingkup dapat memerlukan biaya tambahan dan penyesuaian jadwal.
4.  Klien bertanggung jawab menyediakan informasi, akses, dan sumber daya yang dibutuhkan.
5.  Seluruh deliverable diserahkan sesuai ruang lingkup yang disepakati.
6.  Kepemilikan, lisensi, dan hak penggunaan atas Phoenix dan komponen kustom yang dikembangkan mengikuti perjanjian yang berlaku.
7.  Informasi rahasia yang dibagikan selama proyek wajib dilindungi oleh kedua belah pihak.
8.  Ketentuan tambahan akan didokumentasikan dalam perjanjian layanan final.

## 11\. Acceptance & Approval

Dengan menandatangani di bawah ini, kedua belah pihak menyatakan menerima ruang lingkup, investasi, jadwal, dan ketentuan yang diuraikan dalam dokumen ini.

| **PREPARED BY**  <br>Phoenix — Ginalne | **ACCEPTED BY**  <br>Komunitas Parsibo |
| --- | --- |
| Name: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | Name: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |
| Position: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | Position: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |
| Date: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | Date: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |
| Signature: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | Signature: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

**Phoenix — Build Your Ecosystem. Improve How You Work.**

Website: https://phoenix.ginalne.com | Email: phoenix@ginalne.com