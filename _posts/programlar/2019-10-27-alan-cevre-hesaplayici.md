---
layout: post
title: Alan Çevre Hesaplayıcı
date: 2019-10-27 10:43 +0300
categories: Programlar
tags: Alan, Alan Çevre Hesaplama, Çember, Çevre, Daire, Dikdörtgen, Hesaplama, Kare, Üçgen
excerpt: Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama...
redirect_from:
  - /programlar/alan-cevre-hesaplama/
  - /etiket/alan-cevre-hesaplama/
---
![alan-cevre-hesaplayici](/images/programlar/alan-cevre-hesaplayici.png){: width="28%"}

Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama. Özellikle metotlar konularında fazlasıyla kolaylaşan bu hesap türü ile ilgili basit bir program yazmak istedim bu gündüzü güneşli, akşamı kaotik bir pazar gününde. 

Soyut sınıf (Abstract Class) Metotlar kullanarak alan ve çevre hesaplamalarının üstesinden gelmek ve işimi kolaylaştırmak aklımdan geçti. Fakat normal ve pek çok kişi tarafından bilindik usülle yazmış bulundum, geri dönmek için çok geçti. Her şey bir yana özellikle ödev için buraya gelenlere fikir verecek cinsten bir çalışma oldu. Hayrını görün. Yaptım Oldu. Büyükşehir çalışıyor. Programın o çok bilindik özelliklerine gelecek olursak;

- Üçgen alan hesabını yapabilme,
- Kare, dikdörtgen ve çemberin alan ve çevre hesabını yapabilme.

{:.tablo-ortali}
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.03-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 425c0dd987d51a794552ffbee2d3c931 | **MD5**: 856c8715406307d42e249561b00cd4ab | 
| **Boyut**: 46.3 KB                       | **Boyut**: 324.8 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/sbjiz659xwohoeb/alan-cevre-hesaplayici.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/4wq2lfj9ztx88kz/alan-cevre-hesaplayici-proje.zip?dl=1)                      |

**Ek** : Hesaplamaların nasıl yapıldığını görmeye gelenler için **Hesapla.cs** sınıfındaki kodlar:

```csharp
using System;
using System.Text;

namespace alan_cevre_hesaplayici
{
    public abstract class Geometri
    {
        // Genel değişkenler
        protected double Alan, Cevre;

        // Çember değişkeni
        protected double Yaricap;

        // Dikdörtgen değişkenleri
        protected double KisaKenar, UzunKenar;

        // Kare değişkenleri
        protected double KareKenar, UcgenKenar;

        // Üçgen değişkeni
        protected double UcgenYukseklik;

        // Metotlar
        public abstract string Cember(string yaricap);
        public abstract string Dikdortgen(string kisaKenar, string uzunKenar);
        public abstract string Kare(string kareKenar);
        public abstract string Ucgen(string ucgenKenar, string ucgenH);
    }

    class Hesapla : Geometri
    {
        readonly StringBuilder _sonuc = new StringBuilder();

        public override string Cember(string yaricap)
        {
            Yaricap = Convert.ToDouble(yaricap);
            Cevre = 2 * Math.PI * Yaricap;
            Alan = Math.PI * Math.Pow(Yaricap, 2);

            _sonuc.AppendLine(@"Çemberin Alanı (cm) = " + Alan.ToString("##.####"));
            _sonuc.Append(@"Çemberin cevresi (cm) = " + Cevre.ToString("##.####"));
            return _sonuc.ToString();
        }

        public override string Dikdortgen(string kisaKenar, string uzunKenar)
        {
            KisaKenar = Convert.ToDouble(kisaKenar);
            UzunKenar = Convert.ToDouble(uzunKenar);
            Cevre = (KisaKenar + UzunKenar) * 2;
            Alan = KisaKenar * UzunKenar;

            _sonuc.AppendLine(@"Dikdörtgenin Alanı (cm) = " + Alan);
            _sonuc.Append(@"Dikdörtgenin Çevresi (cm) = " + Cevre);
            return _sonuc.ToString();
        }

        public override string Kare(string kareKenar)
        {
            KareKenar = Convert.ToDouble(kareKenar);
            Cevre = KareKenar * 4;
            Alan = Math.Pow(KareKenar, 2);

            _sonuc.AppendLine(@"Karenin Alanı (cm) = " + Alan);
            _sonuc.Append(@"Karenin Çevresi (cm) = " + Cevre);
            return _sonuc.ToString();
        }

        public override string Ucgen(string ucgenKenar, string ucgenH)
        {
            UcgenKenar = Convert.ToDouble(ucgenKenar);
            UcgenYukseklik = Convert.ToDouble(ucgenH);
            Alan = (UcgenKenar * UcgenYukseklik) / 2;

            _sonuc.Append(@"Üçgenin Alanı (cm) = " + Alan);
            return _sonuc.ToString();
        }
    }
}
```