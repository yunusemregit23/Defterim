# Özellik Araştırması — Hangi Özellik, Hayatın Hangi Zorluğunu Çözüyor

> Sürüm: 1.0 · Tarih: 2026-08-02
> Bu doküman ürünün **asıl tasarım dokümanı**. `01-PAZAR.md` sadece referans.
>
> Buradaki her özellik, insanın gününde tıkandığı **somut bir noktadan** türetildi.
> Kural: bir özelliğin bu dokümanda bir "cephesi" yoksa, o özellik yapılmaz.

---

## 0. Yöntem

"Şu özellik havalı olur" diye başlamadım. Tersinden gittim:

> **İnsan bir işi aklına gelmesinden bitirmesine kadar tam olarak nerelerde tıkanıyor?**

Bilişsel psikoloji ve verimlilik araştırmalarından **10 tıkanma noktası** çıktı.
Her biri bir "cephe". Her cephe için: sorun → kanıt → mevcut uygulamalar neden
çözemiyor → Defterim'in özelliği.

**Tek cümlelik cevap — hayatı hangi cepheden kolaylaştırıyor:**

> Defterim, **"aklımdakini unutmayacağıma güvenmek"** ile
> **"şu an ne yapacağımı bilmek"** arasındaki mesafeyi sıfırlar.
> Diğer her şey bu ikisinin türevi.

---

## Cephe 1 — Yakalama: aklına geleni kaydetmenin maliyeti

### Sorun
Aklına bir iş geliyor. Uygulamayı açıyorsun. Uygulama sana soruyor:
hangi proje? hangi etiket? öncelik? son tarih? — ve sen daha yazmadan vazgeçiyorsun.

### Kanıt
> Yakalama sürtünmesiz ve hızlı olmalı; **bir öğe hakkında karar vermeye
> başladığın an sürtünme eklenmiş olur.** Bu sürtünme birikir: yakalamadan
> önce tereddüt edersin çünkü kararların seni beklediğini bilirsin, daha az
> yakalarsın çünkü her yakalama zihinsel çaba ister, ve açık döngüler daha
> uzun süre açık kalır çünkü yakalamak *iş gibi* gelir.

### Mevcut uygulamalar neden çözemiyor
Todoist'in doğal dil girişi bu sorunun **en iyi mevcut cevabı** — ama yine de
"görev" formatına girmeni istiyor. Aklından geçen şey henüz bir görev değilken
(“Ahmet'le konuşulacak şey vardı, neydi ya”) gidecek yeri yok.

### Defterim'in özelliği: **Tek Kutu**
- Uygulama açılır, imleç yanıp söner. Başka hiçbir şey yok.
- Alan yok, proje yok, etiket yok, kategori yok. **Sadece yaz.**
- Yazdığın şey *ham not* olarak kalıcı kaydedilir — görev olmak zorunda değil.
- Yapılandırma işi **senden sonra** olur, AI tarafından, arka planda.

**Değişmez kural:** Yazdığın metin asla değiştirilmez, asla silinmez. AI'ın
ürettiği her şey türev veridir. Sisteme güvenmediğin gün ham defterine dönersin.

---

## Cephe 2 — Zihni boşaltma: "unutmayacağım" güveni

### Sorun
Bitmemiş işler kafanın içinde döner durur. Gece uykuya dalarken aklına gelen
şey budur. Yazınca biraz rahatlarsın ama tam geçmez.

### Kanıt — bu araştırmanın en önemli bulgusu
**Zeigarnik etkisi:** Bitmemiş işler "psikolojik gerilim" üretir ve çalışma
belleğinde erişilebilir kalır. Duygusal ağırlığı olanlar ruminasyona döner.

Ama asıl bulgu şu — **Masicampo & Baumeister çalışması:**

> Bitmemiş bir işi **ne zaman ve nasıl** yapacağına dair somut bir plan yapan
> katılımcılarda, o iş hakkındaki müdahaleci düşünceler **anlamlı ölçüde azaldı** —
> **işi hiç yapmamış olmalarına rağmen.**

Yani beynin gerilimi bırakması için işin *bitmesi* gerekmiyor.
**Somut bir plana bağlanması yetiyor.** Sadece listeye yazmak yetmiyor.

### Mevcut uygulamalar neden çözemiyor
Listeye yazmak = "bir yere kaydettim". Beyin bunu kapanmış saymıyor, çünkü
*ne zaman* sorusu hâlâ açık. Todoist'te 200 maddelik bir liste, 200 açık döngü.
Motion bunu takvime koyuyor ama sen o kararı görmüyorsun, sana geri konuşmuyor.

### Defterim'in özelliği: **Anında Bağlama + "Böyle Anladım" Satırı**
Sen yazdığın anda AI notu bir plana bağlar ve **sana tek satırda geri söyler**:

```
   sen yazdın:  "ahmete teklifi göndermem lazım"
   Defterim:    → Çarşamba 09:30, 25 dk, "kendi işim" bloğunda.
                  [tamam]  [başka zaman]  [bu bir iş değil]
```

Kritik olan şu: **bu satırı görmen gerekiyor.** Beynin döngüyü kapatması için
planın *bilinçli olarak onaylanması* lazım. Arka planda sessizce yapılan planlama
Zeigarnik gerilimini çözmüyor.

Bu tek özellik, uygulamanın varlık sebebi. Gerisi bunun etrafında.

---

## Cephe 3 — Süre körlüğü: "yarım saat sürer" yalanı

### Sorun
Her şeyin ne kadar süreceğini yanlış tahmin ediyorsun. Sonra gün taşıyor,
plan çöküyor, sisteme güvenin kırılıyor.

### Kanıt
**Planlama yanılgısı:** Planlarken en iyi senaryoya odaklanır, engelleri hesaba
katmayız. İlginç ayrıntı: **kısa işleri fazla, uzun işleri az tahmin ediyoruz.**
5 dakikalık işi abartıyor, 3 saatlik işi küçümsüyoruz.

Kanıtlanmış düzeltme yöntemi **"dışarıdan bakış"**: tahmini içgüdüyle değil,
*benzer işlerde geçmişte ne olduğuna* bakarak yapmak — bu, planlama yanılgısını
azaltıyor, hatta ortadan kaldırıyor. Pratik öneriler: tahmini 1,5–2 ile çarp,
%50 tampon ekle.

### Mevcut uygulamalar neden çözemiyor
Motion, Reclaim ve diğerleri **senin verdiğin süreyi** takvime koyuyor.
Yani planlama yanılgını aynen takvime kopyalıyorlar. Kimse "sen bunu hep
yanlış tahmin ediyorsun" demiyor.

### Defterim'in özelliği: **Öğrenen Süre Katsayısı**
- Her görevin *tahmin edilen* ve *gerçekleşen* süresi kaydedilir.
- Uygulama senin kişisel katsayını görev türüne göre öğrenir:
  *"Yazı işlerinde tahminini 1,8 ile çarpıyorsun. 30 dk dedin, 55 dk açıyorum."*
- Bu **istatistik**, LLM değil. Cihazda çalışır, bedava, hata yapmaz.
- Sert tonda geri bildirim: *"Son 6 'kısa bir bakayım' işin ortalama 40 dakika sürdü."*

---

## Cephe 4 — Başlama: görevi biliyorsun ama başlayamıyorsun

### Sorun
"Teklifi hazırla" listede duruyor. Ne yapacağını biliyorsun. Yine de açmıyorsun.

### Kanıt
Görev başlatma (task initiation) ayrı bir yürütücü işlev sorunu — bilmemek
değil, *ilk hareketi çıkaramamak*. Kanıta dayalı çözümlerin başında
**"işi mümkün olan en küçük sonraki adıma bölmek"** geliyor.

GTD'nin aynı bulgusu: fark verimlilik değil, **psikoloji**. Listendeki her şey
*yapılabilir* olduğunda listeye bakmak ezici değil, güç verici hissettiriyor.

### Mevcut uygulamalar neden çözemiyor
Hiçbiri görevi bölmüyor. "Teklifi hazırla" yazdıysan sana "Teklifi hazırla"
diye bildirim atıyorlar — yani zaten bildiğin şeyi tekrar ediyorlar.

### Defterim'in özelliği: **İlk Hareket**
Bildirim görevi tekrar etmez, **ilk fiziksel hareketi** söyler:

```
   ✗ "Teklifi hazırla"
   ✓ "Geçen ayki teklifi aç, kopyala, başlığı değiştir. 5 dakika."
```

Bu, LLM'in gerçekten iyi olduğu ve deterministik kodun yapamayacağı işlerden biri.
Cihaz üstü küçük model bunun için yeterli.

---

## Cephe 5 — Geçiş: iki hayat arasında gidip gelmenin bedeli

### Sorun
Mesai işinden kendi işine geçmek "sadece uygulama değiştirmek" değil.
Kafanın yeniden kurulması gerekiyor ve bu zaman alıyor.

### Kanıt — senin durumun için en kritik veri
- Bir kesintiden sonra işe **tam olarak** dönmek ortalama **23 dakika 15 saniye** sürüyor.
- Ortalama çalışan günde **47 kez** bağlam değiştiriyor; 30 dakikalık bir çalışma
  diliminde ortalama 12 geçiş oluyor.
- Kısa zihinsel tıkanmalar bile verimli zamanın **%40'ına** mal olabiliyor.
- İki ayrı maliyet var: **geçiş maliyeti** (beynin yeniden kurulması) ve
  **dikkat kalıntısı** (attention residue) — ikincisi daha sinsi, önceki iş
  kafanın arkasında çalışmaya devam ediyor.

### Bunun anlamı
**15 dakikalık bir boşluğa "kendi işinden" bir görev koymak matematiksel olarak
zarar.** Geçiş maliyeti işin kendisinden uzun. Motion ve Reclaim bunu bilmiyor;
boşluk gördükleri yere iş koyuyorlar.

### Defterim'in özelliği: **Bağlam Blokları**
- Her görev bir bağlama ait: `mesai` / `kendi işim` / `kişisel`.
- Zamanlayıcının kuralı: **bağlam değişimi maliyetlidir.** Aynı bağlamdaki işler
  kümelenir, gün içinde en fazla 2–3 bağlam geçişi hedeflenir.
- **Asgari blok süresi:** bir bağlama, geçiş maliyetini karşılamayacak kadar
  kısa süre ayrılmaz (varsayılan: 45 dk altına "kendi işim" konmaz).
- Boşluk 15 dakikaysa oraya derin iş değil, **aynı bağlamdan hafif iş** konur.
- Bağlam geçişinden önce **kapanış satırı**: *"Mesaiyi burada bırakıyorsun.
  Yarım kalan: X. Not düş, kafandan çıksın."* — dikkat kalıntısını temizler.

> **Güncelleme (`06-KISISELLESTIRME.md`):** "Mesai" bağlamı ikiye ayrıldı —
> `ofis` (zaman bazlı, sabit) ve `saha` (konum bazlı, `05-KONUM.md`'deki
> geofence'lerle tetiklenir — örn. şantiye). Saha işleri zamana değil
> **konuma** bağlı olduğu için asgari blok süresi kuralı onlara uygulanmaz;
> oraya vardığında tetiklenirler. Güncel dörtlü: `ofis` / `saha` /
> `kendi işim` / `kişisel`.

---

## Cephe 6 — Karar yorgunluğu: "şimdi ne yapsam?"

### Sorun
Listeyi açıyorsun. 40 madde. Hangisini yapacağına karar vermek, işi yapmaktan
yorucu. Sonuçta en kolayını yapıyorsun.

### Kanıt
- Beynin günde sınırlı sayıda **kaliteli karar** kapasitesi var; tekrarlayan
  karar verme bilişsel verimliliği düşürüyor ve insan giderek daha kolay,
  daha az çabalı seçimlere kayıyor.
- **Seçim aşırılığı (choice overload)** deneyi: 6 seçenek sunulduğunda satın alma
  oranı **%28**, 24 seçenek sunulduğunda **%4**. Daha fazla seçenek =
  daha az aksiyon.
- Zihinsel enerji çoğu insanda sabah en yüksek → yüksek bahisli kararlar erkene.

### Mevcut uygulamalar neden çözemiyor
**Görev uygulamalarının tamamı liste gösteriyor.** Yani asıl sorunu — karar
yükünü — çözmüyor, büyütüyor. 40 maddelik liste, günde 40 karar demek.

### Defterim'in özelliği: **Tek İş Ekranı**
- Varsayılan ekran liste değil. **Şu an yapılacak tek iş.**
- Altında tek bir alternatif (iki seçenek, yirmi değil).
- Liste görmek isteyen bir hareket uzağında — ama varsayılan değil.
- *"Ne yapsam?"* sorusunu ortadan kaldırmak, uygulamanın en radikal kararı
  ve Todoist/TickTick modelinden en net kopuşu.

---

## Cephe 7 — Enerji: saat uygun ama sen değilsin

### Sorun
Takvimde 15:00 boş. Ama 15:00'te derin iş yapamıyorsun ve bunu her hafta
yeniden keşfediyorsun.

### Kanıt
- **Kronotip farkı gerçek ve ölçülebilir:** sabah tipleri 07:00–09:00'da zirve
  yaparken akşam tipleri geç sabah/erken öğleden sonraya kadar aynı seviyeye
  ulaşmıyor. Geç kronotipler günün erken saatlerinde en çok zarar gören grup.
  Çalışma belleği ve dikkat işlevleri bu farktan doğrudan etkileniyor.
- **Ultradian ritim:** beyin 90–120 dakikalık döngülerle çalışıyor.
  Beyin kesintisiz yüksek performans için değil, **salınım** için tasarlanmış.
- Kurumsal saatlere değil, **kişisel kronotipe** göre planlamak daha tutarlı sonuç veriyor.

### Mevcut uygulamalar neden çözemiyor
Takvimdeki boşluğu enerjiden bağımsız dolduruyorlar. Tek istisna **Lifestack** —
giyilebilir cihazdan enerji okuyor. Ama giyilebilir cihaz şartı koşuyor.

### Defterim'in özelliği: **Sessiz Kronotip Öğrenimi**
- **Sana kronotipini sormaz.** Zaten bilmiyorsun ve söylediğin yanlış olur.
- Gözlemler: hangi saatte başlatılan işler bitiyor, hangi saatte erteleniyor,
  hangi saatte tahminler tutuyor.
- 3–4 hafta sonra kendi enerji haritanı çıkarır ve derin işi tepe pencerene,
  hafif işi çukura koyar.
- **90 dakika kuralı:** tek blok 90 dakikayı geçmez, arasına ara girer.
- Bu da tamamen istatistik — cihazda, LLM'siz, bedava.

---

## Cephe 8 — Devam: işin bitmesi işin bitmesi değil

### Sorun
Ahmet'i aradın. Aramada iki yeni iş çıktı. İkisi de kafanda. Uygulama ise
görevi "tamamlandı" işaretleyip sustu.

### Kanıt
GTD'nin merkez kavramı **açık döngüler** — söz verdiğin ama bitirmediğin her şey
kafanda açık duruyor ve düzenli kapatma olmadan bilişsel yük sürekli artıyor.
İşlerin çoğu tek bir aksiyonla bitmiyor; **yeni aksiyon doğuruyor.**

### Mevcut uygulamalar neden çözemiyor
`01-PAZAR.md` §6 tablosundaki en çarpıcı bulgu: **"öneri üretir mi" sütunu
neredeyse tamamen boş.** Tüm ürünler ya listeliyor ya takvime yerleştiriyor.
Aksiyonun *sonucuna bakıp devamını kuran* ürün yok.

### Defterim'in özelliği: **İki Aşamalı Öneri Motoru**
Bu ürünün imzası. `00-ARASTIRMA.md` §3'te ayrıntılı; özeti:

| Aksiyonun sonucu | Aşama 2 tepkisi |
|---|---|
| Tamamlandı | *"Aramada yeni bir şey çıktı mı? 30 saniyede yaz, ben yerleştiririm."* |
| Ertelendi (1–2. kez) | Sessizce yeniden yerleştir, örüntüyü kaydet |
| Ertelendi (3. kez) | *"Bunu 3. kez erteliyorsun. Ya bugün yap ya listeden sil. Üçüncü seçenek yok."* |
| Hiç açılmadı | *"Sabah 09:00'da bitirdiğin işlerin oranı %80, akşam 21:00'de %20. Bunu sabaha alıyorum."* |

---

## Cephe 9 — Güven: sistemlerin ölme biçimi

### Sorun
Her verimlilik sistemi aynı şekilde ölüyor ve sen bunu muhtemelen birkaç kez yaşadın.

### Kanıt
> Düzenli gözden geçirme olmadan listeler kayar, onlara güvenmeyi bırakırsın ve
> sistem çöker. İnsanlar sistemi terk edip baştan başlar — **yeni uygulama, temiz
> liste**; temiz sayfa hissi verimli gelir, birkaç hafta güzel çalışır, sonra aynı
> çürüme başlar: projeler birikir, listeler bayatlar, gözden geçirmeler atlanır.

Bu, **uygulama değiştirme döngüsünün** açıklaması. Sorun uygulamada değil,
listenin gerçeği yansıtmayı bırakmasında.

### Mevcut uygulamalar neden çözemiyor
Haftalık gözden geçirmeyi **kullanıcıya bırakıyorlar**. Yapan çok az kişi var.
Sunsama bunu zorluyor ama günlük 10 dakikalık ritüel istiyor — çoğu kişi bırakıyor.

### Defterim'in özelliği: **Otomatik Budama + 60 Saniyelik Yüzleşme**
- **Uygulama kendi listesini budar.** 30 gündür dokunulmamış, 5 kez ertelenmiş
  görevler otomatik olarak "çürük" işaretlenir ve haftalık ekranda karşına çıkar:
  *"Bu 6 iş bir aydır duruyor. Hiçbirini yapmayacaksın. Siliyorum, itiraz varsa söyle."*
- **60 saniye**, 10 dakika değil. Sunsama'nın ritüeli çok pahalı.
- Dürüst rakamlar: *"Bu hafta 23 iş planladın, 11'ini bitirdin. Kendi işine
  4 saat ayırmıştın, 40 dakika kullandın."* — yorum yok, rakam var.

---

## Cephe 10 — Bırakma: uygulamanın sana bağımlılık yaratmaması

### Sorun
Bildirimler işe yarıyor. Sonra kesiliyor ve davranış çöküyor. Yani uygulama
alışkanlık kurmuyor, **alışkanlığın yerine geçiyor**.

### Kanıt
- Kişiselleştirilmiş, bağlam-farkında bildirimler faydayı artırıyor; sık ve genel
  bildirimler **kullanıcı yorgunluğu** üretiyor.
- Müdahale sonrası veriler, bildirimler kesildiğinde tutarlılığın **sert düştüğünü**
  gösteriyor → **dışsal bağımlılık**. Push bildirimleri kısa vadede etkili davranışsal
  ipucu, ama içsel alışkanlık oluşumunun **önünde engel** olabiliyor.
- **Alışkanlık istifleme (habit stacking):** yeni davranışı var olan bir davranışa
  bağlamak. Zaten her sabah kahve yapıyorsan, o tetikleyici olur.

### Defterim'in özelliği: **Bildirim Bütçesi + Kasıtlı Seyreltme**
- **Günlük bildirim bütçesi** (varsayılan 4–6). Motor bütçeyi aşamaz; aşarsa
  önem sırasına göre eler. Bu bir ayar değil, **mimari kısıt**.
- **Seyreltme:** bir rutini 3 hafta üst üste hatırlatmadan yaptıysan uygulama
  bildirimi **kendi kapatır**: *"Bunu artık hatırlatmıyorum, üç haftadır tek başına
  yapıyorsun."*
- **Alışkanlık istifleme:** yeni rutin çıplak saate değil, var olan sabit bir
  davranışa bağlanır (*"kahveni yaptıktan sonra"*), çünkü saat tetikleyicisi zayıf.

> Bu cephe rakiplerin hiçbirinde yok — çünkü ticari olarak mantıksız.
> Kişisel kullanım için yaptığımız için lüksümüz var: uygulamanın **kendini
> gereksizleştirmesi** bizim için başarı.

---

## Özet Tablo — Cephe / Özellik / Kimde Var

| # | Cephe | Defterim özelliği | Pazarda var mı |
|---|---|---|---|
| 1 | Yakalama sürtünmesi | Tek Kutu (sıfır alan) | Kısmen (Todoist NLP) |
| 2 | Zihni boşaltma | Anında bağlama + "böyle anladım" | **Yok** |
| 3 | Süre körlüğü | Öğrenen süre katsayısı | **Yok** |
| 4 | Başlayamama | İlk Hareket (en küçük adım) | **Yok** |
| 5 | Bağlam geçişi | Bağlam blokları + asgari süre | **Yok** |
| 6 | Karar yorgunluğu | Tek İş Ekranı | **Yok** (herkes liste gösteriyor) |
| 7 | Enerji uyumsuzluğu | Sessiz kronotip öğrenimi | Kısmen (Lifestack, cihaz şartlı) |
| 8 | Devamın gelmemesi | İki aşamalı öneri motoru | **Yok** |
| 9 | Sistemin çürümesi | Otomatik budama + 60 sn yüzleşme | Kısmen (Sunsama, pahalı ritüel) |
| 10 | Bildirim bağımlılığı | Bütçe + kasıtlı seyreltme | **Yok** |

**10 cephenin 7'sinde pazarda karşılık yok.** Bunun sebebi özelliklerin zor
olması değil — ticari ürünlerin bu sorunları çözmeye *niyeti* olmaması.
Bir SaaS ürünü kendi bildirimini kapatmaz, listeni budamaz, "bunu yapmayacaksın"
demez. Kişisel kullanım için yaptığımız için bunları yapabiliyoruz.

---

## Sürümlere Dağılım

Kapsam sözleşmesi (`00-ARASTIRMA.md` §6) bu cephelere göre yeniden dizildi:

| Sürüm | Cepheler | Neden bu sırayla |
|---|---|---|
| **v0.1** | 1 (Yakalama), 2 (Zihni boşaltma) | Bu ikisi olmadan ürün yok. Cephe 2 tek başına uygulamanın varlık sebebi. |
| **v0.2** | 5 (Bağlam), 6 (Karar), 3 (Süre) | Senin "iki hayat" durumunun çekirdeği. |
| **v0.3** | 8 (Devam), 4 (İlk hareket), 9 (Budama) | Zeka katmanı. Veri birikmeden çalışmaz. |
| **v1.0** | 7 (Kronotip), 10 (Seyreltme) | İkisi de **haftalarca veri gerektiriyor**; erken yapılamaz. |

**Cephe 7 ve 10 neden en sonda:** İkisi de senin davranışını istatistiksel olarak
öğrenmeye dayanıyor. 3–4 haftalık gerçek kullanım verisi olmadan tahmin üretirler,
tahmin de güveni kırar. Önce veri, sonra zeka.

---

## Kaynaklar

**Zihinsel yük ve açık döngüler**
- [Consequences of cognitive offloading — PMC](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8358584/)
- [Memory for Incomplete Tasks: Re-examination of the Zeigarnik Effect — eScholarship](https://escholarship.org/uc/item/2qb9x9wd)
- [The Zeigarnik Effect: Why Unfinished Tasks Stay in Our Minds — Meta Psychological Education](https://metapsyched.org/the-zeigarnik-effect-why-unfinished-tasks-stay-in-our-minds/)
- [The Open Loop Problem: Why Your Brain Needs a GTD Inbox — Super Productivity](https://super-productivity.com/blog/gtd-inbox-capture-system/)
- [GTD Weekly Review Guide — Super Productivity](https://super-productivity.com/blog/gtd-weekly-review-guide/)
- [GTD Next Actions: The Art of Defining What's Actually Doable — Super Productivity](https://super-productivity.com/blog/gtd-next-actions-guide/)

**Bağlam geçişi**
- [Examining the cognitive processes underlying resumption costs — PMC](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10896823/)
- [Context Switching: The Hidden Cost of Task-Switching — 4dayweek.io](https://4dayweek.io/blog/context-switching)
- [The Hidden Cost of Context Switching — Claryti](https://www.claryti.ai/blog/context-switching-cost)
- [Context switching is the main productivity killer for developers — Tech World with Milan](https://newsletter.techworld-with-milan.com/p/context-switching-is-the-main-productivity)

**Süre tahmini ve başlatma**
- [Planning fallacy — Wikipedia](https://en.wikipedia.org/wiki/Planning_fallacy)
- [The Planning Fallacy: Why We Underestimate Time — Calendar](https://www.calendar.com/blog/the-planning-fallacy-why-we-underestimate-time-and-overestimate-our-abilities/)
- [Biased Planning and Procrastination — Psychology Today](https://www.psychologytoday.com/gb/blog/dont-delay/200903/biased-planning-and-procrastination)
- [ADHD and Time Management — Refresh Psychiatry](https://www.refreshpsychiatry.com/post/adhd-time-management)

**Karar yorgunluğu**
- [Decision Fatigue — The Decision Lab](https://thedecisionlab.com/biases/decision-fatigue)
- [The Depleted Mind: The Science of Decision Fatigue and Ego Depletion — GC-BS](https://gc-bs.org/articles/the-depleted-mind-the-science-of-decision-fatigue-and-ego-depletion/)
- [Decision Fatigue Psychology: Why Too Many Choices Paralyze You — The Daily Explainer](https://thedailyexplainer.com/decision-fatigue-choice-overload-psychology-2026/)

**Enerji ve ritim**
- [Cognitive functions and underlying parameters of human brain physiology are associated with chronotype — Nature Communications](https://www.nature.com/articles/s41467-021-24885-0)
- [The effects of time of day and chronotype on cognitive and physical performance — PMC](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6200828/)
- [Chronotype and synchrony effects in human cognitive performance: A systematic review — Taylor & Francis](https://www.tandfonline.com/doi/full/10.1080/07420528.2025.2490495)
- [Understanding Your Brain's 90-Minute Ultradian Cycles — Cannelevate](https://www.cannelevate.com.au/article/understanding-ultradian-rhythms-brains-90-minute-cycles-explained/)

**Bildirim ve alışkanlık**
- [Implementation Intention and Reminder Effects on Behavior Change — JMIR](https://www.jmir.org/2017/11/e397/)
- [Push Notifications and Habit Formation — KMAN Publications](https://journals.kmanpub.com/index.php/aitechbesosci/article/view/4724)
