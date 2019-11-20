---
layout: post
title: Dosya Hash Değeri Hesaplayıcı
date: 2019-11-20 16:43 +0300
categories: Programlar
tags: Hash Değeri, Sha-1, MD5, CRC32, Kontrol Kodu
excerpt: Bundan yaklaşık bir hafta önce (programı ilk yazdığım 2017 yılında), programlarımdan birine dair eleştiri geldi. Eleştiriyi yapan kişi temel olarak programın virüs ve casus program barındırdığını söylemekte, kendince çeşitli nedenler sıralamaktaydı. Kendisine verdiğim cevaplarda programın kaynak kodlarına göz gezdirmesini ve VirusTotal sonuçlarına bakmasını istedim...
redirect_from:
  - /programlar/dosya-hash-degeri-hesaplayici/
  - /etiket/crc32/
  - /etiket/md5/
  - /etiket/sha1/
---
![dosya-hash-hesaplayici](/images/programlar/dosya-hash-hesaplayici.png){: width="46%"}

Bundan yaklaşık bir hafta önce (programı ilk yazdığım 2017 yılında), programlarımdan birine dair eleştiri geldi. Eleştiriyi yapan kişi temel olarak programın virüs ve casus program barındırdığını söylemekte, kendince çeşitli nedenler sıralamaktaydı. Kendisine verdiğim cevaplarda programın kaynak kodlarına göz gezdirmesini ve VirusTotal sonuçlarına bakmasını istedim. Çünkü kaynak kodları apaçık ortadayken, VirusTotal sonuçlarına göre 57 ayrı virüs tarama servisinde yapılan taramaya göre de programda herhangi bir anormallik olmadığı gözükmekteydi. Nitekim VirusTotal’in virus/casus/zararlı yazılım tespit ekranında 0 / 57 yazmaktaydı.

Bundan sonra o kişiden ses çıkmadı. Fakat bu kişi ile mesajlaşarak girdiğim diyalog bana iki konuda fikir verdi. Bunlardan ilki, siteme yüklediğim tüm program ve projelere MD5 değerleri ile bunları VirusTotal testlerinden sorunsuz geçtiğine dair sonuç sayfası linkini eklemek; ikincisi ise, internetten indirdiğiniz ve karşı tarafta MD5/SHA-1/CRC32 hash değerleri verilen program/dosya/fotoğraf vs.’nin hash değerlerini bilgisayarınızda kontrol ederek indirdiğiniz yer ile aynı hash değerlerine sahip olup olmadığını kontrol etmek için işlevsel bir programdı. İşte bu programın yazılma sebebi bu oldu. Ayrıca, siteye eklediğim tüm dosyaların MD5 değeri ve VirusTotal sonuçlarını siteme geçtim.

Peki Hash nedir, CRC32 yenilir mi içilir mi, gaz yapar mı? Technopat forumlarında **Recep Baltaş**'ın (ki çok iyi ve bilgili biridir) belirttiği üzere;

> MD5 veya SHA1 olarak sıklıkla gördüğümüz hash değeri, dosyaların parmak izi gibidir. Dosyalar, MD5 ve SHA gibi karmaşık algoritmalarla taranır ve dosyanın benzersiz bir parmak izi, yığını çıkartılır. İşte bu parmak izi aşağıdaki gibi bir şeydir: <br><br> **SHA-1 Karma Değeri**: 748AEF5EA5DC09144560F1F41649418955A83740 <br><br> Örneğin bu kod, **64 Bit Windows 10 teknik önizleme sürümünün (Windows 10 Build 9926)** ISO dosyasının SHA-1 hash değeri, yani bir nevi parmak izidir. ISO dosyasını indirdikten sonra hash kontrolü yapılır. Eğer kontrol sonunda birebir yukarıdaki değerler çıkıyorsa, indirdiğiniz dosyada herhangi bir bozukluk ya da değişiklik yok demektir. Dosyada en ufak bir değişiklik olsa dahi bu değer değişecektir.

Burada bazı faydalar dikkatinizi çekecektir:
- Hash sayesinde dosyaların düzgün indirilip indirilmediği öğrenilebilirsiniz.
- Hash sayesinde dosyalarda değişiklik yapılıp yapılmadığı öğrenilebilirsiniz.

> Vikipedi'ya göre **CRC32**; Döngüsel artıklık denetimi (CRC: Cyclic Redundancy Check), çoğunlukla sayısal şebekelerde ve depolama cihazlarında kullanılan ve ham veride yapılan hatalı değişimleri algılayan, uygulaması kolay ve güvenliği güçlü bir hata bulma yöntemidir. Bu yöntem sayesindeki dosyadaki yapısal bozukluklar algılanarak dosyalarda sorun olup olmadığı kolaylıkla anlaşılabilir.

Girizgah fazla uzadı nedense. Çok mu dolmuşum ne?!?! Özet geçeyim: Bu program ile indirdiğiniz dosyaların çeşitli (MD5 ve SHA-1) hash değerlerini görebilir ve indirdiğiniz sitedeki hash değerleri ile karşılaştırabilirsiniz. Değerler karşı taraf ile bire bir uyuyorsa dosyada hiçbir sorun yoktur ve dosyaya dokunulmamıştır. Fakat değilse o dosyadan hayır yoktur, başkaları ya da 3. sahışlar tarafından değiştirilmiştir. Mümkünse dosyaya temkinli yaklaşın. Hatta dosyasınızı VirusTotal’e yükleyerek tarama yapmanıza salık veririm. Eğer İşinize gelmezse de silin gitsin. Programın özelliklerine gelecek olursak;

* Dosyaları ilgili alanın üzerine sürükleyerek bırakarak açma,
* CRC32 değerini bulma, (Bunu hazır bir sınıf olarak DamienG'den aldım)
* MD5 değerini bulma,
* SHA-1 değerini bulma,
* Dosya hash eşleştirmesi yapabilme.

{:.tablo-ortali}
| Dosya Hash Değeri Hesaplayıcı <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.02-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Dosya Hash Değeri Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: ed8ce2513eccb53cec1e9e53b994d7f3 | **MD5**: 792f75722a1b21bfac2bcd6cb3190b34 | 
| **Boyut**: 140 KB                       | **Boyut**: 779 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/qm72jn7xtsd2hxw/dosya-hash-degeri-hesaplayici.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/ycsfp8q8ad20ind/dosya-hash-degeri-hesaplayici-proje.zip?dl=1)                      |

**Ek** : Hash kodlarının nasıl hesaplandığını görmeye gelenler için **HashIslem.cs** sınıfındaki kodlar:

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace HashHesaplayici.Hash
{
    public class HashIslem : Kontroller
    {
        // Delege ile metotları hafızada tut
        public delegate void Islem(string dosyaAdi);

        // 1. Metot alanı (MD5)
        private readonly Islem _md5 = delegate(string dosyaAdi)
        {
            MD5 md5 = MD5.Create();
            Stream md5AkisOku = File.OpenRead(dosyaAdi);
            string md5Sonuc = BitConverter.ToString(md5.ComputeHash(md5AkisOku));

            TxtMd5.Text = md5Sonuc.Replace("-", "");
        };

        // 2. Metot alanı (SHA-1) - Hayat metotlarla daha kolay
        private readonly Islem _sha1 = delegate(string dosyaAdi)
        {
            SHA1 sha1 = SHA1.Create();
            Stream sha1AkisOku = File.OpenRead(dosyaAdi);
            string sha1Sonuc = BitConverter.ToString(sha1.ComputeHash(sha1AkisOku));

            TxtSha1.Text = sha1Sonuc.Replace("-", "");
        };

        // 3. Metot alanı (CRC-32) - Hayat metotlarla daha kolay
        // Crc32.cs sınıfından bu iş halledildi. Hail to the Damien Guard!..
        private readonly Islem _crc32 = delegate(string dosyaAdi)
        {
            Crc32 crc32 = new Crc32();
            Stream crc32AkisOku = File.OpenRead(dosyaAdi);
            string crc32Sonuc = BitConverter.ToString(crc32.ComputeHash(crc32AkisOku));

            TxtCrc32.Text = crc32Sonuc.Replace("-", "");
        };

        // Delegeleri yürüt (Şahane!)
        public void Hesapla(string dosyaAdresi)
        {
            _md5(dosyaAdresi);
            _sha1(dosyaAdresi);
            _crc32(dosyaAdresi);
        }
    }
}
```