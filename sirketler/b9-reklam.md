---
id: b9-reklam
kat: B
durum: uykuda
faz: uyanma-kosulu
ajanlar: [46-kampanya-planlayicisi, 47-kreatif-uretici, 48-reklam-performanscisi]
---
# B9 — YULA Reklam

## Kimlik ve amaç
Paid-ads/kreatif/performans yeteneği: ASA/Meta/Google App Campaigns kampanya planı, kreatif üretimi (AI-etiket kurallı), CAC/LTV disiplinli performans analizi. Önce kendi ürünlerimize çalışır (ilerde ajans hizmeti = ayrı kurucu kararı).

## Varlıklar ve bağlar
4 aktif ürün (LifeOS, Burun Farkı, Braavolabs, yulalab.com) + 5 Motion app (henüz coming-soon, kampanya hedefi DEĞİL) potansiyel kampanya yüzeyleri. Danışman: paid-ads-strategist (`capabilities.yaml`).

## Uykuda görevleri
Yok — bütçesiz reklam şirketi açmak anlamsız (paid-ads-strategist'in frenleyici ilkesi).

## Uyanma koşulu
Reklam bütçesi kararı (kurucu) — bütçesiz açılış anlamsız olduğundan tetik doğrudan bütçe onayına bağlıdır.

## Uyanış kontrol listesi
- [ ] Kurucu bütçe tavanı + hedef ürün + bölge net şekilde onayladı (karar kaydı)
- [ ] Burun Farkı için Türkiye-only sınırının kampanya hedeflemesine geçtiği doğrulandı
- [ ] AI-etiket disiplini (Anayasa §4 disclosure) kreatif üretim akışına bağlandı
- [ ] Braavolabs kampanyaları için "CTA arkasında ürün var mı" ön-kontrolü tanımlı
- [ ] CAC/LTV ölçüm hattı (kaynak API'ler) Reklam-performansçısı runbook'una işlendi
- [ ] İlk kampanya kurucu-gözetiminde (R3+ onaylı) başlatılacak şekilde işaretlendi

## Uyanış karar tablosu (iskelet)
| Girdi | Aksiyon | Severity/etiket |
|---|---|---|
| Kurucu reklam bütçesi onayladı (ör. Burun Farkı için ASA testi) | Kampanya-planlayıcısı bütçe/test tasarımı taslağı hazırlar | INFO |
| Kreatif üretildi, AI-etiket eksik | Kreatif-üretici YAYINLANMAZ — etiket eklenmeden kapı geçilmez | SEV1 |
| CAC, LTV tahminini 30 gün üst üste aştı | Reklam-performansçısı kesme-kararı kanıt dosyası + kurucuya bildirim | SEV1 |
| Braavolabs kampanyası isteniyor ama site CTA'larının arkasında ürün YOK (bilinen açık nokta) | Kampanya-planlayıcısı BAŞLATMAZ — önce ürün-hazır kontrolü | SEV1 |
| Burun Farkı için Türkiye-dışı bölge hedefleme önerisi geldi | Kampanya-planlayıcısı REDDEDER — Türkiye-only kasıtlı sınır | SEV1 |
| Kampanya metni dürüstlük çizgisini aşıyor (ör. "bahis" çağrışımı) | Kreatif-üretici REDDEDER — BF "analiz, bahis değil" ilkesi | SEV1 |
| tabloda olmayan her durum | ESKALE ET | — |

## Feedback döngüsü
Kaçan-sinyal: CAC/LTV oranı kötüleşirken kesme-kararının 30 günden uzun gecikmesi.

## Sınırlar
Bütçe onayı olmadan kampanya ASLA başlatılmaz. AI-üretimi kreatif etiketsiz ASLA yayınlanmaz. Burun Farkı ASLA Türkiye-dışına hedeflenmez.

## Uzman eşiği
paid-ads-strategist (bütçe/kanal kararı), pricing-monetization-strategist (LTV varsayımları), marketing-aso-specialist (store-yan kreatif tutarlılığı), brand-identity-designer (marka kimliği kontrolü).
