---
layout: post
title: Mors Alfabesi Dönüştürücü
date: 2019-01-12 12:43 +0300
categories: Programlar
tags: Mors, Mors Alfabesi, Mors Kodu
---
> **Mors alfabesi** veya **mors kodu**, kısa ve uzun işaretler (• ve –) ile bunlara karşılık gelen ışık veya sesleri kullanarak bilgi aktarılmasını sağlayan yönteme denir.

![mors-alfabesi-donusturucu](/images/programlar/mors-alfabesi-donusturucu.png){: width="38%"}

Yukarıdaki biçimde Vikipedia'da açıklanan mors alfabesine ve bunun dönüşümüne dair bir program yazmaya çalıştım. 

Sınıfıdır, metodudur, dönüşümüdür. Gırla gitti. Yazması basit ve keyifli oldu. Her zamanki gibi tasarım sıfır. Ben zaten bu tasarım işinden zerre haz etmiyorum. Haz etmediğim için de anlamıyorum. Programı öyle çok gözde büyütmeye gerek yok. Dağlara taşlara bir program değil. Kendi halinde agabında dönüşümünü yapıyor işte. Programın özelliklerine gelecek olursak;

- Yazıdan mors alfabesine dönüşüm yapabilme,
- Mors alfabesinden yazıya dönüşüm yapabilme,
- Yapılan dönüşümü metin belgesi olarak kaydetme.

{:.tablo-ortali}
| Mors Alfabesi Dönüştürücü <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.01-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Mors Alfabesi Dönüştürücü (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: b7ec5bf4be56318d33b8070d5f8b6362 | **MD5**: 7614abcee05c6e9ddf14177700941e4c | 
| **Boyut**: 169.6 KB                       | **Boyut**: 719.3 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar1/mors-alfabesi-donusturucu.zip)         | **İndir**: [Link](http://www.umutd.com/programlar1/mors-alfabesi-donusturucu-proje.zip)                      |

**Ek** : Mors alfebesinin nasıl dönüştürüldüğünü görmeye gelenler için **Donustur.cs** sınıfındaki kodlar:

```csharp
using System.Collections.Generic;
using System.Text;
 
namespace MorsAlfabesiDonusturucu.Siniflar
{
    public class Donustur : MorsKodu
    {
        public StringBuilder Cumle { get; set; } = new StringBuilder();
 
        // Türkçe karakter olup olmadığını belirleyip, ingilizce karakterlere dönüştür
        public string Karakter(string yazi)
        {
            char[] trKarakterler = {'ı', 'ğ', 'İ', 'Ğ', 'ç', 'Ç', 'ş', 'Ş', 'ö', 'Ö', 'ü', 'Ü'};
            char[] enKarakterler = {'i', 'g', 'I', 'G', 'c', 'C', 's', 'S', 'o', 'O', 'u', 'U'};
 
            for (int i = 0; i < trKarakterler.Length; i++)
                yazi = yazi.Replace(trKarakterler[i], enKarakterler[i]);
 
            return yazi.ToUpperInvariant();
        }
 
        // txtGirdi kısmına girilen metin yazı/sayıdan mı, mors alfabesinden mi oluşuyor?
        public bool MetinMi(string girilenMetin)
        {
            girilenMetin = girilenMetin.Replace('-', ' ').Replace('.', ' ').Replace('/', ' ');
            
            return string.IsNullOrWhiteSpace(girilenMetin);
        }
 
        // İngilizce karakterlere dönüştürülen metni, Mors alfabesine dönüştür
        public string Mors(string yazi)
        {
            Cumle.Clear();
 
            // Gelen cümleyi tek tek karaktere dönüştür
            List<char> gelenHarfler = new List<char>(yazi.ToCharArray());
 
            // Dictionary sınıfında eşleştirmeleri yapıp mors kodunu elde et
            foreach (char donusenYazi in gelenHarfler)
                Cumle.Append((MorsAlfabesi[donusenYazi.ToString()]) + @" ");
 
            return Cumle.ToString().TrimEnd();
        }
 
        // İngilizce karakterlere dönüştürülen metni, Mors alfabesine dönüştür
        public string Yazi(string yazi)
        {
            // Gelen cümleyi parçalara ayır
            List<string> dizi = new List<string>(yazi.Split(' '));
            string donusturulenYazi = "";
 
            // Ayrılan cümle harflerini tek tek dönüştür ve yeniden kelime ve cümle haline getir
            foreach (string harf in dizi)
            {
                foreach (KeyValuePair<string, string> pair in MorsAlfabesi)
                {
                    if (pair.Value == harf)
                        donusturulenYazi += pair.Key;
                }
            }
 
            return donusturulenYazi;
        }
    }
}
```