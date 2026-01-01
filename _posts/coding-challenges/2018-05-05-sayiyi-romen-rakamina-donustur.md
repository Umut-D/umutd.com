---
layout: post
title: Sayıyı Romen Rakamına Dönüştür
date: 2018-05-05 19:33 +0300
categories: Coding-Challenges
tags: Dönüşüm, Romen Rakamı, Romen Sayısı
redirect_from:
  - /coding-challenges/sayiyi-romen-rakamina-donustur/
  - /etiket/romen-rakami/
---
### Soru
Programcıya, rastgele bir sayı **(girilenSayi)** veriliyor ve mevcut sayıyı romen rakamına dönüştürmesi isteniyor.

**Not**: Girilen sayının en fazla 3999’a kadar olması isteniyor.

### Örnek

| Girdi               | Çıktı           |
|---------------------|-----------------|
| **girilenSayi**: 11 | **Sonuç**: XI   |
| **girilenSayi**: 8  | **Sonuç**: VIII |

### Çözüm - C#
```csharp
using System;

namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            int girilenSayi = 8;
            string romenRakami = null;

            // Romen rakamlarını dizi olarak belirt
            string[] binlerBasamagi = {"", "M", "MM", "MMM"};
            string[] yuzlerBasamagi = {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
            string[] onlarBasamagi = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
            string[] birlerBasamagi = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};

            // Girilen sayının basamak durumuna göre (Örn. 17) 10'a böl, kalan sayısı belirle.
            // Elde edilen sayıyı ilgili diziden alarak değişkene ekle
            romenRakami += binlerBasamagi[(girilenSayi / 1000) % 10];
            romenRakami += yuzlerBasamagi[(girilenSayi / 100) % 10];
            romenRakami += onlarBasamagi[(girilenSayi / 10) % 10];
            romenRakami += birlerBasamagi[girilenSayi % 10];

            Console.WriteLine("Sonuç: " + romenRakami);

            Console.Read();
        }
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {

        int girilenSayi = 8;
        String romenRakami = "";

        // Romen rakamlarını dizi olarak belirt
        String[] binlerBasamagi = {"", "M", "MM", "MMM"};
        String[] yuzlerBasamagi = {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
        String[] onlarBasamagi = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
        String[] birlerBasamagi = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};

        // Girilen sayının basamak durumuna göre (Örn. 17) 10'a böl, kalan sayısı belirle.
        // Elde edilen sayıyı ilgili diziden alarak değişkene ekle
        romenRakami += binlerBasamagi[(girilenSayi / 1000) % 10];
        romenRakami += yuzlerBasamagi[(girilenSayi / 100) % 10];
        romenRakami += onlarBasamagi[(girilenSayi / 10) % 10];
        romenRakami += birlerBasamagi[girilenSayi % 10];

        System.out.println("Sonuç: " + romenRakami);
    }
}
```