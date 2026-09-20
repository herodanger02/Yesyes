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
