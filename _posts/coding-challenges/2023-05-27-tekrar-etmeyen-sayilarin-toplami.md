---
layout: post
title: Tekrar Etmeyen Sayıların Toplamı
date: 2023-05-27 03:02 +0300
categories: Coding-Challenges
tags: Dizi, Sayı, Tekrar
excerpt: Programcıya; bir dizi sunuluyor ve mevcut dizide tekrar etmeyen sayıların toplamını alması isteniyor...
---

### Soru

Programcıya; bir dizi sunuluyor ve mevcut dizide tekrar etmeyen sayıların toplamını alması isteniyor.

### Örnek

| Girdi                      | Çıktı         |
| -------------------------- | ------------- |
| **dizi**: 4, 5, 7, 5, 4, 8 | **sonuc**: 15 |
| **dizi**: 5, 5, 6, 6, 1, 2 | **sonuc**: 3  |

### Çözüm - C#

```csharp
using System;
using System.Linq;

namespace CodingChallenges
{
    public class Program
    {
        static void Main()
        {
            var dizi = new List<int> { 4, 5, 7, 5, 4, 8 };

            // Diziyi önce gruplandır, ardından grupta sadece 1 kere olanları al
            var gruplandir = dizi
                .GroupBy(sayi => sayi)
                .Where(s => s.Count() < 2);

            // Dönen gruplandırma değerinde, anahtar değerleri topla
            Console.WriteLine(gruplandir.Sum(s => s.Key));

            Console.Read();
        }
    }
}
```

### Çözüm - Python

```python
dizi = [4, 5, 7, 5, 4, 8 ]

toplam = 0
for sayi in dizi:
    # Dizideki her bir sayıyı incelerken bir kere tekrar edenleri toplama dahil et
    if dizi.count(sayi) < 2:
        toplam += sayi

print(toplam)
```
