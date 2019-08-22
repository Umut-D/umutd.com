---
layout: post
title: Sondaki Sıfırları Yok Et
date: 2018-07-07 19:33 +0300
categories: Coding-Challenges
tags: Sıfır, Değer Silme
---
### Soru
Programcıya aynı veya farklı rakamlarda oluşan bir tam sayı -ondalık sayı değil- **(girilenSayi)** veriliyor. Programcıdan ise, ilgili tam sayının sonunda yer alan ve fazlalık olarak görülen sıfırları silmesi/yok etmesi isteniyor.

**Not**: Sayının başında veya ortasında yer alan sıfır rakamlarına dokunulmaması gerekmekte.

### Örnek

| Girdi                   | Çıktı           |
|-------------------------|-----------------|
| **girilenSayi**: 42000  | **Sonuç**: 42   |
| **girilenSayi**: 105500 | **Sonuç**: 1055 |

### Çözüm - C#
```csharp
using System;
 
internal class Program
{
    private static void Main(string[] args)
    {
        int girilenSayi = 44200;
        int sonuc = 0;
 
        // Girilen sayının kontrolünü yap
        if (girilenSayi != 0)
        {
            // Sabit sayı ataması yap
            int sabitSayi = 0;
 
            // Girilen sayıyı String'e dönüştür.
            // Herhangi sorunla karşılaşır ise sabit sayıyı (0) döndür
            if (int.TryParse(girilenSayi.ToString(), out sabitSayi))
            {
                // Sayının sonunda yer alan sıfırları sil
                sonuc = Convert.ToInt32(girilenSayi.ToString().TrimEnd('0'));
            }
 
            Console.WriteLine("Sonuç: " + sonuc);
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
 
        String girilenDeger = "44200";
        StringBuilder sonuc = new StringBuilder();
        boolean durum = false;
 
        // Sondaki sıfırların indeks değerini al
        int sondakiSifirIndeks = girilenDeger.lastIndexOf('0');
 
        // Girilen değerin uzunluğu 0 değilse devam et
        if (sondakiSifirIndeks == girilenDeger.length() - 1) {
 
            // girilen değerin boyutu kadar (tersten) devam et
            for (int i = (girilenDeger.length() - 1); i >= 0; i--)
            {
                // Eğer indeksteki değer sıfır değilse atla
                if (girilenDeger.charAt(i) != '0')
                {
                    durum = true;
                }
 
                // Girilen değer sıfır ise sonuc degiskenine ilgili sayiyi ekle
                if (durum)
                {
                    sonuc.append(girilenDeger.charAt(i));
                }
            }
 
            // Sıfırların ayıklandığı sonuçları ters döndür
            girilenDeger = new StringBuilder(sonuc.toString()).reverse().toString();
        }
 
        System.out.println("Sonuç: " + girilenDeger);
    }
}
```