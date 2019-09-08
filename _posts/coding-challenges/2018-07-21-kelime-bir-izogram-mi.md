---
layout: post
title: Kelime Bir İzogram Mı?
date: 2018-07-21 19:33 +0300
categories: Coding-Challenges
tags: Isogram, İzogram
redirect_from:
  - /coding-challenges/kelime-bir-izogram-mi/
  - /etiket/izogram/
---
### Soru
Programcıya, herhangi bir kelime **(girilenSayi)** veriliyor. Programcıdansa, ilgili kelimenin bir izogram* olup olmadığını bulan ve eğer sonuç doğru ise “Evet, bu bir izogramdır.”, yanlış ise “İzogram değil” yazan bir program oluşturması isteniyor.

> **İzogram**, bir kelimenin içerisinde hiçbir şekilde tekrar etmeyen harflerin bulunması durumudur. Özetle, kelimedeki her harf bir kere kullanılır.

### Örnek

| Girdi                      | Çıktı                            |
|----------------------------|----------------------------------|
| **girilenMetin**: Ada      | **Sonuç**: İzogram değil         |
| **girilenMetin**: Objektif | **Sonuç**: Evet, bu bir izogram. |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenKelime = "flarmoni";
 
        // Girilen kelimeyi (sorun olmaması için) küçük harfe çevir
        girilenKelime = girilenKelime.ToLower();
 
        // Kelimenin tam uzunluğunu al
        int kelimeUzunluk = girilenKelime.Length;
 
        // Kelime içindeki harfleri tek tek ayırıp, tekrar eden kelimeleri kısa kelimeye ekle (Yaşa Linq!)
        string kisaKelime = new string(girilenKelime.Distinct().ToArray());
        int kisaKelimeUzunluk = kisaKelime.Length;
 
        // Kısa kelimenin uzunluk sayısı ile kelime uzunluğu aynı değilse izogram değil
        if (kelimeUzunluk != kisaKelimeUzunluk)
        {
            Console.WriteLine("İzogram değil.");
        }
        else
        {
            // Kısa kelimenin uzunluk sayısıyla kelime uzunluğu aynı ise izogramdır
            Console.WriteLine("Evet, bu bir izogram. ");
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.HashSet;
import java.util.Set;
 
public class Main {
    public static void main(String[] args) {
 
        String girilenKelime = "flarmoni";
 
        // Girilen kelimeyi (sorun olmaması için) küçük harfe çevir
        girilenKelime = girilenKelime.toLowerCase();
 
        // Kelimenin tam uzunluğunu al
        int kelimeUzunluk = girilenKelime.length();
 
        // Kelime içindeki harfleri tek tek ayırıp, tekrar eden kelimeleri kısa kelimeye ekle
        Set<Character> BenzersizHarfler = new HashSet<>();
        for (int i = 0; i < girilenKelime.length(); ++i)
        {
            BenzersizHarfler.add(girilenKelime.charAt(i));
        }
 
        // Kısa kelimenin uzunluk sayısı ile kelime uzunluğu aynı değilse izogram değil
        if (kelimeUzunluk != BenzersizHarfler.size())
        {
            System.out.println("İzogram değil.");
        } 
        else 
        {
            // Kısa kelimenin uzunluk sayısıyla kelime uzunluğu aynı ise izogramdır
            System.out.println("Evet, bu bir izogram. ");
        }
    }
}
```