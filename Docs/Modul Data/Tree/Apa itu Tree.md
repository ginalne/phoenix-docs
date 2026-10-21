---
    status: release
    title: Apa itu Tree?
    description: Tree adalah komponen modul Data untuk menyimpan data berhierarki berbentuk pohon yang terdiri dari banyak Node.
    pageDecoration:
      icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="#aaa" version="1.1"width="16" height="16" viewBox="0 0 512 512">
  	<path class="st0" d="M440.781,203.438c1.188-6.375,1.781-12.781,1.781-19.125c0-45.875-29.094-85.984-71.813-100.625   C354.859,33.969,308.953,0,256,0s-98.875,33.969-114.75,83.688c-42.734,14.625-71.813,54.75-71.813,100.625   c0,6.344,0.594,12.75,1.766,19.125c-24.813,22.813-38.844,54.547-38.844,88.531c0,66.516,54.109,120.625,120.625,120.625   c13.219,0,26.125-2.125,38.531-6.313c14.422,10.219,31.078,16.828,48.484,19.359V512h8h16h8v-86.359   c17.406-2.531,34.063-9.141,48.484-19.359c12.391,4.188,25.313,6.313,38.531,6.313c66.516,0,120.625-54.109,120.625-120.625   C479.641,257.984,465.594,226.25,440.781,203.438z M359.016,380.594c-12.094,0-23.828-2.406-34.922-7.156L315,369.531l-7.563,6.406   c-12.313,10.438-27.516,16.844-43.438,18.469v-41.875l62.547-71.469L314.5,270.531L264,328.25v-58.938l50.438-57.656   l-12.047-10.531L264,245v-90.344h-16v90.359l-38.406-43.891l-12.047,10.531L248,269.313v58.938l-50.5-57.719l-12.047,10.531   L248,352.531v41.875c-15.938-1.625-31.125-8.031-43.453-18.469L197,369.531l-9.109,3.906c-11.078,4.75-22.828,7.156-34.906,7.156   c-48.875,0-88.625-39.75-88.625-88.625c0-27.516,12.563-53.031,34.453-70l8.563-6.656l-2.984-10.406   c-1.969-6.844-2.953-13.781-2.953-20.594c0-34.344,23.297-64.063,56.656-72.266l9.5-2.344l2.25-9.516   C179.344,60.031,214.766,32,256,32s76.656,28.031,86.141,68.188l2.25,9.516l9.5,2.344c33.359,8.203,56.672,37.922,56.672,72.266   c0,6.813-1,13.75-2.969,20.594l-2.984,10.406l8.563,6.656c21.906,16.969,34.469,42.484,34.469,70   C447.641,340.844,407.875,380.594,359.016,380.594z"/>
  </svg>
  '
      tree:
        priority: 4
---
# Apa itu Tree?

>**note** Tree merupakan salah satu komponen dalam modul [[Docs/Modul Data/Pengenalan|Data]] di Phoenix.

Tree adalah komponen yang dapat menyimpan data secara hierarki atau berbentuk pohon. Sifat data ini cocok untuk menyimpan data relasional yang bercabang, seperti kategori dan subkategori atau struktur bertingkat lainnya. Satu Tree dapat memiliki banyak [[Docs/Tipe Data/Node]]. Salah satu atribut penting dalam Tree adalah [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]].

Tree juga dapat dijadikan bersifat Merger. Dengan Merger Mode, satu Tree dapat memanggil Node dari beberapa Tree lain, lalu menambahkannya sebagai *clone* tanpa Anda perlu menyalin Node satu per satu. Anda juga dapat mengatur apakah atribut Node ikut berubah ketika Node asalnya diperbarui lewat [[#External Read Only]].

## Mengapa Menggunakan Tree?

- **Data bercabang tersimpan rapi.** Hubungan induk dan anak antar data tergambar langsung dalam bentuk pohon.
- **Satu Tree, banyak Node.** Anda dapat menambahkan Node sebanyak yang dibutuhkan dan menyusunnya bertingkat.
- **Menggabungkan Node dari banyak Tree.** Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] menghimpun Node dari Tree lain dalam satu tempat.
- **Perubahan terkendali.** [[#External Read Only]] menentukan atribut Node mana yang boleh ikut berubah dari Tree lain.
- **Tampilan mudah disesuaikan.** Pohon dapat ditampilkan secara horizontal atau vertikal, dan cabangnya dapat dilipat atau dibuka.
- **Terhubung dengan komponen lain.** Tree dapat dipublikasikan dan dihubungkan ke Event untuk otomasi di [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[Docs/Tipe Data/Node]] | Satu simpul data di dalam Tree. Node memiliki atribut [[^field|Order]] dan [[^field|Name]], serta dapat memiliki anak. |
| [[#Membuat Tree|Origin]] | Node pertama yang otomatis dibuat ketika Tree baru dibuat. |
| [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]] | Atribut yang menentukan apakah Tree dapat menambahkan (*clone*) Node dari Tree lain. |
| [[#External Read Only]] | Pengaturan yang menentukan apakah [[^field|Order]], [[^field|Name]], dan [[^field|Children]] Node ikut berubah ketika Node di Tree lain diperbarui. |
| [[#Default Configuration|Mode]] | Arah tampilan pohon, yaitu horizontal (kiri ke kanan) atau vertikal (atas ke bawah). |
| [[#Default Configuration|Context]] | Status yang berlaku ketika Anda membuka menu konteks Node. |
| [[#Menu Konteks Node]] | Menu yang muncul ketika Anda klik kanan pada Node, berisi aksi untuk Node tersebut dan pengaturan tampilan cabangnya. |

## Cara Kerja

Penjelasan cara kerja Table View lihat selengkap nya di [[Docs/Modul Interface/Table View/Cara Kerja|Cara Kerja Table View]].

## Mengelola Table View

Berikut adalah halaman yang menjelaskan cara untuk mengelola Table View:
1. [[Docs/Modul Interface/Table View/Membuat Baru]] Tree dalam halaman kerja.
2. [[Docs/Modul Interface/Table View/Mengubah]] Atribut Tree seperti [[^field|Name]], [[^field|Description]].
3. [[Docs/Modul Interface/Table View/Menghapus]] Table View.
4. [[Docs/Modul Interface/Table View/Table View Data|Mengelola Data]] Table View seperti menambahkan, mengubah atau memperbarui Data.

## Membuat Tree

### External Read Only

External Read Only mengatur perubahan nilai pada atribut Node kloningan yang aksinya berasal bersumber dari Tree lain.

Selengkapnya lihat [[Docs/Modul Data/Tree/Konfigurasi External Read Only]].

### Default Configuration

| Isian | Fungsi |
| --- | --- |
| [[^field|Horizontal Mode]] | Menentukan arah tampilan pohon. Jika aktif, pohon berakar dari kiri ke kanan (horizontal). Jika tidak aktif, pohon berakar dari atas ke bawah (vertikal). |
| [[^field|Context]] | Menentukan status ketika Anda membuka menu konteks Node. Pilihannya: [[^field|Menu]], [[^field|Edit]], dan [[^field|Detail]]. Bawaan: [[^field|Menu]]. |

Untuk pilihan [[^field|Context]]:

| Pilihan | Hasil ketika menu konteks Node dibuka |
| --- | --- |
| [[^field|Menu]] | Menampilkan [[#Menu Konteks Node]]. |
| [[^field|Edit]] | Membuka pengelolaan ubah Node. |
| [[^field|Detail]] | Membuka detail Node. |

Kedua isian ini hanya nilai awal. Di halaman kerja, Anda dapat mengganti mode dan context secara sementara (lihat [[#Interaksi Antarmuka Tree]]). Untuk mengubah nilai awalnya, gunakan [[^button/edit|Edit]].

## Mengubah Tree
## Menyegarkan Tree

Klik [[^button/refresh|Refresh]] untuk memuat ulang tampilan.

## Menghapus Tree

1. Buka folder yang berisi Tree
2. Klik kanan Tree, pilih [[^button/delete|Delete]]
3. Konfirmasi dengan [[^button|Delete]]

>**warning** Dampak penghapusan Tree
> Seluruh [[Docs/Tipe Data/Node]] di dalam Tree ikut terhapus. Relasi dari komponen lain yang memakai Tree ini akan terputus, misalnya [[Docs/Tipe Data/Column]] pada Table yang memakai [[Docs/Tipe Data/Node]] dari Tree ini dan [[Docs/Modul Logic/Flow/Flow Block/Pengenalan|Flow Block]] seperti [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event]]. Jika Tree ini menjadi sumber *clone* bagi Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]], Node hasil *clone* di Tree tersebut dapat terdampak.

## Antarmuka Tree

![[Docs/Modul Data/Tree/antarmuka-tree.png]]
Halaman kerja Tree terdiri dari bilah navigasi di bagian atas dan area kerja di bagian bawah yang menampilkan pohon beserta Node-nya. Di sudut bawah area kerja terdapat informasi [[^field|context _]], [[^field|mode _]], koordinat [[^field|x _ y _]], dan [[^field|scale _]].

### Bilah navigasi Tree terdiri dari:

| Elemen | Fungsi |
| --- | --- |
| Judul Tree | Menampilkan ikon Tree dan nama Tree. |
| [[^button/edit|Edit]] | Mengubah atribut Tree. Lihat [[#Mengubah Tree]]. |
| [[^button/publish|Publish]] | Mengatur publikasi Tree. Lihat [[Docs/Modul Data/Tree/Publish]]. |
| [[^button/event|Event]] | Menghubungkan Tree dengan Event. Lihat [[Docs/Modul Data/Tree/Event]]. |
| [[^button/refresh|Refresh]] | Memuat ulang tampilan. Lihat [[#Menyegarkan Tree]]. |
| [[^field|Search Tree Data...]] | Mencari Node berdasarkan [[^field|Name]]. Pencarian tidak mencakup atribut Node yang lain. |

### Informasi Area Kerja

| Informasi | Penjelasan |
| --- | --- |
| [[^field|context _]] | Nilai [[#Default Configuration|Context]] yang sedang berlaku. Klik untuk menggantinya. |
| [[^field|mode _]] | Arah tampilan pohon, yaitu Horizontal atau Vertical. Klik untuk menggantinya. Lihat [[#Default Configuration|Mode]]. |
| [[^field|x _ y _]] | Koordinat posisi tampilan pada area kerja. |
| [[^field|scale _]] | Skala tampilan pada area kerja. |

### Interaksi Antarmuka Tree

| Fungsi | Aksi |
| --- | --- |
| Menggeser tampilan (*pan*) | Tekan dan tahan pada bagian yang kosong dalam halaman kerja, lalu gerakkan kursor. Lepas untuk selesai. |
| Mengubah skala tampilan (*zoom*) | Gulir pada bagian halaman kerja. |
| Memusatkan tampilan | Klik informasi koordinat [[^field|x _ y _]]. Tampilan kembali ke tengah. |
| Mengembalikan skala | Klik informasi [[^field|scale _]]. Tampilan kembali berskala 1. |
| Mengganti mode | Klik informasi [[^field|mode _]]. Perubahan bersifat sementara. |
| Mengganti context | Klik informasi [[^field|context _]]. Perubahan bersifat sementara. |
| Membuka menu konteks Node | Klik kanan pada Node. Hasilnya mengikuti nilai [[^field|context _]]. |

### Menu Konteks Node

![[Docs/Modul Data/Tree/node-menu.png]]
Klik kanan pada Node untuk membuka menu konteks berikut.

| Menu | Fungsi |
| --- | --- |
| [[^field/edit|Edit]] | Mengubah Node. Lihat [[Docs/Modul Data/Tree/Mengelola Node#Mengubah Node]]. |
| [[^field/eye|Detail]] | Melihat detail Node. Lihat [[Docs/Modul Data/Tree/Mengelola Node#Melihat Detail Node]]. |
| [[^field/collapse|Collapse]] atau [[^field/expand|Expand]] | Melipat atau memperluas keturunan selanjutnya dari Node. |
| [[^field|View]] | Membuka submenu pengaturan tampilan keturunan Node (lihat tabel di bawah). |
| [[^field/import|Import]] | Memasukkan data ke Node. Lihat [[Docs/Modul Data/Tree/Import Node]]. |
| [[^field/export|Export]] | Mengeluarkan data dari Node. Lihat [[Docs/Modul Data/Tree/Mengelola Node#Export Node]]. |

Submenu [[^field|View]]:

| Menu | Fungsi |
| --- | --- |
| [[^field/collapse|Collapse Below Level]] | Melipat keturunan pada level Node ini (semua Node). |
| [[^field/expand|Expand Children Only]] | Memperluas hanya satu keturunan di bawahnya. |
| [[^field/collapse|Collapse Descendant]] | Melipat semua keturunan secara *recursive*. |
| [[^field/expand|Expand Descendant]] | Membuka semua keturunan secara *recursive*. |
| [[^field|Hide Collapsed]] | Menyembunyikan anak yang dilipat. |
| [[^field|Show Collapsed]] | Memunculkan anak yang dilipat. |
| [[^field/collapse|Collapse and Hide]] | Melipat sekaligus menyembunyikan anak yang dilipat. |

>**note** Node tanpa anak
> Jika Node tidak memiliki anak, pilihan [[^field|Expand]] atau [[^field|Collapse]] dan [[^field|Expand Children Only]] berubah menjadi [[^field|No children...]].

## Mengelola Node

Halaman kerja Tree adalah untuk mengelola [[Docs/Tipe Data/Node]], mulai dari menambahkan, mengubah atribut, melihat detail, menghapus, hingga mengimpor dan mengekspor. Sebagian aksi tersedia di [[#Menu Konteks Node]]. Langkah rinci ada di [[Docs/Modul Data/Tree/Mengelola Node]].

## Mengatur Tree

Pelajari fitur pendukung Tree di halaman berikut:

- [[Docs/Modul Data/Tree/Konfigurasi Merger Mode]]: menggabungkan Node dari beberapa Tree.
- [[Docs/Modul Data/Tree/Konfigurasi External Read Only]]: mengatur atribut Node yang ikut berubah dari Tree lain.
- [[Docs/Modul Data/Tree/Publish]]: mengatur publikasi Tree.
- [[Docs/Modul Data/Tree/Event]]: menghubungkan Tree dengan Event.

## Contoh Penggunaan

**Katalog Kategori Terpadu dari Beberapa Divisi**

Setiap divisi menyusun kategori produknya sendiri dalam bentuk pohon, tetapi tim pusat membutuhkan satu katalog terpadu untuk dipakai laporan dan sistem lain. Dengan Tree, setiap divisi tetap mengelola [[Docs/Tipe Data/Node]]-nya sendiri, sementara satu Tree penggabung menghimpun semuanya tanpa menyalin ulang secara manual. Ketika katalog terpadu berubah, sistem lain langsung menerima perubahannya.

**Komponen yang terlibat**

| Komponen | Peran |
| --- | --- |
| [[^field/tree|Tree Divisi A]] | Tree non-merger yang menyimpan kategori milik divisi pertama. |
| [[^field/tree|Tree Divisi B]] | Tree non-merger yang menyimpan kategori milik divisi kedua. |
| [[^field/tree|Katalog Terpadu]] | Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] yang menambahkan (*clone*) Node dari kedua Tree divisi. |
| [[^field/flow|Sinkronisasi Katalog]] | [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]] yang meneruskan perubahan katalog ke sistem lain. |

**Alur di Flow**

```mermaid
flowchart LR
    A@{ shape: database, label: "**Tree**<br/>Katalog Terpadu" } -.->|&nbsp;Node Berubah&nbsp;| B@{ shape: rounded, label: "**Tree Node Event**" }-->|"&nbsp;**[Node]**&nbsp;"| C@{ shape: rounded, label: "**Node Parse**" }-->|"&nbsp;**[Object]**&nbsp;"| D@{ shape: rounded, label: "**HTTP Request**" } --> E@{ shape: processes, label: "Sistem lain<br/>menerima data" } --> F@{ shape: circle, label: "Selesai" }
```

| Langkah | Flow Block | Peran dalam alur | Hasil |
| --- | --- | --- | --- |
| 1 | [[Docs/Modul Logic/Flow/Flow Block/Event/Tree Node Event|Tree Node Event]] | Memicu alur ketika Node pada Tree terpadu berubah. | Node yang berubah. |
| 2 | [[Docs/Modul Logic/Flow/Flow Block/Operator/Node Parse|Node Parse]] | Mengurai Node menjadi data yang dapat dikirim. | Data Node yang siap dikirim. |
| 3 | [[Docs/Modul Logic/Flow/Flow Block/Modular/HTTP Request|HTTP Request]] | Mengirim data ke sistem lain. | Sistem lain menerima katalog terbaru. |

**Hasil yang dirasakan**

- Setiap divisi tetap bebas mengelola kategorinya sendiri, tanpa mengubah Tree divisi lain.
- Tim pusat memiliki satu katalog terpadu yang tidak perlu disusun ulang secara manual.
- Sistem lain selalu menerima kategori terbaru tanpa proses kirim manual.

**Ide skenario lain**

| Jenis nilai | Contoh integrasi |
| --- | --- |
| Struktur organisasi lintas cabang | Tree penggabung menghimpun struktur tiap cabang, lalu [[Docs/Modul Data/Tree/Publish|Publish]] membagikannya ke pihak yang membutuhkan. |
| Hierarki kategori produk | [[Docs/Modul Data/Table/Apa itu Table|Table]] memakai Node dari Tree sebagai pilihan kategori pada setiap baris produk. |
| Menu atau navigasi bertingkat | Tree menyimpan susunan menu, lalu Flow memperbarui sistem lain setiap kali susunannya berubah. |

Dengan memisahkan Tree sumber dan Tree penggabung, data tetap dikelola oleh pemiliknya masing-masing, tetapi dapat dipakai bersama oleh seluruh tim.

## Praktik Terbaik

- **Pisahkan Tree sumber dan Tree penggabung.** Simpan Node di Tree non-merger per kebutuhan, dan gunakan Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] hanya untuk menghimpun Node dari Tree lain.
- **Tentukan kebutuhan Merger Mode sejak awal.** [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] tidak dapat diubah setelah Tree dibuat, dan Tree non-merger tidak dapat menambahkan Node dari Tree lain.
- **Kunci atribut yang harus stabil.** Aktifkan [[^field|Order]], [[^field|Name]], atau [[^field|Children]] pada [[#External Read Only]] jika atribut tersebut tidak boleh ikut berubah dari Tree lain, baik pada Tree merger maupun non-merger.
- **Beri [[^field|Name]] Node yang jelas.** [[^field|Search Tree Data...]] hanya mencari berdasarkan [[^field|Name]], sehingga nama yang deskriptif mempermudah pencarian.
- **Rapikan pohon besar dengan [[^field|View]].** Gunakan [[^field|Collapse Descendant]] atau [[^field|Collapse and Hide]] di [[#Menu Konteks Node]] agar tampilan tetap ringkas.
- **Pilih [[^field|Context]] sesuai kebiasaan kerja.** Atur [[#Default Configuration|Context]] agar membuka [[^field|Menu]], [[^field|Edit]], atau [[^field|Detail]] sesuai aksi yang paling sering Anda lakukan.

## Batasan dan Catatan

- Tree yang tidak bersifat merger tidak dapat menambahkan [[Docs/Tipe Data/Node]] dari Tree lain.
- [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] ditentukan saat Tree dibuat dan tidak dapat diubah setelahnya.
- [[^field|Search Tree Data...]] hanya mencari berdasarkan [[^field|Name]] Node.
- Pengaturan [[#External Read Only]] menentukan apakah [[^field|Order]], [[^field|Name]], dan [[^field|Children]] ikut berubah ketika Node di Tree lain diperbarui, baik pada Tree merger maupun non-merger.
- [[^field|Expand]], [[^field|Collapse]], dan [[^field|Expand Children Only]] berubah menjadi [[^field|No children...]] pada Node tanpa anak.
- [[^field|Horizontal Mode]] dan [[^field|Context]] pada [[#Default Configuration]] adalah nilai awal. Perubahan [[^field|mode _]] dan [[^field|context _]] di halaman kerja hanya bersifat sementara, dan untuk mengubah nilai awalnya gunakan [[^button/edit|Edit]].
- Menghapus Tree menghapus seluruh Node dan memutus relasi dari komponen lain (lihat [[#Menghapus Tree]]).
- Penggunaan [[^button/publish|Publish]] dan [[^button/event|Event]] dibatasi oleh Function Access di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## TL:DR

- Tree adalah komponen modul [[Docs/Modul Data/Pengenalan|Data]] untuk menyimpan data berhierarki berbentuk pohon yang terdiri dari banyak [[Docs/Tipe Data/Node]].
- Tree baru otomatis memiliki satu Node bernama [[^field|Origin]]. Buat Tree lewat [[^field/add|Add]] > [[^field|Data]] > [[^field/tree|Tree]] (lihat [[#Membuat Tree]]).
- [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] membuat Tree dapat menambahkan (*clone*) Node dari Tree lain dan tidak dapat diubah setelah Tree dibuat, sedangkan [[#External Read Only]] mengatur atribut Node yang ikut berubah.
- Halaman kerja menampilkan pohon dengan [[#Default Configuration|Mode]] horizontal atau vertikal, dilengkapi [[^field|Search Tree Data...]] yang hanya mencari [[^field|Name]] (lihat [[#Antarmuka Tree]]).
- Klik kanan pada Node untuk membuka [[#Menu Konteks Node]] guna mengelola Node dan mengatur tampilan cabang.
- Hati-hati saat menghapus Tree karena seluruh Node hilang dan relasi dari komponen lain terputus.

## FAQ : Pertanyaan yang Sering Diajukan

> **faq**
> **Apa bedanya Tree biasa dengan Tree yang memakai [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]]?**
> Tree biasa hanya menyimpan Node miliknya sendiri. Tree dengan [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] dapat menambahkan (*clone*) Node dari Tree lain, sedangkan Tree biasa tidak dapat melakukannya.
> **Apakah [[Docs/Modul Data/Tree/Konfigurasi Merger Mode|Merger Mode]] dapat diubah setelah Tree dibuat?**
> Tidak. Pilihan ini ditentukan saat Tree dibuat. Lihat [[#Mengubah Tree]].
> **Apakah perubahan pada Node asal otomatis muncul di Node *clone*?**
> Hal ini bergantung pada [[#External Read Only]]. Jika [[^field|Order]], [[^field|Name]], atau [[^field|Children]] berstatus [[^value/boolean/Non-Active]], atribut tersebut ikut berubah ketika Node di Tree lain diperbarui.
> **Apa yang dicari oleh [[^field|Search Tree Data...]]?**
> Kolom ini hanya mencari berdasarkan [[^field|Name]] Node.
> **Apakah perubahan [[^field|mode _]] dan [[^field|context _]] di halaman kerja bersifat permanen?**
> Tidak. Perubahan di halaman kerja hanya sementara. Untuk mengubah nilai awalnya, gunakan [[^button/edit|Edit]] (lihat [[#Default Configuration]]).
> **Mengapa menu [[^field|Collapse]] berubah menjadi [[^field|No children...]]?**
> Node tersebut tidak memiliki anak, sehingga tidak ada yang dapat dilipat atau diperluas. Lihat [[#Menu Konteks Node]].
> **Apa yang ada di Tree yang baru dibuat?**
> Tree baru otomatis memiliki satu Node bernama [[^field|Origin]]. Anda dapat menambahkan Node lain di [[#Mengelola Node]].

