---
layout: post
title: Çoklu Karekod (QR Kodu) Oluştur
date: 2020-10-18 11:29 +0300
categories: Programlar
tags: Karekod, QR, QR Kodu, Çoklu Karekod, Toplu Karekod
excerpt: Rica üzerine, acele yazdığım bir program daha. Birkaç gün önce bir hoca arkadaşım, bir ilkokuldaki öğrencilerin okula kendine has karekodlarıyla girebilmeleri için, tek seferde çoklu karekod üreten bir sistem olup olmadığını sordu. Bunu yapan bir program bulmuştu. Fakat ücretli olduğu için amacına ulaşamadığını belirtti...
---
![coklu-karekod-olustur](/images/programlar/coklu-karekod-olustur.png){: width="35%"}

Rica üzerine, acele yazdığım bir program daha. Birkaç gün önce bir hoca arkadaşım, bir ilkokuldaki öğrencilerin okula kendine has karekodlarıyla girebilmeleri için, tek seferde çoklu karekod üreten bir sistem olup olmadığını sordu. Bunu yapan bir program bulmuştu. Fakat ücretli olduğu için amacına ulaşamadığını belirtti. Bir zamanlar yine bu sitede QR kodu oluşturma programı (1 yıl sonra kodları beğenmeyip silmiştim) yazan biri olarak bunun zor olmadığını, biraz beklerse yazabileceğimi belirttim. İşte o görüşmenin ardından bu program çıktı.

Programın **Veri(ler)** alanındaki her satıra, Karekoda (QR Koduna) eklenmesi istenen bilgiler eklenince ve istenen ayarlar yapılınca işlem tamamlanıyor. Programın lüzumsuz özellikleri ise;

- İstenen kalite (4 farklı tür), ayraç (7 farklı tür) ve boyutta (maksimum 2500px) QR kodu üretebilme,
- Tek seferde istenildiği kadar karekod oluşturabilme. 

**Not:** Karekodların geçerli olup olmadığını [ZXing Decoder Online](https://zxing.org/w/decode.jspx) sitesinden kontrol edebilirsiniz.

{:.tablo-ortali}
| Çoklu Karekodu (QR Kodu) Oluştur <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Çoklu Karekodu (QR Kodu) Oluştur (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|---------------------------------------------|-------------------------------------------|
| **Boyut**:  5.27 MB                       | **Boyut**:  5.61 MB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0 |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C# |
| **İndir**: [Link](https://www.dropbox.com/s/4hrrc43yfehvr16/coklu-karekod-olustur.zip?dl=1) | **Proje**: [Link](https://www.dropbox.com/s/1c81rrxalkceaxp/coklu-karekod-olustur-proje.zip?dl=1)|