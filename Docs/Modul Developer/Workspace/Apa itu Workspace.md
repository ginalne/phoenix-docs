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
| [[Docs/Dasar/Apa itu Komponen?|Komponen]] | Isi folder yang hak aksesnya diatur oleh Workspace. Selengkapnya lihat [[Docs/Dasar/Apa itu Komponen?]]. |
| [[Docs/Modul Developer/Workspace/Component Access]] | Hak akses pada level komponen (header): [[^field|Visible]], [[^field|Add]], [[^field|Update]], [[^field|Delete]]. |
| [[Docs/Modul Developer/Workspace/Data Access|Data Access]] | Hak akses pada level data: [[^field|Add]], [[^field|Update]], [[^field|Delete]]. |
| [[Docs/Modul Developer/Workspace/Function Access]] | Hak akses pada fungsi komponen: [[^field|Merge]], [[^field|Modify Event]], [[^field|View Publish]], [[^field|Publish]]. |
| [[^value/boolean/allow]] / [[^value/boolean/disallow]] | Nilai pengaturan akses. [[^value/boolean/allow]] berarti diizinkan, [[^value/boolean/disallow]] berarti tidak diizinkan. |


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
| [[^field/variable|Variable]], [[^field/enum|Role]], [[^field/table|Employee]], [[^field/tree|Organizational Structures]] | Contoh [[Docs/Dasar/Apa itu Komponen?|Komponen]], setiap komponen memiliki ikon sesuai jenisnya dan informasi datanya di samping nama. Lihat [[Docs/Folder/Apa itu Folder?#Informasi Data]]. |

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
| [[^field|Visible]] | Jika [[^value/boolean/disallow]] pada komponen, komponen tidak tampil di [[Docs/Antarmuka/Pengenalan#Area Manajemen Folder]] dan juga tidak tampil dalam *field*, misalnya saat mengisi Query atau membuat komponen Interface. Jika [[^value/boolean/disallow]] pada folder, folder beserta isinya tidak tampil di [[Docs/Antarmuka/Pengenalan#Area Manajemen Folder]]. |
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

## Praktik Terbaik

- **Atur folder terlebih dahulu** untuk merapikan tampilan di Area Manajemen Folder dan mengatur penambahan komponen, lalu sesuaikan [[^field|Visible]], Data Access, dan Function Access pada setiap komponen.
- **Berikan akses seminimal mungkin** (*least privilege*) sesuai kebutuhan kerja setiap [[Docs/Modul Developer/Group/Apa itu Group|Group]].
- **Gunakan [[^field|Visible]] = [[^value/boolean/disallow]] pada komponen** untuk menutupnya sepenuhnya, termasuk dari pilihan *field* dan Query. Pada folder, [[^field|Visible]] hanya menyembunyikan isinya dari [[Docs/Antarmuka/Pengenalan#Area Manajemen Folder]].
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
.