# Konum Katmanı — Yerinde Hatırlatma

> Sürüm: 1.0 · Tarih: 2026-08-02
> İstek: *"AI hatırlatıcı konum bilgisi aldığında hatırlatma yapsın. Örnek 1:
> hesap makinesi alınacak — çarşıda veya yakın bir kırtasiyede alınabilir.
> Örnek 2: şantiyede boyama işi var — şantiyede bulununca o iş hatırlatılsın."*

---

## 1. Önce Ayrım: Bu Aslında İki Farklı İstek

Verdiğin iki örnek, teknik olarak **birbirinden tamamen farklı** iki problem.
Bunları aynı özellik sanıp tek çözümle geçersek biri mutlaka bozuk çıkar.

| | Örnek 1 — Hesap makinesi | Örnek 2 — Şantiye boyama |
|---|---|---|
| **Konum türü** | Belirsiz, **kategori** ("bir kırtasiye") | Belirli, **tek nokta** (senin şantiyen) |
| **Aday sayısı** | Şehirde onlarca kırtasiye | Tek yer |
| **Nasıl bulunur** | Anlık POI (yer) araması gerekir | Sen bir kez işaretlersin, biter |
| **Değişkenlik** | Nerede olduğuna göre en yakını değişir | Sabit |
| **Zorluk** | **Yüksek** — dış veri kaynağı gerekir | **Düşük** — klasik geofence |

> **Sonuç:** Örnek 2 (şantiye) bugün var olan teknolojiyle, tamamen offline,
> kolayca yapılabilir. Örnek 1 (kırtasiye) gerçek bir mühendislik problemi ve
> `00-ARASTIRMA.md`'deki "sadece cihazda, backend yok" kararıyla gerginlik
> yaratıyor. İkisini ayrı ayrı çözüyorum.

---

## 2. Örnek 2 — Sabit Nokta (Şantiye): Kolay Olan Taraf

### Nasıl çalışır
Bu, **klasik geofencing** — Apple Hatırlatıcılar'ın 2011'den beri yaptığı şey.
Cihazın GPS/ağ konumu tanımlı bir dairesel alanın (geofence) içine girip
çıktığını algılıyor; sınırı geçince bildirim tetikleniyor.

### Defterim'de akış
```
   Sen yazarsın:  "şantiyede boyama işi var"
   Defterim:      → "Bunu bir yere mi bağlayayım? Şantiye demiştin,
                     haritadan işaretle." [harita açılır, sen bir kez dokunursun]
   Sonra:         Şantiyeye her girişinde: "Boyama işi — buradasın, şimdi tam zamanı."
```

- Konum **sen** işaretlersin (harita üstünde dokunma). AI tahmin etmez —
  "şantiye" gibi öznel bir yeri doğru tahmin etmesi imkânsız.
- Bir kez işaretlenen yer **kalıcı** olarak saklanır: "Şantiye", "Ev", "Ofis"
  gibi kişisel yer listesi oluşur, sonraki notlarda AI bunları tanır.
- Tamamlanınca geofence **otomatik silinir** — iş bitince "şantiyeye her
  girişte" bildirimi almaya devam etmezsin.

### Teknik gerçeklik — platform sınırları

| Platform | Sınır | Kaynak |
|---|---|---|
| **iOS** | Uygulama başına **aynı anda en fazla 20 bölge** izlenebilir | Core Location, sistem genelinde paylaşılan kaynak |
| **Android** | Uygulama başına **aynı anda en fazla 100 bölge** | Geofencing API |

20 sınırı senin kullanımın için **sorun değil** — kaç tane "şantiye", "iş yeri",
"belirli müşteri adresi" gibi sabit nokta biriktireceğini düşün, muhtemelen
tek haneli sayıda kalır. Ama mimari not: **eski/tamamlanmış geofence'ler
otomatik temizlenmeli**, yoksa yıllar içinde 20 sınırına çarpılır.

### Pil etkisi — iyi haber
Sürekli GPS pil açısından en verimsiz yöntem. Buna karşılık:

- **Geofencing**, cihaz sabitken veya tanımlı alan içindeyken takip sıklığını
  düşürerek enerji kullanımını **%20–30 sınırlıyor.**
- iOS ve Android'in ikisi de geofence olayı oluştuğunda uygulamayı **sürekli
  aktif tutmadan** uyandırabilen sofistike sistemlere sahip — arka planda
  çok daha az güç harcayarak konum tabanlı işlevi sağlıyorlar.

Yani şantiye örneği hem teknik olarak kolay hem pil dostu. `00-ARASTIRMA.md`
§4.2'deki "önceden zamanlanmış yerel bildirim" mimarisiyle de uyumlu —
geofence tetiklemesi zaten OS'un kendi mekanizması, bizim arka planda
sürekli çalışmamıza gerek yok.

### Expo tarafında
`expo-location` + `expo-task-manager` ile bölge izleme (region monitoring)
yapılabiliyor; arka plan konumu için iOS'ta `UIBackgroundModes: location`,
Android'de `ACCESS_BACKGROUND_LOCATION` izni gerekiyor. **Bu izin isteğinin
kullanıcıya (yani sana) neden gerektiğini net açıklaması şart** — aksi halde
mağaza incelemesinde ya da senin kendi güveninde sorun çıkarır.

---

## 3. Örnek 1 — Kategori (Kırtasiye/Çarşı): Zor Olan Taraf

### Neden zor
"Yakındaki bir kırtasiye" demek, telefonun **"şu an neredeyim ve yakınımda
hangi dükkanlar var"** sorusuna cevap vermesi demek. Bu, geofencing'in
çözdüğü problem değil — bu bir **yer arama (POI search)** problemi ve
POI verisi telefonda değil, bir haritada/veritabanında duruyor.

### İki gerçekçi yol var

#### Yol A — Çevrimiçi POI sorgusu (OpenStreetMap Overpass API)

- **Ücretsiz**, cömert limitli. Google Places ise **1000 sorguda $7.**
- Kapsamı: dükkan, market, eczane, vb. 20'den fazla kategoriyle sorgulanabilir.
- **Türkiye kapsamı değişken** — büyük şehirlerde iyi, küçük yerleşimlerde
  ve özellikle "kırtasiye" gibi niş kategorilerde eksik/güncel olmayan
  veri riski var. OSM gönüllü emeğiyle güncellenen bir veri tabanı.
- **Bunun bedeli:** anlık konumun bir sunucuya (Overpass/OSM altyapısı)
  sorgu olarak gitmesi gerekiyor. `00-ARASTIRMA.md`'deki "her şey cihazda,
  backend yok" kararını **kısmen** deliyor — bu tek özellik için dışarıya
  bir ağ isteği çıkıyor.

#### Yol B — Kendi kısıtlı POI listen (offline, gizlilik dostu, ama dar)

- Sen zaman içinde "sık gittiğim kırtasiyeler" gibi birkaç yeri kendin
  işaretlersin (Örnek 2'deki gibi, ama kategori etiketiyle: `#kırtasiye`).
- Tamamen offline, sıfır ağ isteği, sıfır üçüncü taraf veri kaynağı.
- **Dezavantaj:** sadece senin daha önce gittiğin yerleri bilir. Hiç
  gitmediğin bir mahallede "yakında kırtasiye var mı" diyemez.

### Karar önerisi

> **v0.2'de Yol B, sonra isteğe bağlı Yol A.**
>
> Gerekçe: Sen zaten belirli yerlerde dolaşıyorsun (ev, iş, şantiye, sık
> gittiğin çarşı). Birkaç haftalık kullanımda "sık gittiğin 5-6 dükkan"
> kendiliğinden birikir — çünkü zaten oralardan geçerken bildirim tetiklenip
> tetiklenmediğini görürsün ve yenisini eklersin. Bu, "sıfır kurulum" ilkesiyle
> de uyumlu: gerçek kullanım, veriyi organik biriktirir.
>
> Yol A (gerçek zamanlı OSM sorgusu) **hiç gitmediğin bir yerde** işe yarar
> ama tek bir ağ bağımlılığı katıyor. Bunu **açıkça opsiyonel** bir ayar
> yapmak doğru: "Bilmediğim yerlerde de ara" anahtarı kapalı başlar, açarsan
> anlık konumun (sadece o sorgu anında) OSM'e gider.

### Defterim'de akış (Yol B ile)

```
   Sen yazarsın:  "hesap makinesi alınacak"
   Defterim:      Belirli bir yer bulamaz → genel not olarak kalır,
                   konuma bağlanmaz. Ama:

   Sen bir kırtasiyenin önünden geçersin (herhangi biri, işaretli değil).
   Defterim:      hiçbir şey yapmaz — henüz bu yeri "kırtasiye" olarak bilmiyor.

   Sen isterse o an uygulamayı açıp "burası kırtasiye" diye 1 dokunuşla
   etiketlersin. Bundan sonra:

   Defterim:      Bu noktadan (veya benzer şekilde etiketlediğin başka
                   kırtasiyelerden) geçtiğinde: "Hesap makinesi — buradasın,
                   şimdi alabilirsin."
```

Bu, tek tek mağaza değil **kategori** biriktirir: "kırtasiye" etiketli 3 yer
işaretlediysen, üçünün de yakınından geçtiğinde aynı hatırlatma tetiklenir.
Bir görev birden fazla geofence'e bağlı olabilir (`Occurrence` başına
1'den N'e coğrafi tetikleyici).

---

## 4. Ortak Mimari — İkisini Aynı Veri Modeline Oturtmak

`00-ARASTIRMA.md` §5'teki veri modeline yeni bir kavram ekleniyor:

```
Place        — kullanıcının işaretlediği yer (nokta + yarıçap + etiket)
              örn. {ad: "Şantiye", tür: "sabit"}
              örn. {ad: "Kırtasiye - Migros yanı", tür: "kategori:kırtasiye"}

Task
 └─ trigger: zaman VEYA konum VEYA ikisi birden
              "yarın 14:00" | "Şantiye'ye girince" | "kırtasiye kategorisinde,
              10 gün içinde geçersen"
```

**Süre sınırı önemli:** "hesap makinesi alınacak" gibi konum tetikli görevler
süresiz beklerse anlamsızlaşır. Varsayılan: konum tetikleyicisi **14 gün**
sonra devre dışı kalır ve normal zaman bazlı hatırlatmaya döner (*"hâlâ
almadın, çarşıya bir uğrama planlayayım mı?"*) — böylece geofence sonsuza
kadar arka planda asılı kalmaz.

---

## 5. İki Aşamalı Öneri Motoruyla Bağlantı

Konum tetiklemesi de `00-ARASTIRMA.md` §3'teki motoru kullanır:

| Aşama 1 (tetikleme) | Aşama 2 (sonuca göre) |
|---|---|
| Şantiyeye girdin, bildirim geldi | **Yapıldı** → kapat, geofence silinir |
| Şantiyeye girdin, bildirim geldi | **Ertelendi** (2. kez aynı yerde) → *"Bu işi şantiyede 2 kez atladın. Süre mi yetmiyor, malzeme mi eksik?"* |
| Kırtasiye yakınından 3 kez geçtin, hiç almadın | Örüntü: *"3 kez kırtasiye yakınından geçtin, almadın. Bu iş gerçekten senin mi?"* — Cephe 8'deki (`02-OZELLIKLER.md`) aynı mantık |

---

## 6. Sürüm Yerleşimi

| Sürüm | Kapsam | Gerekçe |
|---|---|---|
| **v0.2** | Örnek 2 — Sabit nokta geofence (harita üstünde işaretle) | Basit, offline, pil dostu, mevcut teknoloji |
| **v0.3** | Örnek 1 — Yol B (kendi işaretlediğin kategori yerler) | Organik veri birikimi, hâlâ offline |
| **v1.0** | Örnek 1 — Yol A (OSM canlı sorgu, opsiyonel anahtar) | Ağ bağımlılığı gerektirdiği için en sona; kişisel kullanım kararına en çok gerilim yaratan parça |

---

## 7. Açık Sorular

1. **Yol A'yı (canlı OSM sorgusu) hiç istiyor musun,** yoksa "sık gittiğim
   yerler" (Yol B) senin gerçek kullanımın için yeterli mi? Bu, v1.0'da bir
   iş kalemi ekleyip eklemeyeceğimizi belirliyor.
2. **Konum izni endişen var mı?** Arka plan konum izni (`her zaman izin ver`)
   hem iOS hem Android'de kullanıcıya en "ağır" görünen izin türü. Kişisel
   kullanımda sorun değil ama bilerek onaylaman gerekiyor.
3. **Geofence yarıçapı ne olsun?** Şantiye gibi büyük bir alan için 100-150 m
   makul; küçük bir dükkan için 50 m yeterli. Varsayılan öneri: 75 m,
   yer bazında değiştirilebilir.

---

## 8. Kaynaklar

**Platform sınırları ve geofencing mekanizması**
- [Geofencing iOS: Understanding the Limitations — Radar](https://radar.com/blog/limitations-of-ios-geofencing)
- [CLCircularGeographicCondition 20 Condition Limit — Apple Developer Forums](https://developer.apple.com/forums/thread/769113)
- [Create and monitor geofences — Android Developers](https://developer.android.com/develop/sensors-and-location/location/geofencing)
- [How to Use Location-Based Reminders on iPhone — iPhone Life](https://www.iphonelife.com/blog/32671/tip-day-how-set-and-use-location-based-reminders)

**Pil etkisi**
- [About background location and battery life — Android Developers](https://developer.android.com/develop/sensors-and-location/location/battery)
- [How GPS Usage and Geofencing Affect Mobile Device Battery Life — Hubstaff](https://hubstaff.com/blog/employee-gps-tracking-battery-life/)
- [Geofencing Done Right: 7 Mistakes That Kill Battery Life — Glance](https://thisisglance.com/blog/geofencing-done-right-7-mistakes-that-kill-battery-life)

**POI arama ve maliyet**
- [OpenStreetMap Has a Free API — Build Maps Without Google — DEV Community](https://dev.to/0012303/openstreetmap-has-a-free-api-build-maps-without-google-no-key-no-billing-1j1c)
- [Google Places API Alternatives: Which POI API Should You Use in 2026? — DEV Community](https://dev.to/geoapify-maps-api/google-places-api-alternatives-which-poi-api-should-you-use-in-2026-hd4)
- [Geoapify as an Alternative to Google Places API](https://www.geoapify.com/geoapify-as-a-google-places-api-alternative/)

**Expo/React Native uygulaması**
- [expo-location — npm](https://www.npmjs.com/package/expo-location)
- [Expo Location Guide: Permissions, GPS, and Geofencing — Anthony Coffey](https://coffey.codes/articles/building-location-based-features-using-expo-location)
- [GeoFencing in React Native — Medium](https://medium.com/readytowork-org/geofencing-in-react-native-4d8cf42fe90c)
