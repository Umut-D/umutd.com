---
layout: post
title: Harfler, Sayılar ve Hesaplama İşlemi
date: 2020-08-01 13:01 +0300
categories: Coding-Challenges
tags: Harfler, Sayılar, Hesaplama, İşlem
excerpt: Programcıya karışık halde ve harfler, sayılar, hesaplama operatöründen oluşan bir girdi veriliyor. Bu noktadan sonra, girdideki operatör öncesi ve operatör sonrası sayıları ayrı ve tek parça olarak alması isteniyor.Sonuç işlemini gerçekleştirmek içinse eldeki iki ayrı sayıyı mevcut operatöre göre hesaplaması isteniyor...
---
### Soru
Programcıya karışık halde ve harfler, sayılar, hesaplama operatöründen oluşan bir girdi **(girdi)** veriliyor. Bu noktadan sonra, girdideki operatör öncesi ve operatör sonrası sayıları ayrı ve tek parça olarak alması isteniyor. Sonuç işlemini gerçekleştirmek içinse eldeki iki ayrı sayıyı mevcut operatöre göre hesaplaması isteniyor.

**Not:** İşlem sonucunda küsüratlı sayı olursa -kültürden bağımsız olarak- yuvarlama yapılmasını gerekli olduğu belirtiliyor.

### Örnek

| Girdi                | Çıktı                               |
|----------------------|-------------------------------------|
| **girdi**: gdf1dg1gf*4aP0 <br> **11x40**  | **Sonuç**: 440 |
| **girdi**: a9b9cas9/sai11vjck1 <br> **999/111** | **Sonuç**: 9 |

### Çözüm - C#
```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

class Program
{
    static void Main()
    {
        string girdi = "gdf1dg1gf*4aP0";

        // Operatör öncesi ve sonrasını iki parçaya ayır
        char[] operatorler = {'+', '-', '*', '/'};
        string[] parcalar = girdi.Split(operatorler);

        // I. Regex'le birinci kısımdaki sayıları al
        MatchCollection birinciKisim = Regex.Matches(parcalar[0], @"[0-9\.]+");

        string ilkSayi = "";
        foreach (Match match in birinciKisim)
        {
            ilkSayi += match.Value;
        }

        // II. Regex'le ikinci kısımdaki sayıları al
        MatchCollection ikinciKisim = Regex.Matches(parcalar[1], @"[0-9\.]+");

        string digerSayi = "";
        foreach (Match match in ikinciKisim)
        {
            digerSayi += match.Value;
        }

        // Değer dönüşümlerini yap
        double birinciDeger = Convert.ToDouble(ilkSayi);
        double ikinciDeger = Convert.ToDouble(digerSayi);

        // Girdi'den hesaplama operatörünü al
        int operatorYeri = girdi.IndexOfAny(operatorler);
        char islemOperatoru = girdi[operatorYeri];

        // İşlem operatörüne göre işlemleri gerçekleştir
        double sonuc = 0;
        switch (islemOperatoru)
        {
            case '+':
                sonuc = birinciDeger + ikinciDeger;
                break;
            case '-':
                sonuc = birinciDeger - ikinciDeger;
                break;
            case '*':
                sonuc = birinciDeger * ikinciDeger;
                break;
            case '/':
                sonuc = birinciDeger / ikinciDeger;
                break;
        }

        // Sonucu yuvarla ve kültürden bağımsız olarak biçimlendir
        sonuc = Math.Round(sonuc);
        Console.WriteLine("Sonuç: {0}", sonuc.ToString(CultureInfo.InvariantCulture));

        Console.Read();
    }
}
```