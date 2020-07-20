---
layout: post
title: Türkiye Cumhuriyeti Merkez Bankası (TCMB) Kurları
date: 2020-07-19 18:43 +0300
categories: Programlar
tags: Döviz, Döviz Kuru, Kurlar, TCMB, Türkiye Cumhuriyeti Merkez Bankası
excerpt: İşaretleme Dili (Extensible Markup Language, XML) hem Lojistik Bilgi Sistemleri dersinde anlattığım, hem de C#'da uğraşmayı sevdiğim konuların başında geliyor. Hiç doğru düzgün bir XML projesi yapmadığımı düşünürken aklıma XML’i düzgün bir şekilde kullanan ve sık sık güncellenen Türkiye Cumhuriyeti Merkez Bankası (TCMB) kurlar sayfası aklıma geldi...
redirect_from:
  - /programlar/tcmb-kurlari/
  - /etiket/turkiye-cumhuriyeti-merkez-bankasi/
---
![tcmb-kurlari](/images/programlar/tcmb-kurlari.png){: width="52%"} Genişletilebilir İşaretleme Dili (Extensible Markup Language, XML) hem Lojistik Bilgi Sistemleri dersinde anlattığım, hem de C#'da uğraşmayı sevdiğim konuların başında geliyor. Hiç doğru düzgün bir XML projesi yapmadığımı düşünürken aklıma XML’i düzgün bir şekilde kullanan ve sık sık güncellenen Türkiye Cumhuriyeti Merkez Bankası (TCMB) kurlar sayfası aklıma geldi. Ekonomiden zerre kadar anlamayan, ancak ekonomideki her haltın bir teorisi olduğunu bilen biri olarak dinamik olarak farklı para birimlerinin kurları çekerek kullanıcıya bilgi veren bir programın fena olmayacağını düşündüm.

C#’da DataSet'in kolaylığı ve XML sınıfının esnekliğiyle programı yazarken zorlandığım söylenemez. En nihayetinde ortaya iş gören, gerçekten güvenilir bir devlet kaynağından kur verlerini indirilebilen bir program ortaya çıktı. Adet olduğu üzere programın yegane özelliğine gelecek olursak;

- TCMB’nin resmi web sayfasından güncel veya eski tarihli döviz alış/satış ve döviz efektif alış/satış bilgilerini tarih göre çekme,
- Mevcut bilgilerin paylaşıldığı ilk gün olan *2 Mayıs 1996'dan, bugüne değin* tüm kur bilgilerini gösterme.

{:.tablo-ortali}
| Türkiye Cumhuriyeti Merkez Bankası <br>(TCMB) Kurları<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.13-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Türkiye Cumhuriyeti Merkez Bankası <br>(TCMB) Kurları (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 599ebda08f0ca322840acaa66ce5e858 | **MD5**: 88727c85518cec19a4ace405d7e0097a | 
| **Boyut**: 11.6 KB                       | **Boyut**: 84.8 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/43cigy02efq2t9k/tcmb-kurlari.zip?dl=1)         | **Proje**: [Link](https://www.dropbox.com/s/vecdmokm56xk2tx/tcmb-kurlari-proje.zip?dl=1) <br> **GitHub**: [Link](https://github.com/Umut-D/TCMB-Kurlari) |