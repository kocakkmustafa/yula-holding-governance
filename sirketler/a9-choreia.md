---
id: a9-choreia
kat: A
durum: uykuda
faz: uyanma-kosulu
ajanlar: [19-choreia-masasi]
---
# A9 — Choreia (uykuda)

## Kimlik ve amaç
Choreia, Motion ailesinin dans-öğrenme uygulamasıdır (ASC adı "Choreia: Learn to Dance"). motion-core'un paylaşılan hareket-tanıma çekirdeğini tüketecek 5 üründen biridir. Kod kurucu tetiğiyle açılana dek KAPALI; aile içindeki en sıkı kapı buradadır — TAM PLAN yazılmadan kod açılmaz (C-001, M-009). Şirket kaydı şimdiden hazır — aktivasyon günü kod-yazımı değil, tek toggle.

## Varlıklar ve bağlar
- Repo `kocakkmustafa/choreia` · dizin `ventures/choreia/app` (+ `workspace`) · bundle id `com.yulalab.choreia`
- Store: ASC "Choreia: Learn to Dance" (asc_id 6794721329, durum prepare-for-submission) · Play (play_id 4972759001780942116, play_created: true)
- Paylaşılan hesaplar: Apple Developer T5HZGYBWK8 (8 üye — BF 2.3.6 reddi hesap-itibarı riski hepsine değer) · Google Play tek-hesap (⏰2026-08-31 Billing/targetSdk uyarısı henüz Motion'ı vurmuyor ama submit ettiği an aynı hesaba tabi) · GitHub kocakkmustafa (billing tek-nokta-arıza)
- Canonical: `ventures/choreia/VENTURE.md`, `ventures/choreia/workspace/DEFTER.md`, `ventures/choreia/app/docs/choreia-brief.md`

### motion-core ortak varlık
`motion-core` (repo `kocakkmustafa/motion-core`) şirket DEĞİL — Gravita+Lissom+JabLab+Ostinato+Choreia'nın paylaştığı çekirdek kütüphane. Breaking sözleşme değişikliği connections.yaml impact_rule gereği tüketici DEFTER'ine kayıt + pinli-sürüm güncellemesi ister; bu şirket için karşılığı `ventures/choreia/workspace/DEFTER.md`'ye otomatik bulgu satırı. Kayıt notu: connections.yaml'daki mevcut impact_rule metni yalnız gravita+lissom+jablab+ostinato'yu sayıyor, Choreia'yı ayrıca adlandırmıyor — ventures.yaml `consumers` alanı ise Choreia'yı da içeriyor; bu senkron farkı kayıt-senkronu döngüsüne bulgu olarak düşer, mimariyi değiştirmez.

## Uykuda görevleri
| Durum/desen | Aksiyon | Severity |
|---|---|---|
| ASC durumu prepare-for-submission dışına kayar (asc_id 6794721329 poll) | Bulgu yaz + Köprü bildirimi | SEV3 |
| Play kaydı (play_id 4972759001780942116) kaybolur/askıya alınır | Anında bildirim | SEV1 |
| Store'da "Choreia" adıyla başka geliştirici app'i görünür | Marka radarı bulgusu → Hukuk #50 eşiği | SEV2 |
| `ventures/choreia/app` dizininde commit/push algılanır (TAM PLAN onaylanmadan) | Kilit-ihlali alarmı → kurucuya anında | SEV1 |
| motion-core'da breaking-change commit algılanır | DEFTER bulgusu + pinli-sürüm hatırlatması | SEV3 |
| bundle id `com.yulalab.choreia` başka kayıtla çakışır | Anında bildirim | SEV1 |
| Apple/Google hesap-geneli politika uyarısı (⏰2026-08-31 dahil) yayınlanır | Etki notu: "Motion submit ettiğinde bu kurala tabi" | SEV3 |
| **tabloda olmayan HER durum** | ESKALE ET | — |

## Uyanma koşulu + uyanış kontrol listesi
Uyanma koşulu: kurucu tetiği (vault başlangıç promptu) + TAM PLAN'ın yazılıp kurucu onayından geçmesi (C-001, M-009). Kontrol listesi: (1) DEFTER'de açık P0 yok · (2) motion-core pin sürümü güncel · (3) ASC/Play kaydı hâlâ prepare-for-submission · (4) marka radarında açık çakışma yok · (5) masa ajanı (#19) runbook'u tam-göreve yazıldı · (6) CTO mimari kapısından TAM PLAN'la geçti.

## Workflow'ları
Beklenen key'ler (workflows.yaml v2'ye eklenecek, henüz kayıtlı değil): `choreia-rezervasyon-sagligi` (haftalık) · `choreia-marka-radari` (haftalık) · `choreia-kilit-ihlal-alarmi` (olay-tetikli, sürekli devriye).

## Feedback döngüsü
Haftalık retro (DNA kural 1): kaçan-sinyal = "ASC/Play durumu değişti ama bildirilmedi" veya "kilit-ihlali fark edilmeden commit geçti". Runbook revizyonu kurucu onayı olmadan uygulanmaz.

## Sınırlar
Kod dizinine YAZMAZ (TAM PLAN'sız kod kapısı en katı olan şirket) · store submit YAPMAZ · roadmap/ürün kararı ÜRETMEZ · R1 üstü yetki YOK · dış-yazma YOK.

## Uzman eşiği
Marka/isim çakışması → `legal-contracts-advisor` (+B10 Hukuk #50). Kilit-ihlali/mimari soru → CTO (#5) → gerekirse `fable-stratejist`. Store kaydı anomalisi → `store-policy-officer`.
