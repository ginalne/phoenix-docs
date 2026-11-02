---
    status: release
    title: "Contoh Penggunaan Group"
    description: "Penjelasan contoh penggunaan Group : Mengatur akses tim berdasarkan peran"
    pageDecoration:
      tree:
        priority: -3
---
# Contoh Penggunaan Group

## Studi Kasus : Mengatur akses tim berdasarkan peran

Sebuah organisasi memiliki beberapa tim dengan kebutuhan Workspace yang berbeda. Dengan Group, administrator cukup menyusun tim sekali, lalu setiap anggota baru tinggal dipindahkan ke Group yang sesuai tanpa mengatur akses per orang.

## Komponen yang terlibat

| Komponen | Peran |
| -------- | ----- |
| [[^field/group|Manajemen]] | Group induk yang menaungi seluruh tim. |
| [[^field/group|Tim Lapangan]] | Group anak untuk anggota yang hanya memerlukan Workspace operasional. |
| [[^field/workspace|Operasional]] | Workspace untuk pekerjaan harian tim. |
| [[^field/workspace|Laporan]] | Workspace untuk melihat dan mengelola laporan. |

## Langkah pengaturan

| Langkah | Aksi | Hasil |
| ------- | ---- | ----- |
| 1 | Buat Group induk dan Group anak. Lihat [[#Membuat Group]] dan [[#Mengelola Group Anak]]. | Struktur tim tersusun. |
| 2 | Tambahkan Workspace ke setiap Group, termasuk Group anak. Lihat [[#Mengelola Workspace dalam Group]]. | Setiap Group memiliki akses yang tepat. |
| 3 | User baru terdaftar di [[Inisialisasi/Apa itu Pro?|Pro]]. | Sistem menempatkan User ke Group berstatus default. |
| 4 | Pindahkan User ke Group tim dengan *drag and drop*. Lihat [[#Mengelola User dalam Group]]. | Akses User langsung mengikuti Workspace Group tujuan. |

## Hasil yang dirasakan

- Anggota baru langsung bekerja di Workspace yang tepat tanpa pengaturan akses satu per satu.
- Administrator melihat seluruh susunan tim, Workspace, dan anggotanya dalam satu halaman kerja.
- Perubahan akses tim cukup dilakukan pada Group, bukan pada setiap orang.

## Ide skenario lain

| Kebutuhan | Contoh pengaturan |
| --------- | ----------------- |
| Pemisahan departemen | Satu Group per departemen, masing-masing dengan Workspace sendiri. |
| Tim proyek sementara | Buat Group anak untuk proyek, lalu pindahkan anggotanya dan hapus Group setelah proyek selesai. |
| Akses terbatas untuk tamu | Group khusus dengan satu Workspace yang hanya berisi data yang boleh dilihat. |

Dengan Group, pengelolaan akses berpindah dari urusan per orang menjadi urusan per tim, sehingga tim yang bertambah besar tetap mudah diatur.
