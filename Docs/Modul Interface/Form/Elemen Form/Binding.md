---
    status: release
    title: "Binding dalam Form"
    description:  Penjelasan tentang binding dalam komponen Form
    pageDecoration:
      tree:
        priority: 4
    tags:
      draft
---
# Binding dalam Form

>**note** Binding merupakan bagian dari [[Docs/Modul Interface/Form/Apa itu Form#Properties Panel|Properties Panel]] pada Elemen di komponen [[Docs/Modul Interface/Form/Apa itu Form|Form]], salah satu komponen dalam modul [[Docs/Modul Interface/Pengenalan|Interface]] di Phoenix.

Binding adalah ikatan berjenjang yang menghubungkan Elemen dengan data. Tujuannya agar isian pengguna dan hasil akhirnya tersimpan pada [[Docs/Tipe Data/Row]] dan relasi yang tepat di [[Docs/Modul Data/Table/Apa itu Table|Table]].

Setiap Elemen Layout memiliki [[^field|Type]] Binding berupa [[^value/radio|table]] dan [[^value/radio|pivot]]. Artinya, Layout tersebut ditentukan sebagai header bagi Elemen di bawahnya.

| Type | Fungsi |
| --- | --- |
| [[^value/radio|table]] | Memilih [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai header Layout. |
| [[^value/radio|pivot]] | Dipakai pada Layout anak bila Layout induknya sudah memiliki Table. Pivot menjadi relasi lanjutan dari Table tersebut. |

>**note** Pilihan pivot bisa kosong
> Table pada header harus memiliki pivot dengan Table lain. Jika tidak ada, pilihan pada pivot akan kosong.

Setiap Elemen Input memiliki [[^field|Type]] Binding berupa [[^value/radio|column]] dan [[^value/radio|pivot]]. Artinya, Layout tersebut ditentukan sebagai header bagi Elemen di bawahnya.

| Type | Fungsi |
| --- | --- |
| [[^value/radio|table]] | Memilih [[Docs/Modul Data/Table/Apa itu Table|Table]] sebagai header Layout. |
| [[^value/radio|pivot]] | Dipakai pada Layout anak bila Layout induknya sudah memiliki Table. Pivot menjadi relasi lanjutan dari Table tersebut. |

>**note** Pilihan pivot bisa kosong
> Table pada header harus memiliki pivot dengan Table lain. Jika tidak ada, pilihan pada pivot akan kosong.

Secara umum, urutannya seperti ini:

1. Layout paling atas diikat ke [[Docs/Modul Data/Table/Apa itu Table|Table]] sumber datanya lewat Type [[^value/radio|table]].
2. Elemen Input di dalamnya diikat ke [[Docs/Tipe Data/Column]] pada Table tersebut, sehingga setiap *field* tahu ke kolom mana isiannya disimpan.
3. Layout anak yang mewakili data turunan diikat lewat Type [[^value/radio|pivot]] sebagai relasi lanjutan dari Table pada Layout induknya.

Informasi Binding dapat dilihat di [[#Mode View dan Edit Mode|Edit Mode]] sebagai label pada Elemen. Klik kiri Elemen untuk memfokuskannya dan melihat pengaturan [[^field|Binding]] pada [[#Properties Panel]]. Selengkapnya lihat [[Docs/Modul Interface/Form/Layout/Card/Penjelasan#Binding Card|Binding Card]].
