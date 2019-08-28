---
layout: post
title: Site IP Sorgula
date: 2018-12-11 12:43 +0300
categories: Programlar
tags: DNS, IP, Redirect, Site IP, Sorgu, Spam, Spam Referrer, Yönlendirme
---
![site-ip-sorgula](/images/programlar/site-ip-sorgula.png){: width="72%"}

Herkes gibi UmutD.com da spam botlardan muzdarip oluyor kimi zaman. Her siteye dadanan ve web’deki hemen hemen tüm sitelerin azraili olan spam botlar gereksiz yere site trafiginden yedikleri gibi, sitenin çok fazla robot ile taraması sonucu hemen çıkma oranında (bounce rate) artışa ve google’ın sitenizi sevmemeye başlamasına (hit arttırmak için bu trafiğe sizin sebep olduğunuza inanmaya başlayor) sebep olmakta. Aslında bu botlar sitenizin istatistiklerini ciddi manada yükseltse de, Google vb. arama motorları bu durum devam ederse sizi cezalandırıyor ve aramalarda “kimi zaman” aşağıya düşmeye başlıyorsunuz.

Ben de bu botlarla elimden geldiğince; gerek Google Analytics‘teki filtreleme özelliğini, gerek Semalt Redirect Manager eklentisini (Semalt trafiğinin sitenize gelmesini engelleyip Google’a yönlendirme yapıyor) kullanarak botlarla ciddi anlamda mücadele etmeyi başardım. Artık site trafiğimde büyük dalgalanmalar olmuyor ve siteme çoğunlukla insanların girdiğini anlayabiliyorum.

Fakat son zamanlarda Semalt Redirect Manager yetersiz gelmeye başladı (Evet, Google Analytics’in filtre özelliğini kullanmaktan çok daha kolay ve çoğunlukla üşeniyorum). Sanırım program güncellenme almadığı için engellendiğim bazı botların tekrardan siteme kaçak yollarla giriş yaptığını fark ettim. Bu noktada çözüm olarak WordPress’te kullandığım iThemes Security güvenlik eklentisi ile IP bazlı engelleme yapmaya karar verdim. Tek sorun; elimde spam sitelerin web adresleri/DNS’leri olmasına rağmen (Örn.: 100dollars-seo.com) bu sitelerin IP adresleri olmamasıydı. İşte ben de tüm bu sitelerin IP adreslerini tek seferde bulabilmek için işte bu programı yazdım. Hatta yazmakla yetinmedim, Tekil olarak girilen sitenin çeşitli bilgilerini sunan bir seçeneği de programıma ekledim. Valla tasarımı bir kenara koyarsak, program gayet güzel oldu. Basit özelliklere gelecek olursak;

- Adresi girilen web sitesine dair çeşitli bilgiler sunma (Web ve Excel'den),
- Birden fazla web sitesinin adresini, ip adresine dönüştürme.

{:.tablo-ortali}
| Site IP Sorgula<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.01-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Site IP Sorgula (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: a5f299059841f5d77c79587c9d3a4647 | **MD5**: a28ab4cf1f6889c5defa087d6160eef7 | 
| **Boyut**:  3.4 MB                       | **Boyut**: 3.6 MB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/site-ip-sorgula.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/site-ip-sorgula-proje.zip)                      |