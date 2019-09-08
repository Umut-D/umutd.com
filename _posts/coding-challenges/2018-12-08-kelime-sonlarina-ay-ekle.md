---
layout: post
title: Kelime Sonlarına Ay Ekle
date: 2018-12-08 19:33 +0300
categories: Coding-Challenges
tags: Metin, Karakter Ekleme
redirect_from:
  - /coding-challenges/kelime-sonlarina-ay-ekle/
  - /etiket/ekleme/
---
### Soru
Programcıya bir metin **(girilenMetin)** veriliyor. Önce; her bir kelimedeki ilk harfin kelimenin sonuna alınması, sonra ise her kelimenin sonuna “ay” ekinin eklenmesi isteniyor.

### Örnek

| Girdi                           | Çıktı                        |
|---------------------------------|------------------------------|
| **girilenMetin**: Merhaba Dünya | **Sonuç**: erhabaMay ünyaDay |
| **girilenMetin**: Test Yazisi   | **Sonuç**: estTay azisiYay   |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
class Program
{
    static void Main()
    {
        string girilenMetin = "Test Yazisi";
 
        // Girilen metini parçalayarak ayır ve diziye at
        List<string> kelimeler = new List<string>(girilenMetin.Split(Convert.ToChar(" ")));
        string sonuc = "";
 
        // Parçalanan her bir kelimenin ilk harfini al yeni cümle oluştur
        foreach (string kelime in kelimeler)
        {
            string geciciIlkHarf = kelime.Substring(0, 1);
            string geciciCumle = kelime.Remove(0, 1);
 
            // Cümleyi oluştururken yeni kelimelerin sonuna "ay" ekle
            sonuc += geciciCumle + geciciIlkHarf + "ay ";
        }
 
        Console.WriteLine(sonuc);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
import java.util.List;
 
public class Main {
 
    public static void main(String[] args) {
        String girilenMetin = "Test Yazisi";
 
        // Girilen metini parçalayarak ayır ve diziye at
        List<String> kelimeler = Arrays.asList(girilenMetin.split("\\s+"));
        StringBuilder sonuc = new StringBuilder();
 
        // Parçalanan her bir kelimenin ilk harfini al yeni cümle oluştur
        for (String kelime : kelimeler)
        {
            String geciciIlkHarf = kelime.substring(0, 1);
            String geciciCumle = kelime.substring(1);
 
            // Cümleyi oluştururken yeni kelimelerin sonuna "ay" ekle
            sonuc.append(geciciCumle).append(geciciIlkHarf).append("ay ");
        }
 
        System.out.println(sonuc);
    }
}
```