---
id: a6-lissom
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [a6-lissom-gm, a6-lissom-musteri-sesi, a6-lissom-izleme-dogruluk, a6-lissom-rakip-analisti, a6-lissom-pazar-analisti, a6-lissom-pazarlama-analisti, a6-lissom-guvenlik, a6-lissom-veri-gizliligi, a6-lissom-hukuk-uyum, a6-lissom-sosyal-medya, a6-lissom-icerik, a6-lissom-kod-test]
---
# A6 — Lissom (uykuda)

## Kimlik ve amaç
Lissom, Motion ailesinin esneklik/yoga/mobilite koçudur (ASC adı "Lissom: Mobility & Yoga") — birkaç dakikalık kamera testiyle hareket kapasitesini ölçer, yoga/esneklik çalışmalarını sesli yönlendirir, 4 haftada yeniden ölçer. **Aile içi sıra tavsiyesinde 1. — kod kilidi açıldığında ilk üretime alınması önerilen üründür.** motion-core'un paylaşılan hareket-tanıma çekirdeğini tüketecek 5 üründen biridir. Kod kurucu tetiğiyle açılana dek KAPALI; şirket kaydı şimdiden hazır — aktivasyon günü kod-yazımı değil, tek toggle.

**v3 modeli:** EK-C standart iştirak kadrosu (12 rol) bu şirkete de atanmıştır — uykuda modda kadronun 11 rolü PASİF (yalnız GM + İzleme&Doğruluk + Kod&Test hafif nabız tutar), aktivasyonla birlikte hiçbir yeni kurulum gerekmeden C2 tablosundaki tam göreve geçer. Eski EK-A tekil masa modeli (`ajanlar/masalar/56-lissom-masasi.md`, ajan-id 56-lissom-masasi) bu dosyayla SÜPERSEDE edilmiştir — dosya tarihsel referans olarak durur, silinmedi; canonical kadro artık bu dosyadaki 12 roldür.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/lissom` · dizin `ventures/lissom/app` (+ `workspace`) · bundle id `com.yulalab.lissom`
- Store: ASC "Lissom: Mobility & Yoga" (asc_id 6794715023, durum prepare-for-submission) · Play (play_id 4974295481818580631, play_created: true)
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arıza — Kalkan/Kod&Test taraması da bu kesintiden etkilenir)
- Canonical: `ventures/lissom/VENTURE.md`, `ventures/lissom/workspace/DEFTER.md`
- Pazarlama konumlandırması (VENTURE.md'den, planlama girdisi — henüz canlı değil): "Esneklik, yoga & mobilite koçu"; içerik/pazarlama/rakip rollerinin uyanıştaki ilk girdisi budur.

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. Breaking sözleşme değişikliği connections.yaml impact_rule gereği tüketici DEFTER'ine kayıt + pinli-sürüm güncellemesi ister; bu şirket için karşılığı `ventures/lissom/workspace/DEFTER.md`'ye otomatik bulgu satırı. Lissom aile-ilk-sırada olduğu için motion-core'daki her breaking değişiklik burada erken yakalanır — geri kalan 4 ürün için otomatik doğrulanmış sayılmaz, ayrı doğrulama gerekir.

## 12'li İŞTİRAK KADROSU (EK-C standart model)
| # | Rol | Ajan id | Uykuda modda görevi | Faz |
|---|---|---|---|---|
| 1 | Şirket Müdürü (GM) | `a6-lissom-gm` | 11 rolün nabzını haftalık derler, kilit/rezervasyon durumunu özetler, acil eşikleri yönlendirir | uykuda→F1 |
| 2 | Müşteri-Sesi Analisti | `a6-lissom-musteri-sesi` | N/A (yorum/destek yüzeyi yok) — yüzey açılırsa anında algıla | uykuda→F1 |
| 3 | İzleme & Doğruluk Sorumlusu | `a6-lissom-izleme-dogruluk` | ASC/Play/bundle-id/kilit sağlığı — kadronun tek sürekli-aktif rolü | uykuda→F1 |
| 4 | Rakip Analisti | `a6-lissom-rakip-analisti` | Kategori (kamera-tabanlı yoga/mobilite) rakip-adı/listing çakışma radarı, hafif | uykuda→F2 |
| 5 | Pazar Analisti | `a6-lissom-pazar-analisti` | N/A (canlı yüzey yok, GSC/Trends verisi yok) — hazırlık notu tutar | uykuda→F2 |
| 6 | Pazarlama Analisti | `a6-lissom-pazarlama-analisti` | ASO adı/anahtar kelime rezervasyon sağlığı, store listing draft tazeliği | uykuda→F2 |
| 7 | Güvenlik Sorumlusu | `a6-lissom-guvenlik` | Proaktif tarama YOK (b6-kalkan.md istisnası: kod-kilitli Motion app kapsam dışı) — yalnız kilit-ihlaliyle eş-zamanlı reaktif triyaj | uykuda→F2 |
| 8 | Veri Gizliliği Sorumlusu | `a6-lissom-veri-gizliligi` | Veri toplanmıyor — kamera-tabanlı hareket ölçümünün (motion_camera) ileride DPIA adayı olduğunu şimdiden not eder | uykuda→F2 |
| 9 | Hukuk-Uyum Sorumlusu | `a6-lissom-hukuk-uyum` | "Lissom" marka/isim tescil envanterine katkı (B10 Hukuk #50 — TR Patent durumu bilinmiyor) | uykuda→F3 |
| 10 | Sosyal-Medya Takipçisi | `a6-lissom-sosyal-medya` | "Lissom" adına açılmış sahte/squat hesap taraması, hafif | uykuda→F3 |
| 11 | İçerik Üreticisi | `a6-lissom-icerik` | N/A (yayın yok) — brands.yml'e marka girdisi eklenmesi uyanışın ilk adımı | uykuda→F3 |
| 12 | Kod & Test Bekçisi | `a6-lissom-kod-test` | Kilit-ihlal alarmı (yetkisiz commit/push) — kadronun ikinci sürekli-aktif rolü | uykuda→F2(izleme) |

Kurallar: 12 rolün TÜMÜ runbook-first (ISLETIM-DNA kural 7); her runbook'ta L4+ modu bölümü — büyük model geldiğinde AYNI sözleşmeyle derinleşir (yapı sabit, beyin değişir).

## ŞİRKET RAPORU (haftalık — C3 formatı)
GM (`a6-lissom-gm`) haftalık **ŞİRKET RAPORU**'nu derler. Uykuda modda rapor C3'ün TAM formuna (sağlık/doğruluk + müşteri sesi + rakip/pazar + pazarlama + güvenlik/gizlilik/hukuk + içerik performansı) İNDİRGENMİŞ şekilde çıkar — çünkü çoğu rol N/A: fiilen yalnız İzleme&Doğruluk + Kod&Test'in bulguları + varsa Hukuk-Uyum/Sosyal-Medya marka-radarı satırları taşınır, diğer roller "bu hafta N/A" olarak açıkça işaretlenir (sessizce atlanmaz — DNA kural 6). Rapor **doğrudan kurucuya** gider (Köprü + dosya); şirket aktive olup F1'e geçtiğinde format otomatik olarak C3'ün tam haline döner (yeniden tasarım gerekmez). Holding Raporu'na (CEO sentezi + R&A) girdi olarak akar, üzerine yazılmaz.

## GM Yetkileri (C7)
**C7-2 — Acil çıktı rapor beklemez (bağlayıcı):** *Hiçbir severity sinyali rapor bekletilerek geciktirilemez.* Aşağıdaki "Acil eşikleri" tablosundaki her satır, ajanından doğrudan Köprü Kanalı'na ANLIK düşer — GM'i bile beklemez (GM eş-zamanlı bilgilendirilir). GM ayrıca takvim-dışı **FLAŞ NOT** (ara-rapor) üretme yetkisine sahiptir; uykuda modda en olası FLAŞ NOT tetikleyicisi kilit-ihlali veya ASC/Play kaydı kaybıdır.

**C7-3 — GM talep-üzerine ajan çalıştırma (sınırlı):** GM, KENDİ 11 ajanını cron beklemeden tetikleyebilir (ör. marka-çakışma şüphesi → Hukuk-Uyum + Sosyal-Medya'yı hemen koştur). Sınırlar: (a) yalnız a6-lissom önekli ajanlar — şirketler-arası tetik (ör. Gravita masasına) CEO üzerinden; (b) tetiklenen iş R0-R1 tavanında kalır, R2+ çıktı yoktur çünkü R2+ yetki bu şirkette hiç tanımlı değildir; (c) her tetik audit'e yazılır + şirket-başına günlük tetik/harcama bütçesi içinde (Cost Guard — uykuda modda bütçe pratikte ~$0, aşım kendisi sinyaldir); (d) kurucu her ajanı kendisi de SteeringMessage/CLI/mobilden tetikleyebilir (GM tekeli yok).

**C7-1 — Marka-bağlamlı içerik:** İçerik Üreticisi rolü uykuda modda N/A'dır (yayın yüzeyi yok); kural aktivasyonla birlikte doğrudan yürürlüğe girer — bkz. `a6-lissom-icerik.md`.

## Acil eşikleri (şirkete özel)
| Eşik | Aksiyon | Severity | Sorumlu rol |
|---|---|---|---|
| ASC durumu (asc_id 6794715023) `prepare-for-submission` dışına kayar | ANLIK Köprü bildirimi (rapor beklenmez) | SEV3 | İzleme&Doğruluk |
| Play kaydı (play_id 4974295481818580631) kaybolur/askıya alınır | ANLIK, GM eş-zamanlı bilgilendirilir | SEV1 | İzleme&Doğruluk |
| `ventures/lissom/app` dizininde kilit açık değilken commit/push algılanır | ANLIK kurucuya + GM FLAŞ NOT | SEV1 | Kod&Test |
| bundle id `com.yulalab.lissom` başka kayıtla çakışır | ANLIK | SEV1 | İzleme&Doğruluk |
| motion-core'da breaking-change commit algılanır | ANLIK DEFTER bulgusu + pinli-sürüm hatırlatma (aile-ilk-sırada erken yakalama) | SEV3 | Kod&Test |
| Store'da "Lissom" adıyla başka geliştirici app'i / sosyal hesap görünür | ANLIK marka radarı bulgusu → Hukuk-Uyum eşiği | SEV2 | Hukuk-Uyum / Sosyal-Medya |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | ANLIK etki notu: "Motion submit ettiğinde bu kurala tabi" | SEV3 | İzleme&Doğruluk |
| GitHub billing kesintisi repo erişimini durdurur | ANLIK "tarama atlandı" notu (Kalkan paralel) | SEV3 | Kod&Test |
| **tabloda olmayan HER durum** | ESKALE ET | — | — |

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu: kurucu tetiği (vault başlangıç promptu — aile içinde ÖNCE Lissom önerisi). Kontrol listesi: (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü güncel · (3) ASC/Play kaydı hâlâ prepare-for-submission · (4) marka radarında açık çakışma yok · (5) 12 rolün TAMAMI runbook'u ile tam-göreve alındı (yalnız İzleme&Doğruluk + Kod&Test değil) · (6) CTO mimari kapısından geçti · (7) `ops/social-media/config/brands.yml`'e Lissom marka girdisi (ton/dil/kadans/hesap) eklendi · (8) ilk ŞİRKET RAPORU tam-C3 formatında derlendi.

## Workflow'ları
Beklenen key'ler (workflows.yaml v3'e C6 planına göre eklenecek, henüz kayıtlı değil): `lissom-rezervasyon-sagligi` (haftalık) · `lissom-marka-radari` (haftalık) · `lissom-kilit-ihlal-alarmi` (olay-tetikli, sürekli devriye) · `sirket-raporu` (parametrik, `venture=lissom`, haftalık — GM tetikler) · uyanıştan sonra devreye girecek: `lissom-musteri-sesi-triyaj`, `lissom-rakip-taramasi`, `lissom-pazar-taramasi`, `lissom-icerik-taslak`.

## Feedback döngüsü
Haftalık şirket retrosu (DNA kural 1 + taslak §3.4): kaçan-sinyal = "ASC/Play durumu değişti ama bildirilmedi", "kilit-ihlali fark edilmeden commit geçti" veya "marka/isim çakışması radardan kaçtı". Runbook revizyonu kurucu onayı olmadan uygulanmaz. Maliyet hedefi: uykuda modda ~$0 (yalnız İzleme&Doğruluk + Kod&Test düzenli çalışır, diğerleri olay-tetikli/N/A).

## Sınırlar
Kod dizinine YAZMAZ · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ (motion-core aile roadmap'i zaten hazır) · R1 üstü yetki YOK · dış-yazma YOK · GM tetikleme yetkisi yalnız kendi 12 rolüyle sınırlı (C7-3) · İçerik/Sosyal-Medya rolleri kod-kilitli+yayınsız dönemde hiçbir dış-görünür içerik üretmez.

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk #50). Kilit-ihlali/mimari soru → CTO (#5) → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`. Veri gizliliği/DPIA hazırlığı → `privacy-data-guardian`. Güvenlik/kilit-ihlali eş-zamanlı sızıntı şüphesi → `security-compliance-auditor`.
