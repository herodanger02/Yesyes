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
