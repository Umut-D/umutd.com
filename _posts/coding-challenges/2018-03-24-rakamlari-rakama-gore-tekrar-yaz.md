---
layout: post
title: Rakamlarıi Rakama Göre Tekrar Yaz
date: 2018-03-24 19:33 +0300
categories: Coding-Challenges
tags: İç İçe Döngü, Tekrar
---
### Soru
Programcıya, 0 ila 9 arasında olan rakamlardan oluşan bir sayı **(girilenSayi)** veriliyor. Bu noktadan sonra ise, sayıda yer alan rakamların tekrarı kadar olan yeni bir sayı oluşturması isteniyor.

### Örnek

| Girdi                 | Çıktı              |
|-----------------------|--------------------|
| **girilenDeger**: 123 | **Sonuç**: 122333  |
| **girilenDeger**: 502 | **Sonuç**: 5555522 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
internal class Program
{
    private static void Main(string[] args)
    {
        int verilenSayi = 412;
 
        List<string> dizi = new List<string>();
        string sonuc = "";
 
        // Kullanıcıya verilen sayıyı önce string'e oradan da karakter dizisine dönüştür
        char[] karakterler = Convert.ToString(verilenSayi).ToCharArray();
 
        // Karakter dizisindeki her bir değeri liste dizisine at
        foreach (char sayi in karakterler)
        {
            dizi.Add(sayi.ToString());
        }
 
        // Dizideki karakter sayısı boyunca döngü oluştur
        for (int i = 0; i < dizi.Count; i++)
        {
            // Dizideki karakterlerin belirttiği sayı kaçar iç döngüyü çalıştır ve sayıyı o kadar yazdır
            for (int j = 0; j < Convert.ToInt32(dizi[i]); j++)
            {
                // Yazdırılan her bir sayıyı sonuc değişkenine ekle
                sonuc += karakterler[i];
            }
        }
 
        Console.WriteLine(sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
 
public class Main {
    public static void main(String[] args) {
        int verilenSayi = 412;
 
        ArrayList dizi = new ArrayList();
        String sonuc = "";
 
        // Kullanıcıya verilen sayıyı önce string'e oradan da karakter dizisine dönüştür
        char[] karakterler = String.valueOf(verilenSayi).toCharArray();
 
        // Karakter dizisindeki her bir değeri liste dizisine at
        for (int i = 0; i < karakterler.length; i++) {
            dizi.add(karakterler[i]);
        }
 
        // Dizideki karakter sayısı boyunca döngü oluştur
        for (int i = 0; i < dizi.size(); i++) {
            // Dizideki karakterlerin belirttiği sayı kaçar iç döngüyü çalıştır ve sayıyı o kadar yazdır
            for (int j = 0; j < Integer.parseInt(String.valueOf(dizi.get(i))); j++) {
                // Yazdırılan her bir sayıyı sonuc değişkenine ekle
                sonuc += karakterler[i];
            }
        }
 
        System.out.println(sonuc);
    }
}
```