---
layout: post
title: Hemen Çıkma Oranı
date: 2017-11-11 23:41 +0300
categories: Coding-Challenges
tags: Hemen Çıkma Oranı, Web Analitik
---
### Soru
Bir web sitesini, çeşitli zamanlarda farklı kullanıcılar ziyaret etmektedir. Siteye giren kullanıcıların sitede geçirdikleri zamanlar birbirinden farklıdır ve sitede kaldıkları bu sürenin kaydı tutulmaktadır.

Siteye giren toplam ziyaretçilerin **(tk)** sayısı ile, hemen çıkma oranı (sitede 10 saniyeden az kalıp giden) yüzdesine **(h)** sahip olan ziyaretçilerin oranı verilmiştir. Bu noktada ise programcıdan;

- sitede kalmaya devam eden ziyaretçilerin sayısını bulması,
- (eğer varsa) ondalık sayıya sahip sonuçları (örn. 7.1 veya 7.9) aşağı yuvarlaması istenmektedir.

### Örnek

| Girdi           | Çıktı |
|-----------------|-------|
| tk: 1000, b: 25 | 750   |
| tk: 835, b: 17  | 693   |

### Çözüm - C#
```csharp
using System;
 
public class Program
{
    private static void Main(string[] args)
    {
        // Verilen toplam ziyaretçi sayısı ve hemen çıkma oranı
        int toplamZiyaretci = 1000, hemenCikmaOrani = 25;
 
        double oranlamaSonucu = (Convert.ToDouble(hemenCikmaOrani)/100)*toplamZiyaretci;
 
        // Oranlanan sonucu aşağı yuvarla
        double yuvarlamaSonucu = Math.Floor(oranlamaSonucu);
 
        // Sonucu yazdır
        Console.WriteLine(toplamZiyaretci - yuvarlamaSonucu);
 
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
        // Verilen toplam ziyaretçi sayısı ve hemen çıkma oranı
        int toplamZiyaretci = 850, hemenCikmaOrani = 17;
 
        // İşlem alanı
        double oranlamaSonucu = ((double) (hemenCikmaOrani) / 100) * toplamZiyaretci;
 
        // Oranlanan sonucu aşağı yuvarla
        double yuvarlamaSonucu = Math.floor(oranlamaSonucu);
        
        // Ondalık ekini yok etmek için DecimalFormat sınıfı kullan
        DecimalFormat ondalikAt = new DecimalFormat("0.#");
        
        // Sonucu ondalıksız yazdır
        System.out.println(ondalikAt.format(toplamZiyaretci - yuvarlamaSonucu));
    }
}
```