---
layout: post
title: Yazıyı Farklı Şekilde Yaz
date: 2018-05-26 19:33 +0300
categories: Coding-Challenges
tags: Harf, Karakter, Yazım
---
### Soru
Programcıya, içerisinde farklı bir yazı (girilenYazi) olan veriliyor. Her kelimede tek olan sıradaki harfleri büyük, çift olanları küçük olarak yeniden yazdırması bekleniyor.

### Örnek

| Girdi                                      | Çıktı                                |
|--------------------------------------------|--------------------------------------|
| **girilenYazi**: Buradaki bilinmeyen sıfır | **Sonuç**: BuRaDaKi BiLiNmEyEn SıFıR |
| **girilenYazi**: Test midir bu             | **Sonuç**: TeSt MiDiR Bu             |

### Çözüm - C#
```csharp
using System;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenYazi = "test yazisi";
 
        // Girilen yazıyı kelime kelime ayır
        string[] kelimeDizisi = girilenYazi.Split(' ');
        string sonuc = "";
 
        // Kelime dizisindeki her bir kelimeyi teker teker al
        foreach (string kelimeler in kelimeDizisi)
        {
            // Mevcut kelimenin uzunluğunu alarak eyleme geç
            for (int j = 0; j < kelimeler.Length; j++)
            {
                // Her bir kelimeyi karakter dizisine (char) çevir
                char[] harfler = kelimeler.ToCharArray();
 
                // Eğer bulunlan sıra tek ise büyük yazdırarak sonuca ekle
                // Sıra programlamada 0'ıncı sıradan başlıyor!
                if (j%2 == 0)
                {
                    sonuc += harfler[j].ToString().ToUpper();
                }
                // Eğer bulunlan sıra çift ise küçük yazdırarak sonuca ekle
                else
                {
                    sonuc += harfler[j].ToString().ToLower();
                }
            }
 
            // Her bir kelimeden sonra boşluk ekle
            sonuc += " ";
        }
 
        // Cümle sonundaki ekstra boşluğu sil
        Console.WriteLine(sonuc.TrimEnd());
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        String girilenYazi = "test yazisi";
 
        // Girilen yazıyı kelime kelime ayır
        String[] kelimeDizisi = girilenYazi.split(" ");
        StringBuilder sonuc = new StringBuilder();
 
        // Kelime dizisindeki her bir kelimeyi teker teker al
        for (String kelimeler: kelimeDizisi)
        {
            // Mevcut kelimenin uzunluğunu alarak eyleme geç
            for (int j = 0; j < kelimeler.length(); j++)
            {
                // Her bir kelimeyi karakter dizisine (char) çevir
                char[] harfler = kelimeler.toCharArray();
 
                // Eğer bulunlan sıra tek ise büyük yazdırarak sonuca ekle
                // Sıra programlamada 0'ıncı sıradan başlıyor!
                if (j % 2 == 0)
                {
                    sonuc.append(String.valueOf(harfler[j]).toUpperCase());
                }
                // Eğer bulunlan sıra çift ise küçük yazdırarak sonuca ekle
                else
                {
                    sonuc.append(String.valueOf(harfler[j]).toLowerCase());
                }
            }
 
            // Her bir kelimeden sonra boşluk ekle
            sonuc.append(" ");
        }
 
        // Cümle sonundaki ekstra boşluğu sil
        System.out.println(sonuc.toString().trim());
    }
}
```