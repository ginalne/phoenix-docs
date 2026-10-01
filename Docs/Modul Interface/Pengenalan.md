---
    status: released
    date: "2026-10-02"
    pageDecoration:
      #icon: empty
      tree:
        priority: 1
---
# Modul Interface
_Interface_ merupakan salah satu modul dalam Phoenix. Modul ini berfungsi sebagai antar muka yang membantu Anda mengelola Data yang sudah dibangun agar lebih interaktif, mudah dipahami serta cepat diproses.

Berikut adalah beberapa komponen yang bisa digunakan dalam modul ini:
1. [[#Table View]]
2. [[#Form]]
3. [[#Timeline]]
4. [[#Gallery]]
5. [[#Kanban]]
6. [[#Canvas]]
7. [[#Space]]

## Table View
Table View merupakan komponen yang dapat mempermudah Anda mengelola data Tabel secara simultan. 

>[!note] Saran
>Karena sifatnya universal, pastikan Anda menyimpan komponen ini secara aman dan dapat mengatur aksesnya dengan hati-hati menggunakan [[Docs/Komponen/Developer/Workspace]].

## Enum
Enum merupakan komponen yang dapat digunakan sebagai deret data atau yang sering dikenal dengan Master Data. Sifat data ini digunakan sebagai pilihan, menu, opsi ataupun kategori. Salah satu atribut penting dalam Enum adalah [[Docs/Modul Data/Enum/Konfigurasi Ketat]].

lihat selengkapnya [[Docs/Modul Data/Enum/Apa itu Enum]]

## Tabel
Table merupakan komponen yang dapat menyimpan data secara kompleks. Sifat data ini dapat digunakan untuk menyimpan data yang transaksional maupun generik. Table dapat memiliki beberapa [[Docs/Komponen/Table/Kolom]] yang masing-masing memiliki format yang berbeda, begitu juga [[Docs/Data/Format]] 