---
layout: post
title: guclu-sayi
date: 2020-08-08 16:56 +0300
categories: Coding-Challenges
tags: Harfler, Sayılar, Hesaplama, İşlem
excerpt: Programcıya bir sayı veriliyor. Bu noktadan sonra, girilen sayının güçlü sayı olup olmadığını bulan bir kod yazması isteniyor...
---
### Soru
Programcıya bir sayı **(girilenSayi)** veriliyor. Bu noktadan sonra, girilen sayının güçlü sayı olup olmadığını bulan bir kod yazması isteniyor. 

>**Güçlü sayı**, basamaklarının faktör toplamının, sayının kendisine eşit olduğu sayıdır.

### Örnek

| Girdi                | Çıktı                               |
|----------------------|-------------------------------------|
| **girdi**: 145 --> **1!+4!+5!=145**  | **Sonuç**: Güçlü Sayı! |

### Çözüm - C#
```csharp
using System;

class Program
{
    static void Main()
    {
        int girilenSayi = 145;

        // girilenSayı'yı tek tek ayır
        char[] numaralar = girilenSayi.ToString().ToCharArray();

        // Her bir karakterdeki sayının faktöriyelini al
        int faktoriyel = 1, toplam = 0;
        foreach (char karakter in numaralar)
        {
            int sayi = int.Parse(karakter.ToString());
            for (int i = sayi; i >= 1; i--)
            {
                faktoriyel *= i;
            }

            // Her bir sayının faktöriyel sonucunu toplama ekle
            toplam += faktoriyel;
            faktoriyel = 1;
        }

        // Toplam sayısını yazıya çevir ve girilen sayıyla eşit olup olmadığını kontrol et
        string toplamYazi = toplam.ToString();
        if (toplamYazi == new string(numaralar))
        {
            Console.WriteLine("Güçlü Sayı!");
        }

        Console.WriteLine("Güçlü Sayı Değil!");

        Console.Read();
    }
}
```