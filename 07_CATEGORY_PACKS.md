# Prompt 7 — Generate the 16 Category Packs

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

## Normatif kaynak (v5)

- `docs/CATEGORIES.md` **tam metni** (A şema, B katman şablonları, C.1–C.16 kategori spesifikasyonları, D sözlük tohumları) ve `SOURCE_ORIGINAL.md`'nin C/D bölümleri **normatiftir**.
- Ajan 16 pack'i bu spesifikasyonlardan **birebir** üretir; özetle, generic politikayla veya kendi varsayımıyla yetinmez. "CATEGORIES.md şablonundan sapmayacak" kuralı bu tam metne bağlıdır.
- Alan adları `06_PACK_ENGINE.md` eşlemesiyle İngilizce kanonik yazılır; **içerik değerleri** (izinli/yasak kaynak listeleri, bölüm listeleri, yasak iddialar, zorunlu notlar, uzunluk min/ideal/max sayıları, güncelleme günleri) C.1–C.16'daki değerlerin birebir karşılığıdır — çeviri içerik değiştirmemelidir.

`prompts/packs/*.yaml` altında şu 16 pack'i üret: health, law, finance, crypto, technology, product_review, travel, real_estate, automotive, food, news, sports, education_career, pets, beauty, general_guide.

Her YAML, `06_PACK_ENGINE.md` şemasının bütün alanlarını doldurmalı ve en az şu kararları açıkça vermelidir: risk/YMYL, reviewer, auto-publish, first-hand, minimum/primary sources, max source age, permitted/forbidden source types, freshness, required sections, forbidden claims, mandatory notes, language/regional behavior, schema/image/link policy, research mode, insufficient-data behavior ve original contribution policy.

Zorunlu kategori bazlı içerik (C.1–C.16'dan aynen): health → Sağlık Bakanlığı, TİTCK, DSÖ, CDC/NIH/NHS, PubMed/Cochrane, uzmanlık derneği/TTB kılavuzları, min 3 kaynak min 2 birincil, kılavuz güncel sürüm / çalışmalar 5 yıl, acil durum kutusu; law → mevzuat.gov.tr, Resmî Gazete, Yargıtay/Danıştay/AYM arama sistemleri, madde/karar numarası doğrulama gate'leri; finance → TCMB, TÜİK, SPK, BDDK, Hazine ve Maliye, GİB, KAP, Borsa İstanbul, oran/fiyat ≤30 gün, hesap_doğrulama gate'i; crypto → whitepaper, resmî duyurular, zincir üstü gezginler, tahmin dili dedektörü; emlak → TKGM, TÜİK konut verileri, city_permutation gate'i; news → 24–72 saat tazelik, özgün habercilik unsuru zorunlu, NewsArticle şeması; product_review → gerçek test kriterleri, üretici metni kopyalama yasağı, ifşa notları. Diğer kategoriler için C.x satırları aynen.

Materializasyon görevleri:

- `prompts/global_rules.md`: CATEGORIES.md B.1'deki 20 global kural **aynen** yazılır; kilitli; kullanıcı düzenleyemez, yalnızca görüntüler.
- `prompts/templates/*.j2`: B.2–B.7 şablonları (system.j2, outline.j2, draft.j2, critique.j2, compliance.j2, metadata.j2) aynen materialize edilir.
- `lexicons/tr/`: D.1 → `health_claims.txt`, D.2 → `prediction_guarantee.txt`, D.3 → `clickbait.txt`, D.4 → `ai_artifacts_cliches.txt`, D.5 → `certainty_language.txt`; kullanıcı ekleme/çıkarma yapabilir.

Health/law/finance/crypto/real-estate/pets/beauty stricter validation kullanır. News freshness ve editorial review ister. Product review hands-on deneyim uyduramaz; affiliate content merchant copy'sini tekrar edemez.

Her pack için fixture, loader validation ve policy snapshot testi yaz. Her pack'in örnek brief, beklenen blocker ve reviewer davranışını da ekle. `tools/validate_packs.py`: 16 pack'i, şema alanlarını, YMYL invariant'larını (reviewer_required=true, auto_publish_allowed=false, min_sources>=3), first-hand value source zorunluluğunu ve İngilizce-kanonik anahtar denetimini doğrular.
