# Orkestratör Sözleşmeleri

Her orkestratör = **olay/cron-tetiklemeli sözleşmeli ROL** (7/24 açık süreç değil; boşta token yakan kalıcı ajan yok). Sözleşme formatı `.claude/agents/*.md` ile uyumlu **8-alan frontmatter**:

`id · purpose · allowed_tools · forbidden_tools · data_classes · approval · cost_ceiling · escalation_target`

**Kurallar:**
- Sözleşme = referans sinyal: her hop bu sözleşmeye + workflow charter'ına karşı ölçülür (Kompanzasyon §5A).
- Orkestratör uzman işi ÖNCE kataloğdan çağırır (Fable Mental + The Repo God + kurulu envanter — canlı sayılar `holding/registry/capabilities.yaml`'da) — kopyalamaz, adapte eder.
- Orkestratörler birbirine raporlar; kurucuya yalnız 2 kanal akar (günlük brief ≤5 madde + haftalık scorecard ≤8 KPI).
- Devreye alma takvimi (FABLE_PLAN §2): **CEO + CoS + Risk&Assurance → Paket 0-3 (bu ilk dalga)** · COO+CTO → P3-5 · CMO+CRO → P7-8 · CFO → P9 · Data&Learning → P10.

**Tam set (2026-07-27, KK-2026-07-27 sonrası):** Yönetim katı 10 sözleşme — `ceo` · `cos` · `risk-assurance` · `coo` · `cfo` · `cto` · `cpo` · `cmo` · `cro` · `data-learning` — artı 5 şirket masası: `venture-lifeos` · `venture-burun-farki` · `venture-braavolabs` (çift şapka: dogfood raportörü) · `venture-yulalab-com` · `venture-motion-ailesi` (uykuda). 8-alan sözleşmeye ek 9. alan: `model_chain` (MODEL-ROUTING sınıf referansı — tasarım büyük model, işletim küçük model ilkesinin sözleşmedeki karşılığı). Org şeması + katmanlar: `../tanimlar/ORG-SEMASI.md`; çalıştırılabilir workflow tanımları: `../tanimlar/workflows.yaml`. Devreye alma yine paket takvimiyle (rol yazılı olmak ≠ aktif olmak).
