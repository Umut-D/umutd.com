---
layout: post
title: Harflerin Tekrar Sayısını Yıldızla Belirt
date: 2020-09-26 11:26 +0300
categories: Coding-Challenges
tags: Harf, Yıldız, Adet, Tane, Asteriks
excerpt: Programcıya herhangi bir şehir ismi veriliyor. Sonrasında, yıldız işareti/asteriks kullanarak her bir harfin dizede kaç kez göründüğünü gösteren yeni bir dize döndürmesi isteniyor. Harf ve yıldız belli formatta yazıldıktan sonra, her harf aralığına virgül eklenerek sonuçta gösterilmesi bekleniyor...
---
### Soru
Programcıya herhangi bir şehir **(sehir)** ismi veriliyor. Sonrasında, yıldız işareti/asteriks (*) kullanarak her bir harfin dizede kaç kez göründüğünü gösteren yeni bir dize döndürmesi isteniyor. Harf ve yıldız belli formatta yazıldıktan sonra, her harf aralığına virgül eklenerek sonuçta gösterilmesi bekleniyor.

### Örnek

| Girdi                      | Çıktı                               |
|----------------------------|-------------------------------------|
| **girilenCumle**: Ankara   | **Sonuç**: a:***,n:*,k:*,r:*        |
| **girilenCumle**: Chicago" | **Sonuç**: c:**,h:*,i:*,a:*,g:*,o:* |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

class Program
{
    public static void Main()
    {
        string sehir = "Ankara";

        // Karakter ve yıldız (Asteriks) değerlerini yazmak için sözlük dizisi oluştur
        Dictionary<char, string> degerler = new Dictionary<char, string>();
        // Şehir adını küçük harfli ve boşluksuz hale getir
        foreach (char harf in sehir.ToLower().Replace(" ", ""))
        {
            int sayac = 0;
            // Tekrar eden harf yoksa sözlüğe ekleme yap
            if (!degerler.ContainsKey(harf))
            {
                sayac = 1;
                degerler.Add(harf, sayac.ToString());
            }
            // Tekrar eden harf varsa sayacı arttır ve o harfin tekrar sayısını güncelle
            else
            {
                sayac++;
                degerler[harf] += sayac;
            }
        }

        // Tüm değerleri birleştir
        string sonuc = "";
        foreach (KeyValuePair<char, string> tek in degerler)
        {
            sonuc += tek.Key + ":" + tek.Value.Replace("1", "*") + ",";
        }

        // Sonucun sonunda virgül varsa kırp
        Console.WriteLine($"{sonuc.TrimEnd(',')}");

        Console.Read();
    }
}
```

