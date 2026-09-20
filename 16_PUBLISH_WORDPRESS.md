# Prompt 16 — WordPress Publishing and Export

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

WordPress adapter'ı idempotent ve güvenli oluştur. Pre-publish checks: title, slug, body, excerpt, metadata, canonical, category, tags, links, images, schema, language, featured image, disclosure, author, status ve üç karar katmanı.

Required blocker varsa publish yoktur. Publish request idempotency key/content hash taşır. Network failure sonrası successful publish belirsizse önce remote lookup ile mevcut post'u bul; retry ile duplicate oluşturma.

Post-publish HTTP response, WP post ID, final URL, status, content hash, metadata, featured image, categories, tags ve timestamp loglanır. Credentials keyring'de ve loglarda maskeli tutulur.

Export: Markdown, HTML, JSON, review report, research report, fact sheet ve source bibliography. Export'ta source IDs ve audit provenance kaybolmamalıdır.
