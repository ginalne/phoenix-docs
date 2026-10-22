---
    status: release
    title: "Apa itu Timeline?"
    description: Pengenalan lengkap komponen Timeline untuk menampilkan data dalam urutan waktu dan memicu Event terjadwal ke Flow.
    pageDecoration: 
      tree: 
        priority: 5
---

# Apa itu Timeline?

>**note** Timeline merupakan salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Timeline adalah komponen yang menampilkan data dalam urutan waktu sehingga Anda dapat memantau jadwal, riwayat aktivitas, dan perkembangan suatu proses dengan lebih mudah.

Komponen ini cocok untuk perencanaan, pelacakan progres, serta melihat hubungan antar peristiwa dalam satu rentang waktu.

Timeline memiliki dua jenis isi, yaitu [[#Mengelola Timeline Event|Timeline Event]] untuk memicu otomasi terjadwal dan [[#Mengelola Timeline Data|Timeline Data]] untuk menampilkan data sumber di sumbu waktu. Keduanya tampil dalam satu halaman kerja yang dapat digeser, diperbesar, dan diperkecil.

## Mengapa Menggunakan Timeline?

- **Jadwal dan progres dalam satu pandangan.** Setiap data tampil sebagai blok di sumbu waktu sehingga rentang, urutan, dan tumpang tindih peristiwa langsung terlihat.
- **Jadwal dapat diubah langsung.** Geser blok untuk memindahkan waktu [[^field|Start]] atau [[^field|End]] tanpa membuka data sumber satu per satu.
- **Otomasi terjadwal.** [[#Mengelola Timeline Event|Timeline Event]] memicu Flow Block [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]] satu kali atau berulang.
- **Beberapa data dalam satu halaman.** Satu Timeline dapat memiliki lebih dari satu [[#Mengelola Timeline Data|Timeline Data]] dengan [[Docs/Tipe Data/Query|Query]] yang berbeda.
- **Skala waktu fleksibel.** Ubah tampilan dari kuartal sampai detik dengan menu [[#Menu Konteks Timeline|Zoom]] atau *wheel* mouse.

## Konsep Utama

| Istilah | Penjelasan |
| ------- | ---------- |
| [[#Mengelola Timeline Event|Timeline Event]] | Pemicu [[Docs/Event/Apa itu Event|Event]] ke Flow Block Pulser pada waktu tertentu, dengan atau tanpa pengulangan. |
| [[#Mengelola Timeline Data|Timeline Data]] | Pembuka data sumber di sumbu waktu dengan bantuan Query. |
| [[#Query Timeline Data|Query]] | Aturan pengambilan data sumber. Bagian Show menandai kolom yang dipakai sebagai Name, Start, dan End. |
| [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]] | Flow Block Event yang menerima pemicu dari Timeline Event. |
| [[Docs/Tipe Data/Row|Row]] | Satu data sumber. Setiap Row pada Timeline Data tampil sebagai satu blok. |
| [[#Hak Akses Timeline Data|Mode Timeline Data]] | Pengaturan `editable` atau `readonly` yang menentukan apakah Row dapat diubah dari Timeline. |
| [[#Menu Konteks Timeline|Zoom]] | Pengatur tingkat satuan waktu pada header, dari kuartal sampai detik. |
| [[#Preview dan Edit Row|Preview]] | Popup ringkasan Row yang terbuka saat Row diklik kiri. |

## Cara Kerja

Penjelasan cara kerja Timeline lihat selengkap nya di [[Docs/Modul Interface/Timeline/Cara Kerja|Cara Kerja Timeline]].

## Mengelola Timeline

Berikut adalah halaman yang menjelaskan cara untuk mengelola Timeline:

1. [[Docs/Modul Interface/Timeline/Membuat Baru]] Timeline dalam halaman kerja.
2. [[Docs/Modul Interface/Timeline/Mengubah]] Atribut Timeline seperti [[^field|Name]] atau [[^field|Description]].
3. [[Docs/Modul Interface/Timeline/Menghapus]] Timeline.
4. [[Docs/Modul Interface/Timeline/Timeline Event/Pengenalan|Mengelola Event]] Timeline seperti menambahkan, mengubah atau memperbarui Data.
4. [[Docs/Modul Interface/Timeline/Timeline Data/Pengenalan|Mengelola Data]] Timeline seperti menambahkan, mengubah atau memperbarui Data.

## Antarmuka

Penjelasan antarmuka lihat selengkapnya di [[Docs/Modul Interface/Timeline/Antarmuka|Antarmuka Timeline]].

## Praktik Terbaik

- **Atur Query secermat mungkin** dan pastikan Column Name, Start, dan End sesuai agar blok tampil benar.
- **Pisahkan Timeline Data berdasarkan jenis data** atau tahapan agar halaman mudah dibaca.
- **Beri nama Timeline Event yang menjelaskan tujuannya**, misalnya pengingat atau pembersihan, agar mudah dikenali di [[^field|Item List]].
- **Uji Pulser lebih dulu** dengan tombol Trigger pada Flow sebelum menjadwalkannya di Timeline Event.
- **Matikan [[^field|Active]]** bila jadwal hanya perlu dihentikan sementara, daripada menghapus Timeline Event.
- **Gunakan Select sebelum [[^field|Add Row]]** agar Start dan End langsung terisi sesuai rentang yang Anda pilih.
- **Gunakan [[#Menu Konteks Timeline|Zoom]] yang sesuai** dengan rentang data, misalnya Month - Week untuk jadwal bulanan dan Date - Hour untuk jadwal harian.

## Batasan dan Catatan

- Timeline Event hanya memicu [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]]. Proses setelahnya diatur di [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].
- Field [[^field|End]] dan [[^field|Interval]] hilang bila [[^field|Repeat]] [[^value/boolean/false]], sehingga Timeline Event hanya terpicu satu kali.
- Pengelolaan Timeline Event dibatasi Function Access [[^field|Modify Event]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].
- Query Timeline Data mengikuti kaidah Timeline Output. Label [[^field|Name]] dan [[^field|End]] wajib, dan Column untuk [[^field|Start]] serta [[^field|End]] harus berformat DateTime, Date, atau DateTimeZone. Bila tidak terpenuhi, Timeline Data menampilkan [[^field|Error]].
- Row hanya dapat diubah, ditambah, dihapus, dan digeser bila Timeline Data `editable` dan [[Docs/Modul Developer/Workspace/Data Access]] data sumber mengizinkan.
- [[^field|Delete Event]] hanya menghapus Timeline Event dan [[^field|Delete Data]] hanya menghapus konfigurasi dan Query. [[^field|Delete Row]] menghapus Row pada data sumber dan tidak dapat dikembalikan.
- [[^field|Progress]] pada popup preview hanya tampil ketika [[^field|Status]] bernilai [[^field|On Going]].
- Zoom dan *wheel* hanya mengubah tampilan, bukan data.
- Menghapus Timeline menghapus seluruh Timeline Event dan Timeline Data di dalamnya, dan Pulser yang terhubung tidak lagi dipicu dari Timeline tersebut.

## TL:DR

- **Definisi:** Timeline menampilkan data dalam urutan waktu untuk memantau jadwal, riwayat aktivitas, dan progres.
- **Isi:** Timeline Event memicu Pulser dengan atau tanpa pengulangan, Timeline Data menampilkan Row dari data sumber lewat Query.
- **Antarmuka:** bilah navigasi di atas dan area kerja di bawah, dengan menu konteks dan menu [[^field|Zoom]] dari klik kanan.
- **Membangun:** tambahkan isi dengan [[^button/add|Add Event]] dan [[^button/add|Add Data]], lalu atur Query lewat [[^button/q]] yang tersimpan otomatis.
- **Interaksi:** gulir, *wheel*, pindahkan blok, dan Select. Klik kiri Row membuka preview, dan Select mengisi Start dan End saat [[^field|Add Row]].
- **Hati-hati:** Row hanya dapat diubah bila `editable` dan Data Access mengizinkan, Query harus valid, dan [[^field|Delete Row]] menghapus data sumber.
