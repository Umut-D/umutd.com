---
layout: post
title: Rastgele Şifre Oluştur
date: 2021-01-14 12:43 +0300
categories: Programlar
tags: Rastgele Şifre Oluşturucu, Şifre, Şifre Oluşturucu, Şifre Üretici, Şifre Üret
excerpt: Windows'un yanı sıra bazen Mac OS kullanan biri olarak Mac OS'un en sevdiğim özelliklerinden birisi dahili şifre üreticisi. Kullanıcılar ve Gruplar alanından hesabınıza veya diğer hesaplara şifre atamak için kullanabileceğiniz şifre oluşturma özelliği maalesef Windows'a dahil gelmiyor...
redirect_from:
  - /programlar/rastgele-sifre-olusturucu/
  - /etiket/rastgele-sifre-olusturucu/
---
![rastgele-sifre-olusturucu](/images/programlar/rastgele-sifre-olusturucu.png){: width="40%"}

Windows'un yanı sıra bazen Mac OS kullanan biri olarak Mac OS'un en sevdiğim özelliklerinden birisi dahili şifre üreticisi. Kullanıcılar ve Gruplar alanından hesabınıza veya diğer hesaplara şifre atamak için kullanabileceğiniz şifre oluşturma özelliği maalesef Windows'a dahil gelmiyor. Hal böyle olunca Windows'ta veya internette lazım olur ayağına basit bir şifre oluşturucu yazdım. Ortaya basit ve kullanışlı bir şifre oluşturucu çıktı. Üretim doğru yapılıyor mu diye Unit Test yazınca işler ve kod kontrolü daha kolaya geldi. Programın özelliklerine gelecek olursak;

- Tekil veya farklı türlerde (Küçük Harf, Büyük Harf, Rakam, Sembol) sorunsuz şifre oluşturma,
- En az 4, en fazla 48 karakter uzunluğunda şifre oluşturma,
- 7 adet **Unit Test** (Proje boyutu 17MB'ye çıktığından Packages'ları eklemedim).

{:.tablo-ortali}
| Rastgele Şifre Oluşturucu<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.1-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele Şifre Oluşturucu (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 5a824c2eef1ec16a15dc45c18753a88f | **MD5**: a67967770584e4a3a0420e455e333beb | 
| **Boyut**: 97.3 KB                       | **Boyut**: 476 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/qxeimezf1ftozuq/rastgele-sifre-olustur.zip?dl=1) | **İndir**: [Link](https://www.dropbox.com/s/f20ihjxoh39h61n/rastgele-sifre-olustur-proje.zip?dl=1) |

**Ek** : Hash kodlarının nasıl hesaplandığını görmeye gelenler için **Karakter.cs** ve **Sifre.cs** sınıflarındaki kodlar:

```csharp
namespace Rastgele_Sifre_Olustur
{
    public class Karakter
    {
        public string BuyukHarfler => "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        public string KucukHarfler => BuyukHarfler.ToLowerInvariant();
        public string Rakamlar => "0123456789";
        public string Semboller => "!@#&()-+[{}]:;'.,?/*~$^=<>";
    }
}
```
<div id="ara"></div>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace Rastgele_Sifre_Olustur
{
    public class Sifre
    {
        public int Uzunluk { get; set; }
        public Random SayiUret { get; }
        public StringBuilder Sonuc { get; }

        public Sifre(int uzunluk)
        {
            Uzunluk = uzunluk;
            SayiUret = new Random();
            Sonuc = new StringBuilder();
        }

        // Kaç adet tür seçildiyse (Örn. Küçük ve Büyük Harfler) o karakter türüne göre işlem yap
        public void Olustur(int seciliKutuSayisi, List<string> karakterTuru)
        {
            for (int i = seciliKutuSayisi - 1; i >= 0; i--)
            {
                int sayi = SayiUret.Next(1, Uzunluk - i);
                Uzunluk -= sayi;
                Uret(sayi, karakterTuru.ElementAt(i));

                if (i == 0)
                {
                    Uret(Uzunluk, karakterTuru.ElementAt(i));
                    Karistir();
                    break;
                }
            }
        }

        private void Uret(int adet, string tur)
        {
            for (int i = 0; i < adet; i++)
            {
                int sayi = SayiUret.Next(0, tur.Length);
                Sonuc.Append(tur[sayi]);
            }
        }

        private void Karistir()
        {
            char[] sifre = Sonuc.ToString().ToCharArray().OrderBy(x => Guid.NewGuid()).ToArray();
            string sifreyiKaristir = new string(sifre);

            Sonuc.Clear().Append(sifreyiKaristir);
        }
    }
}
```