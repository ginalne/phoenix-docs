
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