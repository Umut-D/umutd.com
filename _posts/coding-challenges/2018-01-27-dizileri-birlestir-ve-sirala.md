---
layout: post
title: Dizileri Birleştir ve Sırala
date: 2018-01-27 19:02 +0300
categories: Coding-Challenges
tags: Dizi, Dizi Birleştirme, Dizi Sıralama, Sıralama
---
### Soru
Programcıya, içerisinde birbiriyle aynı ya da farklı sayılar bulunan 2 adet dizi **(dizi, ikinciDizi)** verilmiştir. Bu noktada programcıdan, kendisine verilen iki diziyi birleştirerek, oluşturduğu yeni **(yeniDizi)** veya mevcut **(dizi)** dizideki değerleri sıralı olarak yazdırması istenmektedir.

### Örnek

| Girdi                                                 | Çıktı                          |
|-------------------------------------------------------|--------------------------------|
| **(dizi)**: 5, 2, 3, 9 <br> **(ikinciDizi)**: 2, 9, 1 | **Sonuç**: 1, 2, 2, 3, 5, 9, 9 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        int[] dizi = {5, 2, 3, 9};
        int[] ikinciDizi = {2, 9, 1};
 
        // Dizilerin uzunluk değerlerini belirleri
        int diziUzunlugu = dizi.Length;
        int ikinciDiziUzunlugu = ikinciDizi.Length;
 
        // dizi'yi ikinci dizinin boyutunu da dahil ederek boyutunu genişlet
        Array.Resize(ref dizi, (dizi.Length + ikinciDizi.Length));
 
        // İkinci dizinin içeriğini dizi değişkenine kopyala
        Array.Copy(ikinciDizi, 0, dizi, diziUzunlugu, ikinciDiziUzunlugu);
 
        // Diziyi sırala
        Array.Sort(dizi);
 
        // Sıralanan değerleri yazdır
        foreach (int degerler in dizi)
            Console.Write(degerler + " ");
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
 
public class Main {
    public static void main(String[] args) {
        int[] dizi = {5, 2, 3, 9};
        int[] ikinciDizi = {2, 9, 1};
 
        // Dizilerin uzunluk değerlerini belirleri
        int diziUzunlugu = dizi.length;
        int ikinciDiziUzunlugu = ikinciDizi.length;
 
        // İki dizinin boyutunu toplayarak yeniDizi'yi oluştur ve genişlik ata
        int[] yeniDizi = new int[diziUzunlugu + ikinciDiziUzunlugu];
 
        // Dizilerde yer alan değerleri yeniDizi değişkenine sırasıyla aktar
        System.arraycopy(dizi, 0, yeniDizi, 0, diziUzunlugu);
        System.arraycopy(ikinciDizi, 0, yeniDizi, diziUzunlugu, ikinciDiziUzunlugu);
 
        // Diziyi sırala
        Arrays.sort(yeniDizi);
 
        // Sıralanan değerleri yazdır
        for (int i : yeniDizi)
            System.out.print(i + " ");
    }
}
```