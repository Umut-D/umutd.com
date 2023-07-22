---
layout: post
title: Virgülle Gruplandırılmış Sayı
date: 2023-07-22 03:02 +0300
categories: Coding-Challenges
tags: Sayı, Virgül
excerpt: Programcıya 2147483647'i geçmeyen bir sayı veriliyor ve programcıdan sayıyı her 3 basamaktan sonra virgüllerle ayrılmış hale getirmesi isteniyor...
---

### Soru

Programcıya 2147483647'i geçmeyen bir sayı (girilenSayi) veriliyor ve programcıdan sayıyı her 3 basamaktan sonra virgüllerle ayrılmış hale getirmesi isteniyor.

### Örnek

| Girdi                         | Çıktı                   |
| ----------------------------- | ----------------------- |
| **girilenSayi**: 1234567      | **sonuc**: "1,234,567"  |
| **girilenSayi**: -35235235 -> | **sonuc**: "35,235,235" |

### Çözüm - C#

```csharp
using System;

public class Program
{
    public static void Main()
    {
        // 1. Şakkadanak çözüm
        var girilenSayi1 = 12441500.ToString("N0");
        Console.WriteLine(girilenSayi1.Replace(".", ","));

        // 2. İşleri uzatarak çözüm
        int girilenSayi2 = 12441500;

        // Sayıyı karakter dizisine dönüştürerek tersine çevir
        char[] sayilar = Convert.ToString(girilenSayi2).ToCharArray();
        Array.Reverse(sayilar);

        int sayac = 0;
        string sonuc = "";
        // Ters çevirilen dizide, her üçer üçer devamda virgül ekle
        foreach (char sayi in sayilar)
        {
            sayac++;
            if (sayac % 3 == 0)
                sonuc += sayi + ",";
            else
                sonuc += sayi;
        }

        // Son alandaki virgülü kaldır ve karakter dizisine dönüştürüp ters çevir
        char[] charArray = sonuc.TrimEnd(',').ToCharArray();
        Array.Reverse(charArray);

        sonuc = new string(charArray);
        Console.WriteLine(sonuc);

        Console.Read();
    }
}
```

### Çözüm - Python

```python
girilen_sayi = 124415

dizi = []
for sayi in str(girilen_sayi):
    dizi.append(sayi)

sayac = 0
ters_sayi = ""
# Ters çevirilen dizide, her üçer üçer devamda virgül ekle
for sayi in dizi[::-1]:
    sayac += 1
    if sayac % 3 == 0:
        ters_sayi += sayi + ","
    else:
        ters_sayi += sayi

# Son alandaki virgülü kaldır ve karakter dizisine dönüştürüp ters çevir
sonuc = ters_sayi[::-1].strip(',')

print(sonuc)
```
