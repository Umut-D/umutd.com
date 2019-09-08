---
layout: post
title: Girilen Sayıyı Yazıya Çevir
date: 2018-03-17 19:33 +0300
categories: Coding-Challenges
tags: Dönüşüm, Sayıyı Yazıya Çevirme
redirect_from:
  - /coding-challenges/girilen-sayiyi-yaziya-cevir/
  - /etiket/sayiyi-yaziya-cevirme/
---
### Soru
Programcıya, 1 ile 99 arasında olan herhangi bir sayı **(girilenSayi)** veriliyor ve bu sayıyı sözel bir ifadeye çevirmesi isteniyor.

### Örnek

| Girdi               | Çıktı                         |
|---------------------|-------------------------------|
| **girilenSayi**: 67 | **Sonuç**: Sonuc: altmış yedi |
| **girilenSayi**: 82 | **Sonuç**: Sonuc: seksen iki  |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        int girilenSayi = 67;
 
        // Değişken dizisi
        string[] birlerBasamagi = new[] {"bir", "iki", "üç", "dört", "beş", "altı", "yedi", "sekiz", "dokuz"};
        string[] onlarBasamagi = new[] {"on", "yirmi", "otuz", "kırk", "elli", "altmış", "yetmiş", "seksen", "doksan"};
 
        // Değişkenler
        string birlerBasamagiYazi, onlarBasamagiYazi;
        int birler, onlar;
 
        // Birler ve onlar basamaklarını parçalarına ayır ve tespit et
        // Girilen sayı (Örn. 82), 10'a bölümünden kalan sayı olarak (Örn. 2) birler basamağı ortaya çıkar
        birler = girilenSayi%10;
 
        // Girilen sayıdan (Örn. 82), birler basamağı çıkartılıp 10'a bölününce onlar basamağının hangi sayı olduğu ortaya çıkar
        onlar = (girilenSayi - birler)/10;
 
        // Eğer girilen sayı 1 ila 9 arasında ise birler basamağını yazdır
        if (girilenSayi > 0 && girilenSayi < 10)
        {
            birlerBasamagiYazi = birlerBasamagi[girilenSayi - 1];
            Console.WriteLine(birlerBasamagiYazi);
        }
        // Girilen sayı 10 ila 99 arasında ise hem onlar hem birler basamağını yazdır
        else
        {
            birlerBasamagiYazi = birlerBasamagi[birler - 1];
            onlarBasamagiYazi = onlarBasamagi[onlar - 1];
            Console.WriteLine(onlarBasamagiYazi + " " + birlerBasamagiYazi);
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
public class Main {
    public static void main(String[] args) {
        int girilenSayi = 67;
 
        // Değişken dizisi
        String[] birlerBasamagi = new String[]{"bir", "iki", "üç", "dört", "beş", "altı", "yedi", "sekiz", "dokuz"};
        String[] onlarBasamagi = new String[]{"on", "yirmi", "otuz", "kırk", "elli", "altmış", "yetmiş", "seksen", "doksan"};
 
        // Değişkenler
        String birlerBasamagiYazi, onlarBasamagiYazi;
        int birler, onlar;
 
        // Birler ve onlar basamaklarını parçalarına ayır ve tespit et
        // Girilen sayı (Örn. 82), 10'a bölümünden kalan sayı olarak (Örn. 2) birler basamağı ortaya çıkar
        birler = girilenSayi % 10;
 
        // Girilen sayıdan (Örn. 82), birler basamağı çıkartılıp 10'a bölününce onlar basamağının hangi sayı olduğu ortaya çıkar
        onlar = (girilenSayi - birler) / 10;
 
        // Eğer girilen sayı 1 ila 9 arasında ise birler basamağını yazdır
        if (girilenSayi > 0 && girilenSayi < 10) {
            birlerBasamagiYazi = birlerBasamagi[girilenSayi - 1];
            System.out.println(birlerBasamagiYazi);
        }
        // Girilen sayı 10 ila 99 arasında ise hem onlar hem birler basamağını yazdır
        else {
            birlerBasamagiYazi = birlerBasamagi[birler - 1];
            onlarBasamagiYazi = onlarBasamagi[onlar - 1];
            System.out.println(onlarBasamagiYazi + " " + birlerBasamagiYazi);
        }
    }
}
```