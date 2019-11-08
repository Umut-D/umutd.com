---
layout: post
title: Sınav Sorularının Sırasını Değiştir
date: 2019-11-09 04:02 +0300
categories: Coding-Challenges
tags: Rastgele Sayı, Sıra
excerpt: Programcıdan, 10 sorudan oluşan bir sınav kağıdındaki soruların sırasının rastgele değiştiren bir program yazması isteniyor. Bu sayede, B grubundaki soruların sıralarının kolayca belirlenmesi amaçlanıyor...
---
### Soru
Programcıdan, 10 sorudan oluşan bir sınav kağıdındaki soruların sırasının rastgele değiştiren bir program yazması isteniyor. Bu sayede, B grubundaki soruların sıralarının kolayca belirlenmesi amaçlanıyor.

### Örnek

| Girdi                                      | Çıktı                                       |
|--------------------------------------------|---------------------------------------------|
| **A Grubu**: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 | **B Grubu**:  5, 7, 3, 1, 4, 6, 9, 10, 2, 8 |
| **A Grubu**: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 | **B Grubu**:  4, 3, 10, 8, 7, 9, 1, 2, 5, 6 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        int toplamSoruSayisi = 10;
        Random rastgeleSayi = new Random();
        List<int> bGrubu = new List<int>();

        for (int i = 0; i < toplamSoruSayisi; i++)
        {
            // Toplam soru sayısı kadar rastgele sayı oluştur
            int olusturulanSayi = rastgeleSayi.Next(1, toplamSoruSayisi + 1);

            // Oluşturulan sayı dizide yoksa ekle
            if (!bGrubu.Contains(olusturulanSayi))
                bGrubu.Add(olusturulanSayi);
            // Oluşturulan sayı dizide varsa bu turu sayma
            else
                i--;
        }

        // Mevcut sonuçları yan yana yazdır
        Console.WriteLine("A - B");
        for (int i = 0; i < toplamSoruSayisi; i++)
        {
            Console.WriteLine("{0} - {1}", i + 1, bGrubu[i]);
        }

        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.Random;

public class App {
    public static void main(String[] args) throws Exception 
    {
        Integer toplamSoruSayisi = 10;
        Random rastgeleSayi = new Random();
        ArrayList<Integer> bGrubu = new ArrayList<>();

        for (int i = 0; i < toplamSoruSayisi; i++) 
        {
            // Toplam soru sayısı kadar rastgele sayı oluştur
            int olusturulanSayi = rastgeleSayi.nextInt(toplamSoruSayisi + 1);

            // Oluşturulan sayı dizide yoksa ekle
            if (!bGrubu.contains(olusturulanSayi) && olusturulanSayi != 0)
                bGrubu.add(olusturulanSayi);
            // Oluşturulan sayı dizide varsa bu turu sayma
            else
                i--;
        }

        // Mevcut sonuçları yan yana yazdır
        System.out.println("A - B");
        for (int i = 0; i < toplamSoruSayisi; i++) 
        {
            System.out.println((i + 1) + " - " + bGrubu.get(i));
        }
    }
}
```