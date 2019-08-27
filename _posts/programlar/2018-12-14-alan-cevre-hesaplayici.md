---
layout: post
title: Alan Çevre Hesaplayıcı
date: 2018-12-14 12:43 +0300
categories: Programlar
tags: Alan, Alan Çevre Hesaplama, Çember, Çevre, Daire, Dikdörtgen, Hesaplama, Kare, Üçgen
---
![iban-kontrol](/images/programlar/alan-cevre-hesaplayici.png){: width="28%"}

Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama. Özellikle metotlar konularında fazlasıyla kolaylaşan bu hesap türü ile ilgili basit bir program yazmak istedim bu gündüzü güneşli, akşamı kaotik bir pazar gününde. Metotlar kullanarak alan ve çevre hesaplamalarının üstesinden gelmek ve işimi kolaylaştırmak aklımdan geçti. Fakat normal ve pek çok kişi tarafından bilindik usülle yazmış bulundum, geri dönmek için çok geçti. Her şey bir yana özellikle ödev için buraya gelenlere fikir verecek cinsten bir çalışma oldu. Hayrını görün. Yaptım Oldu. Büyükşehir çalışıyor. Programın özelliklerine gelecek olursak;

- Üçgen alan hesabını yapabilme,
- Kare, dikdörtgen ve çemberin alan ve çevre hesabını yapabilme.

{:.tablo-ortali}
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.02-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 425c0dd987d51a794552ffbee2d3c931 | **MD5**: 856c8715406307d42e249561b00cd4ab | 
| **Boyut**: 46.3 KB                       | **Boyut**: 324.8 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/alan-cevre-hesaplayici.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/alan-cevre-hesaplayici-proje.zip)                      |

**Ek** : Hesaplamaların nasıl yapıldığını görmeye gelenler için **Hesapla.cs** sınıfındaki kodlar:

```csharp
using System;
 
namespace alan_cevre_hesaplayici
{
    public abstract class Degiskenler
    {
        public double Alan { get; set; }
        public double Cevre { get; set; }
    }
 
    public class Cember : Degiskenler
    {
        private double Yaricap { get; set; }
 
        public string Hesapla(string yaricap)
        {
            Yaricap = Convert.ToDouble(yaricap);
 
            Cevre = 2 * Math.PI * Yaricap;
            Alan = Math.PI * Math.Pow(Yaricap, 2);
 
            return @"Çemberin Alanı (cm) = " + Alan.ToString("##.####") + Environment.NewLine + @"Çemberin cevresi (cm) = " + Cevre.ToString("##.####");
        }
    }
 
    public class Dikdortgen : Degiskenler
    {
        private double KisaKenar { get; set; }
        private double UzunKenar { get; set; }
 
        public string Hesapla(string kisaKenar, string uzunKenar)
        {
            KisaKenar = Convert.ToDouble(kisaKenar);
            UzunKenar = Convert.ToDouble(uzunKenar);
 
            Cevre = (KisaKenar + UzunKenar) * 2;
            Alan = KisaKenar * UzunKenar;
 
            return @"Dikdörtgenin Alanı (cm) = " + Alan + Environment.NewLine + @"Dikdörtgenin Çevresi (cm) = " + Cevre;
        }
    }
 
    public class Kare : Degiskenler
    {
        private double KareKenar { get; set; }
 
        public string Hesapla(string kareKenar)
        {
            KareKenar = Convert.ToDouble(kareKenar);
 
            Cevre = KareKenar * 4;
            Alan = Math.Pow(KareKenar, 2);
 
            return @"Karenin Alanı (cm) = " + Alan + Environment.NewLine + @"Karenin Çevresi (cm) = " + Cevre;
        }
    }
 
    public class Ucgen : Degiskenler
    {
        private double UcgenKenar { get; set; }
        private double UcgenH { get; set; }
 
        public string Hesapla(string ucgenKenar, string ucgenH)
        {
            UcgenKenar = Convert.ToDouble(ucgenKenar);
            UcgenH = Convert.ToDouble(ucgenH);
 
            Alan = (UcgenKenar * UcgenH) / 2;
            return @"Üçgenin Alanı (cm) = " + Alan;
        }
    }
}
```