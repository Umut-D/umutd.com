---
layout: post
title: Önceki ve Sonraki Notayı Bul
date: 2019-10-12 18:47 +0300
categories: Coding-Challenges
tags: Nota, Müzik
excerpt: Programcıdan, girilen nota'ya göre, o notadan önceki ve sonraki notaları yazdıran bir program oluşturması isteniyor...
---
### Soru
Programcıdan, girilen nota'ya **(girilenNota)** göre, o notadan önceki ve sonraki notaları yazdıran bir program oluşturması isteniyor. Ayrıyetten, yanlış nota girilip programın hata vermesine karşılık programcıdan ek bir çözüm bekleniyor.

### Örnek

| Girdi               | Çıktı                                         |
|---------------------|-----------------------------------------------|
| **girilenNota**: do | **Önceki Nota**: si <br>**Sonraki Nota**: re  |
| **girilenNota**: fa | **Önceki Nota**: mi <br>**Sonraki Nota**: sol |

### Çözüm - C#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

internal class Program
{
    private static void Main()
    {
        List<string> notalar = new List<string> {"do", "re", "mi", "fa", "sol", "la", "si"};
        string girilenNota = "re";

        try
        {
            // Girilen notanın sırasını al
            int notaSira = notalar.IndexOf(girilenNota);
            string sonrakiNota, oncekiNota;

            // Girilen notanın sırasına göre işlem yap
            switch (girilenNota)
            {
                // Girilen nota ilk nota ise;
                case "do":
                    oncekiNota = notalar.ElementAt(6);
                    sonrakiNota = notalar.ElementAt(notaSira + 1);
                    break;
                // Girilen nota sonuncu nota ise;
                case "si":
                    oncekiNota = notalar.ElementAt(notaSira - 1);
                    sonrakiNota = notalar.ElementAt(0);
                    break;
                default:
                    oncekiNota = notalar.ElementAt(notaSira - 1);
                    sonrakiNota = notalar.ElementAt(notaSira + 1);
                    break;
            }

            Console.WriteLine("Önceki Nota: {0}", oncekiNota);
            Console.WriteLine("Sonraki Nota: {0}", sonrakiNota);
        }
        catch
        {
            Console.WriteLine("Böyle bir nota yok.");
        }

        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.ArrayList;

public class Main {
    
    public static void main(String[] args) {
        ArrayList<String> notalar = new ArrayList<>();
        notalar.add("do");
        notalar.add("re");
        notalar.add("mi");
        notalar.add("fa");
        notalar.add("sol");
        notalar.add("la");
        notalar.add("si");
        String girilenNota = "re";

        try
        {
            // Girilen notanın sırasını al
            int notaSira = notalar.indexOf(girilenNota);
            String sonrakiNota, oncekiNota;

            // Girilen notanın sırasına göre işlem yap
            switch (girilenNota)
            {
                // Girilen nota ilk nota ise;
                case "do":
                    oncekiNota = notalar.get(6);
                    sonrakiNota = notalar.get(notaSira + 1);
                    break;
                // Girilen nota sonuncu nota ise;
                case "si":
                    oncekiNota = notalar.get(notaSira - 1);
                    sonrakiNota = notalar.get(0);
                    break;
                default:
                    oncekiNota = notalar.get(notaSira - 1);
                    sonrakiNota = notalar.get(notaSira + 1);
                    break;
            }

            System.out.println("Önceki Nota: " + oncekiNota);
            System.out.println("Sonraki Nota: " + sonrakiNota);
        }
        catch (Exception hata)
        {
            System.out.println("Böyle bir nota yok.");
        }
    }
}
```