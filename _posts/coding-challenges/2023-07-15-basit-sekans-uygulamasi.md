---
layout: post
title: Basit Sekans Uygulaması
date: 2023-07-08 03:02 +0300
categories: Coding-Challenges
tags: Sekans, Dizi, İlerleme
excerpt: Programcıdan n'inci terim de dahil olmak üzere, 0'dan n'ye kadar olan sayıların toplamını diziye aktaran bir uygulama yazması isteniyor. Negatif sayının negatif, pozitif sayınınsa pozitif bir dizide olması gerektiği not düşülüyor...
---

### Soru

Programcıdan n'inci terim de dahil olmak üzere, 0'dan n'ye kadar olan sayıların toplamını diziye aktaran bir uygulama yazması isteniyor. Negatif sayının negatif, pozitif sayınınsa pozitif bir dizide olması gerektiği not düşülüyor.

### Örnek

| Girdi     | Çıktı                                        |
| --------- | -------------------------------------------- |
| **n**: 5  | **sonuc**: 0, 1, 3, 6, 10, 15                |
| **n**: -7 | **sonuc**: 0, -1, -3, -6, -10, -15, -21, -28 |

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
            int nDegeri = -5;

            // Sınır değerini, yani döngünün kaçıncı sayıya kadar olacağını belirle
            int sinir = Math.Abs(nDegeri) + 1;
            List<int> dizi = new List<int>();

            // Mevcut işarete göre işlem yap
            bool pozitifMi = Math.Sign(nDegeri) > 0;

            // N'ye kadar devam et
            for (int i = 1; i <= sinir; i++)
            {
                int toplam = 0;
                for (int j = 0; j < i; j++)
                {
                    // Sayının değerine göre pozitif veya negatif toplam yap
                    if (pozitifMi)
                        toplam += j;
                    else
                        toplam -= j;
                }

                // Toplamı diziye ekle
                dizi.Add(toplam);
            }

            Console.WriteLine(string.Join(" ", dizi));

            Console.Read();
        }
    }
}
```

```python
import math

nDegeri = 5

# Sınır değerini, yani döngünün kaçıncı sayıya kadar olacağını belirle
sinir = math.fabs(nDegeri) + 1
dizi = []

# Mevcut işarete göre işlem yap
pozitifMi = nDegeri > 0

# N'ye kadar devam et
for i in range(1, int(sinir) + 1):
    toplam = 0
    for j in range(i):
        # Sayının değerine göre pozitif veya negatif toplam yap
        if pozitifMi:
            toplam += j
        else:
            toplam -= j
    # Toplamı diziye ekle
    dizi.append(toplam)

print(dizi)
```
