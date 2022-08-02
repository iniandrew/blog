---
title: "Stateles & Stateful Widget"
date: 2022-08-02T13:50:18+07:00
draft: false
showtoc: true
author: "Chrisdion Andrew"
categories: ["Programming", "Flutter"]
tags: ["Programming", "Flutter", "Widget"]
description: ""
---

# StatelessWidget dan StatefulWidget

Widget pada Flutter memiliki dua jenis, yaitu StatelessWidget dan StatefulWidget. 

# Apa itu State?

Sebelum membahas kedua jenis widget tersebut, kita harus berkenalan terlebih dahulu dengan istilah State. Kenapa demikian? Widget kita akan terus berurusan dengan State. Lalu apa itu State?

Karena Flutter menggunakan paradigma OOP (Object-Oriented Programming), state biasanya menjadi suatu properti dari sebuah class. Contohnya sebagai berikut:

```
class ContohWidget extends StatelessWidget{
    final String _judul;
    ...
}
```

Variabel _judul di atas merupakan contoh pendeklarasian state pada suatu widget.

# StatelessWidget

StatelessWidget adalah widget yang **nilai state-nya tidak dapat berubah (_immutable_)** maka widget tersebut lebih bersifat statis dan memiliki interaksi yang terbatas.

Contoh:

```
class Heading extends StatelessWidget {
 
  final String text;
 
  const Heading({Key? key, required this.text}) : super(key: key);
 
  @override
  Widget build(BuildContext context){
    return Text(
      text,
      style: const TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
```

Widget di atas merupakan sebuah widget untuk membuat Heading (sebuah text yang digunakan untuk judul).

Kita akan panggil widget yang telah diubah ke kode project pertama kita.
```
import 'package:flutter/material.dart';
 
void main() => runApp(MyApp());
 
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const Scaffold(
        body: Center(
          child: Text("Hello world!"),
        ),
      ),
    );
  }
}
 
class Heading extends StatelessWidget {
  final String text;
 
  const Heading({Key? key, required this.text}) : super(key: key);
 
  @override
  Widget build(BuildContext context){
    return Text(
      text,
      style: const TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
```

Kita coba ubah widget Text yang menampilkan "Hello world!" dengan widget Heading yang kita buat.

```
import 'package:flutter/material.dart';
 
void main() => runApp(MyApp());
 
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const Scaffold(
        body: Center(
          child: Heading( // mengubah widget Text
            text:"Hello world!",
          ),
        ),
      ),
    );
  }
}
 
class Heading extends StatelessWidget {
  final String text;
 
  const Heading({Key? key, required this.text}) : super(key: key);
 
  @override
  Widget build(BuildContext context){
    return Text(
      text,
      style: const TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
```

Ketika kita ubah Text dengan widget Heading, hasilnya akan berubah. Tulisan "Hello world!" jadi lebih besar.


> Note:
Sesuai definisi StatelessWidget, state-nya tidak dapat berubah (immutable), maka state yang ada di dalam kelas tersebut harus dibuat final. Nilainya hanya dapat diisi melalui constructor class-nya.
 
```
final String text; // state text bersifat final
 
const Heading({Key? key, required this.text}) : super(key: key); // lalu state text masuk ke constructor
``` 

# StatefulWidget

Kebalikan dari **StatelessWidget**, StatefulWidget ialah widget yang **state-nya dapat berubah-ubah nilainya**, yang berarti StatefulWidget **bersifat dinamis** dan memiliki interaksi yang tak terbatas.

Penulisan StatefulWidget sangat berbeda dengan StatelessWidget, berikut penulisannya:

```
class ContohStateful extends StatefulWidget {
 
    final String parameterWidget; // ini parameter widget
 
    const ContohStateful({Key? key, required this.parameterWidget}) : super(key: key);
 
    @override
    _ContohStatefulState createState() => _ContohStatefulState();
}
 
class _ContohStatefulState extends State<ContohStateful>{
    String _dataState; // ini state dari Widget ContohStateful
 
    @override
    Widget build(BuildContext context){
        // isi sebuah widget
    }
}
```

Contoh di atas adalah cara penulisan StatefulWidget. Seperti yang kita lihat, penulisan StatefulWidget lebih panjang. Tetapi yang harus diperhatikan adalah properti dari setiap class-nya. Pada class ContohStateful propertinya hanya berupa parameter ketika memanggil ContohStateful, parameter tersebut tidak wajib ada. Sedangkan pada class _ContohStatefulState, properti _dataState merupakan state yang sebenarnya. Kita akan mengubah nilai _dataState.


Misalnya kita coba membuat contoh StatefulWidget sederhana:

```
class BiggerText extends StatefulWidget {
  final String text;
 
  const BiggerText({Key? key, required this.text}) : super(key: key);
 
  @override
  _BiggerTextState createState() => _BiggerTextState();
}
 
 
class _BiggerTextState extends State<BiggerText> {
  double _textSize = 16.0;
 
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        Text(widget.text, style: TextStyle(fontSize: _textSize)),
        ElevatedButton(
          child: const Text("Perbesar"),
          onPressed: () {
            setState(() {
              _textSize = 32.0;
            });
          },
        )
      ],
    );
  }
}
```

Letakkan kode di atas setelah StatelessWidget Heading yang telah kita buat sebelumnya lalu panggil StatefulWidget BiggerText pada MyApp.

```
import 'package:flutter/material.dart';
 
void main() => runApp(MyApp());
 
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const Scaffold(
        body: Center(
          child: BiggerText(text:"Hello world!"), // Ubah widget Heading ke PerubahanText
        ),
      ),
    );
  }
}
 
class Heading extends StatelessWidget {
  final String text;
 
  const Heading({Key? key, required this.text}) : super(key: key);
 
  @override
  Widget build(BuildContext context) {
    return Text(
      text,
      style: const TextStyle(
        fontSize: 24.0,
        fontWeight: FontWeight.bold,
      ),
    );
  }
}
 
class BiggerText extends StatefulWidget {
  final String text;
  const BiggerText({Key? key, required this.text}) : super(key: key);
  @override
  _BiggerTextState createState() => _BiggerTextState();
}
class _BiggerTextState extends State<BiggerText> {
  double _textSize = 16.0;
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        Text(widget.text, style: TextStyle(fontSize: _textSize)),
        ElevatedButton(
          child: const Text("Perbesar"),
          onPressed: () {
            setState(() {
              _textSize = 32.0;
            });
          },
        )
      ],
    );
  }
}
```

> Note: Mengubah nilai state harus dilakukan pada fungsi setState seperti berikut:
```
    setState(() {
    _textSize = 32.0; // ukuran text diubah menjadi 32
    });
```

### Referensi:

- [StatelessWidget](https://api.flutter.dev/flutter/widgets/StatelessWidget-class.html)
- [StatefulWidget](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)