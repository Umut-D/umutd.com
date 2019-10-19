---
layout: post
title: Kredi Kartı Numarasının Doğruluğunu Kontrol Et
date: 2019-10-19 08:47 +0300
categories: Coding-Challenges
tags: Kredi Kartı, Luhn, Luhn Algoritması
excerpt: Programcıdan, girilen kredi kartı numarasının doğruluğunu Luhn Algoritmasına göre kontrol eden bir kod oluşturması isteniyor.
---
### Soru
Programcıdan, girilen kredi kartı numarasının **(girilenKartNumarasi)** doğruluğunu **Luhn Algoritmasına** göre kontrol eden bir kod oluşturması isteniyor.

> **Luhn Algoritması**,  IBM'de çalışan bilim adamı Hans Peter Luhn tarafından üretilen bu algoritma, mod 10 algoritması olarak da bilinir. Dünyadaki tüm kredi kartı numaraları bir algoritmaya göre üretilirler. IMEI Numarası, Kanada Sosyal Güvenlik Numarası gibi birçok numara da Luhn algoritmasına benzer şekilde üretilir.

### Örnek

| Girdi                            | Çıktı                               |
|----------------------------------|-------------------------------------|
| **girilenSayi**: 371449635398431 | **Sonuç**: Kart numarası doğrudur.  |
| **girilenSayi**: 123456789101112 | **Sonuç**: Kart numarası yanlıştır. |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

internal class Program
{
    private static void Main()
    {
        long girilenKartNumarasi = 371449635398431;

        // 1. Girilen Sayının son hanesini ayrı tut
        string sonHaneOlmayanSayi = girilenKartNumarasi.ToString().Remove(girilenKartNumarasi.ToString().Length - 1);
        long duzenliSayi = long.Parse(sonHaneOlmayanSayi);

        // 2. Tek sırada olan değerleri al
        List<int> tekSiradakiSayilar = new List<int>();
        for (int i = 1; i < duzenliSayi.ToString().Length; i += 2)
        {
            int tekSiradakiSayi = int.Parse(duzenliSayi.ToString().Substring(i, 1)) * 2;
            tekSiradakiSayilar.Add(tekSiradakiSayi);
        }

        // 3. Çift sırada olan değerleri 2 ile çarp
        List<int> ciftSiradakiSayilar = new List<int>();
        for (int i = 0; i < duzenliSayi.ToString().Length; i += 2)
        {
            int ciftSiradakiSayi = int.Parse(duzenliSayi.ToString().Substring(i, 1));
            ciftSiradakiSayilar.Add(ciftSiradakiSayi);
        }

        // 4. Tek sıradaki sayılardan elde edilen değerleri topla
        List<int> tekSayilarinToplami = new List<int>();
        foreach (int tekSayi in tekSiradakiSayilar)
        {
            if (tekSayi < 10)
            {
                tekSayilarinToplami.Add(tekSayi);
            }
            else
            {
                int ilkSayi = Convert.ToInt32(tekSayi.ToString().Substring(0, 1));
                int ikinciSayi = Convert.ToInt32(tekSayi.ToString().Substring(1));

                tekSayilarinToplami.Add(ilkSayi + ikinciSayi);
            }
        }

        // 5. Ayrılan iki ayrı sıradaki sayıları birleştir
        List<int> tumSayilar = new List<int>();
        tumSayilar.AddRange(tekSayilarinToplami);
        tumSayilar.AddRange(ciftSiradakiSayilar);

        // 6. Tüm değerleri topla, sonucu 9 ile çarpıp son haneyi al
        int toplam = 0;
        foreach (int sayi in tumSayilar)
        {
            toplam += sayi;
        }

        int sonuc = toplam * 9;
        sonuc %= 10;

        // 7. Girilen sayının son hanesi ile elde edilen son kontrol sayını karşılaştır
        bool sonHaneDogruMu = girilenKartNumarasi.ToString().EndsWith(sonuc.ToString());
        if (sonHaneDogruMu)
        {
            Console.WriteLine("Kart numarası doğrudur.");
        }
        else
        {
            Console.WriteLine("Kart numarası yanlıştır.");
        }

        Console.Read();
    }
}
```