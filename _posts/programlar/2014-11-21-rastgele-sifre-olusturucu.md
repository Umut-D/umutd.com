---
layout: post
title: Rastgele Şifre Oluşturucu
date: 2014-11-21 12:43 +0300
categories: Programlar
tags: Rastgele Şifre Oluşturucu, Şifre, Şifre Oluşturucu, Şifre Üretici, Şifre Üret
---
![rastgele-sifre-olusturucu](/images/programlar/rastgele-sifre-olusturucu.png){: width="30%"}

Windows’un yanı sıra gerek evde gerekse işyerinde Mac OSX Mavericks de kullanan biri olarak Mac OSX’in en sevdiğim özelliklerinden birisi dahili şifre üreticisi. Kullanıcılar ve Gruplar alanından hesabınıza veya diğer hesaplara şifre atamak için kullanabileceğiniz şifre oluşturma özelliği maalesef Windows’a, Mac OSX gibi, dahil gelmemekte. Hal böyle olunca Windows’ta veya internette lazım olur ayağına basit bir şifre oluşturucu yazdım. Ortaya sistemi yormayan basit ama kullanışlı bir şifre oluşturucu çıktı. Hem de Mac OSX’tekine benziyor gibi. Hatta şifre üretiminin içine özel karakterleri de koyacaktım. Fakat her şeyin çorba olacağını düşündüğüm için bundan vazgeçtim. Çünkü tür alanına ekstradan 4 alan eklemek bence hoş olmayacaktı.

Benzer bir işe girişmek isteyenler olursa, yola koyulmadan önce mutlaka Regex (Regular Expressions – Düzenli İfadeler) konusuna göz atmalarını öneririm. Zira Regex sınıfı sayesinde program bir hayli kolaya geldi. Aslında Regex'i biraz daha zorlayıp kodlarda ciddi manada kısaltma yapabilirdim ama yazmış bulundum bir kere. Ona bakılırsa StringBuilder sınıfı da kullanmak da vardı aklımda ama o da yalan oldu. Büyük string işlemleri yapacaksanız mutlaka StringBuilder sınıfı kullanın, performans ciddi manada daha iyi olacaktır. Bu öğüdümü unutmayın sakın.

Programın özelliklerine gelecek olursak;

- Tekli veya farklı türlerde şifre oluşturma,
- En az 8, en fazla 25 karakter uzunluğunda şifre oluşturma.

{:.tablo-ortali}
| Rastgele Şifre Oluşturucu<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele Şifre Oluşturucu (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Kodlar_Gözden_Gecirilecek-red.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **MD5**: E043E4CC702A271723E8A94DD39FC7B8 | **MD5**: E7B35F805B2D907DBDF33164EBDF1027 | 
| **Boyut**: 152.1 KB                       | **Boyut**: 1.0 MB                         |
| **Gereksinimler**: .Net Framework 3.5     | **Gereksinimler**: .Net Framework 3.5     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/rastgele-sifre-olusturucu.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/rastgele-sifre-olusturucu-proje.zip)                      |