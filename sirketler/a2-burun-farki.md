---
id: a2-burun-farki
kat: A
durum: aktif
faz: F1
ajanlar: [12-burun-farki-masasi]
---
# A2 — Burun Farkı

## Kimlik ve amaç
Burun Farkı, Türkiye-only KASITLI bir TJK (at yarışı) **analiz** ürünüdür — bahis değil, dürüstlük çizgisi bağlayıcı: hiçbir çıktı bahis-tavsiyesi imasına kayamaz. Şirket kaydı bu ürünün sinyal→bulgu→brief hattını taşır: masa kod YAZMAZ, tahmin-pipeline sağlığını, store süreçlerini ve dürüstlük çizgisini izler; genişletme (TR-dışı) önerisi ÜRETMEZ — bu kısıt kurucu kararı ve kalıcıdır.

Ölçek kuralı (taslak §1): "her ürün ayrı şirket" ilkesi gereği BF'nin kendine özgü kısıtları (TR-only, dürüstlük çizgisi) yalnız BU şirketin tanımında yaşar — hizmet şirketleri (Gözcü, Hukuk) venture-agnostik kalır. Masa sözleşmesi: `governance/sozlesmeler/venture-desk-burun-farki.md` (allowed/forbidden tools + cost_ceiling + model_chain — burada TEKRAR edilmez, DNA kural 8).

## Varlıklar ve bağlar
- Repolar: `kocakkmustafa/burunfark-web` (web) · `kocakkmustafa/burunfark-mobile` (mobile) — dizinler `ventures/burun-farki/{web,mobile}`; trunk `main`.
- **Deploy tuzağı (kritik):** Vercel prod dalı = `develop`, `main` DEĞİL — push her zaman `main:develop`.
- Yüzeyler: web canlı (`burunfark.com`, TR-only) · iOS ret-döngüsü sürüyor (K-1 deseni: age-rating/gambling-simulated yanlış sınıflandırması, çok turlu resubmit) · Android in-review (onay sonrası "Yayınla" kurucuda, B-013).
- Supabase `hgllgyuckwjeyykidrox` (at-yarisi projesi, members: [burun-farki]).
- Paylaşımlı hesaplar: Apple Developer `T5HZGYBWK8` — risk: "BF reddi hesap itibarına emsal olabilir" · Google Play — hesap-geneli deadline **2026-08-31** (⏰G2: targetSdk) · Lightsail (BF retrain cron + heartbeat; braavolabs ile AYNI/AYRI instance DOĞRULANMADI) · GitHub `kocakkmustafa`.
- Kanonik belgeler: `ventures/burun-farki/mobile/BITIRME-PROGRAMI.md`, `ventures/burun-farki/mobile/DEFTER.md`, `ventures/burun-farki/VENTURE.md`.

## İzleme hedefleri
| Sinyal/durum | Yöntem/kaynak | Faz | Aksiyon/eskalasyon |
|---|---|---|---|
| ASC durum/ret sinyali | ASC Webhooks API + Gmail | F1 | RET = hard sinyal → doğrudan kurucu (K-1 deseni bilinir) |
| Google Play review/durum | Play Developer API poll | F1 | S1 devriye → masa |
| Vercel deploy sonucu (yanlış-dal push riski) | Gmail (Vercel free planda webhook yok) | F1 | dal kontrolü: hedef `develop` mi doğrula, değilse anlık uyarı |
| ⏰G2 targetSdk deadline (2026-08-31) | L0 betik sayaç | F1 | ≤30/14/7 gün artan SEV, günlük brief'te ZORUNLU satır |
| Lightsail retrain cron + heartbeat | Uptime Kuma + cron log | F1 | Kesinti-nöbetçisi (#34) ile ilişkilendirme |
| Supabase `hgllgyuckwjeyykidrox` durumu | Management API poll + advisor sweep | F1-F2 | masa DEFTER bulgu önerisi |
| Dürüstlük çizgisi (pazarlama/çıktı metni ↔ "analiz, bahis değil") | Hukuk (B10) uyum-doğrulayıcısı ile ortak tarama | F2 | ihlal şüphesi → Fable-seans |
| Apple hesap itibarı sinyali (BF ret geçmişi diğer ürünlere emsal) | connections.yaml `impact_rules` — "Apple hesap itibarı" | F2 | LifeOS+Braavolabs iOS submission riskine çapraz-bildirim |
| Domain expiry (`burunfark.com`) | RDAP/whois betiği (ücretsiz, LLM'siz) | F1 | yenileme yaklaşınca artan SEV |
| **tabloda olmayan HER durum** | — | — | **ESKALE ET** (asla tahmin etme) |

## Workflow'ları
`sentinel-s1-devriye` (venture=burun-farki filtresi) · `store-mail-triyaj` (RET hard-sinyal) · `gunluk-brief` (⏰G2 satırı ZORUNLU eşik yaklaşınca) · `haftalik-scorecard` · `defter-sagligi` (BF DEFTER bayat-satır taraması).

**Model zinciri (MODEL-ROUTING sınıf referansı):** sınıf-1 (mail/review sınıflandırma) triyajın omurgası; model-doğruluk iddiaları ASLA masa tarafından şişirilmez/yorumlanmaz — yalnız gerçek metrikten yazılır (dürüstlük kuralı, sözleşme `venture-desk-burun-farki` model_chain). Dürüstlük-çizgisi şüphesi sınıf-6 (Haiku, free-birincil OLMAZ) rubrikle ön-taranır, ihlal olasılığı Fable-seans'a (L4) gider.

## Feedback döngüsü
Haftalık masa retrosu: yanlış-sınıflandırma oranı · **kaçan-sinyal tanımı = bir dürüstlük-çizgisi ihlalinin (bahis imalı metin), ⏰G2 deadline'ının, ya da yanlış-dal push'unun (Vercel prod=develop tuzağı) bildirilmeden geçmesi** · eskalasyon isabeti · bildirim gürültüsü · maliyet ($0.50/run tavanı — sözleşme `venture-desk-burun-farki`).

## Sınırlar
Masa ASLA: kod değişikliği yapmaz, commit/push atmaz, Supabase mutasyonu çalıştırmaz, store işlemi (R4) gerçekleştirmez, tahmin-pipeline çıktısına müdahale etmez, Türkiye-dışı genişleme önerisi üretmez (KASITLI sınır), model-doğruluk metriklerini gerçek ölçümden başka bir kaynakla süslemez/şişirmez.

## Uzman eşiği
Motor küçük modelle çalışır; danışman çağrısı yalnız kurucu-oturumunda — eskalasyon çıktısına `onerilen_danisman` yazılır, Köprü Kanalı'na düşer.
| Durum | Önerilen danışman |
|---|---|
| Store ret / K-1 deseni | `store-policy-officer` |
| Dürüstlük çizgisi / pazarlama dili şüphesi | `marketing-aso-specialist` |
| Model-doğruluk iddiası şişirme şüphesi | `data-ml-engineer` |
| Deploy dal-tuzağı riski | `release-devops-engineer` |
| Çok-alanlı/belirsiz triyaj | `fable-stratejist` |
