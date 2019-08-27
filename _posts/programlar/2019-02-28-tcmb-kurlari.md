---
layout: post
title: Türkiye Cumhuriyeti Merkez Bankası (TCMB) Kurları
date: 2019-02-28 12:43 +0300
categories: Programlar
tags: Döviz, Döviz Kuru, Kurlar, TCMB, Türkiye Cumhuriyeti Merkez Bankası
---
![tcmb-kurlari](/images/programlar/tcmb-kurlari.png){: width="56%"} Genişletilebilir İşaretleme Dili (Extensible Markup Language, XML) hem Lojistik Bilgi Sistemleri dersinde anlattığım, hem de C#'da uğraşmayı sevdiğim konuların başında geliyor. Hiç doğru düzgün bir XML projesi yapmadığımı düşünürken aklıma XML’i düzgün bir şekilde kullanan ve sık sık güncellenen Türkiye Cumhuriyeti Merkez Bankası (TCMB) kurlar sayfası aklıma geldi. Ekonomiden zerre kadar anlamayan, ancak ekonomideki her haltın bir teorisi olduğunu bilen biri olarak dinamik olarak farklı para birimlerinin kurları çekerek kullanıcıya bilgi veren bir programın fena olmayacağını düşündüm.

C#’da DataSet'in kolaylığı ve XML sınıfının esnekliğiyle programı yazarken zorlandığım söylenemez. En nihayetinde ortaya iş gören, gerçekten güvenilir bir devlet kaynağından kur verlerini indirilebilen bir program ortaya çıktı. Adet olduğu üzere programın yegane özelliğine gelecek olursak;

- TCMB’nin resmi web sayfasından güncel veya eski tarihli döviz alış/satış ve döviz efektif alış/satış bilgilerini tarih göre çekme,
- Mevcut bilgilerin paylaşıldığı ilk gün olan *2 Mayıs 1996'dan, bugüne değin* tüm kur bilgilerini gösterme.

{:.tablo-ortali}
| Türkiye Cumhuriyeti Merkez Bankası <br>(TCMB) Kurları<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.11-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Türkiye Cumhuriyeti Merkez Bankası <br>(TCMB) Kurları (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 0949b188d7b5b869fa30aa40d5c72988 | **MD5**: c71a7eb480146a6501e371579cc7afde | 
| **Boyut**: 11.5 KB                       | **Boyut**: 119.8 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/tcmb-kurlari.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/tcmb-kurlari-proje.zip)                      |