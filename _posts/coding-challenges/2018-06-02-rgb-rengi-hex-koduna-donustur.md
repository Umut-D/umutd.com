---
layout: post
title: RGB Rengi HEX Koduna Dönüştür
date: 2018-06-02 19:33 +0300
categories: Coding-Challenges
tags: RGB, HEX, Renk Dönüşümü, Dönüşüm
redirect_from:
  - /coding-challenges/rgb-rengi-hex-koduna-donustur/
  - /etiket/renk-donusumu/
---
### Soru
Programcıya, içerisinde 0 ila 255 değerleri arasında olan 3 farklı RGB değeri **(kirmiziDegeri, yesilDegeri, MaviDegeri)** veriliyor. Bu noktadan sonra ise programcıdan, girilen sayısal değerleri 16’lık Hexadecimal koda dönüştürmesi isteniyor.

> **RGB Renk**, monitör gibi elektronik cihazların ışık kullanarak renk yaratmasını sağlayan bir renk modelidir ve üç temel rengin (kırmızı, yeşil, mavi) farklı yoğunluklarda kullanılarak renk gamından istenilen rengin elde edilmesine dayanır.

### Örnek

| Girdi                                                                  | Çıktı                   |
|------------------------------------------------------------------------|-------------------------|
| **kirmiziDegeri**: 255 <br>**yesilDegeri**: 255<br>**maviDegeri**: 255 | **HEX değeri**: #FFFFFF |
| **kirmiziDegeri**: 222 <br>**yesilDegeri**: 111<br>**maviDegeri**: 33  | **HEX değeri**: #DE6F21 |

### Çözüm - C#
```csharp
using System;
using System.Drawing;
 
internal class Program
{
    private static void Main(string[] args)
    {
        byte kirmiziDegeri = 148;
        byte yesilDegeri = 0;
        byte maviDegeri  = 211;
 
        // Girilen değerlerin 255'ten büyük olmamasını sağla
        // Eğer girilen değer 255'ten büyükse değeri 255'e sabitle
        if (kirmiziDegeri > 255)
            kirmiziDegeri = 255;
        if (yesilDegeri > 255)
            yesilDegeri = 255;
        if (maviDegeri > 255)
            maviDegeri = 255;
 
        // Color sınıfını kullanarak girilen değerleri aktar
        Color donusturulenRenk = Color.FromArgb(kirmiziDegeri, yesilDegeri, maviDegeri);
 
        // Değerleri 16'lık sisteme dönüştürerek değişkene aktar
        string hexDegeri = donusturulenRenk.R.ToString("X2") + donusturulenRenk.G.ToString("X2") + donusturulenRenk.B.ToString("X2");
 
        Console.WriteLine("HEX değeri: #" + hexDegeri);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        int kirmiziDegeri = 148;
        int yesilDegeri = 0;
        int maviDegeri = 211;
 
        // Girilen değerlerin 255'ten büyük olmamasını sağla
        // Eğer girilen değer 255'ten büyükse değeri 255'e sabitle
        if (kirmiziDegeri > 255)
            kirmiziDegeri = 255;
        if (yesilDegeri > 255)
            yesilDegeri = 255;
        if (maviDegeri > 255)
            maviDegeri = 255;
 
        // Değerleri 16'lık sisteme dönüştürerek değişkene aktar
        String hexDegeri = String.format("%02X%02X%02X", kirmiziDegeri, yesilDegeri, maviDegeri);
 
        System.out.println(("HEX değeri: #" + hexDegeri));
    }
}
```