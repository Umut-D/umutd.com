---
layout: post
title: Faktöriyel, Kombinasyon, Permütasyon Hesaplayıcı
date: 2018-11-30 12:43 +0300
categories: Programlar
tags: Faktöriyel, Kombinasyon, Permütasyon
---
![fkp-hesaplayici](/images/programlar/fkp-hesaplayici.png){: width="55%"}

Geçtiğimiz hafta, çalıştığım işle ilgili bir görevde, kombinasyon oluşturmam ve öncelikle bunun sayısını belirlemem gerekti. Haliyle elime kalem kağıdı alıp kombinasyon hesabı yapmaya üşendim. Ancak program yazmaya nedense üşenmedim. Kombinasyon hesaplayabilen bu programı yazdıkça ne olur ne olmaz diye yanına faktöriyel ve permütasyon hesaplama seçeneklerini de koydum ki, belki böyle proje, ödev hazırlamak isteyenlere veyahut netten metotlar yardımıyla işlem yapan bir program arayanlara yardımcı olayım dedim.

Aslında günlük hayatta faktöriyel, kombinasyon, permütasyon hesaplarını işletim sistemlerindeki hesap makinelerinden tutun Excel’e kadar pek çok program kolaylıkla yapmakta. Ben sadece bunu C#’a taşımak ve temiz bir şekilde yazmaya çalıştığım kodlarla bunu gerçekleştirmek istedim. İtiraf ediyorum, özel bir amacım yoktu. Özelliklerine gelecek olursak;

- Faktöriyel (maksimum 11),
- Kombinasyon,
- Permütasyon hesabı yapma.

{:.tablo-ortali}
| Faktöriyel, Kombinasyon, Permütasyon<br> Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.01-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) |  Faktöriyel, Kombinasyon, Permütasyon<br>Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: d161e1cb1e8d0cdce9dbe2d5f6d9c5ee | **MD5**: 16c55f425141f8037ec57a9f65c8a212 | 
| **Boyut**:  112.2 KB                       | **Boyut**:  551.7 KB                         |
| **Gereksinimler**: .Net Framework 3.5     | **Gereksinimler**: .Net Framework 3.5     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/fkp-hesaplayici.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/fkp-hesaplayici-proje.zip)                      |

**Ek** : Nasıl hesaplama yapıldığını görmeye gelenler için **Hesapla.cs** sınıfındaki kodlar:

```csharp
using System;
 
namespace fkp_hesapla
{
    public class Hesapla
    {
        private int _birinciSayi;
        private int _ikinciSayi;
        public int Fark => BirinciSayi - IkinciSayi;
        public int FaktoriyelSonuc { get; set; } = 1;
 
        public int BirinciSayi
        {
            get { return _birinciSayi; }
            set
            {
                if (value < 12)
                    _birinciSayi = value;
                else
                    throw new Exception("1. Sayı 11'den büyük olmamalı");
            }
        }
 
        public int IkinciSayi
        {
            get { return _ikinciSayi; }
            set
            {
                if (value < 12 && _birinciSayi >= _ikinciSayi)
                    _ikinciSayi = value;
                else
                    throw new Exception("2. Sayı 11'den büyük olmamalı.");
            }
        }
 
        public int Faktoriyel(int sayi)
        {
            FaktoriyelSonuc = 1;
 
            for (int i = 1; i <= sayi; i++)
                FaktoriyelSonuc *= i;
 
            return FaktoriyelSonuc;
        }
 
        public int Kombinasyon(int birinciSayi, int ikinciSayi)
        {
            return Faktoriyel(BirinciSayi) / (Faktoriyel(IkinciSayi) * Faktoriyel(Fark));
        }
 
        public int Permutasyon(int birinciSayi, int ikinciSayi)
        {
            return Faktoriyel(BirinciSayi) / Faktoriyel(Fark);
        }
    }
}
```