---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 4
    tags:
      draft
---
# Mengelola Timeline Event

Timeline Event berfungsi untuk membuat *trigger* [[Docs/Event/Apa itu Event|Event]] ke Flow Block [[Docs/Modul Logic/Flow/Flow Block/Event/Pulser|Pulser]], dengan atau tanpa pengulangan. Timeline Event hanya memicu Pulser, sedangkan proses setelahnya diatur di [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

## Atribut Timeline Event

| Atribut | Penjelasan |
| ------- | ---------- |
| [[^field|Name]] | Nama Timeline Event yang tampil di [[^field|Item List]]. |
| [[^field|Pulser Event]] | Flow Block Pulser yang akan dipicu. |
| [[^field|Start]] | Tanggal dan waktu pemicu pertama. |
| [[^field|Repeat]] | Menentukan apakah pemicu berulang. Bawaannya aktif. |
| [[^field|End]] | Tanggal dan waktu berakhirnya pengulangan. Hanya tampil ketika [[^field|Repeat]] aktif. |
| [[^field|Interval]] | Jarak waktu antar pemicu. Hanya tampil ketika [[^field|Repeat]] aktif. |
| [[^field|Active]] | Menentukan apakah jadwal berjalan. Bawaannya aktif. |

Pilihan [[^field|Interval]] adalah [[^field|Custom]], [[^field|Minutely]], [[^field|Hourly]], [[^field|Daily]], [[^field|Weekly]], [[^field|Monthly]], [[^field|Quarterly]], dan [[^field|Yearly]]. Pilihan [[^field|Custom]] memungkinkan jarak antar pemicu diisi dalam satuan menit.

>**note** Repeat dan field turunannya
> Field [[^field|End]] dan [[^field|Interval]] hanya tampil ketika [[^field|Repeat]] aktif. Jika [[^field|Repeat]] [[^value/boolean/false]], Timeline Event hanya memicu Pulser satu kali pada waktu [[^field|Start]].

>**note** Menonaktifkan jadwal
> Matikan [[^field|Active]] untuk menghentikan jadwal tanpa menghapus Timeline Event. Aktifkan kembali saat jadwal perlu berjalan.

## Menambahkan Timeline Event

![[Docs/Modul Interface/Timeline/add-timeline-event.png]]
1. Klik [[^button/add|Add Event]], atau klik kanan ➜ [[^field|Add Event]]
2. Isi [[^field|Name]]
3. Pilih Flow Block Pulser yang akan dipicu di [[^field|Pulser Event]]
4. Isi waktu mulai di [[^field|Start]]
5. Aktifkan [[^field|Repeat]] bila pemicu perlu berulang, lalu isi [[^field|End]] dan [[^field|Interval]]
6. Pastikan [[^field|Active]] aktif agar jadwal berjalan
7. Klik [[^button|Create]]

>**success** Timeline Event berhasil dibuat
> Pemicu berjalan pada jadwal yang ditentukan selama [[^field|Active]] aktif.

## Mengubah Timeline Event

1. Klik kanan blok Timeline Event ➜ [[^field|Edit]]
2. Ubah atribut yang diperlukan
3. Klik [[^button|Update]]

Waktu [[^field|Start]] dan [[^field|End]] juga dapat dipindahkan dengan menggeser blok, lihat [[#Interaksi Antarmuka Timeline]].

## Menghapus Timeline Event

1. Klik kanan blok Timeline Event ➜ [[^field|Delete Event]]
2. Konfirmasi dengan klik [[^button|Delete]]

>**warning** Hanya Timeline Event yang terhapus
> [[^field|Delete Event]] hanya menghapus Timeline Event. Flow Block Pulser tidak ikut terhapus, tetapi tidak lagi dipicu oleh Timeline Event tersebut. Bila jadwal hanya perlu dihentikan sementara, matikan [[^field|Active]].

## Hak Akses Timeline Event

Menambah, mengubah, menggeser, dan menghapus Timeline Event dibatasi Function Access [[^field|Modify Event]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].