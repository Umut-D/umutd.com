---
layout: post
title: Hisse Senetlerim
date: 2023-11-12 03:43 +0300
categories: Programlar
tags: Borsa, Hisse Senetleri, Hisse, BIST, Menkul Kıymet, Canli Borsa
excerpt: En sürüncemede kalan programım. Tatildir, iştir, lüzumsuz şeylerdir araya girince neredeyse 2.5 ayda yazabildim. Sahi niye böyle oldu. Yazdım, kodları unuttum. Yazdım, programı yazdığımı unuttum. Yazdım, "hemen her bir şey nesneye yönelik programlamaya yönelik olsun" diyerek uzattıkça uzattım. Ve yazdım, Unit Test de ekleyeyim dedim...
---

![hisse-senetlerim](/images/programlar/hisse-senetlerim.png){: width="65%"}

En sürüncemede kalan programım. Tatildir, iştir, lüzumsuz şeylerdir araya girince neredeyse 2.5 ayda yazabildim. Sahi niye böyle oldu. Yazdım, kodları unuttum. Yazdım, programı yazdığımı unuttum. Yazdım, "hemen her bir şey nesneye yönelik programlamaya yönelik olsun" diyerek uzattıkça uzattım. Ve yazdım, Unit Test de ekleyeyim dedim.

Program, telefonda uygulamasını kullandığım (gerçi stop-loss özelliği olmadığı için artık kullanmıyorum) Midas'ın web sitesinden borsa verilerini çekiyor. Var olan hisse senetlerinin kar/zarar durumlarını gösteriyor. Çok karmaşık değil. Lakin C#'da bazı şeyler için ek kod yazarken canım sıkılmadı değil. Python'un gevşekliğini ve kütüphanelerindeki kullanım rahatlığını aramadım desem yalan olmaz. Geleyim programın gereksiz özelliklerine;

- Canlı Borsa verilerini çekme,
- Hisse senetlerinin XML veya TXT kaydını tutma,
- O anki borsa verilerine göre kar/zarar hesabı yaparak kullanıcıyı bilgilendirme.

{:.tablo-ortali}
| Hisse Senetlerim <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Hisse Senetlerim (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **Boyut**: 755 KB | **Boyut**: 4.58 MB |
| **Gereksinimler**: .Net Core 6 | **Gereksinimler**: .Net Core 6 |
| **Platform**: Microsoft Windows | **Programlama Dili**: C# |
| **İndir**: [Link](https://www.dropbox.com/scl/fi/q1s1vnhy33n4tsz748fo4/hisse-senetlerim.zip?rlkey=0706vacy48t1p14ta2oa1ou2f&dl=1) | **İndir**: [Link](https://www.dropbox.com/scl/fi/iol097mg2jmz4pr7yw8cq/hisse-senetlerim-proje.zip?rlkey=vcavr4cnlwokuepqigjbjtqey&dl=1) <br> **GitHub**: [Link](https://github.com/Umut-D/HisseSenetlerim) |
