---
layout: post
title: Harfin Sıra Sayısı Kadar Harfi Tekrar Et
date: 2018-04-07 19:33 +0300
categories: Coding-Challenges
tags: Tekrar, Tekrarlama, Harf Tekrarı
redirect_from:
  - /coding-challenges/harfin-sira-sayisi-kadar-harfi-tekrar-et/
  - /etiket/tekrarlama/
---
### Soru
Programcıya, uzunluğu veya kısalığı belli olmayan bir metin **(girilenMetin)** veriliyor. Programcıdansa, metindeki her bir harfin sıra sayısına dikkat edip, harfleri aralarına tire ("-") koyarak ve baş harfleri büyük olarak yeniden yazması isteniyor.

### Örnek

| Girdi                    | Çıktı                                 |
|--------------------------|---------------------------------------|
| **girilenMetin**: abcdef | **Sonuç**: A-Bb-Ccc-Dddd-Eeeee-Ffffff |
| **girilenMetin**: Test   | **Sonuç**: T-Ee-Sss-Tttt              |

### Çözüm - C#
```csharp
using System;
using System.Text;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenMetin = "abcd";
        StringBuilder sonuc = new StringBuilder();
 
        // Eğer girilen metin boş ise gerekeni yap ve sonucu boş döndür
        if (string.IsNullOrEmpty(girilenMetin))
        {
            sonuc = new StringBuilder();
        }
        // Girilen metin boş değilse yola devam et
        else
        {
            // Girilen metindeki harflerin tümünü küçült
            girilenMetin = girilenMetin.ToLower();
 
            // İç içe döngü sayesinde harfleri bulundukları sıra sayısına göre yazdır
            for (int i = 0; i < girilenMetin.Length; i++)
            {
                for (int j = 0; j < i; j++)
                {
                    // Her bir harf değişiminde baş harfi büyük harf yap
                    if (j == 0)
                    {
                        sonuc.Append(girilenMetin[i].ToString().ToUpper());
                    }
 
                    // Büyük harf haricindeki aynı harfi küçük olarak yazmaya ve eklemeye devam et
                    sonuc.Append(girilenMetin[i]);
                }
                // Harf ve sıra geçişinden önce tire ekle
                sonuc.Append("-");
            }
 
            // Döngüyü uygulamadığım birinci harfi ekleyerek, son satırdaki tire işaretini kaldır 
            sonuc = new StringBuilder(girilenMetin[0].ToString().ToUpper() + sonuc.Remove(sonuc.Length - 1, 1));
        }
 
        Console.WriteLine(sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        String girilenMetin = "abcd";
        StringBuilder sonuc = new StringBuilder();
 
        // Eğer girilen metin boş ise gerekeni yap ve sonucu boş döndür
        if (girilenMetin.trim().length() == 0)
        {
            sonuc = new StringBuilder();
        }
        // Girilen metin boş değilse yola devam et
        else
            {
            // Girilen metindeki harflerin tümünü küçült
            girilenMetin = girilenMetin.toLowerCase();
 
            // İç içe döngü sayesinde harfleri bulundukları sıra sayısına göre yazdır
            for (int i = 0; i < girilenMetin.length(); i++)
            {
                for (int j = 0; j < i; j++)
                {
                    // Her bir harf değişiminde baş harfi büyük harf yap
                    if (j == 0)
                    {
                        sonuc.append(String.valueOf(girilenMetin.charAt(i)).toUpperCase());
                    }
                    // Büyük harf haricindeki aynı harfi küçük olarak yazmaya ve eklemeye devam et
                    sonuc.append(String.valueOf(girilenMetin.charAt(i)));
                }
                // Harf ve sıra geçişinden önce tire ekle
                sonuc.append("-");
            }
 
            // Döngüyü uygulamadığım birinci harfi ekleyerek, son satırdaki tire işaretini kaldır
            sonuc = new StringBuilder(String.valueOf(girilenMetin.charAt(0)).toUpperCase() + "-" + sonuc.substring(1, sonuc.length() - 1));
        }
 
        System.out.println(sonuc);
    }
}
```