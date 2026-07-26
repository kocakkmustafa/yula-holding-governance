# yula-holding-governance

YULA AI Holding'in **anayasal katmanı**: ilkeler, risk matrisi, otonomi politikası, bütçe tavanları, karar kayıtları (ADR) ve orkestratör sözleşmeleri. Org/politika değişiklikleri burada **versiyonlu değişiklik** olarak yaşar (FABLE_PLAN §2A: kurucu direktifi → Karar Kaydı → commit).

## Yapı

```
anayasa/       # değişmez ilkeler + politikalar (yalnız kurucu kararı + denetim kaydıyla değişir)
kararlar/      # Karar Kayıtları (KK-YYYY-MM-DD-konu.md) — append-only mantığıyla
sozlesmeler/   # orkestratör rol sözleşmeleri (8-alan frontmatter)
```

## Kaynak hiyerarşisi

1. Bu repo'daki `anayasa/` — işletim kurallarının bağlayıcı hali.
2. `holding/plans/FABLE_PLAN.md` (v2.0, KABUL 2026-07-22) — plan/mimari; çelişkide anayasa maddesinin dayandığı FABLE_PLAN bölümü kazanır.
3. Kurucu El Kitabı (PDF + `EL-KITABI-GUNCELLEME-EKI-2026-07-22.md`) — arka plan/gerekçe.

## Değişmez üst-kurallar (özet — detay anayasa/)

- **R4/R5 daima kurucu:** prod deploy · store submit · fiyat/ödeme · veri silme · ana dala push · secrets · yetki yükseltme. Bu sınır otonomiye HİÇ açılmaz.
- **Hiçbir ajan kendine yetki veremez** (self-grant yasak); yükseltilmiş yetki = R5.
- **Abonelik kotası yalnız YULA-içi iş** — müşteri-yüzü execution = BYOK/metered.
- **Iron Bank holding dışıdır** ve hiçbir build-in-public içeriğine girmez.
- Bütçe tavanları güvenlik ağıdır; ajan değiştiremez.
