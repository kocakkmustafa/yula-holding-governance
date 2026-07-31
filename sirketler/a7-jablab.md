---
id: a7-jablab
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [a7-jablab-gm, a7-jablab-musteri-sesi, a7-jablab-izleme-dogruluk, a7-jablab-rakip-analisti, a7-jablab-pazar-analisti, a7-jablab-pazarlama-analisti, a7-jablab-guvenlik, a7-jablab-veri-gizliligi, a7-jablab-hukuk-uyum, a7-jablab-sosyal-medya, a7-jablab-icerik, a7-jablab-kod-test]
---
# A7 — JabLab (uykuda) · v3 tam-kadrolu iştirak

## Kimlik ve amaç
JabLab, Motion ailesinin gölge-antrenman (boks/dövüş sporu) uygulamasıdır (ASC adı "JabLab: Shadow Training"). motion-core'un paylaşılan hareket-tanıma çekirdeğini tüketecek 5 üründen biridir. Kod kurucu tetiğiyle açılana dek KAPALI; V0 kapısı D2 (fps/blur ölçümü — hızlı yumruk hareketinin kamerada güvenilir yakalanabilirliği) geçilmeden geliştirme başlamaz. **v3 ile şirket 12 kişilik STANDART İŞTİRAK KADROSU'na sahiptir** (EK-C, C2) — bitmemiş ürün de olsa kadro TANIMLI ve DEVREDE, yalnız kapsam "uykuda görevleri"yle sınırlı (rezervasyon sağlığı + marka/isim radarı + kilit-ihlal alarmı + hazırlık dosyaları). Aktivasyon günü kod-yazımı değil, tek toggle + her 12 ajanın "L4+ modu"na (bkz. ilgili runbook) geçişidir.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/jablab` · dizin `ventures/jablab/app` (+ `workspace`) · bundle id `com.yulalab.jablab`
- Store: ASC "JabLab: Shadow Training" (asc_id **6794715669**, durum `prepare-for-submission`) · Play (play_id 4972735151783398353, play_created: true)
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arızası)
- yulalab.com `/projects` + links.yulalab.com: "JabLab — Shadow Training" coming-soon kartı CANLI (kategori/eyebrow ASC adıyla senkron; connections.yaml cross_claim) — sosyal-kilitli (Meta/X/YT/LinkedIn bağlantıları kurucu görevi olarak beklemede, KK-2026-07-28 madde 1)
- Canonical: `ventures/jablab/VENTURE.md`, `ventures/jablab/workspace/DEFTER.md`

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`, v0.9.0) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. Breaking sözleşme değişikliği connections.yaml impact_rule gereği tüketici DEFTER'ine kayıt + pinli-sürüm güncellemesi ister. JabLab'in V0 kapısı (D2 fps/blur) motion-core'un **hızlı-hareket** performansına doğrudan bağlı — jab/kroşe gibi kısa-süreli yüksek-hız hareketlerde `motion_camera` modülünün (0.1.1, emülatör-canlı, judgedRatio 0,810) kare-kaçırma/blur payı diğer 4 üründen daha kritik; çekirdekteki performans regresyonu bu şirket için özellikle ağır sayılır.

## STANDART İŞTİRAK KADROSU (12 ajan — EK-C C2)
Kod kilidi açılana dek tamamı **uykuda görevleri** modunda çalışır (R0 tavan): rol tam-kapsamına geçmez, yalnız aşağıdaki daralmış işleri yürütür. Runbook'ların tamamı `ajanlar/istirakler/a7-jablab/` altında.

| # | Rol | Uykuda modunda iş | Uyanınca (F ile) |
|---|---|---|---|
| 1 | GM (a7-jablab-gm) | 11 ajanı koordine eder, aylık "uykuda özeti" + acil FLAŞ NOT derler | haftalık ŞİRKET RAPORU (C3) |
| 2 | Müşteri-Sesi (a7-jablab-musteri-sesi) | henüz kullanıcı yok — store ön-inceleme metinleri + benzer-ürün yorum ön-taraması (kalibrasyon amaçlı) | gerçek yorum/destek triyajı |
| 3 | İzleme & Doğruluk (a7-jablab-izleme-dogruluk) | ASC/Play/repo/motion-core sağlık pollingi | canlı ürün metrik doğruluğu |
| 4 | Rakip Analisti (a7-jablab-rakip-analisti) | boks/shadow-training dikeyinde listing/fiyat/özellik radarı | tam teardown + konumlandırma |
| 5 | Pazar Analisti (a7-jablab-pazar-analisti) | ev-boksu/fitness trend taraması (Trends/GSC) | pazar raporu + senaryo |
| 6 | Pazarlama Analisti (a7-jablab-pazarlama-analisti) | ASO ön-hazırlık (başlık/anahtar kelime taslağı), cross-claim tazelik kontrolü | funnel/kanal performansı |
| 7 | Güvenlik (a7-jablab-guvenlik) | repo sır/CVE taraması + kilit-ihlal alarmı | tehdit modelleme + pentest planı |
| 8 | Veri Gizliliği (a7-jablab-veri-gizliligi) | kamera-verisi işleme için KVKK/GDPR ÖN-envanteri (on-device pose-estimation varsayımıyla) | canlı beyan↔kod mutabakatı |
| 9 | Hukuk-Uyum (a7-jablab-hukuk-uyum) | "JabLab"/"Shadow Training" marka-tescil + isim çakışma radarı | ToS/EULA hazırlığı |
| 10 | Sosyal-Medya (a7-jablab-sosyal-medya) | hesap adı rezervasyonu takibi (bağlantı bekliyor — KK-2026-07-28 madde 1) | mention/etkileşim takibi |
| 11 | İçerik (a7-jablab-icerik) | coming-soon anlatı taslakları (yayınlanmaz, arşivlenir) | kanal içerik hattı |
| 12 | Kod & Test (a7-jablab-kod-test) | `ventures/jablab/app` dizininde commit/push algılama (izin YOK — kilit-ihlali alarmı) | build/test/coverage izleme |

## ŞİRKET RAPORU (C3 formatı — haftalık, GM derler)
**Tam kapsam (aktive olunca):** GM her hafta 11 ajanın çıktısını derler — sağlık/doğruluk (izleme) + müşteri sesi + rakip/pazar + pazarlama + güvenlik/gizlilik/hukuk + içerik performansı, hepsi kanıt-linkli → **doğrudan kurucuya** (Köprü + dosya). Holding Raporu'nun (yönetim katmanının ayrı sentezi) girdisi olur ama onun üstüne yazılmaz (C3-2, denetlenebilirlik).
**Uykuda modunda (bugün):** haftalık kadans yerine **aylık "uykuda özeti"** (rezervasyon sağlığı + marka radarı + motion-core pin durumu + hazırlık dosyalarının ilerleyişi, tek sayfa) + acil eşik tetiklenirse ay-dışı **FLAŞ NOT**. Rapor formatı ve alıcı aynı kalır (doğrudan kurucu); yalnız hacim/kadans daralır.

## GM yetkileri (C7)
- **C7-2 (acil çıktı rapor beklemez — SERT KURAL):** *"Hiçbir severity sinyali rapor bekletilerek geciktirilemez."* SEV0-1 + bu şirkete özel acil eşikler (aşağıdaki tablo) **ANINDA Köprü Kanalı'na** düşer — ajandan doğrudan, GM'i bile beklemez; GM eş-zamanlı bilgilendirilir.
- **FLAŞ NOT yetkisi:** GM, aylık uykuda-özeti dışında, ihtiyaç gördüğünde takvim-dışı ara-rapor (FLAŞ NOT) üretebilir — ör. ASC durumu beklenmedik şekilde değişirse.
- **C7-3 (talep-üzerine tetik — sınırlı yetki):** GM, KENDİ 11 ajanının workflow'unu cron beklemeden tetikleyebilir (ör. "JabLab" adında rakip app görüldü → Rakip Analisti'ni hemen koştur). Sınırlar: (a) yalnız a7-jablab ajanları — şirketler-arası tetik CEO üzerinden; (b) tetiklenen iş yine **R0 tavanında** (uykuda modda R1'e bile çıkmaz — SABLON gereği monitor-only en dar hali); (c) her tetik audit'e yazılır + günlük tetik/harcama bütçesi içinde (Cost Guard — runaway-GM freni); (d) kurucu her ajanı her an kendisi de tetikleyebilir (GM tekeli yok).

## Acil eşikleri (şirkete özel — SEV0-1 + C7-2 kapsamı)
| Durum/desen | Aksiyon | Severity |
|---|---|---|
| ASC durumu `prepare-for-submission` dışına kayar (asc_id 6794715669 poll) | Bulgu + Köprü bildirimi | SEV3 |
| Play kaydı (play_id 4972735151783398353) kaybolur/askıya alınır | ANINDA Köprü bildirimi | **SEV1** |
| `ventures/jablab/app` dizininde commit/push algılanır (kilit açık değilken) | Kilit-ihlali alarmı → kurucuya ANINDA | **SEV1** |
| bundle id `com.yulalab.jablab` başka kayıtla çakışır | ANINDA bildirim | **SEV1** |
| Store'da "JabLab" adıyla başka geliştirici app'i görünür | Marka radarı bulgusu → Hukuk-Uyum eşiği | SEV2 |
| motion-core'da fps/blur (V0-D2) performansını etkileyecek breaking-change commit algılanır | DEFTER bulgusu + pinli-sürüm hatırlatması, ANINDA | SEV2 |
| Sosyal hesap adı ("jablab"/"JabLab Shadow Training") üçüncü tarafça alınır | Marka-radarı bulgusu → Hukuk-Uyum + Sosyal-Medya | SEV2 |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | Etki notu: "Motion submit ettiğinde bu kurala tabi" | SEV3 |
| **tabloda olmayan HER durum** | ESKALE ET (asla tahmin etme) | — |

## Workflow'ları
> **KANONİK KEY NOTU (denetim düzeltmesi, 2026-07-28):** Bu şirketin bugün ÇALIŞTIRILABİLİR workflow'ları `workflows.yaml`'daki PARAMETRİK tanımlardır: `istirak-raporu` · `sirket-retrosu` · `flas-not` (hepsinde `params.sirket: a7-jablab`). Aşağıda geçen şirket-özel key adları **PLANLI (D5)** etiketlidir — ürün-pipeline'ları kurulurken workflows.yaml'a eklenmeden çalıştırılamazlar.

Beklenen key'ler (workflows.yaml v3'e eklenecek, henüz kayıtlı değil — C6 madde 2): `jablab-sirket-raporu` (aylık, uykuda modda) · `jablab-rezervasyon-sagligi` (haftalık) · `jablab-marka-radari` (haftalık) · `jablab-kilit-ihlal-alarmi` (olay-tetikli, sürekli devriye) · `jablab-gizlilik-on-envanteri` (tek-seferlik + çeyreklik tazeleme).

## Feedback döngüsü
Haftalık/aylık retro (DNA kural 1): kaçan-sinyal tanımı rol-başına ilgili runbook'ta; şirket-geneli ortak kaçan-sinyal = "ASC/Play/motion-core durumu değişti ama bildirilmedi" veya "kilit-ihlali fark edilmeden commit geçti". Runbook revizyon önerisi kurucu onayı olmadan uygulanmaz (İşletim DNA'sı, sürekli-güncellik döngüsü).

## Sınırlar
Kod dizinine YAZMAZ · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ (5/5 Motion roadmap'i zaten hazır) · uykuda modda R0 üstü yetki YOK · dış-yazma YOK · gerçek kullanıcı verisi YOK (henüz canlı ürün yok — Müşteri-Sesi ve Veri-Gizliliği rolleri hazırlık/kalibrasyon modunda).

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu: kurucu tetiği (vault başlangıç promptu) + V0 kapısı D2 (fps/blur ölçümü) geçişi. Kontrol listesi: (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü güncel · (3) ASC/Play kaydı hâlâ prepare-for-submission · (4) marka radarında açık çakışma yok · (5) 12 runbook'un tamamı L4+ moduna geçirildi (bkz. her runbook'un "L4+ modu" bölümü) · (6) CTO mimari kapısından geçti (fps/blur ölçüm kanıtı dahil) · (7) Veri-Gizliliği'nin kamera-verisi ön-envanteri DPIA taslağına terfi etti.

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk). Kilit-ihlali/mimari soru → CTO → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`. Kamera-verisi gizlilik sorusu → `privacy-data-guardian`. Rakip/pazar derinleşmesi → `competitive-intelligence-analyst`.
