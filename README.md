# Defterim

Aklına geleni tek bir yere serbestçe yazdığın; uygulamanın bunu takvimine
oturttuğu, doğru anda hatırlattığı ve bir sonraki adımı önerdiği AI destekli
mobil iş defteri.

> **Durum:** Araştırma aşaması. Henüz kod yok.

## Fikir

Hatırlatıcılar söyleneni yapar, planlayıcılar disiplin ister, not defterleri
unutur. Defterim üçünün arasındaki köprüyü kurar:

1. **Yaz** — serbest metin, biçim yok, sürtünme yok.
2. **Yerleşsin** — AI metinden görevi çıkarır, deterministik zamanlayıcı takvime oturtur.
3. **Devamı gelsin** — aksiyonu aldıktan (veya almadıktan) sonra uygulama bir
   sonraki adımı önerir.

Defterim'in iki sütunu var: **dünyevi iş katmanı** (yukarıdaki) ve
**manevi katman** — tezekkür-ü mevt, muhasebe ve tövbe. İkisi aynı defterde,
aynı motoru paylaşır.

## Dokümanlar

- [`docs/02-OZELLIKLER.md`](docs/02-OZELLIKLER.md) — **asıl tasarım dokümanı.**
  10 tıkanma noktası ve her birini çözen özellik. Bir özelliğin burada karşılığı
  yoksa yapılmaz.
- [`docs/00-ARASTIRMA.md`](docs/00-ARASTIRMA.md) — ürün fikri, mimari kararlar,
  kapsam sözleşmesi ve yapmayacaklar listesi.
- [`docs/03-MANEVI-KATMAN.md`](docs/03-MANEVI-KATMAN.md) — tezekkür-ü mevt ve
  muhasebe sütunu: namaz vakti çıpaları, külliyat kuralları, Tövbe Defteri.
- [`docs/04-DIKKAT.md`](docs/04-DIKKAT.md) — sosyal medya ve zaman sızıntısı:
  neden engelleme çalışmıyor, boşluk doldurma stratejisi, eşik araya girme.
- [`docs/01-PAZAR.md`](docs/01-PAZAR.md) — pazar araştırması (referans): rakipler,
  popülerlik sebepleri, tutundurma verileri.

## Yol Haritası

| Sürüm | Kapsam |
|---|---|
| v0.1 | Çalışan defter: yazma, görev çıkarımı, yerel bildirim |
| v0.2 | Otomatik takvim yerleşimi, rutinler, bildirim bütçesi |
| v0.3 | İki aşamalı öneri motoru, haftalık geri bildirim |
| v1.0 | Kişiselleştirme, takvim entegrasyonu, senkron |

Ayrıntı ve kapsam sınırları için araştırma dokümanına bakın.
