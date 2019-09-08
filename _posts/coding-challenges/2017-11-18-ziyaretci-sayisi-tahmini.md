---
layout: post
title: Ziyaretçi Sayısı Tahmini
date: 2017-11-18 15:40 +0300
categories: Coding-Challenges
tags: Tahmin, Ziyaretçi Sayısı Tahmini
redirect_from:
  - /coding-challenges/ziyaretci-sayisi-tahmini/
  - /etiket/ziyaretci-sayisi-tahmini/
---
### Soru
Bir web sitesini gelen benzersiz ziyaretçi oranı, bir önceki haftaya göre düzenli olarak %7 oranında artmaktadır. Siteye giren benzersiz ziyaretçilerin **(bz)** sayısı ile, geçecek hafta **(h)** sayısı programcıya verilmiştir. 

Bu noktada programcıdan; **h** hafta geçtikten sonra benzersiz ziyaretçi sayısının kaç olacağını ve (eğer varsa) ondalık sayıya sahip sonuçları (örn. 2.1 veya 2.9) aşağı yuvarlayarak bulması istenmektedir.

### Örnek

| Girdi                | Çıktı |
|----------------------|-------|
| **bz**: 10, **h**: 3 | 12    |
| **bz**: 40, **h**: 1 | 42    |

### Çözüm - C#
```csharp
using System;
 
internal class Program
{
    private static void Main(string[] args)
    {
        // Verilen benzerszi ziyaretçi sayısı ve geçecek hafta sayısı
        int ziyaretciSayisi = 100, gecenHaftaSayisi = 3;
 
        // Sonuç 0'dan değil, ziyaretçi sayısından başlasın
        double sonuc = ziyaretciSayisi;
 
        // Gerekli hesaplamayı kaç kere tekrar ediliyorsa yap ve ziyaretçi sayısının üzerine ekle
        for (int i = 0; i < gecenHaftaSayisi; i++)
        {
            sonuc += (sonuc*0.07);
        }
 
        // Sonucu aşağı yuvarla
        Console.WriteLine(Math.Floor(sonuc));
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.text.DecimalFormat;
 
public class Main {
 
    public static void main(String[] args)
    {
        // Verilen benzerszi ziyaretçi sayısı ve geçecek hafta sayısı
        int ziyaretciSayisi = 100, gecenHaftaSayisi = 3;
 
        // Sonuç 0'dan değil, ziyaretçi sayısından başlasın
        double sonuc = ziyaretciSayisi;
 
        // Gerekli hesaplamayı kaç kere tekrar ediliyorsa yap ve ziyaretçi sayısının üzerine ekle
        for (int i = 0; i < gecenHaftaSayisi; i++)
        {
            sonuc += (sonuc*0.07);
        }
 
        // Ondalık ekini yok etmek için DecimalFormat sınıfı kullan
        DecimalFormat ondalikAt = new DecimalFormat("0.#");
 
        // Sonucu ondalıksız yazdır
        System.out.println(ondalikAt.format(Math.floor(sonuc)));
    }
}
```