---
layout: post
title: Alfabedeki Sıraların Toplamı Hangi Harf
date: 2019-11-23 19:42 +0300
categories: Coding-Challenges
tags: Alfabe, Harf, Toplam
excerpt: Programcıya, harflerden oluşan bir karakter dizisi (girilenHarfler) veriliyor. Bu noktadan sonra ise programcıdan, verilen karakterlerin sıra numalarının toplamını bulması ve elde ettiği toplam sayısının alfabedeki hangi harfe denk geldiği yazdırması isteniyor...
---
### Soru
Programcıya, harflerden oluşan bir karakter dizisi **(girilenHarfler)** veriliyor. Bu noktadan sonra ise programcıdan, verilen karakterlerin sıra numalarının toplamını bulması ve elde ettiği toplam sayısının alfabedeki hangi harfe denk geldiği yazdırması isteniyor. Yalnız göz önünde bulundurulması gereken bazı şeyler var:

* Harfler daima küçük harfli olmalı,
* Harf toplamı, alfabede toplamını (26) aşarsa sıra sıfırlanmalı,
* Hiçbir harf verilmezse veya sadece z harfi verilirse sonuç z olarak gösterilmeli.

### Örnek

| Girdi                          | Çıktı         |
|--------------------------------|---------------|
| **girilenHarfler**: 'a', 'b','c'  | **Sonuç**:  f |
| **girilenHarfler**: 'z', 'a'      | **Sonuç**:  a |
| **girilenHarfler**: 'y', 'c', 'b' | **Sonuç**:  d |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        char[] girilenHarfler = new[] {'a', 'b', 'c'};

        // Alfabedeki harfleri diziye ekle (Sıra bulmak için gerekli)
        List<string> alfabe = new List<string>
        {
            "a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"
        };

        // Karakter dizisi olarak girilen harfleri birleştir
        string yazi = string.Join("", girilenHarfler);

        if (girilenHarfler.Length == 0)
            Console.WriteLine("Cevap: z");

        if (girilenHarfler.Length == 0 && girilenHarfler[0] == 'z')
            Console.WriteLine("Cevap: z");

        // Girilen harflerin alfabedeki sırasını bulup topla
        int toplam = 0;
        foreach (char harf in yazi)
        {
            toplam += alfabe.IndexOf(harf.ToString()) + 1;
        }

        // Eğer alfabe uzunluğu, 26'dan fazla ise 26 ile bölümden kalan sayısını bul
        toplam %= alfabe.Count;

        // Elde edilen sayının alfabedeki yerini bul
        // İndeks 0'dan başladığı için mevcut sayıyı 1 düşür
        string sonuc = Convert.ToChar(alfabe[toplam - 1]);
        Console.WriteLine("Sonuç: " + sonuc);

        Console.Read();
    }
}
```

### Çözüm - Java
```java
package zeta;

public class Main {
    public static void main(String[] args) 
    {
        char[] girilenHarfler = {'a', 'b', 'c'};

        // Alfabedeki harfleri diziye ekle (Sıra bulmak için gerekli)
        String alfabe = "abcdefghijklmnopqrstuvwxyz";

        // Girilen harflerin alfabedeki sırasını bulup topla
        int toplam = 0;

        for (char karakter : girilenHarfler) {
            toplam += alfabe.indexOf(karakter) + 1;
            System.out.println(toplam);
        }

        // Eğer alfabe uzunluğu, 26'dan fazla ise 26 ile bölümden kalan sayısını bul
        toplam %= alfabe.length();

        // Elde edilen sayının alfabedeki yerini bul
        // İndeks 0'dan başladığı için mevcut sayıyı 1 düşür
        String sonuc = String.valueOf(alfabe.charAt(toplam - 1));
        System.out.println("Sonuç: " + sonuc);
    }
}
```