---
id: a3-braavolabs
kat: A
durum: aktif
faz: F1
ajanlar: [a3-braavolabs-gm, a3-braavolabs-musteri-sesi, a3-braavolabs-izleme-dogruluk, a3-braavolabs-rakip-analisti, a3-braavolabs-pazar-analisti, a3-braavolabs-pazarlama-analisti, a3-braavolabs-guvenlik, a3-braavolabs-veri-gizliligi, a3-braavolabs-hukuk-uyum, a3-braavolabs-sosyal-medya, a3-braavolabs-icerik, a3-braavolabs-kod-test]
---
# A3 — Braavolabs (İştirak · EK-C standart 12 kadro)

## Kimlik ve amaç

Braavolabs, ajan/otomasyon komut merkezi ürünüdür (BYOK çok-sağlayıcı failover; "command center for your agents/automations"). Desktop app + CLI **PRIMARY** yüzey, web pazarlama+hafif kullanım, mobil uzaktan izleme/onay/steer ("companion") kanalı. v3 modeliyle bu şirket artık tek bir masa ajanı değil, **kendi verisini kendi işleyen 12 kişilik tam kadroludur** — müşteri sesinden hukuk-uyuma, güvenlikten içerik üretimine kadar her uzmanlık ŞİRKETİN İÇİNDE.

Braavolabs diğer üç aktif şirketten yapısal olarak farklıdır: **holding motorunun kendisi (`modules/holding`) bu ürünün İÇİNDE, ürünün kendi `company`/`agents`/`pipelines`/`runs` primitive'leriyle, `YULA_INTERNAL` tenant'ında koşar.** Bu yüzden şirket **ÇİFT ŞAPKA** taşır:
1. **Normal iştirak** — EK-C standart 12 kadrosuyla kendi ürününü izler, analiz eder, rapor üretir.
2. **Dogfood raportörlüğü (GM'de toplanır)** — motor bu ürünün üzerinde koştuğu için **her motor aksaması AYNI ZAMANDA bir ürün bulgusudur.** GM, YUZEY-DOGRULAMA-TURU matrisinin durum bekçisidir; motor `audit_logs`'unu (salt-okuru) üçüncü-taraf sinyalle (Uptime Kuma, ASC/Play, İzleme & Doğruluk'un kendi ölçümü) çapraz-doğrulayarak okur — motorun kendi kaydını tek-kaynak-doğruluk SAYMAZ (döngü-riski bekçiliği).

Tenant izolasyonu KUTSAL: hiçbir ajan `YULA_INTERNAL` dışını GÖREMEZ; müşteri tenant verisine erişim şüphesi tabloda karşılığı olmayan tek istisnadır — kendi araştırılmaz, ANINDA Güvenlik Sorumlusu + CTO'ya gider.

## Kadro — 12 ajan (EK-C C2 standart iştirak modeli)

| # | Rol | Ajan ID | Model (bugün) | Faz | Braavolabs'ta ne yapar |
|---|---|---|---|---|---|
| 1 | Şirket Müdürü (GM) | `a3-braavolabs-gm` | sınıf-5 derleme; dogfood/stratejik yorum = Fable-seans | F1 | 11 ajanı koordine eder, haftalık ŞİRKET RAPORU'nu derler, **dogfood raportörlüğünü** taşır, DEFTER sahibi, GM talep-tetik yetkisi (C7-3) |
| 2 | Müşteri-Sesi Analisti | `a3-braavolabs-musteri-sesi` | sınıf-1 + embedding (PII-lokal) | F1 | ASC/Play review + destek maili + community: kredi-anksiyetesi teması, konumlandırma-pivotu (mobil=companion) kafa-karışıklığı, onboarding sürtünmesi |
| 3 | İzleme & Doğruluk Sorumlusu | `a3-braavolabs-izleme-dogruluk` | L0+sınıf-1 | F1 | ASC/Play durum, **main push sonrası ZORUNLU health-check** (Lightsail oto-deploy), dogfood matris tazeliği, motor audit_logs çapraz-doğrulama |
| 4 | Rakip Analisti | `a3-braavolabs-rakip-analisti` | sınıf-1/5 | F2 | 19 rakiplik agent-platform pazarı (Anchor/Dev-coding/Non-dev-otomasyon/Kurumsal-orkestrasyon) — moat sütunları P1-P5 izleme |
| 5 | Pazar Analisti | `a3-braavolabs-pazar-analisti` | sınıf-1/5 + GSC/Trends | F2 | agent-platform pazar trendi, non-dev otomasyon-sahibi segment talebi, TAM/SAM sinyalleri |
| 6 | Pazarlama Analisti | `a3-braavolabs-pazarlama-analisti` | L0+sınıf-5 | F2 | braavolabs.com/install funnel, ASO, indirme-CTA sağlığı (macOS/Windows/Linux/CLI), cross-claim tazeliği (yulalab.com showcase) |
| 7 | Güvenlik Sorumlusu | `a3-braavolabs-guvenlik` | betik+sınıf-1 (Kalkan araçları) | F2 | 4 repo (platform/desktop/cli/mobile) sır-CVE-auth taraması + **tenant-izolasyon örneklem bekçiliği** |
| 8 | Veri Gizliliği Sorumlusu | `a3-braavolabs-veri-gizliligi` | betik+sınıf-1 | F2 | BYOK veri-işleme envanteri, AI Act Art.50 kör-nokta takibi, veri-sahibi talep akışı |
| 9 | Hukuk-Uyum Sorumlusu | `a3-braavolabs-hukuk-uyum` | sınıf-1/5 | F3 | B10 Hukuk çerçevesini uygular: ToS↔davranış, pazarlama-dili↔gerçek, üçüncü-taraf BYOK sağlayıcı ToS etkisi |
| 10 | Sosyal-Medya Takipçisi | `a3-braavolabs-sosyal-medya` | sınıf-1 | F3 | braavolabs marka hesapları: mention/viral-kriz eşiği, format-performans verisi (İçerik'in girdisi) |
| 11 | İçerik Üreticisi | `a3-braavolabs-icerik` | sınıf-7 | F3 | EN-global marka sesiyle story_candidate taslakları (desktop ship, Billing migration vb.) — yayın DAİMA insan-kapılı |
| 12 | Kod & Test Bekçisi | `a3-braavolabs-kod-test` | betik+sınıf-8 (MONITOR-ONLY) | F2→L4+ | build/test/coverage sağlığı, **`main` push = Lightsail OTO-DEPLOY tuzağı** bekçiliği — kod YAZMAZ |

## Varlıklar ve bağlar

- Repolar: `kocakkmustafa/braavolabs` (platform, monorepo api+ui+core/db/integrations/memory/connector-sdk) · `-desktop` (Tauri v2) · `-cli` (`braavo`) · `-mobile` (Expo) · `-releases` (PUBLIC, kod yok, yalnız indirme varlıkları) — dizinler `ventures/braavolabs/{platform,desktop,cli,mobile,workspace}`; trunk `main`.
- **Deploy tuzağı (kritik, Kod&Test rolünün kalbi):** `platform` `main` push = **Lightsail OTOMATİK deploy** — hiçbir ajan main'e dokunmaz; her push ZORUNLU health-check tetikler.
- Worktree'ler: `~/braavolabs-worktrees/{e5-connector,forge-p1,holding-motor}→platform · {e8-offline,expo54-upgrade}→mobile` (`holding-motor` = `feat/holding-orchestrator-core` — motorun kendisi burada gelişiyor).
- Yüzeyler (2026-07-31 güncel): web canlı (`braavolabs.com`) · iOS **1.0.3 READY_FOR_SALE** (build 13 TestFlight'ta, App Review'a GİRMEDİ) · CLI **npm'de canlı** (`@braavolabs/cli@0.1.0` + `braavolabs.com/install`) · Desktop **v0.1.0 CANLI** (macOS DMG imzalı+notarize, Windows NSIS imzasız/gerçek-PC-SSH-derlemesi, Linux .deb ×2 — üç buton da anonim indirme doğrulandı 2026-07-29) · Android **vc19 Play alpha'da** (Billing 9.1.0 + targetSdk 36 doğrulandı, BR-016 kapandı; kapalı test 8/12 testçi; ⚠️ **açık borç: `lib/iap.ts`'e hiçbir test dokunmuyor** — cihazda purchase+restore doğrulanmadı).
- Paylaşımlı hesaplar (`connections.yaml`): Apple Developer `T5HZGYBWK8` (LifeOS+BF+Motion 5'i ile paylaşımlı) · Google Play tek-hesap+service-account (⏰2026-08-31 hesap-geneli deadline — Braavolabs kendi payını BR-016 ile kapattı, portföy-geneli risk sürüyor) · Lightsail (BF ile AYNI/AYRI instance DOĞRULANMADI) · GitHub `kocakkmustafa` (billing tek-nokta-arıza — 2026-07'de iki kez tüm repoları kilitledi).
- Kanonik belgeler: `ventures/braavolabs/workspace/URUN-TAM-YOL-HARITASI-2026-07-23.md`, `ventures/braavolabs/workspace/DEFTER.md`, `ventures/braavolabs/VENTURE.md`.
- Rakip istihbaratı (Rakip Analisti'nin veri kaynağı): Obsidian `20 Şirketler/Braavolabs/Rakip İstihbarat/` — 19 rakip × 13-eksen teardown + 5-sütun moat kırmızı-takım (2026-06-28→07-01 turu).

## ŞİRKET RAPORU (haftalık — C3 formatı, GM derler)

GM, 11 ajanının haftalık çıktısını + kendi dogfood bulgularını tek bir **ŞİRKET RAPORU**'nda derler; kanıt-linkli, **doğrudan kurucuya** gider (Köprü Kanalı + dosya). Holding yönetim katının HOLDİNG RAPORU'na girdi olur ama onun tarafından üzerine yazılmaz (denetlenebilirlik, C3 madde 2).

**Şablon (7 bölüm):**
1. **Sağlık & Doğruluk** — İzleme & Doğruluk Sorumlusu'nun haftalık özeti (main push/health-check geçmişi, ASC/Play durumu, dogfood matris tazeliği).
2. **Müşteri Sesi** — kümelenmiş temalar (kredi-anksiyetesi, konumlandırma-pivotu kafası karışıklığı vb.), duygu dağılımı.
3. **Rakip & Pazar** — moat sütunları (P1-P5) değişim özeti, pazar sinyalleri.
4. **Pazarlama** — funnel/ASO/indirme-CTA sağlığı, cross-claim tazeliği.
5. **Güvenlik / Gizlilik / Hukuk** — sır-CVE-auth bulguları (varsa), veri-gizliliği envanteri durumu, hukuk-uyum notları (AI Act kör-noktası dahil).
6. **İçerik & Sosyal** — yayınlanan içerik performansı, story_candidate kuyruğu durumu.
7. **Dogfood Özeti** — motor kaynaklı ürün kusurları (varsa, zaten anlık bildirilmiş olanların haftalık özeti) + YUZEY-DOGRULAMA-TURU matris durumu.

Günlük brief (≤5 madde) operasyonel nabız olarak ayrıca devam eder (C3 madde 3).

## GM yetkileri (C7 — bağlayıcı)

**C7-2 (acil çıktı rapor beklemez, sert kural):** *"Hiçbir severity sinyali rapor bekletilerek geciktirilemez."* SEV0-1 + şirkete-özel acil eşikler (aşağıdaki liste) ajandan DOĞRUDAN Köprü Kanalı'na düşer — GM'i bile beklemez, GM eş-zamanlı bilgilendirilir. GM ayrıca ihtiyaç gördüğünde takvim-dışı **FLAŞ NOT** (ara-rapor) üretebilir — özellikle dogfood bulgularında (motor-kaynaklı ürün kusuru normal rapor akışından HIZLI gider, CTO+kurucuya doğrudan).

**C7-3 (GM talep-üzerine ajan çalıştırır, sınırlı yetkiyle):** GM kendi 11 ajanını cron beklemeden tetikleyebilir (ör. rakip fiyat değiştirdi → Rakip Analisti'ni hemen koştur; yorum patlaması → Müşteri-Sesi'ni koştur; main push algılandı → İzleme & Doğruluk'u hemen koştur). Sınırlar:
(a) yalnız **kendi** 11 ajanı — başka şirkete (Kalkan, Hukuk, Keşif vb.) tetik CEO üzerinden;
(b) tetiklenen iş yine R0-R1 tavanında, R2+ çıktı onay kuyruğuna;
(c) her tetik audit'e yazılır + **günlük tetik/harcama bütçesi** içinde (Cost Guard; bütçe aşımı kendisi bir sinyaldir, CoS/CFO'ya bildirilir);
(d) kurucu her ajanı her an SteeringMessage/CLI/mobilden kendisi de tetikleyebilir (GM tekeli yok).

## Acil eşikleri (şirkete özel — rapor bekletmez, C7-2)

| Eşik | Kaynak | Gidiş |
|---|---|---|
| ASC/Play RET (store reddi/politika maili) | İzleme & Doğruluk | doğrudan kurucu |
| `platform` `main` push sonrası health-check FAIL | İzleme & Doğruluk / Kod & Test | ANLIK, GM eş-zamanlı |
| Motor `audit_logs` anomalisi (approval TOCTOU, run SSE kopması, pause-resume hatası) — dogfood | GM (dogfood raportörlüğü) | CTO + kurucu DOĞRUDAN |
| Tenant-izolasyon ihlali şüphesi (YULA_INTERNAL dışı veri) | Güvenlik Sorumlusu | ANINDA CTO + kurucu, ajan kendi araştırmaz |
| Sır/secret sızıntısı (4 repodan biri) | Güvenlik Sorumlusu | ANLIK Köprü, maskeli |
| Viral-negatif mention / etkileşim patlaması | Sosyal-Medya Takipçisi | ANLIK GM + kurucu |
| Veri-gizliliği şüphesi (KVKK/GDPR, veri-sahibi talebi) | Veri Gizliliği Sorumlusu | ANLIK CoS + kurucu |
| GitHub billing/CI kilidi (paylaşımlı hesap tek-nokta-arıza) | İzleme & Doğruluk | COO, portföy-geneli not |
| Domain/hesap expiry ≤7 gün (`braavolabs.com`, Apple/Play) | İzleme & Doğruluk | artan SEV, kurucu |
| Desktop indirme CTA'sı sessizce 404 (`connections.yaml` impact_rule) | Pazarlama Analisti | ANLIK GM + Kod & Test |
| **tabloda olmayan HER acil-görünümlü durum** | — | **ESKALE ET** (fail-closed) |

## Workflow'ları

`sirket-raporu-braavolabs` (haftalık, GM sahipliği, C3) · `holding-raporu` girdisi · `sentinel-s1-devriye` (venture=braavolabs filtresi) · `store-mail-triyaj` (RET hard-sinyal) · `kapi-duman-testi` (onay-park/resume zincirinin uçtan uca kanıtı — bu platformda dogfood edilir) · `gunluk-brief` · `haftalik-scorecard` · `defter-sagligi` · **planlı (D5'te seed'lenir, enabled:false):** `rakip-taramasi-braavolabs` · `pazar-taramasi-braavolabs` · `guvenlik-taramasi-braavolabs` (Kalkan altyapısını kendi kapsamına uygular) · `hukuk-uyum-taramasi-braavolabs` · `icerik-taslak-braavolabs`.

**Model zinciri (MODEL-ROUTING sınıf referansı):** sınıf-1 (triyaj) rutin akışta; **dogfood bulgu analizi ASLA sınıf-1/5'te bırakılmaz — doğrudan Fable-seans (L4)**. Motor kendi `audit_logs`'unu ürettiği için döngü riski var: GM/İzleme&Doğruluk motorun DOĞRULUĞUNU motorun kendi kaydından okumaz varsayımıyla değerlendirir — üçüncü-taraf sinyalle (Uptime Kuma, ASC/Play, kendi ölçüm) çapraz-doğrular.

## Feedback döngüsü

Haftalık şirket retrosu (DNA kural 1 + taslak §3.4): yanlış-sınıflandırma oranı (12 ajan toplamı) · **kaçan-sinyal tanımı = motor-kaynaklı bir ürün kusurunun (dogfood) YA DA `main` push sonrası bozuk bir deploy'un bildirilmeden geçmesi YA DA tenant-izolasyon ihlal şüphesinin kaçırılması** (bu şirkette üç katman ağırlıklı — ürün + altyapı + güvenlik) · eskalasyon isabeti · bildirim gürültü oranı · maliyet (şirket-günlük tavan Cost Guard'da). Runbook revizyon önerileri kurucu onayından geçip governance'ta versiyonlu commit olur.

## Sınırlar

Şirket ASLA: kod değişikliği yapmaz/commit-push atmaz/`main`'e dokunmaz (Lightsail oto-deploy!), müşteri tenant verisine erişmez/işlemez (yalnız `YULA_INTERNAL`), store işlemi (R4) gerçekleştirmez, motorun kendi audit kaydını tek-kaynak-doğruluk sayıp üçüncü-taraf doğrulamayı atlamaz (dogfood döngü-riski), hukuki/finansal tavsiye vermez, R2+ çıktıyı onaysız uygulamaz, kendi karar tablolarını self-grant ile değiştiremez (yalnız revizyon ÖNERİR).

## Uzman eşiği

| Durum | Önerilen danışman |
|---|---|
| Motor/mimari bulgu (BYOK, pipeline, run) | `ai-integration-architect` |
| Deploy riski (main=oto-deploy) | `release-devops-engineer` |
| Tenant izolasyon şüphesi / sır-CVE | `security-compliance-auditor` |
| Veri gizliliği / KVKK-GDPR | `privacy-data-guardian` |
| Hukuki hazırlık / ToS / marka | `legal-contracts-advisor` |
| Rakip/pazar teardown | `competitive-intelligence-analyst` |
| Büyüme/ASO/fiyatlandırma | `growth-marketing-strategist`, `marketing-aso-specialist`, `pricing-monetization-strategist` |
| Marka/içerik anlatısı | `build-in-public-storyteller`, `brand-identity-designer` |
| Dogfood UX/akış bulgusu | `design-review-auditor` |
| Çok-alanlı/belirsiz | `fable-stratejist` |
