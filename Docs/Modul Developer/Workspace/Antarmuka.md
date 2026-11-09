---
    status: release
    title: "Antarmuka Workspace"
    description: Penjelasan antarmuka di halaman kerja komponen Workspace
    pageDecoration:
      tree:
        priority: 0
---
# Antarmuka Workspace

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
| [[^field/folder|Folder]] | Contoh [[Docs/Dasar/Apa itu Folder|Folder]], klik untuk melihat komponen di dalamnya. |
| [[^field/variable|Variable]], [[^field/enum|Role]], [[^field/table|Employee]], [[^field/tree|Organizational Structures]] | Contoh [[Docs/Dasar/Apa itu Komponen|Komponen]], setiap komponen memiliki ikon sesuai jenisnya dan informasi datanya di samping nama. Lihat [[Docs/Dasar/Apa itu Folder#Informasi Data]]. |

Sel yang kosong pada kolom hak akses berarti hak akses tersebut tidak relevan untuk komponen itu.

### Interaksi Antarmuka Workspace

| Fungsi | Aksi |
| --- | --- |
| Memperluas atau melipat folder | Klik folder pada kolom [[^field|Folder/ Component]]. |
| Memindahkan folder atau komponen | *Drag and drop* ke posisi tujuan, baik untuk mengubah urutan maupun memindahkannya ke folder lain. Mengubah urutan di dalam folder yang sama tidak memerlukan [[^field|Add]] maupun [[^field|Delete]]. Memindahkan ke folder lain memerlukan [[^field|Delete]] pada folder atau komponen yang dipindahkan, dan [[^field|Add]] pada folder tujuan. Lihat [[Docs/Modul Developer/Workspace/Component Access#Memindahkan Folder atau Komponen|Memindahkan Folder atau Komponen]]. |
| Mengubah hak akses | Klik tombol toggle pada sel di kolom hak akses. Lihat [[#Mengatur Hak Akses]]. |

>**warning** Memindahkan mengubah struktur folder Pro
>Struktur folder Pro dan Workspace saling berkesinambungan. Memindahkan folder atau komponen di halaman kerja Workspace juga mengubah struktur folder Pro.
