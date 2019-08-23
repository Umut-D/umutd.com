---
layout: post
title: İki Metini Tek Metin Haline Getir
date: 2019-03-02 19:33 +0300
categories: Coding-Challenges
tags: Benzersiz Metin, Metin
---
### Soru
Programcıya iki farklı ve sadece aynı veya farklı harflerden oluşan metinler **(birinciMetin, ikinciMetin)** veriliyor. Bu noktadan sonra ise, her iki metini alfabetik olarak sıralı ve sadece aynı olmayan harflerden oluşan bir hale getirmesi isteniyor.

### Örnek

| Girdi                                             | Çıktı           |
|---------------------------------------------------|-----------------|
| **birinciMetin**: bbcaa<br>**ikinciMetin**: cdddb | **Sonuç**: abcd |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
 
class Program
{
    static void Main()
    {
        string birinciMetin = "xyaabbbccccdefww";
        string ikinciMetin = "xxxxyyyyabklmopq";
 
        // Her iki metini birleştir, karakter dizisine çevir ve aynı olan harfleri ele
        IEnumerable<char> metin = string.Concat(birinciMetin, ikinciMetin).ToCharArray().Distinct();
 
        // Diziyi, char karakter dizisine dönüştür ve sırala
        char[] harfler = metin.ToArray();
        Array.Sort(harfler);
 
        string sonuc = "";
 
        // Her bir karakteri string'e aktar
        foreach (char harf in harfler)
        {
            sonuc += harf.ToString();
        }
 
        Console.WriteLine(sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
import java.util.HashSet;
 
public class Main {
 
    public static void main(String[] args)
    {
        String birinciMetin = "xyaabbbccccdefww";
        String ikinciMetin = "xxxxyyyyabklmopq";
 
        // Her iki metini birleştir
        String metin = birinciMetin.concat(ikinciMetin);
 
        // Diziyi, char karakter dizisine dönüştür ve sırala
        char[] sirali = metin.toCharArray();
        Arrays.sort(sirali);
 
        HashSet<Character> hashDizisi = new HashSet<>();
        StringBuilder sonuc = new StringBuilder();
 
        // Karakterleri yalnız benzersiz harflerin eklendiği diziye aktar
        for (char c : sirali)
        {
            hashDizisi.add(c);
        }
 
        for (char c : hashDizisi)
        {
            sonuc.append(c);
        }
 
        System.out.println(sonuc.toString());
    }
}
```