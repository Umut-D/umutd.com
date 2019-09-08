---
layout: post
title: Öğrenci Gelişimi
date: 2017-12-02 16:05 +0300
categories: Coding-Challenges
tags: Gelişim, Öğrenci Gelişimi, İlerleme
redirect_from:
  - /coding-challenges/ogrenci-gelisimi/
  - /etiket/ogrenci-gelisimi/
---
### Soru
Bir laboratuvar dersini alan öğrencilere dönem içerisinde 4 adet quiz yapılmaktadır. Öğrencilerden, girdikleri her quizde gelişim göstererek ya önceki sınavlarındaki aynı notu ya da sınavdan daha yüksek notu alarak gelişim göstermesi beklenmektedir. 5 quiz sonrasında öğrencilerine Quiz 1, Quiz 2, Quiz 3, Quiz 4 notları Quiz Sonuçları **(qs)** adıyla sisteme girilmiştir. 

Bu noktada programcıdan; öğrenci(ler)in quiz notlarının bir önceki sınavına eşit veya artan şekilde olduğunu bulması ve eğer gelişim gösteren öğrenciler varsa bu öğrenci(ler) için “Başarılı” yazması; ayrıca öğrenci(ler)in quiz notlarının bir önceki sınava göre azalma varsa bu öğrenci(ler) için “Başarısız” yazması istenmektedir.

### Örnek

| Girdi           | Çıktı               |
|-----------------|---------------------|
| **qs**: 1,2,3,5 | **Sonuç**: Başarılı |
| **qs**: 1,3,3,4 | **Sonuç**: Başarılı |
| **qs**: 3,4,5,1 | **Sonuç**: Başarılı |

### Çözüm - C#
```csharp
using System;
using System.Linq;
 
internal class Program
{
    private static void Main(string[] args)
    {
        int[] quizSonuclari = {1, 3, 3, 4};
 
        // Quiz sonuçları boyutunda  bir dizi oluştur
        int[] siraliSonuclar = new int[quizSonuclari.Length];
 
        // Quiz sonuçları dizisini diğer diziye kopyala
        Array.Copy(quizSonuclari, siraliSonuclar, 4);
 
        // Sıralı sonuçlar dizisini küçükten büyüğe sırala
        Array.Sort(siraliSonuclar);
 
        // İki dizideki sonuçlar birbiriyle eşdeğer ise Başarılı, değilse Başarısız
        if (siraliSonuclar.SequenceEqual(quizSonuclari))
            Console.WriteLine("Başarılı");
        else
            Console.WriteLine("Başarısız");
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
 
public class Main {
 
    public static void main(String[] args) {
        int[] quizSonuclari = {1, 4, 3, 4};
 
        // Sıralı sonuçlar dizisi oluştur ve Quiz sonuçlarını kopyala
        int[] siraliSonuclar = quizSonuclari.clone();
 
        // Sıralı sonuçlar dizisini küçükten büyüğe sırala
        Arrays.sort(siraliSonuclar);
 
        // İki dizideki sonuçlar birbiriyle eşdeğer ise Başarılı, değilse Başarısız yaz
        if (Arrays.equals(siraliSonuclar, quizSonuclari))
            System.out.println("Başarılı");
        else
            System.out.println("Başarısız");
    }
}
```