---
id: a9-choreia
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [a9-choreia-gm, a9-choreia-musteri-sesi, a9-choreia-izleme-dogruluk, a9-choreia-rakip-analisti, a9-choreia-pazar-analisti, a9-choreia-pazarlama-analisti, a9-choreia-guvenlik, a9-choreia-veri-gizliligi, a9-choreia-hukuk-uyum, a9-choreia-sosyal-medya, a9-choreia-icerik, a9-choreia-kod-test]
---
# A9 — Choreia (uykuda)

## Kimlik ve amaç
Choreia, Motion ailesinin dans-öğrenme uygulamasıdır (ASC adı "Choreia: Learn to Dance") — telefon kamerasıyla tam-vücut izleyerek, dans eğitmeni yanındaymış gibi sesli yönlendirerek global dans stillerini (V1 hedefi: **Hip-Hop Foundations + Salsa Shines**, K1 kararı) öğretir. motion-core'un paylaşılan hareket-tanıma çekirdeğini tüketecek 5 üründen biridir. **Durum notu (dürüstlük — DNA kural 4):** ailenin en sıkı kod-kapısı burada tanımlanmıştı (**C-001/M-009: TAM PLAN yazılmadan kod açılmaz**) ve bu kapı **2026-07-26'da kurucu onayıyla KAPANDI** — `app/docs/choreia-plan.md` yürürlükte, kod fiilen yazılıyor ve aile içinde **en ileri Motion ürünü** (G1 veri-fabrikası/müfredat-maliyeti ölçüm aşamasında: `beat_annotate.py`, `camera_angle_gate.py`, DTW skorlama motoru + testler). Bu governance kaydı yine de **"uykuda"** kalıyor çünkü ayrı bir kapı henüz açılmadı: **HOLDING'in bu 12-kişilik AI-ajan kadrosu** henüz canlı ürün/kullanıcı verisi işlemiyor (ürün store'a submit edilmedi, `company` toggle'ı kapalı) — uykuda kapsamı bu yüzden rezervasyon-sağlığı + rakip/pazar ön-istihbaratı + marka/gizlilik/hukuk ön-hazırlığı + **motion-core sınır bekçiliği**'nden ibaret. Aktivasyon günü (V1 submit-hazır) tek toggle.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/choreia` · dizin `ventures/choreia/app` (+ `workspace`) · bundle id `com.yulalab.choreia`
- Store: ASC "Choreia: Learn to Dance" (**asc_id 6794721329**, durum prepare-for-submission) · Play (**play_id 4972759001780942116**, play_created: true)
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arıza)
- Canonical: `ventures/choreia/VENTURE.md`, `ventures/choreia/workspace/DEFTER.md`, kapsam otoritesi `ventures/choreia/app/docs/choreia-plan.md` (choreia-brief.md SÜPERSEDE edildi)
- Kayıtlı ürün kararları (DEFTER'den, runbook'lara işlendi): **K7/C-018** müzik $0 varsayılan (kullanıcı-müziği + dahili metronom + CC parça, Spotify/Apple MusicKit **YASAK** — C-008) · **K8 aile kuralı** kalibrasyonsuz skor kullanıcıya gösterilmez (G4 kapısı, C-012) · **C-024** yalnız türetilmiş veri saklanır, ham video/ses **SAKLANMAZ** · **C-017** YouTube kaynak-video riski kurucu kararıyla kabul edildi (aile-geneli bağlayıcı) · **C-007** rakip "Dance Buddy: Learn Any Dance" (id6752668955) pose-feedback+voice-guidance iddia ediyor — dürüst konumlandırma, "ilk biz" DENMEZ

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. **Choreia'ya özgü sınır (M-F-03, 2026-07-26 kurucu kararı):** Dart `motion_core` KANONİK kabul edildi ve bakım/merge sahibi **koordinatör oturum**dur — Choreia oturumu core'a **DOĞRUDAN YAZAMAZ**, ihtiyaç/hata yalnız `M-C-*` kaydıyla bildirilir (açık: M-C-08 config-sürülen koşul yorumlayıcısı, M-C-09 türetilmiş metrik kütüphanesi, M-C-10 faz+beat eşlemesi, M-C-11 kamera-açısı kapısının çekirdeğe terfisi). Bu governance katmanında en somut "kilit" artık bu sınırdır — kilit-ihlal alarmı buna göre kurgulanmıştır (bkz. #12 runbook). Breaking sözleşme değişikliği connections.yaml impact_rule gereği `ventures/choreia/workspace/DEFTER.md`'ye bulgu satırı (öneki **M-C-***) ister.

## 12'li kadro — STANDART İŞTİRAK KADROSU (EK-C C2), uykuda kapsamıyla
Kod kilidi (C-001) açık olsa da HOLDING AI-kadrosu henüz devrede değil: 12 rolün TAMAMI TANIMLI ama görev kapsamı daraltılmış — ham kullanıcı/gelir verisi YOK (store'a çıkmadı), bunun yerine rezervasyon-sağlığı + rakip/pazar ön-istihbaratı + marka/gizlilik/hukuk ön-hazırlığı + motion-core sınır bekçiliği yürütülür. Aktivasyonla her rol C2'deki tam sözleşmesine geçer (runbook'lar değişmez, kapsam genişler).

| # | Rol | Ajan id | Uykuda kapsamı | Model (bugün) | Faz |
|---|---|---|---|---|---|
| 1 | Şirket Müdürü (GM) | `a9-choreia-gm` | 11 ajanı koordine eder, haftalık kısa-ŞİRKET RAPORU derler, FLAŞ NOT yetkili | sınıf-5 derleme | uykuda |
| 2 | Müşteri-Sesi Analisti | `a9-choreia-musteri-sesi` | kendi yorumu YOK — rakip (Dance Buddy id6752668955 + kategori geneli) yorumlarından hedef-kullanıcı ihtiyaç ön-sinyali | sınıf-1 + embedding | uykuda |
| 3 | İzleme & Doğruluk Sorumlusu | `a9-choreia-izleme-dogruluk` | ASC/Play/motion-core-pin/GitHub billing sağlığı + G4 skor-kalibrasyon dürüstlük-çizgisi ön-taraması | L0+sınıf-1 | uykuda |
| 4 | Rakip Analisti | `a9-choreia-rakip-analisti` | Dance Buddy (id6752668955) + kategori rakipleri: pose-feedback/voice-guidance iddia takibi | sınıf-1/5 | uykuda |
| 5 | Pazar Analisti | `a9-choreia-pazar-analisti` | dans-öğrenme pazarı, Hip-Hop/Salsa hedef sinyalleri, stil-genişleme (House/Afrobeats) talep ön-ölçümü | sınıf-1/5 + GSC/Trends | uykuda |
| 6 | Pazarlama Analisti | `a9-choreia-pazarlama-analisti` | fiyat/kanal ön-değerlendirmesi, "ilk biz" DENMEZ dürüstlük-çizgisi (C-007) kural taslağı | L0+sınıf-5 | uykuda |
| 7 | Güvenlik Sorumlusu | `a9-choreia-guvenlik` | repo `choreia` + veri-hasat araçları (`harvest.py`, `beat_annotate.py`, `probe_candidates.py`) sır/CVE taraması | betik+sınıf-1 | uykuda |
| 8 | Veri Gizliliği Sorumlusu | `a9-choreia-veri-gizliligi` | C-024 provenance kararı bekçiliği (yalnız türetilmiş veri saklanır) + KVKK envanteri ön-hazırlığı | betik+sınıf-1 | uykuda |
| 9 | Hukuk-Uyum Sorumlusu | `a9-choreia-hukuk-uyum` | YouTube ToS/türev-eser (C-017) + müzik-telifi (C-008) takibi, marka/isim çakışma radarı | sınıf-1/5 | uykuda |
| 10 | Sosyal-Medya Takipçisi | `a9-choreia-sosyal-medya` | "Choreia" adı mention/marka radarı, yulalab.com coming-soon kart tazeliği | sınıf-1 | uykuda |
| 11 | İçerik Üreticisi | `a9-choreia-icerik` | yayın YOK — yalnız marka-sesi/dürüstlük-çizgisi (K8 + C-007) kural taslağı hazırlığı | sınıf-7 | uykuda |
| 12 | Kod & Test Bekçisi | `a9-choreia-kod-test` | **motion-core doğrudan-yazma alarmı** (M-F-03) + G1 test sağlığı izleme (MONITOR-ONLY) | betik+sınıf-8 | uykuda |

## ŞİRKET RAPORU (haftalık; GM derler; C3 formatı)
Uykuda modda ŞİRKET RAPORU **kısa** biçimde devam eder (rapor kadansı TABANDIR — C7-2, dormant olmak raporu durdurmaz): ASC/Play rezervasyon durumu · motion-core sınır ihlali taraması (temiz/değil) · motion-core pin sürüm sağlığı · marka radarı özet satırı · rakip/pazar tek-satır not (Dance Buddy dahil) · G1 müfredat-maliyeti/G4-kalibrasyon ilerleme notu (kurucu+CTO kararına bağlı, GM yorum katmayı önermez) · KVKK/güvenlik açık bulgu var mı. Doğrudan kurucuya (Köprü + `ventures/choreia/workspace/DEFTER.md`). Holding Raporu'na (yönetim katmanı sentezi) girdi olarak akar — GM üzerine yazmaz.

## GM yetkileri (C7)
**C7-2 (bağlayıcı, aynen):** *"Hiçbir severity sinyali rapor bekletilerek geciktirilemez."* SEV0-1 + şirkete-özel acil eşikler (aşağıdaki tablo) ANINDA Köprü Kanalı'na düşer — kaynak ajandan doğrudan, GM eş-zamanlı bilgilendirilir, rapor döngüsünü BEKLEMEZ. GM ayrıca takvim-dışı **FLAŞ NOT** (ara-rapor) üretme yetkisine sahiptir (ör. G1 müfredat-maliyeti veya rakip hamlesi beklenmedik hızda değişirse).
**C7-3 tetik sınırları:** GM kendi 11 ajanını cron beklemeden tetikleyebilir (ör. marka radarında şüpheli sinyal → Hukuk-Uyum'u hemen koştur) — ancak (a) yalnız a9-choreia ajanları, şirketler-arası tetik CEO üzerinden; (b) tetiklenen iş yine R0-R1 tavanında; (c) her tetik audit'e + **şirket-başına günlük tetik/harcama bütçesi** içinde (Cost Guard); (d) kurucu her ajanı GM'i atlayarak da tetikleyebilir (GM tekeli yok).
**C7-1 (İçerik'e giren marka-bağlamı):** İçerik Üreticisi (#11) uykuda modda yayın yapmaz ama marka-sesi taslağı `brands.yml` referanslı hazırlanır — Motion ailesi geneli EN-global ton (ASC adı İngilizce, "Choreia: Learn to Dance"); Sosyal-Medya (#10) topladığı ön-sinyal + Pazar/Rakip analistlerinin bulguları girdi olur; dürüstlük-çizgisi (C-007 "ilk biz" YASAK, K8 ham-skor YASAK) her taslakta bağlayıcı.

## Acil eşikleri (şirkete özel — SEV0-1 + rapor-bağımsız)
| Eşik | Aksiyon | Sev |
|---|---|---|
| `ventures/motion-core/` dizinine Choreia tarafından DOĞRUDAN commit/push algılanır (M-F-03 ihlali — core sahibi koordinatör oturum) | ANINDA Köprü + kurucu | SEV1 |
| Play kaydı (play_id 4972759001780942116) kaybolur/askıya alınır | ANINDA bildirim | SEV1 |
| bundle id `com.yulalab.choreia` başka kayıtla çakışır | ANINDA bildirim | SEV1 |
| G4 kalibrasyon kapısı geçilmeden kullanıcıya HAM skor gösterildiği tespit edilir (K8 aile kuralı ihlali, C-012) | ANINDA kurucu + CTO | SEV1 |
| Çıkarım-sonrası kaynak medyanın (video/ses/kare) SAKLANDIĞI tespit edilir (`mediaRetained:true`, C-024 provenance ihlali) | ANINDA Veri Gizliliği + kurucu | SEV1 |
| Repo/hasat araçlarında (`harvest.py`, `beat_annotate.py` vb.) sızmış API key/secret bulunur | ANINDA Köprü (kamuya ASLA) | SEV1 |
| Store'da "Choreia" adıyla üçüncü-taraf app görünür | Marka radarı bulgusu → Hukuk-Uyum → B10 eşiği | SEV2 |
| ASC durumu prepare-for-submission dışına kayar | Bulgu + Köprü bildirimi | SEV3 |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | Etki notu, submit anına kadar bekler | SEV3 |
| Rakip (Dance Buddy id6752668955 veya kategori geneli) pose-feedback/voice-guidance iddiasını genişletir ya da büyük kampanya başlatır | Rakip Analisti bulgusu, rapora/FLAŞ NOT değerlendirmesi | SEV2-3 |
| **tabloda olmayan HER durum** | ESKALE ET | — |

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu: kurucu tetiği (vault başlangıç promptu) + Choreia'nın V1'inin store submission'a hazır hale gelmesi (G-kapıları serisinin tamamlanması — özellikle **G4 skor-kalibrasyon kapısı**, K8 aile kuralı gereği zorunlu). Not: C-001/TAM PLAN kapısı zaten geçildi — bu artık uyanma şartı DEĞİL. Kontrol listesi: (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü güncel · (3) ASC/Play kaydı hâlâ prepare-for-submission (ya da submit aşamasına resmî geçti) · (4) marka radarında açık çakışma yok · (5) 12 rolün TAMAMI runbook'u tam-göreve (C2 sözleşmesine) geçti · (6) CTO mimari kapısından geçti (G4 kalibrasyon kapısı dahil) · (7) motion-core'a doğrudan-yazma ihlali kaydı yok (M-F-03 sınırı temiz) · (8) Veri Gizliliği Sorumlusu C-024 provenance envanterini kapattı.

## Workflow'ları
Beklenen key'ler (workflows.yaml v3'e eklenecek, henüz kayıtlı değil): `a9-choreia-sirket-raporu` (haftalık, parametrik C6) · `a9-choreia-rezervasyon-sagligi` (haftalık) · `a9-choreia-marka-radari` (haftalık) · `a9-choreia-motion-core-sinir-alarmi` (olay-tetikli, sürekli devriye — M-F-03 bekçisi) · `a9-choreia-rakip-pazar-taramasi` (haftalık, ön-istihbarat).

## Feedback döngüsü
Haftalık retro (DNA kural 1): kaçan-sinyal = "ASC/Play durumu değişti ama bildirilmedi", "motion-core'a doğrudan yazma denemesi fark edilmeden geçti", "G4 kalibrasyon kapısı ihlali (ham skor gösterimi) yayına kadar fark edilmedi" veya "rakip büyük hamlesi bir hafta gecikmeyle fark edildi". Runbook revizyonu kurucu onayı olmadan uygulanmaz (governance'ta versiyonlu commit).

## Sınırlar
motion-core'a DOĞRUDAN YAZMAZ (M-F-03, core sahibi koordinatör oturum) · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ (TAM PLAN kurucu onaylı, G-kapı kararları CTO+kurucu işi) · içerik/skor YAYINLAMAZ (insan-kapı + AI-etiket aktivasyon sonrası da geçerli) · R1 üstü yetki YOK · dış-yazma YOK

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk #50). motion-core sınırı/mimari soru → CTO (#5) → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`. Hareket-tanıma/pose/kamera-açısı sorusu → `motion-cv-engineer`. Postür/güvenlik-sınırı/skor-kalibrasyon disiplini → `movement-science-advisor`. Beat-senkron/ses gecikmesi → `audio-dsp`. Çocuk-verisi/KVKK/provenance → `privacy-data-guardian`. Repo sır/CVE → `security-compliance-auditor`. Rakip teardown → `competitive-intelligence-analyst`. Fiyatlama → `pricing-monetization-strategist`. Model/çaba seçimi → `model-routing-advisor`.
