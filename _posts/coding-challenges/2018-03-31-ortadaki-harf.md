---
layout: post
title: Ortadaki Harf
date: 2018-02-03 19:33 +0300
categories: Coding-Challenges
tags: Dizi, Orta, Ortanca
---
### Soru
Programcıya, uzunluğu veya kısalığı belli olmayan bir kelime **(kelime)** veriliyor. Eğer kelimenin uzunluğu tek sayıdan oluşuyorsa, kelimenin ortasında yer alan harfi; kelimenin uzunluğu çift sayıdan oluşuyorsa, kelimenin ortasının sağ ve solunda yer alan iki harfi bulması programcıdan isteniyor.

### Örnek

| Girdi                       | Çıktı         |
|-----------------------------|---------------|
| **girilenDeger**: tava      | **Sonuç**: av |
| **girilenDeger**: buzdolabı | **Sonuç**: o  |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        string kelime = "fırın", sonuc = "";
        int uzunluk = kelime.Length, orta = 0;
 
        // Kelime uzunlugu birden fazla ise gerekli işlemlere geç
        if (uzunluk > 1)
        {
            // Kelime uzunluğu tek bir sayı ise
            if (uzunluk%2 == 1)
            {
                // Kelimenin orta noktasını bul ve harfi al
                orta = kelime.Length/2;
                sonuc = kelime[orta].ToString();
            }
            // Kelime uzunluğu çift haneli bir sayı ise
            else
            {
                // Kelimenin orta noktasını bularak önce ve sonrasındaki harfleri al
                orta = kelime.Length/2;
                sonuc = kelime[orta - 1] + "" + kelime[orta];
            }
        }
        // Kelime 2 haneden kısa ise uğraşma, aynen geri döndür
        else
        {            
            Console.WriteLine(kelime);
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
        String kelime = "fırın", sonuc = "";
        int uzunluk = kelime.length(), orta = 0;
 
        // Kelime uzunlugu birden fazla ise gerekli işlemlere geç
        if (uzunluk > 1)
        {
            // Kelime uzunluğu tek bir sayı ise
            if (uzunluk % 2 == 1)
            {
                // Kelimenin orta noktasını bul ve harfi al
                orta = kelime.length() / 2;
                sonuc = String.valueOf(kelime.charAt(orta));
            }
            // Kelime uzunluğu çift haneli bir sayı ise
            else
                {
                // Kelimenin orta noktasını bularak önce ve sonrasındaki harfleri al
                orta = kelime.length() / 2;
                sonuc = kelime.charAt(orta - 1) + "" + kelime.charAt(orta);
            }
        }
        // Kelime 2 haneden kısa ise uğraşma, aynen geri döndür
        else
        {
            System.out.println(kelime);
        }
 
        System.out.println(sonuc);
    }
}
```