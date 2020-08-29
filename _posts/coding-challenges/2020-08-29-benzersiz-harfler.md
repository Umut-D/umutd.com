---
layout: post
title: Benzersiz Harfler
date: 2020-08-29 14:03 +0300
categories: Coding-Challenges
tags: Harf, Kelime, Benzersiz
excerpt: Programcıya aynı harflerden oluşan bir kelime veriliyor. Bu noktadan sonraysa, kelimedeki benzer harfleri ayıklayarak, sadece benzersiz harfleri bulan bir kod oluşturması isteniyor....
---
### Soru
Programcıya aynı harflerden oluşan bir kelime **(kelime)** veriliyor. Bu noktadan sonra ise; kelimedeki benzer harfleri ayıklayarak, sadece benzersiz harfleri bulan bir kod oluşturması isteniyor.

### Örnek

| Girdi                    | Çıktı             |
|--------------------------|-------------------|
| **kelime**: aabbccddeeff | **Sonuç**: abcdef |
| **kelime**: mehmet       | **Sonuç**: meht   |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    public static void Main()
    {
        string kelime = "aabbcceeeeeeeeedd";

        // 1. Yol; Linq ile
        // Kelimeyi karakter dizisine dönüştür
        List<char> harfler = new List<char>(kelime.ToCharArray());
        // Linq ile benzersiz harfleri alıp diziye aktar
        IEnumerable<char> tekrarsizHarfler = kelime.Intersect(harfler);

        // Karakter dizisindeki harfleri birleştir
        string sonuc = string.Join("", tekrarsizHarfler.ToArray());
        Console.WriteLine("Sonuç: {0}", sonuc);

        // 2. Yol
        string ikinciYolVeri = "", ikinciYolSonuc = "";
        foreach (char harf in kelime)
        {
            // Döngü devam ederken gelen harfler, string içinde yoksa ekleme yap
            if (!ikinciYolVeri.Contains(harf))
            {
                ikinciYolVeri += harf;
                ikinciYolSonuc += harf;
            }
        }

        Console.WriteLine("2. Yolun Sonucu: {0}", ikinciYolSonuc);

        // 3. Yol, yine Linq ile
        string ucuncuYolVeri = "", ucuncuYolSonuc = "";
        // Linq sorgusuna göre gelen harfler, string içinde yoksa ekleme yap
        foreach (char harf in kelime.Where(harf => !ucuncuYolVeri.Contains(harf)))
        {
            ucuncuYolVeri += harf;
            ucuncuYolSonuc += harf;
        }

        Console.WriteLine("3. Yolun Sonucu: {0}", ucuncuYolSonuc);


        Console.Read();
    }
}
```

### Çözüm - Java
```java
class Main {
  public static void main(String[] args) 
  {
    String kelime = "aabbcceeeeeeeeedd";

    String ikinciYolVeri = "", ikinciYolSonuc = "";
    for (int i = 0; i < kelime.length(); i++) 
    {
      char harf = kelime.charAt(i);
      // Her bir harf, kelime içinde yoksa ekleme yap
      if (ikinciYolVeri.indexOf(harf) < 0) {
        ikinciYolVeri += harf;
        ikinciYolSonuc += harf;
      }
    }

    System.out.println("Sonuç: " + ikinciYolSonuc);
  }
}
```
