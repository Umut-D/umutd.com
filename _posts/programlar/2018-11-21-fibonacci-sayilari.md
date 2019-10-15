---
layout: post
title: Fibonacci Sayıları
date: 2018-11-21 12:43 +0300
categories: Programlar
tags: Fibonacci, Fibonacci Dizisi, Fibonacci Sayıları, İteratif, Recursive
redirect_from:
  - /programlar/fibonacci-sayilari/
  - /etiket/fibonacci-sayilari/
---
![fibonacci-sayilari](/images/programlar/fibonacci-sayilari.png){: width="33%"}

Algoritma derslerinin vazgeçilmezi Fibonacci Sayıları/Dizisi… Bildiğiniz üzere Fibonacci Sayıları, her sayının kendinden öncekiyle toplanması sonucu oluşan bir sayı dizisi.

Bilgisayarla ilgili bir bölüm okuyup Fibonacci Sayılarına, Iterative (Döngü) ve Recursive (Özyinelemeli) yaklaşımın bu güzide örneğine dair ödev yapmayan öğrenci yok denecek kadar azdır. Ben de üşenmedim, bu konu ve yaklaşıma dair ödevlerde kullanabileceğiniz, fikir alabileceğiniz, kaynak kodlarını kendinize mal edebileceğiniz bir program yazdım. Zira iteratif ve recursif yaklaşımla program çatır çatır çalışıyor ve rekursif yaklaşımının biraz daha yavaş olduğu çıplak gözle görülebiliyor. Zımbırtının özelliklerine gelecek olursak;

- Iterative (Döngü) ve Recursive (Özyinelemeli)- yaklaşımıyla işlem yapabilme,
- StopWatch özelliği ile işlem süresini milisaniye- düzeyinde hesaplama,
- Lazım olur diye(!) metin belgesi olarak kaydetme.

{:.tablo-ortali}
| Fibonacci Sayıları <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.02-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Fibonacci Sayıları (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 6da23e3cb3c4733d868c305b90f383e5 | **MD5**: 8ab9a4a11e186ecffa4c18ccc6cd74b9 | 
| **Boyut**:  130.4 KB                       | **Boyut**:  724.5 KB                         |
| **Gereksinimler**: .Net Framework 4.0      | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/3v1okk8wypnjwt4/fibonacci-sayilari.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/s1g8ors6gd6s4o8/fibonacci-sayilari-proje.zip?dl=1)                      |

**Ek** : Sayıların her iki biçimde nasıl hesaplandığını görmeye gelenler için **Fibonacci.cs** sınıfındaki kodlar:

```csharp
using System.Windows.Forms;
 
namespace FibonacciSayilari
{
    public class Fibonacci
    {
        // Değişken tanımlarken, değişkeni "Nullable" tanımlamak aklıma geldi.
        // Eğer girilen değer 37'den büyük ise null değer döndürüp kullanıcıya boş Textbox göster.
        private int? _girilenDeger;
 
        public int? GirilenDeger
        {
            get { return _girilenDeger; }
            set
            {
                if (value <= 37)
                    _girilenDeger = value;
                else
                {
                    MessageBox.Show(@"Abartmasak hoş olmaz mı!", @"Uyarı", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                    _girilenDeger = null;
                }
            }
        }
 
        // I. yol (Iteratif - Döngü)
        public int Iteratif(int gelenSayi)
        {
            int oncekiSayi = 0, sonrakiSayi = 1, sonuc = 1;
 
            for (int i = 0; i < gelenSayi; i++)
            {
                sonuc = oncekiSayi + sonrakiSayi;
                oncekiSayi = sonrakiSayi;
                sonrakiSayi = sonuc;
            }
 
            return sonuc;
        }
 
        // II. yol (Recursive - Özyinelemeli)
        public int Recursive(int gelenSayi)
        {
            if (gelenSayi <= 1)
                return 1;
 
            return Recursive(gelenSayi - 1) + Recursive(gelenSayi - 2);
        }
    }
}
```