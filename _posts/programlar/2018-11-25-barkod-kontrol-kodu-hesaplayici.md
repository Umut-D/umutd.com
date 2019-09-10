---
layout: post
title: Barkod Kontrol Kodu Hesaplayıcı
date: 2018-11-25 12:43 +0300
categories: Programlar
tags: Barkod, Barkod Kontrol Kodu Hesaplayıcı, EAN-13, Kontrol Kodu
redirect_from:
  - /programlar/barkod-kontrol-kodu-hesaplayici/
  - /c/barkod-kontrol-kodu/
  - /etiket/barkod-kontrol-kodu-hesaplayici/
---
![iban-kontrol](/images/programlar/barkod-kontrol-kodu-hesaplayici.png){: width="29%"}

C#'da yazdığım en gereksiz program olma konusunda şampiyonluğa oynayan program. *EAN-13* için Barkod Kodu Kontrolörü. Her gün satın aldığınız ürünlerin barkod kısımlarında yazan rakamlarda, 13. sıradaki son rakam öndeki 12 sayının hesabına dayanan bir kontrol numarasıdır. İşte bu dandik program o numara kontrolünü yapıyor. Peki bunun size, dünyaya, kainata ne faydası var? “Zaten kontrol numarası 13. hanede yazıyormuş, neden bir de buradan kontrol edelim” diyorsanız cevabı ben de bilmiyorum. Aklıma geldi, kontrol numarası hesaplama matematiğini C#'a aktarmak istedim.

Kırk yıl düşünsem böyle bir program yazacağım aklıma gelmezdi. Sene içinde anlattığım Lojistik Bilgi Sistemleri dersinde barkod konusu ve anlatılan konulardan biri Türkiye ve Avrupa'da kullanılan EAN-13 Barkod Kodu olduğu için buradaki matematik ilgimi çekti. Özelliklerine gelecek olursak;

- Etrafınızda barkod kodu 13 haneli her ürünün (EAN-13 kodludur) son kontrol numarasını bulma.

{:.tablo-ortali}
| Barkod Kontrol Kodu Hesaplayıcı <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.01-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Barkod Kontrol Kodu Hesaplayıcı (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: d673de3180c4ab7f1905fd7640b2eed5 | **MD5**: dae800022863034aff232c3e98922378 | 
| **Boyut**: 14.7 KB                       | **Boyut**: 118.9 KB                         |
| **Gereksinimler**: .Net Framework 3.5     | **Gereksinimler**: .Net Framework 3.5     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/93tchxtsr3j2dng/barkod-kontrol-kodu.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/i7sn079af43czh9/barkod-kontrol-kodu-proje.zip?dl=1)                      |

**Ek** : Kontrol kodunun nasıl hesaplandığını görmeye gelenler için **Barkod.cs** sınıfındaki kodlar:

```csharp
using System;
using System.Collections.Generic;
 
namespace BarkodKontrolKodu
{
    public class Barkod
    {
        public static int Kontrol(string barkod)
        {
            List<char> dizi = new List<char>(barkod.ToCharArray());
 
            // 1.Adım: Barkod rakamının çift haneleri toplanır. 6+7+4+1+0+3=21
            int ciftToplam = 0;
            for (int i = 1; i < barkod.Length; i += 2)
                ciftToplam += (int) Char.GetNumericValue(dizi[i]);
 
            // 2. 1.adımda çıkan sayı 3 ile çarpılır. 21*3=63
            ciftToplam *= 3;
 
            // 3. Barkod rakamının tek haneleri toplanır. 8+9+5+3+7+0=32
            int tekToplam = 0;
            for (int i = 0; i < barkod.Length; i += 2)
                tekToplam += (int) Char.GetNumericValue(dizi[i]);
 
            // 4.Adım: 2 inci adımda elde edilen sayı ile 3 üncü adımda elde edilen sayı toplanır. 63+32=95
            int tekCiftToplam = ciftToplam + tekToplam;
 
            // 5.Adım: 4.adımda elde edilen sayı (yukarıda 95 sayısı) kendisinden büyük 10 u katı olan 100 den çıkartılır.100-95=5
            int yukariYuvarla = 10 * ((tekCiftToplam + 9) / 10);
            
            // Sonuç: 6.ncı adımda elde edilen sayı (yukarıda 5 olarak elde edilmiş) kontrol basamağı (Check Digit) rakamıdır
            return yukariYuvarla - tekCiftToplam;
        }
    }
}
```