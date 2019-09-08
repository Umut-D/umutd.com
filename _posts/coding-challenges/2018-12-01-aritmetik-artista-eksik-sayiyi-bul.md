---
layout: post
title: Aritmetik Artışta Eksik Sayıyı Bul
date: 2018-12-01 19:33 +0300
categories: Coding-Challenges
tags: Artış, Eksik Sayı
redirect_from:
  - /coding-challenges/aritmetik-artista-eksik-sayiyi-bul/
  - /etiket/eksik-sayi/
---
### Soru
Programcıya belirli ve sabit bir artış sayısı olan liste **(girilenListe)** veriliyor. Pozitif sayılardan oluşan listenin, en az 3 sayıdan oluştuğu ve eksik sayının asla ilk ve son sayılar olmayacağı belirtiliyor. Programcıdan ise mevcut listedeki eksik sayıyı programlamatik olarak bulması isteniyor.

### Örnek

| Girdi                            | Çıktı              |
|----------------------------------|--------------------|
| **girilenListe**: 1, 3, 5, 7, 11 | **Eksik Sayı**: 9  |
| **girilenListe**: 5, 10, 20      | **Eksik Sayı**: 15 |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
 
class Program
{
    static void Main()
    {
        // Kullanıcı tarafından girilen değerlerin bulunduğu liste
        List<int> girilenListe = new List<int> {5, 10, 20};
 
        List<int> duzenliListe = new List<int>();
        int[] sayi = new int[girilenListe.Count];
 
        // Girilen değerler en az 3 olmalı ki fark ve eksik sayı bulunsun
        if (girilenListe.Count > 2)
        {
            // Listenin sonundaki iki değere göre farkı bul
            int fark = girilenListe[girilenListe.Count - 1] - girilenListe[girilenListe.Count - 2];
 
            // Mevcut farka göre, artışın düzenli bir şekilde gerçekleştiği düzenli listeyi oluştur
            for (int i = girilenListe[0]; i < girilenListe[girilenListe.Count - 1]; i += fark)
                duzenliListe.Add(i);
 
            // Düzenli liste ile Girilen listeyi karşılaştırıp eksik sayıyı bul
            sayi = duzenliListe.Except(girilenListe).ToArray();
        }
 
        Console.WriteLine(sayi[0]);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
 
public class Main {
 
    public static void main(String[] args) {
        // Kullanıcı tarafından girilen değerlerin bulunduğu liste
        List<Integer> girilenListe = Arrays.asList(5,10,20);
        List<Integer> duzenliListe = new ArrayList<>();
 
        // Girilen değerler en az 3 olmalı ki fark ve eksik sayı bulunsun
        if (girilenListe.size() > 2)
        {
            // Listenin sonundaki iki değere göre farkı bul
            int fark = girilenListe.get(girilenListe.size() - 1) - girilenListe.get(girilenListe.size() - 2);
 
            // Mevcut farka göre, artışın düzenli bir şekilde gerçekleştiği düzenli listeyi oluştur
            for (int i = girilenListe.get(0); i < girilenListe.get(girilenListe.size() - 1); i += fark)
                duzenliListe.add(i);
 
            // Düzenli listeden, girilen listedeki değerleri sil
            duzenliListe.removeAll(girilenListe);
        }
 
        // Düzenli listede kalan son değeri getir
        System.out.println(duzenliListe.get(0));
    }
}
```