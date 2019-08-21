---
layout: post
title: Harf ve Cümle Sayısı
date: 2018-01-06 19:02 +0300
categories: Coding-Challenges
tags: Sayı, Cümle Sayısı, Harf Sayısı
---
### Soru
Programcıya bir veya birkaç cümleden oluşan bir yazı **(girilenYazi)** verilmiştir. Bu noktada programcıdan, kendisine verilen yazıdaki harf ve cümle sayısını bulması istenmektedir.

### Örnek

| Girdi                                           | Çıktı                                        |
|-------------------------------------------------|----------------------------------------------|
| **(girilenYazi)**: Me Tutame Ex Inferno.        | **Harf Sayısı**: 17 <br> **Cümle Sayısı**: 1 |
| **(girilenYazi)**: Lorem ipsum. Sit dolor amet. | **Harf Sayısı**: 22 <br> **Cümle Sayısı**: 2 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        // Girilen yazıyı al
        string girilenYazi = "Merhaba. Bu bir deneme yazısıdır.";
 
        // Girilen yazıyı ekrana yazdır
        Console.WriteLine("Harf sayısı: " + Uzunluk(girilenYazi));
        Console.WriteLine("Cümle sayısı: " + Uzunluk(girilenYazi, true));
 
        Console.Read();
    }
 
    // 1. Metot (Method Overloading): Uzunluk değerini alıp girilen yazının harf sayısını hesapla
    public static int Uzunluk(string gelenDeger)
    {
        // Nokta ve boşlukları parçala
        int noktaSayisi = gelenDeger.Split('.').Length - 1;
        int boslukSayisi = gelenDeger.Split(' ').Length - 1;
 
        // Parçaladnan nokta ve boşlukları hesaptan düşüp harf sayısını döndür
        int harfSayisi = gelenDeger.Length - (noktaSayisi + boslukSayisi);
        return harfSayisi;
    }
 
    // 2. Metot (Method Overloading): Uzunluk değerini alıp girilen yazının harf sayısını hesapla
    public static int Uzunluk(string gelenDeger, bool cumle)
    {
        // Girilen nokta durumuna göre cümle sayısını hesaplayıp döndür
        int cumleSayisi = gelenDeger.Split('.').Length - 1;
        return cumleSayisi;
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
 
        // Girilen yazıyı al
        String girilenYazi = "Merhaba. Bu bir deneme yazısıdır.";
 
        // Girilen yazıyı ekrana yazdır
        System.out.println(("Harf sayısı: " + Uzunluk(girilenYazi)));
        System.out.println(("Cümle sayısı: " + Uzunluk(girilenYazi, true)));
    }
 
    // 1. Metot (Method Overloading): Uzunluk değerini alıp girilen yazının harf sayısını hesapla
    private static int Uzunluk(String gelenDeger) {
        // Nokta ve boşlukları parçala
        int noktaSayisi = gelenDeger.split("\\.").length - 1;
        int boslukSayisi = gelenDeger.split("\\s+").length;
 
        // Parçaladnan nokta ve boşlukları hesaptan düşüp harf sayısını döndür
        int harfSayisi = gelenDeger.length() - (noktaSayisi + boslukSayisi);
        return harfSayisi;
    }
 
    // 2. Metot (Method Overloading): Uzunluk değerini alıp girilen yazının harf sayısını hesapla
    private static int Uzunluk(String girilenYazi, boolean cumle) {
        // Girilen nokta durumuna göre cümle sayısını hesaplayıp döndür
        int cumleSayisi = girilenYazi.split("\\.").length;
        return cumleSayisi;
    }
}
```