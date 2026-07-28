---
id: a3-braavolabs
kat: A
durum: aktif
faz: F1
ajanlar: [13-braavolabs-masasi]
---
# A3 — Braavolabs

## Kimlik ve amaç
Braavolabs, ajan/otomasyon komut merkezi ürünüdür (BYOK, çok-sağlayıcı failover) — masa YÜZEYİ, Forge platformu + desktop + CLI + mobile'ın sinyal→bulgu→brief hattını taşır ve kod YAZMAZ. Bu şirket diğer üçünden farklı: **holding motorunun kendisi (`modules/holding`) bu ürünün İÇİNDE koşar** — masa bu yüzden ikinci bir kalıcı görev taşır (aşağıda).

Ölçek kuralı (taslak §1): Braavolabs'ın primitive'leri (`company`/`agents`/`pipelines`/`runs`) holding'in KENDİ yürütme yüzeyidir — bu nedenle bu şirket yalnız "her ürün ayrı şirket" ilkesinin bir örneği değil, aynı zamanda motorun barındığı zemindir. Masa sözleşmesi: `governance/sozlesmeler/venture-desk-braavolabs.md` (allowed/forbidden tools + cost_ceiling + model_chain — burada TEKRAR edilmez, DNA kural 8).

## Dogfood çift-şapka (KK-2026-07-27)
Masa iki şapka giyer:
1. **Normal venture masası** — diğer üç masayla aynı: sinyal triyajı, DEFTER bulgu önerisi, brief satırı.
2. **Dogfood raportörlüğü** — holding motoru Braavolabs'ın **YULA_INTERNAL tenant'ında**, ürünün kendi `company`/`agents`/`pipelines`/`runs` primitive'leriyle çalışır (taslak §1: "holding çalıştıkça ürünün kendisi test edilir"). Sonuç: her motor aksaması AYNI ZAMANDA bir ürün bulgusudur. Masa, **YUZEY-DOGRULAMA-TURU matrisinin durum bekçisidir** — motor `audit_logs`'unu okur, matris satırı bayatlarsa/motor kaynaklı bir kusur (yanlış pause-resume, run SSE kopması, approval çift-karar TOCTOU vb.) tespit ederse bunu doğrudan **CTO + kurucuya** eskale eder (normal masa akışından daha hızlı — bu sinyal hem ürün hem altyapı riski taşır).
Tenant izolasyonu KUTSAL: masa yalnız `YULA_INTERNAL` tenant'ını görür, müşteri tenant verisine ASLA erişmez (sözleşme `venture-desk-braavolabs`, forbidden_tools).

## Varlıklar ve bağlar
- Repolar: `kocakkmustafa/braavolabs` (platform) · `-desktop` · `-cli` · `-mobile` — dizinler `ventures/braavolabs/{platform,desktop,cli,mobile,workspace}`; trunk `main`.
- **Deploy tuzağı (kritik):** platform `main` push = **Lightsail OTOMATİK deploy** — masa main'e ASLA dokunmaz.
- Worktree'ler: `~/braavolabs-worktrees/{e5-connector,forge-p1,holding-motor}→platform · {e8-offline,expo54-upgrade}→mobile` (holding-motor = `feat/holding-orchestrator-core`).
- Yüzeyler: web canlı (`braavolabs.com`) · iOS canlı (1.0.2) · Android kapalı-test (vc14, 12 testçi/14 gün bekliyor).
- Paylaşımlı hesaplar: Apple Developer `T5HZGYBWK8` · Google Play (deadline **2026-08-31**) · Lightsail (backend main-push=oto-deploy; BF ile AYNI/AYRI instance DOĞRULANMADI) · GitHub `kocakkmustafa`.
- Kanonik belgeler: `ventures/braavolabs/workspace/URUN-TAM-YOL-HARITASI-2026-07-23.md`, `ventures/braavolabs/workspace/DEFTER.md`, `ventures/braavolabs/VENTURE.md`.

## İzleme hedefleri
| Sinyal/durum | Yöntem/kaynak | Faz | Aksiyon/eskalasyon |
|---|---|---|---|
| ASC durum değişimi | ASC Webhooks API + Gmail | F1 | RET = hard sinyal → doğrudan kurucu |
| Google Play review/durum (vc14, 12 testçi/14 gün) | Play Developer API poll | F1 | sayaç eşiğinde artan SEV |
| Lightsail `main` push sonrası deploy sağlığı | Uptime Kuma + deploy-log korelasyonu | F1 | push sonrası ANLIK health-check ZORUNLU (oto-deploy riski) |
| Motor `audit_logs` (dogfood) | motor'un kendi audit-kaydı, salt-okuma | F1 | motor kaynaklı ürün kusuru → CTO + kurucu |
| YUZEY-DOGRULAMA-TURU matrisi tazeliği | dogfood raportörlüğü (masa) | F1 | matris satırı bayatlarsa bulgu → DEFTER |
| GitHub Actions/CI + billing sağlığı (holding-motor worktree dahil) | `gh` API poll (paylaşımlı — billing tek-nokta-arızası) | F2 | CI kırığı/billing kilidi → COO |
| Tenant izolasyon örneklem denetimi | Kalkan (B6) ile ortak; masa yalnız kendi tenant'ını görür | F3 | şüphe → doğrudan CTO |
| Domain expiry (`braavolabs.com`) | RDAP/whois betiği (ücretsiz, LLM'siz) | F1 | yenileme yaklaşınca artan SEV |
| **tabloda olmayan HER durum** | — | — | **ESKALE ET** |

## Workflow'ları
`sentinel-s1-devriye` (venture=braavolabs filtresi) · `store-mail-triyaj` (RET hard-sinyal) · `kapi-duman-testi` (onay-park/resume zincirinin uçtan uca kanıtı — bu platformda dogfood edilir) · `gunluk-brief` · `haftalik-scorecard` · `defter-sagligi`.

**Model zinciri (MODEL-ROUTING sınıf referansı):** sınıf-1 (triyaj — Qwen3-4B → Gemini Flash-Lite → Haiku) normal masa akışında; **dogfood bulgu analizi ASLA sınıf-1/5'te bırakılmaz — doğrudan Fable-seans (L4)** (sözleşme `venture-desk-braavolabs` model_chain). Motor kendi `audit_logs`'unu ürettiği için burada bir döngü riski var: masa motorun DOĞRULUĞUNU motorun kendi kaydından okumaz varsayımıyla değerlendirir — üçüncü-taraf sinyalle (Uptime Kuma, ASC/Play) çapraz-doğrular.

## Feedback döngüsü
Haftalık masa retrosu: yanlış-sınıflandırma oranı · **kaçan-sinyal tanımı = motor-kaynaklı bir ürün kusurunun (dogfood) YA DA `main` push sonrası bozuk bir deploy'un bildirilmeden geçmesi** (bu şirkette çift ağırlıklı — hem ürün hem altyapı) · eskalasyon isabeti · bildirim gürültüsü · maliyet ($0.50/run tavanı — sözleşme `venture-desk-braavolabs`).

## Sınırlar
Masa ASLA: kod değişikliği yapmaz, commit/push atmaz, `main`'e dokunmaz (Lightsail oto-deploy!), müşteri tenant verisine erişmez/işlemez (yalnız YULA_INTERNAL), store işlemi (R4) gerçekleştirmez, motorun kendi audit kaydını tek-kaynak-doğruluk sayıp üçüncü-taraf doğrulamayı atlamaz (dogfood döngü-riski bekçiliği).

## Uzman eşiği
Motor küçük modelle çalışır; danışman çağrısı yalnız kurucu-oturumunda — eskalasyon çıktısına `onerilen_danisman` yazılır, dogfood bulguları için doğrudan Fable-seans (sözleşme: "dogfood bulgu analizi = Fable-seans").
| Durum | Önerilen danışman |
|---|---|
| Motor/mimari bulgu (BYOK, pipeline, run) | `ai-integration-architect` |
| Deploy riski (main=oto-deploy) | `release-devops-engineer` |
| Tenant izolasyon şüphesi | `security-compliance-auditor` |
| Dogfood UX/akış bulgusu | `design-review-auditor` |
| Çok-alanlı/belirsiz triyaj | `fable-stratejist` |
