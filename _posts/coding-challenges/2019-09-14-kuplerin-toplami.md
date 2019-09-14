---
layout: post
title: Küplerin Toplamı
date: 2019-09-14 15:02 +0300
categories: Coding-Challenges
tags: Küp, Toplam, Kuvvet
excerpt: Programcıdan, pozitif n tamsayısını alan (nSayisi) ve 1'den n'e kadar olan tüm kübik değerleri toplayan program yazması isteniyor.
---
### Soru
Programcıdan, pozitif n tamsayısını alan **(nSayisi)** ve 1'den n'e kadar olan tüm kübik değerleri toplayan program yazması isteniyor.

### Örnek

| Girdi          | Çıktı                                          |
|----------------|------------------------------------------------|
| **nSayisi**: 2 | 9 (1<sup>3</sup>+2<sup>3</sup>)                |
| **nSayisi**: 3 | 36 (1<sup>3</sup>+2<sup>3</sup>+3<sup>3</sup>) |

### Çözüm - C#
```csharp
using System;

internal class Program
{
    private static void Main()
    {
        int nSayisi = 3;
        long sonuc = 0;

        // 1'den n'ye kadar olan tüm sayıların önce küpünü al, sonra sonuca ekle
        for (int i = 1; i <= nSayisi; i++)
        {
            sonuc += Convert.ToInt64(Math.Pow(i, 3));
        }
        
        Console.WriteLine("Sonuç: {0}", sonuc);

        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {

    public static void main(String[] args) {

        int nSayisi = 3;
        long sonuc = 0;

        // 1'den n'ye kadar olan tüm sayıların önce küpünü al, sonra sonuca ekle
        for (int i = 1; i <= nSayisi; i++)
        {
            sonuc += (long) (Math.pow(i, 3));
        }

        System.out.println("Sonuç: " + sonuc);
    }
}
```