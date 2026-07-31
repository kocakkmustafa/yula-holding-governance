---
id: b2-kesif
kat: B
durum: aktif
faz: F2
ajanlar: [21-fikir-radarcisi, 22-ihtiyac-madencisi, 23-icerik-firsatcisi, 24-rakip-radarcisi, 25-seo-firsatcisi, 26-sentezci]
---
# YULA Keşif (Scout) — v3 · YENİ-PAZAR KEŞFİ + TARAMA ALTYAPISI

## Kimlik ve amaç

**v3'te Keşif'in kapsamı daraldı, ama daha netleşti:** mevcut 4 aktif dikeyin (LifeOS, Burun Farkı, Braavolabs, yulalab.com) İÇİNDEKİ pazar/rakip analizi artık ilgili iştirakin kendi Pazar Analisti + Rakip Analisti rollerindedir (EK-C C2 rol 4-5 — ör. `a1-lifeos-pazar-analisti`, `a1-lifeos-rakip-analisti`). Keşif artık **mevcut dikeylerin DIŞINDaki** fırsatları tarar: tamamen yeni ürün/proje fikirleri, henüz portföyde olmayan pazar segmentleri, adjacent-kategori rakip hareketleri, cross-vertical içerik temaları — yani "bir sonraki venture ne olabilir" ve "hiçbir mevcut şirketin bakmadığı köşede ne var" sorularının cevabı. İkinci ayağı **tarama altyapısıdır:** HN/Product Hunt/GH Trending/Reddit/GSC/Trends API bağlantıları paylaşılan araçlardır — iştiraklerin kendi Pazar/Rakip/Pazarlama Analistleri KENDİ dikeylerinde aynı araçları KENDİ GSC property'leri ve KENDİ rakip listeleriyle çalıştırır; Keşif araçları kurar/bakımını yapar, çıktıyı YALNIZ dikey-dışı taramada kendisi yorumlar. Kendisi hiçbir karar vermez, hiçbir şey yayınlamaz, hiçbir hesaba yazmaz: yalnız bulur, sınıflandırır, kanıtıyla birlikte önerir.

## v3 rol değişikliği

**Devretti:** Mevcut 4 aktif dikeyin İÇİNDEKİ rakip teardown'u ve pazar trend analizi → ilgili iştirakin Rakip Analisti + Pazar Analisti rollerine (`a1-lifeos-rakip-analisti`/`a1-lifeos-pazar-analisti`, `a2-burun-farki-rakip-analisti`, `a3-braavolabs-rakip-analisti`/`a3-braavolabs-pazar-analisti`, `a4-yulalab-com-rakip-analisti`/`a4-yulalab-com-pazar-analisti`); kendi store yorumlarının ihtiyaç-madenciliği → ilgili iştirakin Müşteri-Sesi Analisti'ne (EK-C C2 rol 2); kendi sitelerinin GSC pozisyon-5-20 "hızlı kazanç" taraması → ilgili iştirakin Pazar/Pazarlama Analisti'ne (C2 rol 5-6, ikisi de GSC/Trends erişimli). Haftalık Fırsat Raporu artık iştiraklerin kendi ŞİRKET RAPORU'ndaki pazar/rakip bölümleriyle ÇAKIŞMAZ — yalnız dikey-dışı/yeni-fırsat maddelerini taşır.

**Tuttu:** Tarayıcı ALTYAPISI (HN Algolia, Product Hunt GraphQL, GitHub Search API, Reddit PRAW read-only, Google Trends, GSC API bağlantıları — kurulum/bakım/health-check Keşif'te kalır, iştirakler bu boruları KENDİ verisiyle yeniden kullanır); Fikir-radarcısı (21, tamamen yeni ürün/proje fikri — hiçbir mevcut dikeye ait değil); İhtiyaç-madencisi (22, artık dikey-dışı/adjacent kategori ihtiyaç madenciliği + Reddit geniş-konu dinleme); İçerik-fırsatçısı (23, cross-vertical/yeni-tema içerik fırsatı — B3 Medya'nın holding-marka içeriğine besler, tek bir ürünün kendi içerik takvimine değil); Rakip-radarcısı (24, artık YENİ giren oyuncu/adjacent-kategori rakip taraması — mevcut dikeylerin bilinen rakiplerinin derin teardown'u değil); SEO-fırsatçısı (25, artık cross-property/yeni-anahtar-kelime-kümesi fırsatı — mevcut sitelerin kendi pozisyon-5-20 optimizasyonu değil); Sentezci (26, haftalık Fırsat Raporu artık yalnız dikey-dışı fırsatları sentezler).

## Varlıklar ve bağlar

Tüm kaynaklar resmî API/feed önceliklidir (Anayasa İlke 8 — Reddit yalnız dinleme, scraping/ToS ihlali yok); bu bölümdeki bağlantılar **paylaşılan altyapıdır** — iştiraklerin kendi Pazar/Rakip/Pazarlama Analistleri de aynı bağlantıları KENDİ dikeyleriyle sınırlı kullanır:
- **Hacker News:** HN Algolia Search API (`hn.algolia.com/api/v1`, key gerektirmez, herkese açık).
- **Product Hunt:** resmî GraphQL API — `PH_API_TOKEN` zaten mevcut (`~/.secrets/yula/`).
- **GitHub Trending:** resmî bir "trending" endpoint'i YOK (dürüst not) — GitHub Search API (`created:>tarih sort:stars`) resmî alternatif olarak kullanılır; topluluk trending-cache'i yalnız çapraz-doğrulama için.
- **Kendi store yorumlarımız:** `app-publish` MCP (zaten bağlı) — `apple_list_reviews` / `google_list_reviews`; v3'te bu veri ÖNCELİKLE ilgili iştirakin Müşteri-Sesi Analisti'ne akar, Keşif yalnız kategori-geneli/adjacent-ürün ihtiyaç deseni ararken kullanır.
- **Rakip store yorumları/listing'leri:** aynı resmî store sayfaları, herkese açık/oturumsuz okuma; bilinen-rakip derinlemesine takibi iştirakin Rakip Analisti'nde, Keşif yalnız yeni-giren tespitinde.
- **Reddit:** PRAW (Python Reddit API Wrapper), **read-only**, 4 hesap credential'ı `~/.secrets/yula/` altında — yalnız dinleme, asla post/yorum/DM (Anayasa İlke 8, 04-DISCLOSURE-BIP §4).
- **Google Trends:** resmî ücretsiz API YOK (dürüst not) — herkese açık, oturumsuz `trends.google.com` verisine topluluk kütüphanesiyle erişilir.
- **GSC (Google Search Console) API:** tam ücretsiz, 40K QPM — Ahrefs API alınmadı (maliyet, §3.2 gerekçesi); property-bazlı erişim iştirakin Pazar/Pazarlama Analisti'nde, Keşif yalnız cross-property/yeni-küme taramasında.

## Hizmet kapsamı

Beş günlük/haftalık tarama hattı (§3.5 taslak tablosu) + bir haftalık sentez hattı; çıktı iki katmanlı: **günlük dijest** (≤3 sinyal/tarayıcı, Köprü Kanalı'na değil, iç kuyruğa) + **haftalık Fırsat Raporu** (Köprü Kanalı'na, kanıt-linkli, YALNIZ dikey-dışı/yeni-fırsat maddeleri). Her tarayıcı **descriptor-tabanlı** çalışır: yeni hedef (yeni subreddit, yeni rakip, yeni GSC property) kod değişikliği değil, konfigürasyon satırı eklemektir — bu, iştiraklerin kendi Pazar/Rakip Analistlerinin aynı altyapıyı yeni bir dikey açıldığında sıfırdan kurmadan devralmasını sağlar.

## Workflow'ları

workflows.yaml'daki GERÇEK key'ler (denetim düzeltmesi — 5 hat TEK parametrik tanımda):
| Workflow key | params.hat | Ajan | Kadans | v3 kapsamı |
|---|---|---|---|---|
| `kesif-gunluk-tarama` | `fikir-radari` | 21-fikir-radarcısı | günlük 07:00 TR | değişmedi — tamamen yeni fikir |
| `kesif-gunluk-tarama` | `ihtiyac-madenciligi` | 22-ihtiyaç-madencisi | günlük 07:30 TR | daraldı — dikey-dışı/adjacent kategori |
| `kesif-gunluk-tarama` | `icerik-firsati` | 23-içerik-fırsatçısı | günlük 08:00 TR | daraldı — cross-vertical/yeni-tema |
| `kesif-gunluk-tarama` | `rakip-radari` | 24-rakip-radarcısı | haftalık, Pazartesi 06:00 TR | daraldı — yeni-giren/adjacent rakip |
| `kesif-gunluk-tarama` | `seo-firsati` | 25-SEO-fırsatçısı | haftalık, Pazartesi 06:30 TR | daraldı — cross-property/yeni-küme |
| `firsat-raporu-haftalik` | — | 26-sentezci | haftalık, Pazar 20:00 TR (5 hattın verisini toplar) | YALNIZ dikey-dışı fırsatlar; iştirak pazar/rakip bölümleri GM raporlarında |

## Feedback döngüsü

DNA §3.4 standardı aynen uygulanır: her tarayıcının kendi **Kaçan-sinyal tanımı** (runbook'larda) haftalık retroda sayılır — **v3'te kaçan-sinyal artık iki türe ayrılır:** (a) Keşif'in kendi kapsamında bir dikey-dışı fırsatın kaçırılması (kendi retrosunda sayılır), (b) bir sinyalin YANLIŞ olarak "dikey-dışı" sanılıp Keşif'e düşmesi ama aslında mevcut bir iştirakin kapsamında olması (kapsam-sızıntısı — bu durumda sinyal ilgili iştirake yönlendirilmeli, Keşif kendi raporuna yazmamalı). Diğer retro metrikleri: yanlış-sınıflandırma oranı, gürültü oranı (kurucunun 👎/"gereksizdi" işaretlediği sinyal payı), API maliyeti (hedef $0 — yalnız ücretsiz katmanlar). Karar-tablosu eşikleri (puan eşiği, dedup penceresi, "dikey-içi mi dikey-dışı mı" ayrım kuralı) haftalık retro bulgusuna göre revizyon ÖNERİSİ olarak kurucuya gider; küçük model kendi eşiğini değiştiremez.

## Sınırlar

- Resmî API/feed dışı hiçbir scraping yapılmaz; robots/ToS ihlali YASAK.
- Reddit'te ASLA post/yorum/DM atılmaz — yalnız dinleme.
- Hiçbir tarayıcı ajanı R1'i aşan yetkiye sahip değil: dış-yazma yok, tek çıktı = iç kuyruk kaydı + (haftalık) Köprü'ye bildirim-önerisi.
- **Mevcut 4 aktif dikeyin İÇİNDEKİ bilinen rakip/pazar analizini kendi raporuna yazmaz** — bu veri iştirakin kendi Rakip/Pazar Analisti'ne aittir; Keşif yalnız "bu dikeyde YENİ bir şey mi var" sorusuna bakar, bulursa iştirake devreder.
- Kişisel veri (kullanıcı adı, e-posta, telefon) dijeste taşınmaz — yalnız tema/özet seviyesinde.
- Kişisel yatırım/finansal araç fikirleri portföy ürün kapsamı dışıdır; bu tür sinyaller rapora taşınmaz.
- Kanıt-linksiz hiçbir madde Fırsat Raporu'na girmez (DNA kural 1).
- Sentezci dahil hiçbir ajan "yap" kararı vermez — yalnız kanıtlı öneri; icra kurucunundur.

## Uzman eşiği

| Durum | Danışman |
|---|---|
| Tarayıcı mimarisi/yeni kaynak kurulumu (altyapı) | `data-collection-architect` |
| Yeni-giren/adjacent rakip hareketi yorumu | `competitive-intelligence-analyst` |
| Cross-property SEO/içerik fırsatı stratejisi | `seo-strategist` |
| Yeni fikir sinyalinin roadmap'e oturması (B5 Lab öncesi ön-değerlendirme) | `roadmap-strategist` |
| Haftalık rapor çok-alanlı/karmaşık sentez gerektiriyorsa | `fable-stratejist` |
