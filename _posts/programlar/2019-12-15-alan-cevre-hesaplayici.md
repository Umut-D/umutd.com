---
layout: post
title: Alan Çevre Hesaplayıcı
date: 2019-12-15 01:43 +0300
categories: Programlar
tags: Alan, Alan Çevre Hesaplama, Çember, Çevre, Daire, Dikdörtgen, Hesaplama, Kare, Üçgen
excerpt: Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama...
redirect_from:
  - /programlar/alan-cevre-hesaplama/
  - /etiket/alan-cevre-hesaplama/
---
![alan-cevre-hesaplayici](/images/programlar/alan-cevre-hesaplayici.png){: width="28%"}

Lise ve üniversitelerdeki bilgisayar ve onunla ilgili bölümlerde Nesneye Yönelik Programlama derslerinde (Java, C++, C# hiç fark etmez) mutlaka örnek verilen bir konu alan hesaplama. Özellikle metotlar konularında fazlasıyla kolaylaşan bu hesap türü ile ilgili basit bir program yazmak istedim güneşli çarşamba gününde. 

Soyut sınıf (Abstract Class) ve Polymorphism (Çok Biçimlilik) ile alan ve çevre hesaplamalarının üstesinden gelmek ve işimi kolaylaştırmak aklımdan geçti. Çok biçimlilik ile sahiden işler çok kolaylaştı. Tabi bu arada dönüştürme işlemlerim kolaylaşsın diye bir tane genişleme metodu eklemeyi ihmal etmedim. İşte bunlar hep tembellik. Bu nedenle işlemlerin üstünde görülen **ToDouble(true)** metodu ben buradayım diye bağırıyor. Her şey bir yana özellikle ödev için buraya gelenlere fikir verecek cinsten bir çalışma oldu. Hayrını görün. Yaptım Oldu. Büyükşehir çalışıyor. Sakın ola program kodları çok uzamış goygoyu yapmayın. Programa ileride yeni şekil ekleyince görürüm sizi. Hiç efor sarf etmeden eklemeyi yapınca anlarsınız Çok Biçimliliğin gücünü. Programın o çok ama çok bilindik özelliklerine gelecek olursak;

- Üçgenin alan, kare, dikdörtgen ve çemberin alan ve çevre hesaplarını yapabilme.

{:.tablo-ortali}
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.08-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 24c965f0eba398fdaeaa6be54a1b6113 | **MD5**: c0475f138da582f1aae46ba47c1ef1d6 | 
| **Boyut**: 46.3 KB                       | **Boyut**: 421.0 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir (Dropbox)**: [Link](https://www.dropbox.com/s/sbjiz659xwohoeb/alan-cevre-hesaplayici.zip?dl=1) <br> **İndir (OneDrive)**: [Link](https://1drv.ms/u/s!Amxylb8Jtc0Ym16F88KNuOF0NxWB?e=EFyv02) | **İndir**: [Link](https://www.dropbox.com/s/4wq2lfj9ztx88kz/alan-cevre-hesaplayici-proje.zip?dl=1)                      |

**Ek** : Hesaplamaların nasıl yapıldığını görmeye gelenler için **Sekil.cs** ve bu sınıfla alakalı kodlar:

```csharp
using System.Text;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    public abstract class Sekil
    {
        protected double Alan { get; set; }
        protected double Cevre { get; set; }
        protected StringBuilder Sonuc { get; } = new StringBuilder();

        public abstract string Formul();
    }
}
```
<br>
```csharp
using Alan_Cevre_Hesaplayici.Geometri;

namespace Alan_Cevre_Hesaplayici
{
    // Kullanıcıya 4 şekilden birini seçmeye zorla
    // Seçilen sınıfa göre ilgili sınıftaki Formül'ü işlet
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
}
```
<br>
```csharp
using System;
using Alan_Cevre_Hesaplayici.Araclar;

namespace Alan_Cevre_Hesaplayici.Geometri
{
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
}
```
<br>
```csharp
using Alan_Cevre_Hesaplayici.Araclar;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    class Dikdortgen : Sekil
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
}
```
<br>
```csharp
using System;
using Alan_Cevre_Hesaplayici.Araclar;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    class Kare : Sekil
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
}
```
<br>
```csharp
using Alan_Cevre_Hesaplayici.Araclar;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    class Ucgen : Sekil
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