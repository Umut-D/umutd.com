---
layout: post
title: Bir Sayının Karesi Mi?
date: 2018-07-28 19:33 +0300
categories: Coding-Challenges
tags: Kare, Kerekök
redirect_from:
  - /coding-challenges/bir-sayinin-karesi-mi/
  - /etiket/kare/
  - /etiket/karekok/
---
### Soru
Programcıya herhangi bir sayı **(girilenSayilar)** veriliyor ve programcıdan, girilen bu sayının bir sayının karesi olup olmadığını bulan bir kod oluşturması isteniyor.

### Örnek

| Girdi                   | Çıktı                                |
|-------------------------|--------------------------------------|
| **girilenSayilar**: 9   | **Sonuç**: Evet, bir sayının karesi. |
| **girilenSayilar**: 115 | **Sonuç**: Bir sayının karesi değil! |

### Çözüm - C#
```csharp
using System;
 
class Program
{
    static void Main(string[] args)
    {
        int girilenSayi = 9;
 
        // Girilen sayının karekökünü al
        double karekok = Math.Sqrt(girilenSayi);
        
        // Karekökük alınan sayıyı, basamaksız bir şekilde karesini al
        double kare = Math.Pow(Math.Round(karekok, 0), 2);
        
        // Eğer girilen sayı, karesi alınan sayı ile eşdeğerse
        if ((int) kare == girilenSayi)
        {
            Console.WriteLine("Evet, bir sayının karesi.");
        }
        // Eğer girilen sayı, karesi alınan sayı ile eşdeğer değilse
        else
        {
            Console.WriteLine("Bir sayının karesi değil!");
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        int girilenSayi = 9;
 
        // Girilen sayının karekökünü al
        double karekok = Math.sqrt(girilenSayi);
 
        // Karekökük alınan sayıyı, basamaksız bir şekilde karesini al
        double kare = Math.pow(Math.round(karekok), 2);
 
        // Eğer girilen sayı, karesi alınan sayı ile eşdeğerse
        if ((int) kare == girilenSayi)
        {
            System.out.println("Evet, bir sayının karesi.");
        }
        // Eğer girilen sayı, karesi alınan sayı ile eşdeğer değilse
        else
        {
            System.out.println("Bir sayının karesi değil!");
        }
    }
}
```