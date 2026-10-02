---
    status: draft
    pageDecoration:
      tree:
        priority: -2
---
# Frontmatter Guidance

Contoh basic untuk dokumen draft
```yaml
---
    status: draft
    pageDecoration:
      icon: x
      tree:
        priority: 0
---
```

Contoh basic untuk dokumen released
```yaml
---
    status: released
    title: #isi judul disini
    desciption: #isi deskripsi disini
    pageDecoration:
      #icon: x #(hapus simbol pagar jika diubah menjadi draft)
      tree:
        priority: 0
    tags:
      - example
      #isi tag disini
---
```

Secara contoh berikut adalah atribut penting untuk frontmatter:
1. [[frontmatter guidance#status|status]]
2. [[frontmatter guidance#title|title]]
3. [[frontmatter guidance#description|description]]
4. [[frontmatter guidance#pageDecoration.icon|pageDecoration.icon]]
5. [[frontmatter guidance#pageDecoration.tree.priority|pageDecoration.tree.priority]]
6. [[frontmatter guidance#tags|tags]]

Berikut penjelasan atribut penting yang bisa atau wajib digunakan.

### status
   *status* adalah atribut untuk penanda status halaman dengan nilai seperti berikut:
   * draft    : jika halaman belum dipublish ke website.
   * released : jika halaman dipublish ke website

### title
   *title* adalah atribut untuk menamakan dokumen dan akan tampil di judul tab website (jika diisi dengan ***“Some Title”***, maka hasil diwebsite akan seperti **Some Title | Phoenix Documentation**), jika tidak diisi, maka Heading 1 akan dijadikan sebagai Judul. Judul akan muncul dalam mesin pencarian seperti Google, jadi harap hati-hati.

### description
   *description* adalah atribut untuk menjelaskan deskripsi dokumen dan akan tampil di SEO tag website (dengan contoh seperti **Halaman yang menjelaskan aturan dalam penulisan dokumentasi**), jika tidak diisi, maka deskripsi akan kosong. Deskripsi akan muncul dalam mesin pencarian seperti Google, jadi harap hati-hati.

### pageDecoration.icon
   ditulis dengan format seperti berikut
   ```yaml
   pageDecoration:
      icon: something...
   ```
   wajib diisi dengan “x” jika status draft, atau diisi “folder” untuk folder. jangan gunakan jika release atau tidak dibutuhkan (dapat gunakan # agar bersifat notes)

### pageDecoration.tree.priority
   ditulis dengan format seperti berikut:
   ```yaml
   pageDecoration:
      tree:
        priority: some number...
   ```
   jika Anda ingin mengubah urutan halaman di Navigation : Tree. Anda dapat mengisi nilai angka besar agar keatas, atau kecil untuk kebawah.
   
### tags
   ditulis dengan format seperti berikut:
   ```yaml
   tags:
    - some tags
    - another tags
   ```
   jika anda ingin menambahkan penanda tags yang relevan agar membantu pembaca menemukan halaman yang relevan bisa gunakan atribut ini.

   