---
layout: post
title: Günü Almanca Döndür
date: 2023-05-20 03:02 +0300
categories: Coding-Challenges
tags: Gün, Almanca, Tarih, Zaman
excerpt: Programcıya; kullanıcı tarafından bir sayı değeri veriliyor. Bu noktadan sonraysa programcıdan, girilen sayının haftanın hangi gününe denk geldiğini almanca diliyle yazdırması isteniyor...
---

### Soru

Programcıya; kullanıcı tarafından bir sayı değeri (girilenSayi) veriliyor. Bu noktadan sonraysa programcıdan, girilen sayının haftanın hangi gününe denk geldiğini almanca diliyle yazdırması isteniyor.

### Örnek

| Girdi              | Çıktı               |
| ------------------ | ------------------- |
| **girilenSayi**: 3 | **sonuc**: Mittwoch |
| **girilenSayi**: 6 | **sonuc**: Samstag  |

### Çözüm - C#

```csharp
using System;
using System.Globalization;
using System.Linq;

namespace CodingChallenges
{
    public class Program
    {
        static void Main()
        {
            int girilenSayi = 6;

            // Gün değerlerini Almanca ayarla
            var deCulture = new CultureInfo("de-DE");

            // Sıra ve Gün değerlerini sözlük olarak birleştir
            // Evet, macera peşindeyim. Sözlük olarak yapmak istedim :)
            var sira = Enumerable.Range(1, 7);
            var sozluk = sira
                .ToDictionary(gun => gun,
                    gun =>
                    {
                        var haftaninGunleri = new DateTime(1989, 01, gun).DayOfWeek;
                        return deCulture.DateTimeFormat.GetDayName(haftaninGunleri);
                    });

            // Kontrol ve sonuç zamanı
            if (sozluk.ContainsKey(girilenSayi))
                Console.WriteLine(sozluk.ElementAt(girilenSayi).Value);
            Console.WriteLine("Gün değerleri 1 ve 7 arasında olmalı!");

            Console.Read();
        }
    }
}
```

### Çözüm - Python

```python
import calendar
import locale

girilen_sayi = 6

# Gün değerlerini Almanca ayarla
locale.setlocale(locale.LC_ALL, 'de')

# Sıra ve Gün değerlerini sözlük olarak birleştir
# Evet, macera peşindeyim. Sözlük olarak yapmak istedim :)
sira = range(1, 8)
gun = calendar.day_name
sira_ve_gun = dict(zip(sira, gun))

# Kontrol ve sonuç zamanı
if 1 <= girilen_sayi <= 7:
    print(sira_ve_gun[girilen_sayi])
else:
    print("Gün değerleri 1 ve 7 arasında olmalı!")
```
