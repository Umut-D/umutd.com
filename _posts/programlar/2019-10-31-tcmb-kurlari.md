---
layout: post
title: Türkiye Cumhuriyeti Merkez Bankası (TCMB) Kurları
date: 2019-10-31 00:43 +0300
categories: Programlar
tags: Döviz, Döviz Kuru, Kurlar, TCMB, Türkiye Cumhuriyeti Merkez Bankası
redirect_from:
  - /programlar/tcmb-kurlari/
  - /etiket/turkiye-cumhuriyeti-merkez-bankasi/
---
![tcmb-kurlari](/images/programlar/tcmb-kurlari.png){: width="56%"} Genişletilebilir İşaretleme Dili (Extensible Markup Language, XML) hem Lojistik Bilgi Sistemleri dersinde anlattığım, hem de C#'da uğraşmayı sevdiğim konuların başında geliyor. Hiç doğru düzgün bir XML projesi yapmadığımı düşünürken aklıma XML’i düzgün bir şekilde kullanan ve sık sık güncellenen Türkiye Cumhuriyeti Merkez Bankası (TCMB) kurlar sayfası aklıma geldi. Ekonomiden zerre kadar anlamayan, ancak ekonomideki her haltın bir teorisi olduğunu bilen biri olarak dinamik olarak farklı para birimlerinin kurları çekerek kullanıcıya bilgi veren bir programın fena olmayacağını düşündüm.

C#’da DataSet'in kolaylığı ve XML sınıfının esnekliğiyle programı yazarken zorlandığım söylenemez. En nihayetinde ortaya iş gören, gerçekten güvenilir bir devlet kaynağından kur verlerini indirilebilen bir program ortaya çıktı. Adet olduğu üzere programın yegane özelliğine gelecek olursak;

- TCMB’nin resmi web sayfasından güncel veya eski tarihli döviz alış/satış ve döviz efektif alış/satış bilgilerini tarih göre çekme,
- Mevcut bilgilerin paylaşıldığı ilk gün olan *2 Mayıs 1996'dan, bugüne değin* tüm kur bilgilerini gösterme.

{:.tablo-ortali}
| Türkiye Cumhuriyeti Merkez Bankası <br>(TCMB) Kurları<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.12-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Türkiye Cumhuriyeti Merkez Bankası <br>(TCMB) Kurları (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: bb9aad335faeb3065c3d77baef5a5c5b | **MD5**: d1e122d914196b2bfca2c463bb99bd9e | 
| **Boyut**: 11.7 KB                       | **Boyut**: 282.0 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/43cigy02efq2t9k/tcmb-kurlari.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/vecdmokm56xk2tx/tcmb-kurlari-proje.zip?dl=1)                      |