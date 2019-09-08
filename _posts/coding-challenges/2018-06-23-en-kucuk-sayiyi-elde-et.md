---
layout: post
title: En Küçük Sayıyı Elde Et
date: 2018-06-23 19:33 +0300
categories: Coding-Challenges
tags: Dizi, En Küçük Sayı
redirect_from:
  - /coding-challenges/en-kucuk-sayiyi-elde-et/
  - /etiket/en-kucuk-sayi/
---
### Soru
Programcıya aynı veya farklı rakamlarda oluşan bir sayı dizisi **(sayiDizisi)** sunuluyor. Programcıdan ise öncelikle, dizide birbiri ile aynı olan rakamları yok etmesi, ardından elde kalan benzersiz rakamlar ile en küçük sayıyı elde etmesi isteniyor.

### Örnek

| Girdi                         | Çıktı          |
|-------------------------------|----------------|
| **sayiDizisi**: 7, 7, 4, 4, 1 | **Sonuç**: 147 |
| **sayiDizisi**: 3, 3, 1       | **Sonuç**: 13  |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        int[] sayiDizisi = new[] {7, 7, 4, 4, 1};
        string sonuc = "";
 
        // Dizide birbiri ile aynı olan sayıları yok et
        int[] yeniDizi = sayiDizisi.Distinct().ToArray();
 
        // Yeni oluşturulan dizideki sayıları küçükten büyüğe sırala
        Array.Sort(yeniDizi);
 
        // Dizide bulunan sıralanmış sayıları string değişkene at
        foreach (int sayilar in yeniDizi)
        {
            sonuc += sayilar.ToString();
        }
 
        Console.WriteLine(sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
import java.util.Set;
import java.util.TreeSet;
 
public class Main {
    public static void main(String[] args) {
 
        Integer[] sayiDizisi = {7, 7, 4, 4, 1};
        String sonuc = "";
 
        Set<Integer> yeniDizi = new TreeSet<>();
 
        // Dizide birbiri ile aynı olan sayıları yok et
        yeniDizi.addAll(Arrays.asList(sayiDizisi));
 
        // Yeni oluşturulan dizideki sayıları küçükten büyüğe sırala
        Arrays.sort(yeniDizi.toArray());
 
        // Dizide bulunan sıralanmış sayıları string değişkene at
        for (int sayilar : yeniDizi)
        {
            sonuc += sayilar;
        }
 
        System.out.println(sonuc);
    }
}
```