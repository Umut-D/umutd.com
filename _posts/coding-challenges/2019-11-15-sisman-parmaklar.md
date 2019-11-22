---
layout: post
title: Şişman Parmaklar
date: 2019-11-16 04:02 +0300
categories: Coding-Challenges
tags: Büyük Küçük Harf, Klavye, Yazı
excerpt: Ferdi'nin çok şişman bir sol serçe parmağı var. Ve Ferdi klavyeden her A tuşuna baslığında, parmağı yanlışlıkla CAPS LOCK tuşuna değiyor...
---
### Soru
Ferdi'nin çok şişman bir sol serçe parmağı var. Ve Ferdi klavyeden her A tuşuna baslığında, parmağı yanlışlıkla CAPS LOCK tuşuna değiyor.

Önündeki klavyeye bakarak yazı yazan Ferdi'nin A tuşu bozuk olduğundan (ki farkında değil), ortaya A harfleri olmayan ve CAPS LOCK açıldığında büyük, kapandığında küçük harflerle yazılan dandik bir metin çıkıyor.

Bu noktada ise programcıdan, Ferdi'nin yazdığı bu hatalı yazıyı bire bir simüle eden bir program oluşturması isteniyor.

### Örnek

| Girdi                                                   | Çıktı                                        |
|---------------------------------------------------------|----------------------------------------------|
| **girilenYazi**: Merhaba dünyalı, biz dost muyuz acaba? | **Sonuç**:  MerhB dünyLI, BİZ DOST MUYUZ cB? |
| **girilenYazi**: Şehir manzarası izlemek harika         | **Sonuç**:  Şehir mNZrSI İZLEMEK Hrik        |

### Çözüm - C#
```csharp
using System;

class Program
{
    static void Main()
    {
        string girilenYazi = "Merhaba dünyalı, biz dost muyuz acaba?";

        // a harflerini tek tek parçalayıp diziye at
        string[] dizi = girilenYazi.Split('a');
        string yeniYazi = string.Empty;

        for (int i = 0; i < dizi.Length; i++)
        {
            // Sırası çift haneli dizide (a harfini sil) yazıyı büyük harfli yap
            if (i % 2 != 0)
            {
                yeniYazi += dizi[i].ToUpper();
            }
            // Sırası ek haneli dizide (a harfini sil) yazıyı küçük harfli yap
            else
            {
                yeniYazi += dizi[i];
            }
        }

        Console.WriteLine(yeniYazi);

        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) 
    {
        String yazi = "";
        String girilenYazi = "Merhaba dünyalı, biz dost muyuz acaba?";

        // a harflerini tek tek parçalayıp diziye at
        String[] dizi = girilenYazi.split("[aA]");

        for (int i = 0; i < dizi.length; i++) 
        {
            // Sırası çift haneli dizide (a harfini sil) yazıyı büyük harfli yap
            if (i % 2 != 0) 
            {
                yazi += dizi[i].toUpperCase();
            } 
            // Sırası ek haneli dizide (a harfini sil) yazıyı küçük harfli yap
            else 
            {
                yazi += dizi[i];
            }
        }
        
        System.out.println(yazi);
    }
}
```