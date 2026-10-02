---
    status: released
    date: "2026-10-02"
    pageDecoration:
      #icon: empty
      tree:
        priority: 4
---
# Modul Data
Data merupakan salah satu modul dalam Phoenix. Modul ini berfungsi untuk memebangun, mengatur serta menyiapkan integrasi Data yang dapat menjadi pondasi dari ekosistem yang Anda bangun.

Berikut adalah beberapa komponen yang bisa digunakan dalam modul ini:
1. [[#Variable]]
2. [[#Enum]]
3. [[#Table]]
4. [[#Tree]]

## Variabel
Variabel merupakan komponen yang dikenali semua komponen sebagai satu sumber universal. Komponen ini secara _default_ dibuat ketika memulai halaman kerja (Pro) baru dan tidak dapat dihapus.

>**warning** Harap hati-hati
>Karena sifatnya universal, pastikan Anda menyimpan komponen ini secara aman dan dapat mengatur aksesnya dengan hati-hati menggunakan [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

lihat selengkapnya [[Docs/Modul Data/Variabel/Apa itu Variabel]].

## Enum
Enum merupakan komponen yang dapat digunakan sebagai deret data atau yang sering dikenal dengan Master Data. Sifat data ini digunakan sebagai pilihan, menu, opsi ataupun kategori. Setiap Enum memiliki banyak [[Docs/Tipe Data/EnumData]] didalamnya. Salah satu atribut penting dalam Enum adalah [[Docs/Modul Data/Enum/Konfigurasi Ketat]].

lihat selengkapnya [[Docs/Modul Data/Enum/Apa itu Enum]].

## Table
Table merupakan komponen yang dapat menyimpan data secara kompleks. Sifat data ini dapat digunakan untuk menyimpan data yang transaksional maupun generik. Table dapat memiliki beberapa [[Docs/Tipe Data/Column]] yang masing-masing memiliki format yang berbeda, dan memiliki [[Docs/Tipe Data/Row]] yang masing-masing memiliki [[Docs/Tipe Data/TableData]] sesuai kolom yang tersedia. [[Docs/Tipe Data/Expression]] dapat berfungsi oleh komponen ini secara langsung.

lihat selengkapnya [[Docs/Modul Data/Table/Apa itu Table]].

## Tree
Tree merupakan komponen yang dapat menyimpan data secara hierarki atau berbentuk pohon. Sifat data ini dapat digunakan untuk menyimpan data relasional yang bercabang. Tree dapat memiliki banyak [[Docs/Tipe Data/Node]]. Salah satu atribut penting dalam Tree adalah [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]].

lihat selengkapnya [[Docs/Modul Data/Tree/Apa itu Tree]].

