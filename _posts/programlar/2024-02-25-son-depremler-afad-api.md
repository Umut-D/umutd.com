---
layout: post
title: Son Depremler AFAD (API)
date: 2024-02-25 03:43 +0300
categories: Programlar
tags: AFAD, Son Depremler, Deprem
excerpt: Python'da kod yazmanın en keyifli yanlarından biri her bir şeyin modülü/kütüphanesi olması. Sağolsun PyPI.org da bu altyapıyı çok güzel oluşturmuş. Kodunu yazıyorsun, karşıya yüklüyorsu...
---

![son-depremler-afad-api](/images/programlar/son-depremler-afad-api.png){: width="65%"}

Python'da kod yazmanın en keyifli yanlarından biri her bir şeyin modülü/kütüphanesi olması. Sağolsun PyPI.org da bu altyapıyı çok güzel oluşturmuş. Kodunu yazıyorsun, karşıya yüklüyorsun. Sonrasında API, istenilen projede kullanıma hazır. Ben de bu gazla AFAD'ın resmi web sayfasında JSON olarak paylaştığı son depremleri çeken bir API oluşturmak istedim. Son 24 saatte Türkiye'de olan depremleri gösteriyor. Fazladan içine Unit Testler de ekledim. Temiz kodla yazmaya dikkat ederken böyle bir şey çıktı.

<b>Nasıl kullanılır:</b>

Paketi kurduktan sonra aşağıdaki import işlemini yapınız: <br>

```python
from app.dosya.depremler import Depremler
```

"Tarih ve Saat, Konum, Şiddet, Enlem, Boylam, Derinlik" şeklinde olan verileri;<br>

- dizi olarak göstermek için -> [['2024-02-25 08:56:38', 'Serik (Antalya)', '2.6', '37.24139', '30.95028', '21.78']]...<br>

```python
depremler = Depremler()
json_veriler = depremler.json_veriler()
```

- satır satır yazdırmak için -> 2024-02-25 08:56:38 - Serik (Antalya) - 2.6 - 37.24139 - 30.95028 - 21.78<br>

```python
depremler = Depremler()
depremler.duzenli_veriler()
```

<br>

{:.tablo-ortali}
| Son Depremler AFAD API (Github) <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Son Depremler AFAD API (PyPI.org)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **Platform**: Tüm platformlar | **Programlama Dili**: Python |
| **Link**: [Link](https://github.com/umut-d/son-depremler-afad-api) | **Link**: [Link](https://pypi.org/project/son-depremler-afad-api/1.0.0/) |
