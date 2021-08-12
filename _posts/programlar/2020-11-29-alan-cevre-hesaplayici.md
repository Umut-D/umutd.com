---
layout: post
title: Alan Çevre Hesaplayıcı
date: 2020-11-29 19:43 +0300
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
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.1-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **Boyut**: 46 KB                       | **Boyut**: 259 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/sbjiz659xwohoeb/alan-cevre-hesaplayici.zip?dl=1) | **İndir**: [Link](https://www.dropbox.com/s/4wq2lfj9ztx88kz/alan-cevre-hesaplayici-proje.zip?dl=1) |

**Ek** : Hesaplamaların nasıl yapıldığını görmeye gelenler için **Geometri.cs** ve bu sınıftan kalıtım alınan sınıflardaki kodlar:

```csharp
using System.Text;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    public abstract class Geometri
    {
        public double Alan { get; set; }
        public double Cevre { get; set; }
        public StringBuilder Bilgi { get; set; } = new StringBuilder();

        protected abstract void Formul();
        public abstract StringBuilder Sonuc();
    }
}
```
<div id="ara"></div>

```csharp
using System;
using System.Text;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    public class Cember : Geometri
    {
        private readonly double _yaricap;

        public Cember(string yaricap)
        {
            _yaricap = yaricap.ToDouble();
        }

        protected override void Formul()
        {
            Cevre = 2 * Math.PI * _yaricap;
            Alan = Math.PI * Math.Pow(_yaricap, 2);
        }

        public override StringBuilder Sonuc()
        {
            Formul();

            Bilgi.AppendLine(@"Çemberin Alanı (cm) = " + Alan.ToString("##.####"));
            Bilgi.Append(@"Çemberin cevresi (cm) = " + Cevre.ToString("##.####"));
            return Bilgi;
        }
    }
}
```
<div id="ara"></div>

```csharp
using System.Text;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    public class Dikdortgen : Geometri
    {
        private readonly double _kisaKenar;
        private readonly double _uzunKenar;

        public Dikdortgen(string kisaKenar, string uzunKenar)
        {
            _kisaKenar = kisaKenar.ToDouble();
            _uzunKenar = uzunKenar.ToDouble();
        }

        protected override void Formul()
        {
            Cevre = (_kisaKenar + _uzunKenar) * 2;
            Alan = _kisaKenar * _uzunKenar;
        }

        public override StringBuilder Sonuc()
        {
            Formul();

            Bilgi.AppendLine(@"Dikdörtgenin Alanı (cm) = " + Alan);
            Bilgi.Append(@"Dikdörtgenin Çevresi (cm) = " + Cevre);
            return Bilgi;
        }
    }
}
```
<div id="ara"></div>

```csharp
using System;
using System.Text;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    public class Kare : Geometri
    {
        private readonly double _kareKenar;

        public Kare(string kareKenar)
        {
            _kareKenar = kareKenar.ToDouble();
        }

        protected override void Formul()
        {
            Cevre = _kareKenar * 4;
            Alan = Math.Pow(_kareKenar, 2);
        }

        public override StringBuilder Sonuc()
        {
            Formul();

            Bilgi.AppendLine(@"Karenin Alanı (cm) = " + Alan);
            Bilgi.Append(@"Karenin Çevresi (cm) = " + Cevre);
            return Bilgi;
        }
    }
}
```
<div id="ara"></div>

```csharp
using System.Text;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    public class Ucgen : Geometri
    {
        private readonly double _yukseklik;
        private readonly double _ucgenKenar;

        public Ucgen(string ucgenKenar, string yukseklik)
        {
            _ucgenKenar = ucgenKenar.ToDouble();
            _yukseklik = yukseklik.ToDouble();
        }

        protected override void Formul()
        {
            Alan = _ucgenKenar * _yukseklik / 2;
        }

        public override StringBuilder Sonuc()
        {
            Formul();

            Bilgi.Append(@"Üçgenin Alanı (cm) = " + Alan);
            return Bilgi;
        }
    }
}
```