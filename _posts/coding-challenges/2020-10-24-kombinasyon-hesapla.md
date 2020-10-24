---
layout: post
title: Kombinasyon Hesapla
date: 2020-10-24 22:17 +0300
categories: Coding-Challenges
tags: Kombinasyon, Hesap, Matematik
excerpt: Programcıya eleman ve seçim sayıları veriliyor. Ardından; bir grup içerisinden seçim yapılacağı zaman, kaç farklı tipte seçim yapılacağını bulabilen bir kod oluşturması isteniyor. Kodun, sonuç olarak çok büyük sayıları da desteklemesi gerektiği ayrıca belirtiliyor...
---
### Soru
Programcıya eleman **(elemanSayisi)** ve seçim **(secimSayisi)** sayıları veriliyor. Ardından; bir grup içerisinden seçim yapılacağı zaman, kaç farklı tipte seçim yapılacağını bulabilen bir kod oluşturması isteniyor. Kodun, sonuç olarak çok büyük sayıları da desteklemesi gerektiği ayrıca belirtiliyor.

### Örnek

| Girdi       | Çıktı              |
|-------------|--------------------|
| **(5, 4)**  | **Sonuç:** 5       |
| **(10, 5)** | **Sonuç:** 252     |
| **(52, 5)** | **Sonuç:** 2598960 |

### Çözüm - C#
```csharp
using System;
using System.Numerics;

class Program
{
    public static void Main()
    {
        // Kombinasyon formülü: C (n,p) = n!/[(n-p)!.p!]
        int elemanSayisi = 0, secimSayisi = 0;

        BigInteger ustSonuc = 1;
        for (BigInteger i = elemanSayisi; i > elemanSayisi - secimSayisi; i--)
            ustSonuc *= i;

        BigInteger altSonuc = 1;
        for (BigInteger i = secimSayisi; i > 0; i--)
            altSonuc *= i;

        BigInteger sonuc = ustSonuc / altSonuc;
        Console.WriteLine($"Sonuç: {sonuc}");

        Console.Read();
    }
}
```