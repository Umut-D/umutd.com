---
layout: post
title: TC Kimlik No
date: 2019-11-04 12:43 +0300
categories: Programlar
tags: Kimlik No, TC Kimlik, TC Kimlik No, TC Kimlik No Algoritması, TC Kimlik Numarası
excerpt: Türkiye Cumhuriyeti Kimlik Numarasının algoritması çözüleli ve internette paylaşılalı çok oldu. Gerekli gereksiz her haltı C#’da yazmaya çalışmak isteyen biri olarak TC Kimlik Numarası algoritmasını anladıktan sonra bu işe de balıklama atladım....
redirect_from:
  - /programlar/tc-kimlik-no/
  - /etiket/tc-kimlik-no-algoritmasi/
  - /etiket/tc-kimlik/
---
{:.uyari}
Bu program sadece TC Kimlik No algoritmasını C# programlama dilinde uygulanması maksadıyla yazılmıştır. Kullanıcılara doğru TC Kimlik Numaraları sunarken -kaynak kodlarından da görüleceği üzere- kullanıcıdan **herhangi bir bilgi asla sızdırmamaktadır**.

> **TC Kimlik Numarası**, Nüfus ve Vatandaşlık İşleri Genel Müdürlüğü’nün uzun yıllardır yürüttüğü Mernis uygulamasının hayata geçmesiyle her vatandaşın nüfus cüzdanında bulunan, 11 haneli numaradır. 

![tc-kimlik-no](/images/programlar/tc-kimlik-no.png){: width="30%"}

 Türkiye Cumhuriyeti Kimlik Numarasının algoritması çözüleli ve internette paylaşılalı çok oldu. Gerekli gereksiz her haltı C#’da yazmaya çalışmak isteyen biri olarak TC Kimlik Numarası algoritmasını anladıktan sonra bu işe de balıklama atladım. Kodları adım adım kurgulasam da, kodları biraz uzattığımın farkındayım. Dizileri (özellikle char) kullanarak çözüm üretsem belki daha az satır sürecekti ama geri dönmek istemedim. Eğer adımlara dikkat ederseniz algoritmanın işlenişi ve kontrolünü siz de kolaylıkla anlayacaksınız.

Eğer programın ürettiği numaralara güvenmediyseniz sorun değil. Üretilen TC Kimlik Numaralarının doğrulamasını nette yer alan ilgili pek çok siteden kolayca yapabilirsiniz. Sorun olmayacaktır. Programın özelliklerine gelecek olursak;

- Aynı anda maksimum 100 adet TC Kimlik Numarası oluşturma,
- Oluşturulan TC kimlik numaralarını metin belgesi olarak- kaydetme,
- TC Kimlik Numarası kontrolü.

{:.tablo-ortali}
| TC Kimlik No<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.1-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | TC Kimlik No (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Sonlandırıldı-lightgray.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: c80bd7422944d5fdde70ad5f1a3a2abc | **MD5**: | 431b081ebe204ba50e517f41cbe47580
| **Boyut**: 88.9 KB                       | **Boyut**: 786.0 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/cqas7tsm6q5as2j/tc-kimlik-no.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/6smrlz98wnehow8/tc-kimlik-no-proje.zip?dl=1)                      |

**Ek** : Algoritmanın nasıl işlediğini görmeye gelenler için **Islemler.cs** sınıfındaki kodlar (**Hesapla** metodunda):

```csharp
using System;
using System.Windows.Forms;

namespace TcKimlikNo
{
    class Islemler
    {
        private string _tcKimlikNo = "";
        private int _onuncuBasamak, _onBirinciBasamak;
        private int _tekBasamaklar, _ciftBasamaklar;

        // I. Girilen TC kimlik numarasını kontrol et
        public void Kontrol(string girilenTcKimlikNo)
        {
            // Girilen numaranın ilk dokuz hanesini al (Son iki hanenin doğruluğunu program hesaplayacak)
            _tcKimlikNo = girilenTcKimlikNo.Substring(0, 9);

            Hesapla();

            // 7) 10. ve 11. basamağı hesaplanıp yeniden oluşturulan numarayla, sisteme girileni karşılaştır
            if (_tcKimlikNo == girilenTcKimlikNo)
                MessageBox.Show(@"TC Kimlik Numarası doğru.", @"Sonuç", MessageBoxButtons.OK, MessageBoxIcon.Information);
            else
                MessageBox.Show(@"TC Kimlik Numarası yanlış.", @"Hata", MessageBoxButtons.OK, MessageBoxIcon.Error);

            DegerleriSifirla();
        }

        // II. Rastgele TC kimlik numaraları oluştur
        public object[] Olustur(decimal nupDeger)
        {
            Random rastgeleSayi = new Random();
            object[] tcKimlikNumaralari = new object[(int) nupDeger];

            for (int j = 0; j < nupDeger; j++)
            {
                DegerleriSifirla();

                // İlk dokuz haneyi kafana göre oluştur
                for (int i = 0; i < 9; i++)
                    _tcKimlikNo += rastgeleSayi.Next(1, 10);

                Hesapla();

                tcKimlikNumaralari[j] = _tcKimlikNo;
            }

            return tcKimlikNumaralari;
        }

        // *** TC kimlik numarasını oluşturan/hesaplayan algoritma
        private void Hesapla()
        {
            // 1) 1, 3, 5, 7 ve 9. sıradaki rakamın toplamının 7 katı 
            for (int i = 0; i < 9; i += 2)
                _tekBasamaklar += int.Parse(_tcKimlikNo.Substring(i, 1)) * 7;

            // 2) 2, 4, 6 ve 8.rakamın toplamının 9 katını topla
            for (int i = 1; i < 9; i += 2)
                _ciftBasamaklar += int.Parse(_tcKimlikNo.Substring(i, 1)) * 9;

            // 3) Çıkan sonucun birler basamağı 10. rakamı veriyor
            _onuncuBasamak = (_tekBasamaklar + _ciftBasamaklar) % 10;

            // 4) Hesaplanan 10. basamağı, 9 basamağı oluşturan Tc kimlik numarasına ekle
            _tcKimlikNo += _onuncuBasamak;

            // 5) ilk 10 rakamın toplamının birler basamağı 11. rakamı veriyor
            for (int i = 0; i < 10; i++)
                _onBirinciBasamak += int.Parse(_tcKimlikNo.Substring(i, 1));
            _onBirinciBasamak %= 10;

            // 6) Elde edilen ilk 10 ve 11. haneyi birleştirip diziye ekle
            _tcKimlikNo += _onBirinciBasamak;
        }

        // Diğer kullanımlar için değişkenleri sıfırla
        private void DegerleriSifirla()
        {
            _tcKimlikNo = "";
            _tekBasamaklar = 0;
            _ciftBasamaklar = 0;
            _onuncuBasamak = 0;
            _onBirinciBasamak = 0;
        }
    }
}
```