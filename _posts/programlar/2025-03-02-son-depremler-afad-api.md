---
layout: post
title: Son Depremler AFAD (API)
date: 2025-03-02 03:43 +0300
categories: Programlar
tags: AFAD, Son Depremler, Deprem
excerpt: Python'da kod yazmanın en keyifli yanlarından biri her bir şeyin modülü/kütüphanesi olması. Sağolsun PyPI.org da bu altyapıyı çok güzel oluşturmuş. Kodunu yazıyorsun, karşıya yüklüyorsun...
---

![son-depremler-afad-api](/images/programlar/son-depremler-afad-api.png){: width="65%"}

Python'da kod yazmanın en keyifli yanlarından biri her bir şeyin modülü/kütüphanesi olması. Sağolsun PyPI.org da bu altyapıyı çok güzel oluşturmuş. Kodunu yazıyorsun, karşıya yüklüyorsun. Sonrasında API, istenilen projede kullanıma hazır. Ben de bu gazla AFAD'ın resmi web sayfasında JSON olarak paylaştığı son depremleri çeken bir API oluşturmak istedim. Son 24 saatte Türkiye'de olan depremleri hem liste hem de sıralı düz yazı olarak gösteriyor. Fazladan içine Unit Testler de ekledim.

<b>Nasıl kullanılır:</b>

Paketi kurduktan sonra aşağıdaki import işlemini yapınız: <br>

Paketi kurduktan sonra aşağıdaki import işlemini yapınız: <br>

```python
from app.dosya.depremler import Depremler
```

**"Tarih ve Saat, Konum, Şiddet, Enlem, Boylam, Derinlik"** şeklinde olan verileri;<br>

dizi olarak göstermek için -> [['2025-03-02 01:35:45', 'Dulkadiroğlu (Kahramanmaraş)', '1.8', '37.44472', '37.1425', '7']]...<br>

```python
depremler = Depremler()
print(depremler.tum_veriler())
```

satır satır ve istenen sayıda yazdırmak için -> 2025-03-02 01:35:45 - Dulkadiroğlu (Kahramanmaraş) - 1.8 - 37.44472 - 37.1425 - 7<br>

```python
depremler = Depremler()
print(depremler.duzenli_veriler()())
```

tablo halinde ve istenen sayıda yazdırmak için (Tablo hali buradan çok daha güzel görünüyor) ->
+---------------------+---------------------------+--------+--------+---------+-----------+
| Tarih ve Saat | Konum | Şiddet | Enlem | Boylam | Derinlik |
+=====================+===========================+========+========+=========+===========+
| 2025-03-02 01:35:45 | Dulkadiroğlu (Kahramanmaraş) | 1.8 | 37.4447 | 37.1425 | 7 |
<br>

```python
depremler = Depremler()
print(depremler.tablo_veriler())
```

<br>

{:.tablo-ortali}
| Son Depremler AFAD (API) (Github) <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.1-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Son Depremler AFAD (API) (PyPI.org)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **Platform**: Tüm platformlar | **Programlama Dili**: Python |
| **Link**: [Link](https://github.com/umut-d/son-depremler-afad-api) | **Link**: [Link](https://pypi.org/project/son-depremler-afad-api/1.1.0/) |
