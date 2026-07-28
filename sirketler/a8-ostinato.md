---
id: a8-ostinato
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [58-ostinato-masasi]
---
# A8 — Ostinato (uykuda)

## Kimlik ve amaç
Ostinato, Motion ailesinin çalgı-pratiği uygulamasıdır (ASC adı "Ostinato: Music Practice") — marka TÜM çalgılara açık tasarlandı, ilk motor çello. motion-core'un paylaşılan hareket-tanıma çekirdeğini tüketecek 5 üründen biridir. Kod kurucu tetiğiyle açılana dek KAPALI; V0 öncesi D3 veri-protokolü + B2B (konservatuvar/öğretmen) değerlendirmesi önce gelir. Şirket kaydı şimdiden hazır — aktivasyon günü kod-yazımı değil, tek toggle.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/ostinato` · dizin `ventures/ostinato/app` (+ `workspace`) · bundle id `com.yulalab.ostinato`
- Store: ASC "Ostinato: Music Practice" (asc_id 6794717868, durum prepare-for-submission) · Play (play_id 4975537094732577317, play_created: true)
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arıza)
- Canonical: `ventures/ostinato/VENTURE.md`, `ventures/ostinato/workspace/DEFTER.md`

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. Breaking sözleşme değişikliği connections.yaml impact_rule gereği tüketici DEFTER'ine kayıt + pinli-sürüm güncellemesi ister; bu şirket için karşılığı `ventures/ostinato/workspace/DEFTER.md`'ye otomatik bulgu satırı. Ostinato'nun D3 veri-protokolü kararı (çalgı-bağımsız duruş/parmak takibi mi, çalgıya özel mi) motion-core'un genelleştirme kapsamını doğrudan etkiler — sözleşme değişince öncelik burada değerlendirilir.

## Uykuda görevleri
| Durum/desen | Aksiyon | Severity |
|---|---|---|
| ASC durumu prepare-for-submission dışına kayar (asc_id 6794717868 poll) | Bulgu yaz + Köprü bildirimi | SEV3 |
| Play kaydı (play_id 4975537094732577317) kaybolur/askıya alınır | Anında bildirim | SEV1 |
| Store'da "Ostinato" adıyla başka geliştirici app'i görünür | Marka radarı bulgusu → Hukuk #50 eşiği | SEV2 |
| `ventures/ostinato/app` dizininde commit/push algılanır (kilit açık değilken) | Kilit-ihlali alarmı → kurucuya anında | SEV1 |
| motion-core'da breaking-change commit algılanır | DEFTER bulgusu + pinli-sürüm hatırlatması | SEV3 |
| bundle id `com.yulalab.ostinato` başka kayıtla çakışır | Anında bildirim | SEV1 |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | Etki notu: "Motion submit ettiğinde bu kurala tabi" | SEV3 |
| **tabloda olmayan HER durum** | ESKALE ET | — |

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu: kurucu tetiği (vault başlangıç promptu) + D3 veri-protokolü/B2B değerlendirmesinin kapanması. Kontrol listesi: (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü güncel · (3) ASC/Play kaydı hâlâ prepare-for-submission · (4) marka radarında açık çakışma yok · (5) masa ajanı (#18) runbook'u tam-göreve yazıldı · (6) CTO mimari kapısından geçti (D3 protokol kararı dahil).

## Workflow'ları
Beklenen key'ler (workflows.yaml v2'ye eklenecek, henüz kayıtlı değil): `ostinato-rezervasyon-sagligi` (haftalık) · `ostinato-marka-radari` (haftalık) · `ostinato-kilit-ihlal-alarmi` (olay-tetikli, sürekli devriye).

## Feedback döngüsü
Haftalık retro (DNA kural 1): kaçan-sinyal = "ASC/Play durumu değişti ama bildirilmedi" veya "kilit-ihlali fark edilmeden commit geçti". Runbook revizyonu kurucu onayı olmadan uygulanmaz.

## Sınırlar
Kod dizinine YAZMAZ · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ (D3 kararı kurucu+CTO işi) · R1 üstü yetki YOK · dış-yazma YOK.

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk #50). Kilit-ihlali/mimari soru → CTO (#5) → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`.
