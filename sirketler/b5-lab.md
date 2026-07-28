---
id: b5-lab
kat: B
durum: uykuda
faz: uyanma-kosulu
ajanlar: [32-fikir-degerlendirici, 33-venture-kurulumcusu]
---
# B5 — YULA Lab (Venture Factory)

## Kimlik ve amaç
Fikir→Aşama-0/2 doğrulama→venture açılışı fabrikası. B2 Keşif'in haftalık Fırsat Raporu'ndan (proje fikirleri, kanıt linkli) beslenir; şablonlu iskeletle (Paket 11) yeni venture'ı ayağa kaldırır. Açılışı ayrı bir kurucu kararıdır.

## Varlıklar ve bağlar
Girdi: B2 Keşif'in haftalık Fırsat Raporu (Fikir-radarcısı + Sentezci çıktısı). Çıktı hedefi: `holding/templates/new-venture/` iskeleti + `holding/registry/ventures.yaml` kaydı. Referans: motion-core (`ventures.yaml`, `product:false`) — yeni bir hareket-app'i fikri gelirse consumers listesine eklenme adayı.

## Uykuda görevleri
Paket 11 (venture-factory şablonları) tamamlanana dek üretim yok; Keşif raporları birikir ama Aşama-0 dosyası açılmaz.

## Uyanma koşulu
B5 Lab için Paket 11 çalışır hale gelince (şablon + doğrulama disiplini hazır) — ilk koşum kurucu tetikli.

## Uyanış kontrol listesi
- [ ] Paket 11 şablonları (`holding/templates/new-venture/`) güncel governance sürümüyle uyumlu mu doğrulandı
- [ ] B2 Keşif'in birikmiş Fırsat Raporları geriye dönük tarandı (kaçmış güçlü sinyal var mı)
- [ ] Aşama-0/Aşama-2 doğrulama kriterleri (kanıt eşiği) yazılı hale getirildi
- [ ] Fikir-değerlendirici ve Venture-kurulumcusu runbook'ları güncel sürümle eşleşiyor
- [ ] `ventures.yaml` kayıt formatı (dirs/repos/canonical) şablonla test edildi
- [ ] İlk açılış kurucu-gözetiminde (R4 onaylı) yürütülecek şekilde işaretlendi

## Uyanış karar tablosu (iskelet)
| Girdi | Aksiyon | Severity/etiket |
|---|---|---|
| B2 Keşif haftalık Fırsat Raporu'nda "proje fikri" satırı | Fikir-değerlendirici Aşama-0 doğrulama dosyası açar | INFO |
| Fikir motion-core'a yeni bağımlılık gerektiriyor | `connections.yaml` impact_rule kontrolü (5 app'e etki) → dosyaya not | SEV bilgi |
| Aşama-0 geçti, Aşama-2 (pazar) kanıtı yetersiz | Venture-kurulumcusu ÇALIŞTIRILMAZ — "daha fazla kanıt gerekli" notu kurucuya | SEV bilgi |
| Kurucu onayı geldi | Venture-kurulumcusu şablon iskelet + `ventures.yaml` kayıt taslağı üretir | SEV bilgi |
| Fikir ismi mevcut markayla (Gravita/Lissom/JabLab/Ostinato/Choreia) çakışıyor | Aşama-2'ye geçmeden Hukuk'a marka/telif ön-kontrol eskalasyonu | SEV1 |
| İki fikir aynı pazarı hedefliyor (kaynak çakışması) | founder-ops-strategist eşiği + kurucuya öncelik sorusu | SEV bilgi |
| tabloda olmayan her durum | ESKALE ET | — |

## Feedback döngüsü
DEFTER Paket 11'de açılır. Kaçan-sinyal: Keşif'in Fırsat Raporu'ndaki kanıt-linkli güçlü bir sinyalin Aşama-0 dosyasına hiç düşmemesi (rapor okunmadı).

## Sınırlar
Kurucu onayı olmadan yeni venture repo/dizini ASLA açılmaz. Aşama-0/2 doğrulaması atlanarak "hazır" ASLA denmez. Venture-kurulumcusu gerçek GitHub kaydını kendisi oluşturmaz — yalnız taslak üretir.

## Uzman eşiği
founder-ops-strategist (hangi ürüne odaklanmalı), competitive-intelligence-analyst (pazar doğrulama), growth-marketing-strategist (launch fizibilitesi), legal-contracts-advisor (isim/marka çakışması).
