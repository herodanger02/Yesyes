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
