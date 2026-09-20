# Prompt 4 — Provider-Independent LLM Orchestration

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

LLMProvider, LLMRequest, LLMResponse, LLMProfile ve LLMRun sözleşmelerini uygula. Structured output, JSON Schema/Pydantic validation, timeout, exponential backoff, cancellation, optional streaming, model fallback, token/cost logging, prompt snapshot, model snapshot, deterministic run ID ve idempotency zorunludur.

LLM hiçbir zaman deterministic validation mümkünken factual veya policy kararının tek otoritesi olamaz. Çıktı suggestion, evidence-backed analysis, classification veya draft'tır. Her response schema dışıysa parse error olarak retry edilir; tekrar başarısızsa insan incelemesi/blok durumu üretilir.

Prompt ve model snapshot'ı immutable kaydet. Aynı run id ile tekrar çağrıda güvenli cache/idempotency uygula. PII ve secret redaction yap. Token/cost tahmini ve gerçek provider maliyetini ayır. MockLLMProvider ile tüm pipeline test edilebilir olmalı.

Batch evaluation destekle; ancak bir kritik iddia için source/evidence mapping zorunluluğunu gevşetme. LLM bulguları rule_id, score 0–5, evidence, confidence, recommendation ve status içermelidir.
