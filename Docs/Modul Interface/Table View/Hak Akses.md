---
    status: release
    title: "Hak Akses dalam Table View"
    description: "Penjelasan hak akses dalam Table View dengan Data"
    pageDecoration:
      tree:
        priority: -2
---
## Hak Akses Table View

Hak akses pada Table View diatur berlapis. Pengelolaan [[Docs/Modul Interface/Table View/Table View Data]] diatur di Workspace, sedangkan perubahan Row dan cell diatur di konfigurasi Data dan di hak akses Table.

| Yang dikelola | Diatur melalui | Penjelasan |
| ------------- | -------------- | ---------- |
| Data: ubah nama, ubah Query, dan ubah konfigurasi | [[Docs/Modul Developer/Workspace/Data Access|Data Access]] di Workspace | Menentukan apakah anggota [[^value/boolean/allow]] atau [[^value/boolean/disallow]] mengubah Data. |
| Baris dan isi sel pada Table View | Konfigurasi Data editable/readonly +  [[Docs/Modul Developer/Workspace/Data Access|Data Access]] sumber di Workspace | Jika salah satu kondisi tidak memenuhi, maka baris dan isi sel tidak dapat dikelola |

>**note** Akses data sumber tetap berlaku
> Jika Workspace tidak mengizinkan pengelolaan pada data sumber, baris dan isi sel tetap tidak dapat diubah dari Table View, meskipun konfigurasi Data mengizinkannya. Aturan ini juga berlaku pada komponen Interface lain yang dapat mengubah data di komponen [[Docs/Modul Data/Pengenalan|Modul Data]].
