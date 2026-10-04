---
    status: release
    title: Konfigurasi Tegas dalam Enum
    description: 
    date: "2026-10-02"
    pageDecoration:
      tree:
        priority: 4
---
# Konfigurasi Tegas dalam Enum
[[Docs/Modul Data/Enum/Apa itu Enum|Enum]] memiliki atribut Name dan Description yang muncul ketika pengguna sedang memilih [[Docs/Tipe Data/EnumData]] , namun dalam proses Data Gathering, terkadang nilai [[Docs/Tipe Data/EnumData]] belum ada yang mewakilkan, sehingga konfigurasi Enum dapat dibuka menjadi tidak ketat agar penambahan data selama input dapat dilakukan.

## Mengatur Konfigurasi
Anda dapat mengaturnya melalui tombol [[button/edit|Edit]] dalam halaman kerja [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] atau saat membuat komponen [[Docs/Modul Data/Enum/Apa itu Enum|Enum]] pertama kali.

![[Docs/Modul Data/Enum/create-new-enum.png|Modal Tambah Enum Baru]]
Kolom [[field|Strict On Selected]] dapat diubah dengan implikasi seperti berikut:
1. [[field|Disabled to insert externally]] : Ketat, EnumData tidak bisa ditambahkan saat pengguna atau Anda melakukan input bebas terhadap Enum ini.
2. [[field|Enable to insert externally]] : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna atau Anda saat melakukan input bebas terhadap Enum ini.

## Arti dari “Externally”
_Externally_ artinya sesuatu yang diluar Enum. Saat menentukan sebuah inputan dengan tipe data [[Docs/Tipe Data/EnumData|EnumData]], anda harus memilih header Enum. Input ini dapat muncul dalam [[Docs/Komponen/Table/Pengenalan|Tabel]], komponen dalam [[Docs/Modul Interface/Pengenalan|Modul Interface]] seperti [[Docs/Modul Interface/Form/Pengenalan|Form]] yang dapat diinput oleh publik.

>**note**Tips
>Meskipun Enum Data bisa bertambah secara liar, namun atribut Name dalam EnumData tetap tidak dapat terduplikat. Meskipun akan banyak variasi Name yang mirip, Anda dapat menggunakan fitur [[Docs/Modul Data/Enum/EnumData Merge]] agar setiap data yang terelasi dengan EnumData tersebut dapat menjadi satu EnumData.

