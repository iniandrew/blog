---
title: "Image"
date: 2022-08-02T19:17:41+07:00
draft: false
showtoc: true
author: "Chrisdion Andrew"
categories: ["Programming", "Widget", "Flutter"]
tags: ["Programming", "Widget", "Flutter", "Image"]
description: ""
---

# Image

Dalam pengembangan suatu aplikasi kita tidak akan lepas dari image atau gambar untuk membuat tampilan semakin menarik.

Pada flutter kita bisa menambahkan image atau gambar dengan 2 cara:
1. Image.network
2. Image.asset

# Image.network

Untuk menampilkan gambar yang bersumber dari internet, kita akan menggunakan method Image.network. 

Cara penulisan method ini sebagai berikut:

`Image.network(url)`

Method ini cukup menambahkan URL gambar dari internet dan kita pun dapat menambahkan width dan height juga.

Berikut adalah contoh penggunaan Image.network:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
      ),
      body: Center(
        child: Image.network(
          'https://picsum.photos/200/300',
          width: 200,
          height: 200,
        ),
      ),
    );
  }
}
```

# Image.asset

Selain melalui internet, kita juga dapat menampilkan gambar yang bersumber dari asset project. 
Asset di sini berupa gambar-gambar yang nantinya didaftarkan pada project. 

Untuk mendaftarkan asset gambar pada project kita harus menambahkannya pada berkas pubspec.yaml.

Pertama kita harus menambahkan terlebih dahulu gambar yang akan didaftarkan ke dalam folder project kita.

Saat ini Flutter mendukung beberapa jenis format gambar, seperti **JPEG, PNG, GIF, Animated GIF, WebP, Animated WebP, BMP, dan WBMP**. Di luar format tersebut, Flutter akan memanfaatkan API dari masing-masing platform. Jika platform native mendukung format gambar yang digunakan, maka gambar tersebut akan bisa di-render oleh Flutter.

Pada contoh kali ini kita menambahkan folder **_images/_** pada folder project. 
dan memasukan berkas gambar yang ingin kita gunakan ke dalam folder image. 
Sebagai contoh kita menggunakan gambar bernama **_android.png._**


Setelah menambahkan gambar pada project, saatnya kita mendaftarkan gambar tersebut pada pubspec.yaml.

```
...
flutter:
 
  uses-material-design: true
 
  # To add assets to your application, add an assets section, like this:
  # assets:
  #  - images/a_dot_burr.jpeg
  #  - images/a_dot_ham.jpeg
  
  assets:
    - images/android.png
...
```

Hapus juga tanda pagar (#) atau komentar yang tidak diperlukan.

> Perhatikan pula indentasi kodenya. assets: berada sejajar dengan uses-material-design: yaitu berjarak 2 spasi dari ujung dan berada di dalam flutter: sedangkan - images/android.png berada di dalam assets: dan berjarak 4 spasi dari ujung.

Apabila ada banyak gambar yang kita masukkan ke dalam lokasi folder, dibandingkan menuliskan lokasi gambar satu per satu, kita bisa langsung menuliskan folder images/ seperti berikut:


```
...
flutter:
 
  uses-material-design: true
 
  assets:
    - images/
...
```

Setelah menambahkan assets, kita harus me-refresh pubspec.yaml dengan cara save file pubspec.yaml bila menggunakan Visual Studio Code atau menekan 'Packages get' yang ada di pojok kanan atas untuk Android Studio.

Setelah kita menambahkan asset ke dalam pubspec.yaml kita perlu melakukan full restart agar asset yang baru dapat digunakan dalam aplikasi.

Cara pemanggilannya dengan menggunakan kode berikut: `Image.asset(lokasi_asset)`

Contoh dalam kodenya akan seperti berikut:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
      ),
      body: Center(
        child: Image.asset('images/android.png', width: 200, height: 200),
      ),
    );
  }
}
```

# Useful Link
- [Image](https://api.flutter.dev/flutter/widgets/Image-class.html)
