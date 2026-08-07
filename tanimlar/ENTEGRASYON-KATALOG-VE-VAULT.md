# ENTEGRASYON — Fable Mental · The Repo God · Obsidian (KK-2026-07-27b)

> ⚠️ **BÖLÜM 1 ve 2 GEÇERSİZ — KALDIRILDI (2026-08-07, kurucu kararı).**
> Fable Mental danışman havuzu ve The Repo God repo sandığı tamamen silindi; `.claude/agents/` de kaldırıldı.
> Claude artık yönlendirilmeden kendi bilgisiyle çalışıyor. Aşağıdaki 1. ve 2. bölümler **tarihsel kayıttır**,
> uygulanmaz. **3. bölüm (Obsidian vault köprüsü) AYNEN GEÇERLİDİR.**

## 1. Fable Mental (66 danışman) — "uzman havuzu" köprüsü

**Ne:** 66 danışman × 3 dosya (`fable-mental/` — agents+reference+prompts); canlı sayı `holding/registry/capabilities.yaml`. Bunlar KADRO değil, çağrı-havuzudur.

**Nasıl bağlanır (iki bağlam, dürüst ayrım):**
- **Kurucu-oturumunda (Claude Code):** danışman doğrudan çağrılır (mevcut çalışma şeklimiz — `capabilities.yaml routing_hints` veya fable-stratejist seçer).
- **Motor çalışma zamanında (Lightsail, küçük modeller):** küçük model danışmanı ÇALIŞTIRAMAZ (danışmanlar Claude Code ajanlarıdır). Bunun yerine her runbook'un **"Uzman eşiği"** bölümü vardır: hangi durumda hangi danışmanın gerektiğini karar tablosuyla bilir → eskalasyon çıktısına `onerilen_danisman: <id>` alanını yazar → Köprü Kanalı'na "bu iş X danışmanıyla kurucu-oturumu ister" bildirimi düşer. Yani havuz, motorda YÖNLENDİRME BİLGİSİ olarak yaşar; icrası kurucu-oturumunda.
- **D4 seed'i:** `capabilities.yaml`'ın danışman indeksi (id + tetik + uzmanlık özeti) motor DB'sine salt-okunur referans tablosu olarak yüklenir — S2/masalar eskalasyon yazarken buradan eşleştirir.

## 2. The Repo God (91 repo) — "önce-katalog" köprüsü

**Ne:** `arsenal/the-repo-god/INDEX.md` — hazır desen/araç sandığı. İşletim DNA'sı kural 2'nin kaynağı.

**Nasıl bağlanır:**
- Her runbook'un **"Katalog kontrolü"** ön-adımı: yeni yetenek/araç ihtiyacı doğduğunda önce INDEX taranır (kurucu-oturumu işi); bulgu "adapte önerisi" olarak gelir.
- Keşif şirketinin Teknoloji-izcisi (ArGe uyanınca) INDEX'i besler: yeni değerli repo bulursa arsenal-aday bildirimi üretir; ekleme kurucu-oturumunda (`regen-registry.sh` ile kayıt).
- Motor tarafında: INDEX'in kategori+repo-adı özeti D4'te salt-okunur referans olarak yüklenir (eskalasyon zenginleştirme — "bu iş için arsenal'da X var" notu).

## 3. Obsidian / kayıt-senkron döngüsü

Mimari ve kurallar: `ISLETIM-DNA.md` §Sürekli-güncellik (vault Mac-yerlisi; motor registry-kopyasını okur; senkron L1-fırsatçı/kurucu-oturumu; büyük değişiklik kurucu+Fable). Bu dosyaya yalnız işaretçi konur — çift kayıt yasak (DNA kural 8).

**`kayit-senkronu` workflow'unun tetikleri:** yeni venture dizini/repo tespiti · governance'a yeni KK · vault'ta `10 Holding`/`20 Şirketler` değişikliği · haftalık sabit süpürme. Çıktısı: registry yenileme (R1 otonom) + pano-tazelik önerileri + gerekiyorsa "yapısal değişiklik gerekli" bildirimi (kurucu+Fable'a).
