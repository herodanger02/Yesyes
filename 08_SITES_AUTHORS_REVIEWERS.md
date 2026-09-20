# Prompt 8 — Sites, Authors, Reviewers and Language Profiles

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Site, Author, Reviewer, SiteInventory ve SiteHealth modelleri ile ekranlarını oluştur. Site language profile: primary_language, supported_languages, locale, country, region, editorial_style, spelling_variant, terminology_policy, address_form, banned/preferred terms.

Author yalnızca gerçek ve configured identity olabilir. Credentials, profession, experience, awards, testing history veya qualification uydurulamaz. First-hand required olup meşru value source yoksa BLOCK.

Reviewer: name, role, languages, categories, permissions, YMYL permissions ve gerçek review event kayıtları. Reviewer inceleme yapmadıysa "reviewed by" gösterme. Tek kişilik kullanımda roller aynı kişiye atanabilir ancak her approval ayrı event olarak tutulur.

Multilingual site için output language ile research languages ayrı konfigüre edilir; native-language QA profili locale/spelling/terminology/regression testleriyle doğrulanır.
