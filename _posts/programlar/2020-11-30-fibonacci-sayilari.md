---
layout: post
title: Fibonacci Sayıları
date: 2020-11-30 20:43 +0300
categories: Programlar
tags: Fibonacci, Fibonacci Dizisi, Fibonacci Sayıları, İteratif, Recursive
excerpt: Algoritma derslerinin vazgeçilmezi Fibonacci Sayıları/Dizisi… Bildiğiniz üzere Fibonacci Sayıları, her sayının kendinden öncekiyle toplanması sonucu oluşan bir sayı dizisi...
redirect_from:
  - /programlar/fibonacci-sayilari/
  - /etiket/fibonacci-sayilari/
---
> **Fibonacci Sayı** dizisi, kendinden önceki iki ardışık sayının toplamının kendisinden sonraki sayıya eşit olmasıdır. Yani her sayı kendisinden önce gelen iki sayının toplamıdır. Örneğin; 0, 1, 1, 2, 3, 5, 8, 13, 21...

![fibonacci-sayilari](/images/programlar/fibonacci-sayilari.png){: width="33%"}

Algoritma derslerinin vazgeçilmezi Fibonacci Sayıları/Dizisi… Bildiğiniz üzere Fibonacci Sayıları, her sayının kendinden öncekiyle toplanması sonucu oluşan bir sayı dizisi.

Bilgisayarla ilgili bir bölüm okuyup Fibonacci Sayılarına, Iterative (Döngü) ve Recursive (Özyinelemeli) yaklaşımın bu güzide örneğine dair ödev yapmayan öğrenci yok denecek kadar azdır. Ben de üşenmedim, bu konu ve yaklaşıma dair ödevlerde kullanabileceğiniz, fikir alabileceğiniz, kaynak kodlarını kendinize mal edebileceğiniz bir program yazdım. Zira iteratif ve recursif yaklaşımla program çatır çatır çalışıyor ve rekursif yaklaşımının biraz daha yavaş olduğu çıplak gözle görülebiliyor. Zımbırtının özelliklerine gelecek olursak;

- Iterative (Döngü) ve Recursive (Özyinelemeli)- yaklaşımıyla işlem yapabilme,
- StopWatch özelliği ile işlem süresini milisaniye- düzeyinde hesaplama,
- Lazım olur diye(!) metin belgesi olarak kaydetme.

{:.tablo-ortali}
| Fibonacci Sayıları <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.04-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Fibonacci Sayıları (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **Boyut**:  131 KB                       | **Boyut**:  642 KB                         |
| **Gereksinimler**: .Net Framework 4.0      | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/3v1okk8wypnjwt4/fibonacci-sayilari.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/s1g8ors6gd6s4o8/fibonacci-sayilari-proje.zip?dl=1) |

**Ek** : Sayıların her iki biçimde nasıl hesaplandığını görmeye gelenler için **Fibonacci.cs** sınıfındaki kodlar:

```csharp
using System.Text;
using System.Windows.Forms;

namespace FibonacciSayilari
{
    public class Fibonacci : Zaman
    {
        private int _sayi;

        public int Sayi
        {
            get => _sayi;
            set

            {
                if (value <= 37)
                    _sayi = value;
                else
                {
                    MessageBox.Show(@"Sayıyı abartmasak hoş olmaz mı!", @"Uyarı", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                    _sayi = 0;
                }
            }
        }

        private readonly StringBuilder _sayilar = new StringBuilder();

        public StringBuilder Iteratif(int donguSayisi)
        {
            Zamanlayici.Start();

            IteratifDongu(donguSayisi);
            IteratifSure = Sonlandir();

            return _sayilar;
        }

        // I. yol (Iteratif - Döngü)
        private void IteratifDongu(int donguSayisi)
        {
            int oncekiSayi = 0, sonrakiSayi = 1;
            for (int i = 0; i < donguSayisi; i++)
            {
                int sonuc = oncekiSayi + sonrakiSayi;
                oncekiSayi = sonrakiSayi;
                sonrakiSayi = sonuc;

                _sayilar.Append(sonuc + @"  ");
            }
        }

        private double Sonlandir()
        {
            Zamanlayici.Stop();

            return Zamanlayici.Elapsed.Milliseconds;
        }

        public StringBuilder Recursive(int donguSayisi)
        {
            Sifirla();
            Zamanlayici.Start();

            for (int i = 1; i <= donguSayisi; i++)
                _sayilar.Append(RecursiveDongu(i) + @"  ");

            RecursiveSure = Sonlandir();

            return _sayilar;
        }

        // II. yol (Recursive - Özyinelemeli)
        private int RecursiveDongu(int donguSayisi)
        {
            if (donguSayisi <= 1)
                return 1;

            return RecursiveDongu(donguSayisi - 1) + RecursiveDongu(donguSayisi - 2);
        }

        private void Sifirla()
        {
            Zamanlayici.Reset();
            _sayilar.Clear();
        }
    }
}
```