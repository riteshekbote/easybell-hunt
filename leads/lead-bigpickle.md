## 2026-09-03 16:29:52 UTC [target] (model bigpickle)
[PRIO] auth.easybell.de,6.5,auth_surface:9+business_value:8+tech_exposure:7+gate_ease:4+cloud_surface:5+freshness:3
[PRIO] portal.easybell.de,6.0,auth_surface:8+business_value:9+tech_exposure:6+gate_ease:3+cloud_surface:4+freshness:3
[PRIO] dev.easybell.de,5.5,auth_surface:7+business_value:6+tech_exposure:8+gate_ease:7+cloud_surface:5+freshness:3
[PRIO] login.easybell.de,5.0,auth_surface:6+business_value:7+tech_exposure:5+gate_ease:3+cloud_surface:4+freshness:3
[PRIO] easybell.de,4.5,auth_surface:5+business_value:7+tech_exposure:4+gate_ease:6+cloud_surface:3+freshness:3
[PRIO] www.easybell.de,4.5,auth_surface:5+business_value:6+tech_exposure:4+gate_ease:6+cloud_surface:3+freshness:3
[PRIO] mail.easybell.de,4.0,auth_surface:4+business_value:5+tech_exposure:5+gate_ease:4+cloud_surface:4+freshness:3
[HYP] dev-staging-misconfiguration
class: MISCONFIG
asset: dev.easybell.de
confidence: 55
reasoning: dev/staging environments historically expose debug endpoints, admin panels, or unprotected APIs. Naming convention suggests internal dev infrastructure potentially exposed to internet.
evidence_needed: HTTP response from dev.easybell.de with status code, headers, any admin/debug pages
verify_steps: GET https://dev.easybell.de/ (HEAD fallback), GET https://dev.easybell.de/api/, GET https://dev.easybell.de/admin/, OPTIONS https://dev.easybell.de/
impact: Internal development data, test credentials, API keys, or admin access → High severity
testability: PASSIVE
[HYP] portal-idor-bola
class: IDOR
asset: portal.easybell.de
confidence: 45
reasoning: Customer portal likely has authenticated endpoints for account management, billing, service configuration. IDOR on account/user IDs could expose cross-tenant PII or enable unauthorized modifications.
evidence_needed: HTTP response with any API endpoints, user/account parameter patterns in URLs or requests
verify_steps: GET https://portal.easybell.de/, GET https://portal.easybell.de/api/, GET https://portal.easybell.de/account, OPTIONS https://portal.easybell.de/
impact: Cross-tenant PII exposure, unauthorized account changes → High severity
testability: AUTH_HELPED
[HYP] auth-oauth-flow
class: OATH
asset: auth.easybell.de
confidence: 40
reasoning: Authentication domain likely hosts OAuth/OIDC provider. Vulnerabilities in OAuth redirect_uri validation, state parameter, or JWT handling could enable account takeover chains.
evidence_needed: HTTP response with OAuth endpoints, JWKS, authorization server metadata
verify_steps: GET https://auth.easybell.de/.well-known/openid-configuration, GET https://auth.easybell.de/.well-known/oauth-authorization-server, GET https://auth.easybell.de/jwks, OPTIONS https://auth.easybell.de/
impact: Account takeover via OAuth flaws → Critical severity
testability: AUTH_HELPED
[PARKED] dev-staging-misconfiguration: Confidence 55 below 60 threshold for active probing without confirmed live HTTP. Re-evaluate after live probe confirms service.
[PARKED] portal-idor-bola: Confidence 45 below 60. Requires authenticated testing which cannot proceed without confirmed live HTTP and valid credentials.
[PARKED] auth-oauth-flow: Confidence 40 below 40 minimum. Also REJECTED-class adjacent (auth-bypass without PoC would fall under brute-force/lockout policy exclusion per scope).
[FINAL] dev-staging-misconfiguration: 55 — retain as top priority pending live confirmation
[FINAL] portal-idor-bola: 45 — retain as secondary, requires auth context
[FINAL] auth-oauth-flow: 40 — RETAIN with caveat: only test redirect_uri/state/JWT alg confusion, explicitly avoid brute-force/lockout
[NEXT] PROBE: GET https://dev.easybell.de/ (fallback: GET http://dev.easybell.de/) — confirm live HTTP, capture status/headers/server banner. Follow with GET https://portal.easybell.de/ and GET https://auth.easybell.de/ in same session. Rate: 1 req/sec.
[LEARN] REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing. Do not propose auth-stuffing or credential-stuffing hypotheses.
[LEARN] ACCEPTED MISCONFIG @ dev.easybell.de: Dev/staging environments commonly misconfigured; high priority for initial probe.
[LEARN] ACCEPTED IDOR @ portal.easybell.de: Customer portals are prime IDOR targets; retain pending auth context.
[RISK] easybell: 65
reasoning: Private program via bugs.olivermaicher.eu with clear scope and exclusions. 0/7 hosts confirmed live — may indicate infrastructure is behind CDN/WAF or uses non-standard ports. Risk elevated by: (1) no confirmed in-scope targets with live HTTP yet, (2) narrow reporting channel (single researcher portal), (3) explicit "no data modification" rule limits active testing depth. Mitigated by: clear scope boundaries, passive-first approach, standard bug bounty norms.
## 2026-09-03 19:35:29 UTC [target] (model bigpickle)
[NEW] my.easybell.com: real customer portal ("Easybell Kundenportal", Laravel 10 + Vue 3 Inertia SPA), 200 at /login, sets Laravel `ekp_session`+encrypted `XSRF-TOKEN`, `X-Inertia` header. Supersedes `portal.easybell.de` (dead). 
[NEW] voip-management.easybell.de: nginx front with live JSON REST API at /api/ ; custom Spring-style error `{"code":404,"message":"/api/v2/<path>"}`. Referenced as `VITE_VOIP_MANAGEMENT_URL` in portal SPA. 
[CHANGED] inventory 0/7 "not live" is stale: www(200 TYPO3), easybell(301), login(302->my), my.easybell.com(200), mail->rcm(200 Roundcube), auth(404 nginx), shared-libs(404 asset CDN), matomo, voip-management(API).
[CHANGED] dev.easybell.de / portal.easybell.de: no DNS/route — effectively dead; top target shifts to my.easybell.com + voip-management.
[PRIO] voip-management.easybell.de,7.6,auth_surface:8+business_value:9+tech_exposure:8+gate_ease:6+cloud_surface:6+freshness:5
[PRIO] my.easybell.com,7.1,auth_surface:8+business_value:9+tech_exposure:7+gate_ease:4+cloud_surface:5+freshness:5
[PRIO] mail.easybell.de,5.6,auth_surface:7+business_value:5+tech_exposure:6+gate_ease:5+cloud_surface:4+freshness:5
[PRIO] auth.easybell.de,4.9,auth_surface:6+business_value:7+tech_exposure:6+gate_ease:4+cloud_surface:4+freshness:4
[PRIO] www.easybell.de,4.6,auth_surface:4+business_value:6+tech_exposure:5+gate_ease:7+cloud_surface:3+freshness:5
[HYP] voip-api-v2-bola
class: IDOR
asset: voip-management.easybell.de/api/
confidence: 60
reasoning: API uses versioned path map /api/v2/ (echoed in 404 body). Serves customer VoIP/account data for the portal backend. Versioned REST + numeric/customer-scoped resources are classic BOLA candidates if object-scoped authorization is missing.
evidence_needed: discovery of real v2 endpoints and whether they respond without auth; any numeric id param pattern. Confirmed the backend is live (JSON 404, not nginx HTML).
verify_steps: GET https://voip-management.easybell.de/api/v2/account/ (needs un-block), OPTIONS https://voip-management.easybell.de/api/ to list Allow methods; enumerate v2 resource paths at <=1rps and look for non-404 JSON.
impact: cross-customer VoIP/account/PII exposure or unauthorized config change → High/Critical
testability: PASSIVE
[HYP] my-portal-idos
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Customer portal (Inertia/Laravel SPA) manages billing, SIP, service config. Root /login public. Authenticated object-scoped endpoints are prime BOLA surface; `customerId` param visible in Matomo tracker on every page. Cross-tenant risk high.
evidence_needed: authenticated session **cannot** be obtained (no creds). Passive: enumerate public/unauth Inertia routes and API proxies the SPA calls (voip-management base URL already leaked).
verify_steps: GET https://my.easybell.com/ (already 200), map SPA route table from fetched JS to catalog public endpoints. No mutating/auth tests without creds.
impact: cross-tenant PII dump, billing tamper → High/Critical
testability: AUTH_HELPED
[HYP] mail-rcm-logic
class: AUTH
asset: mail.easybell.de/rcm
confidence: 42
reasoning: Roundcube webmail exposed. Focus is on request-token / plugin logic and any exposed IMAP/SMTP action handlers; not username enumeration (REJECTED), not brute-force (REJECTED).
evidence_needed: non-default plugins/db handlers visible in HTML.
verify_steps: GET https://mail.easybell.de/rcm/?_task=login (done, 200) — catalog plugins/endpoints passively; no auth attempts.
impact: mailbox compromise / mail data exposure → Medium/High
testability: AUTH_HELPED
[PARKED] my-portal-idos: 55. Genuine target but requires auth credentials; passive-only now. AUTH_HELPED — park pending creds.
[PARKED] mail-rcm-logic: 42. Roundcube is standard OSS; no program-specific anomaly observed yet, near floor. Park.
[FINAL] voip-api-v2-bola: 60 — live backend confirmed, no auth gate observed on JSON error path, highest-value new surface. Active un-auth probing justified (GET/OPTIONS only).
[FINAL] auth-oauth-flow (carried): 40 — auth.easybell.de root 404 with no OAuth well-known; surface effectively dead → RETAIN park.
[FINAL] dev-staging-misconfiguration (carried): 55 — dev.easybell.de now confirmed non-routable; confidence drops.
[NEXT] PROBE: GET https://voip-management.easybell.de/api/account (single, after cool-down; current rate-limit 000s until WAF/backoff clears) → re-confirm JSON API; then GET https://voip-management.easybell.de/api/v2/account/ to test v2 map for a live resource. If 000 persists, back off 60s and retry once. Rate: <=1 rps.
[LEARN] ACCEPTED IDOR @ voip-management.easybell.de/api: unused high-value live API backend discovered via SPA env leak; versioned /api/v2 map is prime BOLA surface.
[LEARN] ACCEPTED IDOR @ my.easybell.com: portal.easybell.de replaced by actual portal my.easybell.com; top IDOR candidate pending auth.
[LEARN] REJECTED brute-force/lockout @ mail.easybell.de: do not test Roundcube login/auth attempts.
[RISK] easybell: 62
reasoning: Confirmed 6+ live in-scope hosts including a real customer portal (Laravel/Vue) and a live VoIP JSON API; raises reward upside. Elevated by: voip-management quickly began timing out after >~10 rapid probes (WAF/rate-limit present — must stay <=1rps), no creds available for authenticated IDOR testing on the highest-value portal surface, and program bans auth-related classes. Mitigated by passive-first, corporate-scope clarity, read-only GET/OPTIONS discipline.
## 2026-09-03 21:58:38 UTC [target] (model bigpickle)
[PRIO] auth.easybell.de,6.5,auth_surface:9+business_value:8+tech_exposure:7+gate_ease:4+cloud_surface:5+freshness:3
[PRIO] portal.easybell.de,6.0,auth_surface:8+business_value:9+tech_exposure:6+gate_ease:3+cloud_surface:4+freshness:3
[PRIO] dev.easybell.de,5.5,auth_surface:7+business_value:6+tech_exposure:8+gate_ease:7+cloud_surface:5+freshness:3
[PRIO] login.easybell.de,5.0,auth_surface:6+business_value:7+tech_exposure:5+gate_ease:3+cloud_surface:4+freshness:3
[PRIO] easybell.de,4.5,auth_surface:5+business_value:7+tech_exposure:4+gate_ease:6+cloud_surface:3+freshness:3
[PRIO] www.easybell.de,4.5,auth_surface:5+business_value:6+tech_exposure:4+gate_ease:6+cloud_surface:3+freshness:3
[PRIO] mail.easybell.de,4.0,auth_surface:4+business_value:5+tech_exposure:5+gate_ease:4+cloud_surface:4+freshness:3
[HYP] dev-staging-misconfiguration
class: MISCONFIG
asset: dev.easybell.de
confidence: 55
reasoning: dev/staging environments historically expose debug endpoints, admin panels, or unprotected APIs. Naming convention suggests internal dev infrastructure potentially exposed to internet.
evidence_needed: HTTP response from dev.easybell.de with status code, headers, any admin/debug pages
verify_steps: GET https://dev.easybell.de/ (HEAD fallback), GET https://dev.easybell.de/api/, GET https://dev.easybell.de/admin/, OPTIONS https://dev.easybell.de/
impact: Internal development data, test credentials, API keys, or admin access → High severity
testability: PASSIVE
[HYP] portal-idor-bola
class: IDOR
asset: portal.easybell.de
confidence: 45
reasoning: Customer portal likely has authenticated endpoints for account management, billing, service configuration. IDOR on account/user IDs could expose cross-tenant PII or enable unauthorized modifications.
evidence_needed: HTTP response with any API endpoints, user/account parameter patterns in URLs or requests
verify_steps: GET https://portal.easybell.de/, GET https://portal.easybell.de/api/, GET https://portal.easybell.de/account, OPTIONS https://portal.easybell.de/
impact: Cross-tenant PII exposure, unauthorized account changes → High severity
testability: AUTH_HELPED
[HYP] auth-oauth-flow
class: OATH
asset: auth.easybell.de
confidence: 40
reasoning: Authentication domain likely hosts OAuth/OIDC provider. Vulnerabilities in OAuth redirect_uri validation, state parameter, or JWT handling could enable account takeover chains.
evidence_needed: HTTP response with OAuth endpoints, JWKS, authorization server metadata
verify_steps: GET https://auth.easybell.de/.well-known/openid-configuration, GET https://auth.easybell.de/.well-known/oauth-authorization-server, GET https://auth.easybell.de/jwks, OPTIONS https://auth.easybell.de/
impact: Account takeover via OAuth flaws → Critical severity
testability: AUTH_HELPED
[PARKED] dev-staging-misconfiguration: Confidence 55 below 60 threshold for active probing without confirmed live HTTP. Re-evaluate after live probe confirms service.
[PARKED] portal-idor-bola: Confidence 45 below 60. Requires authenticated testing which cannot proceed without confirmed live HTTP and valid credentials.
[PARKED] auth-oauth-flow: Confidence 40 below 40 minimum. Also REJECTED-class adjacent (auth-bypass without PoC would fall under brute-force/lockout policy exclusion per scope).
[FINAL] dev-staging-misconfiguration: 55 — retain as top priority pending live confirmation
[FINAL] portal-idor-bola: 45 — retain as secondary, requires auth context
[FINAL] auth-oauth-flow: 40 — RETAIN with caveat: only test redirect_uri/state/JWT alg confusion, explicitly avoid brute-force/lockout
[NEXT] PROBE: GET https://dev.easybell.de/ (fallback: GET http://dev.easybell.de/) — confirm live HTTP, capture status/headers/server banner. Follow with GET https://portal.easybell.de/ and GET https://auth.easybell.de/ in same session. Rate: 1 req/sec.
[LEARN] REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing. Do not propose auth-stuffing or credential-stuffing hypotheses.
[LEARN] ACCEPTED MISCONFIG @ dev.easybell.de: Dev/staging environments commonly misconfigured; high priority for initial probe.
[LEARN] ACCEPTED IDOR @ portal.easybell.de: Customer portals are prime IDOR targets; retain pending auth context.
[RISK] easybell: 65
reasoning: Private program via bugs.olivermaicher.eu with clear scope and exclusions. 0/7 hosts confirmed live — may indicate infrastructure is behind CDN/WAF or uses non-standard ports. Risk elevated by: (1) no confirmed in-scope targets with live HTTP yet, (2) narrow reporting channel (single researcher portal), (3) explicit "no data modification" rule limits active testing depth. Mitigated by: clear scope boundaries, passive-first approach, standard bug bounty norms.
[NEW] my.easybell.com: real customer portal ("Easybell Kundenportal", Laravel 10 + Vue 3 Inertia SPA), 200 at /login, sets Laravel `ekp_session`+encrypted `XSRF-TOKEN`, `X-Inertia` header. Supersedes `portal.easybell.de` (dead). 
[NEW] voip-management.easybell.de: nginx front with live JSON REST API at /api/ ; custom Spring-style error `{"code":404,"message":"/api/v2/<path>"}`. Referenced as `VITE_VOIP_MANAGEMENT_URL` in portal SPA. 
[CHANGED] inventory 0/7 "not live" is stale: www(200 TYPO3), easybell(301), login(302->my), my.easybell.com(200), mail->rcm(200 Roundcube), auth(404 nginx), shared-libs(404 asset CDN), matomo, voip-management(API).
[CHANGED] dev.easybell.de / portal.easybell.de: no DNS/route — effectively dead; top target shifts to my.easybell.com + voip-management.
[PRIO] voip-management.easybell.de,7.6,auth_surface:8+business_value:9+tech_exposure:8+gate_ease:6+cloud_surface:6+freshness:5
[PRIO] my.easybell.com,7.1,auth_surface:8+business_value:9+tech_exposure:7+gate_ease:4+cloud_surface:5+freshness:5
[PRIO] mail.easybell.de,5.6,auth_surface:7+business_value:5+tech_exposure:6+gate_ease:5+cloud_surface:4+freshness:5
[PRIO] auth.easybell.de,4.9,auth_surface:6+business_value:7+tech_exposure:6+gate_ease:4+cloud_surface:4+freshness:4
[PRIO] www.easybell.de,4.6,auth_surface:4+business_value:6+tech_exposure:5+gate_ease:7+cloud_surface:3+freshness:5
[HYP] voip-api-v2-bola
class: IDOR
asset: voip-management.easybell.de/api/
confidence: 60
reasoning: API uses versioned path map /api/v2/ (echoed in 404 body). Serves customer VoIP/account data for the portal backend. Versioned REST + numeric/customer-scoped resources are classic BOLA candidates if object-scoped authorization is missing.
evidence_needed: discovery of real v2 endpoints and whether they respond without auth; any numeric id param pattern. Confirmed the backend is live (JSON 404, not nginx HTML).
verify_steps: GET https://voip-management.easybell.de/api/v2/account/ (needs un-block), OPTIONS https://voip-management.easybell.de/api/ to list Allow methods; enumerate v2 resource paths at <=1rps and look for non-404 JSON.
impact: cross-customer VoIP/account/PII exposure or unauthorized config change → High/Critical
testability: PASSIVE
[HYP] my-portal-idos
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Customer portal (Inertia/Laravel SPA) manages billing, SIP, service config. Root /login public. Authenticated object-scoped endpoints are prime BOLA surface; `customerId` param visible in Matomo tracker on every page. Cross-tenant risk high.
evidence_needed: authenticated session **cannot** be obtained (no creds). Passive: enumerate public/unauth Inertia routes and API proxies the SPA calls (voip-management base URL already leaked).
verify_steps: GET https://my.easybell.com/ (already 200), map SPA route table from fetched JS to catalog public endpoints. No mutating/auth tests without creds.
impact: cross-tenant PII dump, billing tamper → High/Critical
testability: AUTH_HELPED
[HYP] mail-rcm-logic
class: AUTH
asset: mail.easybell.de/rcm
confidence: 42
reasoning: Roundcube webmail exposed. Focus is on request-token / plugin logic and any exposed IMAP/SMTP action handlers; not username enumeration (REJECTED), not brute-force (REJECTED).
evidence_needed: non-default plugins/db handlers visible in HTML.
verify_steps: GET https://mail.easybell.de/rcm/?_task=login (done, 200) — catalog plugins/endpoints passively; no auth attempts.
impact: mailbox compromise / mail data exposure → Medium/High
testability: AUTH_HELPED
[PARKED] my-portal-idos: 55. Genuine target but requires auth credentials; passive-only now. AUTH_HELPED — park pending creds.
[PARKED] mail-rcm-logic: 42. Roundcube is standard OSS; no program-specific anomaly observed yet, near floor. Park.
[FINAL] voip-api-v2-bola: 60 — live backend confirmed, no auth gate observed on JSON error path, highest-value new surface. Active un-auth probing justified (GET/OPTIONS only).
[FINAL] auth-oauth-flow (carried): 40 — auth.easybell.de root 404 with no OAuth well-known; surface effectively dead → RETAIN park.
[FINAL] dev-staging-misconfiguration (carried): 55 — dev.easybell.de now confirmed non-routable; confidence drops.
[NEXT] PROBE: GET https://voip-management.easybell.de/api/account (single, after cool-down; current rate-limit 000s until WAF/backoff clears) → re-confirm JSON API; then GET https://voip-management.easybell.de/api/v2/account/ to test v2 map for a live resource. If 000 persists, back off 60s and retry once. Rate: <=1 rps.
[LEARN] ACCEPTED IDOR @ voip-management.easybell.de/api: unused high-value live API backend discovered via SPA env leak; versioned /api/v2 map is prime BOLA surface.
[LEARN] ACCEPTED IDOR @ my.easybell.com: portal.easybell.de replaced by actual portal my.easybell.com; top IDOR candidate pending auth.
[LEARN] REJECTED brute-force/lockout @ mail.easybell.de: do not test Roundcube login/auth attempts.
[RISK] easybell: 62
reasoning: Confirmed 6+ live in-scope hosts including a real customer portal (Laravel/Vue) and a live VoIP JSON API; raises reward upside. Elevated by: voip-management quickly began timing out after >~10 rapid probes (WAF/rate-limit present — must stay <=1rps), no creds available for authenticated IDOR testing on the highest-value portal surface, and program bans auth-related classes. Mitigated by passive-first, corporate-scope clarity, read-only GET/OPTIONS discipline.
[NEW] voip-management.easybell.de routing map resolved: `/api/<res>` → proxied to Spring backend (returns Spring JSON 404 `{"code":404,"message":"/api/v2/<res>"}` revealing internal v2 rewrite); `/api/` and `/api/v2/` → plain nginx HTML 404. So the live surface is reached via `/api/<resource>` (nginx rewrites to /api/v2/), not `/api/v2/` directly.
[CHANGED] voip-management WAF: aggressive rate-limit confirmed. Bursts of >~8-10 rapid probes → empty/timed-out responses. Must space probes >=5-6s, back off 60s after block.
[CHANGED] voip-api-v2-bola: no live (non-404) Spring resource discovered yet across customer/account/number/user/subscriber probes — all nginx-HTML or rate-limited. Backend is reachable and versioned but actual resource names still unknown.
[PRIO] voip-management.easybell.de,7.6,auth_surface:8+business_value:9+tech_exposure:8+gate_ease:6+cloud_surface:6+freshness:5
[PRIO] my.easybell.com,7.1,auth_surface:8+business_value:9+tech_exposure:7+gate_ease:4+cloud_surface:5+freshness:5
[HYP] voip-api-v2-bola
class: IDOR
asset: voip-management.easybell.de/api/
confidence: 62
reasoning: Live Spring-style JSON API confirmed reachable via `/api/<res>` rewrite to internal `/api/v2/<res>` (error body leaks rewrite map). Versioned REST + customer VoIP/account resources = classic BOLA if object-scoped authz missing. Backend actively responds to unmatched paths with structured JSON, strong signal of an active app not a passive static host.
evidence_needed: at least one REAL v2 resource name returning non-404 (JSON data or 401/403 auth challenge), and whether it responds unauthenticated; any numeric id path param.
verify_steps: after 60s+ cooldown, single spaced probes (>=6s apart, <=1rps) of `/api/<resource>` for likely names (customer, account, user, number, extension, subscriber, trunk, line, contract, invoice, sip, device, tariff) watching for any non-404/non-nginx response; prefer `?` params. No auth bypass/mutation.
impact: cross-customer VoIP/account/PII exposure or unauthorized config access → High/Critical
testability: AUTH_HELPED
[HYP] my-portal-idos (carried)
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Customer portal Laravel/Vue Inertia SPA; `customerId` visible in Matomo tracker; proxies voip-management for backend. Auth-scoped object endpoints prime BOLA surface.
evidence_needed: authenticated session cannot be obtained (no creds). Passive route table mapping only.
verify_steps: map public Inertia/API routes from fetched SPA bundle.
impact: cross-tenant PII dump/billing tamper → High/Critical
testability: AUTH_HELPED
[PARKED] my-portal-idos: 55. Genuine but requires auth creds; passive-only now. AUTH_HELPED.
[PARKED] mail-rcm-logic: 42. Standard Roundcube, no program-specific anomaly; near floor.
[FINAL] voip-api-v2-bola: 62 — live reachable Spring backend confirmed, rewrite map leaked, highest-value in-scope surface. Justify spaced continued enumeration.
[FINAL] auth-oauth-flow (carried): 40 — auth.easybell.de root/well-known all 404; surface dead.
[FINAL] dev-staging-misconfiguration (carried): 55 — dev.easybell.de non-routable; dropped.
[NEXT] PROBE: after >=60s cooldown, single GET https://voip-management.easybell.de/api/customer (spaced >=6s, <=1rps), watch for any non-404 JSON (data or 401/403). If blocked, back off 120s. Continue spaced enumeration of one resource name per probe.
[LEARN] ACCEPTED IDOR @ voip-management.easybell.de/api: nginx→Spring v2 rewrite map leaked via JSON 404 message (`/api/<res>` → `/api/v2/<res>`); live backend confirmed responsive.
[LEARN] ACCEPTED MISCONFIG @ voip-management.easybell.de: WAF/rate-limit aggressive — bursts of >~8 probes yield empty/timeouts; mandates >=6s spacing and 60-120s backoff.
[RISK] easybell: 60
reasoning: Live high-value surface (VoIP JSON API reachable) confirmed; upside solid. Elevated by aggressive WAF rate-limiting limiting enumeration throughput and slowing discovery, plus no creds for authenticated portal testing and program's ban on auth/lockout classes. Mitigated by read-only GET discipline, spaced probing, clear scope.
[HYP] voip-api-v2-bola
class: IDOR
asset: voip-management.easybell.de/api/
confidence: 62
reasoning: Live Spring-style JSON API reachable via `/api/<res>` rewrite to internal `/api/v2/<res>` (error body leaks v2 rewrite map). Versioned REST + customer VoIP/account resources are classic BOLA if object-scoped authz missing. Backend actively responds to unmatched paths with structured JSON — active app, not static host.
evidence_needed: at least one real v2 resource returning non-404 JSON (data or 401/403 challenge) unauthenticated; numeric id param pattern.
verify_steps: after 60s+ cooldown, single spaced probes (>=6s apart, <=1rps) of `/api/<resource>` for likely names (customer, account, user, number, extension, subscriber, trunk, line, contract, invoice, sip, device, tariff); no auth bypass/mutation.
impact: cross-customer VoIP/account/PII exposure or unauthorized config access → High/Critical
testability: AUTH_HELPED
[NEXT] PROBE: after >=60s cooldown, single GET https://voip-management.easybell.de/api/customer (spaced >=6s, <=1rps), watch for non-404 JSON (data or 401/403). If blocked, back off 120s. Continue one resource name per probe.
[RISK] easybell: 60
reasoning: Live reachable high-value VoIP JSON API surface confirmed; upside solid. Elevated by aggressive WAF rate-limiting tightening enumeration throughput, no creds for authenticated portal testing, and program's auth/lockout exclusion. Mitigated by read-only GET discipline, spaced probing, clear scope.
## 2026-09-03 23:44:15 UTC [target] (model bigpickle)
## 2026-09-04 02:34:38 UTC [target] (model bigpickle)
[HYP] voip-cors-cred-exfil
class: MISCONFIG
asset: voip-management.easybell.de/api/
confidence: 68
reasoning: OPTIONS+GET on `/api/accounts|numbers|subscribers` (401 Sipwise data routes) reflect arbitrary Origin in ACAO with `Access-Control-Allow-Credentials:true`, while other paths (`/api/account`, `/api/session`) lock origin to `https://my.easybell.com` — a per-path permit-list inconsistency where the Sipwise-proxy layer is un-scoped. If a victim browser holds an authenticated session to voip-management (cached Basic for realm `sipwisebroker.easybell.de` or a voip-management cookie from the portal flow), any malicious origin can issue a credentialed GET and read VoIP/account JSON cross-origin.
evidence_needed: victim-side authenticated session to voip-management reachable cross-origin by a browser (cookie-based or cached-Basic) + read of `/api/accounts|numbers|subscribers` with that session.
verify_steps: ACAO-* + credentials reflection CONFIRMED. Full-read exploit requires a victim with an active voip-management session (HUMAN authenticated). No unauth read possible (401 without creds).
impact: cross-origin theft of VoIP numbers/subscribers/account data from an authenticated customer session → High
testability: AUTH_HELPED
[HYP] voip-api-v2-bola
class: IDOR
asset: voip-management.easybell.de/api/accounts|numbers|subscribers
confidence: 55
reasoning: Sipwise NGCP-style backend; singular paths 404 but plural live auth-gated (accounts/numbers/subscribers). If per-object authorization is missing, a valid session token could read any customer's objects. Surface is 401-gated; no creds to test cross-customer enumeration.
evidence_needed: valid voipSession token (obtainable after portal login) to test numeric id enumeration on `/api/accounts/{id}` etc.
verify_steps: HUMAN — with creds, enumerate numeric IDs on live plural routes, verify per-object authz. No unauth passive test possible (401).
impact: cross-customer Sipwise/phone-number/PII exposure → High/Critical
testability: AUTH_HELPED
[HYP] my-portal-idos
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Laravel/Vue Inertia portal maps proxies `/api/strapi|crm|ebit` (302→/login) and proxies voip-management via Bearer `voipSession`. Authenticated object endpoints (Users/New, Subsidiary, UserManagement, phone numbers, billing) prime BOLA surface.
evidence_needed: authenticated session.
verify_steps: HUMAN — with creds, exercise Users/Subsidiary/phone-number object endpoints for cross-tenant access.
impact: cross-tenant PII/billing/SIP tamper → High/Critical
testability: AUTH_HELPED
## 2026-09-04 07:25:44 UTC [target] (model bigpickle)
[PRIO] voip-management.easybell.de/api/, 9.2, attack_surface=9 business_value=9 tech_exposure=7 gate_ease=5 cloud_surface=4 freshness=9
[PRIO] my.easybell.com, 7.8, attack_surface=8 business_value=9 tech_exposure=6 gate_ease=3 cloud_surface=3 freshness=8
[PRIO] auth.easybell.de, 2.0, attack_surface=2 business_value=5 tech_exposure=2 gate_ease=1 cloud_surface=1 freshness=2
[HYP] voip-cors-cred-exfil
class: MISCONFIG
asset: voip-management.easybell.de/api/
confidence: 68
reasoning: Confirmed per-path CORS inconsistency: plural routes (accounts, numbers, subscribers) reflect arbitrary Origin in ACAO with Credentials:true; singular routes (account, session) lock to my.easybell.com origin. Live Sipwise backend confirmed on plural routes (401).
evidence_needed: victim-side authenticated session to voip-management reachable cross-origin by browser
verify_steps: HUMAN - with creds, test cross-origin read of /api/accounts|numbers|subscribers from malicious origin with credentials:true
impact: cross-origin theft of VoIP numbers/subscribers/account data from authenticated customer session → High
testability: AUTH_HELPED
[HYP] voip-api-v2-bola
class: IDOR
asset: voip-management.easybell.de/api/accounts|numbers|subscribers
confidence: 62
reasoning: Sipwise NGCP-style backend; plural routes return 401 (live auth-gated). If per-object authorization missing, valid token could enumerate cross-customer data. v2 rewrite map leaked via 404 body.
evidence_needed: valid voipSession token (obtainable after portal login) to test numeric id enumeration
verify_steps: HUMAN - with creds, enumerate numeric IDs on live plural routes, verify per-object authz
impact: cross-customer Sipwise/phone-number/PII exposure → High/Critical
testability: AUTH_HELPED
[HYP] my-portal-idos
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Laravel/Vue Inertia SPA; customerId leaked in Matomo; proxies voip-management via Bearer voipSession; auth-gated object endpoints (Users/Subsidiary/phone-number) prime BOLA surface.
evidence_needed: authenticated session to portal
verify_steps: HUMAN - with creds, exercise Users/Subsidiary/phone-number object endpoints for cross-tenant access
impact: cross-tenant PII/billing/SIP tamper → High/Critical
testability: AUTH_HELPED
[PARKED] my-portal-idos: 55. Genuine but requires auth creds; passive-only now. AUTH_HELPED.
[PARKED] mail-rcm-logic: 42. Standard Roundcube, no program-specific anomaly; near floor.
[PARKED] auth-oauth-flow: 40. auth.easybell.de root/well-known all 404; surface dead.
[PARKED] dev-staging-misconfiguration: 55. dev.easybell.de non-routable; dropped.
[FINAL] voip-cors-cred-exfil: 68 — CONFIRMED per-path CORS inconsistency; highest confidence. Victim session required.
[FINAL] voip-api-v2-bola: 62 — live Sipwise backend confirmed; auth required to test cross-tenant enumeration.
[NEXT] PROBE: after WAF cooldown cleared, test CORS reflection on additional Sipwise-style endpoints: single GET https://voip-management.easybell.de/api/subscribers (spaced >=6s, <=1rps) with Origin: https://evil.com, verify ACAO reflects evil.com + Allow-Credentials:true. If 401 + CORS reflected, pattern confirmed across broader surface. If rate-limited, back off 120s.
[LEARN] ACCEPTED MISCONFIG @ voip-management.easybell.de/api: Per-path CORS inconsistency confirmed; plural Sipwise routes (accounts/numbers/subscribers) reflect arbitrary Origin with Credentials:true; singular routes lock to my.easybell.com.
[LEARN] ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending auth.
[LEARN] ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pending auth.
[LEARN] REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
[LEARN] REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.
[RISK] easybell: 65
reasoning: Live high-value VoIP API surface confirmed with CORS misconfiguration on plural Sipwise routes (reflects arbitrary Origin + Credentials:true). Upside solid for authenticated victim scenario. Elevated by aggressive WAF rate-limiting limiting enumeration throughput, no creds for authenticated portal testing, and program's auth/lockout exclusion. Mitigated by read-only GET discipline, spaced probing, clear scope. CORS finding is HIGH impact but requires victim browser session.
## 2026-09-04 12:16:11 UTC [target] (model bigpickle)
[PRIO] voip-management.easybell.de/api/,7.6,attack_surface=9 business_value=9 tech_exposure=7 gate_ease=5 cloud_surface=4 freshness=9
[PRIO] my.easybell.com,6.7,attack_surface=8 business_value=9 tech_exposure=6 gate_ease=3 cloud_surface=3 freshness=8
[PRIO] auth.easybell.de,2.5,attack_surface=2 business_value=5 tech_exposure=2 gate_ease=1 cloud_surface=1 freshness=2
[HYP] voip-cors-cred-exfil
class: MISCONFIG
asset: voip-management.easybell.de/api/
confidence: 68
reasoning: Confirmed per-path CORS inconsistency: plural routes (accounts, numbers, subscribers) reflect arbitrary Origin in ACAO with Credentials:true; singular routes (account, session) lock to my.easybell.com origin. Live Sipwise backend confirmed on plural routes (401).
evidence_needed: victim-side authenticated session to voip-management reachable cross-origin by browser
verify_steps: HUMAN - with creds, test cross-origin read of /api/accounts|numbers|subscribers from malicious origin with credentials:true
impact: cross-origin theft of VoIP numbers/subscribers/account data from authenticated customer session → High
testability: AUTH_HELPED
[HYP] my-portal-idos
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Laravel/Vue Inertia SPA; customerId leaked in Matomo; proxies voip-management via Bearer voipSession; auth-gated object endpoints (Users/Subsidiary/phone-number) prime BOLA surface.
evidence_needed: authenticated session to portal
verify_steps: HUMAN - with creds, exercise Users/Subsidiary/phone-number object endpoints for cross-tenant access
impact: cross-tenant PII/billing/SIP tamper → High/Critical
testability: AUTH_HELPED
[PARKED] voip-api-v2-bola: superseded by voip-cors-cred-exfil for same asset (higher confidence).
[FINAL] voip-cors-cred-exfil: 68
[FINAL] my-portal-idos: 55
[NEXT] PROBE: single GET https://my.easybell.com/ with header `X-Inertia: true` (spaced >=6s, <=1rps) to retrieve the Inertia page data (JSON) and look for exposed customer data or API endpoints.
[LEARN] No new learnings from this analysis cycle.
[RISK] easybell: 65
reasoning: Live high-value VoIP API surface confirmed with CORS misconfiguration on plural Sipwise routes (reflects arbitrary Origin + Credentials:true). Upside solid for authenticated victim scenario. Elevated by aggressive WAF rate-limiting limiting enumeration throughput, no creds for authenticated portal testing, and program's auth/lockout exclusion. Mitigated by read-only GET discipline, spaced probing, clear scope. CORS finding is HIGH impact but requires victim browser session.
## 2026-09-04 16:31:50 UTC [target] (model bigpickle)
[CHANGED] voip-management.easybell.de/api CORS: knowledge base claimed singular routes lock to my.easybell.com — **FALSE**. `account`, `subscriber`, `number` (singular) ALL return `ACAO: <evil.com> + ACAC:true` (Spring JSON 404 with CORS). Only nginx-only routes (customer, user, extension, trunk, etc.) lack CORS headers. CORS surface is broader than previously thought.
[NEW] my.easybell.com internal API proxy endpoints `/api/crm`, `/api/ebit`, `/api/strapi` — ALL return `Access-Control-Allow-Origin: *` (no ACAC:true) on both redirect and OPTIONS preflight. Accepts POST with `Authorization,Content-Type` from any origin.
[NEW] Internal k8s hostname leaked in client JS bundle: `voip-management.k8s.easybell.de/api` — fallback value in `core.js` when `VITE_VOIP_MANAGEMENT_URL` env is unset.
[NEW] `my.easybell.com/api/strapi` — Strapi CMS proxy endpoint confirmed, same wildcard CORS pattern.
[CHANGED] voip-management.easybell.de/api CORS surface: Spring-handled routes confirmed (404 JSON): account, accounts, subscriber, subscribers, number, numbers, session. Nginx-only routes (HTML 404, no CORS): customer, user, extension, trunk, line, contract, invoice, sip, device, tariff.
[PRIO] voip-management.easybell.de/api,8.0,attack_surface=9 business_value=9 tech_exposure=7 gate_ease=5 cloud_surface=4 freshness=9
[PRIO] my.easybell.com,7.5,attack_surface=9 business_value=9 tech_exposure=6 gate_ease=3 cloud_surface=3 freshness=9
[PRIO] auth.easybell.de,2.5,attack_surface=2 business_value=5 tech_exposure=2 gate_ease=1 cloud_surface=1 freshness=2
[HYP] voip-cors-cred-exfil-v2
class: MISCONFIG
asset: voip-management.easybell.de/api/
confidence: 88
reasoning: CORS surface broader than previously mapped. ALL Spring-handled routes (account, accounts, subscriber, subscribers, number, numbers, session) reflect arbitrary Origin in ACAO with Credentials:true. Singular routes are NOT locked to my.easybell.com as knowledge base stated. An authenticated user's browser session (Bearer voipSession) can be exfiltrated cross-origin from any of these endpoints by a malicious page. 7 distinct endpoints confirmed vulnerable.
evidence_needed: victim-side authenticated session; confirm authenticated response body contains cross-customer data
verify_steps: HUMAN — with valid creds, visit https://evil.com while authenticated to my.easybell.com; evil.com JS makes fetch('https://voip-management.easybell.de/api/accounts', {credentials:'include'}), reads response. Alternatively: confirm portal JS flow reads these endpoints cross-origin.
impact: Cross-origin theft of VoIP accounts/numbers/subscribers/session data from authenticated customer → HIGH
testability: AUTH_HELPED
[HYP] my-portal-api-proxy-wildcard
class: MISCONFIG
asset: my.easybell.com/api/{crm,ebit,strapi}
confidence: 78
reasoning: Three internal portal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return ACAO:* on redirect responses and OPTIONS preflight with POST + Authorization+Content-Type allowed from any origin. Wildcard without ACAC:true means cookies NOT sent cross-origin, BUT the portal uses Bearer tokens via JS (not cookies) for voip-management. If an attacker can exfiltrate the Bearer token (via XSS or CORS on voip-management), the wildcard on portal proxy endpoints allows exfiltration of CRM/EBIT/Strapi data too.
evidence_needed: confirm what /api/crm, /api/ebit, /api/strapi proxy to when authenticated; confirm whether Bearer token is accepted by these endpoints
verify_steps: HUMAN — with creds, observe portal JS network calls to /api/crm and /api/ebit; capture request/response to determine if Bearer token is used and what data is returned
impact: CRM/EBIT/Strapi data leakage via cross-origin requests → MEDIUM/HIGH (depends on data sensitivity)
testability: AUTH_HELPED
[HYP] internal-k8s-hostname-leak
class: MISCONFIG
asset: my.easybell.com (core.js client bundle)
confidence: 65
reasoning: Client-side JS bundle (core.js) contains hardcoded fallback URL `https://voip-management.k8s.easybell.de/api` — an internal Kubernetes service hostname. This reveals internal infrastructure topology (k8s cluster, internal DNS naming). While not directly exploitable from external network, it aids targeted attacks if any internal network access is available (SSRF, VPN, etc.), and may indicate misconfigured env at build time.
evidence_needed: confirm k8s.easybell.de is not externally routable; check if any subdomain takeover or DNS rebinding possible
verify_steps: PASSIVE — DNS lookup k8s.easybell.de; check if it resolves to private IP or if zone is available for registration
impact: Internal infrastructure info disclosure → LOW/MEDIUM
testability: PASSIVE
[FINAL] voip-cors-cred-exfil-v2: 88 — CONFIRMED on 7 endpoints; broader than previously mapped. Highest priority. Requires victim browser session.
[PARKED] my-portal-api-proxy-wildcard: 78 — Wildcard CORS without ACAC:true on portal proxies is less critical than voip-management's ACAC:true pattern. Requires authenticated context to assess full impact.
[PARKED] internal-k8s-hostname-leak: 65 — Info disclosure only; no direct exploit path. Low actionable value.
[NEXT] HUMAN: With authenticated session to my.easybell.com, test cross-origin exfiltration of VoIP data. Open browser console on attacker-controlled origin (or use curl with Bearer token). Make: `fetch('https://voip-management.easybell.de/api/accounts', {credentials:'include'})`. Verify: (1) response body contains customer VoIP account data, (2) response accessible from attacker origin, (3) same for /api/numbers, /api/subscribers, /api/account, /api/number, /api/subscriber, /api/session. Report with CORS header screenshot + response body snippet as POC for HIGH-impact credential-backed CORS misconfiguration.
[LEARN] ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, accounts, subscriber, subscribers, number, numbers, session) reflect arbitrary Origin with Credentials:true. Knowledge base claim "singular routes lock to my.easybell.com" is incorrect.
[LEARN] ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorization+Content-Type allowed from any origin (OPTIONS preflight 204). Wildcard CORS without Credentials:true on portal proxy layer.
[LEARN] ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js).
[LEARN] No new REJECTED items.
[RISK] easybell: 68
reasoning: voip-management CORS misconfiguration confirmed on 7 Spring-handled routes with ACAC:true — HIGH impact with victim browser session. Portal proxy wildcard CORS adds secondary exfiltration path. Internal k8s hostname leak aids reconnaissance. Elevated by: no creds available for authenticated testing, WAF rate-limiting limits probe throughput, program excludes brute-force/lockout. Mitigated by: read-only GET only, clear scope, CORS finding requires victim interaction.
## 2026-09-04 19:07:01 UTC [target] (model bigpickle)
## 2026-09-04 21:34:41 UTC [target] (model bigpickle)
[HYP] voip-cors-cred-exfil-v3
class: MISCONFIG
asset: voip-management.easybell.de/api/
confidence: 92
reasoning: All 7 Spring/Basic-auth routes reflect arbitrary Origin with ACAC:true (confirmed prior cycles). This cycle confirmed auth mechanism = HTTP Basic realm "sipwisebroker.easybell.de,voip-management", which browsers cache per-origin and transparently attach to cross-origin `credentials:'include'` fetches. No cookie session exists (/api/session: 405 GET, no Set-Cookie). Chain is browser-native: victim logs into portal/VoIP surface (Basic creds cached) → visits evil.com → `fetch('/api/accounts',{credentials:'include'})` → server returns 200 customer data with ACAO:evil.com+ACAC:true → attacker JS reads VoIP accounts/numbers/subscribers/session JSON.
evidence_needed: authenticated response body confirmation (with valid Basic/Bearer creds, response to /api/accounts must contain cross-customer data + reflect CORS headers on the 200).
verify_steps: HUMAN — while authenticated to my.easybell.com/voip-management in a browser, open attacker origin and run `fetch('https://voip-management.easybell.de/api/accounts',{credentials:'include'}).then(r=>r.text())`; verify readable body + `Access-Control-Allow-Credentials:true`. Repeat for numbers, subscribers, account, number, subscriber, session.
impact: Cross-origin theft of full VoIP/account/subscriber dataset of any authenticated customer → HIGH (PII/telephony).
testability: AUTH_HELPED
[HYP] my-portal-idos
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Laravel/Vue Inertia portal; customerId in Matomo; X-Inertia props show customer-type flags only (no leak); proxies voip-management via Bearer voipSession; auth-gated object endpoints (Users/Subsidiary/phone-number) are prime BOLA surface. No creds → passive-only.
evidence_needed: authenticated session; cross-tenant object access on Users/Subsidiary/phone-number endpoints.
verify_steps: HUMAN — with creds, exercise object endpoints across two tenants for cross-tenant reads.
impact: cross-tenant PII/billing/SIP tamper → High/Critical.
testability: AUTH_HELPED
[HYP] my-portal-api-proxy-wildcard
class: MISCONFIG
asset: my.easybell.com/api/{crm,ebit,strapi}
confidence: 78
reasoning: Three portal proxy endpoints return ACAO:* + POST/Authorization/Content-Type preflight from any origin (no ACAC:true → cookies not sent cross-origin). Impact only if these accept a JS-held Bearer token that an attacker already controls/exfiltrates (secondary to the voip-management CORS finding) or if any response contains data gated only by Authorization absence.
evidence_needed: what /api/crm, /api/ebit, /api/strapi proxy to when authenticated; whether Bearer token is accepted.
verify_steps: HUMAN — capture portal JS network calls to /api/crm and /api/ebit post-auth; test cross-origin POST from attacker origin with attacker-supplied bearer.
impact: CRM/EBIT/Strapi data via cross-origin → MEDIUM/HIGH.
testability: AUTH_HELPED
reasoning: #1 finding (voip-management credentialed CORS exfil) now has a browser-native, mechanically-confirmed exploit chain (HTTP Basic realm → cached creds → cross-origin `credentials:'include'`), verified across 7 endpoints incl. /api/session; rising to POC-ready. Elevators: 401 body confirms auth gate so unauth read impossible (needs victim session → HUMAN); WAF rate-limits enumeration; no creds for authenticated portal IDOR testing; program excludes brute-force/auth classes. Mitigated by read-only GET/OPTIONS discipline, clear in-scope corporate assets, single clear reporting path.
## 2026-09-04 23:17:46 UTC [target] (model bigpickle)
[NEW] Passive DNS (2026-09-04 23:15 UTC): `voip-management.k8s.easybell.de` and `k8s.easybell.de` return NO public A record (NXDOMAIN/empty). Internal k8s hostname leak from core.js is NOT externally resolvable — no DNS-takeover or DNS-rebinding surface; downgrades internal-k8s-hostname-leak.
[NEW] `my.easybell.com` and `voip-management.easybell.de` share public IP 62.27.117.123 (one nginx ingress); `easybell.de` → 62.27.117.125. The "cross-origin" split between portal and VoIP API is host-header-only at the same ingress.
[CHANGED] Passive surface saturated: all three top leads (CORS exfil 92 / proxy-wildcard 78 / portal IDOR 55) are AUTH_HELPED and unchanged since 21:34. Only unprobed passive surface left = Spring actuator/route-map disclosure on the voip-management ingress. Last live probe 21:34:58 UTC (~105 min ago) — WAF backoff window cleared.
[PRIO] voip-management.easybell.de/api,8.3,attack_surface:9+business_value:9+tech_exposure:9+gate_ease:7+cloud_surface:6+freshness:8
[PRIO] my.easybell.com,7.3,attack_surface:8+business_value:9+tech_exposure:8+gate_ease:4+cloud_surface:5+freshness:7
[PRIO] mail.easybell.de,5.6,attack_surface:7+business_value:5+tech_exposure:6+gate_ease:5+cloud_surface:4+freshness:5
[HYP] voip-spring-actuator-route-map
class: MISCONFIG
asset: voip-management.easybell.de/api/
confidence: 50
reasoning: Live Spring JSON backend behind nginx confirmed (rewrite `/api/<res>`→`/api/v2/<res>` leaked in 404 body). 22 v1 resource names probed — all nginx HTML 404, actual v2 names opaque. Spring Boot apps commonly expose `/actuator`; `/actuator/mappings` or, if Spring Cloud Gateway, `/actuator/gateway/routes` discloses the complete internal route table, ending the v2-name opacity and giving BOLA the exact `(path,method)` surface.
evidence_needed: non-nginx JSON response (Spring-formatted) on any actuator path — concretely a 2xx/401/403 on `/api/actuator`, `/api/v2/actuator`, or `/actuator` instead of nginx HTML 404.
verify_steps: After >=120s cooldown (last probe 21:34:58), spaced >=6s single GETs: `/api/actuator`, `/api/v2/actuator`, `/api/actuator/mappings`, `/api/actuator/gateway/routes`, `/actuator`. Spring JSON => dump `/api/actuator/mappings` for full v2 route map. Report route-topology existence only; do NOT exfiltrate `/actuator/env` secrets.
impact: Full internal Spring route topology (v2 resource names/methods) disclosed → converts opaque BOLA surface into testable cross-tenant VoIP/account/NGC endpoints → HIGH enabler.
testability: PASSIVE
[HYP] my-portal-api-proxy-wildcard
class: MISCONFIG
asset: my.easybell.com/api/{crm,ebit,strapi}
confidence: 78
reasoning: Three portal proxy endpoints return `Access-Control-Allow-Origin:*` + OPTIONS allowing POST/Authorization/Content-Type from any origin (no ACAC:true → cookies not forwarded cross-origin; portal uses JS Bearer for voip-management). If any of these accept the JS-held bearer/voipSession, an attacker who extracts a token (via the confirmed voip-management CORS exfil) can read CRM/EBIT/Strapi through the wildcard proxy.
evidence_needed: authenticated request/response to `/api/crm` + `/api/ebit` showing Bearer acceptance and proxied data; cross-origin readability.
verify_steps: HUMAN — capture portal JS network calls to `/api/crm`,`/api/ebit` post-auth (method, headers, body, response); then from attacker origin POST with attacker-supplied/or stolen bearer and confirm readable response.
impact: CRM/EBIT/Strapi data leakage via cross-origin reads once Bearer is obtained → MEDIUM/HIGH.
testability: AUTH_HELPED
[HYP] my-portal-idos
class: IDOR
asset: my.easybell.com
confidence: 55
reasoning: Laravel 10 + Vue 3 Inertia portal; `customerId` in Matomo tracker; proxies 8 plural Sipwise routes to voip-management with Bearer from voipSession; auth-gated object endpoints (accounts/subscribers/numbers/call-forwardings/voicemail/trusted-ips) use numeric IDs — classic BOLA surface. No creds → passive-only this cycle.
evidence_needed: authenticated cross-tenant reads on Users/Subsidiary/phone-number + proxied Sipwise object endpoints.
verify_steps: HUMAN — with two tenants, swap numeric object IDs on read (GET) endpoints and compare responses.
impact: cross-tenant PII/billing/SIP config access → HIGH/CRITICAL.
testability: AUTH_HELPED
[PARKED] internal-k8s-hostname-leak: NEW passive DNS shows no public A record for voip-management.k8s.easybell.de / k8s.easybell.de — not externally resolvable, no takeover path; confidence drops below 40.
[PARKED] voip-api-ssrf-to-metadata: still no URL-accepting endpoint discovered; dependent on route discovery succeeding.
[PARKED] voip-api-v2-bola: 55 — resumes only if actuator/mappings or a live v2 resource is found.
[FINAL] voip-cors-cred-exfil-v3: 92 — CONFIRMED on 7 Spring-handled routes (ACAC:true reflection); blocks only on authenticated HUMAN POC.
[FINAL] my-portal-api-proxy-wildcard: 78 — wildcard proxy CORS on portal layer; secondary exfil path.
[FINAL] voip-spring-actuator-route-map: 50 — new, concrete, credential-free; single cheapest way to unlock BOLA.
[NEXT] PROBE: After >=120s WAF cooldown, GET `https://voip-management.easybell.de/api/actuator` with `Origin: https://my.easybell.com`; then spaced >=6s: `/api/v2/actuator`, `/api/actuator/mappings`, `/api/actuator/gateway/routes`, `/actuator`. If any returns Spring JSON (vs nginx HTML 404), follow with GET `/api/actuator/mappings` to extract the full `/api/v2/*` route table for BOLA enumeration. If blocked/empty, back off 120s.
[LEARN] ACCEPTED MISCONFIG @ voip-management.easybell.de: Passive DNS confirms `voip-management.k8s.easybell.de` and `k8s.easybell.de` have NO public A record — internal hostname leak is not externally resolvable; downgraded.
[LEARN] ACCEPTED MISCONFIG @ easybell.de: my.easybell.com + voip-management.easybell.de share ingress IP 62.27.117.123 (easybell.de → 62.27.117.125); portal↔VoIP origin split is host-header-only at same nginx.
[LEARN] No new REJECTED items.
[RISK] easybell: 70
reasoning: Leading finding (voip-management credentialed CORS exfil, 7 endpoints) confirmed but POC-blocked on HUMAN session; new passive actuator probe line could unlock the opaque v2 BOLA map at zero credential cost. Elevated by: WAF throttles enumeration, no creds for portal IDOR, auth/lockout classes excluded. Mitigated by read-only GET/OPTIONS discipline, >=6s spacing, clear scope.
## 2026-09-05 01:06:55 UTC [target] (model bigpickle)
## 2026-09-05 05:55:38 UTC [target] (model bigpickle)
