---
layout: post
title: Ziyaretçi Sıralaması
date: 2017-11-04 05:23 +0300
categories: Coding-Challenges
tags: Sıralama, Web Analitik, Ziyaretçi Sayıları
---
### Soru
Bir web sitesi, 3 farklı şehirden **(a, b, c)** benzersiz ziyaretçiler almaktadır. Verilen ziyaretçi sayılarını küçükten büyüğe doğru sıralayınız.

### Örnek

| Girdi                               | Çıktı       |
|-------------------------------------|-------------|
| **a**: 200,  **b**: 100, **c**: 450 | 100 200 450 |

### Çözüm - C#
```csharp
using System;
using System.Collections;

public class Program
{
	public static void Main()
	{
        // Gelen ziyaretçi sayıları
        int a = 200, b = 100, c = 450;
 
        // Dizi oluştur ve ziyaretçi sayılarını diziye ekle
        ArrayList sayiDizisi = new ArrayList
        {
            a, b, c
        };
 
        // Dizideki verileri sırala
        sayiDizisi.Sort();
 
        // Değerleri tek tek yazdır
        foreach (int sehirler in sayiDizisi)
            Console.WriteLine(sehirler);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.Collections;
 
public class Main {
 
    public static void main(String[] args)
    {
        // Gelen ziyaretçi sayıları
        int a = 200, b = 100, c = 450;
 
        // Dizi oluştur ve ziyaretçi sayılarını diziye ekle
        ArrayList<Integer> sayiDizisi = new ArrayList<Integer>();
        sayiDizisi.add(a);
        sayiDizisi.add(b);
        sayiDizisi.add(c);
 
        // Dizideki verileri sırala
        Collections.sort(sayiDizisi);
 
        // Değerleri tek tek yazdır
        for (int sehirler:sayiDizisi) {
            System.out.println(sehirler);
        }
    }
}
```