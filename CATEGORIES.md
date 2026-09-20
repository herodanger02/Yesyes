# CATEGORIES.md — Category Pack Contract (özet / işaretçi)

> Bu dosya özettir; **normatif metin `docs/CATEGORIES.md` tam halidir** (A şema, B katman şablonları, C.1–C.16, D sözlükler). Çelişki hâlinde tam metin kazanır.

Her kategori YAML'ı `06_PACK_ENGINE.md`'deki **İngilizce kanonik** alanların tamamını içermelidir (Türkçe adlar takma addır; eşleme 06'dadır).

YMYL=true ise reviewer_required=true, auto_publish_allowed=false, min sources >=3. First-hand zorunluysa value source olmadan üretim yok. Tüm kategoriler global immutable rules taşır ve yetersiz veride yazmaz.

16 pack: health, law, finance, crypto, technology, product_review, travel, real_estate, automotive, food, news, sports, education_career, pets, beauty, general_guide. Kategori-specific source policy, freshness, reviewer, prohibited claims, sections, schema, image/link and publication behavior zorunludur ve `docs/CATEGORIES.md` C.x satırlarından aynen alınır.

Özgün katkı alanı commodity content'i tespit eder; yetersizse insan incelemesine yönlendirir. Pack loader eksik/yanlış/bilinmeyen alanı reject eder, version ve policy hash'i kaydeder.
