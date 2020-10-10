---
layout: post
title: Hangi Yüzyıl
date: 2020-10-10 13:39 +0300
categories: Coding-Challenges
tags: Yüzyıl, Asır
excerpt:  Programcıya bir yıl veriliyor ve ondan bu yılın kaçıncı yüzyıla ait olduğunu (İngilizce'ye uygun olarak) bulan bir metot oluşturması isteniyor...
---
### Soru
Programcıya bir yıl **(girilenYil)** veriliyor ve ondan bu yılın kaçıncı yüzyıla ait olduğunu (İngilizce'ye uygun olarak) bulan bir metot oluşturması isteniyor.

### Örnek

| Girdi                | Çıktı                   |
|----------------------|-------------------------|
| **girilenYil**: 1999 | **Mevcut Yüzyıl**: 20th |
| **girilenYil**: 2000 | **Mevcut Yüzyıl**: 20th |
| **girilenYil**: 2011 | **Mevcut Yüzyıl**: 21st |
| **girilenYil**: 2154 | **Mevcut Yüzyıl**: 22nd |
| **girilenYil**: 2259 | **Mevcut Yüzyıl**: 23rd |
| **girilenYil**: 1124 | **Mevcut Yüzyıl**: 12th |

### Çözüm - C#
```csharp
using System;

class Program
{
    public static void Main()
    {
        string girilenYil = "2004";
        string sonuc = Yuzyil(girilenYil);

        Console.WriteLine($"Mevcut Yüzyıl: {sonuc}");

        Console.Read();
    }

    public static string Yuzyil(string girilenYil)
    {
        double yil = double.Parse(girilenYil);
        // Mevcut yılı 100'e bölerek ondalık halini elde et (Örn. 2004/100=20.04)
        double ondalik = yil / 100;
        // ondalıklı değeri, kendisinin üstündeki sayıya yuvarlayarak döndür
        double sayi = Math.Ceiling(ondalik);

        // Eğer sayı aralıkları 11 ve 13 arasında ise th eki ekle
        if (sayi >= 11 && sayi <= 13)
            return sayi + "th";

        // sayı 10'a bölündüğünde kalan sayısına göre ekleri ekle
        switch (sayi % 10)
        {
            case 1:
                return sayi + "st";
            case 2:
                return sayi + "nd";
            case 3:
                return sayi + "rd";
        }

        // Diğer seçeneklerde th eki ekle
        return sayi + "th";
    }
}
```