---
layout: post
title: N'inci Büyük Sayı
date: 2018-02-10 05:33 +0300
categories: Coding-Challenges
tags: Büyük Sayı, İç İçe Döngü, Sıralama
---
### Soru
Programcıya, içerisinde aynı olmayan/benzersiz sayılardan oluşan bir dizi **(verilenSayilar)** sunulmuştur. Bu noktada ise programcıdan, dizideki N’inci büyük sayıyı **(sondanKacinci)** bulması istenmektedir.

### Örnek

| Girdi                                                        | Çıktı        |
|--------------------------------------------------------------|--------------|
| **verilenSayilar**: 5, 3, 2, 6, 1, 8<br>**sondanKacinci**: 2 | **Sonuç**: 6 |
| **verilenSayilar**: 5, 1, 3, 7 ,9<br>**sondanKacinci**: 4    | **Sonuç**: 3 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        // Sistem tarafından verilen dizi
        int[] verilenDizi = {5, 3, 2, 6, 1, 8};
 
        // Sondan kaçıncı sıradaki büyük sayı
        int sondanKacinci = 2;
 
        // Geçici olarak kullanılacak değişken
        int geciciSayi = 0;
 
        // Kabarcık sıralama algoritması burada devreye girer
        for (int i = 0; i < verilenDizi.Length; i++)
        {
            for (int j = 0; j < verilenDizi.Length; j++)
            {
                // Önceki sayı, sonraki sayıdan büyükse yer değiştir
                if (verilenDizi[i] > verilenDizi[j])
                {
                    geciciSayi = verilenDizi[i];
                    verilenDizi[i] = verilenDizi[j];
                    verilenDizi[j] = geciciSayi;
                }
            }
        }
 
        // İndeks değeri hep bir farklı olduğu için -1 kullan
        Console.WriteLine(verilenDizi[sondanKacinci - 1]);
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
 
        // Sistem tarafından verilen dizi
        int[] verilenDizi = {5, 3, 2, 6, 1, 8};
 
        // Sondan kaçıncı sıradaki büyük sayı
        int sondanKacinci = 2;
 
        // Geçici olarak kullanılacak değişken
        int geciciSayi = 0;
 
        // Kabarcık sıralama algoritması burada devreye girer
        for (int i = 0; i < verilenDizi.length; i++)
        {
            for (int j = 0; j < verilenDizi.length; j++)
            {
                // Önceki sayı, sonraki sayıdan büyükse yer değiştir
                if (verilenDizi[i] > verilenDizi[j]) {
                    geciciSayi = verilenDizi[i];
                    verilenDizi[i] = verilenDizi[j];
                    verilenDizi[j] = geciciSayi;
                }
            }
        }
 
        // İndeks değeri hep bir farklı olduğu için -1 kullan
        System.out.println(verilenDizi[sondanKacinci - 1]);
    }
}
```
