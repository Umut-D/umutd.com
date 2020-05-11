---
layout: post
title: Alan Çevre Hesaplayıcı
date: 2019-12-22 19:43 +0300
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
| Alan Çevre Hesaplayıcı<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.09-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Alan Çevre Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: f64a925fc6b3a0645e41d6198e45a657 | **MD5**: edd7879261a9189ba040d0e88f491006 | 
| **Boyut**: 46.2 KB                       | **Boyut**: 254.0 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir (Dropbox)**: [Link](https://www.dropbox.com/s/sbjiz659xwohoeb/alan-cevre-hesaplayici.zip?dl=1) <br> **İndir (Google Drive)**: [Link](https://drive.google.com/uc?id=1EuXF5Nnf4X91ebhQbTspRYwBzXisHwRz&export=download) | **İndir**: [Link](https://www.dropbox.com/s/4wq2lfj9ztx88kz/alan-cevre-hesaplayici-proje.zip?dl=1)                      |

**Ek** : Hesaplamaların nasıl yapıldığını görmeye gelenler için **Sekil.cs** ve bu sınıftan kalıtım alınan sınıflardaki kodlar:

```csharp
using System.Text;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    public abstract class Geometri
    {
        protected double Alan { get; set; }
        protected double Cevre { get; set; }
        protected StringBuilder Sonuc { get; } = new StringBuilder();

        public abstract string Hesapla();
    }
}
```
<br>
```csharp
using System;
using Alan_Cevre_Hesaplayici.Araclar;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    class Cember : Geometri
    {
        private readonly double _yaricap;

        public Cember(string yaricap)
        {
            _yaricap = yaricap.ToDouble(true);
        }

        private void CemberFormul()
        {
            Cevre = 2 * Math.PI * _yaricap;
            Alan = Math.PI * Math.Pow(_yaricap, 2);
        }

        private string CemberSonuc()
        {
            Sonuc.AppendLine(@"Çemberin Alanı (cm) = " + Alan.ToString("##.####"));
            Sonuc.Append(@"Çemberin cevresi (cm) = " + Cevre.ToString("##.####"));
            return Sonuc.ToString();
        }

        public override string Hesapla()
        {
            CemberFormul();
            return CemberSonuc();
        }
    }
}
```
<br>
```csharp
using Alan_Cevre_Hesaplayici.Araclar;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    class Dikdortgen : Geometri
    {
        private readonly double _kisaKenar;
        private readonly double _uzunKenar;

        public Dikdortgen(string kisaKenar, string uzunKenar)
        {
            _kisaKenar = kisaKenar.ToDouble(true);
            _uzunKenar = uzunKenar.ToDouble(true);
        }

        private void DikdortgenFormul()
        {
            Cevre = (_kisaKenar + _uzunKenar) * 2;
            Alan = _kisaKenar * _uzunKenar;
        }

        private string DikdortgenSonuc()
        {
            Sonuc.AppendLine(@"Dikdörtgenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Dikdörtgenin Çevresi (cm) = " + Cevre);
            return Sonuc.ToString();
        }

        public override string Hesapla()
        {
            DikdortgenFormul();
            return DikdortgenSonuc();
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
    class Kare : Geometri
    {
        private readonly double _kareKenar;

        public Kare(string kareKenar)
        {
            _kareKenar = kareKenar.ToDouble(true);
        }

        private void KareFormul()
        {
            Cevre = _kareKenar * 4;
            Alan = Math.Pow(_kareKenar, 2);
        }

        private string KareSonuc()
        {
            Sonuc.AppendLine(@"Karenin Alanı (cm) = " + Alan);
            Sonuc.Append(@"Karenin Çevresi (cm) = " + Cevre);

            return Sonuc.ToString();
        }

        public override string Hesapla()
        {
            KareFormul();
            return KareSonuc();
        }
    }
}
```
<br>
```csharp
using Alan_Cevre_Hesaplayici.Araclar;

namespace Alan_Cevre_Hesaplayici.Geometri
{
    class Ucgen : Geometri
    {
        private readonly double _yukseklik;
        private readonly double _ucgenKenar;

        public Ucgen(string ucgenKenar, string yukseklik)
        {
            _ucgenKenar = ucgenKenar.ToDouble(true);
            _yukseklik = yukseklik.ToDouble(true);
        }

        private void UcgenFormul()
        {
            Alan = _ucgenKenar * _yukseklik / 2;
        }

        private string UcgenSonuc()
        {
            Sonuc.Append(@"Üçgenin Alanı (cm) = " + Alan);
            return Sonuc.ToString();
        }

        public override string Hesapla()
        {
            UcgenFormul();
            return UcgenSonuc();
        }
    }
}
```