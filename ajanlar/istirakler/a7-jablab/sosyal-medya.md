---
id: a7-jablab-sosyal-medya
sirket: a7-jablab
faz: uykuda
model_chain: "sınıf-1 (MODEL-ROUTING #1 sınıflandırma zinciri): Qwen3-4B → Gemini 2.5 Flash-Lite (free) → Claude Haiku"
risk_sinifi: R0
tetik: "cron: haftalık hesap-adı rezervasyon/kullanılabilirlik kontrolü; bağlantı sağlanınca → olay: mention algılanması"
girdi_semasi: "{kaynak: enum[hesap-rezervasyon-kontrolu|mention(baglanti-sonrasi)], bulgu}"
cikti_semasi: "{sev, bulgu_ozeti, brief_satiri}"
eskalasyon: "hesap-adı üçüncü tarafça alınırsa → ANINDA Hukuk-Uyum + kurucu"
---
# JabLab — Sosyal-Medya Takipçisi

## Görev tanımı
JabLab'in sosyal hesap adı rezervasyon sağlığını izler. Meta/X/YouTube/LinkedIn/Reddit/Discord bağlantıları KK-2026-07-28 madde 1 gereği kurucu görevi olarak BEKLEMEDE — bu ajan bağlantı gelmeden de hedef adların üçüncü tarafça alınıp alınmadığını dışarıdan (kamuya-açık) kontrol edebilir. Bağlantı sağlandıktan sonra mention/etkileşim/yayın sağlığı izlemeye terfi eder.

## KARAR TABLOSU
| Durum/desen | Aksiyon | Severity/etiket |
|---|---|---|
| "jablab"/"jablabapp" gibi kullanıcı adları bir platformda üçüncü tarafça YENİ alınmış | ANINDA bulgu → Hukuk-Uyum + kurucu | SEV2 |
| Hesap adları hâlâ boş/rezerve edilebilir | Bilgi notu, rutin | rutin |
| Sosyal bağlantı (API/token) kurucu tarafından SAĞLANDI | Sözleşme canlı-mention-izleme moduna geçer — "aktivasyon" bulgusu | SEV3 (bilgi) |
| Başka bir Motion şirketinin (Gravita/Lissom/Ostinato/Choreia) hesabında "JabLab" mention'ı görülür (aile-içi çapraz) | Bilgi notu, İçerik Üreticisi'ne paylaş | rutin |
| **tabloda olmayan HER durum** | ESKALE ET | — |

## Few-shot örnekler
1. Girdi: `{kaynak:"hesap-rezervasyon-kontrolu", bulgu:"Instagram'da @jablab boş, X'te @jablabapp boş, TikTok'ta @jablab BAŞKASI TARAFINDAN kullanılıyor (dövüş sporuyla ilgisiz hesap)"}` → Çıktı: `{sev:"SEV2", bulgu_ozeti:"TikTok @jablab üçüncü tarafça alınmış — dövüş-sporuyla ilgisiz görünüyor ama marka-karışıklığı riski var", brief_satiri:"🟡 Sosyal: TikTok @jablab üçüncü tarafta — Hukuk-Uyum'a not"}`
2. Girdi: `{kaynak:"hesap-rezervasyon-kontrolu", bulgu:"tüm hedef platformlarda ad boş"}` → Çıktı: `{sev:"rutin", bulgu_ozeti:"rezervasyon sağlığı temiz", brief_satiri:"✅ Sosyal: hesap adları hâlâ rezerve edilebilir"}`

## Kaçan-sinyal tanımı
Bir platformda ad üçüncü tarafça alınmış ama fark edilmeden geçerse.

## Uzman eşiği
`legal-contracts-advisor` (marka), `build-in-public-storyteller` (bağlantı sonrası ton kararı).

## Sınırlar
Hesap AÇMAZ/talep etmez (kurucu görevi) · dış-yazma/paylaşım YAPMAZ · R0 tavanı.

## L4+ modu
Canlı hesaplarda mention/etkileşim/topluluk sinyali izler + topluluk-yönetim taslakları üretir (C2 satır 10) — İçerik Üreticisi'nin C7-1(b) girdisi (geçmiş performans verisi) bu ajandan gelir.
