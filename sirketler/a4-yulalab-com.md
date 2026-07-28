---
id: a4-yulalab-com
kat: A
durum: aktif
faz: F1
ajanlar: [14-yulalab-com-masasi]
---
# A4 — yulalab.com

## Kimlik ve amaç
yulalab.com, holding'in vitrin sitesidir (`yulalab.com` + `links.yulalab.com`) — 8 ürün gösterir (3 canlı + 5 motion coming-soon). Masa kod YAZMAZ; portföyün "dış yüzü tutarlı mı" bekçisidir: uptime/deploy sağlığı + **çapraz-iddia (cross-claim) tazeliği** — connections.yaml'daki `cross_claims` ve `impact_rules` bu masanın icra alanıdır.

Ölçek kuralı (taslak §1): yeni bir motion ürünü (A5-A9) aktive olduğunda yulalab.com'daki "coming-soon" kaydı canlıya döner — bu şirketin kendisi DEĞİŞMEZ, yalnız izlediği cross-claim satır sayısı büyür. Masa sözleşmesi: `governance/sozlesmeler/venture-desk-yulalab-com.md` (allowed/forbidden tools + cost_ceiling + model_chain — burada TEKRAR edilmez, DNA kural 8).

## Varlıklar ve bağlar
- Repolar: `kocakkmustafa/yulalab-web` (site) · `kocakkmustafa/yulalab-links` (links) — dizinler `ventures/yulalab-com/{site,links}`.
- **Deploy tuzağı (kritik, iki repo İKİ FARKLI dal):** site trunk `main` (Vercel prod=main) · links trunk `develop` (Vercel prod=develop) — 2026-07-26'da yanlışlıkla main'e push denenip yakalanmıştı (gotcha kaydı).
- Yüzeyler: `yulalab.com` canlı (8 ürün: 3 canlı + 5 motion coming-soon) · `links.yulalab.com` canlı (2-sütun portfolio grid; store butonları hâlâ 3 canlı marka için **manuel senkron**, son senkron 2026-07-10).
- Paylaşımlı hesaplar: Vercel (members: burun-farki + yulalab-com — risk: "İKİ FARKLI prod-dal kuralı: BF=develop, yulalab-site=main — karıştırma klasik tuzak"; yulalab'ın KENDİ içinde de site/links ayrı dal tuzağı var, üstteki maddeyle KARIŞTIRMA) · GitHub `kocakkmustafa`.
- Kanonik belgeler: `ventures/yulalab-com/site/BITIRME-PROGRAMI.md`, `ventures/yulalab-com/site/DEFTER.md`, `ventures/yulalab-com/VENTURE.md`.

## İzleme hedefleri
| Sinyal/durum | Yöntem/kaynak | Faz | Aksiyon/eskalasyon |
|---|---|---|---|
| Herhangi bir store durumu değişir | `impact_rules` kontrolü (connections.yaml) → links.yulalab.com butonları + yulalab.com README | F2 | "bayatladı" bildirimi → DEFTER önerisi |
| BF model metrikleri değişir (Top-1/Top-3 doğruluk) | `impact_rules` kontrolü → yulalab.com README + proje kartı stats | F2 | tazeleme önerisi |
| Braavolabs showcase görselleri | `cross_claims` takibi (Y-007, BR2 UI seansı sonrası tazelenecek) | F2 | tazeleme önerisi |
| Motion 5 app adı/tagline/kategori senkronu | `cross_claims` taraması (ASC adlarıyla senkron olmalı) | F2 | drift bulgusu → DEFTER |
| Vercel deploy sonucu — yulalab KENDİ içi (site=main / links=develop) | Gmail (Vercel free planda webhook yok) + dal-adı kontrolü | F1 | yanlış-dal push riski bekçiliği |
| Vercel deploy tuzağı — CROSS-VENTURE (BF=develop iken yulalab-site=main) | connections.yaml `shared_accounts.vercel` risk notu | F1 | portföy-geneli dal-karışıklığı riskini brief'e taşı |
| GSC organik/SEO sağlığı | GSC API | F2 (Keşif ile paylaşılan) | fırsat listesine besleme |
| Domain expiry (`yulalab.com`) | RDAP/whois betiği (ücretsiz, LLM'siz) | F1 | yenileme yaklaşınca artan SEV |
| **tabloda olmayan HER durum** | — | — | **ESKALE ET** |

## Workflow'ları
`sentinel-s1-devriye` (venture=yulalab-com filtresi) · `gunluk-brief` · `haftalik-scorecard` · `defter-sagligi` (BAYAT durum satırı taraması, H-008 — bu şirkette cross-claim tazeliğiyle doğrudan örtüşür).

**Model zinciri (MODEL-ROUTING sınıf referansı):** sınıf-1 (buton/README metin taraması, tazelik sınıflandırması); içerik/kopya önerileri sınıf-7 (Qwen3-8B taslak) + yayın DAİMA insan-kapılı (marka kapısı). Cross-claim tutarsızlığı bir "sınıflandırma" değil "eşleştirme" işidir — betik + sınıf-1 birlikte çalışır, LLM yorum katmadan önce betik diff'i üretir.

## Feedback döngüsü
Haftalık masa retrosu: yanlış-sınıflandırma oranı · **kaçan-sinyal tanımı = bir store-durumu değişikliğinin links.yulalab.com butonlarına yansımadan uzun süre geçmesi YA DA bir BF metrik güncellemesinin README'ye yansımaması** (bayat cross-claim, H-008) · eskalasyon isabeti · bildirim gürültüsü · maliyet ($0.25/run tavanı — sözleşme `venture-desk-yulalab-com`, portföyün en düşük tavanı: site salt-vitrin).

## Sınırlar
Masa ASLA: kod değişikliği yapmaz, commit/push atmaz, deploy tetiklemez (iki repo FARKLI prod dalı — klasik tuzak), DNS/domain işlemi yapmaz, içerik/kopya değişikliğini insan-onayı olmadan yayına almaz (marka kapısı).

## Uzman eşiği
Motor küçük modelle çalışır; danışman çağrısı yalnız kurucu-oturumunda — eskalasyon çıktısına `onerilen_danisman` yazılır.
| Durum | Önerilen danışman |
|---|---|
| Cross-claim tutarsızlığı / bayat bilgi | `product-status-analyst` |
| SEO fırsatı/gerilemesi | `seo-strategist` |
| Görsel/marka tutarlılığı | `brand-identity-designer` |
| Store buton senkron gecikmesi | `marketing-aso-specialist` |
| Çok-alanlı/belirsiz triyaj | `fable-stratejist` |
