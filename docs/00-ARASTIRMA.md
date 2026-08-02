# Defterim — Ürün ve Teknoloji Araştırması

> Sürüm: 0.1 · Tarih: 2026-08-02 · Durum: Karar bekleyen sorular var (bkz. §11)

---

## 1. Tek Cümlelik Ürün Tanımı

**Defterim**, aklına geleni tek bir yere serbestçe yazdığın; uygulamanın bunu
takvimine oturttuğu, doğru anda hatırlattığı ve *"şimdi tam olarak şunu yap"*
diyerek seni harekete geçirdiği bir mobil iş defteridir.

Hatırlatıcı değil — **hatırlatıcı + planlayıcı + tetikleyici**. Farkı burada.

---

## 2. Pazar Durumu: Kim Ne Yapıyor, Nerede Boşluk Var

### 2.1 Mevcut oyuncular ve konumları

| Ürün | Ne yapıyor | Zayıf tarafı | Fiyat |
|---|---|---|---|
| **Motion** | Görevleri takvime otomatik yerleştirir (auto-scheduling'in en iyisi) | "AI Super App" olma yolunda Docs/Sheets/Chat/Notetaker ekledi → özellik şişkinliği, dik öğrenme eğrisi, fiyat tırmanışı, ücretsiz katman yok | $19/ay+ |
| **Reclaim.ai** | Google/Outlook takvimi üzerine oturur; görev, alışkanlık, tampon süre ve odak bloklarını otomatik açar | Takvim odaklı — görev listesi ve not tarafı zayıf; kendi başına sistem değil, eklenti gibi | $8–18/ay, Lite ücretsiz |
| **Sunsama** | Günlük planlama ritüeli. Senin yerine görev üretmez, otomatik planlamaz | Kasıtlı olarak "yavaş"; disiplin gerektirir, otomasyon yok | $20/ay |
| **Akiflow** | Klavye öncelikli, tüm kaynakları tek gelen kutusunda toplar | Güç kullanıcısı ürünü, mobil ikinci planda | $17/ay |
| **Morgen / Temporal / FlowSavvy** | Takvim öncelikli + AI destek, enerji-farkında planlama | Niş, küçük ekosistem | Değişken |
| **Apple Hatırlatıcılar / Google Takvim** | Ücretsiz, her yerde, güvenilir | "Aptal" — sadece söyleneni yapar, öneri/planlama yok | Ücretsiz |

### 2.2 Araştırmadan çıkan üç net boşluk

**Boşluk 1 — Şişkinlik yorgunluğu.**
Motion'ın kullanıcıları ürünün her şeyi yapmaya çalışmasından şikâyetçi. Pazar
şu an *daha fazla özellik* değil, *daha az sürtünme* istiyor. Bu bizim en
büyük fırsatımız ve aynı zamanda en büyük riskimiz — çünkü senin ilk isteğin
tam olarak "her şeyi yapan uygulama" tarifiydi. §9'daki kapsam disiplini bu
yüzden var.

**Boşluk 2 — Mobil-öncelikli AI planlayıcı neredeyse yok.**
Sayılan ürünlerin tamamı masaüstü/web öncelikli; mobil uygulamaları
"eşlik eden ikinci ekran". Türkiye'de ve genel olarak, telefonun *asıl cihaz*
olduğu bir AI planlayıcı boşta duruyor.

**Boşluk 3 — Not ile görev arasındaki uçurum.**
Notion/Obsidian not tutar ama hatırlatmaz. Todoist hatırlatır ama düşünmene
izin vermez. **Serbest yazıdan doğrudan aksiyona geçen köprü kimsede yok.**
Defterim'in adı zaten bunu söylüyor: önce defter, sonra plan.

### 2.3 Konumlandırma cümlesi

> Motion'ın otomatik planlamasını, Sunsama'nın sakinliğiyle, bir defterin
> serbestliği içinde — telefonda.

---

## 3. Çekirdek Fikir: İki Aşamalı Öneri Motoru

Senin "2 aşama önerisi" isteğini ürün diline çevirdim. Bu, Defterim'i
diğerlerinden ayıran tek mekanizma olacak:

```
   Aşama 1 — NE?            Aşama 2 — SONRA NE?
   ─────────────            ───────────────────
   "Yarın 14:00'te          Kullanıcı aksiyonu aldıktan SONRA:
    Ahmet'i ara"            • Tamamlandı → "Aramada teklif konuşuldu mu?
                              Teklifi çarşamba göndermek için 30 dk açayım mı?"
   Sen yazarsın,            • Ertelendi  → "3. kez erteledin. Bu iş
   AI yerleştirir.            gerçekten senin mi, yoksa devretsen mi?"
                            • Yapılmadı  → "Sabah 09:00 senin için daha mı iyi?
                              Son 4 haftada sabah görevlerini %80 bitirdin."
```

**Aşama 1** klasik: doğal dil → yapılandırılmış görev → takvime yerleşim.
**Aşama 2** ise farkımız: *aksiyonun sonucuna bakarak bir sonraki adımı üretir.*
Uygulama seni bir kez dürtüp bırakmaz; olayın devamını kurar. Senin
"olay örgüsü" dediğin şey teknik olarak budur — **görev zinciri (task chain)**.

### 3.1 Neden bu doğru mekanizma — davranış bilimi dayanağı

Araştırma literatüründen üç bulgu, tasarımı doğrudan belirliyor:

1. **Uygulama niyeti (implementation intention)** — "X olduğunda Y yapacağım"
   formatındaki planlar, hedef başarımında orta-güçlü iyileşme sağlıyor.
   → *Tasarım kararı:* Her görev bir **bağlam çıpasına** bağlanmalı
   (saat, konum, önceki görevin bitişi), çıplak bir liste maddesi olmamalı.

2. **Bildirim yorgunluğu gerçek.** Kişiselleştirilmiş, bağlam-farkında
   bildirimler faydayı artırıyor; sık ve genel bildirimler kullanıcıyı yoruyor.
   → *Tasarım kararı:* Günlük **bildirim bütçesi** (varsayılan: 4–6).
   Motor bütçeyi aşamaz, önem sırasına göre eler.

3. **Dışsal bağımlılık riski.** Bildirimler kesildiğinde davranış tutarlılığı
   sert düşüyor — yani bildirim alışkanlığı kurmuyor, alışkanlığın yerine geçiyor.
   → *Tasarım kararı:* Sistem, tutturulan rutinlerde bildirimi kasten
   **seyreltir** ("bunu 3 haftadır hatırlatmadan yapıyorsun, kapatıyorum").
   Bu, rakiplerin hiçbirinde yok ve güven inşa eder.

---

## 4. Teknik Mimari Kararı

### 4.1 Stack

| Katman | Seçim | Gerekçe |
|---|---|---|
| İstemci | **Expo (React Native)** | Tek kod tabanıyla iOS+Android; OTA güncelleme; bildirim/arka plan modülleri hazır. Flutter da uygun ama JS ekosistemi ve AI SDK'ları RN tarafında daha zengin. |
| Yerel veri | **expo-sqlite + Drizzle ORM** | 2026 önerisi bu: tip güvenliği + canlı sorgular. WatermelonDB daha güçlü ama ağır ve sync sunucusunu kendin yazarsın. Bize gerekmiyor. |
| Senkron | **v1'de yok.** Sonra PowerSync / Turso Offline Sync | Sync altyapısını erken yazmak en klasik zaman kaybı. Tek cihaz + yerel yedek ile başla. |
| Backend | **Supabase** (auth + Postgres + Edge Functions) | AI anahtarını istemcide tutmamak için ince bir proxy yeterli. |
| Bildirim | `expo-notifications` (yerel) + `expo-task-manager`/`expo-background-task` | Aşağıdaki kısıtlara dikkat. |

### 4.2 Kritik platform kısıtları (bunlar mimariyi belirliyor)

Araştırmanın en önemli teknik bulgusu şu — ve pek çok proje buraya çarpıp batıyor:

- **iOS**, arka plan çalışmasını kısa ve işletim sisteminin seçtiği pencerelere
  sıkıştırır; süreç ~30 saniyede öldürülür. iOS 18+ ve Android 15 pil
  optimizasyonunu daha da sertleştirdi.
- **Android**'de Doze, App Standby ve OEM katilleri (Xiaomi, Oppo, Vivo, Huawei)
  arka plan işini **sessizce** öldürür.
- `expo-background-task` sana *garantili zamanlayıcı* değil, **asgari aralık** verir.
- Expo Go, SDK 53'ten beri Android'de push bildirimi çalıştırmıyor →
  development build zorunlu.

**Bunun sonucu — mimarinin belkemiği:**

> Zamana duyarlı her şey **önceden zamanlanmış yerel bildirim** olmalı.
> AI ve planlama işi arka planda "o an" çalışmaya bırakılamaz.

Yani: uygulama açıkken (veya push tetiklemesiyle) **önümüzdeki 24–48 saatin
bildirimlerini hesaplayıp yerel olarak kuyruğa dizeriz**. Plan değişirse
kuyruğu iptal edip yeniden kurarız. Bu, "AI arka planda sürekli düşünsün"
fikrinden çok daha az zarif ama **çalışan tek yaklaşım budur**.

### 4.3 AI mimarisi — hibrit

2026'nın kazanan deseni hibrit: gecikmeye duyarlı ve mahrem işler cihazda,
zor akıl yürütme bulutta.

| İş | Nerede | Neden |
|---|---|---|
| Serbest metin → görev alanları çıkarımı (tarih, süre, kişi, öncelik) | **Cihazda** (Apple Foundation Models / Gemini Nano), destekleyen cihazlarda | İlk token 80–200 ms (bulutta 600–1500 ms). Yazarken anlık his. Not içeriği telefondan çıkmaz. |
| Takvim yerleşimi / çakışma çözümü | **Cihazda, kod ile** — LLM değil | Bu bir kısıt-çözme problemi, dil problemi değil. Deterministik algoritma daha hızlı, daha ucuz, hata yapmaz. |
| Aşama-2 önerileri, haftalık geri bildirim, uzun not özeti | **Bulutta** (Claude API) | Gerçek akıl yürütme gerekiyor; seyrek çalışır, maliyet kontrollü. |

**Maliyet notu:** Token bazlı bulut fiyatlaması kullanıcı sayısıyla kötü
ölçeklenir. Sık çalışan çıkarım işini cihaza almak, ürünü ücretsiz sunabilmenin
ön şartı. Cihaz desteklemiyorsa buluta düşeriz (graceful fallback).

**Kritik ayrım:** Literatürde de görülen desen — LLM'i *çözücü* olarak değil,
*çevirmen* olarak kullan. LLM doğal dili yapılandırılmış kısıtlara çevirir;
çözümü deterministik bir zamanlayıcı üretir. Takvimi LLM'e diziverme.

---

## 5. Veri Modeli (çekirdek)

```
Note        — ham girdi. Kullanıcının yazdığı şey aynen durur, asla kaybolmaz.
 └─ Task    — nota bağlı, çıkarılmış aksiyon (başlık, süre, son tarih, öncelik, enerji)
     ├─ Occurrence  — takvimdeki somut yerleşim (başlangıç, bitiş, durum)
     ├─ Nudge       — zamanlanmış bildirim (yerel bildirim kimliği ile eşleşir)
     └─ Suggestion  — Aşama-2 çıktısı (tetikleyici olay, öneri, kullanıcı yanıtı)
Routine     — tekrar eden iş + tutturma serisi (streak) + seyreltme durumu
Context     — çalışma saatleri, enerji profili, sessiz saatler, bildirim bütçesi
```

**Değişmez kural:** `Note` asla silinmez, asla yeniden yazılmaz. AI'ın ürettiği
her şey türev veridir. Kullanıcı AI'a güvenmediği anda ham defterine dönebilmeli.
Bu, ürünün güven sözleşmesi.

---

## 6. Kapsam Disiplini — "Uç Noktalarda Kaybolmamak"

Bunu özellikle istedin, o yüzden en sert bölüm bu. Aşağıdaki liste bir öneri
değil, **sözleşme**. Her sürümde sadece o sütun yapılır.

### v0.1 — "Çalışan Defter" (hedef: 2–3 hafta)
- [ ] Serbest metin yazma, yerel kayıt (SQLite), tam metin arama
- [ ] Metinden görev çıkarımı: başlık + tarih/saat + süre
- [ ] Bugün / Bu Hafta görünümü
- [ ] Yerel bildirim kuyruğu (48 saatlik ufuk)
- [ ] Tamamla / ertele / iptal

**v0.1 başarı ölçütü:** Sen 7 gün boyunca telefonundaki başka hiçbir hatırlatıcıyı
açmadan yaşayabiliyor musun? Cevap hayırsa v0.2'ye geçilmez.

### v0.2 — "Planlayıcı"
- [ ] Otomatik takvim yerleşimi (deterministik zamanlayıcı + çakışma çözümü)
- [ ] Çalışma saatleri, sessiz saatler, bildirim bütçesi
- [ ] Rutinler + tutturma serisi
- [ ] Gün sonu 60 saniyelik kapanış ritüeli

### v0.3 — "İkinci Aşama"
- [ ] Aşama-2 öneri motoru (§3)
- [ ] Erteleme örüntüsü tespiti ve buna göre yeniden zamanlama
- [ ] Haftalık geri bildirim (Türkçe, dürüst, kısa)
- [ ] Rutin tutturulduğunda bildirim seyreltme

### v1.0 — "Kişisel"
- [ ] Kişiselleştirme katmanı (§11'deki cevaplara göre)
- [ ] Takvim entegrasyonu (Google/Apple, salt-okunur → sonra yazma)
- [ ] Bulut yedek + çok cihaz senkronu

### ❌ YAPMAYACAKLAR LİSTESİ (v1.0'a kadar tartışmaya kapalı)

Bunlar iyi fikirler oldukları için tehlikeliler. Motion'ı şişiren şey tam olarak
bu liste:

- Ekip/paylaşım/işbirliği özellikleri
- Sohbet arayüzü ("AI ile konuş") — ürün bir asistan değil, bir defter
- Web ve masaüstü uygulaması
- Doküman/tablo/wiki özellikleri
- E-posta, Slack, WhatsApp entegrasyonları
- Sesli asistan, sesli not transkripsiyonu
- Widget'lar, watch uygulaması, otomasyon senaryoları
- Gamification (rozet, puan, seviye)
- Kendi LLM'imizi eğitmek / fine-tuning

> Bu listedeki bir şeyi eklemek istediğinde: v0.1 başarı ölçütü tutmuş mu diye bak.
> Tutmadıysa cevap hayır.

---

## 7. Riskler ve Karşılıkları

| Risk | Olasılık | Karşılık |
|---|---|---|
| Arka plan kısıtları yüzünden bildirimler geç/hiç gelmez | **Yüksek** | Önceden zamanlanmış yerel bildirim mimarisi (§4.2). Arka plana iş bırakma. |
| Kapsam şişmesi | **Yüksek** | §6 sözleşmesi. Yapmayacaklar listesi. |
| AI yanlış tarih/saat çıkarır, güven kırılır | Orta | Her çıkarımda "böyle anladım" satırı + tek dokunuşla düzeltme. Ham not korunur. |
| AI maliyeti | Orta | Cihaz-öncelikli hibrit. Bulut çağrıları seyrek ve toplu. |
| Kullanıcı bildirimleri kapatır | Orta | Bildirim bütçesi + seyreltme. Az ama isabetli. |
| Tek geliştirici, uzun proje, motivasyon düşüşü | **Yüksek** | v0.1'i 3 haftada kendi kullanımına sokmak. Kullanılmayan kod yazma. |

---

## 8. Kişiselleştirme Yaklaşımı

Açık olmam gerekiyor: **seni tanımıyorum.** Bu oturumdaki tek bilgim e-posta
adresin ve depo adının "Defterim" olduğu. Uygulamayı sana göre şekillendirmek
için tahmin yürütmek yerine soracağım (§11) — ve verdiğin cevaplar
`docs/01-KISISELLESTIRME.md` dosyasına, kodun okuduğu bir profil olarak yazılacak.

Kişiselleştirmenin üç katmanı olacak:

1. **Kurulum profili** — senin verdiğin cevaplar (çalışma saatleri, iş türü, ton).
2. **Öğrenilen örüntü** — hangi saatte ne bitiriyorsun, neyi erteliyorsun.
   Tamamen cihazda, istatistiksel; LLM'e gerek yok.
3. **Ton ve dil** — bildirim metinleri senin seçtiğin üslupta
   (nazik / nötr / sert). Türkçe, doğal, şablon kokmayan.

---

## 9. Sonraki Adım

§11'deki soruları cevapla → `01-KISISELLESTIRME.md` ve `02-MIMARI.md` yazılır →
v0.1 iskeleti kurulur.

---

## 10. Kaynaklar

- [Top 12 Motion Alternatives in 2026 — Reclaim](https://reclaim.ai/blog/motion-alternatives)
- [Motion vs Sunsama (2026) — Toolfinder](https://toolfinder.com/comparisons/motion-vs-sunsama)
- [Best Sunsama Alternatives in 2026 — Super Productivity](https://super-productivity.com/blog/best-sunsama-alternatives-2026/)
- [Best AI Task Management Tools 2026 — alfred_](https://get-alfred.ai/blog/best-ai-task-management-tools)
- [React Native Background Tasks in 2026: iOS vs Android — 72Technologies](https://www.72technologies.com/blog/react-native-background-tasks-ios-android-2026)
- [Expo Local Notifications in 2026 — Codes of Phoenix](https://www.codesofphoenix.com/articles/expo/local-notifications-expo)
- [Local-first architecture with Expo — Expo Docs](https://docs.expo.dev/guides/local-first/)
- [Offline-First RN: SQLite + Drizzle 2026 — React Native Relay](https://reactnativerelay.com/article/building-offline-first-react-native-apps-2026-expo-sqlite-drizzle-orm-sync-strategies)
- [React Native Local Database Options — PowerSync](https://powersync.com/blog/react-native-local-database-options)
- [On-Device LLMs for Mobile (2026) — ZTABS](https://ztabs.co/blog/on-device-llms-mobile-2026)
- [Apple Intelligence and Gemini Nano in 2026 — TouchZen](https://www.touchzen.ai/blog/on-device-ai-mobile-app-development)
- [Implementation Intention and Reminder Effects on Behavior Change — JMIR](https://www.jmir.org/2017/11/e397/)
- [Push Notifications and Habit Formation — KMAN Publications](https://journals.kmanpub.com/index.php/aitechbesosci/article/view/4724)
- [Global Constraint LLM Agents for Text-to-Model Translation — arXiv](https://arxiv.org/html/2509.08970v1)

---

## 11. Cevap Bekleyen Sorular

Bunlar cevaplanmadan v0.1 kodu yazılmaz — çünkü hepsi ürünün şeklini değiştirir.

1. **Sen bu uygulamayı ne için kullanacaksın?** (öğrencilik / serbest çalışma /
   ofis işi / kendi işin / kişisel düzen)
2. **Günün nasıl geçiyor?** Sabit mesai var mı, en verimli saatlerin hangileri?
3. **"2 aşama önerisi" ile tam olarak neyi kastettin?** Benim §3'teki yorumum
   (aksiyon sonrası devam önerisi) doğru mu, yoksa başka bir şey mi düşündün?
4. **Uygulama sana nasıl konuşsun?** Nazik mi, nötr mü, sert mi?
5. **Sadece sana mı, yoksa yayınlanacak bir ürün mü?** (bu, backend ve
   maliyet kararlarını tamamen değiştirir)
