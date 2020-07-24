---
layout: post
title: Kelimelerin Tersini Cümledeki Yerinde Yaz
date: 2020-07-25 19:38 +0300
categories: Coding-Challenges
tags: Kelime, Cümle, Ters, Aynı Yer
excerpt: Programcıya uzun bir cümle veriliyor. Bu noktadan sonra ise, cümledeki her bir kelimenin -tam bulunduğu yerde- tam tersini yazması isteniyor...
---
### Soru
Programcıya uzun bir cümle **(girilenCumle)** veriliyor. Bu noktadan sonra ise, cümledeki her bir kelimenin -tam bulunduğu yerde- tam tersini yazması isteniyor.

### Örnek

| Girdi                | Çıktı                               |
|----------------------|-------------------------------------|
| **girilenCumle**: merhaba dünya  | **Sonuç**: abahrem aynüd.  |
| **girilenCumle**: Merhaba dünyalılar biz sizler için dostuz.  | **Sonuç**: abahrem ralılaynüd zib relzis niçi zutsod.  |

### Çözüm - C#
```csharp
using System;

class Program
{
    static void Main()
    {
        string girilenCumle = "Merhaba dünyalılar biz sizler için dostuz.";
        // girilenCumle'yi hem küçük harfli yap hem sonundaki noktayı kaldır, hem parçala
        string[] kelimeler = girilenCumle.ToLower().TrimEnd('.').Split();

        string yeniCumle = string.Empty;
        // Dizideki kelimeleri tek tek al
        foreach (string kelime in kelimeler)
        {
            // Her kelimeyi karakter dizisine ekle ve ters çevir
            char[] harfler = kelime.ToCharArray();
            Array.Reverse(harfler);

            // Ters çevirilen harfleri yeniCumle'ye ekle
            foreach (char harf in harfler)
            {
                yeniCumle += harf;
            }

            yeniCumle += " ";
        }

        // Sondaki boşluğu kaldır ve noktayı ekle
        Console.WriteLine("Sonuç: " + yeniCumle.TrimEnd() + ".");
        Console.Read();
    }
}
```