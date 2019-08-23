---
layout: post
title: Değerler Arka Arkaya Geliyor Mu?
date: 2018-11-03 19:33 +0300
categories: Coding-Challenges
tags: Art Arda, Dizi, Sıra
---
### Soru
Programcıya artan veya azalan değerleri olan bir sayı dizisi **(dizi)** veriliyor. Programcıdansa sayı dizinde yer alan rakamların ileri ve geri arka arkaya, yani sıralı bir şekilde gidip gitmediğini, belirleyen bir yapı oluşması bekleniyor.

### Örnek

| Girdi                       | Çıktı                                |
|-----------------------------|--------------------------------------|
| **(dizi)**: 5, 6, 7         | **Sonuç**: Evet, arka arkaya.        |
| **(dizi)**: 11, 10, 9, 8, 7 | **Sonuç**: Evet, arka arkaya.        |
| **(dizi)**: 3, 5, 2         | **Sonuç**: Hayır, arka arkaya değil. |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
class Program
{
    static void Main()
    {
        // Girilen dizi
        int[] dizi = new int[] {4, 3, 2};
        int[] yeniDizi = new int[dizi.Length];
        int ilkSayi = dizi[0];
 
        // Girilen dizideki ilk iki sayı arasındaki farkı bul
        // Eğer fark pozitif ise yeniDiziyi oluştur
        if (dizi[1] - dizi[0] > 0)
        {
            for (int i = 0; i < dizi.Length; i++)
            {
                yeniDizi[i] = ilkSayi + i;
            }
        }
        // Eğer fark negatif ise yeniDiziyi oluştur
        else
        {
            for (int i = 0; i < dizi.Length; i++)
            {
                yeniDizi[i] = ilkSayi - i;
            }
        }
 
        // Dizinin art arda olup olmadığını kontrol et [Linq sağolsun]
        if (dizi.SequenceEqual(yeniDizi))
            Console.WriteLine("Evet, arka arkaya.");
        else
            Console.WriteLine("Hayır, arka arkaya değil.");
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
 
public class Main {
    public static void main(String[] args) {
        // Girilen dizi
        int[] dizi = new int[] {4,3,2};
        int[] yeniDizi = new int[dizi.length];
        int ilkSayi = dizi[0];
 
        // Girilen dizideki ilk iki sayı arasındaki farkı bul
        // Eğer fark pozitif ise yeniDiziyi oluştur
        if (dizi[1] - dizi[0] > 0)
        {
            for (int i = 0; i < dizi.length; i++)
            {
                yeniDizi[i] = ilkSayi + i;
            }
        }
        // Eğer fark negatif ise yeniDiziyi oluştur
        else
        {
            for (int i = 0; i < dizi.length; i++)
            {
                yeniDizi[i] = ilkSayi - i;
            }
        }
 
        // Dizinin art arda olup olmadığını kontrol et
        if (Arrays.equals(dizi, yeniDizi))
            System.out.println("Evet, arka arkaya.");
        else
            System.out.println("Hayır, arka arkaya değil.");
    }
}
```