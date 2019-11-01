---
layout: post
title: İstenen Sıradaki Fibonacci Sayısını Bul
date: 2019-11-02 08:47 +0300
categories: Coding-Challenges
tags: Fibonacci, Sıra
excerpt: Programcıya, bir sıra numarası (girilenSira) veriliyor ve sıranın, hangi Fibonacci Sayısına denk geldiğini bulan program yazması isteniyor.
---
### Soru
Programcıya, bir sıra numarası **(girilenSira)** veriliyor ve sıranın, hangi Fibonacci Sayısına denk geldiğini bulan program yazması isteniyor. 

> **Fibonacci Sayı** dizisi, kendinden önceki iki ardışık sayının toplamının kendisinden sonraki sayıya eşit olmasıdır. Yani her sayı kendisinden önce gelen iki sayının toplamıdır.

* Fibo Sıra: 1, 2, 3, 4, 5, 6, 7,  8,  9
* Fibonacci: 0, 1, 1, 2, 3, 5, 8, 13, 21

### Örnek

| Girdi              | Çıktı         |
|--------------------|---------------|
| **girilenSira**: 8 | **Sonuç**: 13 |
| **girilenSira**: 4 | **Sonuç**: 2  |

### Çözüm - C#
```csharp
using System;

namespace test
{
    class Program
    {
        static void Main()
        {
            int girilenSira = 8;
            int fibonacciSayisi = 0, oncekiSayi = 0, sonrakiSayi = 1;

            // Fibonacci: 0, 1, 1, 2, 3, 5, 8, 13, 21
            // Fibo Sıra: 1, 2, 3, 4, 5, 6, 7,  8,  9
            // Sıranın tam oturması için (Fibonacci 0 ile başlıyor) girilen sıradan bir düş
            girilenSira--;

            if (girilenSira == 1)
                Console.WriteLine("Sonuç: " + 1);

            // Girilen sıra 2 veya daha büyük ise;
            for (int sira = 2; sira <= girilenSira; sira++)
            {
                // Önceki ve sonraki sayıları topla. Sonraki sayıya geçince önceki ve sonraki sayı değerlerini yenile
                fibonacciSayisi = oncekiSayi + sonrakiSayi;
                oncekiSayi = sonrakiSayi;
                sonrakiSayi = fibonacciSayisi;
            }

            Console.WriteLine("Sonuç: " + fibonacciSayisi);

            Console.Read();
        }
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        int girilenSira = 8;
        int fibonacciSayisi = 0, oncekiSayi = 0, sonrakiSayi = 1;

        // Fibonacci: 0, 1, 1, 2, 3, 5, 8, 13, 21
        // Fibo Sıra: 1, 2, 3, 4, 5, 6, 7,  8,  9
        // Sıranın tam oturması için (Fibonacci 0 ile başlıyor) girilen sıradan bir düş
        girilenSira--;

        if (girilenSira == 1)
            System.out.println("Sonuç: " + 1);

        // Girilen sıra 2 veya daha büyük ise;
        for (int sira = 2; sira <= girilenSira; sira++) 
        {
            // Önceki ve sonraki sayıları topla. Sonraki sayıya geçince önceki ve sonraki sayı değerlerini yenile
            fibonacciSayisi = oncekiSayi + sonrakiSayi;
            oncekiSayi = sonrakiSayi;
            sonrakiSayi = fibonacciSayisi;
        }

        System.out.println("Sonuç: " + fibonacciSayisi);
    }
}
```