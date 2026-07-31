---
id: a5-gravita
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [a5-gravita-gm, a5-gravita-musteri-sesi, a5-gravita-izleme-dogruluk, a5-gravita-rakip-analisti, a5-gravita-pazar-analisti, a5-gravita-pazarlama-analisti, a5-gravita-guvenlik, a5-gravita-veri-gizliligi, a5-gravita-hukuk-uyum, a5-gravita-sosyal-medya, a5-gravita-icerik, a5-gravita-kod-test]
---
# A5 — Gravita (uykuda)

## Kimlik ve amaç
Gravita, Motion ailesinin güç/kuvvet + vücut-becerileri koçudur (ASC adı "Gravita: Skills & Strength") — telefon kamerasıyla handstand/ters-duruş ve calisthenics denemesini cihaz-üstü analiz eder, en önemli hatayı söyler, antrenörün yanındaymış gibi sesli yönlendirir, ölçülebilir progresyonla ilerletir. motion-core'un paylaşılan hareket-tanıma çekirdeğini tüketecek 5 üründen biridir.

**v3 modeli:** EK-C standart iştirak kadrosu (12 rol) bu şirkete de atanmıştır — uykuda modda kadronun çoğu rolü PASİF/hazırlık-modunda, yalnız GM + İzleme&Doğruluk + Kod&Test düzenli nabız tutar, aktivasyonla birlikte hiçbir yeni kurulum gerekmeden C2 tablosundaki tam göreve geçer. Eski EK-A tekil masa modeli (`ajanlar/masalar/15-gravita-masasi.md`, ajan-id 15-gravita-masasi) bu dosyayla SÜPERSEDE edilmiştir — dosya tarihsel referans olarak durur, silinmedi; canonical kadro artık bu dosyadaki 12 roldür.

**⚠️ "Uykuda" NEYİ kapsıyor — v2'den düzeltilen ayrım:** Bu dosyanın uykuda statüsü **holding'in otomasyon kadrosunun** (12 ajan + haftalık ŞİRKET RAPORU) aktivasyonunu tanımlar. **Ürünün kendisi uykuda DEĞİLDİR:** `ventures/gravita/workspace/DEFTER.md`'ye göre kurucu 2026-07-26'da "Gravita'ya başlayalım" tetiğini vermiş, kod kilidi kurucu-oturumu geliştirmesi anlamında AÇILMIŞ, V0 kapısı D1 (ters-duruş fizibilitesi) **şartlı geçmiş** (G-001/G-002 kapalı, kurucu onayı 2026-07-29) ve o günden 2026-07-30'a kadar motor (`gravita_engine`) + Flutter kabuk iOS simülatör ve Android'de koşacak kadar ilerlemiştir. Motion ailesi sözleşmesi (`governance/sozlesmeler/venture-motion-ailesi.md`) bunu zaten doğru tanımlıyordu: kilit-ihlali "ailede koda dokunan **OTOMASYON** görürse SEV1" der — kurucunun kendi geliştirme oturumu hiçbir zaman ihlal değildi, v2'nin basitleştirilmiş runbook tablosu bu nüansı kaybetmişti. v3 bunu düzeltir (bkz. `a5-gravita-kod-test.md`).

**Kurucu+Fable gözden geçirmesi önerilir (bulgu, karar değil — DNA kural 4):** eski uyanma-koşulu tanımının iki parçası da ("kurucu tetiği" + "D1 geçişi") DEFTER'e göre 2026-07-26/29'da teknik olarak zaten gerçekleşmiş görünüyor (§Uyanma koşulu). Bu, holding kadrosunun otomatik uyandığı anlamına GELMEZ — yalnız bu dosyanın bir sonraki kurucu+Fable turunda yeniden değerlendirilmesi gerektiğini işaretler.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/gravita` · dizin `ventures/gravita/app` (+ `workspace`) · bundle id `com.yulalab.gravita`.
- Store: ASC "Gravita: Skills & Strength" (asc_id 6794714365, durum prepare-for-submission — submit YOK) · Play (play_id 4975756038960958432, play_created: true).
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arıza — Kalkan/Kod&Test taraması da bu kesintiden etkilenir).
- Canonical: `ventures/gravita/VENTURE.md`, `ventures/gravita/workspace/DEFTER.md`, `ventures/gravita/app/docs/gates/G1-D1-RAPOR.md`.
- Ürün durumu (2026-07-30 anlık görüntü, ayrıntı DEFTER'de — burada TEKRARLANMAZ, DNA kural 8): D1 kapısı yönelim-farkında-çıkarım koşuluyla şartlı geçti · `gravita_engine` + Flutter kabuk simülatörde/Android'de koşar durumda derlendi (G-100) · motion-core `0.9.0` pin'i benimsendi (G-101) · kamera-canlı köprü henüz YOK (bugün üretimde hiçbir kayıt yazılmıyor).
- Pazarlama konumlandırması (VENTURE.md'den, planlama girdisi — henüz canlı değil): "Handstand & vücut becerileri koçu"; içerik/pazarlama/rakip rollerinin uyanıştaki ilk girdisi budur.

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. Breaking sözleşme değişikliği connections.yaml impact_rule gereği tüketici DEFTER'ine kayıt + pinli-sürüm güncellemesi ister; bu şirket için karşılığı `ventures/gravita/workspace/DEFTER.md`'ye otomatik bulgu satırı. Gravita D1 riskini ilk taşıyan üründü (ters-duruş), bu yüzden yönelim-farkında-çıkarım (ADR-001/002) çekirdeğe Gravita'nın ölçümünden girdi — geri kalan 4 ürün için otomatik doğrulanmış sayılmaz, ayrı doğrulama gerekir.

## 12'li İŞTİRAK KADROSU (EK-C standart model)
| # | Rol | Ajan id | Uykuda modda görevi | Faz |
|---|---|---|---|---|
| 1 | Şirket Müdürü (GM) | `a5-gravita-gm` | 11 rolün nabzını haftalık derler, kilit/rezervasyon durumunu özetler, acil eşikleri yönlendirir | uykuda→F1 |
| 2 | Müşteri-Sesi Analisti | `a5-gravita-musteri-sesi` | N/A (yorum/destek yüzeyi yok) — erken/sızmış görünürlük anomalisini algılar | uykuda→F1 |
| 3 | İzleme & Doğruluk Sorumlusu | `a5-gravita-izleme-dogruluk` | ASC/Play/bundle-id sağlığı (**rezervasyon sağlığı**) — kadronun tek sürekli-aktif rolü | uykuda→F1 |
| 4 | Rakip Analisti | `a5-gravita-rakip-analisti` | Kategori (Skills & Strength/calisthenics/handstand) rakip-adı/listing çakışma radarı, hafif | uykuda→F2 |
| 5 | Pazar Analisti | `a5-gravita-pazar-analisti` | N/A (canlı yüzey yok, GSC/Trends verisi yok) — çeyreklik kategori-trend hazırlık notu tutar | uykuda→F2 |
| 6 | Pazarlama Analisti | `a5-gravita-pazarlama-analisti` | Store listing metadata tazeliği + yulalab.com cross-claim tutarlılığı | uykuda→F2 |
| 7 | Güvenlik Sorumlusu | `a5-gravita-guvenlik` | Proaktif kod-tarama YOK (kurucu-oturumu normal kabul edilir) — yalnız kilit-ihlaliyle eş-zamanlı reaktif triyaj + paylaşımlı hesap risk sinyali | uykuda→F2 |
| 8 | Veri Gizliliği Sorumlusu | `a5-gravita-veri-gizliligi` | "Henüz kişisel veri toplanmıyor" iddiasının kod-gerçeğiyle doğruluğunu haftalık teyit eder | uykuda→F2 |
| 9 | Hukuk-Uyum Sorumlusu | `a5-gravita-hukuk-uyum` | "Gravita" marka/isim tescil+store çakışma radarı (**marka radarı** — B10 Hukuk #50 ile ortak) | uykuda→F3 |
| 10 | Sosyal-Medya Takipçisi | `a5-gravita-sosyal-medya` | "Gravita" adına açılmış sahte/squat hesap taraması, hafif | uykuda→F3 |
| 11 | İçerik Üreticisi | `a5-gravita-icerik` | N/A (yayın yok) — `brands.yml`'e marka girdisi eklenmesi uyanışın ilk adımı | uykuda→F3 |
| 12 | Kod & Test Bekçisi | `a5-gravita-kod-test` | **Kilit-ihlal alarmı**: yalnız HOLDİNG OTOMASYONU kaynaklı commit/push'u yakalar (kurucu-oturumu değil) + motion-core breaking-change izleme — kadronun ikinci sürekli-aktif rolü | uykuda→F2(izleme) |

Kurallar: 12 rolün TÜMÜ runbook-first (İŞLETİM-DNA kural 7); her runbook'ta L4+ modu bölümü — büyük model geldiğinde AYNI sözleşmeyle derinleşir (yapı sabit, beyin değişir). Rol tanımları/model zincirleri: `governance/ajanlar/istirakler/a5-gravita/<rol>.md`.

## ŞİRKET RAPORU (haftalık — C3 formatı)
GM (`a5-gravita-gm`) haftalık **ŞİRKET RAPORU**'nu derler. Uykuda modda rapor C3'ün TAM formuna (sağlık/doğruluk + müşteri sesi + rakip/pazar + pazarlama + güvenlik/gizlilik/hukuk + içerik performansı) İNDİRGENMİŞ şekilde çıkar — çünkü çoğu rol N/A: fiilen yalnız İzleme&Doğruluk (rezervasyon sağlığı) + Kod&Test (kilit-ihlal) bulguları + varsa Hukuk-Uyum/Sosyal-Medya marka-radarı satırları taşınır, diğer roller "bu hafta N/A" olarak açıkça işaretlenir (sessizce atlanmaz — DNA kural 6). Rapor **doğrudan kurucuya** gider (Köprü + `ventures/gravita/workspace/DEFTER.md`'ye tarihli "Şirket Raporu" girişi); şirket aktive olup F1'e geçtiğinde format otomatik olarak C3'ün tam haline döner (yeniden tasarım gerekmez). Holding Raporu'na (CEO sentezi + R&A) girdi olarak akar, üzerine yazılmaz.

## GM Yetkileri (C7)
**C7-2 — Acil çıktı rapor beklemez (bağlayıcı):** *Hiçbir severity sinyali rapor bekletilerek geciktirilemez.* Aşağıdaki "Acil eşikleri" tablosundaki her satır, ajanından doğrudan Köprü Kanalı'na ANLIK düşer — GM'i bile beklemez (GM eş-zamanlı bilgilendirilir). GM ayrıca takvim-dışı **FLAŞ NOT** (ara-rapor) üretme yetkisine sahiptir; uykuda modda en olası FLAŞ NOT tetikleyicisi kilit-ihlali (otomasyon kaynaklı) veya ASC/Play kaydı kaybıdır.

**C7-3 — GM talep-üzerine ajan çalıştırma (sınırlı):** GM, KENDİ 11 ajanını cron beklemeden tetikleyebilir (ör. marka-çakışma şüphesi → Hukuk-Uyum + Sosyal-Medya'yı hemen koştur). Sınırlar: (a) yalnız a5-gravita önekli ajanlar — şirketler-arası tetik (ör. Lissom masasına) CEO üzerinden; (b) tetiklenen iş R0-R1 tavanında kalır, R2+ çıktı yoktur çünkü R2+ yetki bu şirkette hiç tanımlı değildir; (c) her tetik audit'e yazılır + şirket-başına günlük tetik/harcama bütçesi içinde (Cost Guard — uykuda modda bütçe pratikte ~$0, aşım kendisi sinyaldir); (d) kurucu her ajanı kendisi de SteeringMessage/CLI/mobilden tetikleyebilir (GM tekeli yok).

**C7-1 — Marka-bağlamlı içerik:** İçerik Üreticisi rolü uykuda modda N/A'dır (yayın yüzeyi yok); kural aktivasyonla birlikte doğrudan yürürlüğe girer — bkz. `a5-gravita-icerik.md`.

## Acil eşikleri (şirkete özel)
| Eşik | Aksiyon | Severity | Sorumlu rol |
|---|---|---|---|
| ASC durumu (asc_id 6794714365) `prepare-for-submission` dışına kayar | ANLIK Köprü bildirimi (rapor beklenmez) | SEV3 | İzleme&Doğruluk |
| Play kaydı (play_id 4975756038960958432) kaybolur/askıya alınır | ANLIK, GM eş-zamanlı bilgilendirilir | SEV1 | İzleme&Doğruluk |
| `ventures/gravita/app` dizinine HOLDİNG OTOMASYONU (ajan/pipeline/CI-bot) commit/push atar | ANLIK kurucuya + GM FLAŞ NOT (kurucu-oturumu commit'leri İHLAL DEĞİL) | SEV1 | Kod&Test |
| bundle id `com.yulalab.gravita` başka kayıtla çakışır | ANLIK | SEV1 | İzleme&Doğruluk |
| motion-core'da breaking-change commit algılanır | ANLIK DEFTER bulgusu + pinli-sürüm hatırlatma (Gravita pin `0.9.0`) | SEV3 | Kod&Test |
| Store'da "Gravita" adıyla başka geliştirici app'i / sosyal hesap görünür | ANLIK marka radarı bulgusu → Hukuk-Uyum eşiği | SEV2 | Hukuk-Uyum / Sosyal-Medya |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | ANLIK etki notu: "Motion submit ettiğinde bu kurala tabi" | SEV3 | İzleme&Doğruluk |
| GitHub billing kesintisi repo erişimini durdurur | ANLIK "tarama atlandı" notu (Kalkan paralel) | SEV3 | Kod&Test |
| **tabloda olmayan HER durum** | ESKALE ET | — | — |

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu (yazılı hâliyle, v2'den değişmedi): kurucu tetiği (vault başlangıç promptu) + V0 kapısı D1 (ters-duruş fizibilitesi) geçişi. **DEFTER durumu (2026-07-30):** ikisi de teknik olarak gerçekleşmiş görünüyor (§Kimlik ve amaç) — bu satır kadronun otomatik uyandığı anlamına GELMEZ, kurucu+Fable'ın bu dosyayı gözden geçirmesi gereken bir bulgudur.

Kontrol listesi (kadroyu FİİLEN uyandırmadan önce): (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü güncel (bugün `0.9.0`, G-101) · (3) ASC/Play kaydı hâlâ prepare-for-submission · (4) marka radarında açık çakışma yok · (5) 12 rolün TAMAMI runbook'u ile tam-göreve alındı (yalnız İzleme&Doğruluk + Kod&Test değil) · (6) CTO mimari kapısından geçti · (7) `ops/social-media/config/brands.yml`'e Gravita marka girdisi (ton/dil/kadans/hesap) eklendi · (8) ilk ŞİRKET RAPORU tam-C3 formatında derlendi.

## Workflow'ları
> **KANONİK KEY NOTU (denetim düzeltmesi, 2026-07-28):** Bu şirketin bugün ÇALIŞTIRILABİLİR workflow'ları `workflows.yaml`'daki PARAMETRİK tanımlardır: `istirak-raporu` · `sirket-retrosu` · `flas-not` (hepsinde `params.sirket: a5-gravita`). Aşağıda geçen şirket-özel key adları **PLANLI (D5)** etiketlidir — ürün-pipeline'ları kurulurken workflows.yaml'a eklenmeden çalıştırılamazlar.

Beklenen key'ler (workflows.yaml v3'e C6 planına göre eklenecek, henüz kayıtlı değil): `gravita-rezervasyon-sagligi` (haftalık) · `gravita-marka-radari` (haftalık) · `gravita-kilit-ihlal-alarmi` (olay-tetikli, sürekli devriye, yalnız otomasyon-kaynaklı yazar-kimliği) · `sirket-raporu` (parametrik, `venture=gravita`, haftalık — GM tetikler) · uyanıştan sonra devreye girecek: `gravita-musteri-sesi-triyaj`, `gravita-rakip-taramasi`, `gravita-pazar-taramasi`, `gravita-icerik-taslak`.

## Feedback döngüsü
Haftalık şirket retrosu (DNA kural 1 + taslak §3.4): kaçan-sinyal = "ASC/Play durumu değişti ama bildirilmedi", "otomasyon-kaynaklı bir commit kilit-ihlali olarak yakalanmadı" veya "marka/isim çakışması radardan kaçtı". Runbook revizyonu kurucu onayı olmadan uygulanmaz. Maliyet hedefi: uykuda modda ~$0 (yalnız İzleme&Doğruluk + Kod&Test düzenli çalışır, diğerleri olay-tetikli/N/A).

## Sınırlar
Kod dizinine hiçbir holding ajanı YAZMAZ (Atölye uykuda — genel kural) · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ (venture kendi PLAN/PRD'sini kurucu-oturumunda yönetir, motion-core aile roadmap'i zaten hazır) · R1 üstü yetki YOK · dış-yazma YOK · GM tetikleme yetkisi yalnız kendi 12 rolüyle sınırlı (C7-3) · İçerik/Sosyal-Medya rolleri yayınsız dönemde hiçbir dış-görünür içerik üretmez · kurucunun kendi geliştirme commit'lerini "ihlal" saymaz (§Kimlik ve amaç ayrımı).

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk #50). Kilit-ihlali/mimari soru → CTO (#5) → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`. Veri gizliliği/DPIA hazırlığı → `privacy-data-guardian`. Güvenlik/kilit-ihlali eş-zamanlı sızıntı şüphesi → `security-compliance-auditor`. Fitness/hareket-koçluğu iddia sınırı (uyanınca içerik/pazarlama için) → `movement-science-advisor`.
