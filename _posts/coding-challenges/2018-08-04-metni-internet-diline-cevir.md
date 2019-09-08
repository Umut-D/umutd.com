---
layout: post
title: Metni İnternet Diline (Leetspeak) Çevir
date: 2018-08-04 19:33 +0300
categories: Coding-Challenges
tags: Dönüşüm, Tercüme, Leetspeak, İnternet Dili
redirect_from:
  - /coding-challenges/metni-internet-diline-cevir/
  - /etiket/tercume/
  - /etiket/donusum/
---
### Soru
Programcıya büyük ve ingilizce karakterler kullanılarak yazılan herhangi bir kelime/cümle **(girilenCumle)** sunuluyor. Programcıdan ise, girilen bu cümledeki harfleri belirli bir alfabeye (İnternet Dili/Leetspeak) dönüştüren bir program oluşturması isteniyor.

> **Leet (veya “1337”, ayrıca eleet ya da leetspeak olarak da bilinir)**, İnternet’te birçok dil için oluşturulmuş, başlıca kullanılan alternatif alfabe sistemi. Yansıma veya benzerlik yoluyla gliflerin benzerliği üzerinde oynanacak şekilde diğer karakterlerle yer değiştirilmesi için bazı karakterler kullanır. Örneğin leet kelimesinin leet yazılışı 1337 ve l33t; eleet kelimesinin ise 31337 ya da 3l33t’dir. (Kaynak: Vikipedi)

### Örnek

| Girdi                              | Çıktı                       |
|------------------------------------|-----------------------------|
| **girilenCumle**: SELAM            | **Sonuç**: $31@M            |
| **girilenCumle**: BU BIR DENEMEDIR | **Sonuç**: 8U 8!R D3N3M3D!R |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
class Program
{
    static void Main(string[] args)
    {
        string tuhafYazi = "BU BIR DENEMEDIR";
        string sonuc = null;
 
        Dictionary<char, char> harfler = new Dictionary<char, char>()
        {
            {'A', '@'},
            {'B', '8'},
            {'C', '('},
            {'D', 'D'},
            {'E', '3'},
            {'F', 'F'},
            {'G', '6'},
            {'H', '#'},
            {'I', '!'},
            {'J', 'J'},
            {'K', 'K'},
            {'L', '1'},
            {'M', 'M'},
            {'N', 'N'},
            {'O', '0'},
            {'P', 'P'},
            {'Q', 'Q'},
            {'R', 'R'},
            {'S', '$'},
            {'T', '7'},
            {'U', 'U'},
            {'V', 'V'},
            {'W', 'W'},
            {'X', 'X'},
            {'Y', 'Y'},
            {'Z', '2'},
            {' ', ' '}
        };
 
        // Girilen yazıdaki her bir harfi karşılaştırarak yerine ekleme yap
        foreach (char harf in tuhafYazi)
        {
            // Her bir eşleşmede anahtar değişikliği yap
            if (harfler.ContainsKey(harf))
            {
                // Sonuçlara tek tek ekleme yaparak cümleyi oluştur
                sonuc += harfler[harf];
            }
        }
 
        Console.WriteLine(sonuc);
 
        Console.Read();
    }
}
```