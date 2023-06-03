---
layout: post
title: İstenen Öğeleri Listeden Kaldır
date: 2023-06-03 03:02 +0300
categories: Coding-Challenges
tags: Dizi, Liste, Değer, Sil
excerpt: Programcıya; iki farklı liste sunuluyor. İkinci, yani silinecek sayıların olduğu listede bulunan değerleri ana listeden silmesi isteniyor...
---

### Soru

Programcıya; iki farklı liste (sayiListesi, silinecekSayiListesi) sunuluyor. İkinci, yani silinecek sayıların olduğu listede bulunan değerleri ana listeden silmesi isteniyor.

### Örnek

| Girdi                                                                                        | Çıktı                    |
| -------------------------------------------------------------------------------------------- | ------------------------ |
| **sayiListesi**: 1, 1, 2, 3, 1, 2, 3, 4 <br> **silinecekSayiListesi** 1,3                    | **sonuc**: 2, 2, 4       |
| **sayiListesi**: 8, 2, 7, 2, 3, 4, 6, 5, 4, 4, 1, 2, 3 <br> **silinecekSayiListesi** 2, 4, 3 | **sonuc**: 8, 7, 6, 5, 1 |
| **sayiListesi**: 5, 5, 6, 7 <br> **silinecekSayiListesi** 5                                  | **sonuc**: 6,7           |

### Çözüm - C#

```csharp
using System;
using System.Linq;

namespace CodingChallenges
{
    public class Program
    {
        static void Main()
        {
            int[] sayiListesi = new int[] { 1, 1, 2, 3, 1, 2, 3, 4 };
            int[] silinecekSayiListesi = new int[] { 1, 3 };

            // Liste, silinecek sayı listesindeki içermiyorsa bu sayıları al
            var sonuc = sayiListesi
                .Where(i => !silinecekSayiListesi.Contains(i));

            Console.WriteLine(String.Join(", ", sonuc));

            Console.Read();
        }
    }
}
```

### Çözüm - Python

```python
sayi_listesi = [1, 1, 2, 3, 1, 2, 3, 4]
silinecek_sayi_listesi = [1, 3]

# Silenecek sayı listedesindeki sayı, listede var olduğu sürece sil
for sayi in silinecek_sayi_listesi:
    while sayi in sayi_listesi:
        sayi_listesi.remove(sayi)

print(sayi_listesi, sep=",")
```
