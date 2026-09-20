# Prompt 15 — Review Dashboard, Native Language QA and Approval Assistant

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Review dashboard kullanıcıya teknik terim yerine Research, Facts, Language, Editorial, SEO, Policy ve Technical durumlarını PASS/WARN/BLOCK olarak gösterir. Her statü evidence, source IDs, claim mapping, confidence, conflict ve rule detail açmalıdır.

## İki geçişli dil sistemi (v5 — tam semantik)

**Pass 1 — Generation:** Writer makaleyi output language'ta yazar.

**Pass 2 — Native Editorial Review:** Ayrı bir LLM/provider/profile makaleyi **ana dil editörü** olarak inceler. Kontrol listesi: grammar, syntax, terminology, readability, naturalness, register, regional appropriateness, repetition, awkward/literal translation, anglicisms, machine-translation artifacts, unnatural keyword insertion, inconsistent formal/informal address, unsupported statements.

Bölgesel profiller: de-DE / de-AT / de-CH farkları; en-US / en-GB; tr-TR. Profiller veri güdümlüdür (locale, spelling variant, terminology, banned/preferred terms); yeni bir dil eklemek pipeline kodunu değiştirmeyi gerektirmez.

Sonuç işleme kuralları:

- **AUTO_FIX** yalnızca güvenli dil sorunları için: yazım, noktalama, açık gramer, bariz tekrar.
- **FLAG** olgusal sorunlar ve belirsiz terminoloji için; otomatik düzeltme yapılmaz.
- Dil editörü **desteklenmeyen olgu ekleyemez**. Herhangi bir olgusal değişiklik Fact Sheet / Fact Check aşamasına geri döner (Prompt 12 ile tutarlı).

Native Language QA çıktısı: PASS/WARN/BLOCK + kullanıcının dilinde (ör. Türkçe) kısa özet; gerektiğinde yardımcı geri çeviri görünümü (doğrulama kanıtı değil).

Approval Assistant claim/source tablosu, conflict paneli, confidence paneli, missing evidence, unsupported claim ve önerilen action gösterir. Human approval alanları role, user, timestamp, decision, rationale ve content version ile imzalanır; otomatik onay üretilemez.

YMYL, advertising, site policy, unresolved material conflict veya pack reviewer requirement varsa reviewer approval kapısı açık ve görünür kalır. Kullanıcı hedef dilde uzman değilse sistem QA'yı basit açıklamalarla sunar; kullanıcıyı zorunlu proofreader yapmaz.
