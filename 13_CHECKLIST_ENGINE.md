# Prompt 13 — Checklist Engine

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

`docs/CHECKLIST.md` tam metni tek gerçek kaynak, `checklist.yaml` machine-readable registry olmalıdır. Her kuralın id, section, title, type (`OTO`, `LLM`, `İNS`, `KRM`, `MYTH`), severity (`E`, `U`, `B`), applies_to, decision_layer, automation mode, deterministic, evidence_required, cannot_decide_alone ve source metadata'sı bulunmalıdır.

OTO deterministic kod kontrolüdür. LLM score/explain/flag/suggest yapar ancak insan-only policy kararını tek başına finalize edemez. İNS yalnız insan onayıdır. KRM otomatik/LLM bulgusu sonrası insan kararıdır. E blocker, U gerekçeli warning, B information'dır. Conditional rule N/A olabilir.

## GY grubu — mitler / bilgi paneli (v5)

`GY-01..GY-15` satırları **kalite kuralı değildir** ve bulunmamalıdır deneyin maddelerdir. Parser bunları `MYTH` türüyle korur; findings üretmez, gate açmaz. Uygulama bunları Ayarlar'da "bilgi paneli" olarak gösterir. Coverage audit, GY maddelerinin **özellik olarak uygulanmadığını** da doğrular: llms.txt üretici yok, AI chunking özelliği yok, meta keywords alanı yok, kelime sayısı/başlık sayısı hedefi yok.

## Bölüm manifestosu (v5)

Parser, ayrıştırılan kural sayılarını bu manifestoyla doğrular; uyuşmazlık hatadır, sessizce atlanmaz:

| Bölüm | Aralık | Adet |
|---|---|---|
| ST | ST-01..ST-14 | 14 |
| DE | DE-01..DE-25 | 25 |
| KA | KA-01..KA-12 | 12 |
| GU | GU-01..GU-14 | 14 |
| YM | YM-01..YM-12 | 12 |
| BA | BA-01..BA-13 | 13 |
| YA | YA-01..YA-14 | 14 |
| AK | AK-01..AK-12 | 12 |
| IL | IL-01..IL-09 | 9 |
| DL | DL-01..DL-10 | 10 |
| AF | AF-01..AF-09 | 9 |
| GO | GO-01..GO-12 | 12 |
| VI | VI-01..VI-07 | 7 |
| TE | TE-01..TE-17 | 17 |
| SD | SD-01..SD-10 | 10 |
| SV | SV-01..SV-06 | 6 |
| SP | SP-01..SP-19 | 19 |
| AS | AS-01..AS-20 | 20 |
| ED | ED-01..ED-12 | 12 |
| QA | QA-01..QA-11 | 11 |
| PS | PS-01..PS-14 | 14 |
| GB | GB-01..GB-05 | 5 |
| PF | PF-01..PF-10 | 10 |
| ON | ON-01..ON-06 | 6 |
| GY | GY-01..GY-15 | 15 |

Exact keyword title, density, arbitrary word count, AI probability, one heuristic similarity, UA farkı veya self-canonical tek başına absolute blocker değildir. Similarity evidence'tir; tek heuristikten plagiarism ilan edilmez.

Coverage audit her rule ID'nin code/UI/test mapping'ini arar; her makalenin tüm conditional/human rule'ları sıfırlamasını beklemez. İnsan approval asla fake edilemez.

Ayrıştırılamayan satırlar sessizce atlanmaz; hata raporu üretilir. Bilinmeyen ID yok sayılamaz.
