---
id: b2-kesif
kat: B
durum: aktif
faz: F2
ajanlar: [21-fikir-radarcisi, 22-ihtiyac-madencisi, 23-icerik-firsatcisi, 24-rakip-radarcisi, 25-seo-firsatcisi, 26-sentezci]
---
# YULA Keşif (Scout)

## Kimlik ve amaç

Portföyün tamamına (A-katı ürün şirketlerinin hepsine, venture-agnostik) hizmet veren tarama/istihbarat şirketi. Günlük olarak dış dünyayı beş açıdan tarar — ürün/proje fikri, kullanıcı ihtiyacı, içerik fırsatı, rakip hareketi, SEO fırsatı — ve bulguları önce günlük kısa sinyale, sonra haftalık kanıt-linkli **Fırsat Raporu**'na dönüştürür. Kendisi hiçbir karar vermez, hiçbir şey yayınlamaz, hiçbir hesaba yazmaz: yalnız bulur, sınıflandırır, kanıtıyla birlikte önerir. F1'de Gözcü canlıya çıktıktan ve bir hafta stabil çalıştıktan sonra devreye girer (§5 faz planı).

## Varlıklar ve bağlar

Tüm kaynaklar resmî API/feed önceliklidir (Anayasa İlke 8 — Reddit yalnız dinleme, scraping/ToS ihlali yok):
- **Hacker News:** HN Algolia Search API (`hn.algolia.com/api/v1`, key gerektirmez, herkese açık).
- **Product Hunt:** resmî GraphQL API — `PH_API_TOKEN` zaten mevcut (`~/.secrets/yula/`).
- **GitHub Trending:** resmî bir "trending" endpoint'i YOK (dürüst not) — GitHub Search API (`created:>tarih sort:stars`) resmî alternatif olarak kullanılır; topluluk trending-cache'i yalnız çapraz-doğrulama için.
- **Kendi store yorumlarımız:** `app-publish` MCP (zaten bağlı) — `apple_list_reviews` / `google_list_reviews`, tüm A-katı uygulamalar için.
- **Rakip store yorumları/listing'leri:** aynı resmî store sayfaları, herkese açık/oturumsuz okuma.
- **Reddit:** PRAW (Python Reddit API Wrapper), **read-only**, 4 hesap credential'ı `~/.secrets/yula/` altında — yalnız dinleme, asla post/yorum/DM (Anayasa İlke 8, 04-DISCLOSURE-BIP §4).
- **Google Trends:** resmî ücretsiz API YOK (dürüst not) — herkese açık, oturumsuz `trends.google.com` verisine topluluk kütüphanesiyle erişilir.
- **GSC (Google Search Console) API:** tam ücretsiz, 40K QPM — Ahrefs API alınmadı (maliyet, §3.2 gerekçesi).

## Hizmet kapsamı

Beş günlük/haftalık tarama hattı (§3.5 taslak tablosu) + bir haftalık sentez hattı; çıktı iki katmanlı: **günlük dijest** (≤3 sinyal/tarayıcı, Köprü Kanalı'na değil, iç kuyruğa) + **haftalık Fırsat Raporu** (Köprü Kanalı'na, kanıt-linkli). Her tarayıcı **descriptor-tabanlı** çalışır: yeni hedef (yeni subreddit, yeni rakip, yeni GSC property) kod değişikliği değil, konfigürasyon satırı eklemektir.

## Workflow'ları

workflows.yaml'daki GERÇEK key'ler (denetim düzeltmesi — 5 hat TEK parametrik tanımda):
| Workflow key | params.hat | Ajan | Kadans |
|---|---|---|---|
| `kesif-gunluk-tarama` | `fikir-radari` | 21-fikir-radarcısı | günlük 07:00 TR |
| `kesif-gunluk-tarama` | `ihtiyac-madenciligi` | 22-ihtiyaç-madencisi | günlük 07:30 TR |
| `kesif-gunluk-tarama` | `icerik-firsati` | 23-içerik-fırsatçısı | günlük 08:00 TR |
| `kesif-gunluk-tarama` | `rakip-radari` | 24-rakip-radarcısı | haftalık, Pazartesi 06:00 TR |
| `kesif-gunluk-tarama` | `seo-firsati` | 25-SEO-fırsatçısı | haftalık, Pazartesi 06:30 TR |
| `firsat-raporu-haftalik` | — | 26-sentezci | haftalık, Pazar 20:00 TR (5 hattın verisini toplar) |

## Feedback döngüsü

DNA §3.4 standardı aynen uygulanır: her tarayıcının kendi **Kaçan-sinyal tanımı** (runbook'larda) haftalık retroda sayılır. Retro metrikleri: yanlış-sınıflandırma oranı, kaçan-sinyal sayısı, gürültü oranı (kurucunun 👎/"gereksizdi" işaretlediği sinyal payı), API maliyeti (hedef $0 — yalnız ücretsiz katmanlar). Karar-tablosu eşikleri (puan eşiği, dedup penceresi, pozisyon bandı) haftalık retro bulgusuna göre revizyon ÖNERİSİ olarak kurucuya gider; küçük model kendi eşiğini değiştiremez.

## Sınırlar

- Resmî API/feed dışı hiçbir scraping yapılmaz; robots/ToS ihlali YASAK.
- Reddit'te ASLA post/yorum/DM atılmaz — yalnız dinleme.
- Hiçbir tarayıcı ajanı R1'i aşan yetkiye sahip değil: dış-yazma yok, tek çıktı = iç kuyruk kaydı + (haftalık) Köprü'ye bildirim-önerisi.
- Kişisel veri (kullanıcı adı, e-posta, telefon) dijeste taşınmaz — yalnız tema/özet seviyesinde.
- Kişisel yatırım/finansal araç fikirleri portföy ürün kapsamı dışıdır; bu tür sinyaller rapora taşınmaz.
- Kanıt-linksiz hiçbir madde Fırsat Raporu'na girmez (DNA kural 1).
- Sentezci dahil hiçbir ajan "yap" kararı vermez — yalnız kanıtlı öneri; icra kurucunundur.

## Uzman eşiği

| Durum | Danışman |
|---|---|
| Tarayıcı mimarisi/yeni kaynak kurulumu | `data-collection-architect` |
| Rakip hareketi yorumu/derinleştirme | `competitive-intelligence-analyst` |
| SEO/içerik fırsatı stratejisi | `seo-strategist` |
| Fikir sinyalinin roadmap'e oturması | `roadmap-strategist` |
| Haftalık rapor çok-alanlı/karmaşık sentez gerektiriyorsa | `fable-stratejist` |
