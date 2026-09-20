# Prompt 12 — End-to-End Article Pipeline

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Pipeline'ı resumable, cancellable, idempotent, event-driven ve versioned kur: PRECHECK → RESEARCH → FACT SHEET → ORIGINAL CONTRIBUTION → SCOPE → USER/CONFIGURED SCOPE GATE → OUTLINE → DRAFT → CRITIQUE → REVISION → NATIVE LANGUAGE EDIT → FACT CHECK → COMPLIANCE → SEO → LINKS → METADATA → STRUCTURED DATA → QUALITY → PUBLICATION POLICY → REVIEW/PUBLISH.

Language edit sonrası fact-check tekrar koşar. Her adımdan önce/sonra checkpoint, input/output hash, audit event ve status update kaydedilir. Failure last safe checkpoint'ten resume olur; duplicate expensive calls cache/idempotency ile engellenir.

AUTONOMOUS generation tamamlanabilir ancak publication ayrı policy kararıdır. USER_PROVIDED modda insan metni korunur. Critical unsupported claim, unresolved material contradiction, missing reviewer, missing disclosure, insufficient contribution veya technical blocker publish'i durdurur.
