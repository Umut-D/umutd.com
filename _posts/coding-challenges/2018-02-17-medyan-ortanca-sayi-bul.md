---
layout: post
title: Medyan (Ortanca) Sayı Bul
date: 2018-02-17 19:33 +0300
categories: Coding-Challenges
tags: Medyan, Ortanca Sayı
redirect_from:
  - /coding-challenges/medyan-ortanca-sayi-bul/ 
  - /etiket/ortanca-sayi/
---
### Soru
Programcıya, çeşitli ve sıralanmamış halde bulunan sayılardan oluşan bir dizi **(sayiDizisi)** veriliyor. Bu noktada ise programcıdan, mevcut dizinin medyan/ortanca sayısını bulması isteniyor.

### Örnek

| Girdi                        | Çıktı          |
|------------------------------|----------------|
| **(sayiDizisi)**: 1, 2, 3    | **Sonuç**: 2   |
| **(sayiDizisi)**: 1, 2, 3, 4 | **Sonuç**: 2.5 |

### Çözüm - C#
```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        // Tanımlı olarak verilen sayı dizisi
        int[] sayiDizisi = new[] {1, 5, 2, 8, 3};
 
        // Dizinin kaç değerden oluştuğunu bul
        int dizininUzunlugu = sayiDizisi.Length;
 
        // Ortanca sayıyı (medyan) bulmada öncelikle sıralama işlemi gerekli
        Array.Sort(sayiDizisi);
 
        /* I. Durum
             Sayı adedi tek ise medyan (n+1/2) formülüyle bulunur
             Örn. 1,2,3 dizisi 3 adet sayıdan oluşur. (3+1)/2 sonucunda 2. sıradaki sayı [2] medyandır.
            */
        if ((dizininUzunlugu%2 == 1))
        {
            int tekliSira = (dizininUzunlugu + 1)/2;
            Console.WriteLine(sayiDizisi[tekliSira - 1]);
        }
        /* II. Durum
             Sayı adedi çift ise medyan ((n/2) + (n/2+1)) hesabında çıkan sonuç 2'ye bölünür
             Örn. 1,2,3,4 dizisi 4 adet sayıdan oluşur. (4/2) sonucunda 2 elde edilir. 
             Ardından 2. ve 3. sayılar toplanıp 2'ye bölünür ((2+3)/2) ve [2.5] sayısı medyandır
            */
        else
        {
            double ikiliSira = dizininUzunlugu/2.0;
            double ortaSayi = (sayiDizisi[(int) ikiliSira - 1] + sayiDizisi[(int) ikiliSira])/2.0;
            Console.WriteLine(ortaSayi);
        }
 
        Console.Read();
    }
}
```

### Çözüm - Java
```java
import java.util.Arrays;
 
public class Main {
    public static void main(String[] args) {
 
        // Tanımlı olarak verilen sayı dizisi
        int[] sayiDizisi = {1, 5, 2, 8, 3};
 
        // Dizinin kaç değerden oluştuğunu bul
        int dizininUzunlugu = sayiDizisi.length;
 
        // Ortanca sayıyı (medyan) bulmada öncelikle sıralama işlemi gerekli
        Arrays.sort(sayiDizisi);
 
        /* I. Durum
             Sayı adedi tek ise medyan (n+1/2) formülüyle bulunur
             Örn. 1,2,3 dizisi 3 adet sayıdan oluşur. (3+1)/2 sonucunda 2. sıradaki sayı [2] medyandır.
            */
        if ((dizininUzunlugu % 2 == 1)) {
            int tekliSira = (dizininUzunlugu + 1) / 2;
            System.out.println(sayiDizisi[tekliSira - 1]);
        }
        /* II. Durum
             Sayı adedi çift ise medyan ((n/2) + (n/2+1)) hesabında çıkan sonuç 2'ye bölünür
             Örn. 1,2,3,4 dizisi 4 adet sayıdan oluşur. (4/2) sonucunda 2 elde edilir.
             Ardından 2. ve 3. sayılar toplanıp 2'ye bölünür ((2+3)/2) ve [2.5] sayısı medyandır
            */
        else {
            double ikiliSira = dizininUzunlugu / 2.0;
            double ortaSayi = (sayiDizisi[(int) ikiliSira - 1] + sayiDizisi[(int) ikiliSira]) / 2.0;
            System.out.println(ortaSayi);
        }
    }
}
```