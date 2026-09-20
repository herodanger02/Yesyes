# JSON Schema Contracts

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Aşağıdaki sözleşmeleri JSON Schema 2020-12 veya Pydantic modelleri olarak uygulayıp version pinle.

### ResearchClaim

```json
{"claim_id":"string","article_id":"string","text":"string","importance":"critical|major|minor","source_ids":["string"],"evidence_ids":["string"],"verification_status":"SUPPORTED|PARTIALLY_SUPPORTED|CONTRADICTED|UNSUPPORTED|OUTDATED|NOT_APPLICABLE","confidence":0,"contradiction_status":"none|open|resolved","freshness_status":"fresh|stale|unknown"}
```

### Evidence

```json
{"evidence_id":"string","source_id":"string","claim_id":"string","excerpt":"string","locator":"string","captured_at":"date-time","confidence":0}
```

### Article draft output

```json
{"body_md":"string","sources_used":["string"],"experience_claims":[{"claim":"string","value_source_ref":"string"}],"general_info_flags":["string"],"to_verify":["string"],"assumptions":["string"],"scope_note":"string"}
```

### Checklist finding

```json
{"rule_id":"string","status":"PASS|WARN|BLOCK|N_A|PENDING","score":0,"evidence":"string","confidence":0,"recommendation":"string","human_required":false}
```

### Publication decision

```json
{"technical":"PASS|FAIL|PENDING","editorial":"PASS|FAIL|PENDING","policy":"PASS|FAIL|PENDING","decision":"PUBLISH|REVIEW|FIX|BLOCK","blockers":["string"],"warnings":["string"],"audit_id":"string"}
```

Şema dışı alanları varsayılan olarak reject et; backward-compatible migration için explicit versioning kullan.
