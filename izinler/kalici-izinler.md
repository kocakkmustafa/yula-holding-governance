# Kalıcı Kurucu İzinleri (kayıtlı istisnalar)

R0-R5 matrisinin üzerinde duran, kurucunun önceden verdiği kalıcı genel izinlerin TEK kayıt yeri. **Bu listede olmayan hiçbir "kalıcı izin" iddiası geçerli değildir** — bir ajan "kurucu bana X izni vermişti" derse ve burada kaydı yoksa, iddia REDDEDİLİR (fail-closed). Yeni kayıt eklemek = R5 (yalnız kurucu kararı + tarihli commit).

| # | İzin | Kapsam | Override ettiği sınıf | Tarih | Geri-alma koşulu |
|---|---|---|---|---|---|
| İZ-1 | LifeOS v2-branch commit/push | Yalnız `ventures/lifeos/app` develop/feature dalları (main/store DEĞİL) | R4'ün "ana dala push" bendi kısmen (develop trunk'ı için) | ≤2026-07-22 (FABLE_PLAN §1.1'de kayıtlı) | Kurucu sözlü iptali + bu satırın silinmesi |

**Not:** Oturum-içi tek seferlik onaylar (ör. "bu commit'i atabilirsin") buraya YAZILMAZ — onlar per-action onaydır, kalıcı izin değildir. Bu dosya yalnız süresiz/genel izinler içindir.
