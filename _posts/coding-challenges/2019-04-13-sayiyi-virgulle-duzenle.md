---
layout: post
title: Sayıyı Virgülle Düzenle
date: 2019-04-13 17:11 +0300
categories: Coding-Challenges
tags: Düzenleme, Format, Sayı
redirect_from:
  - /coding-challenges/sayiyi-virgulle-duzenle/
---
### Soru
Programcıya herhangi bir sayı **(girilenSayi)** veriliyor. Programcıdansa, verilen sayının binlik ayracının virgüllü biçimde düzenlenmesi isteniyor.

### Örnek

| Girdi                     | Çıktı                 |
|---------------------------|-----------------------|
| **girilenSayi**: 100000   | **Sonuç**: 100,000    |
| **girilenSayi**: 32432423 | **Sonuç**: 32,432,423 |

### Çözüm - C#
```csharp
using System;
using System.Globalization;
 
internal class Program
{
    private static void Main()
    {
        int girilenSayi = 100000;
 
        // İngilizce ABD kültür düzeninde değişim yapılıp virgüle geçilecek
        CultureInfo kulturDuzeni = new CultureInfo("En-US");
 
        // Girilen sayıyı önce decimal'e (ondalıklı sayı), sonra virgüllü düzene dönüştür
        string sonuc = Convert.ToDecimal(girilenSayi).ToString("#,##", kulturDuzeni);
 
        Console.WriteLine("Sonuç: {0}", sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.text.DecimalFormat;
import java.util.Locale;
 
public class Main {
 
    public static void main(String[] args) {
 
        int girilenSayi = 100000;
 
        // İngilizce ABD kültür düzeninde değişim yapılıp virgüle geçilecek
        DecimalFormat kulturDuzeni = (DecimalFormat) DecimalFormat.getNumberInstance(Locale.ENGLISH);
 
        // Girilen sayıyı istenen biçimde formatlayıp yazdır
        System.out.println("Sonuç " + kulturDuzeni.format(girilenSayi));
    }
}
```
