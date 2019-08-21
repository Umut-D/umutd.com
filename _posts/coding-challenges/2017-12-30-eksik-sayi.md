---
layout: post
title: Eksik Sayı
date: 2017-12-30 19:02 +0300
categories: Coding-Challenges
tags: Sayı, Eksik Sayı
---
### Soru
Programcıya eksik sayıların olduğu bir dizi **(numaralar)** veriliyor. Bu noktada ise programcıdan, dizideki eksik sayıyı bularak ekrana yazdırılması isteniyor.

### Örnek

| Girdi                       | Çıktı        |
|-----------------------------|--------------|
| **(numaralar)**: 1, 4, 5, 3 | **Sonuç**: 2 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        // Numaraları listele
        int[] numaralar = {1, 4, 5, 3};
 
        // Tüm numaralara yer verilecek diziyi oluştur
        int[] tamNumaralar = new int[numaralar.Length + 1];
 
        // Tüm numaraları ilgili dizeye aktar
        for (int i = 0; i < numaralar.Length + 1; i++)
            tamNumaralar[i] = i + 1;
 
        // Eksik olan sayıyı bul ve değişkene şutla (İyi ki varsın Linq!)
        IEnumerable<int> eksikSayi = tamNumaralar.Except(numaralar);
 
        // Eksik olan değişkeni yazdır
        foreach (int sayi in eksikSayi)
            Console.WriteLine(sayi);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
        // Numaraları listele
        int[] numaralar = {1, 4, 5, 3};
 
        // Tüm numaralara yer verilecek diziyi oluştur
        int[] tamNumaralar = new int[numaralar.length + 1];
 
        // Tüm numaraları ilgili dizeye aktar
        for (int i = 0; i < numaralar.length + 1; i++)
            tamNumaralar[i] = i + 1;
 
        // Numaraları topla
        int numaralarToplam = 0;
 
        for (int i : numaralar) {
            numaralarToplam += i;
        }
 
        // Tam Numaraları topla
        int tamNumaralarToplam = 0;
 
        for (int i : tamNumaralar) {
            tamNumaralarToplam += i;
        }
 
        // Aradaki farkı bul (Bu seçenek eksik sayıyı kolayca veriyor)
        int eksikSayi = tamNumaralarToplam - numaralarToplam;
 
        // Eksik olan değişkeni yazdır
        System.out.println(eksikSayi);
    }
}
```