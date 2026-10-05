---
    status: release
    title: Apa itu Group?
    description:
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
  <path d="M15 14s1 0 1-1-1-4-5-4-5 3-5 4 1 1 1 1zm-7.978-1L7 12.996c.001-.264.167-1.03.76-1.72C8.312 10.629 9.282 10 11 10c1.717 0 2.687.63 3.24 1.276.593.69.758 1.457.76 1.72l-.008.002-.014.002zM11 7a2 2 0 1 0 0-4 2 2 0 0 0 0 4m3-2a3 3 0 1 1-6 0 3 3 0 0 1 6 0M6.936 9.28a6 6 0 0 0-1.23-.247A7 7 0 0 0 5 9c-4 0-5 3-5 4q0 1 1 1h4.216A2.24 2.24 0 0 1 5 13c0-1.01.377-2.042 1.09-2.904.243-.294.526-.569.846-.816M4.92 10A5.5 5.5 0 0 0 4 13H1c0-.26.164-1.03.76-1.724.545-.636 1.492-1.256 3.16-1.275ZM1.5 5.5a3 3 0 1 1 6 0 3 3 0 0 1-6 0m3-2a2 2 0 1 0 0 4 2 2 0 0 0 0-4"/>
</svg>'
      tree:
        priority: 4
---
# # Apa itu Group?

>**note** _Group_ merupakan salah satu komponen dalam modul [[Docs/Modul Developer/Pengenalan|Developer]] di Phoenix.

Group merupakan komponen yang dapat digunakan untuk mengatur komposisi tim Anda serta akses [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] yang diberikan kepada setiap anggota.

Alih-alih mengatur akses satu per satu untuk setiap orang, Anda cukup mengelompokkan anggota ke dalam Group, lalu menentukan Workspace apa saja yang dapat diakses oleh Group tersebut.

## Mengapa Menggunakan Group?

- **Pengaturan akses lebih cepat.** Cukup atur sekali untuk satu Group, dan seluruh anggotanya otomatis mengikuti.
- **Konsisten.** Anggota dengan peran yang sama memiliki hak akses yang sama, sehingga mengurangi kesalahan konfigurasi.
- **Mudah dikelola saat tim berubah.** Anggota baru tinggal dimasukkan ke Group yang sesuai, dan anggota yang keluar cukup dikeluarkan dari Group.
- **Lebih aman.** Setiap anggota hanya mendapatkan akses sesuai kebutuhan kerjanya.

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| **Group** | Kumpulan anggota tim yang berbagi hak akses yang sama. |
| **Anggota** | Pengguna yang tergabung di dalam satu Group. |
| **Workspace** | Ruang kerja yang aksesnya diatur melalui komponen [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]]. |

## Cara Kerja Group

Akses seorang anggota ke sebuah Workspace ditentukan oleh Group tempat ia bergabung.

```mermaid
flowchart LR
    A[Anggota] --> B[Group]
    B --> C[Workspace]
    C --> D[Hak Akses]
```

Anggota hanya boleh tergabung dalam satu Group, akses yang dimilikinya merupakan gabungan dari seluruh Workspace dalam Group tersebut.

## Membuat Group
1. Klik kanan pada [[Docs/Antarmuka#Area Manajemen Folder]].
2. Pilih [[field/add|Add]] > [[field|Developer]] > [[field/group| Group]]
3. Isi [[field|Name]] dan [[field|Description]] Group.
4. Tambahkan anggota ke dalam Group dengan cara *drag and drop*.
5. Isi [[field|Search workspace to add...]]  dan pilih Workspace yang ingin ditambahkan.

## Mengelola Anggota

Anda dapat mengatur komposisi tim di dalam Group dengan cara memindahkan anggota dari satu Group ke Group lain.

## Mengatur Akses Workspace

Setiap Group dapat diberikan akses ke satu atau beberapa Workspace.

## Contoh Penggunaan

| Group | Anggota | Akses |
| --- | --- | --- |
| Admin | Administrator | Workspace pengembangan, antarmuka dan data
| Engineering | Para pengembang | Workspace pengembangan |
| Design | Para desainer | Workspace antarmuka |
| Analytics | Para analis | Workspace data |

Dengan pembagian ini, setiap tim hanya bekerja di Workspace yang relevan, dan penambahan anggota baru cukup dilakukan dengan memasukkannya ke Group yang sesuai.

## Praktik Terbaik

- Buat Group berdasarkan **peran atau fungsi tim**, bukan berdasarkan nama individu.
- Berikan akses **seminimal yang dibutuhkan** (prinsip *least privilege*).
- Gunakan **nama Group yang jelas dan konsisten**, misalnya “Engineering” atau “Analytics”.
- **Tinjau keanggotaan secara berkala**, terutama saat ada perubahan tim.

## Batasan dan Catatan

- Perubahan pada Group berlaku untuk seluruh anggotanya.
- Menghapus Group akan mencabut akses yang diberikan melalui Group tersebut, namun setiap anggota harus dipindahkan ke Group lain terlebih dahulu.
- Group hanya mengatur akses anggota ke Workspace.

## FAQ : Pertanyaan yang Sering Diajukan
>**FAQ** 
>**Apakah satu anggota dapat tergabung di lebih dari satu Group?**
>Tidak. Akses yang dimiliki anggota akan sesuai dengan Group-nya.
>**Apa yang terjadi jika anggota dikeluarkan dari Group?**
>Anggota tersebut kehilangan akses Workspace yang diberikan melalui Group itu.
>**Apakah sebuah Workspace dapat diakses oleh banyak Group?**
>Ya. Satu Workspace dapat diberikan kepada beberapa Group.
>**Siapa yang dapat membuat dan mengelola Group?**
>Pengguna dengan kewenangan pengelolaan di modul Developer.

