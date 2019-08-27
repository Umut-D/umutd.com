---
layout: post
title: Sayıları Basamaklı Halde Yaz
date: 2019-03-16 19:33 +0300
categories: Coding-Challenges
tags: Basamaklı Sayılar, Sayı
excerpt: Programcıya herhangi bir sayı (girilenSayi) veriliyor ve mevcut sayıyı basamak ve çarpanlarına göre ayırıp yazan bir yapı oluşturması isteniyor.
---
### Soru
Programcıya herhangi bir sayı **(girilenSayi)** veriliyor ve mevcut sayıyı basamak ve çarpanlarına göre ayırıp yazan bir yapı oluşturması isteniyor.

**Not**: 0 sayısına sahip basamakların sonuçta görünmemelidir.

### Örnek

| Girdi                 | Çıktı                     |
|-----------------------|---------------------------|
| **girilenSayi**: 123  | **Sonuç**: 100 + 20 + 3   |
| **girilenSayi**: 4901 | **Sonuç**: 4000 + 900 + 1 |

### Çözüm - C#
```csharp
using System;
using System.Text;
 
class Program
{
    static void Main()
    {
        long girilenSayi = 223;
        
        // Girilen Sayıyı tekil karakterlere dönüştek
        char[] sayi = girilenSayi.ToString().ToCharArray();
        int sayac = 0;
 
        StringBuilder sonuc = new StringBuilder();
 
        // Tersten for döngüsünü işlet
        for (int i = girilenSayi.ToString().Length - 1; i >= 0; i--)
        {
            // Her bir basamağın 10'lu katını alarak, ilgili basamaktaki sayıyla çarp
            double hesaplama = Math.Pow(10, i) * char.GetNumericValue(sayi[sayac]);
 
            // Hesaplama sonucu sıfır olmadığı sürece, sonuçları diziye ekle
            if (hesaplama != 0)
            {
                sonuc.Append(hesaplama);
                sonuc.Append(" + ");
            }
 
            sayac++;
        }
 
        // Uzatmadaki fazlalıktan kurtul
        Console.WriteLine(sonuc.ToString().Remove(sonuc.Length - 3));
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args)
    {
        long girilenSayi = 223;
 
        // Girilen Sayıyı tekil karakterlere dönüştek
        char[] sayi = Integer.toString((int) girilenSayi).toCharArray();
        int sayac = 0;
 
        StringBuilder sonuc = new StringBuilder();
 
        // Tersten for döngüsünü işlet
        for (int i = sayi.length - 1; i >= 0; i--)
        {
            // Her bir basamağın 10'lu katını alarak, ilgili basamaktaki sayıyla çarp
            double hesaplama = Math.pow(10, i) * Character.getNumericValue(sayi[sayac]);
 
            // Hesaplama sonucu sıfır olmadığı sürece, sonuçları diziye ekle
            if (hesaplama != 0)
            {
                sonuc.append((int) hesaplama);
                sonuc.append(" + ");
            }
 
            sayac++;
        }
 
        // Uzatmadaki fazlalıktan kurtul
        System.out.println(sonuc.substring(0,sonuc.length() - 3));
    }
}
```