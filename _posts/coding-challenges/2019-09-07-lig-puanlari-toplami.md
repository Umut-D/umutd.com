---
layout: post
title: Lig Puanları Toplamı
date: 2019-09-07 10:08 +0300
categories: Coding-Challenges
tags: Lig, Futbol, Takım
excerpt: Programcıya, toplam 10 maç yapılan bir ligde oynayan bir futbol takımının maç skorları, lig sonunda veriliyor. Her futbol ligindeki galibiyete 3 puan, beraberliğe 1 puan verildiği, yenilgide ise puan alınmadığı biliniyor...
---
### Soru
Programcıya, toplam 10 maç yapılan bir ligde oynayan bir futbol takımının maç skorları **(macSonuclari)**, lig sonunda veriliyor. Her futbol ligindeki galibiyete 3 puan, beraberliğe 1 puan verildiği, yenilgide ise puan alınmadığı biliniyor. Bu noktadan sonra programcıdan, takımın toplam kaç puan topladığını hesaplayan bir program yazması isteniyor. 

**Not**: Her maç sonucunda ilk sonuç, puanı hesaplanan takımı temsil eder.

### Örnek

| Girdi                     | Çıktı                 |
|---------------------------|-----------------------|
| **macSonuclari**: { "1:0", "2:0", "3:0", "4:0", "2:1", "3:1", "4:1", "3:2", "4:2", "4:3" } | **Puan**: 30 |
| **macSonuclari**: { "1:1", "2:2", "3:3", "4:4", "2:2", "3:3", "4:4", "3:3", "4:4", "4:4" } | **Puan**: 10 |

### Çözüm - C#
```csharp
using System;

internal class Program
{
    private static void Main()
    {
        string[] macSonuclari = {"1:0", "2:0", "3:0", "4:0", "2:1", "1:3", "1:4", "2:3", "2:4", "3:4"};

        int puan = 0;

        // Her bir maça göre göre tek tek işlem yap
        foreach (string mac in macSonuclari)
        {
            // Maç sonuçlarını ikiye ayır
            string[] sonuc = mac.Split(':');
            int bizimTakimSonuc = Convert.ToInt32(sonuc[0]);
            int deplasmanTakimiSonuc = Convert.ToInt32(sonuc[1]);

            // Bizim takım maçı kazanmışsa 3 puan ver
            if (bizimTakimSonuc > deplasmanTakimiSonuc)
            {
                puan += 3;
            }
            // Bizim takım berabere kaldıysa 1 puan ver
            else if (bizimTakimSonuc < deplasmanTakimiSonuc)
            {
                puan += 1;
            }
        }

        Console.WriteLine("Puan: {0}", puan);

        Console.Read();
    }
}
```

```java
public class Main {

    public static void main(String[] args) {
        String[] macSonuclari = {"1:0", "2:0", "3:0", "4:0", "2:1", "1:3", "1:4", "2:3", "2:4", "3:4"};

        int puan = 0;

        // Her bir maça göre göre tek tek işlem yap
        for (String mac : macSonuclari)
        {
            // Maç sonuçlarını ikiye ayır
            String[] sonuc = mac.split(":");
            int bizimTakimSonuc = Integer.parseInt(sonuc[0]);
            int deplasmanTakimiSonuc = Integer.parseInt(sonuc[1]);

            // Bizim takım maçı kazanmışsa 3 puan ver
            if (bizimTakimSonuc > deplasmanTakimiSonuc)
            {
                puan += 3;
            }
            // Bizim takım berabere kaldıysa 1 puan ver
            else if (bizimTakimSonuc < deplasmanTakimiSonuc)
            {
                puan += 1;
            }
        }

        System.out.println("Puan: " + puan);
    }
}
```
