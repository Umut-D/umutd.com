---
layout: post
title: Anagram Olanlar Neler
date: 2019-01-26 19:33 +0300
categories: Coding-Challenges
tags: Anagram, Kelime
---
### Soru
Programcıya, herhangi bir kelime **(girilenKelime)** ve kelime dizileri **(girilenKelimeler)** veriliyor. Programcıdansa, ana kelime ile girilen kelimeleri tek tek karşılaştırarak, harfleri birbiriyle bire bir aynı olan kelimeleri bulması ve bunları yazdırması isteniyor.

>**Anagram**, bir sözcüğün veya sözcük grubunun harflerinin değişik düzenle başka bir sözcüğü veya sözcük grubunu oluşturmasıdır. (Örn.: Bahriyeli/Harbiyeli – yasa/asya – imza/mazi)

### Örnek

| Girdi                                                                            | Çıktı                   |
|----------------------------------------------------------------------------------|-------------------------|
| **girilenKelime**: faal<br>**girilenKelimeler**: alfa, teta, beta, zeta          | **Sonuç**: alfa         |
| **girilenKelime**: ihlas<br>**girilenKelimeler**: salih, halis, silahtar, saliha | **Sonuç**: salih, halis |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
internal class Program
{
    private static void Main()
    {
        string girilenKelime = "abba";
        List<string> girilenKelimeler = new List<string> {"aabb", "abcd", "bbaa", "dada"};
 
        // Girilen kelimeyi karakter dizesine dönüştürüp sırala
        char[] girilenKelimeSirali = girilenKelime.ToCharArray();
        Array.Sort(girilenKelimeSirali);
 
        List<string> sonuclar = new List<string>();
 
        // Girilen kelimeleri, girilen kelime ile tek tek karşılaştır
        foreach (string kelime in girilenKelimeler)
        {
            // Girilen kelimeleri karakter dizesine dönüştürüp sırala
            char[] girilenKelimelerSirali = kelime.ToCharArray();
            Array.Sort(girilenKelimelerSirali);
 
            // Girilen değerleri string dizisine dönüştür
            var yeniKelime = new string(girilenKelimeSirali);
            var yeniKelimeler = new string(girilenKelimelerSirali);
 
            // Kelimeler arasında eşitlik varsa, eşit olan kelimeyi yeni diziye ekle
            if (yeniKelime.Equals(yeniKelimeler))
            {
                sonuclar.Add(kelime);
            }
        }
 
        foreach (var sonuc in sonuclar)
        {
            Console.WriteLine(sonuc);
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
 
public class Main {
 
    public static void main(String[] args) {
 
        String girilenKelime = "abba";
        List<String> girilenKelimeler = new ArrayList<>();
        girilenKelimeler.add("aabb");
        girilenKelimeler.add("abcd");
        girilenKelimeler.add("bbaa");
        girilenKelimeler.add("dada");
 
        // Girilen kelimeyi karakter dizesine dönüştürüp sırala
        char[] girilenKelimeSirali = girilenKelime.toCharArray();
        Arrays.sort(girilenKelimeSirali);
 
        List<String> sonuclar = new ArrayList<>();
 
        // Girilen kelimeleri, girilen kelime ile tek tek karşılaştır
        for (String kelime : girilenKelimeler)
        {
            // Girilen kelimeleri karakter dizesine dönüştürüp sırala
            char[] girilenKelimelerSirali = kelime.toCharArray();
            Arrays.sort(girilenKelimelerSirali);
 
            // Girilen değerleri string dizisine dönüştür
            String yeniKelime = new String(girilenKelimeSirali);
            String yeniKelimeler = new String(girilenKelimelerSirali);
 
            // Kelimeler arasında eşitlik varsa, eşit olan kelimeyi yeni diziye ekle
            if (yeniKelime.equals(yeniKelimeler))
            {
                sonuclar.add(kelime);
            }
        }
 
        for (String sonuc : sonuclar)
        {
            System.out.println(sonuc);
        }
    }
}
```