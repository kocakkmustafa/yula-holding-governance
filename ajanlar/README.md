# ajanlar/ — Runbook Katmanı

Bu dizin 59 ajanlık kadronun İŞLEYİŞ runbook'larını taşır (şablon: `RUNBOOK-SABLONU.md`; sayım ve fazlar: `holding/plans/HOLDING-YAPI-TASLAGI-2026-07-27.md` EK-A).

**Bilinçli kararlar (denetim açık-soruları kapatır):**
1. **Yönetim orkestratörlerinin (#1-10) runbook dosyası YOKTUR — kasıtlı:** onların tam tanımı `../sozlesmeler/`'dedir (sözleşme = yetki + tetik + model_chain). Orkestratör işleri karar-tablosuna indirgenemeyecek kadar bağlamsaldır (DNA kural 7'nin istisnası: bu katman zaten büyük-model/kurucu-oturumu ağırlıklıdır); F1 pratiği oturduktan sonra tekrar eden alt-işleri runbook'laştırılır.
2. **ID konvansiyonu (v3, KK-2026-07-28):** A-katı iştirak ajanları GLOBAL NUMARA KULLANMAZ — şirket-önekli slug: `<şirket-id>-<rol>` (ör. `a1-lifeos-gm`); 12 sabit rol slug'ı: gm · musteri-sesi · izleme-dogruluk · rakip-analisti · pazar-analisti · pazarlama-analisti · guvenlik · veri-gizliligi · hukuk-uyum · sosyal-medya · icerik · kod-test. Dosyalar: `istirakler/<şirket>/<rol>.md`. Global numaralar yalnız yönetim+B-katında sürer: 16-20+34-35 Gözcü · 21-26 Keşif · 27-29 Medya · 30-33 Atölye/Lab · 36-39 Kalkan · 40-48 ArGe/Oyun/Reklam · 49-52 Hukuk · 53 Abonelik-bekçisi · 54-55 uykuda-ek. **`masalar/` dizini v3'te SÜPERSEDE edilip kaldırıldı** (içerik GM+kadro runbook'larına evrildi; git geçmişinde durur).
3. **`medya/KRIZ-ILETISIM-RUNBOOK.md` ajan DEĞİL, süreç runbook'udur** (numarasız olması bundandır) — kriz anında Medya ajanlarının ve kurucunun izlediği ortak prosedür.
