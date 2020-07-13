---
layout: post
title: Toplam ve Ortalamayı Sınıf Oluşturarak Bul
date: 2020-07-11 12:15 +0300
categories: Coding-Challenges
tags: Sınıf, Metot, Toplam, Ortalama, Linq
excerpt: Programcıya çeşitli sayılar veriliyor. Verilen sayıların toplam ve ortalamasını ayrı bir sınıf ve metotla hesaplayan bir yapı oluşturması isteniyor....
---
### Soru
Programcıya çeşitli sayılar **(sayilar)** veriliyor. Verilen sayıların toplam ve ortalamasını ayrı bir sınıf ve metotla hesaplayan bir yapı oluşturması isteniyor.

### Örnek

| Girdi                | Çıktı                               |
|----------------------|-------------------------------------|
| **sayilar**: 1, 2, 3 | **Toplam**:  6 <br> **Ortalama**: 2 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Matematik
{
    public int Sayi { get; set; }

    // Generic dizideki sayıları al ve Linq ile topla
    public static int Topla(List<Matematik> sayilar)
    {
        return sayilar.Sum(i => i.Sayi);
    }

    // Generic dizideki sayıları al ve Linq ile ortalama al
    public static double Ortalama(List<Matematik> sayilar)
    {
        return sayilar.Average(i => i.Sayi);
    }
}

class Program
{
    static void Main()
    {
        // Sayıları al
        List<Matematik> sayilar = new List<Matematik>
        {
            new Matematik {Sayi = 1110},
            new Matematik {Sayi = 2220},
            new Matematik {Sayi = 3131}
        };

        int toplam = Matematik.Topla(sayilar);
        Console.WriteLine("Toplam: {0:N0}", toplam);

        double ortalama = Matematik.Ortalama(sayilar);
        Console.WriteLine("Ortalama: {0:N2}", ortalama);

        Console.Read();
    }
}
```