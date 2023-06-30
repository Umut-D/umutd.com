---
layout: post
title: IPv4 Değerini Sayısal İfadeye Dönüştür
date: 2023-07-01 00:02 +0300
categories: Coding-Challenges
tags: Dönüşüm, IPv4, Octet
excerpt: Programcıya; bir IPv4 değeri veriliyor. Bu IP değerinin, 4 ayrı oktetten ve byte değerlerden oluştuğu biliniyor. Bu noktada ise programdan; her bir oktet değerinin binary gösterimini (Örn. 128 ifadesi binary olarak 10000000, 1 ifadesi ise 00000001'dir gibi) elde ederek 4 ayrı oktetin sayısal (int olarak) toplamını elde etmesi isteniyor...
---

### Soru

Programcıya; bir IPv4 (ipDegeri) değeri veriliyor. Bu IP değerinin, 4 ayrı oktetten ve byte değerlerden oluştuğu biliniyor. Bu noktada ise programdan; her bir oktet değerinin binary gösterimini (Örn. 128 ifadesi binary olarak 10000000, 1 ifadesi ise 00000001'dir gibi) elde ederek 4 ayrı oktetin sayısal (int olarak) toplamını elde etmesi isteniyor.

### Örnek

| Girdi                     | Çıktı                 |
| ------------------------- | --------------------- |
| **ipDegeri**: 128.32.10.1 | **sonuc**: 2149583361 |
| **ipDegeri**: 1.1.1.1     | **sonuc**: 16843009   |

### Çözüm - C#

```csharp
using System;

namespace Test
{
    public static class Program
    {
        private static void Main()
        {
            string girilenIp = "128.32.10.1";

            string[] ipDizisi = girilenIp.Split('.');
            int uzunluk = ipDizisi.Length;

            // Dizideki tüm değerleri parça parça sayıya dönüştür
            int[] octetler = new int[uzunluk];
            for (int i = 0; i < uzunluk; i++)
                octetler[i] = Convert.ToInt32(ipDizisi[i]);

            // Dönüştürülen değerleri tek tek binary koduna dönüştür
            string[] donusturulenDegerler = new string[uzunluk];
            for (int i = 0; i < uzunluk; i++)
                donusturulenDegerler[i] = Convert.ToString(octetler[i], 2).PadLeft(8, '0');

            // Dört dilim olan octetlerin hepsini tek parça haline getir
            string tumOctetler = string.Join("", donusturulenDegerler);

            // Octetleri sayısal ifadeye dönüştürerek binary olarak topla
            long toplam = Convert.ToInt64(tumOctetler, 2);
            Console.WriteLine($"Toplam: {toplam}");

            Console.Read();
        }
    }
}
```

### Çözüm - Python

```python
girilenIp = "1.1.1.1"

ip_dizisi = girilenIp.split('.')

# Dizideki tüm değerleri parça parça sayıya dönüştür
octetler = []
for ip in ip_dizisi:
    octetler.append(int(ip))

# Dönüştürülen değerleri tek tek binary koduna dönüştür
donusturulen_degerler = []
for deger in octetler:
    donusturulen_degerler.append(f'{deger:08b}')

# Dört dilim olan octetlerin hepsini tek parça haline getir
tum_octetler = str.join("", donusturulen_degerler)

# Octetleri sayısal ifadeye dönüştürerek binary olarak topla
toplam = int(tum_octetler, 2)
print(f"Toplam: {toplam}")
```
