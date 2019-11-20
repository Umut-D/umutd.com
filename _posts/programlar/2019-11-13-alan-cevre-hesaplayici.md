---
layout: post
title: Alan Çevre Hesaplayıcı
date: 2019-11-13 19:43 +0300
categories: Programlar
tags: Alan, Alan Çevre Hesaplama, Çember, Çevre, Daire, Dikdörtgen, Hesaplama, Kare, Üçgen
excerpt: Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama...
redirect_from:
  - /programlar/alan-cevre-hesaplama/
  - /etiket/alan-cevre-hesaplama/
---
![alan-cevre-hesaplayici](/images/programlar/alan-cevre-hesaplayici.png){: width="28%"}

Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama. Özellikle metotlar konularında fazlasıyla kolaylaşan bu hesap türü ile ilgili basit bir program yazmak istedim güneşli çarşamba gününde. 

Soyut sınıf (Abstract Class) ve Polymorphism (Çok Biçimlilik) ile alan ve çevre hesaplamalarının üstesinden gelmek ve işimi kolaylaştırmak aklımdan geçti. Çok biçimlilik ile sahiden işler çok kolaylaştı. Tabi bu arada dönüştürme işlemlerim kolaylaşsın diye bir tane genişleme metodu eklemeyi ihmal etmedim. İşte bunlar hep tembellik. Bu nedenle işlemlerin üstünde görülen **ToDouble(true)** metodu ben buradayım diye bağırıyor. Her şey bir yana özellikle ödev için buraya gelenlere fikir verecek cinsten bir çalışma oldu. Hayrını görün. Yaptım Oldu. Büyükşehir çalışıyor. Sakın ola program kodları çok uzamış goygoyu yapmayın. Programa ileride yeni şekil ekleyince görürüm sizi. Hiç efor sarf etmeden eklemeyi yapınca anlarsınız Çok Biçimliliğin gücünü. Programın o çok bilindik özelliklerine gelecek olursak;

- Üçgenin alan, kare, dikdörtgen ve çemberin alan ve çevre hesaplarını yapabilme.

{:.tablo-ortali}
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.07-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 76bc76e8daf61c7851b66225e7e37990 | **MD5**: 2e050d666c2e3866b5ebddc934695fe5 | 
| **Boyut**: 46.4 KB                       | **Boyut**: 416.0 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/sbjiz659xwohoeb/alan-cevre-hesaplayici.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/4wq2lfj9ztx88kz/alan-cevre-hesaplayici-proje.zip?dl=1)                      |

**Ek** : Hesaplamaların nasıl yapıldığını görmeye gelenler için **Sekil.cs** ve ondan türetilen sınıfındaki kodlar:

```csharp
using System;
using System.Text;

namespace Alan_Cevre_Hesaplayici
{
    // Polymorphism ile her şey mümkün!
    public abstract class Sekil
    {
        protected double Alan { get; set; }
        protected double Cevre { get; set; }
        protected StringBuilder Sonuc { get; } = new StringBuilder();

        public abstract string Formul();
    }

    // Kullanıcıya 4 şekilden birini seçmeye zorla
    // Seçilen sınıfa göre, ilgili sınıftaki Formül'ü işlet
    public class Islem
    {
        private readonly Sekil _sekil;

        public Islem(Sekil sekil)
        {
            _sekil = sekil;
        }

        public string Hesapla()
        {
            return _sekil.Formul();
        }
    }

    class Cember : Sekil
    {
        private double Yaricap { get; }

        public Cember(string yaricap)
        {
            Yaricap = yaricap.ToDouble(true);
        }

        public override string Formul()
        {
            Cevre = 2 * Math.PI * Yaricap;
            Alan = Math.PI * Math.Pow(Yaricap, 2);

            Sonuc.AppendLine(@"Çemberin Alanı (cm) = " + Alan.ToString("##.####"));
            Sonuc.Append(@"Çemberin cevresi (cm) = " + Cevre.ToString("##.####"));

            return Sonuc.ToString();
        }
    }

    public class Dikdortgen : Sekil
    {
        private double KisaKenar { get; }
        private double UzunKenar { get; }

        public Dikdortgen(string kisaKenar, string uzunKenar)
        {
            KisaKenar = kisaKenar.ToDouble(true);
            UzunKenar = uzunKenar.ToDouble(true);
        }

        public override string Formul()
        {
            Cevre = (KisaKenar + UzunKenar) * 2;
            Alan = KisaKenar * UzunKenar;

            Sonuc.AppendLine(@"Dikdörtgenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Dikdörtgenin Çevresi (cm) = " + Cevre);

            return Sonuc.ToString();
        }
    }

    public class Kare : Sekil
    {
        private double KareKenar { get; }

        public Kare(string kareKenar)
        {
            KareKenar = kareKenar.ToDouble(true);
        }

        public override string Formul()
        {
            Cevre = KareKenar * 4;
            Alan = Math.Pow(KareKenar, 2);

            Sonuc.AppendLine(@"Karenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Karenin Çevresi (cm) = " + Cevre);

            return Sonuc.ToString();
        }
    }

    public class Ucgen : Sekil
    {
        private double Yukseklik { get; }
        private double UcgenKenar { get; }

        public Ucgen(string ucgenKenar, string yukseklik)
        {
            UcgenKenar = ucgenKenar.ToDouble(true);
            Yukseklik = yukseklik.ToDouble(true);
        }

        public override string Formul()
        {
            Alan = UcgenKenar * Yukseklik / 2;

            Sonuc.Append(@"Üçgenin Alanı (cm) = " + Alan);

            return Sonuc.ToString();
        }
    }
}
```