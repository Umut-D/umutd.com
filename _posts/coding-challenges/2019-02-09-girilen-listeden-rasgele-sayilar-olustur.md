---
layout: post
title: Girilen Listeden Rasgele Sayılar Oluştur
date: 2019-02-09 19:33 +0300
categories: Coding-Challenges
tags: Rasgele Sayı, Rasgele
redirect_from:
  - /coding-challenges/girilen-listeden-rasgele-sayilar-olustur/
---
### Soru
Programcıdan; 1-100 arasında olan sayıları boşluklu bir şekilde alan **(girilenSayi)** ve girilen bu sayıların arasında, kullanıcının istediği kadar **(adet)**, rastgele sayı üretilebilen bir program yazması isteniyor.

**Not**: Üretilen sayıların benzersiz olması istenmektedir.

### Örnek

| Girdi       | Çıktı      |
|-------------|------------|
| **girilenSayi**: 1 4 6 7 11<br>**adet**: 3 | **Sonuç**: 4 7 11 |
| **girilenSayi**: 100 200 300<br>**adet**: 2 | **Sonuç**: 200 300 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
class Program
{
    static void Main()
    {
        Console.WriteLine("Lütfen 1-100 arasında istediğiniz sayıları giriniz (Eklemeyi bitirmek için 0'a basınız): ");
 
        // Sayıları al
        string girilenSayi = Console.ReadLine();
 
        // Girilen sayıları parçalayıp diziye aktar
        string[] dizi = girilenSayi?.Split(' ');
 
        Console.Write("Kaç adet rastgele sayı üretilsin: ");
        int adet = Convert.ToInt32(Console.ReadLine());
 
        List<int> uretilen = new List<int>();
 
        // Dizi boş olmadıkça ve dizinin uzunluğu adetten az oldukça devam et
        if (dizi != null && adet <= dizi.Length)
        {
            Random rastgeleSayi = new Random();
 
            for (int i = 0; i < adet; i++)
            {
                int sayilar = Convert.ToInt32(dizi[rastgeleSayi.Next(0, dizi.Length)]);
 
                if (!uretilen.Contains(sayilar))
                {
                    uretilen.Add(sayilar);
                }
                else
                {
                    i--;
                }
            }
 
            Console.WriteLine("Üretilen Sayılar: ");
            foreach (int sayi in uretilen)
            {
                Console.WriteLine(sayi);
            }
        }
        else
        {
            Console.WriteLine("Dizi boş veya girilen adet dizinin boyutundan daha büyük.");
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.Random;
import java.util.Scanner;
 
public class Main {
 
    public static void main(String[] args) {
 
        System.out.println("Lütfen 1-100 arasında istediğiniz sayıları giriniz (Eklemeyi bitirmek için 0'a basınız): ");
 
        Scanner sayilariAl = new Scanner(System.in);
        String girilenSayi = sayilariAl.next();
 
        // Girilen sayıları parçalayıp diziye aktar
        String[] dizi = girilenSayi.split(" ");
 
        System.out.println("Kaç adet rastgele sayı üretilsin: ");
        Scanner adetAl = new Scanner(System.in);
        int adet = adetAl.nextInt();
 
        ArrayList<Integer> uretilen = new ArrayList<>();
 
        // Dizi boş olmadıkça ve dizinin uzunluğu adetten az oldukça devam et
        if (adet <= dizi.length)
        {
            Random rastgeleSayi = new Random();
 
            for (int i = 0; i < adet; i++)
            {
                int sayilar = Integer.parseInt(dizi[rastgeleSayi.nextInt(1) + dizi.length]);
 
                if (!uretilen.contains(sayilar))
                {
                    uretilen.add(sayilar);
                }
                else
                {
                    i--;
                }
            }
 
            System.out.println("Üretilen Sayılar: ");
            for (int sayi : uretilen)
            {
                System.out.println(sayi);
            }
        }
        else
        {
            System.out.println("Dizi boş veya girilen adet dizinin boyutundan daha büyük.");
        }
    }
}
```