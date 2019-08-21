---
layout: post
title: Tek Sayıların Kareleri Toplamı
date: 2018-01-13 19:02 +0300
categories: Coding-Challenges
tags: Kare, İşlem, Toplam, Üslü Sayı
---
### Soru
Programcıya bir adet ilk değer **(ilkDeger)** ve bir adet son değer **(sonDeger)** verilmiştir. Bu noktada programcıdan ilk ve son sayılar arasında yer alan tek sayıları **(tekSayi)** bularak, bu sayıların kareleri alması ve hepsinin toplamını **(sonuc)** yazdırması istenmektedir.

**Not**: Son değer, ilk değerden her zaman büyük olmalıdır.

### Örnek

| Girdi                       | Çıktı        |
|-----------------------------|--------------|
| **ilkDeger**: 1 <br> **SonDeger**: 5 | **Toplam**: 35 |
| **ilkDeger**: 10 <br> **SonDeger**: 13 | **Toplam**: 290 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        int ilkDeger = 1, sonDeger = 5, tekSayi = 0, sonuc = 0;
 
        // Eğer değer tek ise tek olan sayının karesini ve toplama dahil et
        for (int sayac = ilkDeger; ilkDeger <= sonDeger; ilkDeger++)
        {
            // Eğer değer tek ise
            if ((ilkDeger%2) == 1)
            {
                tekSayi = (int) Math.Pow(ilkDeger, 2);
                sonuc += tekSayi;
            }
        }
 
        Console.WriteLine("Toplam: " + sonuc);
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
 
        int ilkDeger = 1, sonDeger = 5, tekSayi = 0, sonuc = 0;
 
        // İlk değerden son değere kadar döngüyü sürdür
        for (int sayac = ilkDeger; ilkDeger <= sonDeger; ilkDeger++)
        {
            // Eğer değer tek ise tek olan sayının karesini ve toplama dahil et
            if ((ilkDeger%2) == 1)
            {
                tekSayi = (int) Math.pow(ilkDeger, 2);
                sonuc += tekSayi;
            }
        }
 
        System.out.println("Toplam: " + sonuc);
    }
}
```