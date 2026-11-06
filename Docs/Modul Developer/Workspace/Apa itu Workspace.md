---
    status: draft
    title: Apa itu Workspace?
    description: Pengenalan Workspace, komponen modul Developer untuk mengatur komponen yang dapat dilihat, dikelola, dan diubah, serta fungsi di dalamnya, termasuk cara kerja hak akses untuk setiap Group.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="#aaa" viewBox="0 0 16 16">
  <path
    d="M2.5 3.5a.5.5 0 0 1 0-1h11a.5.5 0 0 1 0 1zm2-2a.5.5 0 0 1 0-1h7a.5.5 0 0 1 0 1zM0 13a1.5 1.5 0 0 0 1.5 1.5h13A1.5 1.5 0 0 0 16 13V6a1.5 1.5 0 0 0-1.5-1.5h-13A1.5 1.5 0 0 0 0 6zm1.5.5A.5.5 0 0 1 1 13V6a.5.5 0 0 1 .5-.5h13a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-.5.5z"
  />
</svg>
'
    tree:
      priority: 4
---
# Apa itu Workspace?

>**note** Workspace merupakan salah satu komponen dalam modul [[Docs/Modul Developer/Pengenalan|Developer]] di Phoenix.

Workspace adalah komponen yang dapat digunakan untuk mengatur ruang kerja pengembangan Anda, termasuk komponen apa saja yang dapat dilihat, dikelola, dan diubah, serta fungsi di dalamnya. Akses Workspace ke setiap anggota dikelola melalui [[Docs/Modul Developer/Group/Apa itu Group|Group]].

Dengan Workspace, Anda tidak perlu mengatur hak akses di banyak tempat. Seluruh folder dan komponen tersaji dalam satu halaman kerja berbentuk pohon, dan setiap hak akses cukup ditentukan dengan memilih [[^value/boolean/allow]] atau [[^value/boolean/disallow]]. Pengaturan ini berlaku sampai ke level data, sehingga Anda dapat menerapkan prinsip *least privilege* tanpa harus membuat komponen baru.

Aturan yang sama berlaku untuk komponen di modul [[Docs/Modul Data/Pengenalan|Data]], [[Docs/Modul Interface/Pengenalan|Interface]], [[Docs/Modul Logic/Pengenalan|Logic]], dan [[Docs/Modul Developer/Pengenalan|Developer]], sehingga seluruh tim bekerja dengan satu aturan akses yang konsisten.

## Mengapa Menggunakan Workspace?

- **Akses terpusat.** Seluruh hak akses folder dan komponen diatur dalam satu halaman kerja.
- **Kontrol sampai level data.** Anda dapat menentukan siapa yang boleh menambah, mengubah, atau menghapus data, bukan hanya siapa yang boleh melihat komponen.
- **Berlaku seketika.** Setiap perubahan tersimpan langsung dan langsung berlaku bagi anggota yang sedang membuka Phoenix, tanpa perlu memuat ulang.
- **Aman untuk tim.** Anggota hanya melihat dan mengelola bagian yang memang menjadi tanggung jawabnya.
- **Terhubung dengan Group.** Cukup petakan pengguna ke [[Docs/Modul Developer/Group/Apa itu Group|Group]], maka akses Workspace mengikuti.
- **Beberapa ruang kerja untuk satu tim.** Satu Group dapat memiliki beberapa Workspace, dan anggota dapat [[#Berpindah Workspace|berpindah Workspace]] kapan saja dari Area Manajemen Folder.
- **Satu aturan untuk semua tampilan data.** Komponen [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]], [[Docs/Modul Interface/Kanban/Apa itu Kanban|Kanban]], [[Docs/Modul Interface/Gallery/Apa itu Gallery|Gallery]], dan [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]] mengikuti akses data sumbernya, sehingga data tidak dapat diubah lewat tampilan yang berbeda.
- **Terkendali saat dipublikasikan.** [[^field|Publish]] dan [[^field|View Publish]] dipisahkan, sehingga Anda menentukan siapa saja yang boleh mengubah konfigurasi publikasi dan siapa yang hanya boleh menyalin tautannya.

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[#Cara Kerja Workspace|Workspace]] | Komponen untuk mengatur ruang kerja pengembangan, yaitu komponen yang dapat dilihat, dikelola, dan diubah, serta fungsi di dalamnya. |
| [[#Cara Kerja Workspace|Origin]] | Workspace bawaan utama sekaligus folder paling atas yang dimiliki setiap [[Docs/Inisialisasi/Apa itu Pro|Pro]]. Seluruh hak akses Origin bernilai [[^value/boolean/allow]], dan Origin otomatis terhubung ke Group bawaan [[^field/group|Administrator]]. |
| [[#Cara Kerja Workspace|Root]] | Folder paling atas pada halaman kerja Workspace. Jika komponen Workspace ditempatkan di folder yang lebih dalam, folder itulah yang menjadi root. |
| [[#Berpindah Workspace|Workspace aktif]] | Workspace yang sedang dipakai pengguna. Workspace aktif menentukan struktur folder dan hak akses yang berlaku, serta ditampilkan pada Area Manajemen Folder. |
| [[Docs/Modul Developer/Group/Apa itu Group|Group]] | Kumpulan pengguna yang dipetakan ke Workspace. Pada halaman kerja, Group tampil sebagai baris dengan angka jumlah anggotanya. Setiap Pro memiliki Group bawaan bernama [[^field/group|Administrator]]. |
| [[Docs/Folder/Apa itu Folder?|Folder]] | Wadah yang berisi banyak komponen dan dapat diperluas atau dilipat. |
| [[Docs/Apa itu Komponen?|Komponen]] | Isi folder yang hak aksesnya diatur oleh Workspace. Selengkapnya lihat [[Docs/Apa itu Komponen?]]. |
| [[Docs/Modul Developer/Workspace/Component Access]] | Hak akses pada level komponen (header): [[^field|Visible]], [[^field|Add]], [[^field|Update]], [[^field|Delete]]. |
| [[Docs/Modul Developer/Workspace/Data Access|Data Access]] | Hak akses pada level data: [[^field|Add]], [[^field|Update]], [[^field|Delete]]. |
| [[Docs/Modul Developer/Workspace/Function Access]] | Hak akses pada fungsi komponen: [[^field|Merge]], [[^field|Modify Event]], [[^field|View Publish]], [[^field|Publish]]. |
| [[^value/boolean/allow]] / [[^value/boolean/disallow]] | Nilai pengaturan akses. [[^value/boolean/allow]] berarti diizinkan, [[^value/boolean/disallow]] berarti tidak diizinkan. |

## Cara Kerja Workspace

Ketika komponen Group berhasil memetakan pengguna dengan Workspace, maka Workspace dapat digunakan. Saat pengguna membuka Phoenix, mereka akan masuk ke Workspace yang terakhir dipakai, yang sudah memiliki struktur folder. Jika Group memiliki lebih dari satu Workspace, pengguna dapat [[#Berpindah Workspace|berpindah Workspace]].

```mermaid
flowchart TD
    U["Pengguna"] -->|&nbsp;Anggota&nbsp;| G["Group"]
    G -->|&nbsp;Dipetakan&nbsp;| W["Workspace"]
    W -->|&nbsp;Akses&nbsp;| F["Folder"]
    W -->|&nbsp;Akses&nbsp;| K["Komponen"]
    F -->|&nbsp;Berisi&nbsp;| K
    F -->|&nbsp;Diatur&nbsp;| C["Component Access"]
    K -->|&nbsp;Diatur&nbsp;| C
    K -->|&nbsp;Diatur&nbsp;| D["Data Access"]
    K -.->|&nbsp;Jika ada fungsi&nbsp;| FN["Function Access"]
```

Garis putus-putus menandakan bahwa [[Docs/Modul Developer/Workspace/Function Access|Function Access]] hanya tersedia pada komponen yang memiliki fungsi terkait.

Aturan penting:
- Pengguna hanya dapat memakai Workspace setelah dipetakan melalui [[Docs/Modul Developer/Group/Apa itu Group|Group]].
- Satu pengguna hanya dapat berada di satu [[Docs/Modul Developer/Group/Apa itu Group|Group]], sehingga akses seorang pengguna selalu mengikuti Group tempat ia berada.
- Satu [[Docs/Modul Developer/Group/Apa itu Group|Group]] dapat dipetakan ke lebih dari satu Workspace.
- [[Docs/Modul Developer/Group/Apa itu Group|Group]] anak tidak mewarisi Workspace dari Group induk. Workspace perlu diisi ulang di setiap Group.
- Setiap Pro memiliki satu rangkaian folder yang berawal dari **Origin**. Origin terhubung otomatis ke Group bawaan [[^field/group|Administrator]] dan seluruh hak aksesnya [[^value/boolean/allow]].
- Jika komponen Workspace ditempatkan di folder yang lebih dalam, folder itu menjadi **root** dari Workspace tersebut.
- Menu [[^field|Place to Directory]] pada Group anak menempatkan Group tersebut di root dari Workspace yang aktif saat itu.
- [[^field|Visible]] pada folder menentukan apakah folder beserta isinya tampil di [[Docs/Antarmuka#Area Manajemen Folder]]. Komponen di dalamnya tetap dapat muncul pada pilihan *field* atau Query jika [[^field|Visible]] komponen itu sendiri [[^value/boolean/allow]]. Lihat [[Docs/Modul Developer/Workspace/Component Access#Visible pada Folder dan Komponen|Visible pada Folder dan Komponen]].

## Berpindah Workspace

Jika [[Docs/Modul Developer/Group/Apa itu Group|Group]] Anda memiliki lebih dari satu Workspace, Anda dapat mengganti Workspace yang aktif.

1. Buka [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik tombol yang berisi nama Workspace aktif
3. Pilih Workspace tujuan pada popup yang muncul

Popup menampilkan Workspace yang dipetakan ke Group Anda. Struktur folder dan hak akses yang berlaku mengikuti Workspace yang Anda pilih.

>**note** Workspace aktif saat membuka Phoenix
>Saat Anda membuka Phoenix, Workspace yang aktif adalah Workspace yang terakhir Anda pakai. Jika Workspace tersebut sudah tidak valid, misalnya karena Workspace pada Group Anda berubah, Phoenix otomatis memindahkan Anda ke Workspace pertama pada daftar Workspace di Group.

## Membuat Workspace

1. Buka folder tempat Workspace akan ditempatkan di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan ➜ [[^field/add|Add]] ➜ [[^field|Developer]] ➜ [[^field/workspace|Workspace]]
3. Isi [[^field|Name]] dan [[^field|Description]]
4. Klik [[^button|Create]]

Folder tempat Workspace ditempatkan akan menjadi root dari Workspace tersebut.

>**success** Workspace berhasil dibuat
>Nilai awal hak akses Workspace baru mengikuti Workspace yang sedang aktif saat Workspace dibuat. Jika dibuat dari Origin, seluruh hak aksesnya [[^value/boolean/allow]]. Workspace baru belum dapat dipakai oleh anggota sampai dipetakan ke [[Docs/Modul Developer/Group/Apa itu Group|Group]], jadi periksa dan sesuaikan hak aksesnya di [[#Mengatur Hak Akses]] sebelum memetakannya.

## Mengubah Workspace

1. Buka halaman kerja Workspace
2. Klik [[^button/edit|Edit]]
3. Perbarui isian [[^field|Name]] dan [[^field|Description]]
4. Klik [[^button|Update]]

>**note** Tombol Edit berbeda dengan pengaturan hak akses
>Tombol [[^button/edit|Edit]] hanya mengubah atribut Workspace, yaitu [[^field|Name]] dan [[^field|Description]]. Untuk mengubah hak akses, lihat [[#Mengatur Hak Akses]].

## Menyegarkan

Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.

## Menghapus Workspace

1. Buka folder yang berisi Workspace di [[Docs/Antarmuka#Area Manajemen Folder]]
2. Klik kanan Workspace
3. Pilih [[^button/delete|Delete]]
4. Konfirmasi dengan [[^button|Delete]]

>**warning** Harap pastikan
>Sebelum menghapus pastikan setiap [[Docs/Modul Developer/Group/Apa itu Group|Group]] tetap memiliki Workspace selain daripada yang akan dihapus. Sehingga pengalaman pengguna tetap lancar menggunakan Phoenix.

>**warning** Pengaturan hak akses ikut hilang
>Seluruh pengaturan hak akses pada Workspace ini hilang dan pemetaannya pada [[Docs/Modul Developer/Group/Apa itu Group|Group]] terputus. Komponen dan data di dalam folder tidak ikut terhapus.

>**note** Workspace root terakhir tidak dapat dihapus
>Phoenix mencegah hilangnya akses ke root utama. Workspace di posisi root tidak dapat dihapus jika setelah dihapus tidak ada lagi Workspace di posisi root yang terhubung ke [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Karena itu, Origin tidak dapat dihapus selama belum ada Workspace root lain yang terhubung ke Group.

## Halaman Kerja Workspace

![[Docs/Modul Developer/Workspace/antarmuka-workspace.png]]
Halaman kerja Workspace menampilkan seluruh struktur ruang kerja dalam satu tabel. Kolom paling kiri berisi daftar [[^field|Folder/ Component]], sedangkan kolom di sebelah kanannya berisi hak akses yang dikelompokkan menjadi [[^field|Component Access]], [[^field|Data Access]], dan [[^field|Function Access]].

Bilah navigasi Workspace hanya memiliki dua tombol:

| Tombol | Fungsi |
| --- | --- |
| [[^button/edit|Edit]] | Mengubah atribut Workspace seperti [[^field|Name]] dan [[^field|Description]]. |
| [[^button/refresh|Refresh]] | Memuat ulang halaman kerja. |

### Membaca Baris

| Baris | Penjelasan |
| --- | --- |
| [[^field/workspace|Origin]] | Workspace. Biasanya baris paling atas. |
| [[^field/group|Administrator]] | [[Docs/Modul Developer/Group/Apa itu Group|Group]] yang terhubung ke Workspace. Baris Group hanya mengatur akses dari Workspace ke komponen Group tersebut, bukan akses per anggota. |
| [[^field/folder|Folder]] | Contoh [[Docs/Folder/Apa itu Folder?|Folder]], klik untuk melihat komponen di dalamnya. |
| [[^field/variable|Variable]], [[^field/enum|Role]], [[^field/table|Employee]], [[^field/tree|Organizational Structures]] | Contoh [[Docs/Apa itu Komponen?|Komponen]], setiap komponen memiliki ikon sesuai jenisnya dan informasi datanya di samping nama. Lihat [[Docs/Folder/Apa itu Folder?#Informasi Data]]. |

Sel yang kosong pada kolom hak akses berarti hak akses tersebut tidak relevan untuk komponen itu.

### Interaksi Antarmuka Workspace

| Fungsi | Aksi |
| --- | --- |
| Memperluas atau melipat folder | Klik folder pada kolom [[^field|Folder/ Component]]. |
| Memindahkan folder atau komponen | *Drag and drop* ke posisi tujuan, baik untuk mengubah urutan maupun memindahkannya ke folder lain. Mengubah urutan di dalam folder yang sama tidak memerlukan [[^field|Add]] maupun [[^field|Delete]]. Memindahkan ke folder lain memerlukan [[^field|Delete]] pada folder atau komponen yang dipindahkan, dan [[^field|Add]] pada folder tujuan. Lihat [[Docs/Modul Developer/Workspace/Component Access#Memindahkan Folder atau Komponen|Memindahkan Folder atau Komponen]]. |
| Mengubah hak akses | Klik tombol toggle pada sel di kolom hak akses. Lihat [[#Mengatur Hak Akses]]. |

>**warning** Memindahkan mengubah struktur folder Pro
>Struktur folder Pro dan Workspace saling berkesinambungan. Memindahkan folder atau komponen di halaman kerja Workspace juga mengubah struktur folder Pro.

## Mengatur Hak Akses

Hak akses diatur per baris dan per kolom pada halaman kerja. Setiap sel memiliki tombol toggle bernilai [[^value/boolean/allow]] atau [[^value/boolean/disallow]]. Klik tombol pada sel yang ingin diubah untuk berpindah antara kedua nilai tersebut.

>**warning** Perubahan langsung berlaku
>Setiap perubahan tersimpan langsung dan langsung berlaku bagi anggota yang sedang membuka Phoenix, tanpa perlu memuat ulang. Periksa kembali sebelum mengubah akses pada [[Docs/Modul Developer/Group/Apa itu Group|Group]] yang sedang aktif bekerja.

>**note** Hak akses yang disallow menghilangkan fungsi terkait
>Fungsi yang diatur [[^value/boolean/disallow]] hilang dari antarmuka, misalnya tombol dan menu pada konteks menu. Halaman komponen juga menampilkan ikon kunci di samping nama komponen. Arahkan kursor ke ikon tersebut untuk melihat hak akses apa saja yang diizinkan oleh Workspace. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Component Access#Mengenali Ikon Kunci|Mengenali Ikon Kunci]].

### Component Access

Component Access berlaku pada level komponen (header). Hak akses ini mengatur apakah folder atau komponen tampil, dapat ditambah, diubah, dihapus, dan dipindahkan.

| Hak Akses | Penjelasan |
| --- | --- |
| [[^field|Visible]] | Jika [[^value/boolean/disallow]] pada komponen, komponen tidak tampil di [[Docs/Antarmuka#Area Manajemen Folder]] dan juga tidak tampil dalam *field*, misalnya saat mengisi Query atau membuat komponen Interface. Jika [[^value/boolean/disallow]] pada folder, folder beserta isinya tidak tampil di [[Docs/Antarmuka#Area Manajemen Folder]]. |
| [[^field|Add]] | Mengizinkan penambahan folder atau komponen baru, termasuk menempatkan folder atau komponen dari folder lain. |
| [[^field|Update]] | Mengizinkan perubahan atribut pada folder atau komponen. |
| [[^field|Delete]] | Mengizinkan penghapusan folder atau komponen, termasuk memindahkan folder atau komponen ke folder lain. Pastikan folder tujuan mengizinkan [[^field|Component Access]] [[^field|Add]]. |

Penjelasan lengkap, termasuk aturan [[^field|Visible]] pada folder dan komponen, aturan memindahkan folder atau komponen, dan ikon kunci, lihat [[Docs/Modul Developer/Workspace/Component Access]].

>**warning** Tidak ada pengaman bawaan untuk akses administrator
>Menonaktifkan [[^field|Visible]] atau [[^field|Update]] pada komponen Workspace dan [[Docs/Modul Developer/Group/Apa itu Group|Group]] yang Anda pakai dapat mengunci pengelolaan akses Anda sendiri. Phoenix hanya mencegah penghapusan Workspace root terakhir yang terhubung ke Group, dan tidak memiliki pengaman bawaan untuk pengaturan hak akses. Periksa pengaturan sebelum menonaktifkan akses.

### Data Access

Data Access berlaku pada level data. Jenis datanya bergantung pada komponen: semisal pada [[Docs/Modul Data/Table/Apa itu Table|Table]] datanya adalah [[Docs/Tipe Data/Row]] dan [[Docs/Tipe Data/TableData]], pada [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] datanya adalah [[Docs/Modul Interface/Table View/Table View Data/Pengenalan|Table View Data]], sedangkan pada [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]] datanya adalah [[Docs/Modul Interface/Timeline/Timeline Data/Pengenalan]].

| Hak Akses | Penjelasan |
| --- | --- |
| [[^field|Add]] | Mengizinkan penambahan data. |
| [[^field|Update]] | Mengizinkan perubahan data. |
| [[^field|Delete]] | Mengizinkan penghapusan data. |

Data yang diatur pada setiap komponen, mulai dari Table, Enum, Tree, dan Variable hingga Canvas, Form, dan Space, dijelaskan lengkap di [[Docs/Modul Developer/Workspace/Data Access#Data yang Diatur pada Setiap Komponen|Data Access]].

#### Akses Berlapis pada Komponen Interface

Komponen Interface yang dapat memanipulasi data di komponen Modul Data tidak membuka akses baru. Baris dan isi sel hanya dapat dikelola jika dua syarat berikut terpenuhi:

| Syarat | Penjelasan |
| --- | --- |
| Konfigurasi komponen Interface | Data pada komponen Interface berstatus `editable`, misalnya pada [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] dan [[Docs/Modul Interface/Timeline/Apa itu Timeline|Timeline]]. Data berstatus `readonly` tidak dapat dikelola. |
| Data Access data sumber | Data Access komponen Modul Data sumber, misalnya [[Docs/Modul Data/Table/Apa itu Table|Table]], di Workspace mengizinkan aksi yang dilakukan. |

Jika salah satu syarat tidak terpenuhi, baris dan isi sel tidak dapat dikelola. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Data Access#Akses Berlapis pada Komponen Interface|Akses Berlapis]].

>**note** Visible komponen sumber hanya dibutuhkan saat mengisi Query
>Komponen sumber perlu [[^field|Visible]] [[^value/boolean/allow]] ketika Anda mengisi Query, misalnya pada [[Docs/Modul Interface/Table View/Table View Data/Pengenalan|Table View Data]]. Setelah Query terisi, [[^field|Visible]] pada komponen sumber tidak perlu lagi [[^value/boolean/allow]].

>**note** Mode Edit pada Canvas dan Form
>Pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]] dan [[Docs/Modul Interface/Form/Apa itu Form|Form]], toggle [[^mode/edit|Edit]] hanya dapat dipindahkan jika setidaknya salah satu Data Access ([[^field|Add]], [[^field|Update]], [[^field|Delete]]) bernilai [[^value/boolean/allow]]. Jika ketiganya [[^value/boolean/disallow]], komponen hanya tampil dalam mode [[^mode/view|View]] (*read only*).

### Function Access

Function Access mengatur fungsi tambahan pada komponen. Hak akses ini hanya tersedia pada komponen yang memiliki fungsi terkait.

| Hak Akses | Penjelasan |
| --- | --- |
| [[^field|Merge]] | Mengizinkan penggabungan data. |
| [[^field|Modify Event]] | Mengizinkan perubahan [[Docs/Event/Apa itu Event|Event]] pada komponen. |
| [[^field|View Publish]] | Hanya dapat melihat konfigurasi publikasi, misalnya menyalin atau membuka [[^field|Publish Link]], tanpa mengubah status publikasi. |
| [[^field|Publish]] | Dapat memperbarui konfigurasi publikasi. |

Komponen yang memiliki setiap fungsi, perbedaan View Publish dan Publish, serta peringatan tentang tautan publik dijelaskan lengkap di [[Docs/Modul Developer/Workspace/Function Access]].

## Contoh Penggunaan

**Contoh jika Komponen hanya boleh dilihat**

| Komponen | Visible | Update | Delete | Data Access | Function Access |
| --- | --- | --- | --- | --- | --- |
| [[^field/tree|Pohon Kategori Produk]] | [[^value/boolean/allow]] | [[^value/boolean/disallow]] | [[^value/boolean/disallow]] | [[^value/boolean/disallow]] | [[^value/boolean/disallow]] |

Anggota Group tetap dapat membuka komponen untuk dibaca, tetapi tidak dapat mengubah struktur, data, maupun konfigurasi publikasinya.

**Mengizinkan tim memperbarui data pelanggan tanpa mengubah pengaturan tampilannya**

Tim penjualan perlu menambah dan memperbarui data pelanggan setiap hari, tetapi tidak boleh mengubah Query maupun konfigurasi tampilan, dan tidak boleh menghapus data. Dengan Workspace, kebutuhan ini cukup dipenuhi tanpa membuat komponen baru.

| Komponen | Visible | Update | Data Access | Hasil |
| --- | --- | --- | --- | --- |
| [[^field/tableview|Daftar Pelanggan]] | [[^value/boolean/allow]] | [[^value/boolean/disallow]] | [[^value/boolean/disallow]] | Anggota dapat membuka komponen, tetapi tidak dapat mengubah nama, Query, maupun konfigurasi Data. |
| [[^field/table|Data Pelanggan]] | [[^value/boolean/disallow]] | [[^value/boolean/disallow]] | [[^field|Add]] [[^value/boolean/allow]], [[^field|Update]] [[^value/boolean/allow]], [[^field|Delete]] [[^value/boolean/disallow]] | Anggota tidak dapat membuka Table ini, tetapi tetap dapat menambah dan mengubah Row melalui Daftar Pelanggan, tanpa dapat menghapusnya. |

[[^field|Visible]] pada [[^field/table|Data Pelanggan]] cukup [[^value/boolean/disallow]] karena Query pada [[^field/tableview|Daftar Pelanggan]] sudah terisi. Baris pada [[^field/tableview|Daftar Pelanggan]] hanya dapat dikelola jika Data berstatus `editable` dan Data Access [[^field/table|Data Pelanggan]] mengizinkan. Jika Data berstatus `readonly`, anggota tetap hanya dapat membaca.

**Ide skenario lain**

| Kebutuhan | Pengaturan Workspace |
| --- | --- |
| Anggota baru hanya perlu membaca laporan. | [[^field|Visible]] [[^value/boolean/allow]], Data Access dan Function Access [[^value/boolean/disallow]]. |
| Data keuangan harus benar-benar tertutup bagi Group tertentu. | [[^field|Visible]] [[^value/boolean/disallow]] pada folder dan pada setiap komponen di dalamnya. |
| Tim operasional menjalankan otomasi tanpa perlu mengetahui nilai rahasia. | Komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tidak diberi akses, sehingga [[^field|Value]] tersembunyi tetapi Variable Data tetap dapat dipilih. |
| Tim pemasaran menerbitkan [[Docs/Modul Interface/Form/Apa itu Form|Form]] pendaftaran. | [[^field|Publish]] [[^value/boolean/allow]] hanya pada Form tersebut, sedangkan komponen lain tetap [[^value/boolean/disallow]]. |
| Tim lain hanya perlu menyalin tautan laporan publik. | [[^field|View Publish]] [[^value/boolean/allow]] dan [[^field|Publish]] [[^value/boolean/disallow]]. |
| Tim cabang memerlukan ruang kerja sendiri. | Buat Workspace baru dari Workspace yang aksesnya paling mendekati kebutuhan, sesuaikan, lalu petakan ke Group cabang. |

Dengan satu halaman kerja, setiap tim memperoleh akses yang pas dengan perannya, tanpa menambah komponen atau menduplikasi data.

## Praktik Terbaik

- **Atur folder terlebih dahulu** untuk merapikan tampilan di Area Manajemen Folder dan mengatur penambahan komponen, lalu sesuaikan [[^field|Visible]], Data Access, dan Function Access pada setiap komponen.
- **Berikan akses seminimal mungkin** (*least privilege*) sesuai kebutuhan kerja setiap [[Docs/Modul Developer/Group/Apa itu Group|Group]].
- **Gunakan [[^field|Visible]] = [[^value/boolean/disallow]] pada komponen** untuk menutupnya sepenuhnya, termasuk dari pilihan *field* dan Query. Pada folder, [[^field|Visible]] hanya menyembunyikan isinya dari [[Docs/Antarmuka#Area Manajemen Folder]].
- **Sembunyikan komponen sumber setelah Query terisi**, karena [[^field|Visible]] pada komponen sumber hanya dibutuhkan saat mengisi Query.
- **Pisahkan Function Access** untuk [[^field|Publish]] dan [[^field|View Publish]], sehingga tidak semua anggota dapat mengubah konfigurasi publikasi.
- **Berikan [[^field|Publish]] dengan hati-hati** karena tautan publikasi dapat dibuka publik, terutama pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]] yang memiliki widget Button untuk memicu [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].
- **Periksa dua syarat sekaligus** saat anggota tidak dapat mengubah baris di komponen Interface: Data berstatus `editable` dan [[Docs/Modul Developer/Workspace/Data Access]] komponen sumber bernilai [[^value/boolean/allow]].
- **Pastikan folder tujuan mengizinkan [[^field|Add]]** sebelum memindahkan folder atau komponen ke folder lain, dan ingat bahwa setiap pemindahan mengubah struktur folder Pro.
- **Buat Workspace baru dari Workspace yang tepat**, karena nilai awal hak akses mengikuti Workspace yang sedang aktif. Periksa seluruh sel sebelum memetakannya ke [[Docs/Modul Developer/Group/Apa itu Group|Group]].
- **Isi ulang Workspace di setiap Group**, karena [[Docs/Modul Developer/Group/Apa itu Group|Group]] anak tidak mewarisi Workspace dari Group induk.
- **Jaga akses administrator.** Hindari menonaktifkan [[^field|Visible]] atau [[^field|Update]] pada komponen Workspace dan Group yang dipakai administrator, karena tidak ada pengaman bawaan yang mencegah pengelolaan akses terkunci.
- **Berhati-hati saat mengubah akses Group yang sedang aktif**, karena perubahan langsung berlaku tanpa perlu memuat ulang.
- **Cek hasilnya dengan [[^button/refresh|Refresh]]** setelah mengubah pengaturan akses.

## Batasan dan Catatan

- Akses Workspace untuk setiap anggota dikelola melalui [[Docs/Modul Developer/Group/Apa itu Group|Group]], bukan langsung pada pengguna.
- Satu pengguna hanya dapat berada di satu [[Docs/Modul Developer/Group/Apa itu Group|Group]], dan [[Docs/Modul Developer/Group/Apa itu Group|Group]] anak tidak mewarisi Workspace dari Group induk.
- [[^field|Visible]] tidak saling menurunkan nilai antara folder dan komponen. Folder yang [[^value/boolean/disallow]] hanya membuat isinya tidak tampil di Area Manajemen Folder, sehingga tidak dapat dibuka. Komponen di dalamnya tetap dapat muncul pada pilihan *field* atau Query jika [[^field|Visible]] komponen itu [[^value/boolean/allow]].
- Memindahkan folder atau komponen ke folder lain memerlukan [[^field|Delete]] pada yang dipindahkan dan [[^field|Add]] pada folder tujuan, sedangkan mengubah urutan di dalam folder yang sama tidak memerlukan keduanya. Setiap pemindahan mengubah struktur folder Pro.
- Tombol [[^button/edit|Edit]] hanya mengubah atribut Workspace, bukan hak akses.
- Perubahan hak akses tersimpan langsung dan langsung berlaku bagi anggota yang sedang membuka Phoenix, tanpa perlu memuat ulang.
- Saat membuka Phoenix, pengguna masuk ke Workspace yang terakhir dipakai. Jika Workspace itu sudah tidak valid, pengguna dipindahkan ke Workspace pertama pada daftar Group.
- Nilai awal hak akses Workspace baru mengikuti Workspace yang sedang aktif, sedangkan seluruh hak akses Origin bernilai [[^value/boolean/allow]].
- Workspace di posisi root yang terakhir terhubung ke [[Docs/Modul Developer/Group/Apa itu Group|Group]] tidak dapat dihapus, termasuk Origin.
- Tidak ada pengaman bawaan untuk pengaturan hak akses. Menonaktifkan akses pada komponen Workspace atau Group dapat mengunci pengelolaan akses.
- [[Docs/Modul Developer/Workspace/Data Access]] bergantung pada jenis komponen. Pada komponen Interface yang menampilkan data, pengelolaan baris juga bergantung pada status `editable` dan Data Access data sumber.
- [[^field|Visible]] pada komponen sumber hanya dibutuhkan saat mengisi Query. Setelah Query terisi, komponen sumber tidak perlu lagi [[^value/boolean/allow]].
- Pada [[Docs/Modul Interface/Canvas/Apa itu Canvas|Canvas]] dan [[Docs/Modul Interface/Form/Apa itu Form|Form]], mode [[^mode/edit|Edit]] tidak dapat dipakai jika [[^field|Add]], [[^field|Update]], dan [[^field|Delete]] pada Data Access semuanya [[^value/boolean/disallow]].
- Komponen yang [[^field|Visible]]-nya [[^value/boolean/disallow]] tidak tampil di Area Manajemen Folder maupun dalam *field*, kecuali Variable Data yang tetap dapat dipilih meskipun komponen [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] disembunyikan.
- Pengisi [[Docs/Modul Interface/Form/Apa itu Form|Form]] dan pengunjung tautan publikasi tidak diatur melalui Workspace. Akses mereka ditentukan oleh pembuat komponen saat mempublikasikannya.
- Sel yang kosong pada halaman kerja berarti hak akses tidak relevan untuk komponen tersebut.

## TL:DR

- **Workspace** mengatur komponen yang dapat dilihat, dikelola, dan diubah, serta fungsi di dalamnya.
- Akses anggota dikelola lewat [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Satu pengguna hanya berada di satu Group, Group anak tidak mewarisi Workspace dari Group induk, dan anggota dapat berpindah di antara Workspace milik Group-nya.
- Hak akses terbagi tiga: [[^field|Component Access]], [[^field|Data Access]], dan [[^field|Function Access]], masing-masing bernilai [[^value/boolean/allow]] atau [[^value/boolean/disallow]].
- [[^field|Visible]] pada folder hanya menyembunyikan isinya dari Area Manajemen Folder. Untuk menutup komponen sepenuhnya, atur [[^field|Visible]] pada komponen itu sendiri.
- Komponen Interface mengikuti **dua syarat**: Data berstatus `editable` dan Data Access data sumber bernilai [[^value/boolean/allow]].
- Berhati-hatilah dengan [[^field|Publish]] dan dengan pengaturan akses komponen Workspace dan Group: tautan publikasi dapat dibuka publik, dan tidak ada pengaman bawaan untuk akses yang terkunci.
- Perubahan hak akses langsung berlaku, dan memindahkan folder atau komponen mengubah struktur folder Pro. Halaman kerja Workspace memiliki dua tombol: [[^button/edit|Edit]] dan [[^button/refresh|Refresh]].

## FAQ : Pertanyaan yang Sering Diajukan
>**faq**
>**Bagaimana pengguna dapat memakai Workspace?**
>Pengguna harus dipetakan ke Workspace melalui komponen [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Setelah itu, saat membuka Phoenix mereka akan masuk ke Workspace yang terakhir dipakai.
>**Bagaimana cara berpindah Workspace?**
>Klik tombol yang berisi nama Workspace aktif di [[Docs/Antarmuka#Area Manajemen Folder]], lalu pilih Workspace tujuan pada popup yang muncul. Lihat [[#Berpindah Workspace]].
>**Workspace mana yang aktif saat saya membuka Phoenix?**
>Workspace yang terakhir Anda pakai. Jika Workspace itu sudah tidak valid, Anda otomatis dipindahkan ke Workspace pertama pada daftar Workspace di Group.
>**Apakah satu pengguna dapat berada di lebih dari satu Group?**
>Tidak. Satu pengguna hanya dapat berada di satu [[Docs/Modul Developer/Group/Apa itu Group|Group]], sehingga akses Workspace-nya mengikuti Group tersebut.
>**Apakah Group anak otomatis memakai Workspace milik Group induk?**
>Tidak. [[Docs/Modul Developer/Group/Apa itu Group|Group]] anak tidak mewarisi Workspace dari Group induk, sehingga Workspace perlu diisi ulang di setiap Group.
>**Apa nilai awal hak akses pada Workspace baru?**
>Nilai awal mengikuti Workspace yang sedang aktif saat Workspace dibuat. Origin, sebagai Workspace pertama, seluruh hak aksesnya [[^value/boolean/allow]].
>**Apakah Origin dapat dihapus?**
>Origin tidak dapat dihapus selama belum ada Workspace lain di posisi root yang terhubung ke [[Docs/Modul Developer/Group/Apa itu Group|Group]]. Ini untuk mencegah hilangnya akses ke root utama.
>**Apakah perubahan hak akses perlu disimpan atau dimuat ulang oleh anggota?**
>Tidak. Perubahan tersimpan langsung dan langsung berlaku bagi anggota yang sedang membuka Phoenix.
>**Apa yang terjadi jika folder diatur disallow tetapi komponen di dalamnya allow?**
>Komponen tidak dapat dibuka karena folder induknya tidak tampil di Area Manajemen Folder. Namun komponen itu tetap dapat muncul pada pilihan *field* atau Query.
>**Bagaimana cara menyembunyikan komponen sepenuhnya?**
>Atur [[^field|Visible]] pada komponen itu sendiri menjadi [[^value/boolean/disallow]], bukan hanya pada folder induknya.
>**Hak akses apa yang dibutuhkan untuk memindahkan folder atau komponen?**
>Untuk memindahkan ke folder lain, diperlukan [[^field|Delete]] pada folder atau komponen yang dipindahkan, dan [[^field|Add]] pada folder tujuan. Mengubah urutan di dalam folder yang sama tidak memerlukan [[^field|Add]] maupun [[^field|Delete]]. Pemindahan juga mengubah struktur folder Pro, bukan hanya tampilan halaman kerja Workspace.
>**Apa bedanya Component Access dan Data Access?**
>[[^field|Component Access]] mengatur komponen secara keseluruhan (header), sedangkan [[^field|Data Access]] mengatur data di dalam komponen, misalnya [[Docs/Tipe Data/Row]] pada [[Docs/Modul Data/Table/Apa itu Table|Table]]. Selengkapnya lihat [[Docs/Modul Developer/Workspace/Data Access]].
>**Apa arti Visible = disallow?**
>Pada komponen, komponen tidak tampil di Area Manajemen Folder dan tidak tampil dalam *field*, termasuk saat mengisi Query atau membuat komponen Interface. Pada folder, folder beserta isinya tidak tampil di Area Manajemen Folder.
>**Mengapa anggota tidak dapat mengubah baris di Table View padahal Data Access sudah allow?**
>Pengelolaan baris memerlukan dua syarat: Data pada [[Docs/Modul Interface/Table View/Apa itu Table View|Table View]] berstatus `editable` dan [[Docs/Modul Developer/Workspace/Data Access]] komponen sumber mengizinkan. Jika salah satunya tidak terpenuhi, baris tidak dapat dikelola.
>**Apakah komponen sumber harus Visible agar Table View dapat menampilkan datanya?**
>Tidak selalu. Komponen sumber hanya perlu [[^field|Visible]] [[^value/boolean/allow]] ketika Query diisi. Setelah Query terisi, [[^field|Visible]] tidak perlu lagi [[^value/boolean/allow]].
>**Apakah Variable Data tetap dapat dipilih jika komponen Variable disembunyikan?**
>Ya. Anggota tanpa akses ke [[Docs/Modul Data/Variable/Apa itu Variable|Variable]] tidak dapat membuka halamannya dan tidak dapat mengetahui [[^field|Value]], tetapi daftar Variable Data tetap dapat dipilih dan dipakai untuk otomasi atau integrasi.
>**Apa bedanya View Publish dan Publish?**
>[[^field|View Publish]] hanya untuk melihat konfigurasi publikasi, misalnya menyalin [[^field|Publish Link]]. [[^field|Publish]] dapat memperbarui konfigurasi publikasi.
>**Apa arti sel yang kosong pada halaman kerja?**
>Hak akses tersebut tidak relevan untuk komponen yang bersangkutan.
>**Apakah tombol Edit dapat dipakai untuk mengubah hak akses?**
>Tidak. Tombol [[^button/edit|Edit]] hanya mengubah [[^field|Name]] dan [[^field|Description]] Workspace. Hak akses diatur dengan tombol toggle pada sel di halaman kerja.
>**Apakah pengisi Form atau pengunjung tautan publikasi perlu diatur di Workspace?**
>Tidak. Akses mereka tidak dibatasi Workspace dan ditentukan oleh pembuat komponen saat mempublikasikannya, sehingga [[^field|Publish]] sebaiknya hanya diberikan kepada [[Docs/Modul Developer/Group/Apa itu Group|Group]] yang tepercaya.
>**Apakah ada pengaman jika saya tidak sengaja mengunci akses administrator?**
>Tidak ada pengaman bawaan untuk pengaturan hak akses. Phoenix hanya mencegah penghapusan Workspace root terakhir yang terhubung ke Group. Karena itu, periksa pengaturan sebelum menonaktifkan akses pada komponen Workspace dan Group.
>**Tombol apa saja yang tersedia pada bilah navigasi Workspace?**
>Hanya [[^button/edit|Edit]] dan [[^button/refresh|Refresh]].