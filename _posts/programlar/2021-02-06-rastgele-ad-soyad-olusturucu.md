---
layout: post
title: Rastgele Ad Soyad Oluşturucu
date: 2021-02-06 12:43 +0300
categories: Programlar
tags: Ad Soyad Oluşturucu, Random Name Generator, Rastgele, Rastgele Ad Soyad Oluşturucu, Rasgele
excerpt: İşte gene ihtiyaçtan yazdığım bir program daha. Excel'de tablolar üzerinde çalıştığım ve farklı konulara dair pratik yaptığım zaman rastgele sayı üretimini ilgili fonksiyondan kolayca yaparken aynı işlemi maalesef rastgele ad soyadlarda yapamıyordum. Haliyle sütunlarda ad soyad eksikliği göze çarpıyordu...
redirect_from:
  - /programlar/rastgele-ad-soyad-olusturucu/
  - /programlar/rastgele-ad-soyad-olusturucu/attachment/rastgele-ad-soyad-olusturucu-2/
  - /etiket/rastgele-ad-soyad-olusturucu/
---
![rastgele-ad-soyad-olusturucu](/images/programlar/rastgele-ad-soyad-olusturucu.png){: width="33%"} İşte gene ihtiyaçtan yazdığım bir program daha. Excel'de tablolar üzerinde çalıştığım ve farklı konulara dair pratik yaptığım zaman rastgele sayı üretimini ilgili fonksiyondan kolayca yaparken aynı işlemi maalesef rastgele ad soyadlarda yapamıyordum. Haliyle sütunlarda ad soyad eksikliği göze çarpıyordu. Böyle durumlarda sallama isimler girmek hem canımı sıkıyor hem de internette isimler/markalar içeren hazır seçenekleri bulmaya beni yönlendiriyordu. En sonunda illallah deyip internette hazır isimlere dair kısa bir veritabanı araştırması yaparken anonim halde 14.115 ismin yer aldığı bir liste buldum (evet, bazı isimler çok tırt!) ve böyle bir programa ihtiyaç duyduğum için vakit kaybetmeden aksiyona geçtim.

Programı ilk yazdığım zaman sadece rastgele isim üretmekteydi. Bunun yetersiz olduğunu farkına varınca kah internetteki bazı sitelerden kah da önceki dönem milletvekillerinin soyadlarını alarak 1.447 bunları aynı veritabanına ekledim. Finaldeyse ortaya bu ilginç program çıktı. Ve son olarak, programın performanslı çalışması için baya bir optimizasyon yapmaya çalıştım. Önceki versiyonlara göre çok daha hızlı işlem yapabiliyor artık. Programın özelliklerine gelecek olursak;

- Tamı tamına 14.115 x 1.447 = 20.424.405 tane rastgele ad soyad üretebilme,
- Veritabanına eklediğiniz yeni ad ve soyadlara göre genişleyebilme,
- Tek seferde maksimum 500 adet rastgele ad soyad üretebilme (Fazla abartmanın alemi yok),
- Üretilen ad ve soyadları metin belgesi (.txt) olarak kaydetme,
- Üretilen ad ve soyadları Excel çalışma sayfasına aktarma.

{:.tablo-ortali}
| Rastgele Ad Soyad Oluşturucu <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.2-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele Ad Soyad Oluşturucu (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|---------------------------------------------|-------------------------------------------|
| **Boyut**: 336.0 KB                       | **Boyut**: 1.17 MB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/njej547k03zi1ot/rastgele-ad-soyad-olusturucu.zip?dl=1) | **İndir**: [Link](https://www.dropbox.com/s/xxa59mmaaqoe0zw/rastgele-ad-soyad-olusturucu-proje.zip?dl=1) |