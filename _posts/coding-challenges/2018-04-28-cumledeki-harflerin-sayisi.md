---
layout: post
title: Cümledeki Harfleri Sayısı
date: 2018-04-28 19:33 +0300
categories: Coding-Challenges
tags: Cümle, Harf, Say, Sayım
---
### Soru
Programcıya, rastgele bir cümle **(girilenCumle)** veriliyor. Programcıdan ise, girilen cümledeki harflerin kaç kere tekrarlandığının sayılması ve bunu sonuç olarak yazdırması isteniyor.

**Not**: Girilen cümle türkçe karakter içermeyecek, 26 harfli ingiliz alfabesinden oluşacaktır.

### Örnek

| Girdi                         | Çıktı                                                    |
|-------------------------------|----------------------------------------------------------|
| **girilenCumle**: Hello World | **Sonuç**: d:1<br>e:1<br>h:1<br>l:3<br>o:2<br>r:1<br>w:1 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenCumle = "Hello World";
        string sonuc = "";
 
        // ASCII tablosunda yer alan, alfabedeki harfleri otomatik olarak yükle
        for (char ch = (char) 65; ch <= 90; ch++)
        {
            int sayac = 0;
 
            // Girilen metindeki karakterleri döngü vasıtası ile tek tek al
            foreach (char karakter in girilenCumle)
            {
                // Eğer harf numarası (bkz. ASCII tablosu - Örn. A harf 65) var ise sayacı arttır
                if (ch == karakter || (ch + 32) == karakter)
                {
                    sayac++;
                }
            }
 
            // Eğer sayaç 0 değilse sonuca her bir harfin kaç kere yazıldığını ekle
            if (sayac > 0)
            {
                sonuc += ch.ToString().ToLower() + ":" + sayac + "\n";
            }
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
 
        String girilenCumle = "This is simple";
        StringBuilder sonuc = new StringBuilder();
 
        // ASCII tablosunda yer alan, alfabedeki harfleri otomatik olarak yükle
        for (char ch = (char) 65; ch <= 90; ch++)
        {
            int sayac = 0;
 
            // Girilen metindeki karakterleri döngü vasıtası ile tek tek al
            for (char karakter : girilenCumle.toCharArray())
            {
                // Eğer harf numarası (bkz. ASCII tablosu - Örn. A harf 65) var ise sayacı arttır
                if (ch == karakter || (ch + 32) == karakter) {
                    sayac++;
                }
            }
 
            // Eğer sayaç 0 değilse sonuca her bir harfin kaç kere yazıldığını ekle
            if (sayac > 0)
            {
                sonuc.append(String.valueOf(ch).toLowerCase()).append(":").append(sayac).append("\n");
            }
        }
 
        System.out.println(sonuc);
    }
}
```