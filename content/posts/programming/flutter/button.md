---
title: "Flutter - Button"
date: 2022-08-02T18:57:54+07:00
draft: false
showtoc: true
author: "Chrisdion Andrew"
categories: ["Programming", "Widget", "Flutter"]
tags: ["Programming", "Widget", "Flutter", "Button"]
description: ""
---

# Button

Widget button ini adalah widget yang dapat menerima trigger sentuhan atau dapat melakukan suatu fungsi ketika disentuh, widget-widget button tersebut antara lain:

1. ElevatedButton
2. TextButton
3. OutlinedButton
4. IconButton
5. DropdownButton

# ElevatedButton

ElevatedButton merupakan bagian dari Material Design widget dari Flutter. 

Untuk menggunakan ElevatedButton caranya seperti berikut:

```
ElevatedButton(
  child: const Text("Tombol"),
  onPressed: () {
    // Aksi ketika button diklik
  },
),
```

Pada kode di atas ElevatedButton memiliki 2 parameter yaitu **onPressed** dan **child**. Parameter onPressed merupakan sebuah function event ketika tombol ditekan dan sebenarnya ada event lain seperti onLongPress dan onHighlightChanged. Parameter child diisi oleh widget pada umumnya.

# TextButton

TextButton merupakan widget button yang memiliki tampilan yang polos selayaknya Text. 
TextButton umumnya digunakan pada toolbars, dialog, atau bersama komponen button lain. 

Contoh kode dari TextButton adalah seperti berikut:

```
TextButton(
  child: const Text('Text Button'),
  onPressed: () {
    // Aksi ketika button diklik
  },
),
```

Sama halnya ElevatedButton, TextButton juga memiliki parameter onPressed dan child.


# OutlinedButton

OutlinedButton juga merupakan bagian dari material design yang menyediakan tampilan TextButton dengan tambahan outline. 
> OutlinedButton umumnya digunakan untuk tombol atau aksi yang penting, tetapi bukan aksi utama dalam aplikasi.

Berikut ini adalah contoh widget OutlinedButton:

```
OutlinedButton(
  child: const Text('Outlined Button'),
  onPressed: () {
    // Aksi ketika button diklik
  },
),
```

# IconButton

IconButton merupakan widget button dengan icon. Tak seperti widget tombol lainnya, widget IconButton ini tidak memiliki child. 

Perhatikan kode di bawah ini:

```
IconButton(
  icon: const Icon(Icons.volume_up),
  tooltip: 'Increase volume by 10',
  onPressed: () {
    // Aksi ketika button diklik
  },
),
```

Seperti yang kita lihat di atas, IconButton tidak menggunakan child untuk isi (content) melainkan menggunakan parameter icon dan **_tooltip_** (penunjuk) untuk memberikan hint pada tombol.

# DropdownButton

DropdownButton merupakan tombol yang saat diklik, akan muncul pop-up daftar beberapa item yang dapat kita pilih salah satu. 

Berikut contoh kodenya:

```
class FirstScreen extends StatefulWidget {
  const FirstScreen({Key? key}) : super(key: key);
 
  @override
  State<FirstScreen> createState() => _FirstScreenState();
}
 
class _FirstScreenState extends State<FirstScreen> {
  String? language;
 
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('First Screen'),
      ),
      body: DropdownButton<String>(
        items: const <DropdownMenuItem<String>>[
          DropdownMenuItem<String>(
            value: 'Dart',
            child: Text('Dart'),
          ),
          DropdownMenuItem<String>(
            value: 'Kotlin',
            child: Text('Kotlin'),
          ),
          DropdownMenuItem<String>(
            value: 'Swift',
            child: Text('Swift'),
          ),
        ],
        value: language,
        hint: const Text('Select Language'),
        onChanged: (String? value) {
          setState(() {
            language = value;
          });
        },
      ),
    );
  }
}
```

Pada contoh tersebut DropdownButton tidak menggunakan child maupun children, akan tetapi menggunakan items di mana berisi list dari widget DropdownMenuItem.

Pada widget DropdownMenuItem terdapat child untuk tiap itemnya dan value yang ada pada DropdownMenuItem adalah nilai dari tiap itemnya. 

Nantinya akan dibutuhkan parameter **onChanged** ketika ada perubahan atau ketika memilih salah satu dari item tersebut dan mengubah nilai language atau value dari DropdownButton tersebut. 

Sedangkan hint berfungsi ketika nilai value dari DropdownButton null atau kosong.


# Useful Links
- [Button Material Components](https://docs.flutter.dev/development/ui/widgets/material#Buttons)
- [Elevated Button](https://api.flutter.dev/flutter/material/ElevatedButton-class.html)
- [Text Button](https://api.flutter.dev/flutter/material/TextButton-class.html)
- [Outlined Button](https://api.flutter.dev/flutter/material/OutlinedButton-class.html)
- [Icon Button](https://api.flutter.dev/flutter/material/IconButton-class.html)
- [Dropdown Button](https://api.flutter.dev/flutter/material/DropdownButton-class.html)

