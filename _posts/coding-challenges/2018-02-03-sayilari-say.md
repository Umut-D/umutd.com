---
layout: post
title: Sayıları Say
date: 2018-02-03 19:33 +0300
categories: Coding-Challenges
tags: İç İçe Döngü, Sayı
---
### Soru
Programcıya, içerisinde birbiriyle aynı ya da farklı sayılar bulunan bir dizi **(verilenSayilar)** verilmiştir. Bu noktada programcıdan, kendisine verilen dizideki sayıların kaç kere tekrarlandığını bularak sonuçları sıralı, tek tek, adet olarak yazdırması istenmektedir.

### Örnek

| Girdi                                     | Çıktı                                                                                                        |
|-------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| **(verilenSayilar)**: 4, 1, 4             | 1 sayısından 1 adet var. <br>4 sayısından 2 adet var.                                                        |
| **(verilenSayilar)**: 6, 2, 1, 2, 2, 5, 5 | 1 sayısından 1 adet var.<br>2 sayısından 3 adet var.<br>5 sayısından 2 adet var.<br>6 sayısından 1 adet var. |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        int[] verilenSayilar = { 6, 2, 1, 2, 2, 5, 5 };
 
        // Verilen sayıların tekrarsız halini diziye at
        int[] gelenSayilar = verilenSayilar.Distinct().ToArray();
 
        // Tekrarsız sayıları kolayca sırala
        Array.Sort(gelenSayilar);
 
        int sayac = 0;
 
        // İç içe döngü ile karşılaştırma yap
        for (int i = 0; i < gelenSayilar.Length; i++)
        {
            for (int j = 0; j < verilenSayilar.Length; j++)
            {
                // Eğer karşılaştırma yapılan sayılar eşleşiyorsa sayacı arttır
                if (gelenSayilar[i] == verilenSayilar[j])
                {
                    sayac++;
                }
            }
 
            // Sonuçları yazdır
            Console.WriteLine(gelenSayilar[i] + " sayısından " + sayac + " adet var.");
 
            // Diğer sayının tekrarının belirlenebilmesi için sayacı sıfırla
            sayac = 0;
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
import java.util.HashSet;
 
public class Main {
    public static void main(String[] args) {
 
        Integer[] verilenSayilar = new Integer[]{6, 2, 1, 2, 2, 5, 5};
 
        // Set'ler Java'da tekrarlara izin vermiyor ve sıralı oluyor. O sebeple verilen sayıları HashSet'e atmak en kolayı geldi
        HashSet<Integer> ayiklananSayilar = new HashSet<>(Arrays.asList(verilenSayilar));
 
        // Sayaçta sorun yaşamamak için HashSet'ten gelen değerleri Object dizisine at
        Object[] gelenSayilar = ayiklananSayilar.toArray();
 
        int sayac = 0;
 
        // İç içe döngü ile karşılaştırma yap
        for (int i = 0; i < gelenSayilar.length; i++)
        {
            for (int j = 0; j < verilenSayilar.length; j++)
            {
                // Eğer karşılaştırma yapılan sayılar eşleşiyorsa sayacı arttır
                if (gelenSayilar[i] == verilenSayilar[j]) {
                    sayac++;
                }
            }
 
            // Sonuçları yazdır
            System.out.println(gelenSayilar[i] + " sayısından " + sayac + " adet var.");
 
            // Diğer sayının tekrarının belirlenebilmesi için sayacı sıfırla
            sayac = 0;
        }
    }
}
```
