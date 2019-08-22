---
layout: post
title: Cümle İçindeki Sayıların Toplamı
date: 2018-05-12 19:33 +0300
categories: Coding-Challenges
tags: Desen, Düzenli İfadeler, Pattern, Regular Expressions
---
### Soru
Programcıya, içerisinde sayılar **(girilenIfade)** olan bir cümle veriliyor ve programcıdan mevcut cümle içerisindeki sayıların toplamını alması isteniyor.

### Örnek

| Girdi                                          | Çıktı         |
|------------------------------------------------|---------------|
| **girilenIfade**: bu10deneme20midir30          | **Sonuç**: 60 |
| **girilenIfade**: Yıldız2Savaşları3İyi4Filmdi5 | **Sonuç**: 14 |

### Çözüm - C#
```csharp
using System;
using System.Text.RegularExpressions;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenIfade = "bu10deneme20midir30";
 
        // Regular Expressions (Düzenli İfadeler) sınıfı ile her bir sayıyı ayırıp diziye at
        string[] sayilar = Regex.Split(girilenIfade, @"\D+");
        int toplam = 0;
 
        // Dizideki her bir değeri tek tek okut
        foreach (string deger in sayilar)
        {
            // Dizideki değer boş olmadığı sürece sayıları alarak topla
            if (!string.IsNullOrEmpty(deger))
            {
                toplam += int.Parse(deger);
            }
        }
 
        Console.WriteLine("Cümledeki Sayıların Toplamı: " + toplam);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;
 
public class Main {
    public static void main(String[] args) {
        String girilenIfade = "bu10deneme20midir30";
 
        // Pattern ve Matcher (Düzenli İfadeler) ile her bir sayıyı ayırıp diziye at
        Pattern desen = Pattern.compile("[0-9]+");
        Matcher eslesme = desen.matcher(girilenIfade);
 
        int toplam = 0;
 
        // Desendeki eşleşme grubundaki değerlerini tek tek al ve topla
        while (eslesme.find()) 
        {
            Integer sayilar = Integer.parseInt(eslesme.group());
            toplam += sayilar;
        }
 
        System.out.println("Cümledeki Sayıların Toplamı: " + toplam);
    }
}
```