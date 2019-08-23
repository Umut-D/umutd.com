---
layout: post
title: Dersler ve Ders Notları
date: 2019-02-16 19:33 +0300
categories: Coding-Challenges
tags: Sıralama, Ders Notları, Ders
---
### Soru
Programcıya çeşitli ders ve test notlarını içeren (bir sözlük -Dictionary- sınıfında) bir yapı sunuluyor. Bu noktadan sonra ise programcıdan, test puanının en az 60 olduğu dersleri ve bunu da azalan sıraya göre listeleyen bir program yazması isteniyor.

**Not**: Sonuç ekranında tekrar eden değerler bulunmamalıdır.

### Örnek

| Girdi                                                                 | Çıktı                                |
|-----------------------------------------------------------------------|--------------------------------------|
| **gedilenDersler**: {"Almanca", 40}, {"İngilizce", 71}, {"Çince", 93} | **Sonuç**: Çince-93<br>İngilizce-71  |
| **gedilenDersler**: {"Tarih", 10}, {"Geometri", 80}, {"Felsefe", 65}  | **Sonuç**: Geometri-80<br>Felsefe-65 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
 
class Program
{
    static void Main()
    {
        // Dersler ve notlar veriliyor
        Dictionary<string, int> dersler = new Dictionary<string, int>
        {
            {"Java", 10},
            {"Ruby", 80},
            {"Python", 65}
        };
 
        List<string> gecilenDersler = new List<string>();
 
        // Her bir ders notunu, azalan sıraya göre ayır (Yaşasın Linq)
        foreach (KeyValuePair<string, int> author in dersler.OrderByDescending(deger => deger.Value))
        {
            // Notlar 60'ın üzerinde ise yeni diziye ekle
            if (author.Value >= 60)
            {
                gecilenDersler.Add(author.Key + "-" + author.Value);
            }
        }
 
        // Sonuçları göster
        foreach (string ders in gecilenDersler)
        {
            Console.WriteLine(ders);
        }
 
        Console.Read();
    }
}
```