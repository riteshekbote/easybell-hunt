## 2026-09-03 16:49:12 UTC [target] (model nemotron3)
## 2026-09-03 19:45:22 UTC [target] (model nemotron3)
## 2026-09-03 21:55:59 UTC [target] (model nemotron3)
## 2026-09-03 23:45:43 UTC [target] (model nemotron3)
[NEW] my.easybell.com: Confirmed live customer portal (Laravel 10 + Vue 3 Inertia SPA), 200 at /login, sets `ekp_session` + encrypted `XSRF-TOKEN`, `X-Inertia` header; `customerId` leaked in Matomo tracker on every page. Supersedes dead `portal.easybell.de`.
[NEW] voip-management.easybell.de: Live nginx→Spring JSON API at `/api/<res>` (rewrites to internal `/api/v2/<res>`, leaked via 404 body `{"code":404,"message":"/api/v2/<res>"}`). `/api/` and `/api/v2/` direct return nginx HTML 404. Referenced as `VITE_VOIP_MANAGEMENT_URL` in portal SPA.
[CHANGED] dev.easybell.de / portal.easybell.de: No DNS/route — effectively dead (probe timeouts confirmed). Top targets shift to my.easybell.com + voip-management.
[CHANGED] voip-management WAF: Aggressive rate-limit confirmed. Bursts >~8-10 probes → empty/timeouts. Mandates >=6s spacing, 60-120s backoff after block.
[CHANGED] voip-api-v2-bola: No live (non-404) Spring resource discovered yet across customer/account/number/user/subscriber/trunk/line/contract/invoice/sip/device/tariff probes — all nginx-HTML 404 or rate-limited. Backend reachable and versioned but actual resource names unknown.
[PRIO] voip-management.easybell.de,7.8,attack_surface:8+business_value:9+tech_exposure:8+gate_ease:6+cloud_surface:6+freshness:5
[PRIO] my.easybell.com,7.3,attack_surface:8+business_value:9+tech_exposure:7+gate_ease:4+cloud_surface:5+freshness:5
[PRIO] mail.easybell.de,5.6,attack_surface:7+business_value:5+tech_exposure:6+gate_ease:5+cloud_surface:4+freshness:5
[PRIO] www.easybell.de,4.8,attack_surface:4+business_value:6+tech_exposure:5+gate_ease:7+cloud_surface:3+freshness:5
[PRIO] auth.easybell.de,4.5,attack_surface:6+business_value:7+tech_exposure:6+gate_ease:3+cloud_surface:4+freshness:4
[HYP] voip-api-v2-bola
class: IDOR
asset: voip-management.easybell.de/api/
confidence: 62
reasoning: Live Spring-style JSON API confirmed reachable via `/api/<res>` rewrite to internal `/api/v2/<res>` (error body leaks v2 rewrite map). Versioned REST + customer VoIP/account resources = classic BOLA if object-scoped authz missing. Backend actively responds to unmatched paths with structured JSON — active app, not static host.
evidence_needed: At least one real v2 resource returning non-404 JSON (data or 401/403 challenge) unauthenticated; numeric id param pattern.
verify_steps: After 60s+ cooldown, single spaced probes (>=6s apart, <=1rps) of `/api/<resource>` for likely names: customer, account, user, number, extension, subscriber, trunk, line, contract, invoice, sip, device, tariff. Watch for non-404 JSON (data or 401/403). No auth bypass/mutation.
impact: Cross-customer VoIP/account/PII exposure or unauthorized config access → High/Critical
testability: AUTH_HELPED
[HYP] my-portal-inertia-bola
class: IDOR
asset: my.easybell.com
confidence: 58
reasoning: Customer portal (Laravel 10 + Vue 3 Inertia SPA) manages billing, SIP, service config. `customerId` visible in Matomo tracker on every page. SPA proxies to voip-management for backend. Auth-scoped object endpoints are prime BOLA surface. Inertia pattern exposes partial route table in public JS bundles.
evidence_needed: Public/unauth Inertia route table from SPA bundles; any API proxy endpoints the SPA calls unauthenticated; object-id param patterns in routes.
verify_steps: GET https://my.easybell.com/ (200), fetch and parse all linked JS bundles for Inertia page components and route definitions; catalog public endpoints and any API paths proxied via Laravel. No mutating/auth tests without creds.
impact: Cross-tenant PII dump, billing tamper, SIP config hijack → High/Critical
testability: AUTH_HELPED
[HYP] voip-api-ssrf-to-metadata
class: SSRF
asset: voip-management.easybell.de/api/
confidence: 45
reasoning: Spring backend behind nginx proxy may process user-supplied URLs in VoIP provisioning/webhook/callback endpoints (e.g., SIP trunk registration URLs, webhook callbacks, recording callbacks). Cloud metadata endpoint 169.254.169.254 reachable from typical VPC. No auth on JSON error path suggests some endpoints may be accessible.
evidence_needed: Discovery of any endpoint accepting URL parameters (webhook, callback, provisioning, recording, fetch); confirmation SSRF works to internal metadata.
verify_steps: After live resource found, test URL params with http://169.254.169.254/latest/meta-data/ (read-only HEAD/GET). Only if a URL-accepting endpoint is discovered passively first.
impact: Cloud metadata access → IAM keys, instance profile → Critical
testability: AUTH_HELPED
[PARKED] voip-api-ssrf-to-metadata: Confidence 45 < 60. No URL-accepting endpoint discovered yet; purely speculative without a live resource to test against. Requires voip-api-v2-bola to succeed first.
[FINAL] voip-api-v2-bola: 62 — Live reachable Spring backend confirmed, rewrite map leaked, highest-value in-scope surface. Justifies continued spaced enumeration.
[FINAL] my-portal-inertia-bola: 58 — Genuine high-value target but requires auth creds for full exploitation; passive route mapping justified now, AUTH_HELPED for depth.
[NEXT] PROBE: After >=60s cooldown from last probe, single GET https://voip-management.easybell.de/api/customer (spaced >=6s, <=1rps), watch for non-404 JSON (data or 401/403). If blocked/empty, back off 120s. Continue one resource name per probe: account, user, number, extension, subscriber, trunk, line, contract, invoice, sip, device, tariff.
[LEARN] ACCEPTED IDOR @ voip-management.easybell.de/api: nginx→Spring v2 rewrite map leaked via JSON 404 message (`/api/<res>` → `/api/v2/<res>`); live backend confirmed responsive.
[LEARN] ACCEPTED MISCONFIG @ voip-management.easybell.de: WAF/rate-limit aggressive — bursts of >~8 probes yield empty/timeouts; mandates >=6s spacing and 60-120s backoff.
[LEARN] ACCEPTED IDOR @ my.easybell.com: Real customer portal (Laravel/Vue Inertia) confirmed live; `customerId` leaked in Matomo; top IDOR candidate pending auth.
[LEARN] REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
[LEARN] REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.
[RISK] easybell: 60
reasoning: Live high-value VoIP JSON API surface confirmed reachable; upside solid. Elevated by: aggressive WAF rate-limiting tightening enumeration throughput, no creds for authenticated portal testing, program's auth/lockout exclusion limiting attack classes. Mitigated by read-only GET discipline, spaced probing, clear scope boundaries.
