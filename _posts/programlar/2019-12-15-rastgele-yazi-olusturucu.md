---
layout: post
title: Rastgele (Lorem Ipsum) Yazı Oluşturucu
date: 2019-12-15 01:43 +0300
categories: Programlar
tags: Lorem Ipsum, Rastgele Yazı, Rastgele Yazı Oluşturucu
excerpt: Çoğunlukla bir iş için lazım olduğunda program yazmaya kasan biri olarak bu sefer de rastgele yazı oluşturmak için program yazayım dedim. Kah Photoshop’ta, kah Dreamweaver’da, kah Notepad++’da bazen uzun ve anlamsız metinlere ihtiyaç duyduğumda "buraya yazı gelecek" yazmaktan tiksineli çok olduğundan beri yardımıma hep Lorem Ipsum metinleri (ebnebiler dummy text de diyebiliyor) yetişti. 
redirect_from:
  - /programlar/rastgele-yazi-olusturucu/
  - /etiket/rastgele-yazi-olusturucu/
---
> Lorem Ipsum, masaüstü yayıncılık ve basın yayın sektöründe kullanılan taklit yazı bloğu olarak tanımlanır. Lipsum, oluşturulacak şablon ve taslaklarda içerik yerine geçerek yazı bloğunu doldurmak için kullanılır. Lipsum, 1500’lerin başlarında bir matbaacının font model kitabı oluşturmak için, bir yazı tipi kütüphanesindeki harflerin sıralamasını bozarak yerleştirdiğinden bu yana endüstri standardı haline gelmiştir. (Vikipedi)

![rastgele-yazi](/images/programlar/rastgele-yazi.png){: width="39%"}

Çoğunlukla bir iş için lazım olduğunda program yazmaya kasan biri olarak bu sefer de rastgele yazı oluşturmak için program yazayım dedim. Kah Photoshop’ta, kah Dreamweaver’da, kah Notepad++’da bazen uzun ve anlamsız metinlere ihtiyaç duyduğumda "buraya yazı gelecek" yazmaktan tiksineli çok olduğundan beri yardımıma hep Lorem Ipsum metinleri (ebnebiler dummy text de diyebiliyor) yetişti. 

Bu türde koftiden yazılar üretmek için çeşitli programlar için çok çeşitli plug-in’ler var. Ancak ben artık kendim pişirip yiyeyim deyince ortaya böyle bir program çıktı. Bu basit programı uzun uzadıya anlatmanın alemi yok, programın yegane özelliği; Maksimum 30 paragraf, (paragraf içinde) 30 cümle, (cümle içinde) 30 kelime ile rastgele Lorem Ipsum metinleri oluşturmak. Hepsi bu. Maksat laneydain yazı oluşturmak işte.

**Not**: 1.1 versiyon ve sonrasının kaynak kodlarına baktığınızda göreceksiniz ki; program nesneye göre programlanıp, **Generic List** ve **StringBuilder** öğeleri kullanınca çok ciddi bir performans artışı sağladı. Programı 6. nesil i7 (6700HQ) işlemci bilgisayarımda çalıştırdığımda aşağıdaki sonuçları alıyorum.

- **versiyon 1.0**'da; 10 paragraf, 10 cümle, 10 kelime ile oluşturulan *6.100~ harf-3.7 saniye*
- **versiyon 1.1 ve sonrası**'nda; 30 paragraf, 30 cümle, 30 kelime ile oluşturulan *164.000~ harf-0.27 saniye*

{:.tablo-ortali}
| Rastgele (Lorem Ipsum) Yazı Oluşturucu<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.11-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele (Lorem Ipsum) Yazı Oluşturucu (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: efbb28c2d9d58756721211c8c9fbc79d | **MD5**: 37f0567b6db8662c3387fdcc1ea40d30 | 
| **Boyut**: 50 KB                       | **Boyut**:  423 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir (Dropbox)**: [Link](https://www.dropbox.com/s/c4nclpc6npc2a1s/rastgele-yazi-olusturucu.zip?dl=1) <br> **İndir (OneDrive)**: [Link](https://1drv.ms/u/s!Amxylb8Jtc0Ym1wA8N1AeUW23CAP?e=haIfmZ) | **İndir**: [Link](https://www.dropbox.com/s/ohs0fu3rhindjk3/rastgele-yazi-olusturucu-proje.zip?dl=1) |