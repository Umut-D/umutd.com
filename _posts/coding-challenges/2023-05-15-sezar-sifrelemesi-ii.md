---
layout: post
title: Sezar Şifrelemesi II
date: 2023-05-15 03:02 +0300
categories: Coding-Challenges
tags: Sezar, Sezar Şifrelemesi, Şifreleme, Kriptografi
excerpt: Programcıdan; Türkçe karakter kullanılmadan girilen metindeki harfleri, kullanici tarafindan istenen ilerleme değerine göre harflerin yerlerini değiştirip şifreleme yapması isteniyor...
---

### Soru

> **Sezar şifrelemesi**, bir yazıdaki harflerin yerlerinin değiştirilmesi sonucunda elde edilir. Bu şifrede, her harf o harften bir (ya da birkaç) sonraki harf kullanılarak yazılır.

Programcıdan; Türkçe karakter kullanılmadan girilen metindeki (yazi) harfleri, kullanici tarafindan istenen ilerleme değerine (ilerlemeDegeri) göre harflerin yerlerini değiştirip şifreleme yapması isteniyor.

### Örnek

| Girdi                                              | Çıktı                      |
| -------------------------------------------------- | -------------------------- |
| **girilenMetin**: abc <br> **ilerlemeDegeri**: 1   | **sifrelenmisMetin**: bcd  |
| **girilenMetin**: xyza <br> **ilerlemeDegeri**: 29 | **sifrelenmisMetin**: abcd |

### Çözüm - C#

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace CodingChallenges
{
    public class Program
    {
        static void Main()
        {
            string yazi = "xyza";
            int ilerlemeDegeri = 3;

            // Alfabeyi programlamatik olarak oluştur
            List<char> alfabe = new List<char>();
            for (int i = 97; i < 123; i++)
                alfabe.Add((char)i);

            StringBuilder donusturulenYazi = new StringBuilder();
            // Her bir harfi tek tek alarak ilerleme değeriyle hangi indekse denk geldiğini bul
            foreach (char harf in yazi)
            {
                int harfIndeks = alfabe.IndexOf(harf);
                var kalan = (harfIndeks + ilerlemeDegeri) % 26;
                donusturulenYazi.Append(alfabe[kalan]);
            }

            Console.WriteLine(donusturulenYazi);

            Console.Read();
        }
    }
}
```

### Çözüm - Python

```python
import string

yazi = "xyza"
ilerlemeDegeri = 3

# Alfabeyi programlamatik olarak oluştur
harf_araligi = list(string.ascii_lowercase)

# Her bir harfi tek tek alarak ilerleme değeriyle hangi indekse denk geldiğini bul
donusturulenYazi = ""
for harf in yazi:
    harf_indeks = harf_araligi.index(harf)
    kalan = (harf_indeks + ilerlemeDegeri) % 26
    donusturulenYazi += harf_araligi[kalan]

print(donusturulenYazi)
```
