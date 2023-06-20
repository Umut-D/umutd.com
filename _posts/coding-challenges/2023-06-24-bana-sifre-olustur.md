---
layout: post
title: Bana Şifre Oluştur
date: 2023-06-20 18:02 +0300
categories: Coding-Challenges
tags: Rastgele, Random, Şifre
excerpt: Programcıya; büyük ve küçük harflerden, rakamlardan ve özel karakterlerden oluşan bir şifre oluşturucu yazma görevi veriliyor. Buna ek olarak ise; kullanıcının girdiği adetlere göre hazırlanan bu şifrenin dağınık sırada olması isteniyor...
---

### Soru

Programcıya; büyük ve küçük harflerden, rakamlardan ve özel karakterlerden oluşan bir şifre oluşturucu yazma görevi veriliyor. Buna ek olarak ise; kullanıcının girdiği adetlere göre hazırlanan bu şifrenin dağınık sırada olması isteniyor.

### Örnek

| Girdi                                                                                                  | Çıktı           |
| ------------------------------------------------------------------------------------------------------ | --------------- |
| **kucukHarfAdedi**: 1 <br> **buyukHarfAdedi**: 1 <br> **rakamAdedi**: 1 <br> **ozelKarakterAdedi**: 1, | **sonuc**: ?a2P |

### Çözüm - C#

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace Test
{
    public class Program
    {
        private static void Main()
        {
            // Kullanıcı tarafından istenen adetler
            int kucukHarfAdedi = 4;
            int buyukHarfAdedi = 4;
            int rakamAdedi = 2;
            int ozelKarakterAdedi = 2;

            // Sistematik olarak değerleri oluştur (Her bir değeri tek tek almak işime gelmedi)
            var buyukHarfler = Enumerable.Range(65, 26).Select(i => (char)i).ToList();
            var kucukHarfler = buyukHarfler.Select(char.ToLower).ToList();
            var rakamlar = Enumerable.Range(48, 10).Select(i => (char)i).ToList();
            var ozelKarakterler = Enumerable.Range(33, 15).Select(i => (char)i).ToList();

            // Sözlük kullanarak, döngü ile değerlere eriş (Şansımı zorlamak istedim)
            Dictionary<List<char>, int> dizi = new Dictionary<List<char>, int>
            {
                { buyukHarfler, buyukHarfAdedi },
                { kucukHarfler, kucukHarfAdedi },
                { rakamlar, rakamAdedi },
                { ozelKarakterler, ozelKarakterAdedi }
            };

            // Sıralı şekilde elde edilen sifre değişkeninden yerleri değiştir
            var karakterDizisi = Olustur(dizi);
            var karisikSifre = karakterDizisi.OrderBy(x => Guid.NewGuid());

            // Dağınık hale getirilen dizi değerlerinin birleştir
            Console.WriteLine(string.Join("", karisikSifre));

            Console.Read();
        }

        private static char[] Olustur(Dictionary<List<char>, int> dizi)
        {
            StringBuilder sifre = new StringBuilder();
            Random rastgeleSayi = new Random();

            foreach (var deger in dizi)
            {
                for (int i = 0; i < deger.Value; i++)
                {
                    int sayi = rastgeleSayi.Next(0, deger.Key.Count);
                    sifre.Append(deger.Key[sayi]);
                }
            }

            return sifre.ToString().ToCharArray();
        }
    }
}
```

### Çözüm - Python

```python
import random
import string

sifre = []

# Kullanıcı tarafından istenen adetler
kucuk_harf_adedi = 4
buyuk_harf_adedi = 4
rakam_adedi = 2
ozel_karakter_adedi = 2

# Tüm karakterleri oluşturup diziye ekle
kucuk_harfler = list(string.ascii_lowercase)
buyuk_harfler = list(string.ascii_uppercase)
rakamlar = list(string.digits)
ozel_karakterler = list(string.punctuation)

# Sözlük kullanarak, döngü ile değerlere eriş (Şansımı zorlamak istedim)
sozluk = {
    "kucuk": [kucuk_harf_adedi, kucuk_harfler],
    "buyuk": [buyuk_harf_adedi, buyuk_harfler],
    "rakam": [rakam_adedi, rakamlar],
    "ozel": [ozel_karakter_adedi, ozel_karakterler]
}

# Her bir döngüde türe göre üretim yap
for k, v in sozluk.items():
    adet = sozluk[k][0]
    for _ in range(adet):
        degerler = sozluk[k][1]
        sifre.append(random.choice(degerler))

# Sıralı şekilde elde edilen sifre değişkeninden yerleri değiştir
random.shuffle(sifre)

# Dağınık hale getirilen dizi değerlerinin birleştir
yeni_sifre = "".join(sifre)

print(f"Oluşturulan şifre: {yeni_sifre}")
```
