---
    status: release
    title: Apa itu Group?
    description: Group adalah komponen untuk mengatur komposisi tim dan akses Workspace yang diberikan kepada setiap anggotanya.
    pageDecoration:
      tree:
        priority: 6
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
    <path d="M15 14s1 0 1-1-1-4-5-4-5 3-5 4 1 1 1 1zm-7.978-1L7 12.996c.001-.264.167-1.03.76-1.72C8.312 10.629 9.282 10 11 10c1.717 0 2.687.63 3.24 1.276.593.69.758 1.457.76 1.72l-.008.002-.014.002zM11 7a2 2 0 1 0 0-4 2 2 0 0 0 0 4m3-2a3 3 0 1 1-6 0 3 3 0 0 1 6 0M6.936 9.28a6 6 0 0 0-1.23-.247A7 7 0 0 0 5 9c-4 0-5 3-5 4q0 1 1 1h4.216A2.24 2.24 0 0 1 5 13c0-1.01.377-2.042 1.09-2.904.243-.294.526-.569.846-.816M4.92 10A5.5 5.5 0 0 0 4 13H1c0-.26.164-1.03.76-1.724.545-.636 1.492-1.256 3.16-1.275ZM1.5 5.5a3 3 0 1 1 6 0 3 3 0 0 1-6 0m3-2a2 2 0 1 0 0 4 2 2 0 0 0 0-4"/>
  </svg>'
---
# Apa itu Group?

>**note** Group merupakan salah satu komponen dalam modul [[Docs/Modul Developer/Pengenalan|Developer]] di Phoenix.

Group adalah komponen yang dapat digunakan untuk mengatur komposisi tim Anda serta akses [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] yang diberikan kepada setiap anggota.

Alih-alih mengatur akses satu per satu untuk setiap orang, Anda cukup mengelompokkan anggota ke dalam Group, lalu menentukan Workspace apa saja yang dapat diakses oleh Group tersebut. Group juga dapat disusun bertingkat dengan Group anak, sehingga struktur tim Anda terlihat jelas dalam satu halaman kerja.

## Mengapa Menggunakan Group?

- **Akses diatur sekali untuk banyak orang.** Tentukan Workspace pada Group, dan seluruh anggotanya langsung mengikuti.
- **Struktur tim terlihat jelas.** Group anak tersusun di bawah Group induk dan dapat dibuka atau ditutup sesuai kebutuhan.
- **Perpindahan anggota menjadi cepat.** Pindahkan User ke Group lain dengan *drag and drop*, tanpa mengubah akses satu per satu.
- **Anggota baru langsung tertangani.** User yang baru terdaftar otomatis ditempatkan oleh sistem ke Group berstatus default.

## Konsep Utama

| Istilah | Penjelasan |
| ------- | ---------- |
| [[#Cara Kerja Group|Group]] | Kelompok anggota yang memiliki daftar Workspace dan daftar User. |
| [[#Mengelola Group Anak|Group Anak]] | Group yang berada di bawah Group lain dan memiliki daftar Workspace dan User sendiri. |
| [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] | Ruang kerja yang aksesnya diberikan melalui Group. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Apa itu Workspace|Apa itu Workspace]]. |
| [[#Mengelola User dalam Group|User]] | Anggota yang ditempatkan ke dalam Group. Satu User hanya dapat berada dalam satu Group. |
| [[#Mengelola User dalam Group|Group Berstatus Default]] | Group tempat sistem menempatkan User yang baru terdaftar di [[Inisialisasi/Apa itu Pro?|Pro]]. Pro baru otomatis memiliki Group [[^field/group|Administrator]] sebagai Group berstatus default. |
| [[#Menempatkan Group ke Direktori|Place to Directory]] | Menu untuk menempatkan Group anak sebagai komponen di Area Manajemen Folder. |

## Contoh Penggunaan

**Mengatur akses tim berdasarkan peran**

Sebuah organisasi memiliki beberapa tim dengan kebutuhan Workspace yang berbeda. Dengan Group, administrator cukup menyusun tim sekali, lalu setiap anggota baru tinggal dipindahkan ke Group yang sesuai tanpa mengatur akses per orang.

**Komponen yang terlibat**

| Komponen | Peran |
| -------- | ----- |
| [[^field/group|Manajemen]] | Group induk yang menaungi seluruh tim. |
| [[^field/group|Tim Lapangan]] | Group anak untuk anggota yang hanya memerlukan Workspace operasional. |
| [[^field/workspace|Operasional]] | Workspace untuk pekerjaan harian tim. |
| [[^field/workspace|Laporan]] | Workspace untuk melihat dan mengelola laporan. |

**Langkah pengaturan**

| Langkah | Aksi | Hasil |
| ------- | ---- | ----- |
| 1 | Buat Group induk dan Group anak. Lihat [[#Membuat Group]] dan [[#Mengelola Group Anak]]. | Struktur tim tersusun. |
| 2 | Tambahkan Workspace ke setiap Group, termasuk Group anak. Lihat [[#Mengelola Workspace dalam Group]]. | Setiap Group memiliki akses yang tepat. |
| 3 | User baru terdaftar di [[Inisialisasi/Apa itu Pro?|Pro]]. | Sistem menempatkan User ke Group berstatus default. |
| 4 | Pindahkan User ke Group tim dengan *drag and drop*. Lihat [[#Mengelola User dalam Group]]. | Akses User langsung mengikuti Workspace Group tujuan. |

**Hasil yang dirasakan**

- Anggota baru langsung bekerja di Workspace yang tepat tanpa pengaturan akses satu per satu.
- Administrator melihat seluruh susunan tim, Workspace, dan anggotanya dalam satu halaman kerja.
- Perubahan akses tim cukup dilakukan pada Group, bukan pada setiap orang.

**Ide skenario lain**

| Kebutuhan | Contoh pengaturan |
| --------- | ----------------- |
| Pemisahan departemen | Satu Group per departemen, masing-masing dengan Workspace sendiri. |
| Tim proyek sementara | Buat Group anak untuk proyek, lalu pindahkan anggotanya dan hapus Group setelah proyek selesai. |
| Akses terbatas untuk tamu | Group khusus dengan satu Workspace yang hanya berisi data yang boleh dilihat. |

Dengan Group, pengelolaan akses berpindah dari urusan per orang menjadi urusan per tim, sehingga tim yang bertambah besar tetap mudah diatur.

## Praktik Terbaik

- **Kelompokkan berdasarkan peran atau tim**, bukan berdasarkan perorangan, agar akses mudah dipahami dan dirawat.
- **Berikan Workspace seperlunya** pada setiap Group sesuai prinsip *least privilege*, terutama pada Group [[^field/group|Administrator]] sebagai Group berstatus default karena setiap User baru masuk ke sana lebih dulu.
- **Tambahkan Workspace pada setiap Group, termasuk Group anak**, karena Workspace tidak diwarisi dari Group induk.
- **Pastikan setiap Group memiliki minimal satu Workspace** agar anggotanya tetap dapat memakai Phoenix.
- **Pindahkan User ke Group tujuan segera** setelah terdaftar, agar tidak terlalu lama berada di Group berstatus default.
- **Gunakan [[^field|Place to Directory]]** hanya untuk Group anak yang perlu dikelola sebagai komponen di [[Docs/Antarmuka#Area Manajemen Folder]].

## Batasan dan Catatan

- Akses Workspace diberikan melalui Group, bukan per User. Baris Group pada halaman kerja [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] hanya mengatur akses ke komponen Group, bukan akses per anggota.
- Group anak tidak mewarisi Workspace dari Group induk.
- Satu User hanya dapat berada dalam satu Group.
- Form dari Area Manajemen Folder menambahkan Group sebagai komponen di folder dan mewajibkan [[^field|Parent]] diisi. Form dari halaman kerja Group tidak memiliki bagian direktori dan [[^field|Parent]]-nya terisi otomatis.
- Group yang dibuat dari halaman kerja Group tidak otomatis muncul di Area Manajemen Folder sampai ditempatkan dengan [[^field|Place to Directory]].
- [[^field|Place to Directory]] menempatkan Group di posisi *root* folder dari Workspace yang sedang aktif.
- Menghapus Group juga menghapus Group anaknya, dan Group yang dihapus tidak boleh masih memiliki User. Yang hilang hanyalah daftar Workspace pada Group tersebut.
- User baru otomatis masuk Group berstatus default, sehingga aksesnya mengikuti Workspace Group tersebut sampai Anda memindahkannya.
- Menghapus Workspace dari Group langsung memengaruhi akses seluruh anggota Group itu.

## TL:DR

- Group adalah komponen untuk mengatur tim dan akses [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] bagi anggotanya sekaligus.
- Group dapat dibuat dari Area Manajemen Folder (wajib mengisi [[^field|Parent]]) atau dari halaman kerja Group melalui [[^button/add|Add Group]] yang [[^field|Parent]]-nya terisi otomatis.
- Group anak tersusun di bawah Group induk dan tidak mewarisi Workspace-nya. Menu Group anak adalah [[^field/edit|Edit]], [[^field/add|Add Children]], [[^field|Place to Directory]], dan [[^field/delete|Delete]].
- Tambahkan Workspace lewat [[^field|Search workspace to add...]] dan hapus dengan klik Workspace lalu [[^button|Remove]].
- User baru otomatis masuk Group berstatus default (pada Pro baru adalah Group [[^field/group|Administrator]]). Satu User hanya di satu Group, dan dipindahkan dengan *drag and drop*.
- Sebelum menghapus Group, pindahkan seluruh User di Group tersebut dan Group anaknya, karena Group anak ikut terhapus.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apa bedanya menambahkan Group dari Area Manajemen Folder dan dari halaman kerja Group?**
> Dari Area Manajemen Folder, Group ditambahkan sebagai komponen di folder dan [[^field|Parent]] wajib diisi. Dari halaman kerja Group, formnya tidak memiliki bagian direktori dan [[^field|Parent]] terisi otomatis.
> **Mengapa Group yang saya buat dari halaman kerja tidak muncul di Area Manajemen Folder?**
> Group tersebut belum ditempatkan sebagai komponen. Klik kanan Group ➜ [[^field|Place to Directory]] untuk menempatkannya di posisi *root* folder dari Workspace yang sedang aktif.
> **Apakah Group anak mewarisi Workspace dari Group induk?**
> Tidak. Tambahkan Workspace pada setiap Group melalui [[^field|Search workspace to add...]].
> **Bagaimana cara memindahkan User ke Group lain?**
> Buka halaman kerja Group, lalu *drag and drop* User dari Group lama ke Group tujuan. Lihat [[#Memindahkan User]].
> **Apakah satu User dapat berada di beberapa Group?**
> Tidak. Satu User hanya dapat berada dalam satu Group, jadi memindahkan User berarti mengeluarkannya dari Group lama.
> **Apa yang terjadi bila Group tidak memiliki Workspace?**
> Anggota Group tidak memiliki Workspace untuk dipakai. Pastikan setiap Group masih memiliki minimal satu Workspace.
> **Mengapa Group tidak bisa dihapus?**
> Group yang dihapus, beserta Group anaknya, tidak boleh masih memiliki User. Pindahkan semua User ke Group lain terlebih dahulu.
> **Bagaimana cara menutup daftar Group anak?**
> Klik panah di sebelah kiri judul Group.