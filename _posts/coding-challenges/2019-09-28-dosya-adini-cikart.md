---
layout: post
title: Dosya Adını Çıkart
date: 2019-09-28 10:47 +0300
categories: Coding-Challenges
tags: Dosya, Ad, İsim, Kırpma
excerpt: Programcıya, farklı harf ve karakterlerden oluşan bir dosya adı (dosyaAdi) veriliyor. Bu noktadan sonra ise programcıdan;
---
### Soru
Programcıya, farklı harf ve karakterlerden oluşan bir dosya adı **(dosyaAdi)** veriliyor. Bu noktadan sonra ise programcıdan;

* ilk noktadan önceki adda sayı (ve onu izleyen alt çizgi) var ise çıkartması,
* ikinci nokta dahil olmak üzere, sonraki yazıları çıkartması isteniyor.

### Örnek

| Girdi                                          | Çıktı                          |
|------------------------------------------------|--------------------------------|
| **dosyaAdi**: 123_FILE_NAME.EXTENSION.OTHEREXT | **Sonuç**: FILE_NAME.EXTENSION |
| **dosyaAdi**: 1231231223123131_myFile.tar.gz2  | **Sonuç**: myFile.tar          |

### Çözüm - C#
```csharp
using System;
using System.Text.RegularExpressions;

internal class Program
{
    private static void Main()
    {
        string dosyaAdi = "1231231223123131_FILE_NAME.EXTENSION.OTHEREXTENSION";

        // Dosya adını noktayı baz alarak bölümle
        string[] digits = Regex.Split(dosyaAdi, @"\.");

        // Nokta ile birleşim yaparak adı oluştur
        string noktaliAd = digits[0] + "." + digits[1];
        
        // Mevcut addaki alt çizgi duzenlemesini ayıkla
        string[] duzenliAd = noktaliAd.Split(new char[] { '_' }, 2);

        Console.WriteLine("{0}", duzenliAd[1]);

        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {

    public static void main(String[] args) {

        String dosyaAdi = "1231231223123131_FILE_NAME.EXTENSION.OTHEREXTENSION";

        // Dosya adını noktayı baz alarak bölümle
        String[] digits = dosyaAdi.split("\\.");

        // Nokta ile birleşim yaparak adı oluştur
        String noktaliAd = digits[0] + "." + digits[1];

        // Mevcut addaki alt çizgi duzenlemesini ayıkla
        String[] duzenliAd = noktaliAd.split("_", 2);

        System.out.println(duzenliAd[1]);
    }
}
```