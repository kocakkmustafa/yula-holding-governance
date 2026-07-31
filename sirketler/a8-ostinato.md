---
id: a8-ostinato
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [a8-ostinato-gm, a8-ostinato-musteri-sesi, a8-ostinato-izleme-dogruluk, a8-ostinato-rakip-analisti, a8-ostinato-pazar-analisti, a8-ostinato-pazarlama-analisti, a8-ostinato-guvenlik, a8-ostinato-veri-gizliligi, a8-ostinato-hukuk-uyum, a8-ostinato-sosyal-medya, a8-ostinato-icerik, a8-ostinato-kod-test]
---
# A8 — Ostinato (uykuda)

## Kimlik ve amaç
Ostinato, Motion ailesinin çalgı-pratiği uygulamasıdır (ASC adı "Ostinato: Music Practice", asc_id **6794717868**) — marka TÜM uygun çalgılara açık tasarlandı (kapsam ~35 çalgı, dalga planı W1 Şan/Piyano/Gitar → W2 ukulele/bas/banjo/mandolin → W3 yaylılar keman→**çello**→viyola→kontrbas → W4 nefesli → W5 perküsyon → W6 zither/akordeon/harp/pipa → W7 bölgesel/bağlama); **ilk motor çello** olarak başlatıldı ve W3'e taşındı, kapsam genişlemesi malzemeyi çöpe atmadı — çello varlıkları (kamera-açı triyajı, hata-taksonomisi, ses-fixture şeması) çalgı-bağımsız DESEN olarak W1'e taşındı (OK-9). Kod kurucu tetiğiyle açılana dek KAPALI; **D3 veri-protokolü** (pedagoji/hata-taksonomisi kaynağı: kamu eğitmen videoları, ≥3 konsensüs; öğretmen-görüşme/B2B bacağı KALDIRILDI — Ostinato **B2C-first**, M-F-19) ve W3 veri-güdümlü kapı (W1-W2 gerçek çekiş verisi + yaylı-sayfa ilgi sinyali) kod açılmadan ÖNCE netleşecek konular. Şirket kaydı şimdiden hazır — aktivasyon günü kod-yazımı değil, tek toggle.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/ostinato` · dizin `ventures/ostinato/app` (+ `workspace`) · bundle id `com.yulalab.ostinato`
- Store: ASC "Ostinato: Music Practice" (**asc_id 6794717868**, durum prepare-for-submission) · Play (play_id 4975537094732577317, play_created: true)
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arıza)
- **Audio-DSP omurgası:** pitch algoritması SwiftF0 (MIT, aralık 46.9-2094Hz, med ≤19¢) + `YinPitchSource`; çekirdek zaman-kapısı `motion_core-v0.1.0` pin sürümünden tüketilir (`CueGate` + `LatencyCalibrationStore` + `TapTestCalibrator`); MIDI keşfi spike aşamasında (`flutter_midi_command`, BSD-3) — üretim hattına GİRMEDİ
- Canonical: `ventures/ostinato/VENTURE.md`, `ventures/ostinato/workspace/DEFTER.md`, kapsam otoritesi `ventures/ostinato/app/docs/OSTINATO-BLUEPRINT.md`

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. Breaking sözleşme değişikliği connections.yaml impact_rule gereği tüketici DEFTER'ine kayıt + pinli-sürüm güncellemesi ister; bu şirket için karşılığı `ventures/ostinato/workspace/DEFTER.md`'ye otomatik bulgu satırı (öneki **M-O-***). Ostinato'nun D3 veri-protokolü kararı motion-core'un genelleştirme kapsamını doğrudan etkiler — sözleşme değişince öncelik burada değerlendirilir. AI Act Art.50 değerlendirmesi de Ostinato dahil 4 Motion app'i için V1 öncesi ortak kör-nokta olarak kayıtlı (connections.yaml impact_rule).

## 12'li kadro — STANDART İŞTİRAK KADROSU (EK-C C2), uykuda kapsamıyla
Kod kilidi kapalıyken 12 rolün TAMAMI TANIMLI ama görev kapsamı daraltılmış: ham ürün verisi (yorum/kullanım/gelir) YOK, bunun yerine rezervasyon-sağlığı + rakip/pazar ön-istihbaratı + marka/gizlilik/hukuk ön-hazırlığı + kod-kilit bekçiliği yürütülür. Aktivasyonla her rol C2'deki tam sözleşmesine geçer (runbook'lar değişmez, kapsam genişler).

| # | Rol | Ajan id | Uykuda kapsamı | Model (bugün) | Faz |
|---|---|---|---|---|---|
| 1 | Şirket Müdürü (GM) | `a8-ostinato-gm` | 11 ajanı koordine eder, haftalık kısa-ŞİRKET RAPORU derler, FLAŞ NOT yetkili | sınıf-5 derleme | uykuda |
| 2 | Müşteri-Sesi Analisti | `a8-ostinato-musteri-sesi` | kendi yorumu YOK — rakip (Yousician/Simply/Trala/Tonara) yorumlarından W1 hedef kullanıcı ihtiyaç ön-sinyali | sınıf-1 + embedding | uykuda |
| 3 | İzleme & Doğruluk Sorumlusu | `a8-ostinato-izleme-dogruluk` | ASC/Play/motion-core pin/GitHub billing sağlığı + dürüstlük-çizgisi ön-taraması | L0+sınıf-1 | uykuda |
| 4 | Rakip Analisti | `a8-ostinato-rakip-analisti` | Yousician/Simply Piano-Guitar/Trala/Tonara + Purdue "Cello Evaluator" araştırma prototipi izleme | sınıf-1/5 | uykuda |
| 5 | Pazar Analisti | `a8-ostinato-pazar-analisti` | W1-W7 dalga planı sinyalleri, yaylı-sayfa ("yakında") ilgi ölçümü — W3 kapı metriğinin girdisi | sınıf-1/5 | uykuda |
| 6 | Pazarlama Analisti | `a8-ostinato-pazarlama-analisti` | fiyat-koridoru ($19.99-29.99) ön-kıyas, kanal ön-değerlendirmesi, dürüstlük-çizgisi (O-011) kural taslağı | L0+sınıf-5 | uykuda |
| 7 | Güvenlik Sorumlusu | `a8-ostinato-guvenlik` | repo `ostinato` + MIDI spike (`tools/midi_spike/`) sır/CVE taraması | betik+sınıf-1 | uykuda |
| 8 | Veri Gizliliği Sorumlusu | `a8-ostinato-veri-gizliligi` | çocuk-verisi/KVKK envanteri ön-hazırlığı (OK-2 yüz-bulanıklaştırma, OK-8 eğitim-verisi ayrımı) | betik+sınıf-1 | uykuda |
| 9 | Hukuk-Uyum Sorumlusu | `a8-ostinato-hukuk-uyum` | marka-tescil/isim çakışma radarı, AI Act Art.50 kör-nokta takibi | sınıf-1/5 | uykuda |
| 10 | Sosyal-Medya Takipçisi | `a8-ostinato-sosyal-medya` | "Ostinato" adı mention/marka radarı, yulalab.com coming-soon kart tazeliği | sınıf-1 | uykuda |
| 11 | İçerik Üreticisi | `a8-ostinato-icerik` | yayın YOK — yalnız marka-sesi/dürüstlük-çizgisi kural taslağı hazırlığı | sınıf-7 | uykuda |
| 12 | Kod & Test Bekçisi | `a8-ostinato-kod-test` | kilit-ihlal alarmı + motion-core pin senkron izleme (MONITOR-ONLY) | betik+sınıf-8 | uykuda |

## ŞİRKET RAPORU (haftalık; GM derler; C3 formatı)
Uykuda modda ŞİRKET RAPORU **kısa** biçimde devam eder (rapor kadansı TABANDIR — C7-2, dormant olmak raporu durdurmaz): ASC/Play rezervasyon durumu · kilit-ihlal/kod-dokunma taraması (temiz/değil) · motion-core pin sürüm sağlığı · marka radarı özet satırı · rakip/pazar tek-satır not (varsa) · D3/W3 kapı ilerleme notu (kurucu+CTO kararına bağlı, GM yorum katmayı önermez) · KVKK/güvenlik açık bulgu var mı. Doğrudan kurucuya (Köprü + `ventures/ostinato/workspace/DEFTER.md`). Holding Raporu'na (yönetim katmanı sentezi) girdi olarak akar — GM üzerine yazmaz.

## GM yetkileri (C7)
**C7-2 (bağlayıcı, aynen):** *"Hiçbir severity sinyali rapor bekletilerek geciktirilemez."* SEV0-1 + şirkete-özel acil eşikler (aşağıdaki tablo) ANINDA Köprü Kanalı'na düşer — kaynak ajandan doğrudan, GM eş-zamanlı bilgilendirilir, rapor döngüsünü BEKLEMEZ. GM ayrıca takvim-dışı **FLAŞ NOT** (ara-rapor) üretme yetkisine sahiptir (ör. D3/W3 kapı sinyali beklenmedik hızda değişirse).
**C7-3 tetik sınırları:** GM kendi 11 ajanını cron beklemeden tetikleyebilir (ör. marka radarında şüpheli sinyal → Hukuk-Uyum'u hemen koştur) — ancak (a) yalnız a8-ostinato ajanları, şirketler-arası tetik CEO üzerinden; (b) tetiklenen iş yine R0-R1 tavanında; (c) her tetik audit'e + **şirket-başına günlük tetik/harcama bütçesi** içinde (Cost Guard); (d) kurucu her ajanı GM'i atlayarak da tetikleyebilir (GM tekeli yok).
**C7-1 (İçerik'e giren marka-bağlamı):** İçerik Üreticisi (#11) uykuda modda yayın yapmaz ama marka-sesi taslağı `brands.yml` referanslı hazırlanır — Motion ailesi geneli EN-global ton (ASC adı İngilizce); Sosyal-Medya (#10) topladığı ön-sinyal + Pazar/Rakip analistlerinin bulguları girdi olur.

## Acil eşikleri (şirkete özel — SEV0-1 + rapor-bağımsız)
| Eşik | Aksiyon | Sev |
|---|---|---|
| `ventures/ostinato/app` dizininde commit/push algılanır (kilit açık değilken) | ANINDA Köprü + kurucu | SEV1 |
| Play kaydı (play_id 4975537094732577317) kaybolur/askıya alınır | ANINDA bildirim | SEV1 |
| bundle id `com.yulalab.ostinato` başka kayıtla çakışır | ANINDA bildirim | SEV1 |
| repo/spike kodunda sızmış API key/secret bulunur (Kalkan taraması) | ANINDA Köprü (kamuya ASLA) | SEV1 |
| çocuk-verisi/yüz-bulanıklaştırma varsayılanı ihlali şüphesi (OK-2/OK-8) tespit edilir | ANINDA kurucu + Veri Gizliliği | SEV1 |
| ASC durumu prepare-for-submission dışına kayar | Bulgu + Köprü bildirimi | SEV3 (bekleyebilir) |
| Store'da "Ostinato" adıyla üçüncü-taraf app görünür | Marka radarı bulgusu → Hukuk-Uyum → B10 eşiği | SEV2 |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | Etki notu, submit anına kadar bekler | SEV3 |
| motion-core'da breaking-change commit algılanır | DEFTER bulgusu + pinli-sürüm hatırlatması | SEV3 |
| Rakip (Yousician/Simply/Trala) W1 hedef pazarında büyük hamle yapar (fiyat/özellik) | Rakip Analisti bulgusu, rapora | SEV3 |

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu: kurucu tetiği (vault başlangıç promptu) + D3 veri-protokolü kapanışı (kamu-video hasat turu ≥2 bağımsız kaynak/hata-kodu şartı tamam) + W1 platform/ses-çekirdeği teslimi. Kontrol listesi: (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü (motion_core-v0.1.0+) güncel · (3) ASC/Play kaydı hâlâ prepare-for-submission · (4) marka radarında açık çakışma yok · (5) 12 rolün TAMAMI runbook'u tam-göreve (C2 sözleşmesine) geçti · (6) CTO mimari kapısından geçti (D3 protokol + W3 kapı kararı dahil) · (7) Veri Gizliliği Sorumlusu çocuk-verisi envanterini kapattı.

## Workflow'ları
> **KANONİK KEY NOTU (denetim düzeltmesi, 2026-07-28):** Bu şirketin bugün ÇALIŞTIRILABİLİR workflow'ları `workflows.yaml`'daki PARAMETRİK tanımlardır: `istirak-raporu` · `sirket-retrosu` · `flas-not` (hepsinde `params.sirket: a8-ostinato`). Aşağıda geçen şirket-özel key adları **PLANLI (D5)** etiketlidir — ürün-pipeline'ları kurulurken workflows.yaml'a eklenmeden çalıştırılamazlar.

Beklenen key'ler (workflows.yaml v3'e eklenecek, henüz kayıtlı değil): `a8-ostinato-sirket-raporu` (haftalık, parametrik C6) · `a8-ostinato-rezervasyon-sagligi` (haftalık) · `a8-ostinato-marka-radari` (haftalık) · `a8-ostinato-kilit-ihlal-alarmi` (olay-tetikli, sürekli devriye) · `a8-ostinato-rakip-pazar-taramasi` (haftalık, ön-istihbarat).

## Feedback döngüsü
Haftalık retro (DNA kural 1): kaçan-sinyal = "ASC/Play durumu değişti ama bildirilmedi", "kilit-ihlali fark edilmeden commit geçti", "rakip büyük hamlesi bir hafta gecikmeyle fark edildi" veya "çocuk-verisi/marka sinyali kaçırıldı". Runbook revizyonu kurucu onayı olmadan uygulanmaz (governance'ta versiyonlu commit).

## Sınırlar
Kod dizinine YAZMAZ · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ (D3/W3 kararı kurucu+CTO işi) · içerik YAYINLAMAZ (insan-kapı + AI-etiket aktivasyon sonrası da geçerli) · R1 üstü yetki YOK · dış-yazma YOK

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk #50). Kilit-ihlali/mimari soru → CTO (#5) → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`. Ses/DSP/pitch/gecikme sorusu → `audio-dsp`. Postür/güvenlik-sınırı/geri-bildirim-sıklığı → `movement-science-advisor`. Çocuk-verisi/KVKK → `privacy-data-guardian`. Repo sır/CVE → `security-compliance-auditor`. Rakip teardown → `competitive-intelligence-analyst`. Fiyatlama → `pricing-monetization-strategist`. Model/çaba seçimi → `model-routing-advisor`.
