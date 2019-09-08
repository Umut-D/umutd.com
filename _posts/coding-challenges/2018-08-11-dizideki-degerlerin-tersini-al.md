---
layout: post
title: Dizideki Değerlerin Tersini Al
date: 2018-08-11 19:33 +0300
categories: Coding-Challenges
tags: Dizi, Ters Değer
redirect_from:
  - /coding-challenges/dizideki-degerlerin-tersini-al/
  - /etiket/dizi/
  - /etiket/ters-deger/
---
### Soru
Programcıya herhangi bir sayı dizisi **(degerler)** veriliyor. Programcıdan ise sayı dizinde yer alan rakamları matematiğe göre tersini, yani pozitif sayıların negatif, negatif sayıların pozitif hallerinin alınması isteniyor.

### Örnek

| Girdi                         | Çıktı               |
|-------------------------------|---------------------|
| **girilenSayilar**: -1, 2, -3 | **Sonuç**: 1, -2, 3 |
| **girilenSayilar**: 5, -9, -1 | **Sonuç**: -5, 9, 1 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
internal class Program
{
    private static void Main(string[] args)
    {
        int[] degerler = new[] {-1, 2, -3, 4, -5};
        List<int> dizi = new List<int>();
        int yeniSayi = 0;
 
        // Her bir değeri tek tek incele
        foreach (int sayi in degerler)
        {
            // Sayı negatif bir değerde ise
            if (sayi < 0)
            {
                // Sayının iki katı olan değeri çıkarak tersini bul
                yeniSayi = sayi - (sayi * 2);
                // Diziye ekle
                dizi.Add((yeniSayi));
            }
            // Sayı pozitif bir değerde ise
            else
            {
                // Sayının iki katı olan değeri çıkarak tersini bul
                yeniSayi = sayi - (sayi * 2);
                // Diziye ekle
                dizi.Add((yeniSayi));
            }
        }
 
        foreach (int sayilar in dizi)
        {
            Console.Write(sayilar + " ");
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.List;
 
public class Main {
    public static void main(String[] args) {
        int[] degerler = {-1, 2, -3, 4, -5};
 
        List dizi = new ArrayList<Integer>();
        int yeniSayi = 0;
 
        // Her bir değeri tek tek incele
        for (int sayi : degerler)
        {
            // Sayı negatif bir değerde ise
            if (sayi < 0)
            {
                // Sayının iki katı olan değeri çıkarak tersini bul
                yeniSayi = sayi - (sayi * 2);
                // Diziye ekle
                dizi.add((yeniSayi));
            }
            // Sayı pozitif bir değerde ise
            else
            {
                // Sayının iki katı olan değeri çıkarak tersini bul
                yeniSayi = sayi - (sayi * 2);
                // Diziye ekle
                dizi.add(yeniSayi);
            }
        }
 
        for (Object sayilar : dizi) {
            System.out.print(sayilar + " ");
        }
    }
}
```