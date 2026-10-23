---
  pageDecoration:
    tree:
      priority: -12
  tags:
    meta
    prompt
---
2026-10-23 13:30

![[prompt/phoenix.ginalne.com_testing_canvas_14(Documentation) (4).png]]
![[prompt/phoenix.ginalne.com_testing_space_4(Documentation).png]]
/phoenix-docs-knowledge  /phoenix-docs-silverbullet 

Tolong saya membuat halaman "Apa itu Space?".
base knowledge:

1. Space adalah komponen yang menaungi dan mengorganisasi data dalam bentuk 3D (tiga dimensi). Dengan Space, Anda dapat memvisualisasikan data beserta hubungan antar data dalam ruang tiga dimensi dan menjelajahinya dari berbagai sudut pandang, sehingga pola dan keterkaitan yang sulit terlihat pada tampilan tabel menjadi lebih mudah dipahami.
2. Space memiliki 3 jenis data yaitu Weather, Environment dan Object.
3. Weather adalah data yang tampil sebagai _world effect_ dengan atribut Priority [number], Name [string], Description [string], Jenis (dengan properti uniknya), Status [boolean]. Jenis yang bisa digunakan saat ini adalah earth sky (dengan properti waktu [datetime / datetimezone]), dan sea (dengan properti level [number] dan wave rate [number]). Jika ada banyak environment dengan jenis yang sama maka akan diambil priority yang paling rendah. Properti dalam weather bisa statis atau menggunakan Query (kaidah single output)
4. Environment adalah data yang tampil sebagai object dengan atribut Name, Desc, Position (3d vector), Scale (volume unit), Rotation (euler angle), Model (3d model).
5. Object adalah data yang tampil sebagai object dengan atribut Name, Desc, Origin (3d vector), Model (komponen developer/model), Query (dengan kaidah Table Output). Ketika query di isi maka akan tampil tabel Model Attribute dengan kolom Key, Static [boolean], dan Value, jika type = ‘static’ maka value yang di input adalah bebas, dan jika type = ‘bind’ maka value yang diinput adalah kolom yang tersedia di Query. Perlu diketahui bahwa Query bisa memanggil memanggil lebih banyak data, jadi ketika suatu atribut bernilai static maka semua object 3d yang dirender (sesuai jumlah data) nilai atributnya akan sama, berbeda ketika typenya ‘bind’.
6. Ketika object difokuskan, maka akan tampil panel properti disebelah kanan halaman kerja, nilainya bisa diubah dan mempengaruhi row sebenarnya (Namun tetap mengikuti ketentuan Data Access pada sumber).
7. Interaksi yang bisa dilakukan pada halaman kerja space adalah kontrol view 3d nya, yaitu sesuai dengan OrbitControls dan TransformControls pada three js (jangan sebut ini dengan literal, tapi buat penjelasan secara rinci sesuai dengan apa yang ada dihalaman kerja phoenix).