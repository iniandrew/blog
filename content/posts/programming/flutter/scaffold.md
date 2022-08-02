---
title: "Flutter - Scaffold "
date: 2022-08-02T14:11:20+07:00
draft: false
showtoc: true
author: "Chrisdion Andrew"
categories: ["Programming", "Flutter"]
tags: ["Programming", "Widget", "Flutter", "Scaffold", "AppBar", "FloatingActionButton", "Body"]
description: ""
---

# Scaffold

Scaffold merupakan sebuah widget yang digunakan untuk membuat tampilan dasar material design pada aplikasi Flutter, yang dapat disebut juga dasar sebuah halaman pada aplikasi Flutter.

Tampilan dasar tersebut seperti berikut:

![Scaffold](../img/scaffold.png#center)

Tampilan di atas merupakan implementasi dari Scaffold. Scaffold di atas memiliki 3 bagian yaitu **AppBar**, **Body**, dan **FloatingActionButton**.

Untuk membuat sebuah Scaffold kita hanya cukup memanggil class Scaffold seperti berikut:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold();
  }
}
```

Pada kode di atas kita membuat sebuah StatelessWidget bernama FirstScreen, yang merupakan widget tampilan kita. Kemudian di dalam method build kita panggil Scaffold.

Jangan lupa untuk memanggil FirstScreen pada Widget MyApp seperti berikut:

```
import 'package:flutter/material.dart';
 
void main() => runApp(const MyApp());
 
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const FirstScreen(),// Panggil FirstScreen di sini
 
    );
  }
}
 
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold();
  }
}
```

# AppBar

AppBar merupakan Header (bagian paling atas) aplikasi atau biasa dikenal dengan toolbar. Pada AppBar umumnya terdapat judul dan ActionButton.

Berikut adalah cara menambahkan AppBar pada Scaffold:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
      ),
    );
  }
}
```

Pada kode di atas kita menambahkan parameter appBar pada Scaffold dan menambahkan title pada AppBar tersebut. Title di sini tidak hanya spesifik Text saja, melainkan juga dapat diisi dengan widget lainnya seperti TextField untuk kolom pencarian atau yang lainnya.

Selain menambahkan title kita dapat menambahkan widget-widget actions seperti pada kode berikut:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
        actions: <Widget>[
          IconButton(
            icon: const Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {},
          ),
        ],
      ),
    );
  }
}
```

Pada kode di atas kita menambahkan Icon search pada bagian kanan AppBar.

![Scaffold Appbar Action](../img/scaffold-appbar-action.png#center)

Lalu kita juga dapat menambahkan action pada bagian kiri AppBar misalnya untuk tombol yang menampilkan menu (drawer), seperti pada kode berikut:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
        actions: [
          IconButton(
            icon: const Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {},
          ),
        ],
        leading: IconButton(
          icon: const Icon(
            Icons.menu,
            color: Colors.white,
          ),
          onPressed: () {},
        ),
      ),
    );
  }
}
```

![Scaffold Appbar Leading](../img/scaffold-appbar-leading.png#center)

> Tidak seperti pada actions, **leading hanya dapat menampung satu widget saja**. Secara default, leading akan berisi tombol untuk kembali ke halaman sebelumnya (jika tersedia), atau tombol untuk menu drawer (jika kita mengatur untuk drawer pada Scaffold tersebut).
 
# Body

Body merupakan bagian utama dari Scaffold dan kita akan banyak menuliskan kode pada bagian body ini. 

Untuk implementasi body kita akan menambahkan parameter body pada Scaffold seperti berikut:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
        actions: [
          IconButton(
            icon: const Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {},
          ),
        ],
        leading: IconButton(
          icon: const Icon(
            Icons.menu,
            color: Colors.white,
          ),
          onPressed: () {},
        ),
      ),
      body: const Center(
        child: Text('Hello world!'),
      ),
    );
  }
}
```

Pada kode di atas kita telah menambahkan body yang di dalamnya kita memanggil widget Center yang akan menampilkan Text "Hello World!".

# FloatingActionButton

FloatingActionButton ini merupakan bagian dari Scaffold yang digunakan untuk menampilkan sebuah tombol aksi yang posisinya floating (melayang dan posisinya tetap).

Untuk menggunakan FloatingActionButton tambahkan kode Anda seperti berikut:

```
class FirstScreen extends StatelessWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
        actions: [
          IconButton(
            icon: const Icon(
              Icons.search,
              color: Colors.white,
            ),
            onPressed: () {},
          ),
        ],
        leading: IconButton(
          icon: const Icon(
            Icons.menu,
            color: Colors.white,
          ),
          onPressed: () {},
        ),
      ),
      body: const Center(
        child: Text('Hello world!'),
      ),
      floatingActionButton: FloatingActionButton(
        child: const Icon(Icons.add),
        onPressed: () {},
      ),
    );
  }
}
```

### Useful Links

- [Scaffold Class](https://api.flutter.dev/flutter/material/FloatingActionButton-class.html)
- [Scaffold Sample Apps](https://flutter.github.io/samples/#)
