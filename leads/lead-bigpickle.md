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
