---
layout: post
title: ATM'deki Para Adetlerini Say
date: 2019-01-12 19:33 +0300
categories: Coding-Challenges
tags: Para, Sayım
---
### Soru
Bir ATM’de farklı sayıda ve 4 tipte (20$, 10$, 5$, 1$) banknotlar vardır. Programcıdansa, çekmek istenilen paranın **(para)** kaç farklı banknottan oluştuğunun adet adet hesaplanmasını sağlayan bir algoritma oluşturması isteniyor.

### Örnek

| Girdi         | Çıktı                                             |
|---------------|---------------------------------------------------|
| **para**: 76  | **Sonuç**: 3 * 20$<br>1 * 10$<br>1 * 5$<br>1 * 1$ |
| **para**: 128 | **Sonuç**: 6 * 20$<br>1 * 10$<br>1 * 5$<br>3 * 1$ |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Text;
 
class Program
{
    static void Main()
    {
        // ATM'de kalan para türleri
        List<int> dolar = new List<int> {1, 5, 10, 20};
 
        // Kalan para
        decimal para = 58;
        decimal yirmi = 0, on = 0, bes = 0, bir = 0;
 
        // Kalan para ilgili indeksteki değişkenden büyükse,
        while (para >= dolar[3])
        {
            // Parayı bölerek sayının virgülden sonrasını alma
            yirmi = Math.Truncate(para / dolar[3]);
            // Kalan parayı al
            para = para % dolar[3];
        }
 
        while (para >= dolar[2])
        {
            on = Math.Truncate((para / dolar[2]));
            para %= dolar[2];
        }
 
        while (para >= dolar[1])
        {
            bes = Math.Truncate((para / dolar[1]));
            para %= dolar[1];
        }
 
        while (para >= dolar[0])
        {
            bir = Math.Truncate((para / dolar[0]));
            para %= dolar[0];
        }
 
        // Sonuçları birleştirip yazdırmak için hazırla
        StringBuilder sonuc = new StringBuilder();
        sonuc.AppendLine(yirmi + " * 20 $");
        sonuc.AppendLine(on + " * 10 $");
        sonuc.AppendLine(bes + " * 5 $");
        sonuc.AppendLine(bir + " * 1 $");
 
        Console.WriteLine(sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
        // ATM'de kalan  para türleri
        Integer[] dolar = new Integer[]{1, 5, 10, 20};
 
        // Kalan para
        double para = 138;
        double yirmi = 0, on = 0, bes = 0, bir = 0;
 
        // Kalan para ilgili indeksteki değişkenden büyükse,
        while (para >= dolar[3])
        {
            // Parayı bölerek sayının virgülden sonrasını alma
            yirmi = Math.floor(para / dolar[3]);
            // Kalan parayı al
            para = para % dolar[3];
        }
 
        while (para >= dolar[2])
        {
            on = Math.floor((para / dolar[2]));
            para %= dolar[2];
        }
 
        while (para >= dolar[1])
        {
            bes = Math.floor((para / dolar[1]));
            para %= dolar[1];
        }
 
        while (para >= dolar[0])
        {
            bir = Math.floor((para / dolar[0]));
            para %= dolar[0];
        }
 
        // Sonuçları birleştirip yazdırmak için hazırla
        StringBuilder sonuc = new StringBuilder();
        sonuc.append((int) yirmi).append(" * 20$\n");
        sonuc.append((int) on).append(" * 10$\n");
        sonuc.append((int) bes).append(" * 5$\n");
        sonuc.append((int) bir).append(" * 1$\n");
 
        System.out.println(sonuc);
    }
}
```