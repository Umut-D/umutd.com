---
layout: post
title: Gülen Yüzleri Say
date: 2019-03-09 19:33 +0300
categories: Coding-Challenges
tags: Gülen Yüz, Sayım, Emoloji
---
### Soru
Programcıya içinde gülücük olan/olmayan yüz ifadeleri dizisi (yuzler) veriliyor. Önce gözler, sonra burun ve son olarak ağız kısmından oluşacak yüz ifadesi kurallar ise;

-Her yüz : veya ; olarak ifade edilen gözlere sahip olmalı,
-Her burun - veya ~ veya    olarak ifade edilen buruna sahip olmalı (yüz ifadesinde burun olmayadabilir),
-Her ağız ifadesi ) veya D olarak ifade edilen ağıza sahip olmalı.

Programcıdan ise yukarıdaki kurallara uygun olan kaç adet yüz ifadesinin bulması isteniyor.

### Örnek

| Girdi                                  | Çıktı        |
|----------------------------------------|--------------|
| **yuzler**: {":)", ";(", ";}", ":-D"}  | **Sonuç**: 2 |
| **yuzler**: {":D", ":~)", ";~D", ":)"} | **Sonuç**: 4 |

### Çözüm - C#
```csharp
using System;
 
class Program
{
    static void Main()
    {
        string[] yuzler = new string[] {":D", ":~)", ";~D", ":)"};
        int sayac = 0;
 
        // Her bir yüzü tek tek incele
        foreach (string yuz in yuzler)
        {
            // Her bir dizi bileşeninin uzunluğuna göre değerlendirme yap
            switch (yuz.Length)
            {
                // İncelenen değerin uzunluğu 3 ise
                case 3:
                    // Her 3 karakteri sırası ile incele
                    if (yuz.Substring(0, 1) == ":" || yuz.Substring(0, 1) == ";")
                    {
                        if (yuz.Substring(1, 1) == "-" || yuz.Substring(1, 1) == "~" || yuz.Substring(1, 1) == "")
                        {
                            if (yuz.Substring(2, 1) == ")" || yuz.Substring(2, 1) == "D")
                                sayac++;
                        }
                    }
                    
                    break;
                // İncelenen değerin uzunluğu 2 ise
                case 2:
                    // Her 3 karakteri sırası ile incele
                    if (yuz.Substring(0, 1) == ":" || yuz.Substring(0, 1) == ";")
                    {
                        if (yuz.Substring(1, 1) == ")" || yuz.Substring(1, 1) == "D")
                            sayac++;
                    }
 
                    break;
            }
        }
 
        Console.WriteLine(sayac);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args)
    {
        String[] yuzler = new String[] {":D", ":~)", ";~D", ":)"};
        int sayac = 0;
 
        // Her bir yüzü tek tek incele
        for (String yuz: yuzler)
        {
            // Her bir dizi bileşeninin uzunluğuna göre değerlendirme yap
            switch (yuz.length())
            {
                // İncelenen değerin uzunluğu 3 ise
                case 3:
                    // Her 3 karakteri sırası ile incele
                    if (yuz.substring(0, 1).equals(":") || yuz.substring(0, 1).equals(";"))
                    {
                        if (yuz.substring(1, 1).equals("-") || yuz.substring(1, 1).equals("~") || yuz.substring(1, 1).equals(""))
                        {
                            if (yuz.substring(2).equals(")") || yuz.substring(2).equals("D"))
                                sayac++;
                        }
                    }
 
                    break;
                // İncelenen değerin uzunluğu 2 ise
                case 2:
                    // Her 3 karakteri sırası ile incele
                    if (yuz.substring(0, 1).equals(":") || yuz.substring(0, 1).equals(";"))
                    {
                        if (yuz.substring(1).equals(")") || yuz.substring(1).equals("D"))
                            sayac++;
                    }
 
                    break;
            }
        }
 
        System.out.println(sayac);
    }
}
```