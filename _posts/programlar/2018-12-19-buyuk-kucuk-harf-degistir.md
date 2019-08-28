---
layout: post
title: Büyük Küçük Harf Değiştir
date: 2018-12-19 12:43 +0300
categories: Programlar
tags: Büyük Küçük Harf, Harf, Harf Değiştirme, Kelime
---
![buyuk-kucuk-harf-degistir](/images/programlar/buyuk-kucuk-harf-degistir.png){: width="54%"}

Geçen hafta iyi bir dostum aradı. Microsoft Word 2010’la ilgili bir soru sordu. Yazdığı makalenin küçük harfli yazılarının hepsini büyük harfe dönüştürdüğünde bir sorun olmadığını ancak makalenin ingilizce özetinde yabancı kelimeleri küçükken büyük, büyükken küçük harflere çevirdiğinde "İ-i" harfinin dönüşümde sorun çıkardığını belirtti. O konuşmada Word’ün sözlük özelliğinde değişikliğe gidip bu sorunu çözebileceğini belirttim. Sorun çözdü. Ancak Word’de aynı sorunu yaşayanlar için sürecin biraz uzun olduğunu düşündüm ve böyle bir program yazmak aklıma geldi.

Programın mantığı kolay. Yazınızı metin alanına yapıştırıyorsunuz, Türkçe haricindeki bir dile göre harf değişiklikleri yapmak istiyorsanız sağ taraftan ilgili dili seçiyorsunuz (Türkçe metin üzerinde çalışıyorsanız bu alana dokunmanıza gerek yok) ve en nihayetinde metinleri o dilin büyük-küçük harf durumlarına riayet ederek tek tuşla dönüştürebiliyorsunuz. CultureInfo kütüphanesi on numara çalışıyor C#'da. C#’a hayran olduğum kadar var. Programın tek özelliğine gelecek olursak;

- Farklı dillere göre Büyük-Küçük Harf dönüşümü yapabilme.

{:.tablo-ortali}
| Büyük Küçük Harf Değiştir<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.01-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Büyük Küçük Harf Değiştir (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: a8ef122fbb61d1f13c435ddce994ddf0 | **MD5**: a0137c88d57ef943b8a5c7072cfa2d67 | 
| **Boyut**: 60.4 KB                       | **Boyut**: 450.0 KB                         |
| **Gereksinimler**: .Net Framework 3.5     | **Gereksinimler**: .Net Framework 3.5     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/wzv3ar0ohxattt6/buyuk-kucuk-harf-degistir.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/qofnc9rj7j8ggwe/buyuk-kucuk-harf-degistir-proje.zip?dl=1)                      |