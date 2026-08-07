# Anayasa §2 — Otonomi Politikası (v1)

**Kaynak:** Kurucu kararı 2026-07-22 ("risk-bazlı MAKSİMUM otonomi, baştan; süre pini yok") + El Kitabı Böl.31. Otonomi **ajana değil, kanıtlanmış workflow'a** verilir.

## Otonomi seviyeleri (workflow bazında)

| Seviye | Anlam |
|---|---|
| L0 | Yalnız öneri üretir, hiçbir eylem yok |
| L1 | Eylemi hazırlar, insan uygular |
| L2 | Eylemi uygular, HER run insan-onaylı |
| L3 | Merdivendeki aday: ilk 20 run insan-onaylı, metrikleri sayılır |
| L4 | Otomatik, örneklem-denetimli (Muhafız haftalık örneklem alır) |
| L5 | Tam otonom + kendi alt-görev üretimi — **yalnız R0-R1 iş sınıfında mümkündür** |

## Kurallar

1. **R0-R1:** ilk günden L4-L5 (okuma, rapor, taslak, etiket, issue, test).
2. **R2:** onaylı şablon + K0/K1 kompanzasyon kapısından geçen akışlar İLK GÜNDEN otonom; şablon+kapı seti bir kez kurucu onayı alır.
3. **R3 merdiveni (sayı, süre değil):** ilk 20 run insan-onaylı → **≥%90 onay + 0 kritik hata + test edilmiş rollback + AI-etiket uyumu %100** → o workflow L4'e terfi. 20 temiz run 2 haftada gelirse otonomi 2 haftada açılır.
4. **Demotion:** L4 workflow'da Muhafız örnekleminde 1 kritik hata → otomatik L3; merdiven baştan.
5. **R4/R5:** hiçbir seviyeye açılmaz — daima kurucu (bkz. §1).
6. **Kendini genişletme:** sistem skill/workflow/alt-ajan üretebilir (önce-kendi-ürünümüz kuralı — 2026-08-07: Fable Mental + The Repo God + kurulu envanter — canlı sayılar `holding/registry/capabilities.yaml`'da). SERT SINIR: üretilen hiçbir ajan kendine yetki veremez; kalıcı ajan güvenli-varsayılan yetkiyle (read + iç-yazma) doğar; yükseltme = R5. Kalıcı ajan/workflow üretimi Capability Registry kaydı + sandbox/test + **günlük brief'te kurucuya bilgi** (bilgilendirme, onay değil) gerektirir. 90 gün kullanılmayan üretilmiş varlık oto-arşiv.
7. **Kurucu-erişilemez degradasyonu:** 72 saat yanıtsız → R0-R2 + L4 akışlar devam; R3-merdiven ve R4/R5 DONAR; SEV0-1'de otomatik-güvenli aksiyon (restart + rollback-to-last-tag) + bildirim.
8. **Onay UX:** Telegram tek-tık (durum+neden+etki+seçenek); onaylar kuyruk + günde 2 pencere; senkron kesinti yalnız R4+/SEV0-1.
