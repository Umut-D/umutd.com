---
layout: post
title: En Büyük İki Yaş
date: 2023-04-29 16:02 +0300
categories: Coding-Challenges
tags: Yaş, En Büyük Yaş, Sıralama
excerpt: Programcıya dağınık bir şekilde verilen yaş dizisi veriliyor. Sonrasında ise dizi içindeki en yüksek iki sayıyı döndürülmesi gerektiği belirtiliyor...
---

### Soru

Programcıya dağınık bir şekilde verilen yaş dizisi **(yaslar)** veriliyor. Sonrasında ise dizi içindeki en yüksek iki yaşı döndürülmesi gerektiği belirtiliyor.

Dizinin her zaman en az 2 öğe içereceği ifade edilirken, sonuç olarak gösterilen yaşların [en büyük ikinci yaş, en büyük yaş] şeklide görüntülenmesi isteniyor.

### Örnek

| Girdi                       | Çıktı        |
| --------------------------- | ------------ |
| **[1, 2, 10, 8]**           | **[8, 10]**  |
| **[1, 3, 10, 0]**           | **[3, 10]**  |
| **[1, 5, 87, 45, 8, 8, 5]** | **[45, 87]** |

### Çözüm - C#

```csharp
using System;

class Program
{
    public static void Main()
    {
        var yaslar = new[] { 1, 64, 5, 42, 25, 33, 8, 11 };

        // Linq ile hayat daha kolay!
        var sonuc = yaslar
            .OrderByDescending(i => i) // Büyükten küçüğe sırala
            .Take(2) // İlk iki değeri al
            .Reverse(); // Değerleri ters çevir

        Console.WriteLine(string.Join(" ", sonuc));

        Console.Read();
    }
}
```

### Çözüm - Python

```python
import itertools

yaslar = [1, 64, 5, 42, 25, 33, 8, 11]

ters_sirali_liste = sorted(yaslar, reverse=True)
en_buyuk_iki_sayiyi_al = list((itertools.islice(ters_sirali_liste, 2)))
sirala = sorted(en_buyuk_iki_sayiyi_al)

sonuc = " ".join(map(str, sirala))
print(sonuc)
```
