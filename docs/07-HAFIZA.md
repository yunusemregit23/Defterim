# AI Hafızası — Dağınık Olanın Toparlanması

> Sürüm: 1.0 · Tarih: 2026-08-03
> Soru: *"AI hafızası yapıldı mı peki?"*
> Cevap: **Kodu yok — depoda sadece doküman var, hiçbir şey kodlanmadı.**
> Ama tasarımı zaten var, sadece altı dokümana dağılmıştı. Bu doküman onu
> tek yerde toplar.

---

## 0. Önce Bir Ayrım — Sen Zaten Doğru Soruyu Sordun

"AI hafızası" iki farklı şey olabilir ve sordum, netleşti: **davranışını
öğrenen istatistiksel hafıza.** Diğer ihtimal — ChatGPT/Claude tarzı "geçmiş
sohbetlerini hatırlayan asistan hafızası" — **bilerek yok.** `00-ARASTIRMA.md`
§6'daki yapmayacaklar listesinde "sohbet arayüzü" kapalı kapı; Defterim bir
asistanla konuşmuyorsun, bir deftere yazıyorsun. Hafıza sohbeti değil,
**davranışını** hatırlıyor.

---

## 1. Şu Ana Kadar Nerede Neyin Tasarlandığı

Hiçbiri kodlanmadı ama hiçbiri de sıfırdan değil — tasarım kararı olarak
altı dokümanda zaten var:

| Doküman | Ne öğreniyor |
|---|---|
| `02-OZELLIKLER.md` Cephe 3 | Süre tahminlerinin gerçekle farkı → kişisel katsayı |
| `02-OZELLIKLER.md` Cephe 7 | Hangi saatte iş bitiyor/erteleniyor → sessiz enerji haritası |
| `02-OZELLIKLER.md` Cephe 8 | Erteleme sayısı → 3. kez ertelenince yüzleştirme tetiklenir |
| `02-OZELLIKLER.md` Cephe 9 | Dokunulmamış/çürük işler, haftalık plan/bitirme rakamları |
| `02-OZELLIKLER.md` Cephe 10 | Rutin tutturma → bildirim seyreltme kararı |
| `03-MANEVI-KATMAN.md` §5-6 | Haftalık plan-bitirme oranı, Tövbe Defteri tekrar sayısı |
| `04-DIKKAT.md` Özellik 3-5 | "Sadece bakıyorum" sayacı, aynı boşlukta tekrar kaydırma |
| `05-KONUM.md` §5 | Bir yerden kaç kez geçip görevi yapmadığın |

Sekiz farklı yerde sekiz farklı "hafıza" tarif ettim. Aslında hepsi **aynı
mekanizmanın** yedi farklı görünümü: *bir olayı gözlemle, say, örüntü
oluşunca konuş.*

---

## 2. Tek Mekanizma — Konsolide Edilmiş Hali

```
   Olay olur (görev bitti / ertelendi / bildirim gönderildi / boşluktan
              geçildi / yer ziyaret edildi / not yazıldı)
        ↓
   Cihazda, deterministik kodla SAYILIR ve KAYDEDİLİR (LLM yok, sadece SQL)
        ↓
   Eşik aşılınca (3. erteleme, 3 hafta tutturma, 30 gün dokunulmama...)
   ilgili cephenin kuralı TETİKLENİR
        ↓
   Metne çevrilmesi gerekiyorsa (haftalık özet, aşama-2 önerisi) —
   SADECE BURADA, sadece özetlenmiş sayılar cihaz dışına, buluttaki
   LLM'e gider. Ham geçmiş asla gitmez.
```

**Kritik ayrım — hafıza LLM'de değil, SQL'de yaşıyor.** Bulut LLM'e giden
şey ham log değil, tek satırlık özet: *"kullanıcı bu hafta 23 görev
planladı, 11'ini bitirdi"* — geçmiş görevlerin içeriği değil, sayısı.
Bu, `00-ARASTIRMA.md` §4.3'teki "LLM çözücü değil çevirmen" ilkesinin
hafıza tarafındaki karşılığı.

---

## 3. Konsolide Şema

Önceki dokümanlardaki veri modeline (`00-ARASTIRMA.md` §5) ek olarak,
"hafıza" olarak adlandırılabilecek somut tablolar:

```
TaskStat        — {görev_türü, tahmin_süre, gerçek_süre, tarih}
                  → Cephe 3'ün kişisel katsayı hesapladığı ham veri

EnerjiGözlem    — {saat_dilimi, başlatıldı_mı, bitti_mi, ertelendi_mi}
                  → Cephe 7'nin 3-4 haftada enerji haritası çıkardığı veri

ErtelemeSayacı  — {task_id, erteleme_sayısı, son_erteleme_tarihi}
                  → Cephe 8/9'un yüzleşme/budama tetiklediği sayaç

RutinSerisi     — {routine_id, tutturma_sayısı, son_hatırlatma_gerekti_mi}
                  → Cephe 10'un seyreltme kararı verdiği seri

DikkatOlayı     — {uygulama, boşluk_id, sonuç: çıktı/devam_etti}
                  → 04-DIKKAT §5'in örüntü tespiti yaptığı log

YerZiyareti     — {place_id, tarih, bağlı_görev_yapıldı_mı}
                  → 05-KONUM §5'in "3 kez geçtin, yapmadın" tespiti

TövbeSayacı     — {anahtar_kelime/etiket, tekrar_sayısı, ay}
                  → 03-MANEVI-KATMAN §6'nın "bu ay 4. kez" tespiti
```

Hepsi **aynı veritabanında**, `Note`/`Task` tablolarıyla birlikte.
Ayrı bir "hafıza sistemi" değil — aynı SQLite'ın içinde birkaç ek tablo.

---

## 4. Nerede Yaşıyor, Kim Görüyor

| Soru | Cevap |
|---|---|
| Nerede duruyor | Cihazda, `expo-sqlite` (Drizzle ORM ile) — `00-ARASTIRMA.md` §4.1 |
| Buluta çıkar mı | **Hayır.** Kişisel kullanım kararı (§11) — backend yok, senkron yok |
| LLM bunu görüyor mu | Sadece **özetlenmiş sayı** olarak, ihtiyaç anında (haftalık rapor, aşama-2 önerisi). Ham tablo asla prompt'a girmez |
| Tövbe Defteri farklı mı | Evet — **ayrıca şifreli.** Diğer tablolar normal SQLite'ta, bu biri SQLCipher ile |
| Silinebilir mi | Evet, tamamı — ayarlardan "hafızayı sıfırla" tek dokunuş, `Note` hariç (o zaten ayrı, değişmez ilke) |

### Şifreleme — teknik doğrulama

`03-MANEVI-KATMAN.md`'de "Tövbe Defteri cihazda şifreli" dedim ama teknik
olarak nasıl yapılacağını o zaman belirtmemiştim. Şimdi doğruladım:

- `expo-sqlite`, **SQLCipher**'ı destekliyor (256-bit AES, tüm veritabanı
  şifreleme). `app.json`'da `useSQLCipher` config'i açılıp `expo prebuild`
  çalıştırılması gerekiyor.
- **Kısıt:** SQLCipher **Expo Go'da çalışmıyor** — development build
  şart. Bu yeni bir kısıt değil; `00-ARASTIRMA.md` §4.2'de zaten arka plan
  bildirimleri için development build zorunluydu. Aynı gemi.
- Pratik karar: **Tövbe Defteri kendi ayrı SQLCipher veritabanında**, geri
  kalan hafıza tabloları normal (şifresiz) `expo-sqlite`'ta. İkisini aynı
  DB'de karıştırmak yerine ayırmak, performans ve karmaşıklık açısından
  daha temiz.

---

## 5. Ne Zaman "Öğrenmiş" Sayılır — Süre Gerçeği

Bu hafızanın hiçbir parçası **gün 1'de** anlamlı değil. Önceki dokümanlarda
zaten söylenmişti, burada tek yerde toparlıyorum:

| Tablo | Anlamlı olması için gereken süre |
|---|---|
| TaskStat (süre katsayısı) | ~10-15 tamamlanmış görev, aynı türden |
| EnerjiGözlem (kronotip) | 3-4 hafta |
| ErtelemeSayacı | Anında (3. erteleme = tetik, ilk günden çalışır) |
| RutinSerisi (seyreltme) | 3-4 hafta düzenli tekrar |
| DikkatOlayı | 1-2 hafta |
| YerZiyareti | Konuma bağlı, kaç kez geçtiğine göre değişir |
| TövbeSayacı | Aylık pencere |

**Sonuç:** v0.1'de bu tablolar **boş açılır** ve dürüstçe boş kalır.
Uygulama ilk haftalarda "henüz yeterli veri yok" der, sahte bir kalıp
tahmin üretmez. `02-OZELLIKLER.md`'nin "önce veri, sonra zeka" ilkesi
burada da geçerli.

---

## 6. Sürüm Yerleşimi — Yeni Değil, Referans

Bu doküman yeni bir roadmap açmıyor; her tablo zaten kendi cephesinin
sürümüne bağlı (`02-OZELLIKLER.md` §"Sürümlere Dağılım" esas alınır):

| Sürüm | Hangi hafıza tabloları aktif |
|---|---|
| v0.1 | Hiçbiri — sadece `Note`/`Task` var, hafıza yok |
| v0.2 | `TaskStat` (Cephe 3), `ErtelemeSayacı` başlar |
| v0.3 | `EnerjiGözlem` başlar, `DikkatOlayı`, `YerZiyareti`, manevi yüzleşme rakamları |
| v1.0 | `RutinSerisi` seyreltme kararı verecek kadar olgunlaşır, Tövbe Defteri şifreli DB |

---

## 7. Özet — Soruna Doğrudan Cevap

> **Kod: hayır, hiçbir şey yazılmadı.**
> **Tasarım: evet, zaten vardı — sadece dağınıktı, şimdi tek dokümanda.**
> **Ne tür hafıza: sohbet değil, davranış.** LLM seni "hatırlamıyor";
> SQL tablosu senin süre tahminlerini, ertelemelerini, enerji örüntünü
> sayıyor ve eşik aşılınca deterministik kod konuşuyor. LLM sadece,
> gerektiğinde, o sayıları cümleye döküyor.
