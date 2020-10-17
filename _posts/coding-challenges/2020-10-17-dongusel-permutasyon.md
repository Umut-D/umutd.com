---
layout: post
title: Döngusel Permütasyon
date: 2020-10-17 19:28 +0300
categories: Coding-Challenges
tags: Permütasyon, Matematik, Döngü
excerpt: Programcıya bir hedef sayı veriliyor. Ardından, girilen sayıya kadar döngüsel olarak devam ederek, her bir satırda sayı artışıyla başlayan bir yapı oluşturması isteniyor...
---
### Soru
Programcıya bir hedef sayı **(girilenSayi)** veriliyor. Ardından, girilen sayıya kadar döngüsel olarak devam ederek, her bir satırda sayı artışıyla başlayan bir yapı oluşturması isteniyor.

### Örnek

| Girdi              | Çıktı                                                        |
|--------------------|--------------------------------------------------------------|
| **girilenSayi**: 3 | **Sonuç**: 123 <br> 231 <br> 312                             |
| **girilenSayi**: 5 | **Sonuç**: 12345 <br> 23451 <br> 34512 <br> 45123 <br> 51234 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

class Program
{
    public static void Main()
    {
        int girilenSayi = 5;

        // Girilen sayı 0 ise boş yazdır
        if (girilenSayi.ToString().Length == 0)
            Console.WriteLine("Boş");

        // Girilen sayıya kadar olan sayıları diziye ekle
        List<int> sayilar = new List<int>();
        for (int i = 1; i <= girilenSayi; i++)
            sayilar.Add(i);

        string sonuc = "";
        for (int i = 0; i < girilenSayi; i++)
        {
            // Dizideki her bir sayıyı sonuca ekle
            foreach (int sayi in sayilar)
                sonuc += sayi.ToString();

            // Gerekli eklemeyi diziye ekleyerek, 0. indisteki değeri kaldır
            sayilar.Add(sayilar[0]);
            sayilar.RemoveAt(0);
            // Her bir satır sonunda boşluk ekle
            sonuc += "\n";
        }

        // En sondaki değeri kaldır
        sonuc = sonuc.Remove(sonuc.Length - 1, 1);
        Console.WriteLine(sonuc);

        Console.Read();
    }
}
```