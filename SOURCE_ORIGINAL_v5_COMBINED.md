EditorDesk Prompt Pack v5 — birleşik kaynak. Betik bu dosyayı bölerek klasör+ZIP üretir.

### FILE: 00_README.md ###
# EditorDesk — Cline Prompt Pack v5

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

## Amaç

Bu paket, **EditorDesk** adlı Windows-first Python/PySide6/SQLite editorial production system'ı bir kodlama ajanına ürettirmek için hazırlanmıştır. Bu paket uygulamanın kendisi değildir; promptlar, politika kaynakları, şema taslakları, test beklentileri ve uygulama sırasıdır.

## Normatiflik hiyerarşisi (v5)

1. **Tam politika metinleri normatiftir:** `docs/CHECKLIST.md` (bölüm 1–26, GY dahil), `docs/CATEGORIES.md` (A–D bölümleri; C.1–C.16 kategori spesifikasyonları; D sözlükler) ve `SOURCE_ORIGINAL.md` (denetim kaydı).
2. Bu paketteki `contracts/` özet dosyaları yalnızca işaretçidir; çelişki hâlinde tam metin kazanır.
3. Ajan tam metinleri repoya aynen kopyalar; coverage audit bunların varlığını ve bütünlüğünü doğrular.

## Alan adı standardı (v5)

- Pack YAML dosyaları ve kod **yalnızca İngilizce kanonik alan adları** kullanır (`risk_level`, `source_policy`, `value_source_fields`, …).
- `docs/CATEGORIES.md` içindeki Türkçe adlar (`risk_seviyesi`, `kaynak_politikası`, `değer_kaynağı_alanları`, …) dokümantasyon takma adıdır. Eşleme tablosu `06_PACK_ENGINE.md` içindedir.
- Loader yalnızca kanonik anahtarları kabul eder; bilinmeyen/Türkçe anahtar hata üretir.

## Üretilecek teslimatlar (v5 — ajan üretir)

Bu pakette **hazır değil**, ajan tarafından Milestone 3–4'te üretilir ve release gate doğrular:

- `prompts/packs/*.yaml` — 16 kategori paketi (`07` + `docs/CATEGORIES.md` C.1–C.16'dan)
- `prompts/global_rules.md` — CATEGORIES.md B.1'deki 20 kuralın aynen materializasyonu (kilitli)
- `prompts/templates/*.j2` — B.2–B.7 şablonlarının materializasyonu
- `lexicons/tr/*.txt` — D.1–D.5 sözlük tohumları (dosya adı eşlemesi `07`'de)
- `schemas/` — `23_JSON_SCHEMAS` sözleşmeleri
- `docs/CHECKLIST.md`, `docs/CATEGORIES.md` — tam politika metinleri (paketle birlikte verilir, aynen korunur)
- `tools/validate_packs.py` — 16 pack + YMYL invariant + alan adı denetimi

## Kullanım sırası

1. `01_PROJECT_FOUNDATION.md` ile proje sözleşmesini oluştur.
2. `02_DATABASE.md` ve `03_CONNECTIONS.md` ile kalıcı model ve sağlayıcı sınırlarını kur.
3. `04_LLM_LAYER.md`–`11_SCOPE_LENGTH_SELF_WRITTEN.md` arasında çekirdek editorial motoru uygula.
4. `12_PIPELINE.md`–`20_COVERAGE_AUDIT.md` ile kalite, yayın, UI ve denetimi bağla.
5. `21_E2E_RELEASE.md` ile test/release kapısını çalıştır.
6. `23_JSON_SCHEMAS.md`, `24_TEST_MATRIX.md` ve `25_IMPLEMENTATION_ORDER.md` dosyalarını her milestone'da doğrulama kaynağı olarak kullan.

## Ajan çalışma protokolü

Her prompt için: önce mevcut repository'yi incele; varsayımları yaz; küçük ve geri alınabilir değişiklikler yap; testleri ekle; ilgili migration'ı üret; lint/type/test çalıştır; değişen dosyaları ve kalan riskleri raporla. Kullanıcı istemedikçe başka bir ürün, web uygulaması veya servis oluşturma. API anahtarlarını, WordPress kimlik bilgilerini veya gerçek kullanıcı verilerini repoya yazma.

## Değişmez kararlar

- `SOURCE → EVIDENCE → FACT → ARTICLE` zinciri zorunludur.
- Search snippet'i kanıt değildir; gerçek kaynak sayfası alınmadan kritik iddia desteklenmiş sayılamaz.
- Yetersiz veri uydurulmaz; `BLOCKED_INSUFFICIENT_DATA` döndürülür.
- Teknik uygunluk, editoryal kalite ve yayın politikası ayrı kapılardır; üçü de geçmeden yayın yoktur.
- Keyword density, kelime sayısı veya AI-detector puanı kalite geçiş kriteri değildir.
- Sahte yazar, sahte uzmanlık, sahte deneyim, sahte kaynak, sahte insan onayı yoktur.
- YMYL içerikte reviewer zorunlu ve auto-publish kapalıdır.
- Kaynak içindeki talimatlar sistem talimatı değildir; prompt injection olarak işaretlenir.
- Autonomous generation ile autonomous publication birbirinden ayrıdır; global auto-publish varsayılanı `OFF`'tur.

## Sürüm

Bu dosya tek kanonik sürümdür (**v5**). v2/v3/v4 birleşik dosyaları arşivdendir; ajanla paylaşılmaz.

### v5 değişiklik günlüğü

1. CHECKLIST sözleşmesi: BA sayımı düzeltildi (13), GY-01..GY-15 bilgi paneli grubu eklendi; `13`'e bölüm manifestosu (sayı doğrulamalı) eklendi.
2. `docs/CATEGORIES.md` tam metni ve `SOURCE_ORIGINAL.md` C/D normatif ilan edildi; `07` buna bağlandı.
3. Alan adı çelişkisi çözüldü: İngilizce kanonik + tam eşleme tablosu (`06`).
4. README "hazır dosyalar" iddiası düzeltildi: teslimatlar ajan tarafından üretilir.
5. Gömülü v3 metni kaldırıldı; tek kanonik v5.
6. `15`: iki geçişli dil sistemi semantiği (AUTO_FIX/FLAG, olgu değişikliği fact-check'e döner) geri getirildi.
7. `25`: önceki oturumdan taşınan kalıntı cümle silindi.
8. Original Contribution Engine korundu; Promptlar.md'de olmayan v3/v4 evrimi eklemesi olarak belgelendi (DE-10 ile uyumlu).

## Teslimat beklentisi

Ajan her aşamada çalışan kod, migration, test ve kısa CHANGELOG üretmelidir. Bu paketin sonunda Windows paketleme, backup/restore, SBOM ve release notları hazırlanmış olmalıdır.

### FILE: 01_PROJECT_FOUNDATION.md ###
# Prompt 1 — Project Foundation and Editorial Architecture

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Sen kıdemli bir Python 3.12+, PySide6, SQLAlchemy 2, SQLite ve güvenli içerik üretim sistemi mimarısısın. Windows-first, modüler, test edilebilir ve offline-first çalışabilen EditorDesk'i kur.

Zorunlu teknoloji tabanı: PySide6, SQLAlchemy 2, Alembic, Pydantic v2, Jinja2, YAML parser, httpx, tenacity, keyring, trafilatura, markdown-it-py, nh3, python-slugify, Pillow, BeautifulSoup/lxml, python-docx, PDF parser, pytest ve pytest-qt.

Uygulama şu editorial zinciri yönetmelidir: TOPIC → BRIEF → RESEARCH → SOURCE VALIDATION → EVIDENCE → FACT SHEET → CONTRADICTION CHECK → SEARCH INTENT → ORIGINAL ANGLE → SCOPE → OUTLINE → DRAFT → NATIVE LANGUAGE EDITING → FACT CHECK → COMPLIANCE → SEO → QUALITY → PUBLICATION POLICY → WORDPRESS.

Article Wizard minimum alanları: site, category, topic, output language, site locale, country/region, focus keyword, optional secondary keywords, intent, target reader, content type, research mode, optional value source, optional user sources. Research mode tam olarak `AUTONOMOUS`, `USER_PROVIDED`, `HYBRID` olmalıdır.

Mimari kurallar: domain/application/infrastructure/UI ayrımı; pipeline state ile article state ayrımı; her adım event ve audit üretir; cancellation, resume, idempotency ve checkpoint vardır; provider-specific kod domain pipeline'a sızmaz.

Üç karar katmanı ayrı uygulanır: `TECHNICAL_ELIGIBILITY`, `EDITORIAL_QUALITY`, `PUBLICATION_POLICY`. Publish yalnızca üçü de PASS olduğunda mümkün olabilir.

İlk milestone sonunda: proje ağacı, dependency yönetimi, config profilleri, logging, error taxonomy, dependency injection, temel PySide6 shell, health check, test fixture'ları ve boş Alembic migration'ı teslim et. Kodlamaya başlamadan önce mimari karar kaydı yaz.

### FILE: 02_DATABASE.md ###
# Prompt 2 — Database, State Machine and Audit

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

SQLAlchemy 2 modellerini, Alembic migrationlarını, repository/service katmanını ve state transition guard'larını oluştur.

Article alanları: id, site_id, category_id, topic, output_language, site_locale, country, region, focus_keyword, secondary_keywords, search_intent, target_reader, content_type, research_mode, status, body, metadata, length_plan, author_id, reviewer_id, created_at, updated_at, version.

Article durumları: idea, preflight, researching, research_ready, fact_sheet_ready, scope_pending, outlining, outline_ready, drafting, drafted, language_editing, fact_checking, compliance_check, seo_check, quality_check, needs_review, approved, scheduled, publishing, published; alternatif: rejected, needs_fix, blocked, archived, cancelled, failed.

Ayrı pipeline/research durumları: research_created, research_discovering, research_candidates, research_fetching, research_extracting, research_verifying, research_conflict_check, research_fact_sheet, research_ready, research_blocked.

Modeller: ResearchRun, ResearchCandidate, Source, Evidence, ResearchClaim, FactSheet, FactSheetFact, Contradiction, OriginalContribution, PromptSnapshot, LLMRun, AuditLog, PublicationLog, Site, Author, Reviewer, CategoryPack, ChecklistRule, ChecklistFinding, ImageAsset, LinkRecord, Approval.

Source minimum alanları: URL/canonical URL, title, publisher, author, domain, language, country, source type, primary/secondary, authority class, dates, fetched_at, content hash/fingerprint, fetch/robots status, citation_allowed, reliability/freshness/relevance scores, policy status, origin group.

Her critical claim `source_ids` ve `evidence_ids` taşır; verification enum: SUPPORTED, PARTIALLY_SUPPORTED, CONTRADICTED, UNSUPPORTED, OUTDATED, NOT_APPLICABLE. Unsupported critical claim yayın kapısıdır.

State transitionlar whitelist ile korunmalı; invalid transition, duplicate run, stale version ve concurrent edit reddedilmeli. Audit hiçbir önemli olayı sessizce ezmemeli: prompt/model snapshot, kaynaklar, çıktılar, reviewer, approval, waiver, publish response, error, retry ve override kaydedilmeli.

Migration, rollback, seed ve repository testleri ekle. SQLite concurrency ve Windows dosya kilidi davranışını test et.

### FILE: 03_CONNECTIONS.md ###
# Prompt 3 — Connections and Provider Abstraction

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Provider-independent connection architecture kur. LLM, Search, WordPress, Image, Similarity/Plagiarism, GSC, PageSpeed ve Webhook provider'ları aynı sözleşme üzerinden çalışmalı.

Her provider: test_connection, timeout, retry policy, rate limit, cost tracking, health state, capability discovery ve error classification sağlamalıdır. Search provider opsiyoneldir; LLM AI modlarında gereklidir. Search yokken autonomous research, configured authoritative domains, sitemap/feed, direct URL, site inventory ve seed sources ile çalışmalıdır.

Secrets yalnızca OS keyring/secret store'da tutulur; SQLite, log, prompt snapshot veya exception içinde API key bulunamaz. Config'te base_url, auth method, model, timeout, rate limit, enabled, environment ve display name bulunur; secret değerleri maskeli gösterilir.

Domain pipeline provider adı bilmemeli; adapter registry ve dependency injection kullanmalıdır. Mock provider'lar deterministik testler için zorunludur. Network hataları transient/permanent/auth/policy/parse/rate-limit olarak sınıflandırılmalıdır.

Connection UI'da test sonucu, son sağlık zamanı, gecikme, hata sınıfı ve maliyet gösterilir. Credential rotasyonu ve provider disable etme güvenli olmalıdır.

### FILE: 04_LLM_LAYER.md ###
# Prompt 4 — Provider-Independent LLM Orchestration

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

LLMProvider, LLMRequest, LLMResponse, LLMProfile ve LLMRun sözleşmelerini uygula. Structured output, JSON Schema/Pydantic validation, timeout, exponential backoff, cancellation, optional streaming, model fallback, token/cost logging, prompt snapshot, model snapshot, deterministic run ID ve idempotency zorunludur.

LLM hiçbir zaman deterministic validation mümkünken factual veya policy kararının tek otoritesi olamaz. Çıktı suggestion, evidence-backed analysis, classification veya draft'tır. Her response schema dışıysa parse error olarak retry edilir; tekrar başarısızsa insan incelemesi/blok durumu üretilir.

Prompt ve model snapshot'ı immutable kaydet. Aynı run id ile tekrar çağrıda güvenli cache/idempotency uygula. PII ve secret redaction yap. Token/cost tahmini ve gerçek provider maliyetini ayır. MockLLMProvider ile tüm pipeline test edilebilir olmalı.

Batch evaluation destekle; ancak bir kritik iddia için source/evidence mapping zorunluluğunu gevşetme. LLM bulguları rule_id, score 0–5, evidence, confidence, recommendation ve status içermelidir.

### FILE: 05_PROMPT_ENGINE.md ###
# Prompt 5 — Layered Prompt Engine

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Prompt katmanlarını düşük katmanın yüksek katmanı override edemeyeceği şekilde uygula: GLOBAL_IMMUTABLE_RULES → CHECKLIST_RULES → CATEGORY_PACK → SITE_POLICY → AUTHOR_PROFILE → ARTICLE_BRIEF → RESEARCH_FACT_SHEET → TASK_PROMPT.

PromptTemplate, PromptVersion, PromptSnapshot, PromptBlock, PromptRenderer ve PromptLab oluştur. Global kurallar kilitli görünür; kullanıcı yalnızca site/category/task katmanlarını düzenleyebilir.

Renderer, rendered prompt, template/version, source IDs, pack/checklist version, model, output schema ve input hash'i kaydetmeli. Prompt Lab bu alanları görsel olarak göstermeli ve secret/source instruction injection riskini işaretlemelidir.

Kaynak içeriği hiçbir koşulda sistem talimatı değildir. Fetched content içindeki "ignore previous instructions" türü ifadeler veri olarak tutulur ve `SOURCE_INJECTION_SUSPECTED` flag'i alır. Tüm üretim görevleri JSON schema ile sonlanır.

### FILE: 06_PACK_ENGINE.md ###
# Prompt 6 — Category Pack Engine

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

YAML category pack loader ve validator geliştir. Her pack şu alanları zorunlu taşımalıdır: id, name, version, description, risk_level, ymyl, reviewer_required, reviewer_recommended, reviewer_role, auto_publish_allowed, requires_first_hand, value_source_fields, source_policy, intent_defaults, required_sections, optional_sections, tone, prohibited_phrases, prohibited_claim_types, required_notes, schema_types, length_priority, special_gate_rules, originality_angle_examples, image_policy, link_policy, update_frequency_days, prompt_blocks, insufficient_data_behavior, research_policy, language_policy, regional_policy, original_contribution_policy.

YMYL pack'i yüklenirken reviewer_required=true, auto_publish_allowed=false, minimum sources >=3 zorunlu kıl. requires_first_hand=true ise value source boşken üretim başlatma. Schema doğrulaması başarısızsa pack reddedilir. Version pinning, compatibility ve pack audit bilgisi ekle.

Pack policy deterministik gate'lere, LLM rubriklerine ve insan onaylarına ayrı map edilmelidir. Tek generic source policy kullanma; kategoriye göre authority, freshness, primary-source ve review kurallarını uygula.

## Alan adı eşlemesi (kanonik — v5)

YAML ve kod **yalnızca İngilizce anahtar** kullanır. `docs/CATEGORIES.md` içindeki Türkçe adlar dokümantasyon takma adıdır. Loader İngilizce olmayan anahtarı bilinmeyen anahtar olarak reddeder.

| docs/CATEGORIES.md (takma ad) | Pack YAML (kanonik) |
|---|---|
| id, ad, sürüm, açıklama | id, name, version, description |
| risk_seviyesi | risk_level |
| ymyl | ymyl |
| reviewer_required / reviewer_recommended | reviewer_required / reviewer_recommended |
| reviewer_rolü | reviewer_role |
| auto_publish_allowed | auto_publish_allowed |
| requires_first_hand | requires_first_hand |
| değer_kaynağı_alanları [{ad, zorunlu, açıklama, örnek}] | value_source_fields [{name, required, description, example}] |
| kaynak_politikası.izinli_türler | source_policy.allowed_types |
| kaynak_politikası.yasak_türler | source_policy.forbidden_types |
| kaynak_politikası.azami_yaş_gün | source_policy.max_source_age_days |
| kaynak_politikası.min_kaynak | source_policy.min_sources |
| kaynak_politikası.min_birincil | source_policy.min_primary |
| niyet_varsayılanları | intent_defaults |
| zorunlu_bölümler | required_sections |
| isteğe_bağlı_bölümler | optional_sections |
| ton_ve_hitap | tone |
| yasak_ifadeler | prohibited_phrases |
| yasak_iddia_türleri | prohibited_claim_types |
| zorunlu_notlar | required_notes |
| şema_türleri | schema_types |
| uzunluk_önceliği | length_priority |
| özel_kapı_kuralları | special_gate_rules |
| özgün_açı_örnekleri | originality_angle_examples |
| görsel_politikası | image_policy |
| link_politikası | link_policy |
| güncelleme_sıklığı_gün | update_frequency_days |
| prompt_blokları.system_ek / outline_ek / draft_ek / critique_ek / compliance_ek / metadata_ek | prompt_blocks.system_extra / outline_extra / draft_extra / critique_extra / compliance_extra / metadata_extra |
| yetersiz_veri_davranışı | insufficient_data_behavior |
| araştırma_politikası | research_policy |
| dil_politikası | language_policy |
| bölgesel_politika | regional_policy |
| özgün_katkı_politikası | original_contribution_policy |

Özel kapı kuralı id eşlemesi (docs/CATEGORIES.md → kanonik gate id):

| Türkçe kural adı | Kanonik gate id |
|---|---|
| madde_no_doğrulama | law_article_number_verification |
| karar_no_doğrulama | court_decision_number_verification |
| hesap_doğrulama | calculation_recomputation |
| sağlık_iddia_sözlüğü | health_claim_lexicon_match |
| tahmin_dili dedektörü | prediction_language_detection |
| şehir/ilçe permütasyon dedektörü | city_permutation_detection |
| kaynak yaşı engeli | source_age_gate |

### FILE: 07_CATEGORY_PACKS.md ###
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

### FILE: 08_SITES_AUTHORS_REVIEWERS.md ###
# Prompt 8 — Sites, Authors, Reviewers and Language Profiles

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Site, Author, Reviewer, SiteInventory ve SiteHealth modelleri ile ekranlarını oluştur. Site language profile: primary_language, supported_languages, locale, country, region, editorial_style, spelling_variant, terminology_policy, address_form, banned/preferred terms.

Author yalnızca gerçek ve configured identity olabilir. Credentials, profession, experience, awards, testing history veya qualification uydurulamaz. First-hand required olup meşru value source yoksa BLOCK.

Reviewer: name, role, languages, categories, permissions, YMYL permissions ve gerçek review event kayıtları. Reviewer inceleme yapmadıysa "reviewed by" gösterme. Tek kişilik kullanımda roller aynı kişiye atanabilir ancak her approval ayrı event olarak tutulur.

Multilingual site için output language ile research languages ayrı konfigüre edilir; native-language QA profili locale/spelling/terminology/regression testleriyle doğrulanır.

### FILE: 09_TOPIC_KEYWORD.md ###
# Prompt 9 — Topic and Keyword Manager

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Manual topic, CSV/XLSX import, focus keyword, secondary keywords, search intent, clustering, cannibalization, regional duplication, multilingual clustering ve doorway diagnostics geliştir.

Intent enum: informational, commercial_investigation, transactional, navigational, local, mixed. AI sınıflandırabilir; kullanıcı override edebilir. Focus keyword yalnızca topic/intent signal'dir; density, exact percentage, exact count veya unnatural repetition hedefi oluşturma.

Cannibalization aynı site + aynı intent + yakın konu için merge/expand/differentiate önerileri üretir. Multilingual pages otomatik duplicate sayılmaz; hreflang, locale, audience, regional value ve localization kontrol edilir. City/region/keyword permutation ile değersiz seri sayfaları flag et.

İçe aktarılan dosyalarda path traversal, formula injection, oversized file, encoding ve duplicate row güvenlik kontrolleri yap.

### FILE: 10_RESEARCH_FACTS.md ###
# Prompt 10 — Autonomous Research, Sources and Evidence

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Autonomous Research Engine oluştur: discovery.py, source_ranker.py, source_policy.py, fetcher.py, extractor.py, verifier.py, contradiction.py, fact_sheet.py, research_cache.py, autonomous_research.py.

Akış: ARTICLE BRIEF → RESEARCH PLAN → QUERY PLAN → CANDIDATE DISCOVERY → SOURCE FILTER → SOURCE FETCH → CONTENT EXTRACTION → EVIDENCE EXTRACTION → CLAIM VERIFICATION → CONTRADICTION DETECTION → FRESHNESS CHECK → FACT SHEET → RESEARCH SCORE → RESEARCH READY.

Search provider optionaldır ve yalnızca discovery içindir; snippet evidence değildir. Google SERP scraping core dependency olmayacak. Allowed channels: official domains, repositories, sitemap/RSS/feed, site inventory, direct URL, user sources, optional approved API.

SafeFetcher: robots.txt, SSRF/private-IP/localhost blocking, redirect validation, content-type, size limits, timeout/rate limit, user-agent, retry, cache, hash, canonicalization ve HTML/PDF/DOCX/pasted text extraction sağlamalıdır. Kaynak injection'ı ignore et, flag'le; güvenliyse factual extraction'a devam et.

Source overlap için origin group kullan; aynı press release'i kopyalayan 10 siteyi 10 bağımsız kaynak sayma. Her evidence exact excerpt, locator, source id, extraction timestamp ve confidence taşır. LLM knowledge verified fact olamaz.

### FILE: 11_SCOPE_LENGTH_SELF_WRITTEN.md ###
# Prompt 11 — Fact Sheet, Original Contribution, Scope, Length and Self-Written Mode

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Fact Sheet her fact için fact_id, claim, source_ids, evidence, confidence, date, freshness, contradiction, importance ve status taşır. Contradiction sessizce seçilemez; claim A/B, source A/B, likely reason, resolution ve unresolved status tutulur.

Original Contribution Engine araştırmadan sonra comparison, contradiction analysis, calculation, synthesis, decision framework, original categorization veya practical checklist gibi gerçek katkı sinyallerini değerlendirir. `SUFFICIENT` ise draft; `INSUFFICIENT` ise `HUMAN_REVIEW_REQUIRED` ve açıklama. Bu bir AI originality garantisi değildir.

Scope Advisor topic, intent, reader, category, pack, fact sheet, value source, inventory ve observations ile scope/sections/required facts/optional facts/exclusions/complexity/angle üretir. Length seçenekleri: short, standard, comprehensive, custom, unlimited, user outline. Kelime sayısı kalite gate'i değildir; ±15% yalnızca bilgilendiricidir.

Self-written mode'da kullanıcı metni sessizce rewrite edilmez. AI drafting/rewrite atlanır; source mapping, fact-check, language QA, compliance, metadata, SEO, schema ve technical QA uygulanır. Öneriler diff-only olmalıdır.

### FILE: 12_PIPELINE.md ###
# Prompt 12 — End-to-End Article Pipeline

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Pipeline'ı resumable, cancellable, idempotent, event-driven ve versioned kur: PRECHECK → RESEARCH → FACT SHEET → ORIGINAL CONTRIBUTION → SCOPE → USER/CONFIGURED SCOPE GATE → OUTLINE → DRAFT → CRITIQUE → REVISION → NATIVE LANGUAGE EDIT → FACT CHECK → COMPLIANCE → SEO → LINKS → METADATA → STRUCTURED DATA → QUALITY → PUBLICATION POLICY → REVIEW/PUBLISH.

Language edit sonrası fact-check tekrar koşar. Her adımdan önce/sonra checkpoint, input/output hash, audit event ve status update kaydedilir. Failure last safe checkpoint'ten resume olur; duplicate expensive calls cache/idempotency ile engellenir.

AUTONOMOUS generation tamamlanabilir ancak publication ayrı policy kararıdır. USER_PROVIDED modda insan metni korunur. Critical unsupported claim, unresolved material contradiction, missing reviewer, missing disclosure, insufficient contribution veya technical blocker publish'i durdurur.

### FILE: 13_CHECKLIST_ENGINE.md ###
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

### FILE: 14_SEO_METADATA_MEDIA.md ###
# Prompt 14 — SEO, Metadata, Links, Schema and Media

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Title, H1, meta description, slug, canonical, language, hreflang, Open Graph, Twitter/X, internal/external links, images, video, structured data ve nh3 HTML sanitization uygula.

Focus keyword natural signal'dir; density hedefi yoktur. Linkler relevance/value ile seçilir; paid/sponsored/ugc/nofollow rel kuralları uygulanır. Broken link, misleading anchor, orphan page ve unsafe external URL kontrolü yapılır.

Görsellerde licensing, alt text, dimensions, compression, WebP/AVIF, lazy loading, LCP, decorative empty alt ve AI image metadata (`IPTC DigitalSourceType=TrainedAlgorithmicMedia`) kontrol edilir. AI görsel gerçek fotoğraf/deneyim gibi sunulamaz.

Schema yalnız görünür ve desteklenen içeriği temsil eder; ranking guarantee değildir. FAQ gibi güncel destek politikaları hard-code edilmez, versioned policy olarak tutulur. Teknik doğrulama JSON-LD/schema parser ve fixture'larla yapılır.

### FILE: 15_REVIEW_APPROVAL_ASSISTANT.md ###
# Prompt 15 — Review Dashboard, Native Language QA and Approval Assistant

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Review dashboard kullanıcıya teknik terim yerine Research, Facts, Language, Editorial, SEO, Policy ve Technical durumlarını PASS/WARN/BLOCK olarak gösterir. Her statü evidence, source IDs, claim mapping, confidence, conflict ve rule detail açmalıdır.

## İki geçişli dil sistemi (v5 — tam semantik)

**Pass 1 — Generation:** Writer makaleyi output language'ta yazar.

**Pass 2 — Native Editorial Review:** Ayrı bir LLM/provider/profile makaleyi **ana dil editörü** olarak inceler. Kontrol listesi: grammar, syntax, terminology, readability, naturalness, register, regional appropriateness, repetition, awkward/literal translation, anglicisms, machine-translation artifacts, unnatural keyword insertion, inconsistent formal/informal address, unsupported statements.

Bölgesel profiller: de-DE / de-AT / de-CH farkları; en-US / en-GB; tr-TR. Profiller veri güdümlüdür (locale, spelling variant, terminology, banned/preferred terms); yeni bir dil eklemek pipeline kodunu değiştirmeyi gerektirmez.

Sonuç işleme kuralları:

- **AUTO_FIX** yalnızca güvenli dil sorunları için: yazım, noktalama, açık gramer, bariz tekrar.
- **FLAG** olgusal sorunlar ve belirsiz terminoloji için; otomatik düzeltme yapılmaz.
- Dil editörü **desteklenmeyen olgu ekleyemez**. Herhangi bir olgusal değişiklik Fact Sheet / Fact Check aşamasına geri döner (Prompt 12 ile tutarlı).

Native Language QA çıktısı: PASS/WARN/BLOCK + kullanıcının dilinde (ör. Türkçe) kısa özet; gerektiğinde yardımcı geri çeviri görünümü (doğrulama kanıtı değil).

Approval Assistant claim/source tablosu, conflict paneli, confidence paneli, missing evidence, unsupported claim ve önerilen action gösterir. Human approval alanları role, user, timestamp, decision, rationale ve content version ile imzalanır; otomatik onay üretilemez.

YMYL, advertising, site policy, unresolved material conflict veya pack reviewer requirement varsa reviewer approval kapısı açık ve görünür kalır. Kullanıcı hedef dilde uzman değilse sistem QA'yı basit açıklamalarla sunar; kullanıcıyı zorunlu proofreader yapmaz.

### FILE: 16_PUBLISH_WORDPRESS.md ###
# Prompt 16 — WordPress Publishing and Export

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

WordPress adapter'ı idempotent ve güvenli oluştur. Pre-publish checks: title, slug, body, excerpt, metadata, canonical, category, tags, links, images, schema, language, featured image, disclosure, author, status ve üç karar katmanı.

Required blocker varsa publish yoktur. Publish request idempotency key/content hash taşır. Network failure sonrası successful publish belirsizse önce remote lookup ile mevcut post'u bul; retry ile duplicate oluşturma.

Post-publish HTTP response, WP post ID, final URL, status, content hash, metadata, featured image, categories, tags ve timestamp loglanır. Credentials keyring'de ve loglarda maskeli tutulur.

Export: Markdown, HTML, JSON, review report, research report, fact sheet ve source bibliography. Export'ta source IDs ve audit provenance kaybolmamalıdır.

### FILE: 17_SCHEDULER.md ###
# Prompt 17 — Scheduler and Autonomous Publishing Policy

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Scheduler immediate, scheduled, recurring, queue ve daily safety limit destekler. Default daily limit EditorDesk/site safety setting'dir; Google limiti değildir.

Global auto-publish default OFF. YMYL auto-publish disabled. Advertising + AI + no human approval configured policyye göre BLOCK. Autonomous research/writing production mode'dur; autonomous publication ayrı karardır.

Emergency kill switch research, generation, publication ve scheduling'i güvenli checkpoint ile durdurur; DB corrupt etmez. Queue lease, retry/backoff, cancellation, idempotency, timezone/locale ve crash recovery testleri yaz.

### FILE: 18_MONITORING.md ###
# Prompt 18 — Monitoring, GSC and Maintenance

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Opsiyonel GSC adapter'ı published URL, index status if available, clicks, impressions, CTR, query data, errors ve last checked saklar. GSC future ranking truth veya guarantee olarak sunulamaz.

Stale maintenance: outdated sources, expired claims, changed regulations, broken links, changed product info, stale prices/statistics ve changed URLs tespit edilir. Update flow: UPDATE → RESEARCH AGAIN → COMPARE OLD/NEW FACTS → IDENTIFY CHANGES → UPDATE → FACT CHECK → COMPLIANCE → QUALITY → REPUBLISH.

Tarih yalnız esaslı güncellemede değişir. Aynı intent için merge/redirect/differentiate öner; policy olmadan değerli içeriği otomatik silme. Monitoring failures editorial publish'i yanlışlıkla başarılı göstermemeli.

### FILE: 19_UI_INTEGRATION.md ###
# Prompt 19 — Windows-First UI and Article Wizard

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

PySide6 Windows-first UI: Setup Wizard, Dashboard, Article Wizard, Research Monitor, Prompt Lab, Pack Manager, Checklist Audit, Review/Approval Assistant, Site/Author/Reviewer settings, connections and audit viewer.

Article Wizard alanları: site, category, topic, output language, site locale, country/region, focus keyword, secondary keywords, intent, target reader, content type, research mode, research languages, value source, user sources, length plan, author and reviewer.

Research mode açıklamaları: AUTONOMOUS "EditorDesk araştırmayı yapacak"; USER_PROVIDED "Kaynakları siz sağlayacaksınız"; HYBRID "Verilen kaynaklara ek araştırma yapılacak." Output language ve research languages ayrı gösterilir.

Dashboard queue, research status, source count, verified claims, conflicts, language/editorial QA, blockers/warnings, publication status ve estimated cost gösterir. UI dili başlangıçta Türkçe/İngilizce/Almanca/İspanyolca/Fransızca; article output dilleri bağımsızdır.

Keyboard navigation, contrast, scalable UI, screen-reader labels ve color-only olmayan status kullan. Destructive changes için açık confirmation; sıradan draft/edit işlemlerinde gereksiz modal kullanma.

### FILE: 20_COVERAGE_AUDIT.md ###
# Prompt 20 — Coverage, Security and Policy Audit

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Automated coverage auditor geliştir: docs/CHECKLIST.md ↔ code ↔ category packs ↔ prompts ↔ UI ↔ tests. Her rule ID, pack field, prompt block, research step ve language profile mapping'ini raporla. Checklist bölüm manifestosu sayıları (13'teki tablo) birebir doğrulanır.

Ayrıca auditor, GY-01..GY-15 mit maddelerinin **özellik olarak uygulanmadığını** doğrular: llms.txt üretici yok, AI chunking özelliği yok, meta keywords alanı yok, kelime/başlık sayısı hedefi yok, sahte mention/görünürlük aracı yok.

Security testleri: SSRF, localhost/private network, redirects, huge downloads, malicious PDFs, HTML injection, prompt injection, API key/WordPress credential leakage, SQL injection, path traversal ve unsafe imports.

Policy testleri: unsupported claim, fake experience/author/reviewer/citation, keyword stuffing, doorway, source copying, thin affiliate, stale info, YMYL without reviewer, missing disclosure, conflicting sources, insufficient data, fake freshness ve fake human approval.

Audit output machine-readable JSON + insan okunabilir rapor olmalı. Critical unmapped rule, invalid pack, missing E2E mapping veya manifest sayım uyuşmazlığı release'i block eder.

### FILE: 21_E2E_RELEASE.md ###
# Prompt 21 — E2E Tests, Packaging and Release

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Aşağıdaki E2E senaryolarını gerçek pipeline üzerinden test et: German autonomous article (`Beste Wanderschuhe für Anfänger`, de-DE); insufficient data; contradictory sources; source prompt injection; YMYL health; focus keyword stuffing request; copied source; self-written mode; WordPress retry after ambiguous success; cancel/resume; multilingual German/English/Turkish; original contribution insufficient; commodity content; approval assistant; ad-enabled site.

Beklenenler: source fetch olmadan snippet'ten article yok; German native QA; unsupported claim block; conflict record; injection flag; YMYL reviewer/auto-publish gate; natural keyword usage; similarity warning vs plagiarism distinction; user text silent rewrite edilmemesi; no duplicate WP post; cached research resume.

Packaging: Windows executable/package, installer, migration runner, config/user/admin/backup/security guides, SBOM, dependency audit ve release notes. Release gate yalnızca şunlar geçerse açılır: tests, migrations, security, coverage audit (manifesto sayıları dahil), 16 pack validation (İngilizce-kanonik anahtarlar + YMYL invariant'lar), prompts validation, `prompts/global_rules.md` ve `lexicons/tr/*.txt` varlık/bütünlük kontrolü, backup/restore, WP, autonomous research ve native-language QA E2E. Critical blocker varsa release yok.

### FILE: 22_ARCHITECTURE_NOTES.md ###
# Architecture Notes and Non-Negotiable Decisions

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

## Ana zincir

USER → ARTICLE BRIEF → CATEGORY POLICY → AUTONOMOUS RESEARCH → SOURCES → EVIDENCE → FACT SHEET → ORIGINAL CONTRIBUTION → AI WRITER → NATIVE LANGUAGE EDITOR → FACT CHECK → CHECKLIST → TECHNICAL/EDITORIAL GATES → PUBLICATION POLICY → WORDPRESS.

`docs/CHECKLIST.md` evrensel kontrol kaynağıdır. `docs/CATEGORIES.md` kategori ve source policy'dir. Autonomous Research mevcut sisteme eklenen motordur. Human Approval özellikle YMYL/reklamlı içerikte varsayılan olarak açık kalır.

## Yanlış zincirler

SEARCH SNIPPET → AI → ARTICLE; AI KNOWLEDGE → PRESENT AS FACT; AI DETECTOR → QUALITY; WORD COUNT → QUALITY; KEYWORD DENSITY → SEO; HUMAN APPROVAL → FAKE AUTOMATICALLY kesinlikle uygulanmaz.

## Original contribution gate

Kaynakların ötesinde comparison, synthesis, analysis, framework, calculation, categorization veya practical checklist yoksa `original_contribution_status=INSUFFICIENT`; varsayılan karar `HUMAN_REVIEW_REQUIRED`.

### FILE: 23_JSON_SCHEMAS.md ###
# JSON Schema Contracts

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Aşağıdaki sözleşmeleri JSON Schema 2020-12 veya Pydantic modelleri olarak uygulayıp version pinle.

### ResearchClaim

```json
{"claim_id":"string","article_id":"string","text":"string","importance":"critical|major|minor","source_ids":["string"],"evidence_ids":["string"],"verification_status":"SUPPORTED|PARTIALLY_SUPPORTED|CONTRADICTED|UNSUPPORTED|OUTDATED|NOT_APPLICABLE","confidence":0,"contradiction_status":"none|open|resolved","freshness_status":"fresh|stale|unknown"}
```

### Evidence

```json
{"evidence_id":"string","source_id":"string","claim_id":"string","excerpt":"string","locator":"string","captured_at":"date-time","confidence":0}
```

### Article draft output

```json
{"body_md":"string","sources_used":["string"],"experience_claims":[{"claim":"string","value_source_ref":"string"}],"general_info_flags":["string"],"to_verify":["string"],"assumptions":["string"],"scope_note":"string"}
```

### Checklist finding

```json
{"rule_id":"string","status":"PASS|WARN|BLOCK|N_A|PENDING","score":0,"evidence":"string","confidence":0,"recommendation":"string","human_required":false}
```

### Publication decision

```json
{"technical":"PASS|FAIL|PENDING","editorial":"PASS|FAIL|PENDING","policy":"PASS|FAIL|PENDING","decision":"PUBLISH|REVIEW|FIX|BLOCK","blockers":["string"],"warnings":["string"],"audit_id":"string"}
```

Şema dışı alanları varsayılan olarak reject et; backward-compatible migration için explicit versioning kullan.

### FILE: 24_TEST_MATRIX.md ###
# Test Matrix

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

| Alan | Birim | Entegrasyon | E2E | Release blocker |
|---|---:|---:|---:|---:|
| State transitions | ✓ | ✓ | ✓ | Evet |
| Source canonical/hash | ✓ | ✓ | ✓ | Evet |
| SSRF/redirect/size limits | ✓ | ✓ | ✓ | Evet |
| Source injection | ✓ | ✓ | ✓ | Evet |
| Evidence-to-claim mapping | ✓ | ✓ | ✓ | Evet |
| Contradiction handling | ✓ | ✓ | ✓ | Evet |
| Insufficient data | ✓ | ✓ | ✓ | Evet |
| Original contribution | ✓ | ✓ | ✓ | Yapılandırılabilir |
| Native language QA | ✓ | ✓ | ✓ | Evet |
| Checklist coverage + manifesto | ✓ | ✓ | ✓ | Evet |
| YMYL reviewer gate | ✓ | ✓ | ✓ | Evet |
| Keyword density rejection | ✓ |  | ✓ | Evet |
| WordPress idempotency | ✓ | ✓ | ✓ | Evet |
| Cancel/resume/cache | ✓ | ✓ | ✓ | Evet |
| Backup/restore |  | ✓ | ✓ | Evet |
| Pack key naming (EN kanonik) | ✓ |  |  | Evet |
| GY myths not-implemented | ✓ |  | ✓ | Uyarı |
| Accessibility/i18n | ✓ | ✓ | ✓ | Uyarı/kurala bağlı |

Her test deterministic fixture, expected status, audit event ve cleanup strategy içermeli. Network testlerinde live provider yerine MockProvider ve recorded fixtures kullan; ayrı opt-in smoke suite tanımla.

### FILE: 25_IMPLEMENTATION_ORDER.md ###
# Implementation Order and Agent Handoff

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

## Milestone 0 — Sözleşme

Repository inventory, architecture decision record, config, logging, error taxonomy, global immutable rules ve test harness.

## Milestone 1 — Persistence

SQLAlchemy models, Alembic, state machine, audit, repositories, seed registry.

## Milestone 2 — Provider boundaries

Keyring, provider registry, mocks, LLM structured output, optional search, WordPress adapter skeleton.

## Milestone 3 — Policy data

Checklist parser/registry + bölüm manifesto doğrulaması, category pack schema/loader (İngilizce-kanonik anahtar denetimi), 16 pack fixtures, `prompts/global_rules.md` (B.1 aynen) ve `prompts/templates/*.j2` (B.2–B.7) materializasyonu, `lexicons/tr/*.txt` (D.1–D.5), site/language/author/reviewer profiles.

## Milestone 4 — Research

SafeFetcher, discovery, source ranking/policy, extraction, evidence, claims, contradiction, freshness, cache, fact sheet.

## Milestone 5 — Editorial pipeline

Scope/length, original contribution, outline, draft, native language QA (iki geçişli sistem), fact check, compliance, SEO, metadata, schema.

## Milestone 6 — Review and publish

Three gates, approval assistant, scheduler, kill switch, WordPress idempotency, exports, monitoring.

## Milestone 7 — UI and release

Wizards, dashboards, accessibility/i18n, coverage audit, E2E, security, packaging, backup/restore, SBOM.

Her milestone için ajan: (a) önce mevcut durumu özetler, (b) değişiklik planı verir, (c) uygular, (d) test/migration çalıştırır, (e) dosya listesi ve risk raporu sunar. Test başarısızken bir sonraki milestone'a geçme. Bu metinler yalnızca ajan talimatıdır; ajan dış servislerde gerçek publish yapmadan önce dry-run fixture kullanmalıdır.

### FILE: contracts/CATEGORIES.md ###
# CATEGORIES.md — Category Pack Contract (özet / işaretçi)

> Bu dosya özettir; **normatif metin `docs/CATEGORIES.md` tam halidir** (A şema, B katman şablonları, C.1–C.16, D sözlükler). Çelişki hâlinde tam metin kazanır.

Her kategori YAML'ı `06_PACK_ENGINE.md`'deki **İngilizce kanonik** alanların tamamını içermelidir (Türkçe adlar takma addır; eşleme 06'dadır).

YMYL=true ise reviewer_required=true, auto_publish_allowed=false, min sources >=3. First-hand zorunluysa value source olmadan üretim yok. Tüm kategoriler global immutable rules taşır ve yetersiz veride yazmaz.

16 pack: health, law, finance, crypto, technology, product_review, travel, real_estate, automotive, food, news, sports, education_career, pets, beauty, general_guide. Kategori-specific source policy, freshness, reviewer, prohibited claims, sections, schema, image/link and publication behavior zorunludur ve `docs/CATEGORIES.md` C.x satırlarından aynen alınır.

Özgün katkı alanı commodity content'i tespit eder; yetersizse insan incelemesine yönlendirir. Pack loader eksik/yanlış/bilinmeyen alanı reject eder, version ve policy hash'i kaydeder.

### FILE: contracts/CHECKLIST.md ###
# CHECKLIST.md — Source-of-Truth Policy (özet / işaretçi)

> Bu dosya özettir; **normatif metin `docs/CHECKLIST.md` tam halidir** (bölüm 1–26). Çelişki hâlinde tam metin kazanır.

Bu dosya uygulamanın evrensel kontrol kaynağıdır. Rule type: OTO=deterministic code, LLM=model scoring/evidence, İNS=human-only, KRM=machine/LLM flag plus human approval, **MYTH=bilgi paneli (kural değildir)**. Severity E=blocker, U=reasoned warning, B=information. Conditional rules can be N/A.

Immutable: ranking/traffic/indexing guarantee yok; word count, AI-detector, keyword density kalite gate'i değil; source copying, fake identity/experience/citation, unsupported claim, cloaking, doorway, paid ranking links, fake freshness, fake human approval yok.

Zorunlu rule groups ve ID aralıkları: ST-01..ST-14; DE-01..DE-25; KA-01..KA-12; GU-01..GU-14; YM-01..YM-12; **BA-01..BA-13**; YA-01..YA-14; AK-01..AK-12; IL-01..IL-09; DL-01..DL-10; AF-01..AF-09; GO-01..GO-12; VI-01..VI-07; TE-01..TE-17; SD-01..SD-10; SV-01..SV-06; SP-01..SP-19; AS-01..AS-20; ED-01..ED-12; QA-01..QA-11; PS-01..PS-14; GB-01..GB-05; PF-01..PF-10; ON-01..ON-06; **GY-01..GY-15 (MYTH — kural olarak eklenmez, Ayarlar'da bilgi paneli)**.

Parser, registry and coverage audit tüm ID'leri korumalı ve `13_CHECKLIST_ENGINE.md`'deki bölüm manifestosuyla sayı doğrulaması yapmalıdır. Uygulama bilinmeyen ID'yi sessizce yok sayamaz.