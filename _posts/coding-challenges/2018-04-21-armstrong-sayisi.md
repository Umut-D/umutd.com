---
layout: post
title: Armstrong Sayısı
date: 2018-04-21 19:33 +0300
categories: Coding-Challenges
tags: Armstrong Sayısı, Narsist Sayılar
---
### Soru
Programcıya, rastgele bir sayı **(girilenSayi)** veriliyor. Programcıdansa, ilgili sayının bir Armstrong sayısı*/Narsist sayı* olup olmadığını bulan, eğer sonuç doğru ise “Evet, bu bir Armstrong sayısıdır.”, yanlış ise “Hayır, bu bir Armstrong sayısı değildir!” yazan bir program oluşturması isteniyor.

-**Açıklama**: N haneli bir sayının basamaklarının n’inci üstlerinin toplamı, girilen sayının yine kendisine eşitse, bu türden sayı ya da sayılara Armstrong sayısı veya Narsist sayı denir. Örneğin; 153 sayısı, 3 hanelidir. İşlemsel olaraksa; 1^3 + 5^3 + 3^3 = 153 eder. Sayının kendisi, işlem sonucunda elde edilen sayıya eşit ise bu bir Armstrong sayısıdır.

### Örnek

| Girdi                 | Çıktı                                               |
|-----------------------|-----------------------------------------------------|
| **girilenSayi**: 100  | **Sonuç**: Hayır, bu bir Armstrong sayısı değildir! |
| **girilenSayi**: 1634 | **Sonuç**: Evet, bu bir Armstrong sayısıdır.        |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        int girilenSayi = 1634;
 
        // Girilen sayıyı parçalarına ayırmak için her bir rakamı string değere dönüştür
        string sayi = Convert.ToString(girilenSayi);
        double toplam = 0;
 
        // Karakter uzunluğu boyunca döngü oluştur
        foreach (char karakter in sayi)
        {
            // Her bir karakterin (yani sayının üssünü al)
            // Üs sayısı Girilen Sayının uzunluğuna göre değişmekte
            toplam += Math.Pow((int) Char.GetNumericValue(karakter), sayi.Length);
        }
 
        // Eğere girilen sayı, elde edilen toplama eşit ise sayı bir Armstrong sayısıdır
        if (girilenSayi == toplam)
        {
            Console.WriteLine("Evet, bu bir Armstrong sayısıdır.");
        }
        else
        {
            // Eğere girilen sayı, elde edilen toplama eşit değilse sayı sıradan bir sayıdır 
            Console.WriteLine("Hayır, bu bir Armstrong sayısı değildir!");
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        int girilenSayi = 1634;
 
        // Girilen sayıyı parçalarına ayırmak için her bir rakamı string değere dönüştür
        String sayi = String.valueOf(girilenSayi);
        double toplam = 0;
 
        // Karakter uzunluğu boyunca döngü oluştur
        for (int i = 0; i < sayi.length(); i++)
        {
            // Her bir karakterin (yani sayının üssünü al)
            // Üs sayısı Girilen Sayının uzunluğuna göre değişmekte
            toplam += Math.pow(Character.getNumericValue(sayi.charAt(i)), sayi.length());
        }
 
        // Eğere girilen sayı, elde edilen toplama eşit ise sayı bir Armstrong sayısıdır
        if (girilenSayi == toplam)
        {
            System.out.println("Evet, bu bir Armstrong sayısıdır.");
        }
        else
        {
            // Eğere girilen sayı, elde edilen toplama eşit değilse sayı sıradan bir sayıdır
            System.out.println("Hayır, bu bir Armstrong sayısı değildir!");
        }
    }
}
```