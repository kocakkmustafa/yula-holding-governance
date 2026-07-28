---
id: a6-lissom
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [16-lissom-masasi]
---
# A6 — Lissom (uykuda)

## Kimlik ve amaç
Lissom, Motion ailesinin mobilite/yoga uygulamasıdır (ASC adı "Lissom: Mobility & Yoga") — aile içi sıra tavsiyesinde 1. yani kod kilidi açıldığında ilk üretime alınması önerilen üründür. motion-core'un paylaşılan hareket-tanıma çekirdeğini tüketecek 5 üründen biridir. Kod kurucu tetiğiyle açılana dek KAPALI. Şirket kaydı şimdiden hazır — aktivasyon günü kod-yazımı değil, tek toggle.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/lissom` · dizin `ventures/lissom/app` (+ `workspace`) · bundle id `com.yulalab.lissom`
- Store: ASC "Lissom: Mobility & Yoga" (asc_id 6794715023, durum prepare-for-submission) · Play (play_id 4974295481818580631, play_created: true)
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arıza)
- Canonical: `ventures/lissom/VENTURE.md`, `ventures/lissom/workspace/DEFTER.md`

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. Breaking sözleşme değişikliği connections.yaml impact_rule gereği tüketici DEFTER'ine kayıt + pinli-sürüm güncellemesi ister; bu şirket için karşılığı `ventures/lissom/workspace/DEFTER.md`'ye otomatik bulgu satırı. Lissom aile-ilk-sırada olduğu için motion-core'daki her breaking değişiklik burada erken yakalanır — geri kalan 4 üründen önce test edilmiş kabul edilmez, ayrı doğrulama gerekir.

## Uykuda görevleri
| Durum/desen | Aksiyon | Severity |
|---|---|---|
| ASC durumu prepare-for-submission dışına kayar (asc_id 6794715023 poll) | Bulgu yaz + Köprü bildirimi | SEV3 |
| Play kaydı (play_id 4974295481818580631) kaybolur/askıya alınır | Anında bildirim | SEV1 |
| Store'da "Lissom" adıyla başka geliştirici app'i görünür | Marka radarı bulgusu → Hukuk #50 eşiği | SEV2 |
| `ventures/lissom/app` dizininde commit/push algılanır (kilit açık değilken) | Kilit-ihlali alarmı → kurucuya anında | SEV1 |
| motion-core'da breaking-change commit algılanır | DEFTER bulgusu + pinli-sürüm hatırlatması | SEV3 |
| bundle id `com.yulalab.lissom` başka kayıtla çakışır | Anında bildirim | SEV1 |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | Etki notu: "Motion submit ettiğinde bu kurala tabi" | SEV3 |
| **tabloda olmayan HER durum** | ESKALE ET | — |

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu: kurucu tetiği (vault başlangıç promptu — aile içinde ÖNCE Lissom önerisi). Kontrol listesi: (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü güncel · (3) ASC/Play kaydı hâlâ prepare-for-submission · (4) marka radarında açık çakışma yok · (5) masa ajanı (#16) runbook'u tam-göreve yazıldı · (6) CTO mimari kapısından geçti.

## Workflow'ları
Beklenen key'ler (workflows.yaml v2'ye eklenecek, henüz kayıtlı değil): `lissom-rezervasyon-sagligi` (haftalık) · `lissom-marka-radari` (haftalık) · `lissom-kilit-ihlal-alarmi` (olay-tetikli, sürekli devriye).

## Feedback döngüsü
Haftalık retro (DNA kural 1): kaçan-sinyal = "ASC/Play durumu değişti ama bildirilmedi" veya "kilit-ihlali fark edilmeden commit geçti". Runbook revizyonu kurucu onayı olmadan uygulanmaz.

## Sınırlar
Kod dizinine YAZMAZ · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ (5/5 roadmap zaten hazır) · R1 üstü yetki YOK · dış-yazma YOK.

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk #50). Kilit-ihlali/mimari soru → CTO (#5) → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`.
