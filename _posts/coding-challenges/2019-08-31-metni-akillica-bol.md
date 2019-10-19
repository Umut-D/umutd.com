---
layout: post
title: Metni Akıllıca Böl
date: 2019-08-31 14:04 +0300
categories: Coding-Challenges
tags: Metin, Bölme, Düzenli İfadeler
---
### Soru
Programcıya, içerisinde ! ve [ veya ] karakterleri de içeren bir metin veriliyor. Bu noktadan sonra programcıdan; verilen metni parçalaması, fakat köşeli parantez olan alanları da olduğu gibi, yani kalıp halinde diziye aktarması isteniyor.

### Örnek

| Girdi                     | Çıktı                 |
|---------------------------|-----------------------|
| **girilenMetin**: !ben [bir ceviz] agaciyim [gülhane parkında] | **Sonuç**: "ben", "[bir ceviz]", "agaciyim", "[gülhane parkında]" |
| **girilenMetin**: [Mekanın sahibi geri geldi] !bebeleri pistten !alalim | **Sonuç**: "[Mekanın sahibi geri geldi]", "!bebeleri", "pistten", "!alalim" |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text.RegularExpressions;

class Program
{
    static void Main()
    {
        string girilenMetin = "[Mekanın sahibi geri geldi] !bebeleri pistten !alalim";
        List<string> yazilar = new List<string>();

        // Girilen metni hem köşeli parantezlere hem de kelimelere (ünlem dahil) bölerek diziye aktar
        foreach (Match eslesme in Regex.Matches(girilenMetin, @"\[(.*?)\]|[!a-zA-z]*"))
        {
            yazilar.Add(eslesme.ToString());
        }

        // Diziye aktarma sonrarı boşluklar oluşursa, boş olan dizileri yok et
        foreach (string yazi in yazilar.Where(x => !string.IsNullOrEmpty(x)).ToArray())
        {
            Console.WriteLine(yazi);
        }

        Console.Read();
    }
}
```