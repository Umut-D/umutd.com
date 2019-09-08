---
layout: post
title: Aynı Dersi Seçen Öğrenciler
date: 2017-12-09 16:05 +0300
categories: Coding-Challenges
tags: Ders Seçimi, Ders Alma
redirect_from:
  - /coding-challenges/ayni-dersi-secen-ogrenciler/
  - /etiket/ayni-ders-secimi/
---
### Soru
Bir üniversitede okuyan öğrenciler A **(aDersiniAlanlar)** veya B **(bDersiniAlanlar)** dersini seçmişlerdir. Bazı öğrenciler ise hem A hem B dersini seçmiştir. A ve B derslerinin danışman hocası her iki dersi alan, ortak öğrencileri görmek istemektedir. 

Bu noktada programcıdan istenen; her iki dersi de alan öğrenci numaralarını tespit etmesi ve ilgili öğrenci numaralarını sıralı bir şekilde yazması istenmektedir.

### Örnek

| Girdi                                                                                        | Çıktı                 |
|----------------------------------------------------------------------------------------------|-----------------------|
| **aDersiniAlanlar**: 10, 60, 80, 70, 40, 90 <br> **bDersiniAlanlar**: 50, 30, 20, 10, 90, 60 | **Sonuç**: 10, 60, 90 |
| **aDersiniAlanlar**: 5, 8, 1 <br> **bDersiniAlanlar**: 1, 6, 2, 8, 9                         | **Sonuç**: 1,8        |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        // A ve B derslerini alan öğrencilerin öğrenci numaraları
        int[] aDersiniAlanlar = {10, 60, 80, 70, 40, 90};
        int[] bDersiniAlanlar = {50, 30, 20, 10, 90, 60};
 
        // Her iki dersi seçen (aynı) öğrencileri bul (Yaşasın Linq!)
        IEnumerable<int> ikiDersiSecenler = aDersiniAlanlar.Intersect(bDersiniAlanlar);
 
        // Her iki dersi seçen (aynı) öğreleri sırala (Yaşasın Linq!) 
        IEnumerable<int> siraliListe = ikiDersiSecenler.OrderBy(i => i);
 
        // Aynı dersi seçen öğrencileri sıralı olarak yazdır
        foreach (var secimYapanlar in siraliListe)
            Console.Write(secimYapanlar + " ");
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
 
public class Main {
 
    public static void main(String[] args) {
        int[] quizSonuclari = {1, 4, 3, 4};
 
        // Sıralı sonuçlar dizisi oluştur ve Quiz sonuçlarını kopyala
        int[] siraliSonuclar = quizSonuclari.clone();
 
        // Sıralı sonuçlar dizisini küçükten büyüğe sırala
        Arrays.sort(siraliSonuclar);
 
        // İki dizideki sonuçlar birbiriyle eşdeğer ise Başarılı, değilse Başarısız yaz
        if (Arrays.equals(siraliSonuclar, quizSonuclari))
            System.out.println("Başarılı");
        else
            System.out.println("Başarısız");
    }
}
```