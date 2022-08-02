---
title: "Flutter - Scaffold "
date: 2022-08-02T14:11:20+07:00
draft: false
showtoc: true
author: "Chrisdion Andrew"
categories: ["Programming", "Flutter"]
tags: ["Programming", "Widget", "Flutter", "Scaffold"]
description: ""
---

# Scaffold

Scaffold merupakan sebuah widget yang digunakan untuk membuat tampilan dasar material design pada aplikasi Flutter, yang dapat disebut juga dasar sebuah halaman pada aplikasi Flutter.

Tampilan dasar tersebut seperti berikut:

![Scaffold](./img/scaffold.png#center)

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

