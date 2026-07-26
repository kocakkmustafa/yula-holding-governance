# KK-2026-07-26 — HAT B Hibrit Açılış

**Tür:** Karar Kaydı (ADR) · **Karar veren:** Kurucu (AskUserQuestion, 2026-07-26) · **Durum:** KABUL

## Ne istendi

Kurucu direktifi: "Braavolabs ile AI holding otomasyonunu kuralım — ajan tanımları/hiyerarşi/sınırlar dosya olarak, ücretsiz API + lokal modellerle çalışsın, her adım deftere (build-in-public video kaynağı), mail/mesaj→tetik→dosya→çözüm döngüsü; Braavolabs'ın yetenekleri yetmezse ekleme/geliştirme yaparak devam."

## Bağlam ve kanıt

FABLE_PLAN v2.0 (KABUL 2026-07-22) istenen her şeyi zaten tanımlıyordu; blokaj iki eşikti: (a) Paket 0-1'in Dönüşüm Kapısı'na bağlanması (07-25), (b) motor inşaatının üç-ürün eşiği (07-22). Kapının asıl koruduğu risk — dosya ağacı dönüşümü — 2026-07-25'te zaten uygulandı. 5 paralel ajanla kanıtlı kapı taraması (2026-07-26): **G1 ✅ · G7 ✅ · G6 🟡 · G2/G3/G4/G5/G8 ⬜** (detay: `holding/GOREVLER.md` kapı tablosu + PROGRESS 17. tur).

## Karar (3 madde)

1. **HAT B HİBRİT AÇILIŞ:** Paket 0-1 + motor çekirdeği (P2-P3) ŞİMDİ başlar. Kalan kapı maddeleri (G2-G6, G8) HAT A'da ayrı oturumlarda paralel kapanır; **G2 (BF targetSdk 36, ⏰2026-08-31) en acil ürün işi.** Üç-ürün eşiği motor için kaldırıldı. 07-25 "tam bekleme" kararı geçersiz.
2. **Kurucu girdileri (4/4 verildi):** K1 governance repo (Fable açar) · K3 model key'leri (kurucu edinir, runbook: `holding/plans/KEY-KURULUM-RUNBOOK.md`) · K4 Ollama model çekimi (başladı) · K5 Telegram kalan ID'ler (runbook'ta).
3. **İlk uçtan uca döngü: Nöbetçi + GP1 PARALEL** (çekirdek P2-P3 sonrası iki golden path birlikte).

## Kapsam / etkilenen şirketler

Holding (motor, governance, nöbetçi) + 4 aktif venture (sinyal kaynağı olarak) + SM hattı. Iron Bank kapsam DIŞI (kalıcı). Ürün repolarına bu kararla dokunulmaz; motor işi Braavolabs monorepo'da `services/holding-orchestrator` dalında yürür.

## Değişmeyenler

R4/R5 daima kurucu (deploy/submit/fiyat/silme/secrets) · bütçe tavanları · abonelik ToS çizgisi · AI-etiket zorunluluğu · Reddit yalnız dinleme · K2 spend-cap'ler kurulmadan motor canlı cron'a bağlanmaz.

## Geri alma yolu

Bu karar dosyası revert edilir + GOREVLER/PROGRESS'e "HAT B yeniden beklemede" işlenir; motor işi dalda olduğundan main'e girmemiş hiçbir şey geri alınmaz; başlatılan model çekimleri disk temizliğiyle (`ollama rm`) geri alınabilir.
