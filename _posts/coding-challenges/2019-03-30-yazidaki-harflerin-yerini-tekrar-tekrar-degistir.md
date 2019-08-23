---
layout: post
title: Yazıdaki Harfleri Yerini Tekrar Tekrar Değiştir
date: 2019-03-30 19:33 +0300
categories: Coding-Challenges
tags: Değişim, Döngü
---
### Soru
Programcıya bir kelime/cümle **(yazi)** ve tekrar sayisi **(adet)** veriliyor. Sonrasında; mevcut yaziyi alarak, çift sırada yer alan karakterleri öne, tek sırada yer alan karakterleri arkaya biriktirerek birleştiren ve bunu da istenilen tekrar sayısı kadar yapan bir fonksiyon/işlev yazması isteniyor.

### Örnek

| Girdi       | Çıktı      |
|-------------|------------|
| **yazi**: Denemedir<br>**adet**: 1 | **Sonuç**: Dnmdreeei |
| **yazi**: Denemedir<br>**adet**: 2 | **Sonuç**: Dmreindee |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Text;
 
class Program
{
    static void Main()
    {
        Console.WriteLine(YerleriDegistir("Denemedir", 2));
 
        Console.Read();
    }
 
    public static string YerleriDegistir(string alinanYazi, long adet)
    {
        List<string> tekler = new List<string>();
        List<string> ciftler = new List<string>();
        StringBuilder yazi = new StringBuilder(alinanYazi);
        int sayac = 0;
 
        // Kaç defa tekrarlanacaksa o kadar döngü oluştur
        while (sayac != adet)
        {
            // Yeni ve üzerine eklemeleri önlemek için diziyi temizle
            tekler.Clear();
            ciftler.Clear();
 
            // İstenilen tek ve çift sıradaki karakterleri al ve ilgili diziye ekle
            for (int i = 0; i < alinanYazi.Length; i += 2)
            {
                tekler.Add(yazi[i].ToString());
 
                if (i + 1 != alinanYazi.Length)
                {
                    ciftler.Add(yazi[i + 1].ToString());
                }
            }
 
            // Mevcut yazıdaki birleştirmeyi temizle
            yazi.Clear();
            
            // Her iki dizideki harfleri birleştirip ilgili değişkene aktar 
            yazi.Append(string.Join("", tekler.ToArray()) + string.Join("", ciftler.ToArray()));
 
            sayac++;
        }
 
        return yazi.ToString();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
 
public class Main {
 
    public static void main(String[] args)
    {
        System.out.println((YerleriDegistir("Denemedir", 2)));
 
    }
 
    public static String YerleriDegistir(String alinanYazi, long adet)
    {
        ArrayList<String> tekler = new ArrayList<>();
        ArrayList<String> ciftler = new ArrayList<>();
        StringBuilder yazi = new StringBuilder(alinanYazi);
        int sayac = 0;
 
        // Kaç defa tekrarlanacaksa o kadar döngü oluştur
        while (sayac != adet)
        {
            // Yeni ve üzerine eklemeleri önlemek için diziyi temizle
            tekler.clear();
            ciftler.clear();
 
            // İstenilen tek ve çift sıradaki karakterleri al ve ilgili diziye ekle
            for (int i = 0; i < alinanYazi.length(); i += 2)
            {
                tekler.add(String.valueOf(yazi.charAt(i)));
 
                if (i + 1 != alinanYazi.length())
                {
                    ciftler.add(String.valueOf(yazi.charAt(i+1)));
                }
            }
 
            // Mevcut yazıdaki birleştirmeyi temizle
            yazi.setLength(0);
 
            // Her iki dizideki harfleri birleştirip ilgili değişkene aktar
            yazi.append(String.join("", tekler) + String.join("", ciftler));
 
            sayac++;
        }
 
        return yazi.toString();
    }
}
```