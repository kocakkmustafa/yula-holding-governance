# Anayasa §1 — R0-R5 Risk Matrisi (v1)

**Kaynak:** El Kitabı Böl.4.4 + FABLE_PLAN §1.1. Her task/workflow envelope'ı bir `risk_class` taşımak ZORUNDADIR; sınıfsız iş policy-middleware'den geçemez.

| Sınıf | Tanım | Örnekler | Kim karar verir |
|---|---|---|---|
| **R0** | Salt okuma / analiz | log okuma, tarama, rapor hazırlama, sınıflandırma | Tam otomatik |
| **R1** | İç yazma (workspace/DB-iç, dışa görünmez) | DEFTER/PROGRESS güncelleme, issue açma, etiket, taslak üretimi, test koşma | Tam otomatik |
| **R2** | Düşük etkili dış işlem (dar kitle / geri alınabilir) | Telegram/Discord changelog, şablonlu FAQ yanıtı, iç kanal bildirimi | Policy-tabanlı otomatik — onaylı şablon + K0/K1 kapısı şartıyla (şablon seti bir kez kurucu onayı alır) |
| **R3** | Geniş kamu yayını / çalışan sisteme dokunuş | X/LinkedIn/YouTube postu, feature-flag, servis restart | Kanıtlanmış-workflow merdiveni (bkz. §2 Otonomi: 20-run) |
| **R4** | Geri alınması zor / itibari-mali etki | prod deploy, store submit, fiyat/IAP değişikliği, ödeme, veri silme, ana dala merge/push, hukuk-finans-sağlık iddiası içeren içerik | **DAİMA kurucu** |
| **R5** | Yapısal / yetkisel | secrets erişimi, yeni yüksek-risk yetki grant'ı, anayasa/politika değişikliği, harcama tavanı değişikliği, hesap açma/kapama | **DAİMA kurucu** |

**Sert kurallar:**
- R4/R5 hiçbir merdivenle, hiçbir başarı geçmişiyle otonomiye açılmaz.
- `trust_level: untrusted` girdiye dayanan hiçbir tool çağrısı insan onayı olmadan R1 üstüne çıkamaz (prompt-injection kapısı).
- Sınıf belirsizse bir ÜST sınıfa yuvarlanır (fail-closed).
- Kurucunun önceden verdiği kalıcı genel izinler (ör. LifeOS v2-branch commit/push) bu matrisin üzerinde, kayıtlı istisnadır.
