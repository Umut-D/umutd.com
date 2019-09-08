---
layout: post
title: Saniyeleri Okunabilir Zamana Dönüştür
date: 2019-04-06 17:09 +0300
categories: Coding-Challenges
tags: Dakika, Saat, Saniye, Süre, Zaman, EPoch Zamanı
excerpt: Programcıya saniye (girilenSaniye) içeren bir sayı veriliyor. Girilen bu saniyenin ise (HH:MM:SS) formatına dönüştürülerek gösterilmesi isteniyor.
redirect_from:
  - /coding-challenges/saniyeleri-okunabilir-zamana-donustur/ 
  - /etiket/duzenlenebilir-bolge/
---
### Soru
Programcıya saniye **(girilenSaniye)** içeren bir sayı veriliyor. Girilen bu saniyenin ise (HH:MM:SS) formatına dönüştürülerek gösterilmesi isteniyor.

### Örnek

| Girdi                    | Çıktı               |
|--------------------------|---------------------|
| **girilenSaniye**: 360   | **Sonuç**: 00:06:00 |
| **girilenSaniye**: 10000 | **Sonuç**: 02:46:40 |

### Çözüm - C#
```csharp
using System;
 
class Program
{
    static void Main()
    {
        int girilenSaniye = 359999;
 
        // 1 Ocak 1970 den beridir geçen saniye sayısına denilen sayısal veri tipine Epoch/Unix zamanı denmekte 
        DateTime epochZamani = new DateTime(1970, 1, 1, 0, 0, 0, DateTimeKind.Utc);
 
        // Epoch zamanına saniyeyi ekle
        DateTime sonuc = epochZamani.AddSeconds(girilenSaniye);
 
        // Mevcut sonuçları gün, dakika, saniyelere dönüştür
        int gun = (sonuc.Day - 1) * 24 + sonuc.Hour;
        int dakika = sonuc.Minute;
        int saniye = sonuc.Second;
 
        // Dönüştürülen sayıları 2 basamaklı decimal'ler olarak birleştir
        string zaman = gun.ToString("D2") + ":" + dakika.ToString("D2") + ":" + saniye.ToString("D2");
 
        Console.WriteLine(zaman);
        Console.Read();
    }
}
```