---
layout: post
title: Kimler Beğenmiş
date: 2018-11-10 19:33 +0300
categories: Coding-Challenges
tags: Beğeni, Dizi, Sosyal Medya
---
### Soru
Facebook, Twitter gibi sosyal medya sitelerinde "… beğendi" yazısı herkesin malumu. İnsanlar bu vb. site ve bloglarda yazıları, fotoğrafları ve diğer paylaşımları beğenmekteler. Bu noktada ise programcıdan, gönderiyi beğenen kişi sayısına göre;

- Gönderiyi kimse beğenmediyse, "Henüz kimse beğenmedi."
- 1 kişi beğendiyse, "X kişisi beğendi."
- 2 kişi beğendiyse, "X ve Y kişisi beğendi."
- 3 veya daha fazla kişi beğendiyse "X ve 10 kişi daha bunu beğendi."

yazabilen bir metot/fonksiyon oluşturması isteniyor.

### Örnek

| Girdi                    | Çıktı                               |
|--------------------------|-------------------------------------|
| **Beğenenler**: Ali, Ece | **Sonuç**: Ali ve Ece bunu beğendi. |
| **Beğenenler**: Neşe     | **Sonuç**: Neşe bunu beğendi.       |

### Çözüm - C#
```csharp
using System;
 
class Program
{
    static void Main()
    {
        Console.WriteLine(Begenenler("Ali", "Ece", "Neşe"));
 
        Console.Read();
    }
 
    public static string Begenenler(params string[] isimler)
    {
        int begenenKisiSayisi = isimler.Length;
        string begenenKisiler;
 
        switch (begenenKisiSayisi)
        {
            case 0:
                begenenKisiler = "Henüz kimse beğenmedi.";
                break;
            case 1:
                begenenKisiler = isimler[0] + " beğendi.";
                break;
            case 2:
                begenenKisiler = isimler[0] + " ve " + isimler[1] + " beğendi.";
                break;
            default:
                begenenKisiler = isimler[0] + " ve " + (begenenKisiSayisi - 1) + " kişi daha bunu beğendi.";
                break;
        }
 
        return begenenKisiler;
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args)
    {
        System.out.println(Begenenler(new String[]{"Ali", "Ece", "Neşe"}));
    }
 
    private static String Begenenler(String[] isimler)
    {
        int begenenKisiSayisi = isimler.length;
        String begenenKisiler;
 
        switch (begenenKisiSayisi)
        {
            case 0:
                begenenKisiler = "Henüz kimse beğenmedi.";
                break;
            case 1:
                begenenKisiler = isimler[0] + " beğendi.";
                break;
            case 2:
                begenenKisiler = isimler[0] + " ve " + isimler[1] + " beğendi.";
                break;
            default:
                begenenKisiler = isimler[0] + " ve " + (begenenKisiSayisi - 1) + " kişi daha bunu beğendi.";
                break;
        }
 
        return begenenKisiler;
    }
}
```