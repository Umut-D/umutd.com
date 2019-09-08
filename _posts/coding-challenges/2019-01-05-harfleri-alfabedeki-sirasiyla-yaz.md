---
layout: post
title: Harfleri Alfabedeki Sırasıyla Yaz
date: 2019-01-05 19:33 +0300
categories: Coding-Challenges
tags: Dönüşüm, Karakter, Yazı, Alfabe
redirect_from:
  - /coding-challenges/harfleri-alfabedeki-sirasiyla-yaz/
  - /etiket/yazi/
---
### Soru
Programcıya, bir yazı veya cümle **(girilenYazi)** veriliyor. Bu noktadan sonra ise programcıdan, ilgili yazıdaki harflerin, alfabede kaçıncı sırada olduğunu bularak bu sayıları yazdırması isteniyor.

### Örnek

| Girdi                          | Çıktı                                |
|--------------------------------|--------------------------------------|
| **girilenYazi**: Merhaba Dünya | **Sonuç**: 13 5 18 8 1 2 1 4 14 25 1 |
| **girilenYazi**: Test          | **Sonuç**: 	20 5 19 20               |

### Çözüm - C#
```csharp
using System;
using System.Text;
 
class Program
{
    static void Main()
    {
        string girilenYazi = "Merhaba Dünya";
        string sonuc = null;
 
        StringBuilder dizi = new StringBuilder();
 
        // Girilen yazıyı küçült ve karakterlerine ayır ve diziye ekle
        foreach (char karakter in girilenYazi.ToLower())
        {
            if (karakter >= 'a' && karakter <= 'z')
                dizi.Append(karakter);
        }
 
        if (girilenYazi.Length > 0)
        {
            // Her bir karakterin sayısal değerini sonuca ekle
            for (int i = 0; i < dizi.Length; i++)
                sonuc += dizi[i] - 96 + " ";
        }
 
        // Sondaki fazlalık boşluğu kes
        Console.WriteLine(sonuc?.TrimEnd());
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args)
    {
        String girilenYazi = "test";
        String sonuc = "";
 
        StringBuilder dizi = new StringBuilder();
 
        // Girilen yazıyı küçült ve karakterlerine ayır ve diziye ekle
        for (char karakter : girilenYazi.toLowerCase().toCharArray())
        {
            if (karakter >= 'a' && karakter <= 'z')
                dizi.append(karakter);
        }
 
        if (girilenYazi.length() > 0)
        {
            // Her bir karakterin sayısal değerini sonuca ekle
            for (int i = 0; i < dizi.length(); i++)
                sonuc += dizi.charAt(i) - 96 + " ";
        }
 
        // Sondaki fazlalık boşluğu kes
        System.out.println(sonuc.trim());
    }
}
```