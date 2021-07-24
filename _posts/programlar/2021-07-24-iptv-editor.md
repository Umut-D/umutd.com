---
layout: post
title: IPTV Editör
date: 2021-07-24 12:01 +0300
categories: Programlar
tags: IPTV, IP TV, Online Tv, Editor, Kanal, Kanal Düzenleme
excerpt: Yaklaşık 2.5 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım programların çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile çoğuna güven olmuyor...
---
![iptv-editor](/images/programlar/iptv-editor.png){: width="55%"}

Yaklaşık 2.5 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım programların çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile çoğuna güven olmuyor.

Programın, basit ve kompakt (yalnız kanal adı, grup ve link alanları alanlarına sahip) olması ana hedefim olduğundan, diğer editörlere nazaran çok daha hızlı çalıştığını belirtmek isterim*. Gereksiz özellikleri kaldırıp sadece kanalları açma, izleme ve silme özelliklerine yer verdim. Ayrıca, yüksek bellek tüketen kanal logo linklerini programda kullanmadım**. 

Her şey bir yana, program SOLID'deki **"Open/Closed felsefesi"**ne müsait. Çünkü nesneye yönelik programlama mantığıyla yazdım. Üşenmedim; kavramsal çerçeve oluşturdum, sınıf diyagramları çizdim. Kaynak kodlarını Github'dan görebilir. Programın gelişimine katkıda bulunabilirsiniz. Eğer bu olmazsa, mesaj göndererek eklenmesini istediğiniz özellikleri söyleyebilirsiniz.

Her ne kadar IP TV kanallarını ayrıntılı biçimde düzenlemek isteyen gelişmiş kullanıcılara hitap etmese de, ben gibi düz ve sadece işine gelen kanalları IPTV listesinde görmek isteyen kullanıcılar için olduğuna eminim. Gelelim **oldukça performanslı** özelliklere;

- M3U uzantısına sahip dosyalardaki IPTV kanal ve videolarını yükleme ve silme***,
- İstenen kanalları (ad ve gruba göre) arama ve bulma,
- Kanalları kaydetme,
- (Eğer sisteminizde yüklüyse) İstenen kanalı VLC Player'la açma,
- Hi-DPI ekranları destekleme.

**\*** Program *10~ MB boyutlu, 45.000~ adet kanalı 1~ saniyede* açabiliyor.<br>
**\*\*** IPTV listelerinde yer alan bazı kanal logolarının linkleri satırlarca uzunluğa sahip. Bu da, çok fazla kanallı IP TV listelerinde, başta VLC player olmak üzere pek çok uygulamanın yavaş açılmasına neden oluyor. Bu nedenle logo alanına programda hiçbir şekilde yer vermedim.<br>**\*\*\*** Kanalları silme işleminde, yani 3.000 üstünde bir sayıda kanal silerken programda bir yavaşlama ister istemez oluyor. Üstelik sorgulamayı **Linq** kullanarak yapmama rağmen! Programı 6. nesil i7 (6700HQ) işlemci bilgisayarımda çalıştırdığımda *3.000 adet kanalı silmesi 12~ saniye* alıyor. Ancak piyasadaki diğer editörlerde bu sürenin 1 dakikayı bulduğunu veya geçtiğini belirteyim.

{:.tablo-ortali}
| IPTV Editor <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.02-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) |  IPTV Editor (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 10b7f13c8789491b8fa6fd1002d639f7 | **MD5**: 8e689db7e8133f6c84612f4c94924b97 | 
| **Boyut**:  73.8 KB                       | **Boyut**:  53.3 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0 |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C# |
| **İndir**: [Link](https://www.dropbox.com/s/fu5kpcpkpqucwud/iptv-editor.zip?dl=1) | **Proje**: [Link](https://www.dropbox.com/s/l85bdeahf0f73xd/iptv-editor-proje.zip?dl=1) <br> **GitHub**: [Link](https://github.com/Umut-D/iptv-editor)|