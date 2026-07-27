# YULA AI Holding — Org Şeması v1 (2026-07-27)

**Tasarım ilkesi (kurucu direktifi):** mimari + sözleşmeler + charter'lar BÜYÜK modelle (Fable) tasarlanır; **işletim 7/24 sunucuda küçük modellerle** koşar; zor vaka eskalasyon merdiveniyle yukarı taşınır. Hiçbir orkestratör 7/24 açık süreç değildir — hepsi olay/cron-tetiklemeli sözleşmeli roldür (boşta token yakımı = 0).

## Hiyerarşi

```
KURUCU (insan — tek hukuki yetkili; R4/R5 daima onda)
│
├── YÖNETİM KATI (olay-tetiklemeli orkestratörler; 10 sözleşme: sozlesmeler/)
│   ├── CEO ............ direktif→karar-kaydı→görev dağıtımı; günlük brief
│   ├── CoS ............ onay kuyruğu, defter sağlığı, haftalık scorecard
│   ├── Risk&Assurance . BAĞIMSIZ denetim (CEO'yu bypass edebilir; üretici≠yargıç)
│   ├── COO ............ akış/kuyruk/cron sağlığı
│   ├── CTO ............ mimari kapısı; kritik kod DAİMA büyük modelde
│   ├── CFO ............ maliyet ataması + P&L (tavanları DEĞİŞTİREMEZ)
│   ├── CPO ............ review/destek→ürün backlog kanıt dosyaları
│   ├── CMO ............ story_candidate→hero-artifact→onaylı yayın
│   ├── CRO ............ müşteri sinyali→şablonlu yanıt→closed-loop
│   └── Data&Learning .. learning-card + terfi disiplini + hâkim kalibrasyonu
│
├── ŞİRKET MASALARI (venture-desk sözleşmeleri; sinyal→bulgu→brief hattı)
│   ├── LifeOS masası          (aktif — sağlık-iddia nöbeti)
│   ├── Burun Farkı masası     (aktif — ⏰G2 bekçisi; dürüstlük çizgisi)
│   ├── Braavolabs masası      (aktif — ÇİFT ŞAPKA: venture + dogfood raportörü)
│   ├── yulalab.com masası     (aktif — çapraz-iddia tazeliği)
│   └── Motion ailesi masası   (⏸️ uykuda — kod kilidi bekçisi)
│   [Iron Bank: KALICI OLARAK YOK — holding dışı, hiçbir katmanda görünmez]
│
├── İŞÇİ KATMANI (kalıcı kimliksiz, ucuz-model görev işçileri)
│   ├── Nöbetçi S0 ..... deterministik sensörler ($0: mail-filtre, heartbeat,
│   │                    dead-letter, cost-rate, uptime) — KOD, model değil
│   ├── Nöbetçi S1 ..... Qwen3-4B devriyesi (3 saatte bir; sinyal yoksa LLM yok)
│   ├── Nöbetçi S2 ..... olay-tetikli değerlendirici (sınıf-5 zinciri)
│   ├── K0/K1 hâkimler . K0=betik linter; K1=Haiku drift-hâkimi (rubrik)
│   ├── Sınıflandırıcılar (mail/review/mention — sınıf-1 zinciri, batch)
│   └── İçerik taslakçısı (Qwen3-8B — yayın DAİMA insan-kapılı)
│
└── UZMAN HAVUZU (kadrolu DEĞİL — çağrıldıkça)
    ├── Fable Mental danışmanları (66; canlı sayı registry'de)
    ├── The Repo God (91 repo — önce-katalog kuralı)
    └── Kurulu skill/MCP envanteri
```

## Model katmanlaması (kim hangi beyinle çalışır)

| Katman | Model | Ne zaman |
|---|---|---|
| TASARIM (bu iş) | **Fable / Opus** | Mimari, sözleşme, charter, anayasa, kritik kod, adversarial denetim — kurucu oturumlarında |
| İŞLETİM-yerel L1 | Qwen3-4B (devriye) · Qwen3-8B (taslak) · Qwen2.5-Coder-7B (basit kod) · EmbeddingGemma/BGE-M3 | Mac açıkken $0; sınıf-1/3/5/7/8/9 işleri |
| İŞLETİM-bulut L2 | Gemini Flash-Lite (omurga) · Groq · NVIDIA NIM · OpenRouter-free | Mac kapalıyken + lokal yetmezse; YALNIZ PII'siz |
| KALİTE TABANI L3 | Claude Haiku | Drift/SEV hâkimleri (free birincil OLAMAZ) |
| ESKALASYON L4 | Sonnet/Opus/Fable | Eşik-altı güven, kritik yayın kapısı, incident |

Eskalasyon tetikleri + zincir tabloları: `holding/plans/MODEL-ROUTING.md` (9 görev sınıfı). Bozulmazlık modelden değil KAPILARDAN gelir: constrained-decode + şema-validator + N=3 retry + self-consistency + devre kesici + fail-closed policy.

## Yürütme yüzeyi (KK-2026-07-27)

İş, **Braavolabs YULA_INTERNAL tenant'ında** ürünün kendi pipeline/run/approval makinesiyle koşar (desktop/mobil/CLI yüzeylerinde görünür); `modules/holding` kabuğu her run'ı charter+policy+cost+audit ile sarar. Onay yüzeyleri: Telegram (v1) + Braavo mobil (D5 turu ile).
