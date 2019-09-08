---
layout: post
title: Uygun Telefon Numarası Biçimi
date: 2018-06-09 19:33 +0300
categories: Coding-Challenges
tags: Desen, Düzenli İfadeler, Pattern, Regex
redirect_from:
  - /coding-challenges/uygun-telefon-numarasi-bicimi/
  - /etiket/duzenli-ifadeler/
  - /etiket/desen/
---
### Soru
Programcıdan, belli düzene sahip ve sadece sayılardan oluşan telefon numaralarının istenen (123) 456-7890 format/biçime uygun olup olmadığını tespit edebilen bir program oluşturması isteniyor. Girilen telefon numarası **(girilenTelefonNumarasi)** uygun ise programın kullanıcıya olumlu yanıt vermesi, değilse olumsuz yanıt gösterilmesi ise ek olarak belirtiliyor.

### Örnek

| Girdi                                      | Çıktı                                        |
|--------------------------------------------|----------------------------------------------|
| **girilenTelefonNumarasi**: 321 9991133    | **Sonuç**: Maalesef istenen düzende değil... |
| **girilenTelefonNumarasi**: (312) 188-7733 | **Sonuç**: Numara düzgün formatta            |

### Çözüm - C#
```csharp
using System;
using System.Text.RegularExpressions;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenTelefonNumarasi = "(123) 456-7890";
 
        // Girilen telefon numarası Regex sınıfı kontrol et
        Regex numaraKontrol = new Regex(@"^(\+\d{1,2}\s)?\(?\d{3}\)?[\s.-]\d{3}[-]\d{4}$");
 
        // İstenen desen telefon numarası ile eşleşiyorsa
        if (numaraKontrol.IsMatch(girilenTelefonNumarasi))
        {
            Console.WriteLine("Numara düzgün formatta");
        }
        else
        {
            Console.WriteLine("Maalesef istenen düzende değil...");
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.regex.Pattern;
 
public class Main {
    public static void main(String[] args) {
        String girilenTelefonNumarasi = "(123) 456-7890";
 
        // Girilen telefon numarası Pattern sınıfı ile kontrol et
        Pattern numaraKontrol = Pattern.compile("\\(\\d{3}\\) \\d{3}-\\d{4}");
 
        // İstenen desen telefon numarası ile eşleşiyorsa
        if (numaraKontrol.matcher(girilenTelefonNumarasi).matches())
        {
            System.out.println("Numara düzgün formatta");
        } else
        {
            System.out.println("Maalesef istenen düzende değil...");
        }
    }
}
```