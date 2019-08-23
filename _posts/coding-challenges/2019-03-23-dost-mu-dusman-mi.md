---
layout: post
title: Dost Mu Düşman Mı?
date: 2019-03-23 17:05 +0300
categories: Coding-Challenges
tags: Dizi
---
### Soru
Programcıya biri isim dizisi **(isimler)** verilerek, bu dizide yer alan 4 harfe sahip kişilerin dost, olmayanların düşman olduğu belirtiliyor. Bu noktadan sonra ise programcıdan, dizideki 4 harfli isimleri ayrıştırarak tek tek yazdırması isteniyor.

### Örnek

| Girdi                                            | Çıktı                     |
|--------------------------------------------------|---------------------------|
| **isimler**: "Ali", "Burak", "Neşe"              | **Sonuç**: "Neşe"         |
| **isimler**: "Abdullah", "Ersu", "Ersoy", "Adem" | **Sonuç**: "Ersu", "Adem" |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
 
class Program
{
    static void Main()
    {
        string[] isimler = {"Neşe", "Adem", "Eylem", "Ece", "Ali", "Dilara", "Süleyman"};
        List<string> dostlar = new List<string>();
 
        // Dizideki her bir isimi ayrıştır
        foreach (var isim in isimler)
        {
            // 4 harfe sahip isimleri dostlara ekle
            if (isim.Length == 4)
            {
                dostlar.Add(isim);
            }
        }
 
        foreach (string dost in dostlar)
        {
            Console.WriteLine(dost);
        }
        
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
 
public class Main {
 
    public static void main(String[] args)
    {
        String[] isimler = {"Neşe", "Adem", "Eylem", "Ece", "Ali", "Dilara", "Süleyman"};
        ArrayList<String> dostlar = new ArrayList<>();
 
        // Dizideki her bir isimi ayrıştır
        for (String isim: isimler)
        {
            // 4 harfe sahip isimleri dostlara ekle
            if (isim.length() == 4)
            {
                dostlar.add(isim);
            }
        }
 
        for (String dost: dostlar)
        {
            System.out.println(dost);
        }
    }
}
```