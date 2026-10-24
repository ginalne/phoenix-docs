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

Tree adalah komponen yang dapat menyimpan data secara hierarki atau berbentuk pohon. Sifat data ini cocok untuk menyimpan data relasional yang bercabang, seperti kategori dan subkategori atau struktur bertingkat lainnya. Satu Tree dapat memiliki banyak [[Docs/Tipe Data/Node]]. Salah satu atribut penting dalam Tree adalah [[Docs/Modul Data/Tree/Merger Mode|Merger Mode]].

Tree juga dapat dijadikan bersifat Merger. Dengan Merger Mode, satu Tree dapat memanggil Node dari beberapa Tree lain, lalu menambahkannya sebagai *clone* tanpa Anda perlu menyalin Node satu per satu. Anda juga dapat mengatur apakah atribut Node ikut berubah ketika Node asalnya diperbarui lewat [[Docs/Modul Data/Tree/External Read Only]].

## Mengapa Menggunakan Tree?

- **Data bercabang tersimpan rapi.** Hubungan induk dan anak antar data tergambar langsung dalam bentuk pohon.
- **Satu Tree, banyak Node.** Anda dapat menambahkan Node sebanyak yang dibutuhkan dan menyusunnya bertingkat.
- **Menggabungkan Node dari banyak Tree.** Tree dengan [[Docs/Modul Data/Tree/Merger Mode|Merger Mode]] menghimpun Node dari Tree lain dalam satu tempat.
- **Perubahan terkendali.** [[Docs/Modul Data/Tree/External Read Only]] menentukan atribut Node mana yang boleh ikut berubah dari Tree lain.
- **Tampilan mudah disesuaikan.** Pohon dapat ditampilkan secara horizontal atau vertikal, dan cabangnya dapat dilipat atau dibuka.
- **Terhubung dengan komponen lain.** Tree dapat dipublikasikan dan dihubungkan ke Event untuk otomasi di [[Docs/Modul Logic/Flow/Apa itu Flow|Flow]].

## Konsep Utama

| Istilah | Penjelasan |
| --- | --- |
| [[Docs/Tipe Data/Node]] | Satu simpul data di dalam Tree. Node memiliki atribut [[^field|Order]] dan [[^field|Name]], serta dapat memiliki anak. |
| [[#Membuat Tree|Origin]] | Node pertama yang otomatis dibuat ketika Tree baru dibuat. |
| [[Docs/Modul Data/Tree/Merger Mode]] | Atribut yang menentukan apakah Tree dapat menambahkan (*clone*) Node dari Tree lain. |
| [[Docs/Modul Data/Tree/External Read Only]] | Pengaturan yang menentukan apakah [[^field|Order]], [[^field|Name]], dan [[^field|Children]] Node ikut berubah ketika Node di Tree lain diperbarui. |
| [[#Default Configuration|Context]] | Status yang berlaku ketika Anda membuka menu konteks Node. |

## Cara Kerja

Penjelasan cara kerja Table View lihat selengkap nya di [[Docs/Modul Interface/Table View/Cara Kerja|Cara Kerja Table View]].

## Antarmuka

Penjelasan antarmuka Table View lihat selengkap nya di [[Docs/Modul Interface/Table View/Antarmuka|Antarmuka Table View]].

### Merger Node

Merger Node adalah atribut dalam Tree agar Node dapat dikloning dari [[Docs/Tipe Data/Node]] yang sudah ada.

Selengkapnya lihat [[Docs/Modul Data/Tree/Merger Mode]].

### External Read Only

External Read Only mengatur perubahan nilai pada atribut Node kloningan yang aksinya berasal bersumber dari Tree lain.

Selengkapnya lihat [[Docs/Modul Data/Tree/External Read Only]].

## Mengelola Tree

Berikut adalah halaman yang menjelaskan cara untuk mengelola Table View:
1. [[Docs/Modul Data/Tree/Membuat Baru]] Tree dalam halaman kerja.
2. [[Docs/Modul Data/Tree/Mengubah]] Atribut Tree seperti [[^field|Name]], [[^field|Description]].
3. [[Docs/Modul Data/Tree/Menghapus]] Table View.
4. [[Docs/Modul Data/Tree/Node/Pengenalan|Mengelola Node]] seperti menambahkan, mengubah atau memperbarui Node.
5. [[Docs/Modul Data/Tree/Publikasi]]: mengatur publikasi Table.
6. [[Docs/Modul Data/Tree/Otomasi]]: menghubungkan Table dengan [[Docs/Event/Apa itu Event|Event]].

## Praktik Terbaik

- **Pisahkan Tree sumber dan Tree penggabung.** Simpan Node di Tree non-merger per kebutuhan, dan gunakan Tree dengan [[Docs/Modul Data/Tree/Merger Mode|Merger Mode]] hanya untuk menghimpun Node dari Tree lain.
- **Tentukan kebutuhan Merger Mode sejak awal.** [[Docs/Modul Data/Tree/Merger Mode|Merger Mode]] tidak dapat diubah setelah Tree dibuat, dan Tree non-merger tidak dapat menambahkan Node dari Tree lain.
- **Kunci atribut yang harus stabil.** Aktifkan [[^field|Order]], [[^field|Name]], atau [[^field|Children]] pada [[#External Read Only]] jika atribut tersebut tidak boleh ikut berubah dari Tree lain, baik pada Tree merger maupun non-merger.
- **Beri [[^field|Name]] Node yang jelas.** [[^field|Search Tree Data...]] hanya mencari berdasarkan [[^field|Name]], sehingga nama yang deskriptif mempermudah pencarian.
- **Rapikan pohon besar dengan [[^field|View]].** Gunakan [[^field|Collapse Descendant]] atau [[^field|Collapse and Hide]] di [[#Menu Konteks Node]] agar tampilan tetap ringkas.
- **Pilih [[^field|Context]] sesuai kebiasaan kerja.** Atur [[#Default Configuration|Context]] agar membuka [[^field|Menu]], [[^field|Edit]], atau [[^field|Detail]] sesuai aksi yang paling sering Anda lakukan.

## Batasan dan Catatan

- Tree yang tidak bersifat merger tidak dapat menambahkan [[Docs/Tipe Data/Node]] dari Tree lain.
- [[Docs/Modul Data/Tree/Merger Mode|Merger Mode]] ditentukan saat Tree dibuat dan tidak dapat diubah setelahnya.
- [[^field|Search Tree Data...]] hanya mencari berdasarkan [[^field|Name]] Node.
- Pengaturan [[#External Read Only]] menentukan apakah [[^field|Order]], [[^field|Name]], dan [[^field|Children]] ikut berubah ketika Node di Tree lain diperbarui, baik pada Tree merger maupun non-merger.
- [[^field|Expand]], [[^field|Collapse]], dan [[^field|Expand Children Only]] berubah menjadi [[^field|No children...]] pada Node tanpa anak.
- [[^field|Horizontal Mode]] dan [[^field|Context]] pada [[#Default Configuration]] adalah nilai awal. Perubahan [[^field|mode _]] dan [[^field|context _]] di halaman kerja hanya bersifat sementara, dan untuk mengubah nilai awalnya gunakan [[^button/edit|Edit]].
- Menghapus Tree menghapus seluruh Node dan memutus relasi dari komponen lain (lihat [[#Menghapus Tree]]).
- Penggunaan [[^button/publish|Publish]] dan [[^button/event|Event]] dibatasi oleh Function Access di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]].

## TL:DR

- Tree adalah komponen modul [[Docs/Modul Data/Pengenalan|Data]] untuk menyimpan data berhierarki berbentuk pohon yang terdiri dari banyak [[Docs/Tipe Data/Node]].
- Tree baru otomatis memiliki satu Node bernama [[^field|Origin]]. Buat Tree lewat [[^field/add|Add]] > [[^field|Data]] > [[^field/tree|Tree]] (lihat [[#Membuat Tree]]).
- [[Docs/Modul Data/Tree/Merger Mode|Merger Mode]] membuat Tree dapat menambahkan (*clone*) Node dari Tree lain dan tidak dapat diubah setelah Tree dibuat, sedangkan [[#External Read Only]] mengatur atribut Node yang ikut berubah.
- Halaman kerja menampilkan pohon dengan [[#Default Configuration|Mode]] horizontal atau vertikal, dilengkapi [[^field|Search Tree Data...]] yang hanya mencari [[^field|Name]] (lihat [[#Antarmuka Tree]]).
- Klik kanan pada Node untuk membuka [[#Menu Konteks Node]] guna mengelola Node dan mengatur tampilan cabang.
- Hati-hati saat menghapus Tree karena seluruh Node hilang dan relasi dari komponen lain terputus.

