---
    status: release
    title: "Mengelola Timeline Event"
    description: 
    pageDecoration:
      tree:
        priority: 6
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

## Mengelola Timeline Event

Berikut adalah halaman yang menjelaskan cara untuk mengelolanya:
1. [[Docs/Modul Interface/Timeline/Timeline Event/Menambahkan]] Timeline Event.
2. [[Docs/Modul Interface/Timeline/Timeline Event/Mengubah]] Timeline Event.
3. [[Docs/Modul Interface/Timeline/Timeline Event/Menghapus]] Timeline Event.

## Hak Akses Timeline Event

Menambah, mengubah, menggeser, dan menghapus Timeline Event dibatasi Function Access [[^field|Modify Event]] di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].