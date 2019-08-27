---
layout: post
title: TC Kimlik No
date: 2014-11-29 12:43 +0300
categories: Programlar
tags: Kimlik No, TC Kimlik, TC Kimlik No, TC Kimlik No Algoritması, TC Kimlik Numarası
---
{:.uyari}
Bu program sadece TC Kimlik No algoritmasını C# programlama dilinde uygulanması maksadıyla yazılmıştır. Kullanıcılara doğru TC Kimlik Numaraları sunarken -kaynak kodlarından da görüleceği üzere- kullanıcıdan **herhangi bir bilgi asla sızdırmamaktadır**.

![tc-kimlik-no](/images/programlar/tc-kimlik-no.png){: width="30%"}

> **TC Kimlik Numarası**, Nüfus ve Vatandaşlık İşleri Genel Müdürlüğü’nün uzun yıllardır yürüttüğü Mernis uygulamasının hayata geçmesiyle her vatandaşın nüfus cüzdanında bulunan, 11 haneli numaradır. 

Yukarıdaki şekilde açıklanan Türkiye Cumhuriyeti Kimlik Numarasının algoritması çözüleli ve internette paylaşılalı çok oldu. Gerekli gereksiz her haltı C#’da yazmaya çalışmak isteyen biri olarak TC Kimlik Numarası algoritmasını anladıktan sonra bu işe de balıklama atladım. Kodları adım adım kurgulasam da, kodları biraz uzattığımın farkındayım. Dizileri (özellikle char) kullanarak çözüm üretsem belki daha az satır sürecekti ama geri dönmek istemedim. Eğer adımlara dikkat ederseniz algoritmanın işlenişi ve kontrolünü siz de kolaylıkla anlayacaksınız.

Eğer programın ürettiği numaralara güvenmediyseniz sorun değil. Üretilen TC Kimlik Numaralarının doğrulamasını nette yer alan ilgili pek çok siteden kolayca yapabilirsiniz. Sorun olmayacaktır. Programın özelliklerine gelecek olursak;

- Aynı anda maksimum 50 adet TC Kimlik Numarası oluşturma,
- Oluşturulan TC kimlik numaralarını metin belgesi olarak- kaydetme,
- TC Kimlik Numarası kontrolü.

{:.tablo-ortali}
| TC Kimlik No<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | TC Kimlik No (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Kodlar_Gözden_Gecirilecek-red.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: E99BB4C686A093275C9182DBB8177995 | **MD5**: | 
| **Boyut**: 89.2 KB                       | **Boyut**: 615.1 MB                         |
| **Gereksinimler**: .Net Framework 3.5     | **Gereksinimler**: .Net Framework 3.5     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/tc-kimlik-no.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/tc-kimlik-no-proje.zip)                      |