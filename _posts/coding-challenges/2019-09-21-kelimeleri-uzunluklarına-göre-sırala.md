---
layout: post
title: Kelimeleri Uzunluklarına Göre Sırala
date: 2019-09-21 15:02 +0300
categories: Coding-Challenges
tags: Sıralama, Kelime, Uzunluk
excerpt: Programcıya, çeşitli kelimelerden oluşan bir dizi (girilenDizi) veriliyor. Sonrasında ise, dizideki kelimeleri baş harflerine göre değil, uzunluklarına göre sıralaması isteniyor.
---
### Soru
Programcıya, çeşitli kelimelerden oluşan bir dizi **girilenDizi)** veriliyor. Sonrasında ise, dizideki kelimeleri baş harflerine göre değil, uzunluklarına göre sıralaması isteniyor.

### Örnek

| Girdi                                              | Çıktı                                |
|----------------------------------------------------|--------------------------------------|
| **girilenDizi**: "Ali", "Ahmet", "Neşe", "Zeynep"  | **Sonuç**: Ali, Neşe, Ahmet, Zeynep  |
| **girilenDizi**: "Gözlük", "Ev", "Anahtar", "Kapı" | **Sonuç**: Ev, Kapı, Gözlük, Anahtar |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

internal class Program
{
    private static void Main()
    {
        string[] girilenDizi = {"Gözlük", "Ev", "Anahtar", "Kapı"};

        // Diziyi sıralı olarak saklamak için Sorted List kullanmak en kolayı 
        SortedList<int, string> siraliListe = new SortedList<int, string>();

        // Her bir kelimenin uzunluğunu ve kelimeyi sıralı listeye ekle ve anahtar değere göre sırala
        foreach (var dizi in girilenDizi)
        {
            siraliListe.Add(dizi.Length, dizi);
        }

        // Her bir değeri (anahtarı değil) yazdır
        foreach (KeyValuePair<int, string> pair in siraliListe)
        {
            Console.WriteLine(pair.Value);
        }

        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.HashMap;

public class Main {

    public static void main(String[] args) {

        String[] girilenDizi = {"Gözlük", "Ev", "Anahtar", "Kapı"};

        // Diziyi sıralı olarak saklamak için Sorted List kullanmak en kolayı
        HashMap<Integer, String> siraliListe = new HashMap<>();

        // Her bir kelimenin uzunluğunu ve kelimeyi sıralı listeye ekle ve anahtar değere göre sırala
        for (var dizi : girilenDizi)
        {
            siraliListe.put(dizi.length(), dizi);
        }

        // Her bir değeri (anahtarı değil) yazdır
        for (var pair : siraliListe.values())
        {
            System.out.println(pair);
        }
    }
}
```