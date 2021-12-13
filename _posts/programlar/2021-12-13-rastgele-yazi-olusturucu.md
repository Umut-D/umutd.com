---
layout: post
title: Rastgele (Lorem Ipsum) Yazı Oluşturucu
date: 2021-12-13 04:43 +0300
categories: Programlar
tags: Lorem Ipsum, Rastgele Yazı, Rastgele Yazı Oluşturucu
excerpt: Çoğunlukla bir iş için lazım olduğunda program yazmaya kasan biri olarak bu sefer de rastgele yazı oluşturmak için program yazayım dedim. Kah Photoshop’ta, kah Dreamweaver’da, kah Notepad++’da bazen uzun ve anlamsız metinlere ihtiyaç duyduğumda "buraya yazı gelecek" yazmaktan tiksineli çok olduğundan beri yardımıma hep Lorem Ipsum metinleri (ebnebiler dummy text de diyebiliyor) yetişti. 
redirect_from:
  - /programlar/rastgele-yazi-olusturucu/
  - /etiket/rastgele-yazi-olusturucu/
---
> Lorem Ipsum, masaüstü yayıncılık ve basın yayın sektöründe kullanılan taklit yazı bloğu olarak tanımlanır. Lipsum, oluşturulacak şablon ve taslaklarda içerik yerine geçerek yazı bloğunu doldurmak için kullanılır. Lipsum, 1500’lerin başlarında bir matbaacının font model kitabı oluşturmak için, bir yazı tipi kütüphanesindeki harflerin sıralamasını bozarak yerleştirdiğinden bu yana endüstri standardı haline gelmiştir. (Vikipedi)

![rastgele-yazi](/images/programlar/rastgele-yazi.png){: width="39%"}

Çoğunlukla bir iş için lazım olduğunda program yazmaya kasan biri olarak bu sefer de rastgele yazı oluşturmak için program yazayım dedim. Kah Photoshop’ta, kah Dreamweaver’da, kah Notepad++’da bazen uzun ve anlamsız metinlere ihtiyaç duyduğumda "buraya yazı gelecek" yazmaktan tiksineli çok olduğundan beri yardımıma hep Lorem Ipsum metinleri (ebnebiler dummy text de diyebiliyor) yetişti. 

Bu türde koftiden yazılar üretmek için çeşitli programlar için çok çeşitli plug-in’ler var. Ancak ben artık kendim pişirip yiyeyim deyince ortaya böyle bir program çıktı. Bu basit programı uzun uzadıya anlatmanın alemi yok, programın yegane özelliği; Maksimum 30 paragraf, (paragraf içinde) 30 cümle, (cümle içinde) 30 kelime ile rastgele Lorem Ipsum metinleri oluşturmak. Hepsi bu. Maksat laneydain yazı oluşturmak işte.

{:.tablo-ortali}
| Rastgele (Lorem Ipsum) Yazı Oluşturucu<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.2-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Rastgele (Lorem Ipsum) Yazı Oluşturucu (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **Boyut**: 49.7 KB                       | **Boyut**:  70.3 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir (Dropbox)**: [Link](https://www.dropbox.com/s/c4nclpc6npc2a1s/rastgele-yazi-olusturucu.zip?dl=1) | **İndir**: [Link](https://www.dropbox.com/s/ohs0fu3rhindjk3/rastgele-yazi-olusturucu-proje.zip?dl=1) |


**Ek** : Algoritmanın nasıl işlediğini görmeye gelenler için **LoremIpsum.cs** sınıfındaki kodlar hizmetinizde;

```csharp
using System;
using System.Globalization;
using System.Text;

namespace RastgeleYaziOlusturucu
{
    public class LoremIpsum
    {
        public int ParagrafSayisi { get; set; }
        public int CumleSayisi { get; set; }
        public int KelimeSayisi { get; set; }
        private readonly Kelime _kelime;
        private readonly StringBuilder _yazi;
        private readonly Random _rastgele;

        public LoremIpsum(Kelime kelime)
        {
            _kelime = kelime;

            _rastgele = new Random();
            _yazi = new StringBuilder();
        }

        public string Olustur(bool kelimeyeGoreMi)
        {
            ParagrafOlustur(kelimeyeGoreMi);

            return _yazi.ToString();
        }

        private void ParagrafOlustur(bool kelimeyeGoreMi)
        {
            for (int sira = 0; sira < ParagrafSayisi; sira++)
            {
                SatirEkle(sira);

                CumleOlustur(kelimeyeGoreMi);
            }
        }

        private void SatirEkle(int i)
        {
            if (i >= 1)
                _yazi.AppendLine(Environment.NewLine);
        }

        private void CumleOlustur(bool kelimeyeGoreMi)
        {
            for (int sira = 0; sira < CumleSayisi; sira++)
            {
                if (kelimeyeGoreMi)
                    KelimeSayisi = _rastgele.Next(1, 11);

                KelimeleriOlustur();
            }
        }

        private void KelimeleriOlustur()
        {
            for (int sira = 0; sira < KelimeSayisi; sira++)
            {
                int toplamKelimeSayisi = _kelime.Kelimeler.Count;

                IlkHarfiBuyut(sira, toplamKelimeSayisi);
                KelimeEkle(toplamKelimeSayisi);
                NoktaKoy(sira);
            }
        }

        private void IlkHarfiBuyut(int sira, int toplamKelimeSayisi)
        {
            if (sira == 0)
            {
                // i harfleri başta iken İ olmasın diye kültürü en-US yaptım
                var yaziBilgi = new CultureInfo("en-US", false).TextInfo;
                _yazi.Append($"{yaziBilgi.ToTitleCase(RastgeleKelimeOlustur(toplamKelimeSayisi))} ");
            }
        }

        private string RastgeleKelimeOlustur(int toplamKelimeSayisi)
        {
            return _kelime.Kelimeler[_rastgele.Next(1, toplamKelimeSayisi)];
        }

        private void KelimeEkle(int toplamKelimeSayisi)
        {
            _yazi.Append($"{RastgeleKelimeOlustur(toplamKelimeSayisi)} ");
        }

        private void NoktaKoy(int sira)
        {
            if (sira == KelimeSayisi - 1)
            {
                _yazi.Length -= 1;
                _yazi.Append(@". ");
            }
        }
    }
}
```