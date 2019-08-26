---
layout: post
title: Rastgele (Lorem Ipsum) Yazı Oluşturucu
date: 2018-12-08 12:43 +0300
categories: Programlar
tags: Lorem Ipsum, Rastgele Yazı, Rastgele Yazı Oluşturucu
---
![rastgele-yazi](/images/programlar/rastgele-yazi.png){: width="45%"}

Çoğunlukla bir iş için lazım olduğunda program yazmaya kasan biri olarak bu sefer de rastgele yazı oluşturmak için program yazayım dedim. Kah Photoshop’ta, kah Dreamweaver’da, kah Notepad++’da bazen uzun ve anlamsız metinlere ihtiyaç duyduğumda “buraya yazı gelecek” yazmaktan tiksineli çok olduğundan beri yardımıma hep Lorem Ipsum metinleri (ebnebiler dummy text de diyebiliyor) yetişti. 

Bu türde koftiden yazılar üretmek için çeşitli programlar için çok çeşitli plug-in’ler var. Ancak ben artık kendim pişirip yiyeyim deyince ortaya böyle bir program çıktı. Tabi bu arada Lorem Ipsum'un ne olduğundan bahsetmemek olmaz:

> Lorem Ipsum, masaüstü yayıncılık ve basın yayın sektöründe kullanılan taklit yazı bloğu olarak tanımlanır. Lipsum, oluşturulacak şablon ve taslaklarda içerik yerine geçerek yazı bloğunu doldurmak için kullanılır. Lipsum, 1500’lerin başlarında bir matbaacının font model kitabı oluşturmak için, bir yazı tipi kütüphanesindeki harflerin sıralamasını bozarak yerleştirdiğinden bu yana endüstri standardı haline gelmiştir. (Vikipedi)

Bu basit programı uzun uzadıya anlatmanın alemi yok, programın yegane özelliğine geçelim;

- Maksimum 30 paragraf, (paragraf içinde) 30 cümle, (cümle içinde) 30 kelime ile rastgele Lorem Ipsum metinleri oluşturma.

**Not**: 1.1 versiyonun kaynak kodlarına baktığınızda göreceksiniz ki; program nesneye göre programlanıp, Generic List ve StringBuilder öğeleri kullanınca çok ciddi bir performans artışı sağladı. Örneğin; 6. nesil i7 işlemci bilgisayarımda çalıştırdığımda;

- **versiyon 1.0**'da; 10 paragraf, 10 cümle, 10 kelime ile oluşturulan *6.100~ harf-3.7 saniye*
- **versiyon 1.1**'de; 30 paragraf, 30 cümle, 30 kelime ile oluşturulan *164.000~ harf-0.27 saniye*

{:.tablo-ortali}
| Rastgele (Lorem Ipsum) Yazı Oluşturucu<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.1-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele (Lorem Ipsum) Yazı Oluşturucu (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 269de8ee7e237f75e1fd0bee46fd5431 | **MD5**: 88a3c0f02416a624979c3d6a78b0deae | 
| **Boyut**: 49.8 KB                       | **Boyut**:  339.5 KB                         |
| **Gereksinimler**: .Net Framework 3.5     | **Gereksinimler**: .Net Framework 3.5     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar1/rastgele-yazi-olusturucu.zip)         | **İndir**: [Link](http://www.umutd.com/programlar1/rastgele-yazi-olusturucu-proje.zip)                      |