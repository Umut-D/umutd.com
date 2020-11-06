---
layout: post
title: Sayılarla Oyna
date: 2020-10-31 16:02 +0300
categories: Coding-Challenges
tags: Sayı, Rakam, Matematik
excerpt: Programcıya sayi ve üs değerleri veriliyor. Sonrasında abcd... olarak verilen bir sayının, ardışık üsleriyle alınan basamak toplamının k * n'ye eşit olup olmadığının bulunması isteniyor. Eğer eşitlik varsa, n sayısının, değilse -1 sonucunun döndürülmesi gerektiği belirtiliyor...
---
### Soru
Programcıya sayi **(girilenSayi)** ve üs **(us)** değerleri veriliyor. Sonrasında abcd... olarak verilen bir sayının, ardışık üsleriyle alınan basamak toplamının **k * n'ye** eşit olup olmadığının bulunması isteniyor. Eğer eşitlik varsa, n sayısının, değilse -1 sonucunun döndürülmesi gerektiği belirtiliyor. 

### Örnek

| Girdi   | Çıktı                                            |
|---------|--------------------------------------------------|
| **89**  | **8¹ + 9² = 89** 89 * 1                          |
| **695** | **6² + 9³ + 5⁴ = 1390 =** 695 * 2                |
| **695** | **4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 =** 46288 * 51 |

### Çözüm - C#
```csharp
using System;

class Program
{
    public static void Main()
    {
        int girilenSayi = 89;
        int us = 1;

        // girilenSayi'yi tek tek rakamlara dönüştür
        char[] karakter = girilenSayi.ToString().ToCharArray();

        double sonuc = 0;
        foreach (char sayi in karakter)
        {
            // Her bir sayinin üssünü al ve her döngüde üs değerini arttır
            sonuc += Math.Pow(double.Parse(sayi.ToString()), us);
            us++;
        }

        // Sonuç/girilenSayi sonucu tam sayı ise sonucu yazdır
        sonuc /= girilenSayi;
        if (!(sonuc % 1 > 0))
            Console.WriteLine(sonuc);
        else
            Console.WriteLine(-1);

        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main
{
    public static void main(String[] args)
    {
        int girilenSayi = 89;
        int us = 1;

        // girilenSayi'yi tek tek rakamlara dönüştür
        char[] karakter = Integer.toString(girilenSayi).toCharArray();

        double sonuc = 0;
        for (char sayi : karakter)
        {
            // Her bir sayinin üssünü al ve her döngüde üs değerini arttır
            sonuc += Math.pow(Character.getNumericValue(sayi), us);
            us++;
        }

        // Sonuç/girilenSayi sonucu tam sayı ise sonucu yazdır
        sonuc /= girilenSayi;
        if (!(sonuc % 1 > 0))
            System.out.println((int) sonuc);
        else
            System.out.println(-1);
    }
}
```