---
layout: post
title: Sayılar Arasındaki En Büyük ve En Küçük Sayıyı Bul
date: 2018-06-30 19:33 +0300
categories: Coding-Challenges
tags: Dizi, En Büyük Sayı, En Küçük Sayı
---
### Soru
Programcıya aynı veya farklı rakamlarda oluşan bir sayı metini **(girilenSayilar)** veriliyor. Programcıdansa metinde yer alan ve aralarında boşluk olan sayıların içerisindeki en büyük ve en küçük sayıları bularak sonuç olarak yazdırması isteniyor.

### Örnek

| Girdi                           | Çıktı                                                            |
|---------------------------------|------------------------------------------------------------------|
| **girilenSayilar**: 1 5 4 6 8 3 | **Sonuç 1**: En büyük sayı: 8<br> **Sonuç 2**: En küçük sayı: 1  |
| **girilenSayilar**: 22 11 33 5  | **Sonuç 1**: En büyük sayı: 33<br> **Sonuç 2**: En küçük sayı: 5 |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenSayilar = "1 5 4 6 8 3";
 
        // Girilen sayıları al ve diziye ayrı at
        // Bu noktada Linq devreye giriyor ve işleri kolaylaştırıyor
        int[] ints = girilenSayilar.Split(' ').Select(int.Parse).ToArray();
 
        // Dizi içindeki en büyük ve en küçük sayıları bul
        int enBuyuk = ints.Max();
        int enKucuk = ints.Min();
 
        Console.WriteLine("En büyük sayı: " + enBuyuk);
        Console.WriteLine("En küçük sayı: " + enKucuk);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
 
public class Main {
    public static void main(String[] args) {
 
        String girilenSayilar = "1 5 4 6 8 3";
 
        // Girilen sayıları al ve ayırarak diziye at
        String[] girilenSayiDizisi = girilenSayilar.split(" ");
 
        // Sayı dizisi için int türünde dizi oluştur
        List<Integer> sayiDizisi = new ArrayList<>();
 
        // String dizideki sayıları int olarak oluşturulan diziye at
        for (int i = 0; i < girilenSayiDizisi.length; i++)
        {
            sayiDizisi.add(Integer.parseInt(girilenSayiDizisi[i]));
        }
 
        // Dizi içindeki en büyük ve en küçük sayıları bul
        int enBuyuk = Collections.max(sayiDizisi);
        int enKucuk = Collections.min(sayiDizisi);
 
        System.out.println("En büyük sayı: " + enBuyuk);
        System.out.println("En küçük sayı: " + enKucuk);
    }
}
```