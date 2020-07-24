---
layout: post
title: Beş Harften Büyük Olan Kelimenin Tersini Yaz
date: 2018-04-14 19:33 +0300
categories: Coding-Challenges
tags: Ters, Ters Yazı
redirect_from:
  - /coding-challenges/kelimenin-tersini-yaz/
  - /etiket/ters-yazi/
  - /etiket/ters/
---
### Soru
Programcıya, uzunluğu veya kısalığı belli olmayan bir metin **(girilenMetin)** veriliyor. Programcıdan; tüm cümledeki kelimelere dikkat ederek, 5 harften uzun olan kelimeleri tersten yazması, 5 ve daha kısa olan kelimeleri ise normal şekilde bırakması isteniyor.

### Örnek

| Girdi                                                 | Çıktı                                          |
|-------------------------------------------------------|------------------------------------------------|
| **girilenMetin**: Futbol nedir                        | **Sonuç**: Futbol riden                        |
| **girilenMetin**: Bu bir deneme yazısı olabilir belki | **Sonuç**: Bu bir emened ısızay rilibalo ikleb |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenDeger = "Bu bir deneme yazısı olabilir belki";
 
        // Girilen değerdeki kelimeleri tek tek ayırıp diziye at
        string[] kelimeDizisi = girilenDeger.Split(' ');
        string sonuc = "";
 
        // Dizi uzunluğu boyunca döngüye devam et
        for (int i = 0; i < kelimeDizisi.Length; i++)
        {
            // Kelime uzunluğu 5 harften fazlaysa kelimeyi ters çevir
            if (kelimeDizisi[i].Length >= 5)
            {
                // Kelimeyi karakter dizisine at ve ters çevir
                char[] karakterDizisi = kelimeDizisi[i].ToCharArray();               
                Array.Reverse(karakterDizisi);
                // Karakter dizisini string'e dönüştürüp tekrar diziye yaz
                kelimeDizisi[i] = new string(karakterDizisi);
            }
            
            // Kelimeleri sonuç bileşenine ekle
            sonuc += kelimeDizisi[i] + " ";
        }
 
        // Cümlenin sondaki boşluğu sil ve sonucu göster
        Console.WriteLine(sonuc.TrimEnd());
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        String girilenDeger = "Bu bir deneme yazısı olabilir belki";
 
        // Girilen değerdeki kelimeleri tek tek ayırıp diziye at
        String[] kelimeDizisi = girilenDeger.split(" ");
        StringBuilder sonuc = new StringBuilder();
 
        // Dizi uzunluğu boyunca döngüye devam et
        for (int i = 0; i < kelimeDizisi.length; i++)
        {
            // Kelime uzunluğu 5 harften fazlaysa kelimeyi ters çevir
            if (kelimeDizisi[i].length() >= 5)
            {
                // Kelimeyi karakter dizisine at
                char[] karakterDizisi = kelimeDizisi[i].toCharArray();
 
                // Karakter dizisini ters çevir
                kelimeDizisi[i] = new StringBuilder(new String(karakterDizisi)).reverse().toString();
            }
 
            // Kelimeleri sonuç bileşenine ekle
            sonuc.append(kelimeDizisi[i]).append(" ");
        }
 
        // Cümlenin sondaki boşluğu sil ve sonucu göster
        System.out.println(sonuc.toString().trim());
    }
}
```