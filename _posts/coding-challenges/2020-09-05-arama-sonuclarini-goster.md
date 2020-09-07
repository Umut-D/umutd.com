---
layout: post
title: Arama Sonuçlarını Göster
date: 2020-09-05 16:58 +0300
categories: Coding-Challenges
tags: Personel, Liste, Linq, Veritabani, Sorgu
excerpt: Programcıya bir veritabanında olduğu farz edilen ve bir personel listesi veriliyor. Ardından, yapılması istenen çeşitli sorgulamaları Linq ile yaparak yazdırması isteniyor...
---
### Soru
Programcıya bir veritabanında olduğu farz edilen ve bir personel listesi **(Personel.Liste())** veriliyor. Ardından, yapılması istenen çeşitli sorgulamaları **Linq** ile yaparak yazdırması isteniyor.

### Örnek

| Girdi                    | Çıktı             |
|--------------------------|-------------------|
| **Talep:** Adı E ile başlayan personeller <br>**Liste**: Ali, Ece, Efe, Neşe, Zeynep | **Sonuç**: Ece, Efe |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

namespace CodingChallenges
{
    class Personel
    {
        public string AdSoyad { get; set; }
        public string Bolum { get; set; }
        public int Maas { get; set; }
        public DateTime Baslangic { get; set; }

        public static List<Personel> Liste()
        {
            List<Personel> personeller = new List<Personel>
            {
                new Personel
                    {AdSoyad = "Ali Üstün", Bolum = "Lojistik", Maas = 4500, Baslangic = new DateTime(2018, 10, 18)},
                new Personel
                    {AdSoyad = "Ece Ölür", Bolum = "Muhasebe", Maas = 5000, Baslangic = new DateTime(2019, 01, 28)},
                new Personel
                    {AdSoyad = "Burak Aslan", Bolum = "Yönetim", Maas = 6000, Baslangic = new DateTime(2017, 03, 11)},
                new Personel
                    {AdSoyad = "Barış Bilir", Bolum = "Muhasebe", Maas = 5000, Baslangic = new DateTime(2018, 02, 16)},
                new Personel
                    {AdSoyad = "Neşe Gider", Bolum = "Lojistik", Maas = 4500, Baslangic = new DateTime(2019, 03, 30)},
                new Personel
                    {AdSoyad = "Metin Kalır", Bolum = "Yönetim", Maas = 6000, Baslangic = new DateTime(2018, 11, 03)},
                new Personel
                    {AdSoyad = "Ali Esten", Bolum = "Lojistik", Maas = 4500, Baslangic = new DateTime(2016, 07, 01)},
                new Personel
                    {AdSoyad = "Merve Uzan", Bolum = "Muhasebe", Maas = 5000, Baslangic = new DateTime(2017, 12, 30)},
                new Personel
                    {AdSoyad = "Eslem Bilir", Bolum = "Muhasebe", Maas = 5000, Baslangic = new DateTime(2017, 12, 30)}
            };
            return personeller;
        }
    }
}
```

 
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace CodingChallenges
{
    class Program
    {
        public static void Main()
        {
            // Personel listesi yükleniyor
            List<Personel> personeller = Personel.Liste();

            // 1. Adı 'Ali' olanları bulun
            Console.WriteLine("1. Adı 'Ali' olanlar");
            var adAra = from ad in personeller 
                where ad.AdSoyad.StartsWith("Ali") 
                select ad;
            // var adAraAlt = personeller.Where(p => p.ToString().StartsWith("Ali"));

            foreach (Personel kisi in adAra)
                Console.WriteLine(kisi.AdSoyad);

            // 2. Baş harfi 'B' olanları bulun
            Console.WriteLine(Environment.NewLine + "2. Baş harfi 'B' olanlar");
            var bHarfleBaslayanlar = from bHarfli in personeller 
                where bHarfli.AdSoyad.StartsWith("B") 
                select bHarfli;
            // var bHarfleBaslayanlarAlt = personeller.Where(p => p.AdSoyad.StartsWith("B"));

            foreach (Personel kisi in bHarfleBaslayanlar)
                Console.WriteLine(kisi.AdSoyad);

            // 3. Bölümü muhasebe olanları bulun
            Console.WriteLine(Environment.NewLine + "3. Bölümü muhasebe olanlar");
            var muhasebeBolumu = from muhasebeciler in personeller
                where muhasebeciler.Bolum == "Muhasebe"
                select muhasebeciler;

            foreach (Personel kisi in muhasebeBolumu)
                Console.WriteLine(kisi.AdSoyad);

            // 4. Maaşı 5500'ün üstünde olanları bulun
            Console.WriteLine(Environment.NewLine + "4. Maaşı 5500'ün üstünde olanlar");
            var maas4400Ustu = from para in personeller 
                where para.Maas >= 5500 
                select para;
            // var maas4400UstuAlt = personeller.Where(p => p.Maas >= 5500);

            foreach (Personel kisi in maas4400Ustu)
                Console.WriteLine(kisi.AdSoyad);

            // 5. 2018 sonrası girişlilerin ad soyad ve departmanlarını bulun
            Console.WriteLine(Environment.NewLine + "5. 2018 sonrası girişlilerin ad soyad ve departmanları");
            var iseBaslangic2019 = from isGiris in personeller
                where isGiris.Baslangic >= new DateTime(2018, 1, 1)
                select isGiris;
            // var iseBaslangic2019Alt = personeller.Where(p => p.Baslangic >= new DateTime(2018, 1, 1));

            foreach (Personel kisi in iseBaslangic2019)
                Console.WriteLine(kisi.AdSoyad + "," + kisi.Bolum);

            Console.Read();
        }
    }
}
```