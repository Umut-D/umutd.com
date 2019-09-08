---
layout: post
title: Aranan Değerin Düz ve Tersten İndeks Değeri
date: 2018-03-03 19:57 +0300
categories: Coding-Challenges
tags: Arama, Düz Arama, Ters Arama
redirect_from:
  - /coding-challenges/aranan-degerin-duz-ve-tersten-indeks-degeri/
  - /etiket/ters-arama/
---
### Soru
Programcıya, anlamlı veya anlamsız bir halde kelime/sözcük **(girilenDeger)** veriliyor. Daha sonra, verilen değerde aranıp bulunması **(arananDeger)** istenen bir değer de programcıya sunuluyor.

Bu noktadan sonra ise programcıdan, aranan değeri bularak girilen değerde hem düz indeksini hem de tersten indeksini bulması isteniyor.

### Örnek

| Girdi                                                         | Çıktı                                                                                                |
|---------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| **(girilenDeger)**: abcdefaadadacd <br> **(arananDeger)**: c  | Düz-Bulunan indeks: 2<br>Düz-Bulunan indeks: 12<br>Ters-Bulunan indeks: 1<br>Ters-Bulunan indeks: 11 |
| **(girilenDeger)**: abcdefaadadacd <br> **(arananDeger)**: aa | Düz-Bulunan indeks: 6<br>Ters-Bulunan indeks: 6                                                      |

### Çözüm - C#
```csharp
using System;
using System.Text.RegularExpressions;
 
internal class Program
{
    private static void Main(string[] args)
    {
        // Kullanıcı tanımlı girilen değerler
        String girilenDeger = "abcdefaadadacd";
        String arananDeger = "c";
 
        // 1. Düz halde girilen değerler alanı
        // Girilen değerleri aranan değerler ile eşleştir
        MatchCollection eslesmeler = Regex.Matches(girilenDeger, arananDeger);
 
        // Aranan değerlerin indeks değerini tek tek göster
        foreach (Match eslesenDeger in eslesmeler)
            Console.WriteLine("Düz-Bulunan indeks: " + (eslesenDeger.Index));
 
        // 2. Terse dönüştürülüp arama yapılan değerler alanı
        // Girilen değeri ters döndürmek için önce karakter dizisine at ve dizi metodu ile ters çevirerek string değere aktar
        char[] tersDonustur = girilenDeger.ToCharArray();
        Array.Reverse(tersDonustur);
        String terstenDeger = new string(tersDonustur);
 
        // Ters döndürülen değerleri aranan değerler ile eşleştir
        MatchCollection tersEslesmeler = Regex.Matches(terstenDeger, arananDeger);
 
        // Ters döndürülen değerlerin indeks değerini tek tek göster
        foreach (Match eslesenDeger in tersEslesmeler)
            Console.WriteLine("Ters-Bulunan indeks: " + eslesenDeger.Index);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;
 
public class Main {
    public static void main(String[] args) {
        // Kullanıcı tanımlı girilen değerler
        String girilenDeger = "abcdefaadadacd";
        String arananDeger = "c";
 
        // 1. Düz halde girilen değerler alanı
        // Girilen değerleri aranan değerler ile eşleştir
        Pattern arananDesen = Pattern.compile(arananDeger);
        Matcher eslesenDeger = arananDesen.matcher(girilenDeger);
 
        // Aranan değerlerin indeks değerini tek tek göster
        while (eslesenDeger.find()) {
            System.out.println("Düz-Bulunan indeks: " + eslesenDeger.start());
        }
 
        // 2. Terse dönüştürülüp arama yapılan değerler alanı
        // Girilen değeri ters döndürmek için önce karakter dizisine at ve for döngüsü ile string değere aktar
        char[] tersDonustur = girilenDeger.toCharArray();
        StringBuilder terstenDeger = new StringBuilder();
 
        for (int i = tersDonustur.length - 1; i >= 0; i--) {
            terstenDeger.append(String.valueOf(tersDonustur[i]));
        }
 
        // Ters döndürülen değerleri aranan değerler ile eşleştir
        Pattern tersArananDesen = Pattern.compile(arananDeger);
        Matcher tersEslesenDeger = tersArananDesen.matcher(terstenDeger);
 
        // Ters döndürülen değerlerin indeks değerini tek tek göster
        while (tersEslesenDeger.find()) {
            System.out.println("Ters-Bulunan indeks: " + tersEslesenDeger.start());
        }
    }
}
```
