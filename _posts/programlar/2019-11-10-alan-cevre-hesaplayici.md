---
layout: post
title: Alan Çevre Hesaplayıcı
date: 2019-11-10 10:43 +0300
categories: Programlar
tags: Alan, Alan Çevre Hesaplama, Çember, Çevre, Daire, Dikdörtgen, Hesaplama, Kare, Üçgen
excerpt: Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama...
redirect_from:
  - /programlar/alan-cevre-hesaplama/
  - /etiket/alan-cevre-hesaplama/
---
![alan-cevre-hesaplayici](/images/programlar/alan-cevre-hesaplayici.png){: width="28%"}

Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama. Özellikle metotlar konularında fazlasıyla kolaylaşan bu hesap türü ile ilgili basit bir program yazmak istedim güneşli pazar gününde. 

Soyut sınıf (Abstract Class) ve gerekli metotları kullanarak alan ve çevre hesaplamalarının üstesinden gelmek ve işimi kolaylaştırmak aklımdan geçti. Fakat biraz daha temiz ve sade kod yazmak adına bundan 1.05 versiyon ile vazgeçtim. Tabi bu arada dönüştürme işlemlerim kolaylaşsın diye bir tane genişleme metodu eklemeyi ihmal etmedim. İşte bunlar hep tembellik. Bu nedenle işlemlerin üstünde görülen **ToDouble(true)** metodu ben buradayım diye bağırıyor. Her şey bir yana özellikle ödev için buraya gelenlere fikir verecek cinsten bir çalışma oldu. Hayrını görün. Yaptım Oldu. Büyükşehir çalışıyor. Programın o çok bilindik özelliklerine gelecek olursak;

- Üçgenin alan, kare, dikdörtgen ve çemberin alan ve çevre hesaplarını yapabilme.

{:.tablo-ortali}
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.05-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 033b8bb5be596cf2a093b52d44770752 | **MD5**: 12720745dd5804f64077ddcbd0019161 | 
| **Boyut**: 46.5 KB                       | **Boyut**: 413.0 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/sbjiz659xwohoeb/alan-cevre-hesaplayici.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/4wq2lfj9ztx88kz/alan-cevre-hesaplayici-proje.zip?dl=1)                      |

**Ek** : Hesaplamaların nasıl yapıldığını görmeye gelenler için **Hesapla.cs** sınıfındaki kodlar:

```csharp
using System;
using System.Text;

namespace Alan_Cevre_Hesaplayici
{
    class Hesapla
    {
        private double Alan { get; set; }
        private double Cevre { get; set; }
        private double Yaricap { get; set; }
        private double KKenar { get; set; }
        private double UKenar { get; set; }
        private double Yukseklik { get; set; }
        private StringBuilder Sonuc { get; } = new StringBuilder();

        public string Cember(string yaricap)
        {
            Yaricap = yaricap.ToDouble(true);

            // İşlemler
            Cevre = 2 * Math.PI * Yaricap;
            Alan = Math.PI * Math.Pow(Yaricap, 2);

            Sonuc.AppendLine(@"Çemberin Alanı (cm) = " + Alan.ToString("##.####"));
            Sonuc.Append(@"Çemberin cevresi (cm) = " + Cevre.ToString("##.####"));

            return Sonuc.ToString();
        }

        public string Dikdortgen(string kisaKenar, string uzunKenar)
        {
            KKenar = kisaKenar.ToDouble(true);
            UKenar = uzunKenar.ToDouble(true);

            // İşlemler
            Cevre = (KKenar + UKenar) * 2;
            Alan = KKenar * UKenar;

            Sonuc.AppendLine(@"Dikdörtgenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Dikdörtgenin Çevresi (cm) = " + Cevre);

            return Sonuc.ToString();
        }

        public string Kare(string kareKenar)
        {
            KKenar = kareKenar.ToDouble(true);

            // İşlemler
            Cevre = KKenar * 4;
            Alan = Math.Pow(KKenar, 2);

            Sonuc.AppendLine(@"Karenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Karenin Çevresi (cm) = " + Cevre);

            return Sonuc.ToString();
        }

        public string Ucgen(string ucgenKenar, string yukseklik)
        {
            UKenar = ucgenKenar.ToDouble(true);
            Yukseklik = yukseklik.ToDouble(true);

            // İşlem
            Alan = UKenar * Yukseklik / 2;

            Sonuc.Append(@"Üçgenin Alanı (cm) = " + Alan);

            return Sonuc.ToString();
        }
    }
}
```