---
layout: post
title: IP Kontrolü
date: 2018-12-22 19:33 +0300
categories: Coding-Challenges
tags: IP Adresi, IP, Kontrol
redirect_from:
  - /coding-challenges/ip-kontrolu/
---
### Soru
Programcıya IPv4 adresi içeren bir **(ipAdresi)** veriliyor ve ilgili IP Adresinin doğru olup olmadığının kontrol eden bir metot oluşturması isteniyor.

### Örnek

| Girdi                       | Çıktı            |
|-----------------------------|------------------|
| **ipAdresi**: 123.45.67.89  | **Sonuç**: true  |
| **ipAdresi**: 123.456.78.90 | **Sonuç**: false |

### Çözüm - C#
```csharp
using System;
using System.Net;
using System.Net.Sockets;
 
class Program
{
    static void Main()
    {
        string ipAdresi = "111.111.11.11";
 
        Console.WriteLine(IpKontrol(ipAdresi));
        Console.Read();
    }
 
    public static bool IpKontrol(string ipAdresi)
    {
        // Gelen ip adresini parçalara ayır
        string[] dizi = ipAdresi.Split('.');
 
        // Her bir alana tek tek bak
        foreach (var alan in dizi)
        {
            if (alan.StartsWith("0"))
                return false;            
        }
 
        // dizi ayrı bölümden oluşuyorsa devam et
        if (dizi.Length == 4)
        {
            IPAddress sabitAdres;
 
            // Ip adresini kontrol etmek için IP Adress sınıfından faydalan
            if (!IPAddress.TryParse(ipAdresi.Trim(), out sabitAdres))
                return false;
 
            // IP adresi düzenli ise doğru değerini döndür
            if (sabitAdres.AddressFamily == AddressFamily.InterNetwork)
                return true;            
        }
 
        return false;
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args)
    {
        System.out.println(isValidIP4Address("111.111.11.11"));
    }
 
    private static boolean isValidIP4Address(String ipAdresi)
    {
        // Gerekli ip adresi için Regex kullan
        boolean durum = ipAdresi.matches("^(\\d{1,3})\\.(\\d{1,3})\\.(\\d{1,3})\\.(\\d{1,3})$");
 
        if (durum)
        {
            // Gelen ip adresini parçalara ayır
            String[] dizi = ipAdresi.split("\\.");
 
            for (int i = 0; i <= 3; i++)
            {
                String alan = dizi[i];
 
                // Her bir alana tek tek bak
                if (alan == null || alan.length() <= 0)
                    return false;
 
                // Her bir alandaki değer 255'den büyükse yanlış döndür
                if (Integer.parseInt(alan) > 255)
                    return false;
            }
 
            // IP adresi düzenli ise doğru değerini döndür
            return true;
        }
        return false;
    }
}
```