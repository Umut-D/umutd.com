---
layout: post
title: İkili Kodu (Binary), Ondalık Sayıya (Decimal) Çevir
date: 2018-11-17 19:33 +0300
categories: Coding-Challenges
tags: Binary, Decimal, Dönüşüm, Çevrim
redirect_from:
  - /coding-challenges/ikili-kodu-ondalik-sayiya-cevir/
  - /etiket/binary/
---
### Soru
Programcıya İkili/Binary kodundan oluşan ondalık bir sayı  **(sayi)**veriliyor. Programcıdan ise; kendisine verilen sayıyı Ondalık/Decimal hale dönüştüren bir kod yazması isteniyor.

### Örnek

| Girdi             | Çıktı            |
|-------------------|------------------|
| **sayi**: 100.011 | **Sonuç**: 4.125 |
| **sayi**: 100.1   | **Sonuç**: 4.5   |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string binarySayi = "100.1";
 
        // Gerekli değişkenleri oluştur
        double noktaninSoluToplam = 0, noktaninSagiToplam = 0, sayi;
 
        // Binary (İkilik) düzendeki sayıyı noktaya göre ikiye ayır
        string[] noktaliSayi = binarySayi.Split('.');
 
        // Parçalanmış sayıları ilgili değişkenlere aktar
        string noktaninSolu = noktaliSayi[0];
        string noktaninSagi = noktaliSayi[1];
 
        // 1. Aşama - Eşitliğin solunu hallet
        // Noktanın solunda kalan sayıları ters çevirerek işe başla
        char[] tersCevir = noktaninSolu.ToCharArray().Reverse().ToArray();
 
        // Tek tek aktarım yap ve üs hesaplamasını genel toplama ekle
        for (int i = 0; i < noktaninSolu.Length; i++)
        {
            // Tek tek aktarım yap ve üs hesaplamasını toplama ekle
            sayi = Convert.ToInt32(tersCevir[i].ToString());
            noktaninSoluToplam += (sayi * (Math.Pow(2, i)));
        }
 
        // 2. Aşama - Eşitliğin sağını hallet
        for (int i = 0; i < noktaninSagi.Length; i++)
        {
            // Tek tek aktarım yap ve üs hesaplamasını ondalık toplamına ekle
            sayi = Convert.ToInt32(noktaninSagi[i].ToString());
            noktaninSagiToplam += (sayi * (Math.Pow(2, -i - 1)));
        }
 
        Console.WriteLine(noktaninSoluToplam + noktaninSagiToplam);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
 
        String binarySayi = "100.1";
 
        // Binary (İkilik) düzendeki sayıyı noktaya göre ikiye ayır
        String[] noktaliSayi = binarySayi.split("\\.");
 
        // Parçalanmış sayıları ilgili değişkenlere aktar
        String noktaninSolu = noktaliSayi[0];
        String noktaninSagi = noktaliSayi[1];
 
        // Gerekli değişkenleri oluştur
        double noktaninSoluToplam = 0, noktaninSagiToplam = 0, sayi;
 
        // 1. Aşama - Eşitliğin solunu hallet
        // Noktanın solunda kalan sayıları ters çevirerek işe başla
        char[] tersCevir = new StringBuilder(noktaninSolu).reverse().toString().toCharArray();
 
        // Tek tek aktarım yap ve üs hesaplamasını genel toplama ekle
        for (int i = 0; i < noktaninSolu.length(); i++)
        {
            // Tek tek aktarım yap ve üs hesaplamasını toplama ekle
            sayi = Double.parseDouble(String.valueOf(tersCevir[i]));
            noktaninSoluToplam += (sayi * (Math.pow(2, i)));
        }
 
        // 2. Aşama - Eşitliğin sağını hallet
        for (int i = 0; i < noktaninSagi.length(); i++)
        {
            // Tek tek aktarım yap ve üs hesaplamasını ondalık toplamına ekle
            sayi = Double.parseDouble(String.valueOf(noktaninSagi.indexOf(i)));
            noktaninSagiToplam += (sayi * (Math.pow(2, -i - 1)));
        }
 
        System.out.println(noktaninSoluToplam + (-noktaninSagiToplam));
    }
}
```