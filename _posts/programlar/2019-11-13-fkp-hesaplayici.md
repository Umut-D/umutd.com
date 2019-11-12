---
layout: post
title: Faktöriyel, Kombinasyon, Permütasyon Hesaplayıcı
date: 2019-11-13 12:43 +0300
categories: Programlar
tags: Faktöriyel, Kombinasyon, Permütasyon
excerpt: Geçtiğimiz hafta, çalıştığım işle ilgili bir görevde, kombinasyon oluşturmam ve öncelikle bunun sayısını belirlemem gerekti. Haliyle elime kalem kağıdı alıp kombinasyon hesabı yapmaya üşendim. Ancak program yazmaya nedense üşenmedim...
redirect_from:
  - /programlar/fkp-hesaplayici/
  - /etiket/permutasyon/
---
![fkp-hesaplayici](/images/programlar/fkp-hesaplayici.png){: width="55%"}

Geçtiğimiz hafta, çalıştığım işle ilgili bir görevde, kombinasyon oluşturmam ve öncelikle bunun sayısını belirlemem gerekti. Haliyle elime kalem kağıdı alıp kombinasyon hesabı yapmaya üşendim. Ancak program yazmaya nedense üşenmedim. Kombinasyon hesaplayabilen bu programı yazdıkça ne olur ne olmaz diye yanına faktöriyel ve permütasyon hesaplama seçeneklerini de koydum ki, belki böyle proje, ödev hazırlamak isteyenlere veyahut netten metotlar yardımıyla işlem yapan bir program arayanlara yardımcı olayım dedim.

Aslında günlük hayatta faktöriyel, kombinasyon, permütasyon hesaplarını işletim sistemlerindeki hesap makinelerinden tutun Excel’e kadar pek çok program kolaylıkla yapmakta. Ben sadece bunu C#’a taşımak ve temiz bir şekilde yazmaya çalıştığım kodlarla bunu gerçekleştirmek istedim. İtiraf ediyorum, özel bir amacım yoktu. Özelliklerine gelecek olursak;

- Faktöriyel (maksimum 11),
- Kombinasyon,
- Permütasyon hesabı yapma.

{:.tablo-ortali}
| Faktöriyel, Kombinasyon, Permütasyon<br> Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.02-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) |  Faktöriyel, Kombinasyon, Permütasyon<br>Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 9b24b1e5fba9705bfc424cc6e891adde | **MD5**: 97b519b98b74ec34a3a6528d7f65093f | 
| **Boyut**:  112 KB                       | **Boyut**:  788 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4    |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/61a22sn9ozb2qrr/fkp-hesaplayici.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/mxbl0lqsswst9yg/fkp-hesaplayici-proje.zip?dl=1)                      |

**Ek** : Nasıl hesaplama yapıldığını görmeye gelenler için **Hesapla.cs** sınıfındaki kodlar:

```csharp
using System;

namespace fkp_hesapla
{
    public class Matematik
    {
        private int _birinciSayi;
        private int _ikinciSayi;
        public int Fark => BirinciSayi - IkinciSayi;

        public int BirinciSayi
        {
            get => _birinciSayi;
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
            get => _ikinciSayi;
            set
            {
                if (value < 12 && _birinciSayi >= _ikinciSayi)
                    _ikinciSayi = value;
                else
                    throw new Exception("2. Sayı 11'den büyük olmamalı.");
            }
        }

        public virtual int Hesap() => throw new NotImplementedException();
    }

    public sealed class Faktoriyel
    {
        private int Sonuc { get; set; } = 1;

        public int Hesap(int sayi)
        {
            Sonuc = 1;

            for (int i = 1; i <= sayi; i++)
                Sonuc *= i;

            return Sonuc;
        }
    }

    public sealed class Kombinasyon : Matematik
    {
        private readonly Faktoriyel _faktoriyel;

        public Kombinasyon(Faktoriyel faktoriyel, int birinciSayi, int ikinciSayi)
        {
            _faktoriyel = faktoriyel;
            BirinciSayi = birinciSayi;
            IkinciSayi = ikinciSayi;
        }

        public override int Hesap()
        {
            return _faktoriyel.Hesap(BirinciSayi) / (_faktoriyel.Hesap(IkinciSayi) * _faktoriyel.Hesap(Fark));
        }
    }

    public sealed class Permutasyon : Matematik
    {
        private readonly Faktoriyel _faktoriyel;

        public Permutasyon(Faktoriyel faktoriyel, int birinciSayi)
        {
            _faktoriyel = faktoriyel;
            BirinciSayi = birinciSayi;
        }

        public override int Hesap()
        {
            return _faktoriyel.Hesap(BirinciSayi) / _faktoriyel.Hesap(Fark);
        }
    }
}
```