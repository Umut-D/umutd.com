---
layout: post
title: Şanssız Günler
date: 2023-07-29 03:02 +0300
categories: Coding-Challenges
tags: Gün, Tarih
excerpt: Programcıdan, belirli bir yılda kaç tane şanssız gün (13. Cuma) olduğunu hesaplayan bir kod yazması isteniyor...
---

### Soru

> **13. Cuma veya Kara Cuma**, Batı'nın hurafe anlayışında şanssız bir gün olarak kabul edilir. Miladi takvimde ayın 13. günü, her yıl en az bir kez olan ancak aynı yıl içinde üç defaya kadar meydana gelebilen bir Cuma gününe denk geldiğinde ortaya çıkar.

Programcıdan, belirli bir yılda kaç tane şanssız gün (13. Cuma) olduğunu hesaplayan bir kod yazması isteniyor.

### Örnek

| Girdi                 | Çıktı        |
| --------------------- | ------------ |
| **girilenSayi**: 2015 | **sonuc**: 3 |
| **girilenSayi**: 1986 | **sonuc**: 1 |

### Çözüm - C#

```csharp
using System;

namespace CodingChallenges
{
    public class Program
    {
        public static void Main()
        {
            int girilenYil = 2013;

            int onUcuncuCumaAdedi = 0;
            // Yılın her bir ayına tek tek bak
            for (int i = 1; i <= 12; i++)
            {
                var yil = new DateTime(girilenYil, i, 13);
                // Ayın 13. günü Cuma'ya denk geliyorsa sayacı arttır
                if (yil.DayOfWeek == DayOfWeek.Friday)
                    onUcuncuCumaAdedi++;
            }

            Console.WriteLine(onUcuncuCumaAdedi);

            Console.Read();
        }
    }
}
```
