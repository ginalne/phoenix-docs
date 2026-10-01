---
    status: released
    date: "2026-10-02"
    pageDecoration:
      #icon: empty
      tree:
        priority: 1
---
# Modul Data
Data merupakan salah satu modul dalam Phoenix. Modul ini berfungsi untuk memebangun, mengatur serta menyiapkan integrasi Data yang dapat menjadi pondasi dari ekosistem yang Anda bangun.

Berikut adalah beberapa komponen yang bisa digunakan dalam modul ini:
1. [[#Variable]]
2. [[#Enum]]
3. [[#Table]]
4. [[#Tree]]

## Variabel
Variabel merupaakan komponen yang dikenali semua komponen sebagai satu sumber universal. Komponen ini secara _default_ dibuat ketika memulai halaman kerja (Pro) baru dan tidak dapat dihapus.

>[!note] Saran
>Karena sifatnya universal, pastikan Anda menyimpan komponen ini secara aman dan dapat mengatur aksesnya dengan hati-hati menggunakan [[Docs/Komponen/Developer/Workspace]].

## Enum
Enum merupakan komponen yang dapat digunakan sebagai deret data atau yang sering dikenal dengan Master Data. Sifat data ini digunakan sebagai pilihan, menu, opsi ataupun kategori. Salah satu atribut penting dalam Enum adalah [[Docs/Modul Data/Enum/Konfigurasi Ketat]].

lihat selengkapnya [[Docs/Modul Data/Enum/Apa itu Enum]]

## Tabel
Table merupakan komponen yang dapat menyimpan data secara kompleks. Sifat data ini dapat digunakan untuk menyimpan data yang transaksional maupun generik. Table dapat memiliki beberapa [[Docs/Komponen/Table/Kolom]] yang masing-masing memiliki format yang berbeda, begitu juga [[Docs/Data/Format]] 