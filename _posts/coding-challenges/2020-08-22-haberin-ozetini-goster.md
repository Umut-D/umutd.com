---
layout: post
title: Haberin Özetini Göster
date: 2020-08-22 10:52 +0300
categories: Coding-Challenges
tags: Haber, Özet, Özetle
excerpt: Programcıya bir haber metni ve haber özetinin ne kadar uzunluğa  sahip olacağını bildiren bir sayı veriliyor. Bu noktadan sonra programcıdan, özet uzunluğuna göre...
---
### Soru
Programcıya bir haber metni **(haber)** ve haber özetinin ne kadar harf uzunluğuna **(ozetUzunlugu)**  sahip olacağını bildiren bir sayı veriliyor. Bu noktadan sonra programcıdan, özet uzunluğuna göre haberi kesmesi isteniyor. Ancak özette kesilen/yarım alınan bir kelime olmaması, onun yerine kelimenin tümünün özete dahil edimesi gerektiği bildiriliyor. Son olarak da özetin sonuna üç nokta eklenmesi isteniyor.

### Örnek

| Girdi                  | Çıktı            |
|------------------------|------------------|
| **haber**: Karadeniz’deki aramalarda sondaja başlandıktan bir ay gibi çok kısa bir sürede gazın bulunduğunu belirten <br> **ozetUzunlugu:** 20 | **Sonuç**: Karadeniz’deki... |
| **haber**: İstanbul’un Fatih ilçesinde bulunan Bizans döneminden kalma Kariye Müzesi’nin <br> **ozetUzunlugu:** 15 | **Sonuç**: İstanbul’un Fatih... |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

class Program
{
    public static void Main()
    {
        string haber = "Karadeniz’deki aramalarda sondaja başlandıktan bir ay gibi çok kısa bir sürede gazın bulunduğunu belirten";
        int ozetUzunlugu = 40;

        List<string> dizi = new List<string>();
        int harfSayisi = 0;
        
        // Cümledeki kelimeleri parçala
        foreach (string yazi in haber.Split(' '))
        {
            // Her kelimenin uzunluğunu genel toplama ekle
            harfSayisi += yazi.Length;

            // Eğer toplam harf sayısı özet uzunluğundan kısa ise özetin yer alacağı dizi'ye ekle
            if (harfSayisi < ozetUzunlugu)
                dizi.Add(yazi);
            // Eğer toplam harf sayısı özet uzunluğundan uzunsa döngüden çık
            else
                break;
        }

        // Özet yazıyı aralıklı olarak birleştir ve özetin sonuna üç nokta ekleyerek işlemi tamamla
        string ozetYazi = string.Join(" ", dizi);
        Console.WriteLine(ozetYazi.TrimEnd() + "...");

        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;

class Main {
  public static void main(String[] args) {
        String haber = "İstanbul’un Fatih ilçesinde bulunan Bizans döneminden kalma Kariye Müzesi’nin";
        Integer ozetUzunlugu = 20;

        ArrayList<String> dizi = new ArrayList<String>();
        Integer harfSayisi = 0;
        
        // Cümledeki kelimeleri parçala
        for (String yazi : haber.split(" ",0))
        {
            // Her kelimenin uzunluğunu genel toplama ekle
            harfSayisi += yazi.length();

            // Eğer toplam harf sayısı özet uzunluğundan kısa ise özetin yer alacağı dizi'ye ekle
            if (harfSayisi < ozetUzunlugu)
                dizi.add(yazi);
            // Eğer toplam harf sayısı özet uzunluğundan uzunsa döngüden çık
            else
                break;
        }

        // Özet yazıyı aralıklı olarak birleştir ve özetin sonuna üç nokta ekleyerek işlemi tamamla
        String ozetYazi = String.join(" ", dizi);
        System.out.println(ozetYazi.trim() + "...");
  }
}
```