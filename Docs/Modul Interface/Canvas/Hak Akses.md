---
    status: release
    title: "Hak Akses dalam Canvas"
    description: "Penjelasan hak akses dalam Canvas dengan Elemen"
    pageDecoration:
      tree:
        priority: -2
---
# Hak Akses Canvas

Canvas mengikuti Comp. Access, Data Access, dan Function Access di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]] seperti komponen lain.

| Akses                                                                                                  | Pengaruh pada Canvas                                                                                                                              |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Docs/Modul Developer/Workspace/Apa itu Workspace#Comp. Access|Comp. Access]]                        | Mengatur apakah Canvas terlihat, dapat ditambahkan, diubah atributnya (Name dan Description), dan dihapus.                                        |
| [[Docs/Modul Developer/Workspace/Data Access|Data Access]] Add                                        | Menambahkan widget ke dalam Canvas.                                                                                                               |
| [[Docs/Modul Developer/Workspace/Data Access|Data Access]] Update                                     | Mengubah Query, atribut, atau styling widget.                                                                                                     |
| [[Docs/Modul Developer/Workspace/Data Access|Data Access]] Delete                                     | Menghapus widget dari Canvas.                                                                                                                     |
| [[Docs/Modul Developer/Workspace/Apa itu Workspace#Function Access|Function Access]] View Publish     | Hanya melihat konfigurasi publikasi, misalnya menyalin tautan.                                                                                    |
| [[Docs/Modul Developer/Workspace/Apa itu Workspace#Function Access|Function Access]] Publish          | Memperbarui konfigurasi publikasi, yaitu mengubah Status.                                                                                         |

Data Access pada Canvas mengatur setiap perubahan widget dan atributnya di dalam Canvas. Jika salah satu dari Add, Update, atau Delete bernilai [[^value/boolean/allow]], toggle [[^field|mode]] dapat dipindahkan ke Edit Mode. Jika ketiganya [[^value/boolean/disallow]], Canvas hanya dapat dilihat.
