---
id: a2-burun-farki
kat: A
durum: aktif
faz: F1
ajanlar: [a2-burun-farki-gm, a2-burun-farki-musteri-sesi, a2-burun-farki-izleme-dogruluk, a2-burun-farki-rakip-analisti, a2-burun-farki-pazar-analisti, a2-burun-farki-pazarlama-analisti, a2-burun-farki-guvenlik, a2-burun-farki-veri-gizliligi, a2-burun-farki-hukuk-uyum, a2-burun-farki-sosyal-medya, a2-burun-farki-icerik, a2-burun-farki-kod-test]
---
# A2 — Burun Farkı

## Kimlik ve amaç

Burun Farkı, Türkiye-only KASITLI bir TJK (Türkiye Jokey Kulübü resmî verisi) at yarışı **analiz** ürünüdür — bahis değil. Dürüstlük çizgisi ("analiz, bahis değil") bu şirketin var oluş sebebidir ve bağlayıcıdır: hiçbir çıktı — pazarlama metni, sosyal gönderi, içerik taslağı, kullanıcıya yanıt — bahis-tavsiyesi imasına kayamaz; bu 12 ajanın HEPSİNDE tekrar eden ortak sınırdır. TR-dışı genişleme önerisi de aynı şekilde KASITLI ve kalıcı bir sınırdır — hiçbir ajan (Pazar/Rakip Analisti dahil) bunu öneremez, karar kurucuya aittir.

**v3 geçişi (EK-C, KK-2026-07-28):** v2'de bu şirket tek bir masa ajanıyla (12-burun-farki-masasi) temsil ediliyordu; uzmanlık B-katındaki ortak hizmet şirketlerinde topluydu. v3'te uzmanlık ŞİRKETİN İÇİNE indi: BF artık standart 12 kişilik iştirak kadrosuyla kendi verisini kendi işleyen, kendi ŞİRKET RAPORU'nu üreten bir birim. Eski masa runbook'u (`ajanlar/masalar/12-burun-farki-masasi.md`) tarihsel kayıt olarak durur, kanonik kadro budur. B-katı (Gözcü/Kalkan/Hukuk) artık ANALİZ/YORUM üretmez — ortak boruyu (sensör hattı, tarama aracı, hukuk çerçevesi) işletir; BF'nin kendi Güvenlik/Veri Gizliliği/Hukuk-Uyum sorumluları bu boruyu KENDİ verisine uygular.

Ölçek kuralı (taslak §1): "her ürün ayrı şirket" ilkesi gereği BF'nin kendine özgü kısıtları (TR-only, dürüstlük çizgisi) yalnız BU şirketin tanımında yaşar. Masa/sözleşme mirası: `governance/sozlesmeler/venture-burun-farki.md`.

## Varlıklar ve bağlar

- Repolar: `kocakkmustafa/burunfark-web` (web) · `kocakkmustafa/burunfark-mobile` (mobile) — dizinler `ventures/burun-farki/{web,mobile}`; trunk `main`.
- **Deploy tuzağı (kritik, tekrar eden gotcha):** Vercel prod dalı = `develop`, `main` DEĞİL — push her zaman `main:develop`.
- Yüzeyler: web canlı (`burunfark.com`, TR-only) · **iOS 5. resubmit arkı** (K-1 deseni: Age Rating `gamblingSimulated`→`NONE` yolu, Xcode Cloud kırık/Apple-şüphesi → headless yerel `.ipa`+`altool` ile yükleme; Waiting for Review) · **Android production CANLI** (build 9, %100 rollout, TR) — 2026-07-29'da hesap-geneli zorunluluk (targetSdk 36 + Billing Library 8.0.0) BF tarafında ship edildi.
- Supabase `hgllgyuckwjeyykidrox` (at-yarisi projesi, members: [burun-farki], LifeOS org'undan tamamen izole).
- Lightsail: haftalık retrain cron'u (`retrain_weekly.py`, Pzt 00:30 UTC, 5-kontrollü kapı G1-G5, otomatik yayın YOK) + heartbeat (05:00/10:30 UTC); Braavolabs backend'iyle AYNI/AYRI instance DOĞRULANMADI.
- 2026-07-25 kapanan kök-neden: TJK ingest normalizer 2 yıldır var-olmayan alan adı (`KULVAR`/`HANDIKAP_PUANI`) okuyordu, gerçek adlar `START`/`HANDIKAP` — 147.737 satırın tamamında iki kolon sessizce boş kaldı, optional-chaining hata fırlatmadığı için ingest hep "başarılı" raporladı (sessiz-veri-kaybı deseni — İzleme & Doğruluk Sorumlusu'nun kalıcı nöbet konusu). Aynı gün RLS privilege-escalation P0'ı (herhangi bir girişli kullanıcı `plan_tier`'ı kendi başına `pro` yapabiliyordu) da kapatıldı.
- Model doğruluk gerçeği (dürüstlük kuralının somut hali): canlı walk-forward ölçüm Top-1 ≈%30 / Top-3 ≈%60-61 (600+ yarış, sürekli güncellenir); site genelinde bir süre "~%69 Top-3" eğitim-backtest rakamı niteliksiz kullanılmıştı (B-012) — artık "eğitim backtest'i" etiketiyle ayrıştırıldı. **Hiçbir ajan bu iki rakamı birbirinin yerine geçirmez.**
- Paylaşımlı hesaplar: Apple Developer `T5HZGYBWK8` (risk: "BF reddi hesap itibarına emsal olabilir") · Google Play tek-hesap (hesap-geneli deadline **2026-08-31** — BF kendi payını kapattı ama portföy-geneli risk sürüyor) · Lightsail · GitHub `kocakkmustafa` (billing tek-nokta-arızası).
- Kanonik belgeler: `ventures/burun-farki/mobile/BITIRME-PROGRAMI.md`, `ventures/burun-farki/mobile/DEFTER.md`, `ventures/burun-farki/VENTURE.md` — kadro buraya bulgu ÖNERİSİ bırakır, kopyalamaz (DNA kural 8).

## Kadro — 12 iştirak ajanı (EK-C C2)

| # | Rol | Ajan ID | Görev (BF'nin kendi verisi üzerinde) | Model (bugün) | Faz |
|---|---|---|---|---|---|
| 1 | Şirket Müdürü (GM) | `a2-burun-farki-gm` | 11 ajanı koordine eder, haftalık ŞİRKET RAPORU'nu derler, DEFTER'in sahibidir | sınıf-5 derleme | F1 |
| 2 | Müşteri-Sesi Analisti | `a2-burun-farki-musteri-sesi` | Store yorumları + destek mailleri: dürüstlük-çizgisi algısı (kullanıcı bizi "bahis" sanıyor mu), form-veri şikayetleri | sınıf-1 + embedding (PII-lokal) | F1 |
| 3 | İzleme & Doğruluk Sorumlusu | `a2-burun-farki-izleme-dogruluk` | ⏰targetSdk/Billing sayacı, retrain cron/heartbeat, canlı model-doğruluk ↔ iddia mutabakatı | L0+sınıf-1 | F1 |
| 4 | Rakip Analisti | `a2-burun-farki-rakip-analisti` | TR at yarışı analiz/tahmin rakiplerinin listing/özellik/fiyat hareketleri | sınıf-1/5 | F2 |
| 5 | Pazar Analisti | `a2-burun-farki-pazar-analisti` | TR at yarışı arama/trend talebi (GSC+Trends), mevsimsel/bölgesel fırsat | sınıf-1/5 + GSC/Trends | F2 |
| 6 | Pazarlama Analisti | `a2-burun-farki-pazarlama-analisti` | Funnel/ASO metrikleri, dönüşüm; kampanya YOKSA dürüstçe "kampanya-yok" kaydı | L0+sınıf-5 | F2 |
| 7 | Güvenlik Sorumlusu | `a2-burun-farki-guvenlik` | Kalkan (B6) araçlarını `burunfark-web`+`burunfark-mobile`'a uygular, bulguyu DEFTER'e taşır | betik+sınıf-1 | F2 |
| 8 | Veri Gizliliği Sorumlusu | `a2-burun-farki-veri-gizliligi` | KVKK envanteri (kamu-yarış-verisi ↔ kişisel-veri ayrımı), veri-sahibi talep SLA'sı | betik+sınıf-1 | F2 |
| 9 | Hukuk-Uyum Sorumlusu | `a2-burun-farki-hukuk-uyum` | Hukuk (B10) çerçevesini BF'ye uygular: dürüstlük-çizgisi taraması, ToS/beyan tutarlılığı | sınıf-1/5 | F3 |
| 10 | Sosyal-Medya Takipçisi | `a2-burun-farki-sosyal-medya` | BF hesaplarının mention/etkileşim/format-performansı — İçerik'in girdisi | sınıf-1 | F3 |
| 11 | İçerik Üreticisi | `a2-burun-farki-icerik` | Marka-bağlamlı (TR + dürüstlük çizgisi) içerik taslakları, insan-kapılı yayın | sınıf-7 | F3 |
| 12 | Kod & Test Bekçisi | `a2-burun-farki-kod-test` | build/test/coverage sağlığı (deno+flutter), MONITOR-ONLY, kod YAZMAZ | betik+sınıf-8 | F2 (izleme) |

Runbook'lar: `ajanlar/istirakler/a2-burun-farki/{gm,musteri-sesi,izleme-dogruluk,rakip-analisti,pazar-analisti,pazarlama-analisti,guvenlik,veri-gizliligi,hukuk-uyum,sosyal-medya,icerik,kod-test}.md`.

## ŞİRKET RAPORU (haftalık — C3 formatı)

GM her hafta (Pazartesi) 11 ajanının kanıt-linkli çıktısını tek dosyada derler: **sağlık/doğruluk** (İzleme&Doğruluk) + **müşteri sesi** (Müşteri-Sesi) + **rakip/pazar** (Rakip+Pazar Analisti) + **pazarlama** (Pazarlama Analisti) + **güvenlik/gizlilik/hukuk** (Güvenlik+Veri Gizliliği+Hukuk-Uyum) + **içerik performansı** (Sosyal-Medya+İçerik) — hepsi kanıt-linkli (DEFTER satırı/API rakamı/screenshot referansı, tahmin yok). Rapor **doğrudan kurucuya** gider (Köprü Kanalı + dosya); HOLDİNG RAPORU'nun (yönetim katmanının haftalık sentezi, ayrı üretilir) üzerine YAZILMAZ — iki rapor denetlenebilirlik için ayrı yaşar (C3-2). Kod & Test Bekçisi'nin haftalık veri üretmediği durumlar raporda "veri yok" olarak açıkça işaretlenir, sessizce atlanmaz.

## GM yetkileri (C7)

**Rapor bekletme yasağı (C7-2, bağlayıcı):** *"Hiçbir severity sinyali rapor bekletilerek geciktirilemez."* SEV0-1 + BF'ye özgü acil eşikler (aşağıda) her zaman üreten ajandan DOĞRUDAN Köprü Kanalı'na düşer — GM'i beklemez, GM eş-zamanlı bilgilendirilir. GM ayrıca ihtiyaç gördüğünde takvim-dışı **FLAŞ NOT** (ara-rapor) üretebilir; günlük tam-döküm digest her şeyi taşımaya devam eder.

**Talep-üzerine tetikleme (C7-3, sınırlı yetki):** GM, kendi 11 ajanının workflow'unu cron beklemeden tetikleyebilir (ör. yeni store ret sinyali → Hukuk-Uyum'u hemen koştur; canlı doğruluk rakamı sıçradı → İzleme&Doğruluk'u hemen koştur). Sınırlar: **(a)** yalnız BF'nin KENDİ ajanları — LifeOS/Braavolabs/yulalab.com ajanlarını tetikleyemez, şirketler-arası tetik CEO üzerinden; **(b)** tetiklenen iş yine R0-R1 tavanında kalır, R2+ çıktı onay kuyruğuna düşer; **(c)** her tetik audit'e yazılır ve BF'nin günlük tetik/harcama bütçesi (Cost Guard) içinde kalır — bütçe aşımı kendisi bir sinyaldir; **(d)** kurucu her ajanı her an kendisi de tetikleyebilir (GM tekeli yoktur).

## Acil eşikleri (şirkete özel — rapor beklemez, C7-2)

| Eşik/desen | Neden acil |
|---|---|
| Herhangi bir yüzeyde (pazarlama/içerik/sosyal/kullanıcı-yanıtı) bahis-imalı dil ("kazanma garantisi", "kesin kazandırır", "winning tip") | Dürüstlük çizgisi ihlali — şirketin var-oluş sınırı, ASLA düşürülmez |
| iOS store ret bildirimi (herhangi bir tur — K-1 deseni tekrar etsin etmesin) | Apple hesap itibarı paylaşımlı (T5HZGYBWK8), gecikme = ret döngüsü uzar |
| Android/Play politika ihlali veya kaldırma bildirimi | Hesap-geneli risk, portföyün 8 ürünü aynı hesaba bağlı |
| ⏰Play hesap-geneli deadline (2026-08-31) ≤7 gün VEYA BF'nin kendi targetSdk/Billing durumunda regresyon | Submission tamamen engellenebilir |
| Vercel'e `main`'e push denemesi (prod dalı `develop` olmalı) | Sessiz deploy hatası riski, tekrar eden gotcha |
| Lightsail retrain cron/heartbeat beklenen pencerede koşmadı | Model dondurulmuş kalabilir, fark edilmeden |
| Canlı model-doğruluk (Top-1/Top-3) ile kamuya-dönük iddia arasında düzeltilmemiş fark (B-012 emsali) | Metrik-şişirme = dürüstlük kuralı ihlali |
| P0-sınıfı güvenlik açığı (RLS/privilege-escalation türü, B-014 emsali) veya sızmış secret | Gelir kaçağı / veri riski, geri-dönüşü zor |
| Veri-sahibi talebi SLA eşiğine (30 gün) 7 günden az kaldı | Yasal yükümlülük penceresi |
| **Tabloda olmayan HER SEV0/SEV1 desen** | **ESKALE ET** — asla "rapora bırak" deme |

## Workflow'ları

Mevcut (workflows.yaml v2): `sentinel-s1-devriye` (venture=burun-farki filtresi) · `store-mail-triyaj` (RET hard-sinyal) · `gunluk-brief` (⏰deadline + dürüstlük satırı ZORUNLU) · `haftalik-scorecard` · `defter-sagligi` · `sirket-retrosu` (params.sirket=a2-burun-farki). C6 planında eklenecek (henüz motora yüklenmedi): parametrik `sirket-raporu` (haftalık, GM derler, C3 formatı) — bu governance tanımı o üretimin temelidir.

## Feedback döngüsü

Haftalık şirket retrosu (DNA kural 3.4): yanlış-sınıflandırma oranı · **kaçan-sinyal tanımı = bir dürüstlük-çizgisi ihlalinin (bahis imalı metin — hangi ajandan çıkarsa çıksın), ⏰deadline'ın, sessiz-veri-kaybı deseninin (B-019 türü) ya da yanlış-dal push'unun bildirilmeden/rapor bekletilerek geçmesi** · eskalasyon isabeti · bildirim gürültüsü (kurucunun "gereksizdi" işaretlediği) · maliyet + GM'in günlük tetik bütçesi kullanımı. Runbook revizyon önerisi kurucu onayı almadan yürürlüğe girmez (self-grant yasağı).

## Sınırlar

Kadronun HİÇBİRİ: kod değişikliği yapmaz/commit-push atmaz (Kod & Test dahil — MONITOR-ONLY), Supabase mutasyonu çalıştırmaz, store işlemi (R4) gerçekleştirmez, tahmin-pipeline çıktısına müdahale etmez, TR-dışı genişleme önerisi üretmez (KASITLI ve kalıcı), model-doğruluk metriklerini gerçek ölçümden başka bir kaynakla süslemez/şişirmez, severity düşüremez, kendi karar tablosunu self-grant ile değiştiremez (yalnız revizyon ÖNERİR). GM dahil hiçbir rol başka şirketin ajanını tetikleyemez.

## Uzman eşiği

Motor küçük modelle çalışır; danışman çağrısı yalnız kurucu-oturumunda — eskalasyon çıktısına `onerilen_danisman` yazılır, Köprü Kanalı'na düşer.
| Durum | Önerilen danışman |
|---|---|
| Store ret / K-1 deseni | `store-policy-officer` |
| Dürüstlük çizgisi / pazarlama-içerik dili şüphesi | `marketing-aso-specialist` + `legal-contracts-advisor` |
| Model-doğruluk iddiası şişirme şüphesi / sessiz-veri-kaybı deseni | `data-ml-engineer` |
| Deploy dal-tuzağı / CI kırmızı | `release-devops-engineer`, `qa-test-engineer` |
| Güvenlik bulgusu | `security-compliance-auditor` |
| KVKK/veri-sahibi talebi | `privacy-data-guardian` |
| Çok-alanlı/belirsiz triyaj | `fable-stratejist` |
