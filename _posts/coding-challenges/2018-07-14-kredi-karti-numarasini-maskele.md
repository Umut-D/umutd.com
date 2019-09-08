---
layout: post
title: Kredi Kartı Numarasını Maskele
date: 2018-07-14 19:33 +0300
categories: Coding-Challenges
tags: Kredi Kartı, Maskeleme, Düzenleme
redirect_from:
  - /coding-challenges/kredi-karti-numarasini-maskele/
  - /etiket/kredi-karti//
---
### Soru
Programcıya, uzunluğu 5 daha üstü olan farklı kredi kartı numarası **(girilenNumara)** veriliyor ve bu kredi kartı numarasındaki son 4 hane hariç tümünü # (diyez/kare/baklava dilimi) işareti ile maskelemesi isteniyor. Eğer kredi kartı numarası uzunluğu 4 ve 4’ten daha az ise herhangi bir maskeleme yapılmaması belirtiliyor.

### Örnek

| Girdi                           | Çıktı                   |
|---------------------------------|-------------------------|
| **girilenNumara**: 12345678     | **Sonuç**: ####5678     |
| **girilenNumara**: 123456782167 | **Sonuç**: ########2167 |

### Çözüm - C#
```csharp
using System;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenNumara = "1469123955127";
        string sonuc = null;
 
        // Girilen numaranın uzunluğu 4'ten büyük ise istenen maskelemeyi yap    
        if (girilenNumara.Length > 4)
        {
            for (int i = 0; i < girilenNumara.Length - 4; i++)
            {
                sonuc += "#";
            }
 
            // Girilen numaranın son dört hanesini sonuç katarına ekle
            sonuc += girilenNumara.Substring(girilenNumara.Length - 4, 4);
        }
        // Girilen numaranın uzunluğu 4'ten kısa ise hiçbir şey yapma
        else
        {
            sonuc = girilenNumara;
        }
 
        Console.WriteLine("Sonuç: " + sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
 
        String girilenNumara = "1469123955127";
        String sonuc = "";
 
        // Girilen numaranın uzunluğu 4'ten büyük ise istenen maskelemeyi yap
        if (girilenNumara.length() > 4)
        {
            // Girilen numaranın 4 eksiği kadar # işareti ekle
            for (int i = 0; i < girilenNumara.length() - 4; i++)
            {
                sonuc += "#";
            }
 
            // Girilen numaranın son dört hanesini sonuç katarına ekle
            sonuc += girilenNumara.substring(girilenNumara.length() - 4);
        }
        // Girilen numaranın uzunluğu 4'ten kısa ise hiçbir şey yapma
        else
        {
            sonuc = girilenNumara;
        }
 
        System.out.println("Sonuç: " + sonuc);
    }
}
```