---
layout: post
title: Parçalara Ayır
date: 2020-09-19 17:55 +0300
categories: Coding-Challenges
tags: Cümle, Parçalama, Parça, Kelime, Harf
excerpt: Programcıya birbirine yapışık kelimelerden oluşan uzun bir cümle ve kaç harfte bir cümlenin parçalara ayırılacağını belirten sayı da veriliyor. Sonrasında, istenen her sayı ve onun katında cümlenin parçalara ayrılması isteniyor...
---
### Soru
Programcıya birbirine yapışık kelimelerden oluşan uzun bir cümle **(girilenCumle)** ve kaç harfte bir cümlenin parçalara ayırılacağını belirten sayı da veriliyor. Sonrasında, istenen her sayı **(parcaSayisi)** ve onun katında cümlenin parçalara ayrılması isteniyor.

### Örnek

| Girdi                                                        | Çıktı                             |
|--------------------------------------------------------------|-----------------------------------|
| **girilenCumle**: merhabadunya <br>**parcaSayisi**: 3        | **Sonuç**: mer hab adu nya        |
| **girilenCumle**: selamsanauzaylikisi <br>**parcaSayisi**: 5 | **Sonuç**: selam sanau zayli kisi |

### Çözüm - C#
```csharp
using System;

class Program
{
    public static void Main()
    {
        string girilenCumle = "supercalifragilisticexpialidocious";
        int parcaSayisi = 4;

        // Girilen yazıyı teker teker karakter dizisine çevir
        char[] karakterler = girilenCumle.ToCharArray();

        string cumle = string.Empty;
        for (int i = 0; i < karakterler.Length; i++)
        {
            // Girilen parça sayısı ve katlarına gelindiğinde, bir adet boşluk ekle
            if (i % parcaSayisi == 0)
                cumle += new string(' ', 1);

            // Aksi takdirde cumle'ye harfleri ekleme devam et
            cumle += karakterler[i];
        }

        // Başta boşluk olursa kırp
        Console.WriteLine($"Sonuç: {cumle.TrimStart()}");

        Console.Read();
    }
}
```

### Çözüm - Java
```java
class Main 
{
  public static void main(String[] args) 
  {
        String girilenCumle = "supercalifragilisticexpialidocious";
        int parcaSayisi = 4;

        // Girilen yazıyı teker teker karakter dizisine çevir
        char[] karakterler = girilenCumle.toCharArray();

        String cumle = "";
        for (int i = 0; i < karakterler.length; i++)
        {
            // Girilen parça sayısı ve katlarına gelindiğinde, bir adet boşluk ekle
            if (i % parcaSayisi == 0)
                cumle += " ";

            // Aksi takdirde cumle'ye harfleri ekleme devam et
            cumle += karakterler[i];
        }

        // Başta boşluk olursa kırp
        System.out.println("Sonuç: " + cumle.trim());
  }
}
```