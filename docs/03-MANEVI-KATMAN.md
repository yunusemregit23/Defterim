# Manevi Katman — Tezekkür-ü Mevt ve Muhasebe

> Sürüm: 1.0 · Tarih: 2026-08-02
> İstek: *"Her saat başı AI'ın, ölümün beni bir gün bulacağını, buna hazır olmam
> ve tövbe etmem gerektiğini telkin etmesi."*

---

## 1. Bu Ne Değiştiriyor

Şimdiye kadarki Defterim tek sütunluydu: **dünyevi iş katmanı** — yakala, planla,
hatırlat, devamını kur. Bu istek ikinci bir sütun ekliyor: **manevi katman.**

Ve aslında ürünün adını hak ettiren şey bu. "Defterim" bir görev listesi değil;
**amel defteri** çağrışımı taşıyan bir kelime. İki sütun aynı defterde:
ne yaptın ve ne için yaptın.

**Bu bir özellik değil, bir sütun.** O yüzden ayrı doküman.

---

## 2. Önce Dürüst Uyarı

Kendi araştırmam bu isteğe karşı çıkıyor ve bunu söylemem gerekiyor:

`02-OZELLIKLER.md` Cephe 10'da tasarladığımız **günlük bildirim bütçesi 4–6**.
Her saat başı = uyanık saatlerde **16 bildirim**. Bütçeyi üçe katlıyor.

Daha önemlisi: araştırma, **sık ve genel bildirimlerin kullanıcı yorgunluğu**
ürettiğini gösteriyor. Aynı mesaj saat başı tekrarlandığında beyin onu birkaç
gün içinde **filtrelemeye başlar** — bildirim gelir, göz kayar, hiçbir şey olmaz.
Alışkanlaşma (habituation) kaçınılmaz.

Yani **"her saat başı aynı telkin"** kurgusu, tam olarak amacını öldüren kurgudur:
ölümü hatırlatmak isterken ölüm hatırlatmasını *gürültüye* çevirir.

Bu uyarıyı yaptım. Şimdi isteği **çalışacak şekilde** tasarlıyorum — çünkü niyet
doğru, sadece teslimat biçimi ölümcül.

---

## 3. Çözüm: Tek Kanal Değil, Üç Katman

Alışkanlaşmayı yenmenin yolu bildirimi azaltmak değil, **kanalı ayırmak**.
Sürekli var olan bir şey ile kesintiye uğratan bir şey aynı şey değil.

### Katman A — Pasif: Her Baktığında Orada (kesintisiz, sınırsız)

**Kilit ekranı widget'ı + ana ekran widget'ı.**

- Bildirim değil. Ses yok, titreşim yok, kesinti yok.
- Telefonuna günde ortalama **80–150 kez** bakıyorsun. Bu, saat başından
  **10 kat sık** ama **sıfır rahatsızlık** demek.
- Widget içeriği saat başı sessizce döner.
- Alışkanlaşma sorunu yok çünkü *seni kesmiyor* — sen ona bakıyorsun.

> **Bu, isteğinin en güçlü karşılığı.** "Her saat başı hatırlatsın" derken
> istediğin şey aslında **sürekli farkındalık**, sürekli kesinti değil.
> Widget bunu bildirimden çok daha iyi yapıyor.

### Katman B — Çıpalı: Namaz Vakitleri (5 bildirim/gün)

Araştırmanın **alışkanlık istifleme** bulgusu diyor ki: yeni davranışı çıplak
saate değil, **zaten var olan bir davranışa** bağla. Saat tetikleyicisi zayıf.

Senin gününde zaten **beş doğal çıpa** var: namaz vakitleri. Bunlar rastgele
saat başları değil; zaten manevi anlam taşıyan, zaten günü bölen anlar.

| Vakit | Telkinin doğal karakteri |
|---|---|
| İmsak/Sabah | Niyet — *"bugün hangi niyetle kalktın?"* |
| Öğle | Ara muhasebe — *"sabahtan buraya ne kaldı?"* |
| İkindi | Asr suresi vurgusu — vaktin akışı, hüsran uyarısı |
| Akşam | Günün kapanışı, istiğfar |
| Yatsı | Gün muhasebesi + uyku/ölüm benzetmesi |

Vakit hesabı **tamamen cihazda, internetsiz**: `adhan-js` kütüphanesi
Jean Meeus'un *Astronomical Algorithms* kitabındaki yüksek hassasiyetli
denklemleri kullanıyor, 18 farklı hesaplama metodu destekliyor (Diyanet dahil
ayarlanabilir). API yok, ağ yok, izin yok — sadece konum bir kez.

### Katman C — Saat Başı: İstersen, Ama Sessiz

İsteğin literal karşılığı, alışkanlaşmaya karşı korumalı:

- **Sessiz teslimat** (ses ve titreşim yok, sadece bildirim merkezine düşer).
- **İçerik havuzu rotasyonu** — asla aynı metin arka arkaya çıkmaz.
- **Uyku ve sessiz saatlerde kapalı.**
- **Yoğunluk ayarı:** saat başı / 2 saatte bir / 3 saatte bir.
- Varsayılan **kapalı**, Katman A + B varsayılan açık. İstersen açarsın.

---

## 4. Alışkanlaşmaya Karşı: İçerik Mimarisi

Tek mesajı tekrarlamak ölümcül. İçerik **havuz** olmalı ve havuz **derinleşmeli**.

### 4.1 İçerik türleri

| Tür | Örnek | Kaynak |
|---|---|---|
| **Ayet** | Asr suresi, "Her nefis ölümü tadacaktır" (Âl-i İmrân 185) | Sabit yerel külliyat |
| **Hadis** | "Lezzetleri yok edeni (ölümü) çokça hatırlayın" (Tirmizî) | Sabit yerel külliyat, **kaynak ve derece etiketiyle** |
| **Selef sözü** | "Hesaba çekilmeden önce kendinizi hesaba çekin" (Hz. Ömer'e atfedilir) | Sabit külliyat, **atıf durumu açıkça belirtilir** |
| **Muhasebe sorusu** | *"Bugün kimseyi kırdın mı? Düzeltmek için vaktin var."* | Üretilebilir |
| **Kişisel yüzleştirme** | *"Bu hafta 23 iş planladın. Kaçı seninle kalacak?"* | Senin verinden üretilir |

### 4.2 Kırmızı çizgi: LLM'e dini metin ürettirilmez

Bu, dokümanın **en önemli mühendislik kuralı**:

> **Ayet ve hadis metinleri asla LLM tarafından üretilmez, tamamlanmaz veya
> "hatırlanmaz". Sadece sabit, doğrulanmış yerel bir külliyattan seçilir.**

Sebep — araştırma bulgusu net:

- LLM'in makul görünen bir hadis ibaresi uydurması **özellikle ciddi bir
  halüsinasyon** türü, çünkü kullanıcı bunu peygamber sözü olarak alır.
  Model uydurma bir rivayet, uydurma bir kaynak adı veya uydurma bir sened
  üretebiliyor.
- Bu metinler asırlardır **harfi harfine** korunmuş; tek bir harekenin yanlışı
  bile anlamı tamamen değiştirebiliyor. Hata toleransı sıfır.
- Bir rivayetin metnini getirip **sıhhat derecesini** görmezden gelmek de
  yanıltıcı sonuç üretiyor.

**Uygulama kuralı:**

```
   LLM'in yapabileceği:   havuzdan seçmek, bağlama göre sıralamak,
                          senin verinle çerçevelemek, muhasebe sorusu üretmek
   LLM'in yapamayacağı:   ayet/hadis metni yazmak, meal üretmek,
                          kaynak atfetmek, sıhhat derecesi belirlemek
```

Her dini metin kaydı şu alanlarla saklanır ve ekranda **kaynağı görünür**:

```
  { metin, meal, kaynak, derece, kaynak_notu }
    örn. derece: "sahih" | "hasen" | "zayıf" | "atfedilir, sabit değil"
```

Külliyat versiyonlanır ve gözden geçirilir. Bir kayıt kaynaksızsa **havuza girmez**.

### 4.3 Havf–Reca dengesi

Sadece korku içeriği hem geleneksel olarak eksik hem psikolojik olarak aşındırıcı.
Klasik çerçeve **havf (korku) ve reca (ümit)** dengesidir. Saat başı sadece
"öleceksin" mesajı, birkaç hafta içinde ya kaygı ya kayıtsızlık üretir — ikisi de
istenen sonuç değil.

**Havuz dengesi kuralı:** ardışık üç telkinin üçü birden havf olamaz.
Rotasyon motoru dengeyi zorunlu tutar:

| Ton | Pay | Örnek yön |
|---|---|---|
| Havf — uyarı | ~%40 | vaktin azlığı, hesap |
| Reca — ümit | ~%30 | tövbenin kabulü, rahmetin genişliği |
| Amel — aksiyon | ~%30 | *"şu an yapabileceğin küçük bir hayır: ..."* |

**Reca tarafının pratik önemi:** tövbe telkininin işe yaraması için kapının açık
olduğu hissi gerekiyor. Sadece tehdit, tövbeye değil kaçışa iter.

---

## 5. Asıl Fikir: İki Sütunu Birleştirmek

Buraya kadar anlatılanı herhangi bir "günün ayeti" uygulaması da yapar.
**Defterim'i ayıran şey, elinde senin görev verinin olması.**

En güçlü tezekkür-ü mevt soyut bir cümle değil — **kendi listene o gözle bakmak.**

```
   Genel telkin (herkes için aynı):
   → "Ölümü çokça hatırlayın."          ... birkaç günde etkisini yitirir

   Kişisel yüzleştirme (senin verinden):
   → "Bu hafta 23 iş planladın, 11'ini bitirdin.
      Bitirdiklerinden hangisi seninle gelecek?"

   → "Kendi işine 4 saat ayırmıştın, 40 dakika kullandın.
      Anneni aramaya ayırdığın süre: 0."

   → "Bu görevi 3 haftadır erteliyorsun: 'Babamı ziyaret et.'
      Erteleyebileceğin bir şey değil bu."
```

Sonuncusu için ne ayete ne hadise gerek var. Sadece **kendi defterin.**

Ve bu, `02-OZELLIKLER.md` Cephe 9'daki **haftalık yüzleşme** özelliğinin
manevi karşılığı. İki sütun aynı motoru paylaşıyor.

---

## 6. İki Aşamalı Öneri Motoruyla Bağlantı

Manevi katman da iki aşamalı çalışır — telkin tek başına aksiyon üretmez:

| Aşama 1 (telkin) | Aşama 2 (aksiyon) |
|---|---|
| *"Her nefis ölümü tadacaktır."* | *"Bugün bir istiğfar için 2 dakika ayırayım mı? 15:30 uygun."* |
| *"Hesaba çekilmeden önce hesaplaşın."* | *"Gece muhasebesi için yatsıdan sonra 5 dakika ayırdım."* |
| *"Kul hakkı en ağır borçtur."* | *"Kırdığını düşündüğün biri var mı? Yaz, ben hatırlatırım."* |

**Tövbe tarafı için özel akış — Tövbe Defteri:**
- Kimseye gitmez, buluta çıkmaz, cihazda şifreli durur.
- Tekrar eden bir şeyi yazdığında sayar: *"Bunu bu ay 4. kez yazıyorsun.
  Sebebini de yazmayı denedin mi?"* — bu, örüntü tespitinin manevi karşılığı.
- Sert ton tercihinle uyumlu: yargılamaz ama **saymayı da bırakmaz.**

---

## 7. Teknik Kararlar

| Konu | Karar | Not |
|---|---|---|
| Namaz vakti hesabı | `adhan-js` | Tamamen offline, Jean Meeus algoritmaları, 18 metot, Diyanet ayarı yapılabilir. Ağ yok. |
| Konum | Bir kez alınır, yerelde kalır | Sürekli konum takibi yok |
| Külliyat | Uygulama içinde gömülü SQLite tablosu | Ağ yok, versiyonlu, kaynak alanları zorunlu |
| Bildirim | Önceden zamanlanmış yerel bildirim | `00-ARASTIRMA.md` §4.2'deki mimari; vakitler günlük hesaplanıp 48 saatlik kuyruğa dizilir |
| Widget | iOS WidgetKit / Android Glance | Expo tarafında native modül gerekir — **v1.0 işi**, v0.1'de değil |
| Tövbe defteri | Cihazda şifreli, `expo-secure-store` anahtarı | Buluta asla çıkmaz, yedeğe bile |
| LLM kullanımı | Sadece seçme/çerçeveleme | §4.2 kırmızı çizgi |

---

## 8. Bildirim Bütçesine Etkisi

`02-OZELLIKLER.md` Cephe 10'daki bütçe **ikiye ayrılıyor** — iki sütun birbirinin
payını yemez:

```
   Dünyevi katman bütçesi   : 4–6 bildirim/gün   (görev, plan, hatırlatma)
   Manevi katman bütçesi    : 5 bildirim/gün     (namaz vakti çıpaları)
   Pasif katman             : sınırsız           (widget — bildirim değil)
   Saat başı modu           : opsiyonel, sessiz, varsayılan kapalı
```

**Seyreltme kuralı manevi katmanda da geçerli** ama tersine çalışır: bir telkin
üzerine düzenli aksiyon alıyorsan o telkin seyrekleşir, **aksiyon alınmayan
alanlar sıklaşır.** Yani uygulama zayıf olduğun yere yönelir.

---

## 9. Sürüm Yerleşimi

Bu sütun kapsam şişmesi değil — ama v0.1'i de bloke etmemeli.

| Sürüm | Manevi katman kapsamı |
|---|---|
| **v0.1** | Yok. Önce defter çalışsın. |
| **v0.2** | Namaz vakti hesabı + 5 çıpalı bildirim + temel külliyat (~100 kayıt, kaynaklı) |
| **v0.3** | Rotasyon motoru + havf/reca dengesi + gece muhasebesi + Tövbe Defteri |
| **v0.3** | **Kişisel yüzleştirme** (§5) — görev verisiyle birleşme. Bu sütunun asıl değeri burada. |
| **v1.0** | Widget'lar (Katman A) + saat başı sessiz mod (Katman C) |

**Not:** İsteğinin literal hali (saat başı) en sonda, en güçlü hali (§5 kişisel
yüzleştirme) daha erken. Bu bilinçli bir sıralama — saat başı jenerik telkin
kolay ama zayıf; kendi defterinden çıkan tek bir cümle ondan güçlü.

---

## 10. Açık Sorular

1. **Külliyat kaynağı ne olsun?** Diyanet meali mi, belirli bir eser mi
   (İhya, Riyâzü's-Sâlihîn vb.)? Bu, ~100 kayıtlık ilk havuzu kimin/neyin
   belirleyeceğini tayin eder.
2. **Namaz vakti metodu:** Diyanet mi, başka bir hesaplama metodu mu?
3. **Saat başı modunu gerçekten istiyor musun** — yoksa widget + 5 vakit
   çıpası isteğini zaten karşılıyor mu? (§3'teki argümanım ikincisi yönünde,
   ama karar senin.)
4. **Tövbe Defteri'ni istiyor musun?** Ayrı bir alan mı olsun, yoksa normal
   notların içinde özel bir etiket mi?

---

## 11. Kaynaklar

**Teknik**
- [Adhan — High precision prayer time library (GitHub)](https://github.com/batoulapps/Adhan)
- [adhan — npm](https://www.npmjs.com/package/adhan)
- [adhan-js calculation methods](https://github.com/batoulapps/adhan-js/blob/master/METHODS.md)
- [Pray Times! User Manual](https://praytimes.org/manual)

**LLM ve dini metin güvenilirliği**
- [BurhanAI at IslamicEval 2025: Combating Hallucinations in LLMs for Islamic Content — OpenReview](https://openreview.net/forum?id=r00SAkJo7o)
- [TCE at IslamicEval 2025: Retrieval-Augmented LLMs for Quranic and Hadith Content Verification — OpenReview](https://openreview.net/forum?id=HLT8TduRQp)
- [Islamic Large Language Models: Trustworthy and Hallucination-Resistant AI — arXiv](https://arxiv.org/html/2606.16629)
- [Can LLMs Write Faithfully? An Agent-Based Evaluation of LLM-generated Islamic Content — arXiv](https://arxiv.org/pdf/2510.24438)

**Bildirim ve alışkanlık** (bkz. `02-OZELLIKLER.md` Cephe 10)
- [Push Notifications and Habit Formation — KMAN Publications](https://journals.kmanpub.com/index.php/aitechbesosci/article/view/4724)
- [Implementation Intention and Reminder Effects on Behavior Change — JMIR](https://www.jmir.org/2017/11/e397/)
