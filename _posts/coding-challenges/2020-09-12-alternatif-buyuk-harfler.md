---
layout: post
title: Alternatif Büyük Harfler
date: 2020-09-12 21:55 +0300
categories: Coding-Challenges
tags: Harf, Kelime, Büyük Harf, Küçük Harf
excerpt: Programcıya küçük harfler içeren bir yazı veriliyor. Sonrasında, kelimedeki çift ve tek dizinlere gelen harfleri ayrı ayrı halde yazarak, bir diziye eklemesi isteniyor. Ayrıca, 0. dizinin çift kabul edilmesi gerektiği belirtiliyor...
---
### Soru
Programcıya küçük harfler içeren bir yazı **(girilenYazi)** veriliyor. Sonrasında, kelimedeki çift ve tek dizinlere gelen harfleri ayrı ayrı halde yazarak, bir diziye eklemesi isteniyor. Ayrıca, 0. dizinin çift kabul edilmesi gerektiği belirtiliyor.

### Örnek

| Girdi                   | Çıktı                     |
|-------------------------|---------------------------|
| **girilenYazi**: deneme | **Sonuç**: DeNeMe, dEnEmE |
| **girilenYazi**: aaaa   | **Sonuç**: AaAa, aAaA     |
| **girilenYazi**: test   | **Sonuç**: TeSt, tEsT     |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

class Program
{
    public static void Main()
    {
        string girilenYazi = "deneme";
        string ilkKelime = null, ikinciKelime = null;

        for (int i = 0; i < girilenYazi.Length; i++)
        {
            // 0,2,4... sıradaki harfleri büyük yap, diğerlerine dokunma
            if (i % 2 == 0)
                ilkKelime += girilenYazi[i].ToString().ToUpper();
            else
                ilkKelime += girilenYazi[i];

            // 1,3,5... sıradaki harfleri büyük yap, diğerlerine dokunma
            if (i % 2 != 0)
                ikinciKelime += girilenYazi[i].ToString().ToUpper();
            else
                ikinciKelime += girilenYazi[i];
        }

        List<string> sonuclar = new List<string>
        {
            ilkKelime,
            ikinciKelime
        };

        foreach (string sonuc in sonuclar)
            Console.WriteLine(sonuc);

        Console.Read();
    }
}
```