---
layout: post
title: IPTV Editör
date: 2021-07-25 12:01 +0300
categories: Programlar
tags: IPTV, IP TV, Online Tv, Editor, Kanal, Kanal Düzenleme, Kanal Editör, IpTV Editör
excerpt: Yaklaşık 2.5 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım programların çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile çoğuna güven olmuyor...
---
![iptv-editor](/images/programlar/iptv-editor.png){: width="55%"}

Yaklaşık 2.5 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım programların çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile çoğuna güven olmuyor.

Programın, basit ve kompakt (yalnız kanal adı, grup ve link alanları alanlarına sahip) olması ana hedefim olduğundan, diğer editörlere nazaran çok daha hızlı çalıştığını belirtmek isterim*. Gereksiz özellikleri kaldırıp sadece kanalları açma, izleme ve silme özelliklerine yer verdim. Ayrıca, yüksek bellek tüketen kanal logo linklerini programda kullanmadım**. 

Her şey bir yana, program SOLID'deki **"Open/Closed felsefesi"**ne müsait. Çünkü nesneye yönelik programlama mantığıyla yazdım. Üşenmedim; kavramsal çerçeve oluşturdum, sınıf diyagramları çizdim. Kaynak kodlarını Github'dan görebilir. Programın gelişimine katkıda bulunabilirsiniz. Eğer bu olmazsa, mesaj göndererek eklenmesini istediğiniz özellikleri söyleyebilirsiniz. (Ek: Çok mesaj ve istek geldi. Zaman içinde hepsini gerçekleştireceğim. Şüpheniz olmasın)

Her ne kadar IP TV kanallarını ayrıntılı biçimde düzenlemek isteyen gelişmiş kullanıcılara hitap etmese de, ben gibi düz ve sadece işine gelen kanalları IPTV listesinde görmek isteyen kullanıcılar için olduğuna eminim. Gelelim özelliklere;

- M3U uzantısına sahip dosyalardaki IPTV kanal ve videolarını yükleme ve silme***,
- İstenen kanalları (ad ve gruba göre) arama ve bulma,
- Silme sonrası oluşturulan kanal listesini kaydetme,
- (Eğer sisteminizde yüklüyse) İstenen kanalı VLC Player'la açma,
- Hi-DPI ekranları destekleme.

**\*** Program *10~ MB boyutlu, 45.000~ adet kanalı 1~ saniyede* açabiliyor.<br>
**\*\*** IPTV listelerinde yer alan bazı kanal logolarının linkleri satırlarca uzunluğa sahip. Bu da, çok fazla kanallı IP TV listelerinde, başta VLC player olmak üzere pek çok uygulamanın yavaş açılmasına neden oluyor. Bu nedenle logo alanına programda hiçbir şekilde yer vermedim.<br>
**\*\*\*** Kanalları silme işleminde, yani 3.000 üstünde bir sayıda kanal silerken programda bir yavaşlama ister istemez oluyor. Silmeyi 6. nesil i7 (6700HQ) işlemci bilgisayarımda yaptığımda *3.000 adet kanalı silmesi 8.5~ saniye* alıyor. Önceki versiyonda bu süre 12~ saniyeydi. Birkaç kod değişikliği performansa %30'luk katkı yaptı. Nitekim piyasadaki diğer editörlerde aynı silme işleminin 1 dakikayı bulduğunu veya geçtiğini ekleyeyim.<br>
**Not:** Çok fazla kanal silerken donmuş gibi duran program için *Threading veya async/await* kullanmadım. Çünkü her iki seçenek de programa ciddi anlamda performans kaybı yaşattı.

{:.tablo-ortali}
| IPTV Editor <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.03-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) |  IPTV Editor (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **MD5**: d7777ec196034b711a9f26f1f4ea1185 | **MD5**: 9cf4bae978effc96290f28f723103631 | 
| **Boyut**:  53.2 KB                       | **Boyut**:  73.8 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0 |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C# |
| **İndir**: [Link](https://www.dropbox.com/s/fu5kpcpkpqucwud/iptv-editor.zip?dl=1) | **Proje**: [Link](https://www.dropbox.com/s/satbnnctycjbo4f/iptv-editor-proje.zip?dl=1) <br> **GitHub**: [Link](https://github.com/Umut-D/iptv-editor)|