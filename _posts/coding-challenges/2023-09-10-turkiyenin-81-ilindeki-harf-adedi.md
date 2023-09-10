---
layout: post
title: Türkiye'nin 81 İlindeki Harf Adedi
date: 2023-09-10 03:02 +0300
categories: Coding-Challenges
tags: Kim Milyoner Olmak İster, Şehir, Türkiye
excerpt: Programcıdan, Türkiye'nin 81 ilindeki harf adedini listeleyen bir program yazması ve sayılara göre büyükten küçüğe sıralaması isteniyor...
---

### Soru

> **Kim Milyoner Olmak İster** programında, 1 milyon liralık "Türkiye'deki 81 ilin adında bu dört harften hangisi diğer üçünden daha az bulunur" sorusunu görünce "Bunun kodunu yazayım da programın sonunu beklemeyeyim" derken aklıma gelen bir Coding Challenge bu.

Programcıdan, Türkiye'nin 81 ilindeki harf adedini listeleyen bir program yazması ve sayılara göre büyükten küçüğe sıralaması isteniyor.

### Çözüm - C#

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Program
{
    static void Main()
    {
        List<string> sehirler = new List<string>
        {
            "Adana", "Adıyaman", "Afyon", "Ağrı", "Amasya", "Ankara", "Antalya", "Artvin", "Aydın", "Balıkesir", "Bilecik", "Bingöl", "Bitlis", "Bolu", "Burdur", "Bursa", "Çanakkale", "Çankırı", "Çorum", "Denizli", "Diyarbakır", "Edirne", "Elazığ", "Erzincan", "Erzurum", "Eskişehir", "Gaziantep", "Giresun", "Gümüşhane", "Hakkari", "Hatay", "Isparta", "Mersin", "İstanbul", "İzmir", "Kars", "Kastamonu", "Kayseri", "Kırklareli", "Kırşehir", "Kocaeli", "Konya", "Kütahya", "Malatya", "Manisa", "Kahramanmaraş", "Mardin", "Muğla", "Muş", "Nevşehir", "Niğde", "Ordu", "Rize", "Sakarya", "Samsun", "Siirt", "Sinop", "Sivas", "Tekirdağ", "Tokat", "Trabzon", "Tunceli", "Şanlıurfa", "Uşak", "Van", "Yozgat", "Zonguldak", "Aksaray", "Bayburt", "Karaman", "Kırıkkale", "Batman", "Şırnak", "Bartın", "Ardahan", "Iğdır", "Yalova", "Karabük", "Kilis", "Osmaniye", "Düzce"
        };

        var harfler = new Dictionary<char, int>();
        foreach (string sehir in sehirler)
        {
            foreach (char harf in sehir.ToLower())
            {
                if (!harfler.ContainsKey(harf))
                    harfler[harf] = 0;

                harfler[harf]++;
            }
        }

        var harfleriSirala = harfler.OrderByDescending(p => p.Value);
        foreach (var harfSayi in harfleriSirala)
            Console.WriteLine(harfSayi.Key + "-" + harfSayi.Value);

        Console.Read();
    }
}
```
