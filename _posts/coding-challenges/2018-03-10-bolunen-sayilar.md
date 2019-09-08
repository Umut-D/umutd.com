---
layout: post
title: Bölünen Sayılar
date: 2018-03-10 19:33 +0300
categories: Coding-Challenges
tags: Bölen Sayı, Bölüm, Bölünebilme
redirect_from:
  - /coding-challenges/bolunen-sayilar/
  - /etiket/bolen-sayi/
---
### Soru
Programcıya, herhangi bir sayi **(girilenSayi)** veriliyor. Sonrasında, verilen değeri hangi pozitif sayı ya da sayıların bölebildiğini **(sonuc)** ve toplamda kaç adet sayının bölüm yapabildiğini bulması isteniyor.

### Örnek

| Girdi                | Çıktı                                               |
|----------------------|-----------------------------------------------------|
| **girilenDeger**: 24 | **Sonuç**: 1 2 3 4 6 8 12 24<br>Bölen sayı adedi: 8 |
| **girilenDeger**: 67 | **Sonuç**: 1 67<br>Bölen sayı adedi: 2              |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
internal class Program
{
    private static void Main(string[] args)
    {
        int girilenSayi = 162;
        List<int> bolenSayilar = new List<int>();
 
        // Girilen sayıya kadar olan bir döngü oluştur
        for (int i = 1; i <= girilenSayi; i++)
        {
            // Döngüdeki sayı girilen sayıyı bölüyorsa diziye ekle
            if ((girilenSayi % i) == 0)
            {
                bolenSayilar.Add(i);
            }
        }
 
        // Dizideki değerleri tek tek yazdır
        foreach (int degerler in bolenSayilar)
        {
            Console.Write(degerler + " ");
        }
 
        // Boş bir satır ekle
        Console.Write(Environment.NewLine);
 
        // Kaç adet sayının böldüğünü bildir
        Console.WriteLine("Bölen sayı adedi: " + bolenSayilar.Count);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
 
public class Main {
    public static void main(String[] args) {
 
        int girilenSayi = 162;
        ArrayList<Integer> bolenSayilar = new ArrayList<>();
 
        // Girilen sayıya kadar olan bir döngü oluştur
        for (int i = 1; i <= girilenSayi; i++) {
            // Döngüdeki sayı girilen sayıyı bölüyorsa diziye ekle
            if ((girilenSayi % i) == 0) {
                bolenSayilar.add(i);
            }
        }
 
        // Dizideki değerleri tek tek yazdır
        for (int degerler : bolenSayilar) {
            System.out.print((degerler + " "));
        }
 
        // Boş bir satır ekle
        System.out.print(System.lineSeparator());
 
        // Kaç adet sayının böldüğünü bildir
        System.out.print("Bölen sayı adedi: " + bolenSayilar.size());
    }
}
```