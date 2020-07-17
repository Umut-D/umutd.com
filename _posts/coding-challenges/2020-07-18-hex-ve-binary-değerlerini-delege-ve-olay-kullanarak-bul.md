---
layout: post
title: Hex ve Binary Değerlerini Delege ve Olay Kullanarak Bul
date: 2020-07-18 06:29 +0300
categories: Coding-Challenges
tags: Hex, Binary, Delege, Olay
excerpt: Programcıya Hex ve Binary değerlerini hesaplaması için farklı sayılar veriliyor. Programcıdan, girilen sayılara dair istenen hesaplamaları Delege (Delegate) ve Olay (Event) kullanarak hesaplaması isteniyor...
---
### Soru
Programcıya Hex ve Binary değerlerini hesaplaması için farklı sayılar (**hexSayisi** ve **binarySayisi**) veriliyor. Programcıdan, girilen sayılara dair istenen hesaplamaları Delege (Delegate) ve Olay (Event) kullanarak hesaplaması isteniyor.

### Örnek

| Girdi                | Çıktı                               |
|----------------------|-------------------------------------|
| **hexSayisi**: 155 <br> **binarySayisi**: 1010 | **Hex Sonuç**:  9B <br> **Binary Sonuç**: 10 |

### Çözüm - C#
```csharp
using System;

// Delegeyi ata
public delegate void TemsilciHex(int sayi);
public delegate void TemsilciBinary(int sayi);

class Hesapla
{
    public string HexSonuc { get; set; }
    public int BinarySonuc { get; set; }

    // Delege temelli olay oluştur
    public event TemsilciHex HexOlayi;
    public event TemsilciBinary BinaryOlayi;

    // a. Olayları aktive et
    public void OnHexOlayi(int sayi)
    {
        HexOlayi?.Invoke(sayi);
    }

    // b. Olayları aktive et
    public void OnBinaryOlayi(int sayi)
    {
        BinaryOlayi?.Invoke(sayi);
    }

    public void Hex(int sayi)
    {
        HexSonuc = sayi.ToString("X");
        Console.WriteLine("Hex: {0}", HexSonuc);
    }

    public void Binary(int sayi)
    {
        BinarySonuc = Convert.ToInt32(Convert.ToString(sayi), 2);
        Console.WriteLine("Hex: {0}", BinarySonuc);
    }
}
```
<div id="ara"></div>

```csharp
using System;

class Program
{
    static void Main()
    {
        int hexSayisi = 1521;
        int binarySayisi = 1010;

        Hesapla hesapla = new Hesapla();
        hesapla.HexOlayi += hesapla.OnHexOlayi;
        hesapla.Hex(hexSayisi);

        hesapla.BinaryOlayi += hesapla.OnBinaryOlayi;
        hesapla.Binary(binarySayisi);

        Console.Read();
    }
}
```