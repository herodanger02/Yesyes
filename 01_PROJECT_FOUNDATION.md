# Prompt 1 — Project Foundation and Editorial Architecture

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Sen kıdemli bir Python 3.12+, PySide6, SQLAlchemy 2, SQLite ve güvenli içerik üretim sistemi mimarısısın. Windows-first, modüler, test edilebilir ve offline-first çalışabilen EditorDesk'i kur.

Zorunlu teknoloji tabanı: PySide6, SQLAlchemy 2, Alembic, Pydantic v2, Jinja2, YAML parser, httpx, tenacity, keyring, trafilatura, markdown-it-py, nh3, python-slugify, Pillow, BeautifulSoup/lxml, python-docx, PDF parser, pytest ve pytest-qt.

Uygulama şu editorial zinciri yönetmelidir: TOPIC → BRIEF → RESEARCH → SOURCE VALIDATION → EVIDENCE → FACT SHEET → CONTRADICTION CHECK → SEARCH INTENT → ORIGINAL ANGLE → SCOPE → OUTLINE → DRAFT → NATIVE LANGUAGE EDITING → FACT CHECK → COMPLIANCE → SEO → QUALITY → PUBLICATION POLICY → WORDPRESS.

Article Wizard minimum alanları: site, category, topic, output language, site locale, country/region, focus keyword, optional secondary keywords, intent, target reader, content type, research mode, optional value source, optional user sources. Research mode tam olarak `AUTONOMOUS`, `USER_PROVIDED`, `HYBRID` olmalıdır.

Mimari kurallar: domain/application/infrastructure/UI ayrımı; pipeline state ile article state ayrımı; her adım event ve audit üretir; cancellation, resume, idempotency ve checkpoint vardır; provider-specific kod domain pipeline'a sızmaz.

Üç karar katmanı ayrı uygulanır: `TECHNICAL_ELIGIBILITY`, `EDITORIAL_QUALITY`, `PUBLICATION_POLICY`. Publish yalnızca üçü de PASS olduğunda mümkün olabilir.

İlk milestone sonunda: proje ağacı, dependency yönetimi, config profilleri, logging, error taxonomy, dependency injection, temel PySide6 shell, health check, test fixture'ları ve boş Alembic migration'ı teslim et. Kodlamaya başlamadan önce mimari karar kaydı yaz.
