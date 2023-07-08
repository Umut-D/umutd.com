---
layout: post
title: Kartezyen Komşular
date: 2023-07-08 03:02 +0300
categories: Coding-Challenges
tags: Koordinat, Kartezyen, Komşu Noktalar
excerpt: Programcıya, ızgaradaki bir noktanın koordinatları (x ve y) veriliyor. Bu noktadan sonra ise; x ekseni ve y ekseninde olan ve tüm komşu noktaların listesini döndüren bir kod yazması bekleniyor...
---

### Soru

> **Kartezyen koordinat sistemi**, 2 boyutlu bir yüzey üzerindeki bir noktanın veya 3 boyutlu bir uzaydaki (boşluktaki) bir objenin yerini belirlemek ve belirtmek için kullanılır. Eksenlerin kesişme noktasına koordinat merkezi, başlangıç noktası veya orijin adı verilir. Eksenler ise x, y, z adlarıyla anılır. Bir yüzeyde veya uzayda bir noktanın yeri, bu eksenler üzerinden orijine olan uzaklıkları olup x, y, z cinsinden ifade edilir.

Programcıya, ızgaradaki bir noktanın koordinatları (x ve y) veriliyor. Bu noktadan sonra ise; x ekseni ve y ekseninde olan ve tüm komşu noktaların listesini döndüren bir kod yazması bekleniyor.

### Örnek

| Girdi          | Çıktı                                                      |
| -------------- | ---------------------------------------------------------- |
| **x, y**: 2, 2 | **sonuc**: {1,1},{1,2},{1,3},{2,1},{2,3},{3,1},{3,2},{3,3} |
| **x, y**: 5, 7 | **sonuc**: {6,7},{6,6},{6,8},{4,7},{4,6},{4,8},{5,6},{5,8} |

### Çözüm - C#

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace CodingChallenges
{
    public class Program
    {
        public static void Main()
        {
            int x = 2;
            int y = 2;

            // Önceki, mevcut, sonraki alanları değişken dizisine ekle
            int[] xKoordinati = { x - 1, x, x + 1 };
            int[] yKoordinati = { y - 1, y, y + 1 };

            // İki farklı değişkenleri verileri birleştir
            var degerler = xKoordinati.SelectMany(k => yKoordinati, (x1, y1) => new[] { x1, y1 });

            var koordinatlar = new List<int[]>(degerler);
            var yeniKoordinat = new List<int[]>();
            foreach (int[] ints in koordinatlar)
            {
                // İki koleksiyonu karşılaştırarak tüm elemanların aynı dizilimde olduğuna bak
                var sekans = new[] { x, y }
            .SequenceEqual(new[] { ints[0], ints[1] });
                if (sekans)
                    continue;

                yeniKoordinat.Add(new[] { ints[0], ints[1] });
            }

            // Önceki, mevcut, sonraki her bir koordinatı yazdır
            yeniKoordinat.ForEach(k =>
            {
                foreach (int sayi in k)
                {
                    Console.Write(sayi + " ");
                }

                Console.WriteLine();
            });

            Console.Read();
        }
    }
}
```
