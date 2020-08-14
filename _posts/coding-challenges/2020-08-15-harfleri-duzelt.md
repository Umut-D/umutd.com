---
layout: post
title: Harfleri Düzelt
date: 2020-08-15 10:56 +0300
categories: Coding-Challenges
tags: Harfler, Kelime, Büyük Harf, Küçük Harf
excerpt: Programcıya bir kelime veriliyor. Kelimedeki büyük ve küçük harf sayısına göre,  harflerin tümünü büyük veya küçük yazan bir program oluşturması isteniyor...
---
### Soru
Programcıya bir kelime **(girilenYazi)** veriliyor. Kelimedeki büyük ve küçük harf sayısına göre,  harflerin tümünü büyük veya küçük yazan bir program oluşturması isteniyor. Dolasıyla kelimede;

* Büyük harfler çoğunlukta ise, tüm harflerin büyük,
* Küçük harfler çoğunlukta ise, tüm harflerin küçük,
* Küçük ve büyük harfler eşit ise, tüm harflerin küçük olması isteniyor.

### Örnek

| Girdi                  | Çıktı            |
|------------------------|------------------|
| **girilenYazi**: coder (Küçük harflerden oluşmuş) | **Sonuç**: coder |
| **girilenYazi**: CODer (Büyük harfler çoğunlukta)| **Sonuç**: CODER |
| **girilenYazi**: CodeR (Küçük harfler çoğunlukta)| **Sonuç**: coder |
| **girilenYazi**: CoDE (Büyük ve küçük harfler eşit)| **Sonuç**: code |

### Çözüm - C#
```csharp
using System;

class Program
{
    public static void Main()
    {
        string girilenYazi = "CODer";

        int buyukHarfSayisi = 0;
        foreach (char karakter in girilenYazi)
        {
            // Her bir karakteri incelerken büyük harfleri say
            if (char.IsUpper(karakter))
                buyukHarfSayisi++;
        }

        // Kelime uzunluğundan büyük harf sayısını çıkar
        int fark = girilenYazi.Length - buyukHarfSayisi;
        // Büyük harf sayısı kelime uzunluğunda az veya ona eşitse küçük harfli yaz
        if (fark > buyukHarfSayisi || fark == buyukHarfSayisi)
            Console.WriteLine("Sonuç: {0}", girilenYazi.ToLower());
        // Büyük harf sayısı kelime uzunluğunda fazlaysa büyük harfli yaz
        else
            Console.WriteLine("Sonuç: {0}", girilenYazi.ToUpper());

        Console.Read();
    }
}
```