---
layout: post
title: Dosya Hash Değeri Hesaplayıcı
date: 2018-11-22 12:43 +0300
categories: Programlar
tags: Barkod, Barkod Kontrol Kodu Hesaplayıcı, EAN-13, Kontrol Kodu
---
![iban-kontrol](/images/programlar/dosya-hash-hesaplayici.png){: width="46%"}

Bundan yaklaşık bir hafta önce, programlarımdan birine dair eleştiri geldi. Eleştiriyi yapan kişi temel olarak programın virüs ve casus program barındırdığını söylemekte, kendince çeşitli nedenler sıralamaktaydı. Kendisine verdiğim cevaplarda programın kaynak kodlarına göz gezdirmesini ve VirusTotal sonuçlarına bakmasını istedim. Çünkü kaynak kodları apaçık ortadayken, VirusTotal sonuçlarına göre 57 ayrı virüs tarama servisinde yapılan taramaya göre de programda herhangi bir anormallik olmadığı gözükmekteydi. Nitekim VirusTotal’in virus/casus/zararlı yazılım tespit ekranında 0 / 57 yazmaktaydı.

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
| Dosya Hash Değeri Hesaplayıcı <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.01-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Dosya Hash Değeri Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 1b3b7532b57e722e2d9302bc06f76844 | **MD5**: b52d621224822341fd08f977cb75cf76 | 
| **Boyut**: 140.1 KB                       | **Boyut**: 778.8 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/dosya-hash-hesaplayici.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/dosya-hash-hesaplayici-proje.zip)                      |

**Ek** : Hash kodlarının nasıl hesaplandığını görmeye gelenler için **HashHesapla.cs** sınıfındaki kodlar:

```csharp
using System;
using System.IO;
using System.Security.Cryptography;
using System.Windows.Forms;
 
namespace HashHesaplayici.Hash
{
    public class HashHesapla
    {
        public static string Md5 { get; set; }
        public static string Sha1 { get; set; }
        public static string Crc32 { get; set; }
 
        static readonly TextBox TxtDosyaAdi = Application.OpenForms["FrmHash"]?.Controls["txtDosyaAdi"] as TextBox;
        public static TextBox TxtCrc32 = Application.OpenForms["FrmHash"]?.Controls["txtCrc32"] as TextBox;
        public static TextBox TxtMd5 = Application.OpenForms["FrmHash"]?.Controls["txtMd5"] as TextBox;
        public static TextBox TxtSha1 = Application.OpenForms["FrmHash"]?.Controls["txtSha1"] as TextBox;
 
        // 1. Metot alanı (MD5) - Hayat metotlarla daha kolay
        public static string Md5Hesapla(string dosyaAdi)
        {
            MD5 md5Islemi = MD5.Create();
            Stream md5AkisOku = File.OpenRead(dosyaAdi);
            Md5 = BitConverter.ToString(md5Islemi.ComputeHash(md5AkisOku)).Replace("-", "");
 
            return Md5;
        }
 
        // 2. Metot alanı (SHA-1) - Hayat metotlarla daha kolay
        public static string Sha1Hesapla(string dosyaAdi)
        {
            SHA1 sha1Islemi = SHA1.Create();
            Stream sha1AkisOku = File.OpenRead(dosyaAdi);
            Sha1 = BitConverter.ToString(sha1Islemi.ComputeHash(sha1AkisOku)).Replace("-", "");
 
            return Sha1;
        }
 
        // 3. Metot alanı (CRC-32) - Hayat metotlarla daha kolay
        // Crc32.cs sınıfından bu iş halledildi. Hail to the Damien Guard!..
        public static string Crc32Hesapla(string dosyaAdi)
        {
            Crc32 crc32Islemi = new Crc32();
            Stream crc32AkisOku = File.OpenRead(dosyaAdi);
            Crc32 = BitConverter.ToString(crc32Islemi.ComputeHash(crc32AkisOku)).Replace("-", "");
 
            return Crc32;
        }
 
        // Genel hesaplama işlemlerini yaparak ilgili bilgileri FrmHash'a döndr
        public static void Hesapla()
        {
            TxtDosyaAdi.Text = Path.GetFileName(FrmHash.DosyaAdresi);
 
            TxtCrc32.Text = Crc32Hesapla(FrmHash.DosyaAdresi);
            TxtMd5.Text = Md5Hesapla(FrmHash.DosyaAdresi);
            TxtSha1.Text = Sha1Hesapla(FrmHash.DosyaAdresi);
        }
    }
}
```