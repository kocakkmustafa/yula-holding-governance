---
id: b8-oyun
kat: B
durum: uykuda
faz: uyanma-kosulu
ajanlar: [43-oyun-tasarim-masasi, 44-oyun-tech-masasi, 45-liveops-gozcusu]
---
# B8 — YULA Oyun

## Kimlik ve amaç
Oyun stüdyosu YETENEĞİ (PC + mobil oyun üretimi): motor seçimi, core-loop tasarımı, playtest disiplini, LiveOps. Önemli ayrım: çıkacak her oyun A-katında KENDİ şirketi olur (ürün); B8 ona üretim hizmeti verir (Atölye'nin oyun muadili).

## Varlıklar ve bağlar
Danışman havuzu hazır: game-design-architect + game-tech-engineer (`capabilities.yaml`). Henüz hiçbir A-şirketi oyun değil — 4 aktif ürün (LifeOS/Burun Farkı/Braavolabs/yulalab.com) + 5 Motion app hiçbiri oyun kategorisinde değil.

## Uykuda görevleri
Yok. Mevcut kural korunur: oyun venture'ları B5 Lab (Paket 11) çalışır hale gelmeden açılmaz.

## Uyanma koşulu
Paket 11 sonrası (B5 Lab çalışır hale gelince) VE ilk oyun fikri Aşama-2 doğrulamasını geçince.

## Uyanış kontrol listesi
- [ ] B5 Lab'ın ilk onaylı oyun fikri (Aşama-0+2 geçmiş) elde var mı doğrulandı
- [ ] Oyun-tasarım masası ve Oyun-tech masası runbook'ları güncel sürümle eşleşiyor
- [ ] Motor lisans taraması (AGPL/GPL yasağı — motion-ailesi kuralına paralel) kontrol listesine eklendi
- [ ] IAP/monetizasyon kararı için pricing-monetization-strategist eşiği tanımlı
- [ ] LiveOps-gözcüsü için metrik kaynağı (hangi platform API'si) netleşti
- [ ] İlk oyun venture'ının A-katında ayrı şirket olarak açılacağı registry'ye işlendi

## Uyanış karar tablosu (iskelet)
| Girdi | Aksiyon | Severity/etiket |
|---|---|---|
| B5 Lab'dan onaylı bir oyun fikri geldi | Oyun-tasarım masası core-loop/ekonomi taslağı hazırlar | INFO |
| Motor seçimi gerekiyor (Flame/Godot/Unity) | Oyun-tech masası performans bütçesi (60fps/16.6ms) karşılaştırması yapar | INFO |
| İlk oyun canlıya çıktı | LiveOps-gözcüsü nöbeti başlar (metrik/etkinlik) | INFO |
| Playtest'te core-loop terk oranı yüksek çıktı | Oyun-tasarım masası ekonomi/zorluk revizyonu + kanıt dosyası | SEV1 |
| Oyun IAP/monetizasyon kararı gerekiyor | pricing-monetization-strategist danışman eşiğine düşer | SEV bilgi |
| Yeni oyun mevcut bir Motion app ile aynı pazarı hedefliyor | Oyun-tasarım masası → B5 Lab çakışma kontrolü ister | SEV1 |
| tabloda olmayan her durum | ESKALE ET | — |

## Feedback döngüsü
Kaçan-sinyal: playtest bulgusunun core-loop tasarım dosyasına hiç işlenmemesi (aynı hata tekrar oynanır).

## Sınırlar
Paket 11 tamamlanmadan bir oyun venture'ı ASLA açılmaz. Motor seçimi performans bütçesi kanıtı olmadan ASLA onaylanmaz. Etik-dışı monetizasyon deseni (pay-to-win vb.) kurucu onayı olmadan tasarıma ASLA girmez.

## Uzman eşiği
game-design-architect (core-loop/ekonomi/playtest), game-tech-engineer (motor/performans/platform servisleri), pricing-monetization-strategist (IAP/monetizasyon etiği).
