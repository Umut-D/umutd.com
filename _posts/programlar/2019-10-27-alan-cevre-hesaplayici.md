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

Soyut sınıf (Abstract Class) ve gerekli metotları kullanarak alan ve çevre hesaplamalarının üstesinden gelmek ve işimi kolaylaştırmak aklımdan geçti. Aklımdan her geçeni yapmayan biri olsam da, bu seferlik öyle yapayım, öyle gitsin diye karar verdim. Tabi bu arada dönüştürme işlemlerim kolaylaşsın diye bir tane genişleme metodu yazdım. İşte o yüzden formüllerde **ToDouble(true)** metodu ben buradayım diye bağırıyor. Her şey bir yana özellikle ödev için buraya gelenlere fikir verecek cinsten bir çalışma oldu. Hayrını görün. Yaptım Oldu. Büyükşehir çalışıyor. Programın o çok bilindik özelliklerine gelecek olursak;

- Üçgen alan hesabını yapabilme,
- Kare, dikdörtgen ve çemberin alan ve çevre hesabını yapabilme.

{:.tablo-ortali}
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.04-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 233dfc8b6603e7f4e85467e884ef2231 | **MD5**: 2ca5973a57dce17c07cf51179247df3d | 
| **Boyut**: 45.9 KB                       | **Boyut**: 481.0 KB                         |
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
        protected StringBuilder Sonuc = new StringBuilder();

        // Metotlar
        public abstract string Cember(string yaricap);
        public abstract string Dikdortgen(string kisaKenar, string uzunKenar);
        public abstract string Kare(string kareKenar);
        public abstract string Ucgen(string ucgenKenar, string yukseklik);
    }

    class Hesapla : Geometri
    {
        public override string Cember(string yaricap)
        {
            Cevre = 2 * Math.PI * yaricap.ToDouble(true);
            Alan = Math.PI * Math.Pow(yaricap.ToDouble(true), 2);

            Sonuc.AppendLine(@"Çemberin Alanı (cm) = " + Alan.ToString("##.####"));
            Sonuc.Append(@"Çemberin cevresi (cm) = " + Cevre.ToString("##.####"));
            return Sonuc.ToString();
        }

        public override string Dikdortgen(string kisaKenar, string uzunKenar)
        {
            Cevre = (kisaKenar.ToDouble(true) + uzunKenar.ToDouble(true)) * 2;
            Alan = kisaKenar.ToDouble(true) * uzunKenar.ToDouble(true);

            Sonuc.AppendLine(@"Dikdörtgenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Dikdörtgenin Çevresi (cm) = " + Cevre);
            return Sonuc.ToString();
        }

        public override string Kare(string kareKenar)
        {
            Cevre = kareKenar.ToDouble(true) * 4;
            Alan = Math.Pow(kareKenar.ToDouble(true), 2);

            Sonuc.AppendLine(@"Karenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Karenin Çevresi (cm) = " + Cevre);
            return Sonuc.ToString();
        }

        public override string Ucgen(string ucgenKenar, string yukseklik)
        {
            Alan = ucgenKenar.ToDouble(true) * yukseklik.ToDouble(true) / 2;

            Sonuc.Append(@"Üçgenin Alanı (cm) = " + Alan);
            return Sonuc.ToString();
        }
    }
}
```