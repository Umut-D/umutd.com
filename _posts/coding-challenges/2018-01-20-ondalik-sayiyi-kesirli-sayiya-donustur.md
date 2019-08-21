---
layout: post
title: Ondalık Sayıyı Kesirli Sayıya Dönüştür
date: 2018-01-20 19:02 +0300
categories: Coding-Challenges
tags: Kesirli Sayı, Ondalık Sayı, Dönüşüm
---
### Soru
Programcıya bir adet ondalık sayı **(girilenSayi)** verilmiştir. Bu noktadan sonra programcıdan, verilen ondalık sayının kesirli sayıya çevirilmiş halini bularak, sonucu kesirli sayı halinde (sonuc) yazdırması istenmektedir.

### Örnek

| Girdi                  | Çıktı          |
|------------------------|----------------|
| **(girilenSayi)**: 1.8 | **Sonuç**: 9/5 |
| **(girilenSayi)**: 2.5 | **Sonuç**: 5/2 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        double girilenSayi = 1.2;
 
        // Sayacı rakamlar döngüsü boyunca arttır
        for (int sayac = 1; sayac < 10; sayac++)
        {
            // Tam sayı elde etmek için girilen sayı ile rakamları çarp
            double yeniSayi = girilenSayi*sayac;
 
            // Çarpım sonucu tam sayı ise kesirli sayıyı yazdır ve işlemi sonlandır
            if (yeniSayi%1 == 0)
            {
                String sonuc = yeniSayi + "/" + sayac;
 
                Console.WriteLine(sonuc);
                break;
            }
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
 
        double girilenSayi = 1.2;
 
        // Sayacı rakamlar döngüsü boyunca arttır
        for (int sayac = 1; sayac < 10; sayac++)
        {
            // Tam sayı elde etmek için girilen sayı ile rakamları çarp
            double yeniSayi = girilenSayi * sayac;
 
            // Çarpım sonucu tam sayı ise kesirli sayıyı yazdır ve işlemi sonlandır
            if (yeniSayi % 1 == 0)
            {
                // Ondalık sayı kısmını kırp
                String sonuc = String.format("%.0f", yeniSayi) + "/" + sayac;
 
                System.out.println(sonuc);
                break;
            }
        }
    }
}
```