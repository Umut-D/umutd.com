---
layout: post
title: Karmaşık Harfler Kelime İçinde Var Mı?
date: 2018-05-19 19:33 +0300
categories: Coding-Challenges
tags: Karmaşık Harfler, Harf
redirect_from:
  - /coding-challenges/karmasik-harfler-kelime-icinde-var-mi/
  - /etiket/karmasik-harfler/
---
### Soru
Programcıya, içerisinde çok çeşitli harfler **(mevcutDeger)** olan anlamsız bir cümle ve anlamlı bir kelime **(mevcutDeger)** veriliyor. Programcıdan ise eldeki değerleri karşılaştırarak mevcut değerdeki harflerin bire bire girilen değerde olup olmadığını bulması isteniyor. Bu durumda eğer girilen kelimedeki harflerin tümü, mevcut değerlerle eşleşiyorsa sonuç ekranına “Olumlu”, değilse “Olumsuz” yazdırması bekleniyor.

### Örnek

| Girdi                                                           | Çıktı              |
|-----------------------------------------------------------------|--------------------|
| **mevcutDeger**: ysduaraudmazvnut <br> **girilenDeger**: umut   | **Sonuç**: Olumlu  |
| **mevcutDeger**: thunesrtoradanpza <br> **girilenDeger**: manik | **Sonuç**: Olumsuz |

### Çözüm - C#
```csharp
using System;
using System.Linq;
using System.Text;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string mevcutDeger = "ysduaraudmazvnut";
        string girilenDeger = "umut";
 
        // Girilen değeri alıp mevcut değer değişkenini de tek tek parçalara ayır
        StringBuilder aranan = new StringBuilder(girilenDeger);
        char[] arananDizi = mevcutDeger.ToCharArray();
 
        int harfSayaci = 0;
 
        // Eğer girilen değer adedi mevcut değer ile eşleşiyorsa sayacı arttır
        for (int i = 0; i < aranan.Length; i++)
        {
            if (arananDizi.Contains(aranan[i]))
            {
                harfSayaci++;
            }
        }
 
        // Girilen değerin uzunluğu harf sayısı eşit ise doğru döndür
        if (harfSayaci == aranan.Length)
        {
            Console.WriteLine("Girilen değer, o dandik değerin içinde var sahiden! Olumlu.");
        }
        else
        {
            Console.WriteLine("Karakterler tutmadı. Olumsuz.");
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
package com.zeta;
 
public class Main {
    public static void main(String[] args) {
        String mevcutDeger = "ysduaraudmazvnut";
        String girilenDeger = "umut";
 
        // Girilen değeri alıp mevcut değer değişkenini de tek tek parçalara ayır
        StringBuilder aranan = new StringBuilder(girilenDeger);
        char[] arananDizi = mevcutDeger.toCharArray();
 
        int harfSayaci = 0;
 
        // Eğer girilen değer adedi mevcut değer ile eşleşiyorsa sayacı arttır
        for (int i = 0; i < aranan.length(); i++)
        {
            if (arananDizi.equals(aranan.charAt(i)))
            {
                harfSayaci++;
            }
        }
 
        // Girilen değerin uzunluğu harf sayısı eşit ise doğru döndür
        if (harfSayaci == aranan.length())
        {
            System.out.println("Girilen değer, o dandik değerin içinde var sahiden! Olumlu.");
        } else {
            System.out.println("Karakterler tutmadı. Olumsuz.");
        }
    }
}
```