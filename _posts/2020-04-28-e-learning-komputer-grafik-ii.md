---
layout: post
title: "Tugas e-Learning Komputer Grafik II"
description: "Blog post Anti-Aliasing."
date: 2020-04-28
tags: [Kuliah]
comments: true
share: true
---

### 1. Anti-Aliasing

Anti-Aliasing (AA) adalah sebuah teknologi strategi untuk menghilangkan Jaggies atau effek seperti “tangga” pada garis tepi sebuah grafis video game agak terlihat lebih mulus atau Smooth.

![Gambar Anti-Aliasing](http://blog.ki2naiver.id/images/komgraf/a.jpg "Gambar Anti-Aliasing")

Antialiasing, kemudian, adalah teknologi yang mencoba untuk menyelesaikan aliasing yang ditemukan pada gambar (atau bahkan dalam sampel audio).

Anda mungkin menemukan pilihan untuk anti-aliasing jika Anda melihat melalui pengaturan video game.

Beberapa pilihan mungkin termasuk 4x, 8x, dan 16x, meskipun 128x dimungkinkan dengan konfigurasi perangkat keras tingkat lanjut.

> Catatan: Antialiasing sering dilihat sebagai anti-aliasing atau AA, dan kadang-kadang disebut oversampling.

**Bagaimana Antialiasing Bekerja?**

Kita melihat kurva dan garis halus di dunia nyata. Namun, saat merender gambar untuk dipajang di monitor, mereka dipecah menjadi elemen persegi kecil yang disebut piksel. Proses ini menghasilkan garis dan tepi yang sering tampak bergerigi.

Antialiasing mengurangi masalah ini dengan menerapkan teknik tertentu untuk menghaluskan bagian tepi gambar yang lebih baik secara keseluruhan. Ini mungkin bekerja dengan sedikit mengaburkan tepi sampai tampak kehilangan kualitas bergerigi. Dengan sampling piksel di sekitar tepi, antialiasing menyesuaikan warna piksel di sekitarnya, mencampuradukkan tampilan bergerigi.

Meskipun pencampuran piksel menghilangkan tepi yang tajam, efek antialiasing bisa membuat piksel lebih fuzzier.

**Jenis Pilihan Antialiasing**

Berikut adalah beberapa jenis teknik antialiasing:

##### Supersample Antialiasing (SSAA)

Proses SSAA mengambil gambar beresolusi tinggi dan contoh rendah ke ukuran yang diperlukan. Ini menghasilkan tepi yang jauh lebih mulus, namun supersampling memerlukan lebih banyak sumber daya perangkat keras dari kartu grafis, seperti memori video tambahan.

![Contoh SSAA](http://blog.ki2naiver.id/images/komgraf/b.png "Contoh SSAA")

##### Multisample Antialiasing (MSAA)

Proses pengambilan sampel MSAA memerlukan sumber daya yang lebih sedikit dengan hanya mengabadikan sebagian gambar, terutama poligon. Proses ini tidak begitu intensif. Sayangnya, MSAA tidak bekerja dengan baik dengan tekstur alfa / transparan, dan karena tidak mencicipi keseluruhan pemandangan, kualitas gambar dapat dikurangi.

![Contoh MSAA](http://blog.ki2naiver.id/images/komgraf/c.png "Contoh MSAA")

##### Antialiasing Adaptif

Antialiasing Adaptif adalah perpanjangan MSAA yang bekerja lebih baik dengan tekstur alfa / transparan namun tidak memerlukan bandwidth dan sumber daya dari kartu grafis seperti yang dilakukan oleh supersampling.

![Contoh Adaptif](http://blog.ki2naiver.id/images/komgraf/d.jpg "Contoh Adaptif")

##### Coverage Sampling Antialiasing (CSAA)

Dikembangkan oleh NVIDIA, CSAA menghasilkan MSAA serupa dengan MSAA.

![Contoh CSAA](http://blog.ki2naiver.id/images/komgraf/e.png "Contoh CSAA")

##### Enhanced Quality Antialiasing (EQAA)

Dikembangkan oleh AMD untuk kartu grafis Radeon mereka, EQAA serupa dengan CSAA dan memberikan antialiasing berkualitas tinggi melebihi MSAA dengan persyaratan kinerja memori kecil.

![Contoh EQAA](http://blog.ki2naiver.id/images/komgraf/f.jpg "Contoh EQAA")

##### Fast Approximate Antialiasing (FXAA)

FXAA adalah perbaikan pada MSAA yang jauh lebih cepat dengan biaya kinerja perangkat keras yang lebih rendah. Plus, itu menghaluskan tepi pada keseluruhan gambar.

![Contoh FXAA](http://blog.ki2naiver.id/images/komgraf/g.jpg "Contoh FXAA")

##### Temporal Antialiasing (TXAA)

TXAA adalah proses antialiasing baru yang menghasilkan FXAA dengan mencocokkan hasil teknik perataan berbeda yang berbeda. Metode ini tidak bekerja pada semua kartu grafis.

![Contoh TXAA](http://blog.ki2naiver.id/images/komgraf/h.png "Contoh TXAA")

**Cara Menyesuaikan Antialiasing**

Seperti disebutkan di atas, beberapa game menawarkan opsi di bawah pengaturan video, untuk mengkonfigurasi antialiasing. Orang lain mungkin menawarkan beberapa pilihan atau bahkan memberi Anda pilihan untuk mengganti antialiasing sama sekali.

Anda juga dapat menyesuaikan pengaturan antialiasing melalui panel kontrol kartu video Anda. Beberapa driver antivi lainnya mungkin memberi Anda pilihan antialiasing yang tidak disebutkan di halaman ini.

Anda biasanya dapat memilih untuk memiliki pengaturan antialiasing yang didiktekan oleh aplikasi sehingga pilihan yang berbeda dapat digunakan untuk permainan yang berbeda, atau Anda dapat mematikan antialiasing sepenuhnya.

**Pengaturan Antialiasing mana yang Terbaik?**
Ini bukan pertanyaan yang mudah dijawab. Bereksperimenlah dengan pengaturan kartu permainan dan kartu grafis untuk melihat opsi mana yang Anda inginkan.

Jika Anda menemukan penurunan kinerja secara substansial, kurangi pengaturan kualitas atau kurangi antialiasing sumber daya yang intensif.

Namun, ingatlah bahwa memilih pengaturan antialiasing adalah resolusi paling banyak yang menghilangkan aliasing yang paling terlihat.

Sekian, Terima Kasih!

Faridl Nur Prastya W.
**NIM**: 161011400304
**Kelas**: 08TPLE003
_faridl@prastya.my.id_
