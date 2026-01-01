---
layout: post
title: Dosya Hash Değeri Hesaplayıcı
date: 2023-04-04 11:43 +0300
categories: Programlar
tags: Hash Değeri, MD5, Sha-1, Kontrol Kodu, Hash Hesapla
excerpt: Bundan yaklaşık bir hafta önce (programı ilk yazdığım 2017 yılında), programlarımdan birine dair eleştiri geldi. Eleştiriyi yapan kişi temel olarak programın virüs ve casus program barındırdığını söylemekte, kendince çeşitli nedenler sıralamaktaydı. Kendisine verdiğim cevaplarda programın kaynak kodlarına göz gezdirmesini ve VirusTotal sonuçlarına bakmasını istedim...
redirect_from:
  - /programlar/dosya-hash-degeri-hesaplayici/
  - /etiket/crc32/
  - /etiket/md5/
  - /etiket/sha1/
---

![dosya-hash-hesaplayici](/images/programlar/dosya-hash-hesaplayici.png){: width="44%"}

Bundan yaklaşık bir hafta önce (programı ilk yazdığım 2017 yılında), programlarımdan birine dair eleştiri geldi. Eleştiriyi yapan kişi temel olarak programın virüs ve casus program barındırdığını söylemekte, kendince çeşitli nedenler sıralamaktaydı. Kendisine verdiğim cevaplarda programın kaynak kodlarına göz gezdirmesini ve VirusTotal sonuçlarına bakmasını istedim. Çünkü kaynak kodları apaçık ortadayken, VirusTotal sonuçlarına göre 57 ayrı virüs tarama servisinde yapılan taramaya göre de programda herhangi bir anormallik olmadığı gözükmekteydi. Nitekim VirusTotal’in virus/casus/zararlı yazılım tespit ekranında 0 / 57 yazmaktaydı.

Bundan sonra o kişiden ses çıkmadı. Fakat bu kişi ile mesajlaşarak girdiğim diyalog bana iki konuda fikir verdi. Bunlardan ilki, siteme yüklediğim tüm program ve projelere MD5 değerleri ile bunları VirusTotal testlerinden sorunsuz geçtiğine dair sonuç sayfası linkini eklemek; ikincisi ise, internetten indirdiğiniz ve karşı tarafta SHA-1 ve MD5 hash değerleri verilen program/dosya/fotoğraf vs.’nin hash değerlerini bilgisayarınızda kontrol ederek indirdiğiniz yer ile aynı hash değerlerine sahip olup olmadığını kontrol etmek için işlevsel bir programdı. İşte bu programın yazılma sebebi bu oldu. Ayrıca, siteye eklediğim tüm dosyaların MD5 değeri ve VirusTotal sonuçlarını siteme geçtim.

Peki Hash nedir, yenilir mi içilir mi, gaz yapar mı? Technopat forumlarında **Recep Baltaş**'ın (ki çok iyi ve bilgili biridir) belirttiği üzere;

> MD5 veya SHA1 olarak sıklıkla gördüğümüz hash değeri, dosyaların parmak izi gibidir. Dosyalar, MD5 ve SHA gibi karmaşık algoritmalarla taranır ve dosyanın benzersiz bir parmak izi, yığını çıkartılır. İşte bu parmak izi aşağıdaki gibi bir şeydir: <br><br> **SHA-1 Karma Değeri**: 748AEF5EA5DC09144560F1F41649418955A83740 <br><br> Örneğin bu kod, **64 Bit Windows 10 teknik önizleme sürümünün (Windows 10 Build 9926)** ISO dosyasının SHA-1 hash değeri, yani bir nevi parmak izidir. ISO dosyasını indirdikten sonra hash kontrolü yapılır. Eğer kontrol sonunda birebir yukarıdaki değerler çıkıyorsa, indirdiğiniz dosyada herhangi bir bozukluk ya da değişiklik yok demektir. Dosyada en ufak bir değişiklik olsa dahi bu değer değişecektir.

Burada bazı faydalar dikkatinizi çekecektir:

- Hash sayesinde dosyaların düzgün indirilip indirilmediği öğrenilebilirsiniz.
- Hash sayesinde dosyalarda değişiklik yapılıp yapılmadığı öğrenilebilirsiniz.

Girizgah fazla uzadı nedense. Çok mu dolmuşum ne?!?! Özet geçeyim; bu programla dosyaların MD5 ve SHA-1 değerlerini görebilir ve bunları indirdiğiniz sitedeki hash değerleri ile karşılaştırabilirsiniz. Değerler karşı taraf ile bire bir uyuyorsa dosyada hiçbir sorun yoktur ve dosyaya dokunulmamıştır. Fakat değerler aynı değilse o dosyadan hayır yoktur. Dosya başkaları veya 3. şahıslarca değiştirilmiştir. Mümkünse dosyaya temkinli yaklaşın. Hatta dosyayı VirusTotal'e yükleyerek tarama yapın. Programın özelliklerine gelecek olursak;

- Dosyaları ilgili alanın üzerine sürükleyerek bırakarak açma,
- MD5 değerini bulma,
- SHA-1 değerini bulma,
- Dosya hash eşleştirmesi yapabilme.

{:.tablo-ortali}
| Dosya Hash Değeri Hesaplayıcı <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.14-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Dosya Hash Değeri Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|---------------------------------------------|-------------------------------------------|
| **Boyut**: 143 KB | **Boyut**: 629 KB |
| **Gereksinimler**: .Net Framework 4.8 | **Gereksinimler**: .Net Framework 4.8 |
| **Platform**: Microsoft Windows | **Programlama Dili**: C# |
| **İndir**: [Link](https://www.dropbox.com/s/qm72jn7xtsd2hxw/dosya-hash-degeri-hesaplayici.zip?dl=1) | **İndir**: [Link](https://www.dropbox.com/s/ycsfp8q8ad20ind/dosya-hash-degeri-hesaplayici-proje.zip?dl=1) <br> **GitHub**: [Link](https://github.com/Umut-D/Dosya-Hash-Hesaplayici) |
