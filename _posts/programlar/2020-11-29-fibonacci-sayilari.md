---
layout: post
title: Fibonacci Sayıları
date: 2020-11-29 12:43 +0300
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
| Fibonacci Sayıları <br>![Versiyon](https://img.shields.io/badge/Versiyon-1.03-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | Fibonacci Sayıları (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 61d81fde25ff0016cc4e6bfd45952c08 | **MD5**: 33335b87f0fcf5cba987d6134d2ba6d9 | 
| **Boyut**:  130 KB                       | **Boyut**:  583 KB                         |
| **Gereksinimler**: .Net Framework 4.0      | **Gereksinimler**: .Net Framework 4.0     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/3v1okk8wypnjwt4/fibonacci-sayilari.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/s1g8ors6gd6s4o8/fibonacci-sayilari-proje.zip?dl=1) |

**Ek** : Sayıların her iki biçimde nasıl hesaplandığını görmeye gelenler için **Fibonacci.cs** sınıfındaki kodlar:

```csharp
using System.Windows.Forms;

namespace FibonacciSayilari
{
    public class Fibonacci
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

        // I. yol (Iteratif - Döngü)
        public int Iteratif(int sayi)
        {
            int oncekiSayi = 0, sonrakiSayi = 1, sonuc = 1;
            for (int i = 0; i < sayi; i++)
            {
                sonuc = oncekiSayi + sonrakiSayi;
                oncekiSayi = sonrakiSayi;
                sonrakiSayi = sonuc;
            }

            return sonuc;
        }

        // II. yol (Recursive - Özyinelemeli)
        public int Recursive(int sayi)
        {
            if (sayi <= 1)
                return 1;

            return Recursive(sayi - 1) + Recursive(sayi - 2);
        }
    }
}
```