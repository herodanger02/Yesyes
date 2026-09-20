# Test Matrix

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

| Alan | Birim | Entegrasyon | E2E | Release blocker |
|---|---:|---:|---:|---:|
| State transitions | ✓ | ✓ | ✓ | Evet |
| Source canonical/hash | ✓ | ✓ | ✓ | Evet |
| SSRF/redirect/size limits | ✓ | ✓ | ✓ | Evet |
| Source injection | ✓ | ✓ | ✓ | Evet |
| Evidence-to-claim mapping | ✓ | ✓ | ✓ | Evet |
| Contradiction handling | ✓ | ✓ | ✓ | Evet |
| Insufficient data | ✓ | ✓ | ✓ | Evet |
| Original contribution | ✓ | ✓ | ✓ | Yapılandırılabilir |
| Native language QA | ✓ | ✓ | ✓ | Evet |
| Checklist coverage + manifesto | ✓ | ✓ | ✓ | Evet |
| YMYL reviewer gate | ✓ | ✓ | ✓ | Evet |
| Keyword density rejection | ✓ |  | ✓ | Evet |
| WordPress idempotency | ✓ | ✓ | ✓ | Evet |
| Cancel/resume/cache | ✓ | ✓ | ✓ | Evet |
| Backup/restore |  | ✓ | ✓ | Evet |
| Pack key naming (EN kanonik) | ✓ |  |  | Evet |
| GY myths not-implemented | ✓ |  | ✓ | Uyarı |
| Accessibility/i18n | ✓ | ✓ | ✓ | Uyarı/kurala bağlı |

Her test deterministic fixture, expected status, audit event ve cleanup strategy içermeli. Network testlerinde live provider yerine MockProvider ve recorded fixtures kullan; ayrı opt-in smoke suite tanımla.
