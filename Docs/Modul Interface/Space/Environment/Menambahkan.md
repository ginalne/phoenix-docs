---
    status: release
    title: "Menambahkan Environment"
    description: 
    pageDecoration: 
      tree: 
        priority: 0 
---
# Menambahkan Environment

1. Buka halaman kerja Space
2. Klik kanan pada [[#Antarmuka Space|Outliner]] ➜ [[^field/add|Add Environment]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Upload file 3D pada [[^field|Model]]
5. Atur [[^field|Position]], [[^field|Scale]], dan [[^field|Rotation]]

## Mengatur Model Attribute

Ketika [[^field|Query]] sudah diisi, tabel [[^field|Model Attribute]] akan tampil dengan kolom [[^field|Key]], [[^field|Static]], dan [[^field|Value]]. Kolom [[^field|Static]] berisi pilihan radio yang menentukan cara nilai atribut diisi:

| Pilihan | Value yang diisi | Hasil pada objek 3D |
| --- | --- | --- |
| [[^value/radio|static]] | Nilai bebas sesuai kebutuhan. | Seluruh objek 3D yang dirender memiliki nilai atribut yang sama. |
| [[^value/radio|bind]] | Kolom yang tersedia pada [[Docs/Tipe Data/Query|Query]]. | Nilai atribut tiap objek 3D mengikuti [[Docs/Tipe Data/Row]] masing-masing. |

Perlu diketahui bahwa Query dapat memanggil banyak data. Jika atribut bernilai [[^value/radio|static]], semua objek 3D yang dirender akan memiliki nilai atribut yang sama, sedangkan atribut [[^value/radio|bind]] dapat berbeda pada setiap objek 3D.