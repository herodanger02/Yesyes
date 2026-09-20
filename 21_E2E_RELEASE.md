# Prompt 21 — E2E Tests, Packaging and Release

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Aşağıdaki E2E senaryolarını gerçek pipeline üzerinden test et: German autonomous article (`Beste Wanderschuhe für Anfänger`, de-DE); insufficient data; contradictory sources; source prompt injection; YMYL health; focus keyword stuffing request; copied source; self-written mode; WordPress retry after ambiguous success; cancel/resume; multilingual German/English/Turkish; original contribution insufficient; commodity content; approval assistant; ad-enabled site.

Beklenenler: source fetch olmadan snippet'ten article yok; German native QA; unsupported claim block; conflict record; injection flag; YMYL reviewer/auto-publish gate; natural keyword usage; similarity warning vs plagiarism distinction; user text silent rewrite edilmemesi; no duplicate WP post; cached research resume.

Packaging: Windows executable/package, installer, migration runner, config/user/admin/backup/security guides, SBOM, dependency audit ve release notes. Release gate yalnızca şunlar geçerse açılır: tests, migrations, security, coverage audit (manifesto sayıları dahil), 16 pack validation (İngilizce-kanonik anahtarlar + YMYL invariant'lar), prompts validation, `prompts/global_rules.md` ve `lexicons/tr/*.txt` varlık/bütünlük kontrolü, backup/restore, WP, autonomous research ve native-language QA E2E. Critical blocker varsa release yok.
