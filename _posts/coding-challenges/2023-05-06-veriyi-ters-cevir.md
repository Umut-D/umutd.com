---
layout: post
title: Veriyi Ters Çevir
date: 2023-04-29 03:02 +0300
categories: Coding-Challenges
tags: Veri, Bit, Ters, Ters Sıralama
excerpt: Programcıya bir veri akışı veriliyor. Programcıdan ise bunu tersine çevrilmesi isteniyor. Her segmentin 8 bit uzunluğunda olduğu belirtiliyor ve bu segmentlerin sırasının tersine çevrilmesi gerektiği söyleniyor...
---

### Soru

Programcıya bir veri akışı veriliyor. Programcıdan ise bunu tersine çevrilmesi isteniyor. Her segmentin 8 bit uzunluğunda olduğu belirtiliyor ve bu segmentlerin sırasının tersine çevrilmesi gerektiği söyleniyor.

### Örnek

| Girdi                                   | Çıktı                                   |
| --------------------------------------- | --------------------------------------- |
| **11111111 00000000 00001111 10101010** | **10101010 00001111 00000000 11111111** |

### Çözüm - C#

```csharp
using System;

class Program
{
    public static void Main()
    {
        int[] veriler = new[] { 11111111, 00000000, 00001111, 10101010 };

        List<int> dizi = new List<int>();
        for (int i = veriler.Length - 1; i >= 0; i--)
        {
            if (i % 8 == 0)
            {
                dizi.AddRange(veriler.Skip(i).Take(8));
            }
        }

        string veri = "";
        foreach (int sayilar in dizi)
        {
            veri += sayilar.ToString().PadLeft(8, '0');
        }

        Console.Write(veri);

        Console.Read();
    }
}
```
