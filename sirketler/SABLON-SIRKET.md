# ŞİRKET TANIM ŞABLONU (her sirketler/*.md bu yapıyı izler)

```markdown
---
id: <a1-lifeos | b1-gozcu ...>
kat: A | B
durum: aktif | yari-aktif | uykuda
faz: F1 | F2 | F3 | uyanma-kosulu
ajanlar: [runbook id listesi]
---
# <Şirket adı>

## Kimlik ve amaç        (2-4 cümle: ne yapar, neden var)
## Varlıklar ve bağlar   (repolar/hesaplar/servisler — registry referanslı; A-şirketlerinde canlı yüzeyler)
## İzleme hedefleri      (Gözcü'nün bu şirket için dinlediği sinyaller; A-şirketleri) VEYA Hizmet kapsamı (B)
## Workflow'ları         (workflows.yaml'daki key'ler + tetik/kadans)
## Feedback döngüsü      (haftalık retro metrikleri — DNA kural 1; şirkete özgü "kaçan sinyal" tanımı)
## Sınırlar              (bu şirketin ASLA yapmadıkları — fail-closed liste)
## Uzman eşiği           (hangi durum → hangi Fable Mental danışmanı; routing_hints'ten)
```

Kurallar: İşletim DNA'sının 10 kuralı her şirkete otomatik uygulanır (tekrar yazılmaz, çelişilmez). Uykuda şirketlerde "İzleme hedefleri" yerine **"Uykuda görevleri"** + **"Uyanma koşulu + uyanış kontrol listesi"** bölümleri yazılır.
