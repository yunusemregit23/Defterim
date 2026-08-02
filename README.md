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

## Dokümanlar

- [`docs/00-ARASTIRMA.md`](docs/00-ARASTIRMA.md) — ürün fikri, mimari kararlar,
  kapsam sözleşmesi ve yapmayacaklar listesi.
- [`docs/01-PAZAR.md`](docs/01-PAZAR.md) — derin pazar araştırması: rakipler,
  kullanıcı sayıları, popülerlik sebepleri, tutundurma verileri, persona dikeyi.

## Yol Haritası

| Sürüm | Kapsam |
|---|---|
| v0.1 | Çalışan defter: yazma, görev çıkarımı, yerel bildirim |
| v0.2 | Otomatik takvim yerleşimi, rutinler, bildirim bütçesi |
| v0.3 | İki aşamalı öneri motoru, haftalık geri bildirim |
| v1.0 | Kişiselleştirme, takvim entegrasyonu, senkron |

Ayrıntı ve kapsam sınırları için araştırma dokümanına bakın.
