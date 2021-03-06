---
layout: post
title: Toplam ve Ortalamayı Sınıf Oluşturarak Bul
date: 2020-07-11 12:15 +0300
categories: Coding-Challenges
tags: Sınıf, Metot, Toplam, Ortalama, Linq
excerpt: Programcıya çeşitli sayılar veriliyor. Verilen sayıların toplam ve ortalamasını ayrı bir sınıf ve metotla hesaplayan bir yapı oluşturması isteniyor...
---
### Soru
Programcıya çeşitli sayılar **(sayilar)** veriliyor. Verilen sayıların toplam ve ortalamasını ayrı bir sınıf ve metotla hesaplayan bir yapı oluşturması isteniyor.

### Örnek

| Girdi                | Çıktı                               |
|----------------------|-------------------------------------|
| **sayilar**: 1, 2, 3 | **Toplam**:  6 <br> **Ortalama**: 2 |

### Çözüm - C#
```csharp
using System.Collections.Generic;
using System.Linq;

class Matematik
{
    public int Sayi { get; set; }

    // Generic dizideki sayıları Linq ile topla
    public static int Topla(List<Matematik> sayilar)
    {
        return sayilar.Sum(i => i.Sayi);
    }

    // Generic dizideki sayıların Linq ile ortalamasını al
    public static double Ortalama(List<Matematik> sayilar)
    {
        return sayilar.Average(i => i.Sayi);
    }
}
```
<div id="ara"></div>

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Sayıları, nesne oluşturma aşamasında al
        List<Matematik> sayilar = new List<Matematik>
        {
            new Matematik {Sayi = 1110},
            new Matematik {Sayi = 2220},
            new Matematik {Sayi = 3131}
        };

        // Statik metodu işleterek toplamı ver
        int toplam = Matematik.Topla(sayilar);
        Console.WriteLine("Toplam: {0:N0}", toplam);

        // Statik metodu işleterek, ortalamayı 2 basamaklı olarak ver
        double ortalama = Matematik.Ortalama(sayilar);
        Console.WriteLine("Ortalama: {0:N2}", ortalama);

        Console.Read();
    }
}
```