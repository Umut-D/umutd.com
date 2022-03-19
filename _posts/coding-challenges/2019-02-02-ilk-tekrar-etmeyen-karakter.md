---
layout: post
title: İlk Tekrar Etmeyen Karakter
date: 2019-02-02 19:33 +0300
categories: Coding-Challenges
tags: Harf, Kelime, Karakter, Tekrar
redirect_from:
  - /coding-challenges/ilk-tekrar-etmeyen-karakter/
  - /etiket/harf/
---
### Soru
Programcıya, herhangi bir kelime **(girilenYazi)** veriliyor. Programcıdansa, yazı içinde hiçbir yerde tekrar etmeyen ilk harfi bulan bir kod yazması isteniyor.

**Not**: Büyük ve küçük harflerin de aynı olarak kabul edilmekte ve sonuç ekranında bire bir (karakter büyük ise büyük, küçük ise küçük) yazılması gerekmekte.

### Örnek

| Girdi                      | Çıktı                                                           |
|----------------------------|-----------------------------------------------------------------|
| **girilenKelime**: taassup | **Sonuç**:  t (Bir kere var ve en başta)                        |
| **girilenKelime**: sTreSS  | **Sonuç**:  T                                                   |
| **girilenKelime**: Genelge  | **Sonuç**:  n                                                  |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
class Program
{
    static void Main()
    {
        string girilenYazi = "sTreSS";
        string yazininIlkHali = girilenYazi;
 
        // Tüm harfleri önce küçük harflere, sonra tek tek karaktere dönüştür
        girilenYazi = girilenYazi.ToLower();
        char[] harfler = girilenYazi.ToCharArray();
 
        List<char> harf = new List<char>();
 
        // Harfleri karakter olarak alıp, ayrı ayrı koleksiyona ekle
        foreach (char karakter in harfler)
        {
            // Eğer harf daha önce eklenmemişse ekle
            if (!harf.Contains(karakter))
            {
                harf.Add(karakter);
            }
            // Daha önce eklenen varsa diziden kaldır (Ekleme yapma)
            else
            {
                harf.Remove(karakter);
            }
        }
 
        if (harf.Count > 0)
        {
            // Dizide ilk tekrar etmeyen karakteri al
            int yer = girilenYazi.IndexOf(harf[0]);
            Console.WriteLine(yazininIlkHali[yer].ToString());
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;

public class Main
{
    public static void main(String[] args)
    {
        String girilenYazi = "Genelge";
        String yazininIlkHali = girilenYazi;

        // Tüm harfleri önce küçük harflere, sonra tek tek karaktere dönüştür
        girilenYazi = girilenYazi.toLowerCase();
        char[] harfler = girilenYazi.toCharArray();

        ArrayList<Character> harf = new ArrayList<>();

        // Harfleri karakter olarak alıp, ayrı ayrı koleksiyona ekle
        for (char karakter : harfler)
        {
            // Eğer harf daha önce eklenmemişse ekle
            if (!harf.contains(karakter))
            {
                harf.add(karakter);
            }
            // Daha önce eklenen varsa diziden kaldır (Ekleme yapma)
            else
            {
                harf.remove(Character.valueOf(karakter));
            }
        }

        if (harf.size() > 0)
        {
            // Dizide ilk tekrar etmeyen karakteri al
            Character yer = harf.get(0);
            System.out.println(yer);
        }
    }
}
```