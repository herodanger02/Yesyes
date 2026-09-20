# Architecture Notes and Non-Negotiable Decisions

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

## Ana zincir

USER → ARTICLE BRIEF → CATEGORY POLICY → AUTONOMOUS RESEARCH → SOURCES → EVIDENCE → FACT SHEET → ORIGINAL CONTRIBUTION → AI WRITER → NATIVE LANGUAGE EDITOR → FACT CHECK → CHECKLIST → TECHNICAL/EDITORIAL GATES → PUBLICATION POLICY → WORDPRESS.

`docs/CHECKLIST.md` evrensel kontrol kaynağıdır. `docs/CATEGORIES.md` kategori ve source policy'dir. Autonomous Research mevcut sisteme eklenen motordur. Human Approval özellikle YMYL/reklamlı içerikte varsayılan olarak açık kalır.

## Yanlış zincirler

SEARCH SNIPPET → AI → ARTICLE; AI KNOWLEDGE → PRESENT AS FACT; AI DETECTOR → QUALITY; WORD COUNT → QUALITY; KEYWORD DENSITY → SEO; HUMAN APPROVAL → FAKE AUTOMATICALLY kesinlikle uygulanmaz.

## Original contribution gate

Kaynakların ötesinde comparison, synthesis, analysis, framework, calculation, categorization veya practical checklist yoksa `original_contribution_status=INSUFFICIENT`; varsayılan karar `HUMAN_REVIEW_REQUIRED`.
