---
layout: post
title: Ardışık Olarak En Çok Tekrar Eden Harf ve Adedi
date: 2020-10-03 17:29 +0300
categories: Coding-Challenges
tags: Harf, Tekrar, Sayi, Adet
excerpt: Programcıya rastgele harflerden oluşan bir yazi veriliyor. Daha sonra ise, yazıdan arka arkaya en çok tekrar eden harf ve bunun sayısının belirlenmesi isteniyor. Eğer aynı sayıda tekrar yapan birden fazla harf varsa, alfabetik olarak ilk olanı sonuç olarak yazdırması bekleniyor...
---
### Soru
Programcıya rastgele harflerden oluşan bir yazi **(yazi)** veriliyor. Daha sonra, yazıdan arka arkaya en çok tekrar eden harf ve bunun sayısının belirlenmesi isteniyor. Eğer aynı sayıda tekrar yapan birden fazla harf varsa, alfabetik olarak ilk olanı sonuç olarak yazdırması bekleniyor.

### Örnek

| Girdi                             | Çıktı             |
|-----------------------------------|-------------------|
| **girilenCumle**: aazzdddd        | **Sonuç**: [d, 4] |
| **girilenCumle**: teeeeeeemttttto | **Sonuç**: [e, 7] |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    public static void Main()
    {
        string yazi = "ykkkkaada";

        // Boşluk kontrolü yap
        if (string.IsNullOrEmpty(yazi))
            Console.WriteLine(new Tuple<char?, int>(null, 0));

        // Tüm harfleri diziye aktar
        char[] harfler = yazi.ToCharArray();
        Dictionary<int, int> sonuc = new Dictionary<int, int>();

        // Her bir harfin durumuna bak
        int sayac = 1;
        for (int i = 0; i < harfler.Length; i++)
        {
            if (i + 1 == harfler.Length)
                break;

            // Harf daha önce diziye dahil edildi ise tekrar sayısını güncelle
            if (harfler[i] == harfler[i + 1])
            {
                sayac++;
                sonuc[harfler[i]] = sayac;
            }
            else
            {
                sonuc[harfler[i]] = sayac;
                sayac = 1;
            }
        }

        // Değerleri azalan sıraya göre sırala
        var sirala = from entry in sonuc orderby entry.Value descending select entry;
        // Sonucu Tuple biçimine dönüştür
        Tuple<int, int>[] degerler = sirala.Select(o => Tuple.Create(o.Key, o.Value)).ToArray();

        Console.WriteLine(new Tuple<char?, int>((char) degerler[0].Item1, degerler[0].Item2));

        Console.Read();
    }
}
```