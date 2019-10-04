---
layout: post
title: Sayıların OBEB ve OKEK'ini bul
date: 2019-10-05 00:47 +0300
categories: Coding-Challenges
tags: Obeb, Ortak Bölenleri En Büyüğü, Okek, Ortak Katların En Küçüğü
excerpt: Programcıya, iki sayı (birinciSayi, ikinciSayi) veriliyor ve bu iki sayının OBEB (Ortak Bölenleri En Büyüğü) ve OKEK'ini (Ortak Katların En Küçüğü) bulması isteniyor.
---
### Soru
Programcıya, iki sayı **(birinciSayi, ikinciSayi)** veriliyor ve bu iki sayının OBEB (Ortak Bölenleri En Büyüğü) ve OKEK'ini (Ortak Katların En Küçüğü) bulması isteniyor.

>**OBEB**, Aynı anda iki veya daha fazla tam sayıyı bölen pozitif bölen sayıların en büyüğüne bu sayıların Ortak Bölenlerinin En Büyüğü (OBEB) denir.
>**OKEK**, İki yada daha fazla tam sayının ortak katlarının en küçüğüne OKEK denir.

### Örnek

| Girdi                                    | Çıktı                       |
|------------------------------------------|-----------------------------|
| **birinciSayi**: 4<br>**ikinciSayi**: 3  | **OBEB**: 1<br>**OKEK**: 12 |
| **birinciSayi**: 4<br>**ikinciSayi**: 10 | **OBEB**: 2<br>**OKEK**: 20 |


### Çözüm - C#
```csharp
internal class Program
{
    private static void Main()
    {
        int birinciSayi = 4, ikinciSayi = 10;
        int obeb = 0;

        // BirinciSayi ve İkinciSayı'ya gelene dek döngüyü çalıştır
        for (int i = 1; i <= birinciSayi && i <= ikinciSayi; i++)
        {
            // Her iki sayının bölümlerinden kalan 0 ise Obeb'i o sayıya eşitle
            if (birinciSayi % i == 0 && ikinciSayi % i == 0)
            {
                obeb = i;
            }
        }

        // Her iki sayıyı çarpıp, elde edilen Obeb'e böl
        int okek = (birinciSayi * ikinciSayi) / obeb;

        Console.WriteLine("OBEB: {0}", obeb);
        Console.WriteLine("OKEK: {0}", okek);

        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {

    public static void main(String[] args) {

        int birinciSayi = 4, ikinciSayi = 3;
        int obeb = 0;

        // BirinciSayi ve İkinciSayı'ya gelene dek döngüyü çalıştır
        for (int i = 1; i <= birinciSayi && i <= ikinciSayi; i++)
        {
            // Her iki sayının bölümlerinden kalan 0 ise Obeb'i o sayıya eşitle
            if (birinciSayi % i == 0 && ikinciSayi % i == 0)
            {
                obeb = i;
            }
        }

        // Her iki sayıyı çarpıp, elde edilen Obeb'e böl
        int okek = (birinciSayi * ikinciSayi) / obeb;

        System.out.println("OBEB: " + obeb);
        System.out.println("OKEK: " + okek);
    }
}
```