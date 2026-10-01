---
    status: draft
    date: "2026-10-02"
    pageDecoration:
      icon: x
      tree:
        priority: 4
---
# Konfigurasi Ketat dalam Enum
Enum memiliki atribut Name dan Description yang muncul ketika pengguna sedang memilih EnumData, namun dalam proses Data Gatehring, terkadang nilai EnumData belum ada yang mewakilkan, sehingga konfigurasi Enum dapat dibuka menjadi tidak ketat agar penambahan data selama input dapat dilakukan.

## Mengatur Konfigurasi
Anda dapat mengaturnya melalui tombol Edit Enum dalam halaman kerja atau saat membuat [[Docs/Modul Data/Enum/Apa itu Enum|Komponen Enum]] pertama kali.

![[Docs/Modul Data/Enum/create-new-enum.png]]
Kolom _Strict On Selected_ dapat diubah dengan implikasi seperti berikut:
* Disabled to insert externally : Ketat, EnumData tidak bisa ditambahkan saat pengguna atau Anda melakukan input bebas terhadap Enum ini.
* _Enable to insert externally_ : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna atau Anda saat melakukan input bebas terhadap Enum ini.

## Arti dari “Externally”
Externally artinya sesuatu yang diluar Enum. 