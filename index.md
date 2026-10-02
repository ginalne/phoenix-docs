---
    status: draft
    pageDecoration:
      tree:
        priority: -3
---
# Welcome to Phoenix Docs
Sebagai pembaca saya harap anda dapat mengabaikan pesan ini, berikut adalah aturan yang berlaku saat menulis dokumentasi ini:

## Frontmatter
frontmatter adalah section dalam penulisan dokumentasi yang dibuka dengan “---” dan ditutup dengan “---”, isi dari frontmatter ditulis dengan format YAML. 

Berikut adalah atribut penting yang bisa atau wajib digunakan.

### status
   *status* adalah atribut untuk penanda status halaman dengan nilai seperti berikut:
   * draft    : jika halaman belum dipublish ke website.
   * released : jika halaman dipublish ke website

### title
   *title* adalah atribut untuk :
   * draft    : jika halaman belum dipublish ke website.
   * released : jika halaman dipublish ke website

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


## Heading
Sebagai penulis Anda wajib menambahkan judul pada baris pertama diawali dengan mengetik # dan spasi.

Harap pastikan 