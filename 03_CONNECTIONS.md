# Prompt 3 — Connections and Provider Abstraction

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Provider-independent connection architecture kur. LLM, Search, WordPress, Image, Similarity/Plagiarism, GSC, PageSpeed ve Webhook provider'ları aynı sözleşme üzerinden çalışmalı.

Her provider: test_connection, timeout, retry policy, rate limit, cost tracking, health state, capability discovery ve error classification sağlamalıdır. Search provider opsiyoneldir; LLM AI modlarında gereklidir. Search yokken autonomous research, configured authoritative domains, sitemap/feed, direct URL, site inventory ve seed sources ile çalışmalıdır.

Secrets yalnızca OS keyring/secret store'da tutulur; SQLite, log, prompt snapshot veya exception içinde API key bulunamaz. Config'te base_url, auth method, model, timeout, rate limit, enabled, environment ve display name bulunur; secret değerleri maskeli gösterilir.

Domain pipeline provider adı bilmemeli; adapter registry ve dependency injection kullanmalıdır. Mock provider'lar deterministik testler için zorunludur. Network hataları transient/permanent/auth/policy/parse/rate-limit olarak sınıflandırılmalıdır.

Connection UI'da test sonucu, son sağlık zamanı, gecikme, hata sınıfı ve maliyet gösterilir. Credential rotasyonu ve provider disable etme güvenli olmalıdır.
