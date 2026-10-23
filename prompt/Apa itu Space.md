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

Pertanyaan lanjutan : 
1.  **Menambah dan mengelola data.** Bagaimana cara menambah Weather, Environment, dan Object? Apakah lewat klik kanan pada grup di Outliner (Weather, Environment, Object), atau ada tombol lain? Bagaimana cara mengubah dan menghapusnya? Pada screenshot, grup di Outliner bertanda panah dan bertuliskan angka jumlah data, misalnya `Weather (0)`. Apakah angka itu jumlah data di grup tersebut?
2.  **Tombol \[\[^button/edit|Edit\]\] di bilah navigasi.** Apakah hanya mengubah atribut Space (Name dan Description), seperti komponen lain? Lalu, apakah kolom \[\[^field|Search Space Data...\]\] mencari nama data di Outliner saja, atau juga hal lain?
3.  **Kontrol view 3D.** Mohon konfirmasi gestur di halaman kerja:
    *   Mengubah sudut pandang (memutar), menggeser (*pan*), dan zoom: tombol mouse mana untuk masing-masing, dan bagaimana gestur di mobile?
    *   Setelah data difokuskan, apakah muncul penanda untuk memindah, memutar, dan mengubah skala? Bagaimana cara berpindah antar mode tersebut (tombol, pintasan keyboard, atau lainnya)?
    *   Apakah memindah atau memutar langsung tersimpan ke Position, Rotation, Scale (Environment) dan Origin (Object)? Dan apakah ada *snap* atau tombol reset kamera?
4.  **Weather.** Pada poin Weather tertulis “banyak *environment* dengan jenis yang sama”, apakah maksudnya banyak *weather*? Lalu, apakah priority paling rendah (angka terkecil) yang menang, dan apakah hanya data dengan Status = \[\[^value/boolean/true\]\] yang dihitung? Mohon juga tuliskan nama Jenis persis seperti di aplikasi (misalnya “Earth Sky” atau “Earth” dan “Sky” terpisah, serta “Sea”).
5.  **Model.** Dari mana pilihan Model pada Environment dan Object berasal? Apakah dari komponen modul Developer bernama “Model” (path halaman dan nama komponennya apa)? Apakah daftar Model pada Environment dan Object sama?
6.  **Tabel Model Attribute.** Pada Object, kolom Static berupa boolean tetapi Anda menyebut “type = static / bind”. Apakah maksudnya Static = \[\[^value/boolean/true\]\] berarti *static* dan \[\[^value/boolean/false\]\] berarti *bind*? Jika *bind*, apakah Value berupa pilihan kolom dari Query? Dan dari mana daftar Key berasal, apakah mengikuti atribut Model yang dipilih?
7.  **Hak akses.** Di Workspace, apakah Space punya Data Access sendiri dengan jenis data seperti SpaceWeather, SpaceEnvironment, dan SpaceObject? Apakah perubahan di panel properti yang memengaruhi row juga butuh Data Access Table sumber? Dan apakah panel properti berlaku untuk ketiga jenis data, atau hanya Object (dan Environment)?

Jawaban: 

1.  Cara menambahkannya adalah dengan klik kanan pada panel Outline, akan ada context menu Add Weather, Add Environment dan Add Object. Pada daftar yang terisi juga akan ada opsi Delete. Angka pada Outliner adalah jumlah data di group tersebut.
2.  Iya hanya name dan description, sedangkan search adalah mencari data di outliner berdasarkan name dan search. Jika object memiliki banyak data, maka data tersebut tetap bisa disearch.
3.  Memutar dengan klik kiri,menggeser dengan shift + klik move kiri, zoom dengan wheel, pada mobile menggunakan gesture touch seperti biasa. Ketika difokuskan ada bantuan pemindah dll. Untuk antar mode belum ada.
4.  Iya maaf maksudnya banyak weather, priority terkecil yang menang, dengan status harus True
5.  Environment hanya objek statis tanpa logika jadi user bisa hanya dengan upload 3d file. Sedangkan Object memiliki logika yang kompleks sehingga menyiapkannya dilakukab di komponen Model dalam modul Developer.
6.  Static dan bind adalah radio, kalau bind berarti akan memilih kolom di Query. Daftar key dipersiapkan di komponen Model sesuai dengan yang dipilih di field.
7.  Tidak ada, Data Access mewakili semua kategori. perubahan di panel mempengaruhi data sumber hanya berlaku di Object, karena Weather menggunakan Query single output (hasil kalkulasi) dan Environment hanya data statis, sedangkan Object menggunakan kaidah Table Output yang datanya ril bukan hasil kalkulasi.