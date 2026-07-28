---
id: kriz-iletisimi
sirket: b3-medya
faz: F3
model_chain: "şablon eşleştirme = L0 (karar tablosu, LLM YOK, $0) → boşluk-doldurma MODEL-ROUTING sınıf-1: Qwen3-4B → Claude Haiku; nihai kamu-metni DAİMA Fable-seans (kurucu-oturumu — hukuki+itibari hassasiyet, ücretsiz model asla birincil)"
risk_sinifi: R1
tetik: "olay: kriz_tetiklendi — S1/S2'den SEV0-1 + kategori∈{veri-ihlali, uzun-kesinti, store-krizi} | manuel: kurucu/CEO 'kriz ilan et'"
girdi_semasi: "{ tetikleyen_sinyal_id, venture, kategori, sev(0/1), kanit_link, ilk_tespit_zamani, etkilenen_yuzeyler[] }"
cikti_semasi: "{ secilen_sablon_id, doldurulmus_metin{ic_kopru, kamu_taslak}, donma_kapsami[venture...], eskalasyon_hedefi, ne_asla_soylenmez_kontrolu{passed, ihlaller[]} }"
eskalasyon: "DAİMA CEO+CoS+Köprü Kanalı ANLIK; kamu-metninin YAYINLANMASI DAİMA kurucu (bu runbook'un R1 tavanı DIŞINDA, R3/R4); veri-ihlali kategorisinde privacy-data-guardian + legal-contracts-advisor önerisi ZORUNLU alan"
---
# Kriz İletişimi Runbook'u (B3 YULA Medya)

Workflow-seviyeli runbook — tek bir sayılı ajana değil, B3'ün 3 ajanına (27/28/29) ve CEO/CoS'a bağlanan olay-tetikli bir prosedürdür (plan EK-A: "ajan artışı yok"). Mevcut `ops/social-media/config/compliance.yml` kriz-filtresinden (kullanıcı DM/yorum seviyesi, zaten kurulu) AYRIDIR — bu runbook altyapı/olay-seviyesi (SEV0-1) krizleri kapsar: veri ihlali, uzun kesinti, store krizi.

## Görev tanımı

SEV0-1 bir kriz tespit edildiğinde dört şeyi yapar: (1) markalar-arası bulaşmayı DERHAL durdurur — etkilenen ve paylaşımlı-hesaplı venture'ların yayın kuyruğunu dondurur, (2) hazır tek-ses şablonundan iç Köprü Kanalı bildirimi + kamu-taslağı üretir, (3) "ne asla söylenmez" kontrolünü geçirir, (4) kamu-metninin YAYINLANMASINI kurucuya bırakır. Kendisi hiçbir zaman dış-yazma yapmaz — üretici≠yargıç ilkesi burada üretici≠yayıncı olarak uygulanır.

## KARAR TABLOSU — senaryo → ilk-aksiyon → dondurma kapsamı

| Senaryo/desen | Aksiyon | Severity/etiket |
|---|---|---|
| Supabase RLS/policy açığı nedeniyle tenant-arası veri sızıntısı şüphesi (Braavolabs çok-kiracılı model) | SEV0 — TÜM markaların yayın kuyruğu DONAR, veri-ihlali şablonu + privacy-data-guardian ZORUNLU eskalasyon | dondur-tum + eskale-hukuki |
| LifeOS/Burun Farkı Supabase'inde kişisel/sağlık verisi (TCKN, sağlık kaydı) expose olduğu tespit edildi | SEV0 — ilgili venture + paylaşımlı Apple/Play hesabı üyeleri donar, privacy-data-guardian ZORUNLU | dondur-paylasimli + eskale-hukuki |
| Lightsail kesintisi >2 saat (braavolabs backend + Burun Farkı retrain cron aynı instance'ta olabilir — `connections.yaml`: "AYNI/AYRI DOĞRULANMADI") | SEV1 — uzun-kesinti şablonu; kanıt netleşene dek TEDBİREN her ikisinin de kuyruğu donar | dondur-ikili |
| Vercel/site 5xx fırtınası >30dk (yulalab.com veya Burun Farkı web) | SEV1 — uzun-kesinti şablonu, ilgili marka kuyruğu donar | dondur-tekli |
| Apple `T5HZGYBWK8` hesabına politika ihlali/askıya-alma uyarısı (BF 2.3.6 reddi emsal-riski, `connections.yaml`) | SEV0 — store-krizi şablonu, hesabı paylaşan TÜM 8 üye (LifeOS+BF+Braavolabs+5 Motion) kuyruğu donar | dondur-tum + eskale-hukuki |
| Google Play hesap-geneli 2. uyarı ⏰2026-08-31 eşiğini geçti / submission engellendi | SEV0 — store-krizi şablonu, Android'i olan TÜM markalar donar | dondur-tum |
| Tek bir venture'da rutin store reddi (ör. bir K-tipi resubmit süreci, mevcut/olağan akış) | SEV2 — bu runbook'un eşiğinin ALTINDA, kriz İLAN ETME; normal Kesinti-nöbetçisi/masa akışına bırak | esik-alti-normal-akis |
| Sinyal kaynağı doğrulanmamış (tek bir kullanıcı yorumu, resmî mail/webhook DEĞİL) | Kriz İLAN ETME — S2 Değerlendirici'ye doğrulama iste, dondurma BAŞLATMA | esik-alti-dogrulama-bekle |
| **tabloda karşılığı olmayan HER durum** | ESKALE ET (asla kendi başına kriz ilan/iptal etme) | — |

## Hazır tek-ses şablonları

Üç senaryo × iki katman: **İÇ** (Köprü Kanalı, anında, tam detay) ve **KAMU** (taslak — kurucu onayı ŞART, kapsam doğrulanmadan gönderime HAZIR DEĞİL). Marka dili `brands.yml`'den miras alınır (Burun Farkı = TR + 18+ footer zorunlu; diğerleri EN/TR karışık).

**1) Veri ihlali**
- İÇ: "🔴 SEV0 — [venture] veri-ihlali şüphesi. Tespit: [zaman]. Kaynak: [kanit_link]. Etki kapsamı: BİLİNMİYOR, netleşene dek konuşma. Donan kuyruklar: [liste]. privacy-data-guardian + legal-contracts-advisor eskale edildi."
- KAMU (taslak): "[Ürün] için bir güvenlik olayını araştırıyoruz. Kapsamı doğruladıkça [kanal]'dan güncelleyeceğiz."

**2) Uzun kesinti**
- İÇ: "🟠 SEV1 — [venture] kesintisi [başlangıç_saati]'nden beri sürüyor. Etkilenen yüzey: [liste]. Kök-neden: ARAŞTIRILIYOR. Donan kuyruklar: [liste]."
- KAMU (taslak): "[Ürün] şu anda bir teknik sorun yaşıyor, ekip üzerinde çalışıyor. Güncelleme: [tahmini saat]."

**3) Store krizi**
- İÇ: "🔴 SEV0 — [Apple/Google] hesap-geneli [uyarı/ihlal türü]. Etkilenen ürünler (paylaşımlı hesap, `connections.yaml members`): [liste]. Donan kuyruklar: TÜMÜ."
- KAMU (taslak): genelde YAYINLANMAZ (store-içi süreç, Anayasa §4.2 "sonuçlanmamış detaylandırılmaz") — yalnız kullanıcı doğrudan sorarsa hazır kısa yanıt: "[Ürün] şu anda mağaza incelemesinden geçiyor, detay paylaşamıyoruz."

## Ne ASLA söylenmez

- Kapsam/etkilenen-kullanıcı-sayısı DOĞRULANMADAN rakam verilmez (tahmin = yasak, DNA kural 4).
- Düzeltilmemiş güvenlik açığının TEKNİK detayı asla paylaşılmaz (Anayasa §4.2).
- Sonuçlanmamış store süreci (ret/inceleme) detaylandırılmaz — yalnız "inceleniyor" serbest.
- Suçu üçüncü tarafa (Apple/Google/Supabase/hosting sağlayıcı) atma dili kurucu onayı olmadan kullanılmaz — doğrulanmamış suçlama hukuki risk yaratır.
- Kesin bir düzelme ETA'sı verilmez ("birkaç saat içinde düzelir" gibi doğrulanmamış vaat yasak) — yalnız "üzerinde çalışıyoruz, güncelleyeceğiz".
- Etkiyi küçümseyen/mizahi/rahatlatıcı-abartılı dil kullanılmaz (özellikle SEV0/veri-ihlalinde).
- Bir markanın kriz metni başka markanın ton/dil kuralına (Burun Farkı 18+ footer dahil) uyarlanmadan kopyalanmaz.
- Sorumluluk kabulü/itiraf niteliğinde ifade (ör. "hatalıydık", "tazminat ödeyeceğiz") kurucu+legal-contracts-advisor onayı olmadan yazılmaz.

## Markalar-arası bulaşma önleme (otomatik dondurma)

1. Kriz tetiklendiğinde (yukarıdaki tabloda `dondur-*` etiketli satır), bu runbook TÜM etkilenen venture'ların yayın kuyruğuna mevcut kontrol yüzeyini (company/pipeline pause-resume, plan §4.5) kullanarak R1-içi bir `pause` bayrağı yazar — bu DIŞ-YAZMA değildir, kendi kuyruğunu durdurmaktır.
2. Kapsam belirsizse (ör. paylaşımlı Lightsail/hesap netleşmemiş) TEDBİREN GENİŞ donar — dar açıp sonra genişletmek yerine geniş açıp daralt (fail-closed, DNA kural 6).
3. Dondurma SÜRESİZDİR — yalnız kurucunun Köprü Kanalı'nda verdiği açık "devam" onayıyla marka-marka açılır; **blanket-resume YOK**, her marka ayrı onay ister.
4. 29-SM-yayın-işçisi kendi karar tablosunda bu bayrağı kontrol eder (bkz. `29-sm-yayin-iscisi.md` — "AKTİF kriz-dondurma bayrağı" satırı); bayrak aktifken hiçbir gönderim geçmez, kuyruğa birikir.
5. Dondurma kaydı DEFTER'e düşer (hangi marka, ne zaman, hangi olay, ne zaman açıldı) — kanıtsız kapanış olmaz (DNA kural 1).

## Few-shot örnekler

1. **Girdi:** `{kategori:"uzun-kesinti", venture:"braavolabs", sev:1, kanit_link:"Uptime Kuma alert #482", ilk_tespit_zamani:"2026-08-02T14:10", etkilenen_yuzeyler:["braavolabs.com","platform API"]}` → **Çıktı:** `{secilen_sablon_id:"uzun-kesinti", doldurulmus_metin:{ic_kopru:"🟠 SEV1 — braavolabs kesintisi 14:10'dan beri sürüyor...", kamu_taslak:"Braavolabs şu anda bir teknik sorun yaşıyor..."}, donma_kapsami:["braavolabs","burun-farki"], eskalasyon_hedefi:"CEO+CoS+Köprü", ne_asla_soylenmez_kontrolu:{passed:true, ihlaller:[]}}` (Lightsail paylaşımı doğrulanmadığı için ikisi de donar)
2. **Girdi:** `{kategori:"veri-ihlali", venture:"lifeos", sev:0, kanit_link:"Supabase advisor alert", ilk_tespit_zamani:"2026-08-05T09:00", etkilenen_yuzeyler:["supabase_lifeos"]}` → **Çıktı:** `{secilen_sablon_id:"veri-ihlali", donma_kapsami:["lifeos","braavolabs","burun-farki"], eskalasyon_hedefi:"CEO+CoS+Köprü+privacy-data-guardian+legal-contracts-advisor", ne_asla_soylenmez_kontrolu:{passed:true, ihlaller:[]}}` (paylaşımlı Apple hesabı tedbiren donar)
3. **Girdi:** tek kullanıcı yorumu "sitem çöktü" (doğrulanmamış, tek kaynak, resmî sinyal yok) → **Çıktı:** kriz İLAN EDİLMEZ; `{secilen_sablon_id:null, donma_kapsami:[], eskalasyon_hedefi:"18-S2-Degerlendirici (doğrulama)"}`.
4. **Girdi:** Burun Farkı'nda rutin bir store resubmit süreci (K-tipi, olağan akış) → **Çıktı:** `{secilen_sablon_id:null, donma_kapsami:[], eskalasyon_hedefi:null}` — esik-alti-normal-akis, normal masa süreci devam eder.

## Kaçan-sinyal tanımı

(a) SEV0-1 bir olay yaşandığı halde kriz ilan edilmemesi / dondurma tetiklenmemesi, (b) dondurma sonrası bir markanın yanlışlıkla içerik gönderdiğinin tespit edilmesi, (c) kamu-taslağının "ne asla söylenmez" listesindeki bir ifadeyi (doğrulanmamış rakam/ETA/suçlama) içerdiği halde kontrolün `passed:true` döndürmesi — üçü de retro'da otomatik FAIL sayılır.

## Uzman eşiği

| Durum | Danışman |
|---|---|
| Kriz komuta, triage, post-mortem | `incident-commander` (BİRİNCİL, her SEV0-1'de otomatik öneri) |
| Veri ihlali kapsam/KVKK-GDPR beyanı | `privacy-data-guardian` |
| Kamu metninin hukuki riski (sorumluluk kabulü, iddia dili) | `legal-contracts-advisor` |
| Kriz-sonrası "normale dönüş" içeriği, ton tutarlılığı | `build-in-public-storyteller` |
| tabloda olmayan → ESKALE ET | Köprü Kanalı + kurucu-oturumu |

## Sınırlar

- ASLA kamu-metnini kendi başına yayınlamaz — yayın DAİMA kurucu (R3/R4, bu runbook'un R1 tavanı dışında).
- ASLA doğrulanmamış rakam/kapsam/ETA vermez.
- ASLA tabloda karşılığı olmayan bir severity kararını kendi muhakemesiyle tahmin etmez — eskale eder.
- ASLA dondurmayı kendi başına kaldırmaz — yalnız kurucu onayı marka-marka açar.
- Untrusted sinyal (tek kullanıcı yorumu, doğrulanmamış mail) DAİMA veri sayılır, otomatik kriz tetikleyici DEĞİLDİR — S0/S1'in resmî sinyal doğrulaması şarttır.
