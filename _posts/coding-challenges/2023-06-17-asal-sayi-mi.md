---
layout: post
title: Asal Sayı Mı?
date: 2023-06-17 03:02 +0300
categories: Coding-Challenges
tags: Asal, Matematik, Asal Sayı, Prime Number
excerpt: Programcıya bir sayı veriliyor ve o sayının asal sayı olup olmadığını bulması isteniyor. Ayrıca asal olmayan sayının tüm bölenlerinin de ek olarak yazdırılması gerektiği belirtiliyor...
---

### Soru

Programcıya bir sayı (**sayi**) veriliyor ve o sayının asal sayı olup olmadığını bulması isteniyor. Ayrıca, asal olmayan sayının tüm bölenlerinin de ek olarak yazdırılması gerektiği belirtiliyor.

### Örnek

| Girdi        | Çıktı                                               |
| ------------ | --------------------------------------------------- |
| **sayi**: 17 | **sonuc**: Asal sayıdır                             |
| **isim**: 18 | **sonuc**: Asal sayı değil. Bölenler: 1, 2, 3, 6, 9 |

### Çözüm - C#

```csharp
using System;
using System.Collections.Generic;

namespace CodingChallenges
{
    public class Program
    {
        public static void Main()
        {
            int sayi = 18;
            var sayininYarisi = Math.Round((double)sayi / 2 + 1);

            List<int> dizi = new List<int>();
            for (int i = 1; i < sayininYarisi; i++)
            {
                if (sayi % i == 0)
                    dizi.Add(i);
            }

            if (dizi.Count == 1)
                Console.WriteLine("Asal sayıdır");
            else
                Console.WriteLine($"Asal sayı değil. Tam bölenler: {string.Join(" ", dizi)}");

            Console.Read();
        }
    }
}
```

### Çözüm - Python

```python
sayi = 18
sayinin_yarisi = round(sayi / 2) + 1

dizi = []
for _ in range(1, sayinin_yarisi):
    if sayi % _ == 0:
        dizi.append(_)

if len(dizi) == 1:
    print("Asal sayıdır")
else:
    print("Asal sayı değil. Tam bölenler:", dizi)
```
