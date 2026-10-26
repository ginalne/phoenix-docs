---
    status: release
    title: "Hak Akses dalam Space"
    description: "Penjelasan hak akses dalam Space dengan Data"
    pageDecoration:
      tree:
        priority: -2
---
## Hak Akses Space

Space mengikuti pengaturan di [[Docs/Modul Developer/Workspace/Apa itu Workspace|Workspace]]:

| Hak Akses | Pengaruh pada Space |
| --- | --- |
| Comp. Access | Mengatur apakah Space terlihat ([[^field|Visible]]), serta dapat diubah ([[^field|Update]]) atau dihapus ([[^field|Delete]]). |
| Data Access | Satu pengaturan [[Docs/Modul Developer/Workspace/Data Access|Data Access]] mewakili ketiga jenis data (Weather, Environment, dan Object) untuk menambah ([[^field|Add]]), mengubah ([[^field|Update]]), dan menghapus ([[^field|Delete]]) data. |
| Data Access sumber | Pada Object, perubahan yang memengaruhi Row sumber hanya berhasil bila Data Access data sumber (misalnya [[Docs/Tipe Data/Table]]) juga mengizinkan. |
