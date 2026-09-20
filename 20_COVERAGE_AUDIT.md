# Prompt 20 — Coverage, Security and Policy Audit

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Automated coverage auditor geliştir: docs/CHECKLIST.md ↔ code ↔ category packs ↔ prompts ↔ UI ↔ tests. Her rule ID, pack field, prompt block, research step ve language profile mapping'ini raporla. Checklist bölüm manifestosu sayıları (13'teki tablo) birebir doğrulanır.

Ayrıca auditor, GY-01..GY-15 mit maddelerinin **özellik olarak uygulanmadığını** doğrular: llms.txt üretici yok, AI chunking özelliği yok, meta keywords alanı yok, kelime/başlık sayısı hedefi yok, sahte mention/görünürlük aracı yok.

Security testleri: SSRF, localhost/private network, redirects, huge downloads, malicious PDFs, HTML injection, prompt injection, API key/WordPress credential leakage, SQL injection, path traversal ve unsafe imports.

Policy testleri: unsupported claim, fake experience/author/reviewer/citation, keyword stuffing, doorway, source copying, thin affiliate, stale info, YMYL without reviewer, missing disclosure, conflicting sources, insufficient data, fake freshness ve fake human approval.

Audit output machine-readable JSON + insan okunabilir rapor olmalı. Critical unmapped rule, invalid pack, missing E2E mapping veya manifest sayım uyuşmazlığı release'i block eder.
