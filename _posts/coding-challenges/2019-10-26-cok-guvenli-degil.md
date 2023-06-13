---
layout: post
title: Çok Güvenli Değil
date: 2019-10-26 08:47 +0300
categories: Coding-Challenges
tags: Regex, Alfanümerik
excerpt: Programcıdan, bir kullanıcı giriş dizesinin (girilenIfade) alfanümerik olup olmadığını doğrulayan bir program oluşturması isteniyor.
---

### Soru

Programcıdan, bir kullanıcı giriş dizesinin **(girilenIfade)** alfanümerik olup olmadığını doğrulayan bir program oluşturması isteniyor. Ayrıca alfanümerik ifadenin;

- Büyük harf(ler), küçük harf(ler) ve 0'dan 9' kadar olan rakamlara izin veriliyor,
- En az bir karakterden oluşması isteniyor (Boş olmamalı),
- Boşluk ya da altçizgi içermemesi gerektiği belirtiliyor.

### Örnek

| Girdi                    | Çıktı            |
| ------------------------ | ---------------- |
| **girilenIfade**: "a4A8" | **Sonuç**: True  |
| **girilenIfade**: "ne_A8 | **Sonuç**: False |

### Çözüm - C#

```csharp
using System;
using System.Text.RegularExpressions;

class Program
{
    static void Main()
    {
        string girilenIfade = "a4Ap";
        bool sonuc = false;

        // Boyut kontrolü yap
        if (girilenIfade.Length > 0)
        {
            // Boş ya da boşluğa sahip değilse devam et
            if (!String.IsNullOrWhiteSpace(girilenIfade))
            {
                // İstenen kalıba uyan Regular Expressions (Düzenli İfadeler) ile olayı çöz
                Regex duzenliIfade = new Regex(@"^[a-zA-Z0-9]*$");
                sonuc = duzenliIfade.IsMatch(girilenIfade);
            }
        }

        Console.WriteLine("Sonuç: {0}", sonuc);
        Console.Read();
    }
}
```

### Çözüm - Python

```python
sifre = "a2_A4"

if len(sifre) != 0:
    if str.isalnum(sifre) and not str.isspace(sifre):
        print(True)
    else:
        print(False)
```
