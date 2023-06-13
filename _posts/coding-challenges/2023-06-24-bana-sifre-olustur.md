---
layout: post
title: Bana Şifre Oluştur
date: 2023-06-24 03:02 +0300
categories: Coding-Challenges
tags: Rastgele, Random, Şifre
excerpt: ...
---

### Soru

Programcıya; .

### Örnek

| Girdi               | Çıktı           |
| ------------------- | --------------- |
| **sayiListesi**: 1, | **sonuc**: True |

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
