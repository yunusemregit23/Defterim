# Kişiselleştirme Profili — Elimdeki Verilerle

> Sürüm: 1.0 · Tarih: 2026-08-03
> İstek: *"Beni tanıdığın kadarıyla ayarlamaya çalış."*

---

## 0. Dürüstlük Notu

Bunu baştan söylemem gerekiyor: **seni gerçekten tanımıyorum.** Yaşını,
medeni halini, mesleğinin tam adını, eğitimini bilmiyorum ve bunları
biliyormuş gibi davranmayacağım — uydurmak, "seni tanıyorum" hissi vermek
gerçek kişiselleştirme değil, yanlış güven olur.

Elimde olan tek şey: bu konuşma boyunca **kendi seçtiğin sözlerle** bıraktığın
izler. Aşağıda ikiye ayırdım — **söylediğin** ve **söylediğinden çıkardığım**.
İkincisi tahmin, yanlış olabilir, düzeltirsen hemen değişir.

---

## 1. Doğrudan Söylediklerin (kesin)

| Konu | Söylediğin |
|---|---|
| Kullanım amacı | Kendi işim/girişim **+** ofis/sabit mesai — ikisi birden |
| "2 aşama" tanımı | Aksiyon sonrası devam önerisi (görev zinciri), doğruladın |
| Kapsam | Şimdilik sadece sen kullanacaksın, ürünleşme yok |
| Ton | **Dürüst ve sert** — yumuşatma istemiyorsun |
| Manevi katman | Ölüm/tövbe telkini istiyorsun — düzenli hatırlatma, yumuşak değil |
| Dikkat sorunu | Sosyal medyada çok zaman kaybettiğini kendin söyledin |
| Konum örnekleri | Şantiye (boyama işi) + çarşı/kırtasiye |
| Konum yöntemi | Kendi işaretlediğin yerler, dış veri kaynağı yok |
| İzin ve varsayılanlar | Arka plan konum izni ve 75 m yarıçap onaylandı |
| Sosyal medya hedefi | **Instagram** — engelleme değil, boşluk doldurma + eşik araya girme |

---

## 2. Söylediklerinden Çıkardıklarım (tahmin — işaretli)

Bunlar **kanıt değil çıkarım.** Yanlışsa düzelt, config anında değişir.

### 2.1 "Şantiye" kelimesi tesadüf değil
Örnek olarak rastgele bir şey seçmedin — "şantiyede boyama işi" hem çok
somut hem sektörel bir dil (boya işi genelde inşaat/taşeron/badana-boya
işiyle uğraşan biri ya da böyle bir işi yöneten biri tarafından kullanılır).

→ **Çıkarım:** Kendi işin muhtemelen inşaat/taşeronluk/usta-esnaf tarafında,
ya da bu işleri yöneten/takip eden bir konumdasın. Ofis/sabit mesai + saha işi
birleşimi, klasik "masabaşı + saha" ikili hayatına işaret ediyor.

→ **Etkisi:** Bağlam blokları (`02-OZELLIKLER.md` Cephe 5) sadece "mesai / kendi
işim / kişisel" değil, **"ofis" / "saha"** ayrımını da tanımalı. Saha işleri
zamana değil **konuma** bağlı olduğu için zamanlayıcı bunu ayrı ele almalı —
zaten `05-KONUM.md`'nin var olma sebebi bu.

### 2.2 Dindarlık — yüzeysel değil, günlük pratiğe entegre isteniyor
"Her saat başı" telkin istemen, dini hayatın sana **arka plan bilgisi** değil
**aktif, günlük bir mücadele alanı** olduğunu gösteriyor. Bu tesadüfi bir
özellik isteği değil.

→ **Çıkarım:** Namaz kılıyorsun (yoksa vakit çıpalarının anlamı olmazdı),
Diyanet hesaplama metodunu muhtemelen bekliyorsun (Türkiye'de standart).

→ **Etkisi:** `03-MANEVI-KATMAN.md`'deki namaz vakti metodu varsayılanı
**Diyanet** olarak sabitleniyor (aksini söylemedikçe).

### 2.3 Sosyal medya hedefi — artık tahmin değil, kesin
Sana sormadım, sen açtın; sonra doğrudan söyledin: **Instagram.** Bu artık
§1'e taşınabilecek kesin bir bilgi, ama iz sürme mantığını göstermesi için
burada bırakıyorum — önce çıkarım boştu ("hangi uygulama bilmiyorum, ölçerek
bulunsun"), sonra sen doldurdun.

→ **Kesinleşen:** Hedef uygulama Instagram. `04-DIKKAT.md`'deki tüm özellikler
(boşluk doldurma, eşik araya girme, niyet sorusu, sızıntı raporu) öncelikle
Instagram için etkinleşecek. Diğer uygulamalar (YouTube, X, TikTok) yine
ölçülerek eklenir — varsayımla değil.

### 2.4 Sert ton tercihi — tutarlı bir kişilik sinyali
"Sert" istemen tek bir yerde kalmadı — bunu ton sorusuna da, manevi katman
isteğine de (tövbe telkini, yumuşak değil) taşıdın. Bu, **kararlı bir tercih**,
tek seferlik bir cevap değil.

→ **Etkisi:** Bütün katmanlarda (dünyevi, manevi, dikkat) varsayılan dil
**doğrudan, yorumsuz, rakamla konuşan** olacak. "Belki düşünebilirsin" değil,
"3. kez erteliyorsun, ya yap ya sil" tarzı — zaten önceki dokümanlarda bu
sesle yazdım, burada resmileştiriyorum.

---

## 3. Bunlardan Çıkan Somut Config

Kodun ilerde okuyacağı ilk varsayılan profil:

```yaml
profil:
  dil: tr
  ton: sert            # yumuşatma yok, öğüt yok, rakamla konuş

bağlamlar:
  - ofis        # sabit mesai, zaman bazlı
  - saha        # şantiye/iş sahası, KONUM bazlı (05-KONUM.md)
  - kendi_isim  # esnek, zaman bazlı ama düşük öncelikli slotlara girmez
  - kişisel

bildirim_bütçesi:
  dünyevi: 5          # 4-6 aralığının ortası, veri birikince ayarlanır
  manevi: 5           # namaz vakti çıpaları
  saat_başı_mod: kapalı   # 03-MANEVI-KATMAN.md §3 Katman C, varsayılan kapalı

manevi_katman:
  vakit_metodu: diyanet     # tahmin — teyit gerekirse değişir
  havf_reca_dengesi: aktif
  tövbe_defteri: aktif, cihazda şifreli

dikkat_katmanı:
  hedef_uygulamalar: ["Instagram"]   # kesin — kullanıcı doğrudan söyledi
  engelleme: hayır          # kanıtlanmış şekilde işe yaramıyor, bkz 04-DIKKAT.md §2
  boşluk_doldurma: aktif    # izin gerektirmeyen, en etkili özellik
  eşik_araya_girme: aktif   # Wellspent mekanizması — sorar, engellemez
  günlük_sınır: kullanıcı_belirler   # sıfır hedef yok, Wellspent bulgusu

konum_katmanı:
  yöntem: kendi_işaretlediğin_yerler
  varsayılan_yarıçap_m: 75
  ön_tanımlı_kategori: ["şantiye", "kırtasiye"]   # senin verdiğin örneklerden
```

---

## 4. Bilerek Varsaymadıklarım

Bunları **söylemediğin için tahmin etmiyorum** — yanlış tahmin, doğru
tahminden daha kötü çünkü sistemi baştan yanlış kurar:

- Yaşın, medeni halin, kaç çocuğun olduğu
- İşinin tam adı/unvanı (taşeron mu, usta mı, saha şefi mi, esnaf mı)
- Mesai saatlerinin tam aralığı (09:00–18:00 mi, vardiyalı mı)
- Hangi mezhep/meşrepten pratik ettiğin (külliyat seçimini etkiler,
  `03-MANEVI-KATMAN.md` §10'daki açık soru hâlâ açık)
- Hangi sosyal medya uygulamasının asıl sorun olduğu

Bu liste boş değil — **eksik bilgiyi doldurmanın doğru yolu tahmin değil,
ölçmek.** Uygulama açıldıktan sonraki 2-3 hafta, yukarıdaki config'i senin
gerçek davranışına göre kendi kendine kalibre edecek (`02-OZELLIKLER.md`
Cephe 7 ve 9'daki sessiz öğrenme mantığı).

---

## 5. Değişirse

Bu profil taş değil. Herhangi bir satırı yanlış bulursan tek cümlede
düzelt — "sert değil nötr olsun" ya da "saha değil sadece ofis" dersen
bu doküman ve ileride yazılacak kod aynı oturumda güncellenir.
