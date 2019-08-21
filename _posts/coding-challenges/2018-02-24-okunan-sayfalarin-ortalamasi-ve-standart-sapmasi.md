---
layout: post
title: Okunan Sayfaların Ortalaması ve Standart Sapması
date: 2018-02-24 19:33 +0300
categories: Coding-Challenges
tags: Ortalama, Standart Sapma
---
### Soru
Bir öğrencinin, bir hafta içerisinde okuduğu kitap sayfa sayıları **(okunanSayfaSayisi)** programcıya veriliyor. Programcıdan ise, bu öğrencinin kitap okuma performansını hem ortalama **(ortalama)**, hem de standart sapma **(standartSapma)** olarak değerlendiren bir program yazması isteniyor.

### Örnek

| Girdi                                     | Çıktı                                                     |
|-------------------------------------------|-----------------------------------------------------------|
| **okunanSayfaSayisi**: 10, 25, 15, 20, 10 | **Ortalama**: 16<br> **Standart Sapma**: 6,51920240520265 |
| **okunanSayfaSayisi**: 15, 10, 35, 5, 15  | **Ortalama**: 16<br> **Standart Sapma**: 11,4017542509914 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        // Öğrencinin hafta içinde okuduğu sayfa sayısı
        double[] okunanSayfaSayisi = new double[] { 15, 10, 35, 5, 15};
 
        // 1. Öğrencinin sayfa ortalamasını hesapla
        double sayfaOrtalamasi = OrtalamaHesapla(okunanSayfaSayisi);
 
        // 2. Öğrencinin standart sapma değerini fonksiyonla hesapla
        double standartSapma = StandartSapmaHesapla(okunanSayfaSayisi);
 
        Console.WriteLine("Günlük Ortalama Okunan Sayfa: " + sayfaOrtalamasi);
        Console.WriteLine("Standart Sapma: " + standartSapma);
 
        Console.Read();
    }
 
    // Öğrencilerin ortalamasını hesaplayan fonksiyon
    public static double OrtalamaHesapla(params double[] gelenDegerler)
    {
        int toplam = 0;
        double ortalama = 0;
 
        foreach (int sayi in gelenDegerler)
        {
            toplam += sayi;
            ortalama = toplam/(double) gelenDegerler.Length;
        }
 
        return ortalama;
    }
 
    // Öğrencilerin standart sapmasını hesaplayan fonksiyon
    private static double StandartSapmaHesapla(params double[] gelenDegerler)
    {
        // Ortalama fonksiyonundan gelen değeri al
        double ortalama = OrtalamaHesapla(gelenDegerler);
        double payToplami = 0;
 
        // Gelen dizi değerlerini tek tek hesapla
        // Her bir veriden, ortalamayı çıkararak mutlak değeri al. Negatifsiz hale gelen verinin karesini al. (Örn. |16-10|^2)
        // Mevcut işlemi her bir veri için tekrar tekrar gerçekleştir
        foreach (double sayi in gelenDegerler)
        {
            payToplami += Math.Pow(Math.Abs((sayi - ortalama)), 2);
        }
 
        // Paydadaki sayı, dizinin uzunluğu-1 formülü ile hesaplanıyor (Örn. 5-1)
        int paydaSayisi = gelenDegerler.Length - 1;
 
        // Pay ve paydadaki değerleri bölerek, bölümün karekökünü al
        double sonuc = Math.Sqrt((payToplami/paydaSayisi));
 
        return sonuc;
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        // Öğrencinin hafta içinde okuduğu sayfa sayısı
        double[] okunanSayfaSayisi = new double[]{10, 25, 15, 20, 10};
 
        // 1. Öğrencinin sayfa ortalamasını hesapla
        double sayfaOrtalamasi = OrtalamaHesapla(okunanSayfaSayisi);
 
        // 2. Öğrencinin standart sapma değerini fonksiyonla hesapla
        double standartSapma = StandartSapmaHesapla(okunanSayfaSayisi);
 
        System.out.println("Günlük Ortalama Okunan Sayfa: " + sayfaOrtalamasi);
        System.out.println("Standart Sapma: " + standartSapma);
 
    }
 
    // Öğrencilerin ortalamasını hesaplayan fonksiyon
    private static double OrtalamaHesapla(double[] gelenDegerler) {
        int toplam = 0;
        double ortalama = 0;
 
        for (double sayi : gelenDegerler) {
            toplam += sayi;
            ortalama = toplam / (double) gelenDegerler.length;
        }
 
        return ortalama;
    }
 
    // Öğrencilerin standart sapmasını hesaplayan fonksiyon
    private static double StandartSapmaHesapla(double[] gelenDegerler) {
        // Ortalama fonksiyonundan gelen değeri al
        double ortalama = OrtalamaHesapla(gelenDegerler);
        double payToplami = 0;
 
        // Gelen dizi değerlerini tek tek hesapla
        // Her bir veriden, ortalamayı çıkararak mutlak değeri al. Negatifsiz hale gelen verinin karesini al. (Örn. |16-10|^2)
        // Mevcut işlemi her bir veri için tekrar tekrar gerçekleştir
        for (double sayi : gelenDegerler) {
            payToplami += Math.pow(Math.abs((sayi - ortalama)), 2);
        }
 
        // Paydadaki sayı, dizinin uzunluğu-1 formülü ile hesaplanıyor (Örn. 5-1)
        int paydaSayisi = gelenDegerler.length - 1;
 
        // Pay ve paydadaki değerleri bölerek, bölümün karekökünü al
        double sonuc = Math.sqrt((payToplami / paydaSayisi));
 
        return sonuc;
    }
}
```