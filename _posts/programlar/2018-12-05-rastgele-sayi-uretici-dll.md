---
layout: post
title: Rastgele Sayı Üretici (DLL)
date: 2018-12-05 12:43 +0300
categories: Programlar
tags: DLL, Farklı Sayı, Random Sayı, Rastgele Sayı
---
![rastgele-sayi-uretici-dll](/images/programlar/rastgele-sayi-uretici-dll.png){:.resim-ortali}

Çok fazla anlatmaya gerek yok. Rastgele Sayı Üretici programının ayrı olarak hazırladığım DLL dosyası. Bu DLL dosyasını C# projenize entegre ederek rastgele sayılar üretip, kendi projenizde kolayca kullanabilirsiniz. DLL’nin Generic List halinde sayı(lar) döndürdüğünü belirteyim. DLL'nin basit özelliklerine gelecek olursak;

- İstenilen sayı aralıklarında ve belirtilen adet kadar rastgele sayı üretme,
- İstenilen sayı aralıklarında ve belirtilen adet kadar benzersiz rastgele sayı üretme.


{:.tablo-ortali}
| Rastgele Sayı Üretici (DLL) <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele Sayı Üretici (DLL) (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 967886479b5afe7677e19cf152846d59 | **MD5**: 2b70ae582fbf2f89478ba81220627a70 | 
| **Boyut**: 5.1 KB                       | **Boyut**:  28.8 KB                         |
| **Gereksinimler**: .Net Framework 4.0     | **Gereksinimler**: .Net Framework  4.0    |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/rastgele-sayi-dll.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/rastgele-sayi-dll-proje.zip)                      |

**Ek** : Rastgele sayıların nasıl üretildiğini görmeye gelenler için **RastgeleSayiOlustur.dll** kodları:

```csharp
using System;
using System.Collections.Generic;
 
namespace RastgeleSayiOlustur
{
    /// <summary>
    /// Rastgele Sayı oluşturma sınıfı
    /// </summary>
    public class RastgeleSayi
    {
        private int _kucukSayi;
        private int _buyukSayi;
        private int _adet;
        private int _fark;
        private Random Sayi { get; } = new Random();
        private List<int> Sayilar { get; } = new List<int>();
 
        private int KucukSayi
        {
            get { return _kucukSayi; }
            set
            {
                if (value < 10000)
                    _kucukSayi = value;
                else
                    throw new Exception("Girilen değer 10.000'den büyük olmamalı!");
            }
        }
 
        private int BuyukSayi
        {
            get { return _buyukSayi; }
            set
            {
                if (value <= 10000 && _kucukSayi < value)
                    _buyukSayi = value + 1;
                else
                    throw new Exception("Girilen değer 10.000'den büyük olmamalı veya küçük sayıdan büyük olmalı!");
            }
        }
 
        private int Adet
        {
            get { return _adet; }
            set
            {
                if (value <= 10000 && _adet < value)
                    _adet = value;
                else
                    throw new Exception("Girilen değer 10.000'den büyük olmamalı!");
            }
        }
 
        private int Fark
        {
            set
            {
                if (value == Adet || Adet < value)
                    _fark = value;
                else
                    throw new Exception("Benzersiz olarak üretilen sayılar Büyük Sayı ile Küçük Sayı farkından fazla olamaz!");
            }
        }
 
        /// <summary>
        /// Küçük sayı, Büyük sayı ve Adet değişkenlerini alarak rastgele sayıları geri döndürür.
        /// </summary>
        public List<int> Olustur(int kucukSayi, int buyukSayi, int adet)
        {
            KucukSayi = kucukSayi;
            BuyukSayi = buyukSayi;
            Adet = adet;
 
            for (int i = 0; i < adet; i++)
            {
                int olusturulanSayi = Sayi.Next(KucukSayi, BuyukSayi);
                Sayilar.Add(olusturulanSayi);
            }
 
            return Sayilar;
        }
 
        /// <summary>
        /// Küçük sayı, Büyük sayı ve Adet değişkenlerini alarak rastgele ve benzersiz sayıları geri döndürür.
        /// </summary>
        public List<int> BenzersizOlustur(int kucukSayi, int buyukSayi, int adet)
        {
            KucukSayi = kucukSayi;
            BuyukSayi = buyukSayi;
            Adet = adet;
            // Fark değişkeninin durumuna göre devam et veya etme
            // Eğer Büyük, Küçük sayılar arasındaki fark, adetten büyükse işlemi sonlandır
            Fark = BuyukSayi - KucukSayi;
 
            for (int i = 0; i < Adet; i++)
            {
                int olusturulanSayi = Sayi.Next(KucukSayi, BuyukSayi);
 
                if (!Sayilar.Contains(olusturulanSayi))
                    Sayilar.Add(olusturulanSayi);
                else
                    i--;
            }
 
            return Sayilar;
        }
    }
}
```

