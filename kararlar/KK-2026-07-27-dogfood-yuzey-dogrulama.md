# KK-2026-07-27 — Holding = Braavolabs Dogfood: Tüm Ürün Yüzeyleri Doğrulanacak

**Tür:** Karar Kaydı (kurucu direktifi) · **Durum:** KABUL

## Kurucu direktifi (2026-07-27)

"Asıl amacımız Braavolabs desktop app'inin, mobil app'inin, CLI'ın kontrolünü yapmak; gerçekten istediğimiz gibi çalışıp haberleşebiliyorlar mı, AI modelleri arasında geçiş yapabiliyor mu, holding çalışırken ilerleme/işlemler telefondan takip edilebiliyor mu — bütün özelliklerini kontrol edip çalıştığından emin olmak için holdingi KENDİ ürünümüzde kuruyoruz."

## Kararın anlamı (mimari netleşme)

1. **Holding yürütmesi ürün primitive'lerinden GEÇER.** `modules/holding` katmanı yönetişim kabuğudur (charter/K0 · policy · Cost Guard · append-only audit · Nöbetçi S0 · Telegram yedek onay kanalı); **iş yürütme, ürünün kendi `companies/pipelines/runs/approvals` makinesine** verilir ki desktop/mobil/CLI yüzeyleri gerçek trafikle yansın.
2. **YULA_INTERNAL tenant'ı:** holding, üründe gerçek bir tenant olarak yaşar (Anayasa §3 ToS kuralındaki izinli istisna — abonelik/BYOK yalnız bu tenant'ta serbest).
3. **`pipeline` adım türü:** holding runner'a yeni step kind — bir holding adımı, YULA tenant'ında ürün pipeline'ı tetikler ve sonucunu bekler. Köprü budur: yönetişim kabuğu ürün yürütmesini sarar (R-matrisi + charter + audit korunur).
4. **Her yüzey KANITLA doğrulanır** — test matrisi: `holding/plans/BRAAVOLABS-YUZEY-DOGRULAMA-TURU.md`. Bulunan her kusur ürünün kendi DEFTER'ine bulgu olarak düşer (dogfood = sürekli QA) ve build-in-public malzemesidir.

## Doğrulama hedefleri (kurucu listesi → test hedefi)

| Kurucu sorusu | Nasıl kanıtlanacak |
|---|---|
| Desktop app kontrolü | Holding run'ları desktop v3 shell'de görünür + yönetilebilir mi (oturum/ajan görünümleri, governed_command) |
| Mobil app kontrolü + telefondan takip | Braavo mobil (1.0.3) companion/relay kanalından holding run ilerlemesi CANLI izlenebilir + onay verilebilir mi |
| CLI | `braavo` ile holding tenant'ının run listesi/log/tetik çalışıyor mu |
| AI modelleri arası geçiş | Cascade router'da zorlanmış failover: birincil sağlayıcı kapatılınca run kesintisiz L1(Ollama)↔L2(Gemini/Groq/NIM) geçiyor mu; her adımda kullanılan sağlayıcı/model `run_steps`'te kayıtlı mı |
| Yüzeyler arası haberleşme | Mobil→backend→desktop olay akışı (relay) uçtan uca; SSE/stream kesinti toleransı |

## Değişmeyenler

R4/R5 daima kurucu · Cost Guard tavanları · charter/K0 zorunluluğu · append-only audit · `HOLDING_ENABLED` bayrağı ve K2 ön şartı · Iron Bank kapsam dışı.

## Geri alma yolu

`pipeline` adım türü kapatılır (STEP_KINDS'ten çıkarılır), YULA tenant'ı pasifleştirilir; yönetişim kabuğu bağımsız çalışmaya devam eder — iki katman gevşek bağlı tasarlandığı için tek yönlü sökülebilir.
