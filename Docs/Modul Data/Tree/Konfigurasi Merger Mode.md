---
    status: draft
    date: "2026-10-02"
    pageDecoration:
      icon: x
      tree:
        priority: 4
---
# Konfigurasi Merger Mode
Tree memiliki [[Docs/Tipe Data/Node]] dengan atribut Order dan Name yang muncul ketika pengguna memilih atau menambahkannya, namun dalam proses pengelolaan data, sifat Tree ini cukup sulit untuk difiltrasi ataupun digabungkan.

## Mengatur Konfigurasi
Anda dapat mengaturnya hanya ketika saat membuatnya pertama kali.

![[Docs/Modul Data/Enum/create-new-enum.png]]
Kolom _Strict On Selected_ dapat diubah dengan implikasi seperti berikut:
* Disabled to insert externally : Ketat, EnumData tidak bisa ditambahkan saat pengguna atau Anda melakukan input bebas terhadap Enum ini.
* _Enable to insert externally_ : Tidak ketat, Enum Data bisa ditambahkan oleh pengguna atau Anda saat melakukan input bebas terhadap Enum ini.

## Arti dari “Externally”
Externally artinya sesuatu yang diluar Enum. Saat menentukan sebuah inputan dengan tipe data [[Docs/Tipe Data/EnumData|EnumData]], anda harus memilih header Enum. Input ini dapat muncul dalam [[Docs/Komponen/Table/Pengenalan|Tabel]], komponen dalam [[Docs/Modul Interface]] seperti [[Docs/Modul Interface/Form/Pengenalan|Form]] yang dapat diinput oleh publik.

>[!note]Tips
>Meskipun Enum Data bisa bertambah secara liar, namun atribut Name dalam EnumData tetap tidak dapat terduplikat. Meskipun akan banyak variasi Name yang mirip, Anda dapat menggunakan fitur [[Docs/Modul Data/Enum/EnumData Merge]] agar setiap data yang terelasi dengan EnumData tersebut dapat menjadi satu EnumData.

