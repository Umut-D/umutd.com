---
layout: post
title: Son Depremler
date: 2019-11-16 16:20 +0300
categories: Programlar
tags: Deprem, Son Depremler
excerpt: Geçen gün arşivimde, bundan 2 yıl önce yarısına kadar yazdığım, ama ne hikmetse tamamlamayı unuttuğum bu programı buldum. İşlerini pek yarıda bırakmayı sevmeyen biri olarak, "programı neden yarıda bıraktım" demeyi bırakıp işimi tamamlamaya koyuldum...
---
![son-depremler](/images/programlar/son-depremler.png){: width="49%"}

Geçen gün arşivimde, bundan 2 yıl önce yarısına kadar yazdığım, ama ne hikmetse tamamlamayı unuttuğum bu programı buldum. İşlerini pek yarıda bırakmayı sevmeyen biri olarak, "programı neden yarıda bıraktım" demeyi bırakıp işimi tamamlamaya koyuldum. Açıkçası Windows Form'lar ile uğraşmayı hiç sevmiyorum. Buradan kasıt, görsel olarak form oluşturma ve onun tasarımı. Hal böyle olunca kod yazmaktan uzaklaşıp, nefret ettiğim tasarım işine vakit ayırdıkça program yazmak külfet olmaya başlıyor. Halbuki konsol (meşhur siyah-beyaz ekran) ekranı her işi görüyor. Şu programı konsol ekranında yazsam program çok çok daha erken biterdi.

Ülkemiz maalesef bir deprem ülkesi. Deprem yaşandığı zaman da güvenilir yerlerden anında bilgi almak gerek. Bu program ise Türkiye'nin deprem konusunda en yetkili kurumundan; **Boğaziçi Üniversitesi, Kandilli Rasathanesi ve Deprem Araştırma Enstitüsü (KRDAE)** aracılığıyla sağlanan deprem verilerini kullanıcıya sunuyor. Fazla uzatmayıp, geleyim programın lüzumsuz özelliklerine;

- Türkiye'de yaşanan son 20 depremi gösterme ve bunu otomatik olarak (5 dk.) yapma,
- Deprem büyüklüklerine göre renkli gösterim sunma,
- Yeni deprem olduğunda bildirim verme,
- İlgili deprem(ler)e tıklayarak mevcut tarayıcıda depremin olduğu lokasyonu görüntüleme. 

**Not:** Deprem yerini haritada aktif etme ve gösterme özelliğinin Windows Form üzerinde yapmak çok istedim. Fakat **Google** ve **Bing Haritalar**'ın kişie özel API anahtarı istemelerinden dolayı bu özellikten vazgeçtim. API anahtarı paralı bir şey değil biliyorum. Ama bu anahtarın her yerde veya açık kaynak kodlu bir projede paylaşılması da hoş olmazdı diye düşünüyorum. 

{:.tablo-ortali}
| Son Depremler <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.02-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) |  Son Depremler (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Devam_Ediyor-success.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 3072a00b381a473b8d805303390edf2a | **MD5**: 89cd7a7dcb0db92787046e23413e060b | 
| **Boyut**:  234 KB                       | **Boyut**:  2.57 MB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4    |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/ohlch6m0icorxes/son-depremler.zip?dl=1)         | **İndir (Proje)**: [Link](https://www.dropbox.com/s/jjx7d3xfftkkooj/son-depremler-proje.zip?dl=1) <br> **GitHub Sayfası**: [Link](https://github.com/Umut-D/Son-Depremler)                    |