---
layout: post
title: İsimleri Yıldızlı Yaz
date: 2023-06-10 03:02 +0300
categories: Coding-Challenges
tags: Yıldız, İsim, Veri
excerpt: Programcıya ad ve soyaddan oluşan bir değer veriliyor. Bu noktadan sonra ise, girilen isimdeki her bir değerin baş harfini büyük yapıp, kalan harfleri ise yıldızlı yazması isteniyor...
---

### Soru

Programcıya ad ve soyaddan oluşan bir değer **(isim)** veriliyor. Bu noktadan sonra ise, girilen isimdeki her bir değerin baş harfini büyük yapıp, kalan harfleri ise yıldızlı yazması isteniyor.

### Örnek

| Girdi                    | Çıktı                          |
| ------------------------ | ------------------------------ |
| **isim**: Ali ufuk cakir | **sonuc**: A** U\*** C\*\*\*\* |
| **isim**: Ece kalır      | **sonuc**: E** K\*\***         |
| **isim**: ahmet Bulduk   | **sonuc**: A\***\* B\*\*\*\*** |

### Çözüm - C#

```csharp
using System;
using System.Collections.Generic;

namespace Test
{
    public class Program
    {
        private static void Main()
        {
            string isim = "Mehmet üstün kal";

            // Her bir ismin baş harfini büyük yapıp diziye dönüştür
            string[] dizi = isim.Split(' ');


            List<string> deger = new List<string>();
            // Her bir dizi değerini tek tek al
            foreach (string ad in dizi)
            {
                // Kullanıcı baş harf yazmasa da baş harfleri büyük yap
                string yeniDeger = ad[0].ToString().ToUpper();

                // Dizideki her bir isimdeki ilk harf haricinde olanları yıldızla değiştir
                for (int i = 1; i < ad.Length; i++)
                    yeniDeger += ad[i].ToString().Replace(ad[i].ToString(), "*");

                deger.Add(yeniDeger);
            }

            Console.WriteLine(string.Join(" ", deger));

            Console.Read();
        }
    }
}
```

### Çözüm - Python

```python
isim = "Mehmet Üstün kal"

# Her bir ismin baş harfini büyük yapıp diziye dönüştür
dizi = isim.title().split()

yildizli_gorunum = ""
# Her bir dizi değerini tek tek al
for ad_soyad in dizi:
    # Kullanıcı baş harf yazmasa da baş harfleri büyük yap
    yildizli_gorunum += ad_soyad[0].upper()

    # Dizideki her bir isimdeki ilk harf haricinde olanları yıldızla değiştir
    for harf in ad_soyad[1:]:
        yildizli_gorunum += harf.replace(harf, "*")

    # Diğer dizi değerine geçerken boşluk ekle
    yildizli_gorunum += " "

print(yildizli_gorunum)
```
