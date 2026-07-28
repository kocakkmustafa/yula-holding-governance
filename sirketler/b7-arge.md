---
id: b7-arge
kat: B
durum: uykuda
faz: uyanma-kosulu
ajanlar: [40-teknoloji-izcisi, 41-prototipci, 42-deney-raportoru]
---
# B7 — YULA ArGe

## Kimlik ve amaç
Teknoloji araştırma + prototipleme yeteneği. Keşif'ten farkı: Keşif PAZARI tarar, ArGe TEKNOLOJİYİ. İşleri: paper/repo/model izciliği (arsenal güncellenir), fizibilite prototipleri, deney raporları. Motion V0 kapıları açıldığında ilk gerçek müşterisi Motion ailesi olur.

## Varlıklar ve bağlar
`arsenal/the-repo-god/INDEX.md` (91 repo, önce-katalog kaynağı); motion-core (`ventures.yaml`, 5 app'in ortak çekirdeği); Motion ailesi V0 kapıları — Gravita D1 (ters-duruş fizibilitesi), JabLab D2 (fps/blur ölçümü), Ostinato D3 (veri protokolü+B2B), Choreia (TAM PLAN önce zorunlu, C-001/M-009).

## Uykuda görevleri
ArGe kararı gelene dek çalışmaz; Motion V0 kapıları AÇIK olsa da prototip üretimi başlamaz (kapı açılışı ayrı, ArGe uyanışı ayrı).

## Uyanma koşulu
ArGe kararı (ayrı kurucu kararı) — devreye girince ilk hedef Motion V0 kapılarıdır.

## Uyanış kontrol listesi
- [ ] arsenal INDEX.md güncelliği (kaç repo, hangi kategori) teyit edildi
- [ ] Motion V0 kapı tanımları (D1/D2/D3, Choreia plan-önce kısıtı) runbook'lara işlendi
- [ ] Prototip sandbox dalı politikası (asla motion-core ana dalına doğrudan merge yok) test edildi
- [ ] Deney-raportörü'nün ön-kayıt disiplini (kriter deney ÖNCESİ) şablonlaştı
- [ ] Teknoloji-izcisi'nin lisans-kontrol adımı (AGPL/GPL yasağı — motion-ailesi kuralı) doğrulandı
- [ ] İlk koşum kurucu-gözetiminde işaretlendi

## Uyanış karar tablosu (iskelet)
| Girdi | Aksiyon | Severity/etiket |
|---|---|---|
| Gravita V0 kapısı D1 (ters-duruş fizibilitesi) açılış istendi | Prototipçi fizibilite prototipi + Deney-raportörü kanıt dosyası | INFO |
| JabLab V0 kapısı D2 (fps/blur ölçümü) istendi | Prototipçi MediaPipe tabanlı ölçüm prototipi hazırlar | INFO |
| Ostinato D3 (veri protokolü+B2B) fizibilitesi istendi | Teknoloji-izcisi ilgili repo/paper taraması → arsenal-aday | INFO |
| motion-core'da yeni bir CV modeli denenecek | Prototipçi ayrı dalda dener, motion-core ana dal ETKİLENMEZ | SEV bilgi |
| arsenal INDEX.md'de zaten karşılığı olan araç yeniden aranıyor | Teknoloji-izcisi ADAPTE öner, yeniden yazma önermez (DNA kural 2) | SEV1 |
| Deney sonucu negatif çıktı (fizibilite YOK) | Deney-raportörü "hayır" kararını da kanıtlı kapatır | INFO |
| tabloda olmayan her durum | ESKALE ET | — |

## Feedback döngüsü
Kaçan-sinyal: arsenal'da zaten var olan bir repo/deseni bilmeden sıfırdan yazma girişimi (DNA kural 2 ihlali) veya negatif sonuçlu bir deneyin raporlanmadan terk edilmesi.

## Sınırlar
Prototip kodunu ASLA doğrudan production'a taşımaz (Atölye/CTO devralır). Katalog taraması atlanmadan "yeni araç" önerisi ASLA çıkmaz. Choreia gibi plan-önce kısıtlı venture'da plan yokken prototip ASLA başlamaz.

## Uzman eşiği
model-routing-advisor (hangi model/mimari), motion-cv-engineer / audio-dsp / movement-science-advisor (Motion'a özgü prototipler), legal-contracts-advisor (lisans uyumu, AGPL/GPL riski).
