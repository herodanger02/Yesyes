# Prompt 9 — Topic and Keyword Manager

> Bu dosya yalnızca uygulama promptudur. Kod burada yazılmayacak; kodlama ajanı bu talimatları projede uygulayacaktır.

Manual topic, CSV/XLSX import, focus keyword, secondary keywords, search intent, clustering, cannibalization, regional duplication, multilingual clustering ve doorway diagnostics geliştir.

Intent enum: informational, commercial_investigation, transactional, navigational, local, mixed. AI sınıflandırabilir; kullanıcı override edebilir. Focus keyword yalnızca topic/intent signal'dir; density, exact percentage, exact count veya unnatural repetition hedefi oluşturma.

Cannibalization aynı site + aynı intent + yakın konu için merge/expand/differentiate önerileri üretir. Multilingual pages otomatik duplicate sayılmaz; hreflang, locale, audience, regional value ve localization kontrol edilir. City/region/keyword permutation ile değersiz seri sayfaları flag et.

İçe aktarılan dosyalarda path traversal, formula injection, oversized file, encoding ve duplicate row güvenlik kontrolleri yap.
