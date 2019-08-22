---
layout: post
title: En Kısa Kelimenin Uzunluğunu Bul
date: 2018-06-16 19:33 +0300
categories: Coding-Challenges
tags: Cümle, Kelime, Uzunluk
---
### Soru
Programcıya farklı uzunluktaki kelimelerden oluşan bir cümle veriliyor. Programcıdan ise girilen cümlendeki **(girilenCumle)** en kısa kelimenin uzunluğunun kaç olduğunu bulmasını sağlayan bir kod yapısı oluşturması isteniyor.

**Not**: Cümle içinde yer alan nokta ve virgül’ün sonuçlara yansımaması ayrıca belirtiliyor.

### Örnek

| Girdi                                     | Çıktı        |
|-------------------------------------------|--------------|
| **girilenCumle**: Bu bir deneme metnidir. | **Sonuç**: 3 |
| **girilenCumle**: Ali, ata bak.           | **Sonuç**: 3 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
internal class Program
{
    private static void Main(string[] args)
    {
        string girilenCumle = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. " +
                              "Nam auctor placerat maximus. Donec cursus felis vel sem interdum" +
                              ", sit amet dapibus mauris vulputate.";
 
        // Girilen cümledeki virgül ve nokta işaretlerini kaldır
        string duzenlenenCumle = girilenCumle.Replace(',', ' ').Replace('.', ' ');
 
        List<int> deger = new List<int>();
 
        // Düzenlenen cümledeki her bir kelimeyi diziye at
        foreach (string kelime in duzenlenenCumle.Split(' '))
        {
            // Eğer kelimenin uzunluğu 0 değilse, kelime uzunluklarını diziye at
            if (kelime.Length > 0)
            {
                deger.Add(kelime.Length);
            }
        }
 
        // Dizideki değerleri küçükten büyüğe göre sırala
        deger.Sort();
 
        Console.WriteLine("En kısa kelimenin uzunluğu: " + deger[0]);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.Collections;
 
public class Main {
    public static void main(String[] args) {
        String girilenCumle = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. " +
                "Nam auctor placerat maximus. " +
                "Donec cursus felis vel sem interdum, sit amet dapibus mauris vulputate.";
 
        // Girilen cümledeki virgül ve nokta işaretlerini kaldır
        String duzenlenenCumle = girilenCumle.replace(',', ' ').replace('.', ' ');
 
        ArrayList<Integer> deger = new ArrayList<>();
 
        // Düzenlenen cümledeki her bir kelimeyi diziye at
        for (String kelime : duzenlenenCumle.split(" ")) {
            // Eğer kelimenin uzunluğu 0 değilse, kelime uzunluklarını diziye at
            if (kelime.length() > 0)
            {
                deger.add(kelime.length());
            }
        }
 
        // Dizideki değerleri küçükten büyüğe göre sırala
        Collections.sort(deger);
 
        System.out.println("En kısa kelimenin uzunluğu: " + deger.get(0));
    }
}
```