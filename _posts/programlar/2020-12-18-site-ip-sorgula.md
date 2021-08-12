---
layout: post
title: Site IP Sorgula
date: 2020-12-18 12:43 +0300
categories: Programlar
tags: DNS, IP, Redirect, Site IP, Sorgu, Spam, Spam Referrer, Yönlendirme
excerpt: Herkes gibi Umutd.com da spam botlardan muzdarip oluyor kimi zaman. Her siteye dadanan ve web’deki hemen hemen tüm sitelerin azraili olan spam botlar gereksiz yere site trafiginden yedikleri gibi, sitenin çok fazla robot ile taraması sonucu hemen çıkma oranında (bounce rate) artışa ve google’ın sitenizi sevmemeye başlamasına (hit arttırmak için bu trafiğe sizin sebep olduğunuza inanmaya başlayor) sebep olmaktaydı...
redirect_from:
  - /programlar/site-ip-sorgula/
  - /etiket/site-ip/
---
![site-ip-sorgula](/images/programlar/site-ip-sorgula.png){: width="72%"}

Herkes gibi Umutd.com da spam botlardan muzdarip oluyor kimi zaman. Her siteye dadanan ve web’deki hemen hemen tüm sitelerin azraili olan spam botlar gereksiz yere site trafiginden yedikleri gibi, sitenin çok fazla robot ile taraması sonucu hemen çıkma oranında (bounce rate) artışa ve google’ın sitenizi sevmemeye başlamasına (hit arttırmak için bu trafiğe sizin sebep olduğunuza inanmaya başlayor) sebep olmaktaydı. Aslında bu botlar sitenizin istatistiklerini ciddi manada yükseltse de, Google vb. arama motorları bu durum devam ederse sizi cezalandırıyor ve aramalarda “kimi zaman” aşağıya düşmeye başlıyorsunuz.

Ben de bu botlarla elimden geldiğince; gerek Google Analytics‘teki filtreleme özelliğini, gerek Semalt Redirect Manager eklentisini (Semalt trafiğinin sitenize gelmesini engelleyip Google’a yönlendirme yapıyor) kullanarak botlarla ciddi anlamda mücadele etmeyi başardım. Artık site trafiğimde büyük dalgalanmalar olmuyor ve siteme çoğunlukla insanların girdiğini anlayabiliyorum.

Fakat son zamanlarda Semalt Redirect Manager yetersiz gelmeye başladı (Evet, Google Analytics’in filtre özelliğini kullanmaktan çok daha kolay ve çoğunlukla üşeniyorum). Sanırım program güncellenme almadığı için engellendiğim bazı botların tekrardan siteme kaçak yollarla giriş yaptığını fark ettim. Bu noktada çözüm olarak WordPress’te kullandığım iThemes Security güvenlik eklentisi ile IP bazlı engelleme yapmaya karar verdim. Tek sorun; elimde spam sitelerin web adresleri/DNS’leri olmasına rağmen (Örn.: 100dollars-seo.com) bu sitelerin IP adresleri olmamasıydı. İşte ben de tüm bu sitelerin IP adreslerini tek seferde bulabilmek için işte bu programı yazdım. Hatta yazmakla yetinmedim, Tekil olarak girilen sitenin çeşitli bilgilerini sunan bir seçeneği de programıma ekledim. Valla tasarımı bir kenara koyarsak, program gayet güzel oldu. Basit özelliklere gelecek olursak;

- Adresi girilen web sitesine dair çeşitli bilgiler sunma,
- Birden fazla web sitesinin adresini, ip adresine dönüştürme.

{:.tablo-ortali}
| Site IP Sorgula<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.2-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Site IP Sorgula (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **Boyut**:  30,7 KB                       | **Boyut**: 221 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/ntvmr82cj5vzafx/site-ip-sorgula.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/ku9fktbd1o63ysb/site-ip-sorgula-proje.zip?dl=1) |