---
layout: post
title: Artan ve Azalan Hisseler
date: 2025-03-02 03:43 +0300
categories: Programlar
tags: Borsa, BIST, Borsa İstanbul, Midas, Hisse, Hisse Senedi
excerpt: Az kodla çok iş yapılan Python'da basit bir kod parçasıyla web scraping ve BeatifulSoup'la verileri ayrıştırma paha biçilemez. C# veya Java'da ekstra efor sarf edip yapılacak pek çok şey Python'da sahiden çok daha kolay yapılabiliyor...
---

![artan-ve-azalan-hisseler](/images/programlar/artan-ve-azalan-hisseler.png){: width="65%"}

Az kodla çok iş yapılan Python'da basit bir kod parçasıyla web scraping ve BeatifulSoup'la verileri ayrıştırma paha biçilemez. C# veya Java'da ekstra efor sarf edip yapılacak pek çok şey Python'da sahiden çok daha kolay yapılabiliyor.

Aslında okuduğum bir yatırım kitabında "en çok yükselen ve düşen hisselerin olduğu alana bakmayın. Hatta o alan ekranınızdan kaldırın" yazıyordu. Oldum olası bu alanlara bakmasam, hatta bakmayı sevmesem de, buna bakan kişiler olduğunu tahmin ediyorum. Bu nedenle de Borsa İstanbul'da (BIST) en çok yükselen ve alçalan hisseleri, istenen değere göre gösteren bir program yazmak istedim.

Kodları çalıştırmak için [Repl.it](https://replit.com) sitesini öneririm. Buradaki veya Github'a eklediğim kodu kopyalarak kodları yürütebilirsiniz. Ayrıyetten, tüm bilgileri Midas'ın web sitesinden çektiğimi ve verilerin (seans vaktinde) 15 dakika gecikmeli olduğunu belirtmek isterim.

**\*** Uygulama, ilk versiyonda Python'daki Request modülüyle veri çekiyordu. Ancak Midas web sitesi bu modüle engelleme getirdiği için kodlar çalışmamaya başladı. Cloudflare'in anti-bot sayfasını atlamak için cloudscraper modülüne geçtim. Sayfa istemini sorunsuz yapabildim ve kodlar yeniden çalışmaya başladı.<br>

```python
import datetime
import locale
import bs4
import cloudscraper

locale.setlocale(locale.LC_ALL, 'TR-tr.UTF-8')
URL = "https://www.getmidas.com/canli-borsa/en-cok-artan-hisseler"


def _web_sayfasini_indir() -> str:
    try:
        with (cloudscraper.create_scraper() as scraper):
            response = scraper.get(URL)
            response.raise_for_status()
            return response.text
    except cloudscraper.exceptions.CloudflareChallengeError:
        return "Web sayfası indirilemedi! İnternetiniz var mı?"


def _verileri_duzenle() -> zip:
    beautiful_soup = bs4.BeautifulSoup(_web_sayfasini_indir(), "html.parser")
    tum_hisseler = beautiful_soup.select("a.title.stock-code")
    gunluk_degisim_orani = beautiful_soup.select("td.dailyChangePercent")

    return zip(tum_hisseler, gunluk_degisim_orani)


def _ondalikli_sayiya_donustur(oran: str) -> float:
    ondalikli_oran = oran.replace('%', '').replace(",", ".")
    try:
        return float(ondalikli_oran)
    except ValueError:
        return 0.0


def _verileri_sirala(veriler, oran) -> list:
    return sorted(veriler, key=lambda x: x["Oran"], reverse=oran >= 0)


def _verileri_indeksle(oran: float):
    veriler = []
    for hisse, degisim in _verileri_duzenle():
        degisim_orani = _ondalikli_sayiya_donustur(degisim.text.strip())
        if (0 < oran <= degisim_orani) or (0 > oran >= degisim_orani):
            sozluk = {"Hisse": hisse.text, "Oran": degisim_orani}
            veriler.append(sozluk)

    return _verileri_sirala(veriler, oran)


def _bugun():
    mevcut_gun = datetime.date.today()
    gun = mevcut_gun

    if mevcut_gun.weekday() == 5:
        gun = mevcut_gun - datetime.timedelta(days=1)
    elif mevcut_gun.weekday() == 6:
        gun = mevcut_gun - datetime.timedelta(days=2)

    return gun.strftime("%d.%m.%Y %A")


def hisseleri_yazdir(oran: float):
    bugun = _bugun()
    ek_bilgi = "Veriler 15 dakika gecikmelidir"

    if oran > 0:
        print(f"[{bugun}] En Çok Artan Hisseler (* {ek_bilgi})")
    else:
        print(f"[{bugun}] En Çok Düşen Hisseler (* {ek_bilgi})")

    for hisse in _verileri_indeksle(oran):
        print(f"{hisse['Hisse']}: %{hisse['Oran']}")


if __name__ == "__main__":
    hisseleri_yazdir(-2)
```
