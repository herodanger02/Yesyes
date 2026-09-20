# CHECKLIST.md — Source-of-Truth Policy (özet / işaretçi)

> Bu dosya özettir; **normatif metin `docs/CHECKLIST.md` tam halidir** (bölüm 1–26). Çelişki hâlinde tam metin kazanır.

Bu dosya uygulamanın evrensel kontrol kaynağıdır. Rule type: OTO=deterministic code, LLM=model scoring/evidence, İNS=human-only, KRM=machine/LLM flag plus human approval, **MYTH=bilgi paneli (kural değildir)**. Severity E=blocker, U=reasoned warning, B=information. Conditional rules can be N/A.

Immutable: ranking/traffic/indexing guarantee yok; word count, AI-detector, keyword density kalite gate'i değil; source copying, fake identity/experience/citation, unsupported claim, cloaking, doorway, paid ranking links, fake freshness, fake human approval yok.

Zorunlu rule groups ve ID aralıkları: ST-01..ST-14; DE-01..DE-25; KA-01..KA-12; GU-01..GU-14; YM-01..YM-12; **BA-01..BA-13**; YA-01..YA-14; AK-01..AK-12; IL-01..IL-09; DL-01..DL-10; AF-01..AF-09; GO-01..GO-12; VI-01..VI-07; TE-01..TE-17; SD-01..SD-10; SV-01..SV-06; SP-01..SP-19; AS-01..AS-20; ED-01..ED-12; QA-01..QA-11; PS-01..PS-14; GB-01..GB-05; PF-01..PF-10; ON-01..ON-06; **GY-01..GY-15 (MYTH — kural olarak eklenmez, Ayarlar'da bilgi paneli)**.

Parser, registry and coverage audit tüm ID'leri korumalı ve `13_CHECKLIST_ENGINE.md`'deki bölüm manifestosuyla sayı doğrulaması yapmalıdır. Uygulama bilinmeyen ID'yi sessizce yok sayamaz.
