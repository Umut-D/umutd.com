---
layout: post
title: Sezar Şifrelemesi
date: 2017-12-16 19:02 +0300
categories: Coding-Challenges
tags: Sezar Şifrelemesi, Şifreleme
---
### Soru
Sezar şifrelemesi, bir yazıdaki harflerin yerlerinin değiştirilmesi sonucunda elde edilir. Bu şifrede, her harf o harften bir (ya da birkaç) sonraki harf kullanılarak yazılır. 

Bu noktada programcıdan; Türkçe karakter kullanılmadan girilen metindeki (girilenMetin) harfleri bir sonraki harflere (tek harf atlamalı) dönüştürüp (sifrelenmisMetin) basit (yer değiştirme) şifreleme yapması istenmektedir.

### Örnek

| Girdi                  | Çıktı                      |
|------------------------|----------------------------|
| **girilenMetin**: test | **sifrelenmisMetin**: uftu |
| **girilenMetin**: abcd | **sifrelenmisMetin**: bcde |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenMetin = "Bu bir denemedir";
 
        // Girilen düz metini, tek tek harflere dönüştür ve karakter dizisine at
        char[] karakter = girilenMetin.ToCharArray();
 
        foreach (char tekHarf in karakter)
        {
            // Her bir karakteri bir sonraki karaktere dönüştür
            string sifrelenmisMetin = Convert.ToChar(tekHarf + 1).ToString();
 
            // Klavye düzeninde değişik karakterlere gelen harflerde değişim yaparak yazdır
            Console.Write(sifrelenmisMetin
                .Replace('[', 'A')
                .Replace('!', ' ')
                .Replace('Z', 'A'));
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
 
    public static void main(String[] args) {
 
        String girilenMetin = "Bu bir denemedir";
 
        // Girilen düz metini, tek tek harflere dönüştür ve karakter dizisine at
        char[] karakter = girilenMetin.toCharArray();
 
        for (char tekHarf : karakter)
        {
            // Her bir karakteri bir sonraki karaktere dönüştür
            String sifrelenmisMetin = String.valueOf((tekHarf += 1));
 
            // Klavye düzeninde değişik karakterlere gelen harflerde değişim yaparak yazdır
            System.out.print(sifrelenmisMetin
                    .replace('[', 'A')
                    .replace('!', ' ')
                    .replace('Z', 'A'));
        }
    }
}
```