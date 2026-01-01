---
layout: post
title: IPTV Editör
date: 2025-11-27 15:01 +0300
categories: Programlar
tags: IPTV, IP TV, Online Tv, Editor, Kanal, Kanal Düzenleme, Kanal Editör, IpTV Editör
excerpt: Yaklaşık 3 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım programların çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile çoğuna güven olmuyor...
---

![iptv-editor](/images/programlar/iptv-editor.png){: width="55%"}

Yaklaşık 5 yıldır IP TV kullanıyorum ve böyle bir hizmete sahip olmaktan baya memnunum. Bu programı, IP TV'de işime yaramayan bazı kanal ve videoları silmek için kullandığım programların çok yavaş olması yüzünden yazdım. Daha doğrusu yazmak zorunda kaldım. Zaten piyasada da çok fazla IP TV kanal editörü bulunmuyor. Bulunsa bile çoğuna güven olmuyor.

Programın, basit ve kompakt (yalnız kanal adı, grup ve link alanlarına sahip) olması ana hedefim olduğundan, diğer editörlere nazaran çok daha hızlı çalıştığını belirtmek isterim\*. Gereksiz özellikleri kaldırıp sadece kanalları açma, izleme ve silme özelliklerine yer verdim. Ayrıca, yüksek bellek tüketen kanal logo linklerini programda kullanmadım\*\*.

Her şey bir yana, program SOLID'deki **"Open/Closed felsefesi"**ne müsait. Çünkü nesneye yönelik programlama mantığıyla yazdım. Üşenmedim; kavramsal çerçeve oluşturdum, sınıf diyagramları çizdim. Kaynak kodlarını Github'dan görebilir, programın gelişimine katkıda bulunabilirsiniz. Eğer bu olmazsa, mesaj göndererek eklenmesini istediğiniz özellikleri söyleyebilirsiniz. (Ek: Çok mesaj ve istek geldi. Zaman içinde hepsini gerçekleştireceğim. Şüpheniz olmasın)

Her ne kadar IP TV kanallarını ayrıntılı biçimde düzenlemek isteyen gelişmiş kullanıcılara hitap etmese de, ben gibi düz ve sadece işine gelen kanalları IPTV listesinde görmek isteyen kullanıcılar için olduğuna eminim. Gelelim özelliklere;

- M3U uzantısına sahip dosyalardaki IPTV kanal ve videolarını yükleme ve silme\*\*\*,
- İstenen kanalları, ad ve gruba göre arayıp bulma **(Aramanızın başına @ işareti eklerseniz gruplarda arama yapabilirsiniz)**,
- Silme sonrası oluşturulan kanal listesini kaydetme,
- Hi-DPI ekranları destekleme,
- (Eğer sisteminizde yüklüyse) İstenen kanalı VLC Player'la açma,
- (İstek) Görme engelli kullanıcılar için erişilebilirlik seçenekleri,
- (İstek) Gruba göre yapılan arama sonuçlarını kaydetme,
- (İstek) Kanal linkini kopyalama,
- (İstek) Sütunlara göre sıralama işlemi.

**\*** Program _15~ MB boyutlu, 85.000~ adet kanalı 1~ saniyede_ açabiliyor.<br>
**\*\*** IPTV listelerinde yer alan bazı kanal logolarının linkleri satırlarca uzunluğa sahip. Bu da, çok fazla kanallı IP TV listelerinde, başta VLC player olmak üzere pek çok uygulamanın yavaş açılmasına neden oluyor. Bu nedenle logo alanına programda hiçbir şekilde yer vermedim.<br>
**\*\*\*** Kanalları silme işleminde _Threading ve async/await_ kullandım ve çok ciddi bir performans artışı sağlamayı başardım. _80.000'in üstünde kanal 1~ saniye içinde_ silindi :)

{:.tablo-ortali}
| IPTV Editor <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.09-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | IPTV Editor (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) |
|---------------------------------------------|-------------------------------------------|
| **Boyut**: 62 KB | **Boyut**: 437 KB |
| **Gereksinimler**: .Net Framework 4.5 | **Gereksinimler**: .Net Framework 4.5 |
| **Platform**: Microsoft Windows | **Programlama Dili**: C# |
| **İndir**: [Link](https://www.dropbox.com/scl/fi/zcyhmh3101en424tv9bm1/iptv-editor.zip?rlkey=uvm5c3ybpgnbgvoduvoznb6cf&dl=1) | **Proje**: [Link](https://www.dropbox.com/scl/fi/yeesl0918wvm2mi7ons5v/iptv-editor-proje.zip?rlkey=zmki52u7q15u78j7bk4y6qitd&dl=1) <br> **GitHub**: [Link](https://github.com/Umut-D/iptv-editor)|
