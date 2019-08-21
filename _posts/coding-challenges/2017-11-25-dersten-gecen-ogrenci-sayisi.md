---
layout: post
title: Dersten Geçen Öğrenci Sayısı
date: 2017-11-25 15:44 +0300
categories: Coding-Challenges
tags: Geçen Öğrenci Sayısı, Ortalama, Dersten Geçme
---
### Soru
Bir kursta yer alan öğrencilerin final notları **(fn)** elektronik ortama girilmiştir. Dersin öğretmeni ise sınıfın sene içindeki durumuna göre dersin geçme notunu **(gn)** kendisi belirlemektedir. Bu noktada ise programcıdan;

- girilen dersten geçme notuna istinaden kaç öğrencinin dersten geçtiğini **(gs)** bulması,
- (bonus) sınıfın ortalamasını **(ort)** hesaplaması istenmektedir.

### Örnek

| Girdi                                                         | Çıktı                       |
|---------------------------------------------------------------|-----------------------------|
| **fn**: 50, 72, 18, 55, 45, 94, 64, 48, 82, 36 <br>**gn**: 60 | **gs**: 4 <br>**ort**: 56,4 |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        // Değişkenler
        int[] finalNotlari = {50, 72, 18, 55, 45, 94, 64, 48, 82, 36};
        byte gecmeNotu = 60, gecenSayisi = 0;
 
        // Öğrenci notlarına tek tek bak
        foreach (var ogrencininNotu in finalNotlari)
        {
            // Eğer öğrencinin notu belirlenen geçme notundan yüksekse gecenSayisi sayacını arttır
            if (ogrencininNotu >= gecmeNotu)
                gecenSayisi++;
        }
 
        // Sonuçları yazdır
        Console.WriteLine("Dersten geçen öğrenci sayısı: " + gecenSayisi);
        Console.WriteLine("Sınıf ortalaması: " + finalNotlari.Average());
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
        
        // Değişkenler
        int[] finalNotlari = {50, 72, 18, 55, 45, 94, 64, 48, 82, 36};
        int gecmeNotu = 60, gecenSayisi = 0;
        double toplam = 0, ortalama;
 
        // Öğrenci notlarına tek tek bak
        for (int i = 0; i < finalNotlari.length; i++) {
            // Eğer öğrencinin notu belirlenen geçme notundan yüksekse gecenSayisi sayacını arttır
            if (finalNotlari[i] >= gecmeNotu)
                gecenSayisi++;
        }
 
        // Sınıfın not toplamını hesapla
        for (int i = 0; i < finalNotlari.length; i++)
            toplam = toplam + finalNotlari[i];
 
        // Sınıfın ortalama notunu hesapla
        ortalama = toplam / finalNotlari.length;
 
        // Sonuçları yazdır
        System.out.println("Dersten geçen öğrenci sayısı: " + gecenSayisi);
        System.out.println("Sınıf ortalaması: " + (ortalama));
    }
}
```
