---
layout: post
title: TC Kimlik No
date: 2020-09-27 12:43 +0300
categories: Programlar
tags: Kimlik No, TC Kimlik, TC Kimlik No, TC Kimlik No Algoritması, TC Kimlik Numarası
excerpt: Türkiye Cumhuriyeti Kimlik Numarasının algoritması çözüleli ve internette paylaşılalı çok oldu. Gerekli gereksiz her haltı C#’da yazmaya çalışmak isteyen biri olarak TC Kimlik Numarası algoritmasını anladıktan sonra bu işe de balıklama atladım....
redirect_from:
  - /programlar/tc-kimlik-no/
  - /etiket/tc-kimlik-no-algoritmasi/
  - /etiket/tc-kimlik/
---
> **TC Kimlik Numarası**, Nüfus ve Vatandaşlık İşleri Genel Müdürlüğü’nün uzun yıllardır yürüttüğü Mernis uygulamasının hayata geçmesiyle her vatandaşın nüfus cüzdanında bulunan, 11 haneli numaradır. 

{:.uyari}
Bu program sadece TC Kimlik No algoritmasını C# programlama dilinde uygulanması maksadıyla yazılmıştır. Kullanıcılara doğru TC Kimlik Numaraları sunarken -kaynak kodlarından da görüleceği üzere- kullanıcıdan **herhangi bir bilgi asla sızdırmamaktadır**.

![tc-kimlik-no](/images/programlar/tc-kimlik-no.png){: width="30%"}

 Türkiye Cumhuriyeti Kimlik Numarasının algoritması çözüleli ve internette paylaşılalı çok oldu. Gerekli gereksiz her haltı C#’da yazmaya çalışmak isteyen biri olarak TC Kimlik Numarası algoritmasını anladıktan sonra bu işe de balıklama atladım. Kodları adım adım kurgulasam da, kodları biraz uzattığımın farkındayım. Dizileri (özellikle char) kullanarak çözüm üretsem belki daha az satır sürecekti ama geri dönmek istemedim. Eğer adımlara dikkat ederseniz algoritmanın işlenişi ve kontrolünü siz de kolaylıkla anlayacaksınız.

Eğer programın ürettiği numaralara güvenmediyseniz sorun değil. Üretilen TC Kimlik Numaralarının doğrulamasını nette yer alan ilgili pek çok siteden kolayca yapabilirsiniz. Sorun olmayacaktır. Programın özelliklerine gelecek olursak;

- Aynı anda maksimum 200 adet TC Kimlik Numarası oluşturma,
- Oluşturulan TC kimlik numaralarını metin belgesi olarak kaydetme,
- TC Kimlik Numarası kontrolü,
- **(İstek üzerine)** Toplu halde TC Kimlik Numarası kontrolü.

{:.tablo-ortali}
| TC Kimlik No<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.2-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | TC Kimlik No (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Arşiv](https://img.shields.io/badge/Arşiv-orange.svg?style=flat)|
|----------------------------------------- -|-------------------------------------------|
| **MD5**: 8d17726ebd2fcf50a45def7522938007 | **MD5**: 0feb595b0b9cf8b3b17a821b4dce4aa2 | 
| **Boyut**: 89.9 KB                       | **Boyut**: 550 KB                         |
| **Gereksinimler**: .Net Framework 4     | **Gereksinimler**: .Net Framework 4     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](https://www.dropbox.com/s/cqas7tsm6q5as2j/tc-kimlik-no.zip?dl=1)         | **İndir**: [Link](https://www.dropbox.com/s/6smrlz98wnehow8/tc-kimlik-no-proje.zip?dl=1)  <br> **GitHub**: [Link](https://github.com/Umut-D/TC-Kimlik-No) |

**Ek** : Algoritmanın nasıl işlediğini görmeye gelenler için **Islem.cs** sınıfındaki kodlar (**Hesapla** metodunda):

```csharp
using System;
using System.Linq;
using System.Reflection;

namespace TcKimlikNo
{
    public class Islem
    {
        private string _tcKimlikNo = "";

        public bool Kontrol(string tcKimlikNo)
        {
            // Girilen numaranın ilk dokuz hanesini al (Son iki hanenin doğruluğunu program hesaplayacak)
            _tcKimlikNo = tcKimlikNo.Substring(0, 9);

            Hesapla();

            if (!Karsilastir(tcKimlikNo))
                return false;

            Sifirla();
            return true;
        }

        public object[] RastgeleOlustur(int adet)
        {
            Random rastgeleSayi = new Random();
            object[] tcKimlikNumaralari = new object[adet];

            for (int j = 0; j < adet; j++)
            {
                Sifirla();

                // İlk dokuz haneyi kafana göre oluştur
                for (int i = 0; i < 9; i++)
                    _tcKimlikNo += rastgeleSayi.Next(1, 10);

                Hesapla();

                tcKimlikNumaralari[j] = _tcKimlikNo;
            }

            return tcKimlikNumaralari;
        }

        private void Hesapla()
        {
            // 1) 1, 3, 5, 7 ve 9. sıradaki rakamın toplamının 7 katı 
            int tekBasamaklar = 0;
            for (int i = 0; i < 9; i += 2)
                tekBasamaklar += int.Parse(_tcKimlikNo.Substring(i, 1)) * 7;

            // 2) 2, 4, 6 ve 8.rakamın toplamının 9 katını topla
            int ciftBasamaklar = 0;
            for (int i = 1; i < 9; i += 2)
                ciftBasamaklar += int.Parse(_tcKimlikNo.Substring(i, 1)) * 9;

            // 3) Çıkan sonucun birler basamağı 10. rakamı veriyor
            int onuncuBasamak = (tekBasamaklar + ciftBasamaklar) % 10;

            // 4) Hesaplanan 10. basamağı, 9 basamağı oluşturan Tc kimlik numarasına ekle
            _tcKimlikNo += onuncuBasamak;

            // 5) ilk 10 rakamın toplamının birler basamağı 11. rakamı veriyor
            int onBirinciBasamak = 0;
            for (int i = 0; i < 10; i++)
                onBirinciBasamak += int.Parse(_tcKimlikNo.Substring(i, 1));
            onBirinciBasamak %= 10;

            // 6) Elde edilen ilk 10 ve 11. haneyi birleştirip diziye ekle
            _tcKimlikNo += onBirinciBasamak;
        }

        private bool Karsilastir(string tcKimlikNo)
        {
            // 7) 10. ve 11. basamağı hesaplanıp yeniden oluşturulan numarayla, sisteme girileni karşılaştır
            return _tcKimlikNo == tcKimlikNo;
        }

        public void Sifirla()
        {
            // _tcKimlikNo alanını (field) komutla sıfırlayacağıma, Reflection kullandım
            // İşte gerçek tembellik bu!
            foreach (FieldInfo alan in GetType().GetFields(BindingFlags.Instance | BindingFlags.NonPublic).ToArray())
            {
                if (alan.FieldType == typeof(string))
                    alan.SetValue(this, null);
            }
        }
    }
}
```