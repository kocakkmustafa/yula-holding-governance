---
id: b4-atolye
kat: B
durum: uykuda
faz: uyanma-kosulu
ajanlar: [30-bakim-icracisi, 31-deploy-yardimcisi]
---
# B4 — YULA Atölye (Works)

## Kimlik ve amaç
Kod yazma/bakım/deploy İCRA şirketi. Kurucu kararı (2026-07-27): gelir API maliyetini karşılayana dek kapalı. Bugün "Atölye" fiilen kurucu-Claude oturumlarıdır — Gözcü bir sorun bulur, Köprü Kanalı'nda oturum-Claude aksiyon önerir, kurucu "yap" derse iş kurucu oturumunda yürür.

## Varlıklar ve bağlar
Potansiyel hedef repolar (registry `ventures.yaml`): lifeos (app+site), burunfark-web/mobile, braavolabs 4 repo (platform/desktop/cli/mobile), yulalab-web/links, Motion 5 app + motion-core. Bilinen deploy tuzakları (`connections.yaml`): Braavolabs platform `main`=Lightsail OTOMATİK · BF web Vercel prod=`develop` · yulalab site prod=`main` · yulalab links prod=`develop`.

## Uykuda görevleri
Bu şirketin toggle'ı kapalı; hiçbir workflow otonom koşmaz. Yalnız kayıt: Gözcü bulgusu → Köprü'de öneri → kurucu onayı → iş kurucu oturumunda (bu şirketin dışında).

## Uyanma koşulu
Gelir, API maliyetini karşılayınca (kurucu kararı) — ayrı bir kurucu kararıyla toggle açılır; şirket zaten kurulu olduğundan kurulum sıfır.

## Uyanış kontrol listesi
- [ ] Gelir eşiği kurucu tarafından teyit edildi (karar kaydı KK formatında)
- [ ] `HOLDING_ENABLED` + b4-atolye enabled bayrağı açıldı
- [ ] Bakım-icracısı ve Deploy-yardımcısı runbook'ları güncel governance sürümüyle uyumlu mu kontrol edildi
- [ ] Sandbox-önce disiplini (asla oto-commit) tüm agent kayıtlarında doğrulandı
- [ ] Deploy tuzak tablosu (main/develop karışıklığı) her hedef repo için güncel mi tazelendi
- [ ] İlk 5 run kurucu-gözetiminde (R4 onaylı) çalıştırılacak şekilde işaretlendi

## Uyanış karar tablosu (iskelet)
| Bulgu türü | Aksiyon | Severity/etiket |
|---|---|---|
| LifeOS Android testçi eşiği doldu (12/12, 14 gün) | Bakım-icracısı DEĞİL — Deploy-yardımcısı release checklist başlatır | SEV2 |
| Burun Farkı G2 targetSdk deadline'ı (2026-08-31) yaklaşıyor | Bakım-icracısı bağımlılık güncelleme taslağı hazırlar | SEV1 (deadline ≤30gün) |
| Braavolabs platform `main` push sonrası Lightsail deploy hata verdi | Deploy-yardımcısı rollback taslağı + kurucuya anında bildirim | SEV0 |
| GitHub billing kilidi (portföy-geneli CI durdu) | Bakım-icracısı devreye girmez — doğrudan kurucu bildirimi (tek-nokta-arıza) | SEV0 |
| yulalab.com links (`develop` prod) yanlışlıkla `main`'e push denemesi | Deploy-yardımcısı deploy_notes kontrolü + push'u engeller | SEV1 |
| motion-core'da breaking değişiklik önerisi (5 app etkilenir) | Bakım-icracısı çalışmaz — CTO/Fikir-değerlendirici eskalasyonu | SEV1 |
| tabloda olmayan her durum | ESKALE ET | — |

## Feedback döngüsü
DEFTER şirket açıldığında kurulur (DNA kural 1). Kaçan-sinyal tanımı: kurucu oturumunda yapılan bir fix'in Atölye workflow'una hiç kaydedilmemesi (gölge-icra) — bu durumda Bakım-icracısı görev kaydı boş kalır ve retro'da BULGU sayılır.

## Sınırlar
Otonom commit/push/deploy ASLA yapmaz (açıldığında bile submit/deploy DAİMA kurucu onayı ister). Sandbox atlanarak "düzeltildi" bildirimi ASLA çıkmaz. Kritik kod (IAP/güvenlik/store) her zaman büyük modelde kalır — bu şirket onu devralmaz.

## Uzman eşiği
Kod türüne göre: backend-engineer, frontend-engineer, database-engineer, release-devops-engineer. Kritik kod (IAP/güvenlik/store submission) DAİMA Fable/Opus — bu şirketin küçük modeli değil.
