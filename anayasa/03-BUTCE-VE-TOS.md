# Anayasa §3 — Bütçe Tavanları + Abonelik ToS Çizgisi (v1)

**Kaynak:** FABLE_PLAN §1.3 + kurucu model stratejisi (lokal + ücretsiz öncelik; normal işleyiş ~$0-20/ay; tavanlar HEDEF değil GÜVENLİK AĞIDIR). Bu tabloyu hiçbir ajan değiştiremez (değişiklik = R5).

## Tavanlar (0-6 ay)

| Kalem | Değer |
|---|---|
| Provider konsol hard-cap | Anthropic $150/ay · OpenAI $50/ay · Gemini $20/ay (konsoldan — kod çökse bile çalışan tek fren; kurulum K2) |
| Günlük holding tavanı | soft $10 → alert · hard $25 → freeze (yalnız kurucu reset) |
| Workflow-run tavanı | $2 (içerik $0.50 · premium/Opus $5 + onay) |
| Eval/replay bütçesi | $30/ay, dataset ≤50 görev |
| Nöbetçi öz-bütçesi | $0.50/gün hard (aşım = "gürültülü ortam" sinyali) |
| Harcama-hız sensörü | >$2/5dk → anında S3 alarm |
| X (Twitter) ücretli API | 0-6 ay YOK |

6-12 ay: global $300/ay'a çıkarılabilir (kurucu kararı). Her çağrı venture'a cost-attribution taşır; tag'siz run reddedilir (Paket 9'dan itibaren zorunlu).

## Abonelik ToS çizgisi (birinci sınıf kural)

Claude Max + Codex + Gemini abonelik kotası **YALNIZCA** YULA'nın kendi iç işi + build-in-public + kurucu geliştirme işi içindir. **Müşteri-yüzü her execution = BYOK veya metered API.**
Policy guard: `run.tenant != YULA_INTERNAL && provider == subscription → REDDET`.

## Model önceliği

L0 betik → L1 lokal (Ollama) → L2 ücretsiz API (PII'siz işler) → L3 abonelik (yalnız YULA-içi) → L4 ücretli. Detay: `holding/plans/MODEL-ROUTING.md`. Ham PII/finans/sağlık verisi Çin-menşeli sağlayıcılara ve free-Gemini'ye HİÇBİR koşulda gitmez; PII redaction lokal-zorunludur (fail-closed).
