---
layout: post
title: IBAN Kontrol
date: 2015-11-04 12:43 +0300
categories: Programlar
tags: Banka, IBAN, IBAN Doğrulama, IBAN Kontrol, IBAN Sorgulama
---
![iban-kontrol](/images/programlar/iban-kontrol.png){:.resim-ortali}

> **IBAN (International Bank Account Number)**, para transferlerinin yanlış hesap numaralarına yapılmasını önlemek amacıyla ilk olarak Avrupa Birliği ülkelerinde ortaya çıkmış bir hesap numarası standardıdır. Avrupa Birliği düzenlemeleri çerçevesinde, ülkeler arasında gerçekleştirilen para transferlerinin hızı ile kalitesini artırmak ve maliyetlerini düşürmek amacıyla IBAN (International Bank Account Number) adı verilen Uluslararası Banka Hesap Numarası standardı geliştirilmiştir. IBAN’ın amacı, Avrupa ülkelerindeki banka ve diğer finansal kurumlar aracılığı ile gerçekleştirilen para transferlerindeki hataları ve bundan doğan gecikmeleri engellemektir. IBAN sayesinde transfer edilen para daha hızlı ve hatasız bir biçimde göndericinin hesabından alıcının hesabına geçmekte; böylece, işlemlerde oluşan hatalardan kaynaklanan bekleme süreleri ve ek maliyetler ortadan kalkmaktadır.

Yukarıdaki şeklinde açıklanan IBAN numarası ile havale yapmak istediğimde IBAN şeysinin algoritmasını merak etmemle başladı her şey. "Yok program sadece IBAN doğruluğunu bulsun; yok IBAN'ın hangi bankaya ait olduğunu da tespit etsin, yok IBAN’ın hangi şubeyi gösterdiğini de aradan belirlesin" diye diye program yazdıkça genişledi. Yeni özellikler eklendi. Halbuki IBAN algoritmasına bakıp çıkacaktım ben?!?! Her neyse, olan oldu artık.

Son olarak; programdaki tüm banka verilerini Türkiye Cumhuriyet Merkez Bankası, Elektronik Fon Transfer - Elektronik Menkul Kıymet Transfer Sistemleri sayfasından Katılımcı Banka Şube Kodları (BaSub) alanından aldığımı belirtmek isterim. Programın özelliklerine gelecek olursak;

- TR kodlu (Türkiye içi) IBAN hesap numaralarının doğruluğunu hesaplama,
- IBAN kodunun hangi bankaya ait olduğunu bulma ve bankanın logosunu gösterme,
- IBAN kodunun hangi şubeye *(Ziraat Bankası, Akbank, HSBC, Bank Asya, Halk Bankası, Garanti Bankası, İş- Bankası ve TEB)* ait olduğunu bulma,
- IBAN sonuçlarını TXT belgesi olarak kaydetme.

**Not 1**: Daha çok tercih edildiğine inandığım ve şube sayısı çok olan bankaların şube bulma özelliğine programda yer vermeme rağmen *Vakıfbank, Yapı Kredi, ING Bank, Finansbank, Denizbank, Albaraka Türk, Kuveyt Türk* bankalarının şube algoritmalarını çözemediğim için bu bankaların şube tespitine yer veremedim. Bulan ya da bilen varsa haber etsin lütfen.

**Not 2**: 64 bit Microsoft Windows 7/8/8.1/10 işletim sistemlerinde Microsoft.ACE.OleDb.12.0 sağlayıcısı yerel makinede kayıtlı değil **(The 'Microsoft.ACE.OLEDB.12.0' provider is not registered on the local machine)** hatası alırsanız eğer, programın sorunsuz çalışabilmesi adına, Microsoft Access Database Engine 2010 Redistributable eklentisini indirmeniz gerekmekte.

{:.tablo-ortali}
| IBAN Kontrol<br>![Versiyon](https://img.shields.io/badge/Versiyon-1.00-blueviolet.svg?style=flat) ![Durum](https://img.shields.io/badge/Durum-Çalışıyor-success.svg?style=flat) | IBAN Kontrol (Proje)<br>![Lisans](https://img.shields.io/badge/Lisans-MIT-blue.svg?style=flat) ![Durum](https://img.shields.io/badge/Proje-Kodlar_Gözden_Gecirilecek-red.svg?style=flat) |
|----------------------------------------- -|-------------------------------------------|
| **MD5**: F649A2A56766D3C46C17F7E25FEE2D19 | **MD5**: E32144A89083CD2AD39F128A82A38602 | 
| **Boyut**: 661.3 KB                       | **Boyut**: 2.6 MB                         |
| **Gereksinimler**: .Net Framework 3.5     | **Gereksinimler**: .Net Framework 3.5     |
| **Platform**: Microsoft Windows           | **Programlama Dili**: C#                  |
| **İndir**: [Link](http://www.umutd.com/programlar/iban-kontrol.zip)         | **İndir**: [Link](http://www.umutd.com/programlar/iban-kontrol-proje.zip)                      |