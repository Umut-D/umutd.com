---
layout: post
title: IPTV Editör
date: 2021-01-03 12:01 +0300
categories: Programlar
tags: IPTV, IP TV, Online Tv, Editor, Kanal, Kanal Düzenleme
excerpt: Yaklaşık 2.5 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım birkaç programın çok ama çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile hiçbirine güven olmuyor...
---
![iptv-editor](/images/programlar/iptv-editor.png){: width="55%"}

Yaklaşık 2.5 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım birkaç programın çok ama çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile hiçbirine güven olmuyor.

Programın, basit ve kompakt (yalnız kanal adı, grup ve link alanları alanlarına sahip) olması ana hedefim olduğundan, diğer editörlere nazaran çok daha hızlı çalıştığını belirtmek isterim*. Gereksiz özellikleri kaldırıp sadece kanalları açma, izleme ve silme özelliklerine yer verdim. Ayrıca, gereksiz yere yüksek bellek tüketen kanal logo linklerini programda kullanmadım**. 

Her şey bir yana, program SOLID'deki "Open/Closed felsefesi"ne müsait. Yani kod eklemeleriyle, mevcut yapı korunarak geliştirmeye müsait. Çünkü nesneye yönelik programlama mantığıyla yazdım. Üşenmedim; kavramsal çerçeve oluşturdum, sınıf diyagramları oluşturdum. Github'da kaynak kodlarını görebilir ve programın gelişimine katkıda bulunabilirsiniz. Bu olmazsa, mesaj göndererek eklenmesini istediğiniz özellikleri söyleyebilirsiniz.

Her ne kadar IP TV kanallarını ayrıntılı biçimde düzenlemek isteyen gelişmiş kullanıcılara hitap etmese de, ben gibi düz ve sadece işine gelen kanalları IPTV listesinde görmek isteyen kullanıcılar için olduğuna eminim. Geleyim programın lüzumsuz ve **oldukça performanslı** özelliklerine;

- M3U uzantısına sahip dosyalardaki IPTV kanal ve videolarını yükleme ve silme***,
- İstenen kanalları (ad ve gruba göre) arama ve bulma,
- Kanalları kaydetme,
- (Eğer sisteminizde yüklüyse) İstenen kanalı VLC Player'la açma,
- Hi-DPI ekranları destekleme.

**Not 1:** Program *10~ MB boyutlu, 45.000~ adet kanal/videoyu 1 saniyeden daha az sürede* açabiliyor.<br>
**Not 2:** IPTV listelerinde yer alan bazı kanal logolarının linkleri satırlarca uzunluğa sahip. Bu ise, çok fazla kanala sahip olan IP TV listelerinde, başta VLC player olmak üzere pek çok uygulamanın çok yavaş açılmasına neden olmakta. Bu nedenle logo alanına programda hiçbir şekilde yer vermedim.<br>**Not 3:** Kanalları silme işleminde, yani 3000 üstünde bir sayıda kanal seçilip silmek istendiğinde programda bir yavaşlama ister istemez oluyor. Üstelik sorgulamayı **Linq** kullanarak yapmama rağmen! Programı 6. nesil i7 (6700HQ) işlemci bilgisayarımda çalıştırdığımda *tam 3.000 adet kanalı silinmesi 12~ saniye* alıyor. Ancak piyasadaki diğer editörlerde bu sürenin 1 dakikayı bulduğunu veya geçtiğini belirteyim.

{:.tablo-ortali}
| IPTV Editor <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) |  IPTV Editor (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 1d422983e3fe80784c5188858928ca16 | **MD5**: 2482780a3126181b7e9aade706ac048e | 
| **Boyut**:  167 KB                       | **Boyut**:  2.78 MB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0 |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C# |
| **İndir**: [Link](https://www.dropbox.com/s/gyuteqtx81jq2s9/son-depremler.zip?dl=1) | **Proje**: [Link](https://www.dropbox.com/s/4cmijvnrdbmpqv4/son-depremler-proje.zip?dl=1) <br> **GitHub**: [Link](https://github.com/Umut-D/iptv-editor)|