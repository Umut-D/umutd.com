---
layout: post
title: Rastgele Sayı Üretici
date: 2020-12-16 12:43 +0300
categories: Programlar
tags: Farklı Sayı, Random Sayı, Rastgele Benzersiz Sayı, Rastgele Sayı, Rastgele Sayı Üretici
excerpt: Bundan bir süre önce bir arkadaşım telefon etti. Artık illallah dediği bir istatistik ödevinin verilerini toplamaya çalışırken gördüğü muameleden ve proje hocasının yaptığı araştırmaya olan ilgisizliğinden dem vurdu. Sağlıkla ilgili olarak yaptığı araştırmada 80 çocuğun kilolarını tek tek ölçmesinin istenildiği için mutsuz olduğunu, bunun için gerekli izinleri almanın ve çocukları tek tek tartıya çıkarmanın zorluğunu anlattı...
redirect_from:
  - /programlar/rastgele-sayi-uretici/
  - /etiket/rastgele-sayi/
---
![rastgele-sayi-uretici](/images/programlar/rastgele-sayi-uretici.png){: width="30%"}

Bundan bir süre önce bir arkadaşım telefon etti. Artık illallah dediği bir istatistik ödevinin verilerini toplamaya çalışırken gördüğü muameleden ve proje hocasının yaptığı araştırmaya olan ilgisizliğinden dem vurdu. Sağlıkla ilgili olarak yaptığı araştırmada 80 çocuğun kilolarını tek tek ölçmesinin istenildiği için mutsuz olduğunu, bunun için gerekli izinleri almanın ve çocukları tek tek tartıya çıkarmanın zorluğunu anlattı. Ne yalan söyleyeyim dayanamadım, tüm sıkıntısını efor sarf etmeden, sadece rastgele sayılar üreterek çözebileceğini, dünyayı kurtarmayacak araştırmasının da eninde sonunda rafa kaldırılacağını kendisine söyledim. Sırf bu iş için kendisine program yazabileceğimi belirttim. Etik metik hak getire. Şeytani ikna yolları kullanmam işe yaradı.

Vakit geçirmeden programı yazdım ve kendisine yolladım. İşte böyle tuhaf diyaloglardan sonra çıktı rastgele sayılar üreten bir program yazma fikri. Program sayesinde rastgele sayılar üretip bunları Txt dosyasına kolaylıkla kaydediyor, paşa gönlünüz isterse verileri Excel’e, Word’e yapıştırabiliyorsunuz. Her türlü araştırmanızda rastgele sayı sahtekarlığı yapmanızı sağlayan bu güzel programı araştırmanız için, yeni veriler lazım olduğunda yanınızdan ayıramayacaksınız :)) Özelliklerine gelecek olursak;

- İstenilen sayı aralıklarında ve belirtilen adet kadar- rastgele sayı üretme,
- İstenilen sayı aralıklarında ve belirtilen adet kadar- benzersiz rastgele sayı üretme,
- Üretilen sayıları Metin Belgesi (Text dosyası) olarak kaydetme.

{:.tablo-ortali}
| Rastgele Sayı Üretici<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.21-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele Sayı Üretici (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) |![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)
|----------------------------------------- -|-------------------------------------------|
| **MD5**: d2a7ab340bbe5e69d6fbe81cd6464760 | **MD5**: 91d7f3fa4d40573e3112d35b63e2174c | 
| **Boyut**: 10.8 KB                       | **Boyut**:  101 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/bh2lgtnsg5cbe85/rastgele-sayi-uretici.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/navr87uh7u8oj7b/rastgele-sayi-uretici-proje.zip?dl=1) |

**Ek** : Rastgele sayıların nasıl oluşturulduğunu görmeye gelenler için **Sayi.cs** ve **Islem.cs** sınıflarındaki kodlar:

```csharp
using System;

namespace rastgele_sayi
{
    public abstract class Sayi
    {
        private int _kucukSayi;
        private int _buyukSayi;
        private int _adet;

        protected int KucukSayi
        {
            get => _kucukSayi;
            set
            {
                if (value < 10000)
                    _kucukSayi = value;
                else
                    throw new Exception("Girilen değer 10.000'den büyük olmamalı!");
            }
        }

        protected int BuyukSayi
        {
            get => _buyukSayi;
            set
            {
                if (value <= 10000 && _kucukSayi < value)
                    _buyukSayi = value + 1;
                else
                    throw new Exception("Girilen değer 10.000'den büyük olmamalı veya küçük sayıdan büyük olmalı!");
            }
        }

        protected int Adet
        {
            get => _adet;
            set
            {
                if (value <= 10000 && _adet < value)
                    _adet = value;
                else
                    throw new Exception("Girilen değer 10.000'den büyük olmamalı!");
            }
        }

        protected bool Fark
        {
            get
            {
                int fark = BuyukSayi - KucukSayi;
                if (fark >= 1 && fark >= Adet)
                    return true;

                return false;
            }
        }

        protected Sayi(int kucukSayi, int buyukSayi, int adet)
        {
            KucukSayi = kucukSayi;
            BuyukSayi = buyukSayi;
            Adet = adet;
        }
    }
}
```
<div id="ara"></div>

```csharp
using System;
using System.Collections.Generic;

namespace rastgele_sayi
{
    public class Islem : Sayi
    {
        private readonly Random _rastgeleSayi;
        private readonly List<int> _sayilar;

        public Islem(int kucukSayi, int buyukSayi, int adet) : base(kucukSayi, buyukSayi, adet)
        {
            _rastgeleSayi = new Random();
            _sayilar = new List<int>();
        }

        public List<int> SayiOlustur()
        {
            for (int i = 0; i < Adet; i++)
            {
                int sayi = _rastgeleSayi.Next(KucukSayi, BuyukSayi);
                _sayilar.Add(sayi);
            }

            return _sayilar;
        }

        public List<int> BenzersizSayiOlustur()
        {
            if (!Fark)
                throw new Exception("Benzersiz olarak üretilen sayılar Büyük Sayı ile Küçük Sayı farkından fazla olamaz!");

            for (int i = 0; i < Adet; i++)
            {
                int sayi = _rastgeleSayi.Next(KucukSayi, BuyukSayi);

                if (!_sayilar.Contains(sayi))
                    _sayilar.Add(sayi);
                else
                    i--;
            }

            return _sayilar;
        }
    }
}
```