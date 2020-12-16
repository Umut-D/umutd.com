---
layout: post
title: Dosya Hash Değeri Hesaplayıcı
date: 2020-12-13 16:43 +0300
categories: Programlar
tags: Hash Değeri, Sha-1, MD5, Kontrol Kodu
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

Girizgah fazla uzadı nedense. Çok mu dolmuşum ne?!?! Özet geçeyim: Bu program ile indirdiğiniz dosyaların çeşitli (MD5 ve SHA-1) hash değerlerini görebilir ve indirdiğiniz sitedeki hash değerleri ile karşılaştırabilirsiniz. Değerler karşı taraf ile bire bir uyuyorsa dosyada hiçbir sorun yoktur ve dosyaya dokunulmamıştır. Fakat değilse o dosyadan hayır yoktur, başkaları ya da 3. sahışlar tarafından değiştirilmiştir. Mümkünse dosyaya temkinli yaklaşın. Hatta dosyasınızı VirusTotal’e yükleyerek tarama yapmanıza salık veririm. Eğer İşinize gelmezse de silin gitsin. Programın özelliklerine gelecek olursak;

* Dosyaları ilgili alanın üzerine sürükleyerek bırakarak açma,
* MD5 değerini bulma,
* SHA-1 değerini bulma,
* Dosya hash eşleştirmesi yapabilme.

{:.tablo-ortali}
| Dosya Hash Değeri Hesaplayıcı <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.1-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Dosya Hash Değeri Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 108deaee52db879160493371e44cb465 | **MD5**: 015b36ee9b9e08537674338cf6483cf1 | 
| **Boyut**: 139 KB                       | **Boyut**: 829 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/qm72jn7xtsd2hxw/dosya-hash-degeri-hesaplayici.zip?dl=1) | **İndir**: [Link](https://www.dropbox.com/s/ycsfp8q8ad20ind/dosya-hash-degeri-hesaplayici-proje.zip?dl=1)  |

**Ek** : Hash kodlarının nasıl hesaplandığını görmeye gelenler için **Hash.cs**, **Sha1.cs** ve **Md5.cs** sınıflarındaki kodlar:

```csharp
using System.IO;

namespace HashHesaplayici.Islem
{
    public abstract class Hash
    {
        protected Stream DosyaOku { get; set; }
        protected byte[] HashHesapla { get; set; }
        private string _sonuc;

        public string Sonuc
        {
            get => _sonuc.Replace("-", "");
            protected set => _sonuc = value;
        }

        protected Hash(string dosyaAdi)
        {
            DosyaOku = new FileStream(dosyaAdi, FileMode.Open, FileAccess.Read);
        }

        protected abstract void Hesapla();
    }
}
```
<div id="ara"></div>

```csharp
using System;
using System.Security.Cryptography;

namespace HashHesaplayici.Islem
{
    public sealed class Sha1 : Hash
    {
        private readonly SHA1 _sha1;

        public Sha1(string dosyaAdi) : base(dosyaAdi)
        {
            _sha1 = SHA1.Create();

            Hesapla();
        }

        protected override void Hesapla()
        {
            HashHesapla = _sha1.ComputeHash(DosyaOku);
            Sonuc = BitConverter.ToString(HashHesapla);
        }
    }
}
```
<div id="ara"></div>

```csharp
using System;
using System.Security.Cryptography;

namespace HashHesaplayici.Islem
{
    public sealed class Md5 : Hash
    {
        private readonly MD5 _md5;

        public Md5(string dosyaAdi) : base(dosyaAdi)
        {
            _md5 = MD5.Create();

            Hesapla();
        }

        protected override void Hesapla()
        {
            HashHesapla = _md5.ComputeHash(DosyaOku);
            Sonuc = BitConverter.ToString(HashHesapla);
        }
    }
}
```