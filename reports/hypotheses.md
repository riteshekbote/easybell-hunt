# Hypotheses (ranked)

## RANKED HYPOTHESES 2026-09-02 21:54:05 UTC

## RANKED HYPOTHESES 2026-09-02 23:47:09 UTC

## RANKED HYPOTHESES 2026-09-03 02:32:15 UTC

## RANKED HYPOTHESES 2026-09-03 07:23:53 UTC

## RANKED HYPOTHESES 2026-09-03 12:16:38 UTC

## RANKED HYPOTHESES 2026-09-03 16:49:23 UTC
- [55] dev.easybell.de: dev-staging-misconfiguration (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://dev.easybell.de/ (fallback: GET http://dev.easybell.de/) — confirm live HTTP, capture status/headers/server banner. Follow with GET https://p
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing. Do not propose auth-stuffing or cred
- LEARN: ACCEPTED MISCONFIG @ dev.easybell.de: Dev/staging environments commonly misconfigured; high priority for initial probe.
- LEARN: ACCEPTED IDOR @ portal.easybell.de: Customer portals are prime IDOR targets; retain pending auth context.

## RANKED HYPOTHESES 2026-09-03 19:45:37 UTC
- [60] voip-management.easybell.de/api/: voip-api-v2-bola (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://voip-management.easybell.de/api/account (single, after cool-down; current rate-limit 000s until WAF/backoff clears) → re-confirm JSON API; th
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: unused high-value live API backend discovered via SPA env leak; versioned /api/v2 map is prime BOLA surface.
- LEARN: ACCEPTED IDOR @ my.easybell.com: portal.easybell.de replaced by actual portal my.easybell.com; top IDOR candidate pending auth.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-03 21:58:47 UTC
- [55] dev.easybell.de: dev-staging-misconfiguration (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://dev.easybell.de/ (fallback: GET http://dev.easybell.de/) — confirm live HTTP, capture status/headers/server banner. Follow with GET https://p
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing. Do not propose auth-stuffing or cred
- LEARN: ACCEPTED MISCONFIG @ dev.easybell.de: Dev/staging environments commonly misconfigured; high priority for initial probe.
- LEARN: ACCEPTED IDOR @ portal.easybell.de: Customer portals are prime IDOR targets; retain pending auth context.
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: unused high-value live API backend discovered via SPA env leak; versioned /api/v2 map is prime BOLA surface.
- LEARN: ACCEPTED IDOR @ my.easybell.com: portal.easybell.de replaced by actual portal my.easybell.com; top IDOR candidate pending auth.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: do not test Roundcube login/auth attempts.
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: nginx→Spring v2 rewrite map leaked via JSON 404 message (`/api/<res>` → `/api/v2/<res>`); live backend confirme
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de: WAF/rate-limit aggressive — bursts of >~8 probes yield empty/timeouts; mandates >=6s spacing and 60-120s backo

## RANKED HYPOTHESES 2026-09-03 23:45:55 UTC
- [62] voip-management.easybell.de/api/: voip-api-v2-bola (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: After >=60s cooldown from last probe, single GET https://voip-management.easybell.de/api/customer (spaced >=6s, <=1rps), watch for non-404 JSON (data or 
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: nginx→Spring v2 rewrite map leaked via JSON 404 message (`/api/<res>` → `/api/v2/<res>`); live backend confirme
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de: WAF/rate-limit aggressive — bursts of >~8 probes yield empty/timeouts; mandates >=6s spacing and 60-120s backo
- LEARN: ACCEPTED IDOR @ my.easybell.com: Real customer portal (Laravel/Vue Inertia) confirmed live; `customerId` leaked in Matomo; top IDOR candidate pending auth.
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-04 02:34:48 UTC
- [68] voip-management.easybell.de/api/: voip-cors-cred-exfil (from art/lead_bigpickle.txt)
- [60] voip-management.easybell.de/api/: voip-api-v2-bola (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: After >=120s cooldown from last probe (2026-09-03 23:45:57), single GET https://voip-management.easybell.de/api/extension (spaced >=6s, <=1rps), watch fo
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: nginx→Spring v2 rewrite map leaked via JSON 404 message (`/api/<res>` → `/api/v2/<res>`); live backend confirme
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de: WAF/rate-limit aggressive — bursts >~8 probes yield empty/timeouts; mandates >=6s spacing and 60-120s backoff.
- LEARN: ACCEPTED IDOR @ my.easybell.com: Real customer portal (Laravel/Vue Inertia) confirmed live; `customerId` leaked in Matomo; top IDOR candidate pending auth.
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-04 07:26:02 UTC
- [68] voip-management.easybell.de/api/: voip-cors-cred-exfil (from art/lead_bigpickle.txt)
- [60] voip-management.easybell.de/api/: voip-api-v2-bola (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: Single GET https://voip-management.easybell.de/api/extension (spaced >=6s, <=1rps), watch for non-404 JSON (data or 401/403). If blocked/empty, back off 
- NEXT(hypotheses-bigpickle.txt): PROBE: after WAF cooldown cleared, test CORS reflection on additional Sipwise-style endpoints: single GET https://voip-management.easybell.de/api/subscribers (s
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: nginx→Spring v2 rewrite map leaked via JSON 404 message (`/api/<res>` → `/api/v2/<res>`); live backend confirme
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de: WAF/rate-limit aggressive — bursts >~8 probes yield empty/timeouts; mandates >=6s spacing and 60-120s backoff.
- LEARN: ACCEPTED IDOR @ my.easybell.com: Real customer portal (Laravel/Vue Inertia) confirmed live; `customerId` leaked in Matomo; top IDOR candidate pending auth.
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: Per-path CORS inconsistency confirmed; plural Sipwise routes (accounts/numbers/subscribers) reflect arbitr
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-04 12:29:49 UTC
- [85] voip-management.easybell.de/api/: voip-cors-cred-exfil (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: single GET https://my.easybell.com/ with header `X-Inertia: true` (spaced >=6s, <=1rps) to retrieve the Inertia page data (JSON) and look for exposed cus
- NEXT(hypotheses-nemotron3.txt): PROBE: Single GET https://voip-management.easybell.de/api/accounts with `Origin: https://my.easybell.com` header (spaced >=6s from last), watch for ACAO + ACAC:
- LEARN: No new learnings from this analysis cycle.
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: nginx→Spring v2 rewrite map leaked via JSON 404 message (`/api/<res>` → `/api/v2/<res>`); live backend confirme
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de: WAF/rate-limit aggressive — bursts >~8 probes yield empty/timeouts; mandates >=6s spacing and 60-120s backoff.
- LEARN: ACCEPTED IDOR @ my.easybell.com: Real customer portal (Laravel/Vue Inertia) confirmed live; `customerId` leaked in Matomo; top IDOR candidate pending auth.
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: Per-path CORS inconsistency confirmed; plural Sipwise routes (accounts/numbers/subscribers) reflect arbitr
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend

## RANKED HYPOTHESES 2026-09-04 16:34:56 UTC
- [88] voip-management.easybell.de/api/: voip-cors-cred-exfil-v2 (from art/lead_bigpickle.txt)
- [85] voip-management.easybell.de/api/: voip-cors-cred-exfil (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: With authenticated session to my.easybell.com, test cross-origin exfiltration of VoIP data. Open browser console on attacker-controlled origin (or use cu
- NEXT(hypotheses-nemotron3.txt): PROBE: Single GET https://voip-management.easybell.de/api/accounts with `Origin: https://my.easybell.com` header (spaced >=6s from last), watch for ACAO + ACAC:
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, ac
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorizati
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js).
- LEARN: No new REJECTED items.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: Per-path CORS inconsistency confirmed; plural Sipwise routes (accounts/numbers/subscribers) reflect arbitr
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-04 19:13:07 UTC
- [88] voip-management.easybell.de/api/: voip-cors-cred-exfil-v2 (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: With authenticated session to my.easybell.com, test cross-origin exfiltration of VoIP data. Open browser console on attacker-controlled origin (or use cu
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, ac
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorizati
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js).
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-04 21:34:53 UTC
- [92] voip-management.easybell.de/api/: voip-cors-cred-exfil-v3 (from art/lead_bigpickle.txt)
- [88] voip-management.easybell.de/api/: voip-cors-cred-exfil-v2 (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET to https://voip-management.easybell.de/api/v2/accounts with header `Origin: https://my.easybell.com` (>=6s from last probe), watch for Spring 
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, ac
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorizati
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js).
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-04 23:18:21 UTC
- [92] voip-management.easybell.de/api/: voip-cors-cred-exfil-v3 (from art/lead_nemotron3.txt)
- [50] voip-management.easybell.de/api/: voip-spring-actuator-route-map (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: After >=120s WAF cooldown, GET `https://voip-management.easybell.de/api/actuator` with `Origin: https://my.easybell.com`; then spaced >=6s: `/api/v2/actu
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET (≥6s from last) to `https://voip-management.easybell.de/api/v2/customers` with header `Origin: https://my.easybell.com` — watch for Spring JSO
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de: Passive DNS confirms `voip-management.k8s.easybell.de` and `k8s.easybell.de` have NO public A record — interna
- LEARN: ACCEPTED MISCONFIG @ easybell.de: my.easybell.com + voip-management.easybell.de share ingress IP 62.27.117.123 (easybell.de → 62.27.117.125); portal↔VoIP origin
- LEARN: No new REJECTED items.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, ac
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorizati
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js). Not
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-05 01:07:06 UTC
- [92] voip-management.easybell.de/api/: voip-cors-cred-exfil-v3 (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET (≥6s from last) to `https://voip-management.easybell.de/api/v2/customers` with header `Origin: https://my.easybell.com` — watch for Spring JSO
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, ac
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorizati
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js). Not
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-05 05:55:47 UTC
- [92] voip-management.easybell.de/api/: voip-cors-cred-exfil-v3 (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET (≥6s from last probe at 2026-09-05 01:07:09 UTC) to `https://voip-management.easybell.de/api/actuator` with header `Origin: https://my.easybel
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, ac
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorizati
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js). Not
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-05 09:51:21 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-exfil-v3 (from art/lead_bigpickle.txt)
- [65] voip-management.easybell.de/api/actuator: voip-spring-actuator-route-map (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://voip-management.easybell.de/api/actuator with Header `Origin: https://my.easybell.com` — spaced ≥6s from each subsequent probe to /api/v2/act
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET (≥6s from last probe at 2026-09-05 01:07:09 UTC) to `https://voip-management.easybell.de/api/actuator` with header `Origin: https://my.easybel
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface confirmed across ALL Spring-handled routes (singular + plural: account, accounts, subscriber,
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: /api/crm, /api/ebit, /api/strapi return ACAO:* wildcard without ACAC:true — preflight 200, POST+Authorization+Content-
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked in core.js as fallback URL; NXDOMAIN via passive DNS — 
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies 8 plural Sipwise routes to voip-management; auth-gated object endpoin
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface broader than knowledge base stated. ALL Spring-handled routes (singular + plural: account, ac
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: Internal proxy endpoints (/api/crm, /api/ebit, /api/strapi) return Access-Control-Allow-Origin:* with POST+Authorizati
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (core.js). Not
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies voip-management; auth-gated object endpoints; top IDOR candidate pend
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-05 13:13:48 UTC
- [92] voip-management.easybell.de/api/: voip-spring-actuator-route-map (from art/lead_bigpickle.txt)
- [92] voip-management.easybell.de/api/: voip-cors-cred-exfil-v3 (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: GET https://voip-management.easybell.de/api/actuator with Header `Origin: https://my.easybell.com` — spaced ≥6s from each subsequent probe to /api/v2/act
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET (≥6s from last probe at 2026-09-05 01:07:09 UTC) to `https://voip-management.easybell.de/api/actuator` with header `Origin: https://my.easybel
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface confirmed across ALL Spring-handled routes (singular + plural: account, accounts, subscriber,
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: /api/crm, /api/ebit, /api/strapi return ACAO:* wildcard without ACAC:true — preflight 200, POST+Authorization+Content-
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked in core.js as fallback URL; NXDOMAIN via passive DNS — 
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies 8 plural Sipwise routes to voip-management; auth-gated object endpoin
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: Spring actuator route-map hypothesis DISPROVEN by direct probe — /api/actuator, /api/v2/actuator, /api/act
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS credentialed reflection live-reconfirmed (13:12 UTC) on /api/account — Origin https://evil.example.at
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: /api/{crm,ebit,strapi} wildcard ACAO:* without ACAC:true remains the secondary (token-gated) exfil path — unchanged.
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api + my.easybell.com: BOLA + portal IDOR remain confirmed-class but credential-gated; no passive vector left to adv
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: program excludes auth-stuffing/brute-force/lockout — still no new information.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS surface confirmed across ALL Spring-handled routes (singular + plural: account, accounts, subscriber,
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: /api/crm, /api/ebit, /api/strapi return ACAO:* wildcard without ACAC:true — preflight 200, POST+Authorization+Content-
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked in core.js as fallback URL; NXDOMAIN via passive DNS — 
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api: Sipwise NGCP backend live; plural routes 401-auth-gated; v2 rewrite map leaked; BOLA surface confirmed pending 
- LEARN: ACCEPTED IDOR @ my.easybell.com: Laravel/Vue Inertia portal; customerId in Matomo; proxies 8 plural Sipwise routes to voip-management; auth-gated object endpoin
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing.
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts.

## RANKED HYPOTHESES 2026-09-05 16:10:13 UTC
- [92] voip-management.easybell.de/api/: voip-cors-cred-exfil-v3 (from art/lead_nemotron3.txt)
- [42] my.easybell.com: my-laravel-misconfig-surface (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: POST-13:13:54UTC cooldown done → spaced ≥6s, ≤1rps, GET-only: 1) https://my.easybell.com/.env (expect 200 PHP env vs 403/404 block), 2) https://my.easybe
- NEXT(hypotheses-nemotron3.txt): HUMAN: File consolidated report for voip-cors-cred-exfil-v3 (92) and my-portal-api-proxy-wildcard-exfil (82) with verified CORS evidence; request credentialed t
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Laravel dotfile/debug misconfig surface (.env, /.git, /telescope, /_ignition) confirmed untested across all prior cycles —
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: Actuator re-probed 13:13:54 UTC — all paths nginx HTML 404; Spring Boot actuator definitively not exposed;
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: OpenAPI/swagger unprobed — next (and last) passive doc-disclosure line, confidence floor 40.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS credentialed reflection live-reconfirmed (13:12 UTC) on /api/account — Origin https://evil.example.at
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: /api/{crm,ebit,strapi} wildcard ACAO:* without ACAC:true remains the secondary (token-gated) exfil path — unchanged
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api + my.easybell.com: BOLA + portal IDOR remain confirmed-class but credential-gated; no passive vector left to adv
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: Spring actuator route-map hypothesis DISPROVEN by direct probe — /api/actuator, /api/v2/actuator, /api/act
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: program excludes auth-stuffing/brute-force/lockout — still no new information
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts

## RANKED HYPOTHESES 2026-09-05 18:33:14 UTC
- [65] my.easybell.com: my-laravel-misconfig-surface (from art/lead_nemotron3.txt)
- [45] order-form.easybell.de/api: order-form-unauth-api-surface (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: Passive depth on order-form: GET https://order-form.easybell.de/ → extract all referenced JS chunks → grep `/api/` and endpoint strings → single spaced G
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET (≥6s from last probe at 2026-09-05 13:13:54 UTC) to `https://my.easybell.com/.env` — watch for 200 with PHP/env content (APP_KEY, DB_*, MAIL_*
- LEARN: REJECTED MISCONFIG @ my.easybell.com: Laravel dotfile/debug surface DISPROVEN (18:21 UTC) — /.env, /.git/config, /telescope, /horizon, /_ignition/health-check, 
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: OpenAPI/swagger line closed (18:22 UTC) — /api/v2/api-docs, /api/swagger-ui.html, /api/openapi.json, /api/
- LEARN: ACCEPTED MISCONFIG @ easybell.de: CT sweep (18:24 UTC, crt.sh DoH-verified) shows 18 live A-record subdomains never in inventory; "passive surface exhausted" wa
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de: Vite SPA bundle (index-BiM9ZwNg.js, 18:30 UTC) leaks /api/ base, live POST-only /api/apc/check (GET→405), partner.e
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: /authenticate → OIDC redirect to external Keycloak (dstny.d4sp.com, client_id=coven, response_type=code) with in-scop
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com: Laravel dotfile/debug misconfig surface (.env, /.git, /telescope, /_ignition) confirmed untested across all prior cycles —
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: Spring OpenAPI/swagger (springfox `/v2/api-docs`, springdoc `/v3/api-docs`, `/swagger-ui.html`, `/openapi.
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: Actuator re-probed 13:13:54 UTC — all paths nginx HTML 404; Spring Boot actuator definitively not exposed;
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS credentialed reflection live-reconfirmed (13:12 UTC) on /api/account — Origin https://evil.example.at
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: /api/{crm,ebit,strapi} wildcard ACAO:* without ACAC:true remains the secondary (token-gated) exfil path — unchanged
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api + my.easybell.com: BOLA + portal IDOR remain confirmed-class but credential-gated; no passive vector left to adv
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: program excludes auth-stuffing/brute-force/lockout — still no new information
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts

## RANKED HYPOTHESES 2026-09-05 20:47:39 UTC
- [72] order-form.easybell.de/api: order-form-unauth-data-exposure (from art/lead_bigpickle.txt)
- [70] order-form.easybell.de/api: order-form-unauth-api-surface (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: Single GET `https://partner.easybell.de/login` → extract script/css asset paths → fetch referenced JS (read-only, ≥6s spacing, ≤1rps) → grep `/api/`, `VI
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET ≥6s from last probe (2026-09-05 18:33:33 UTC) → `GET https://order-form.easybell.de/` → extract all referenced JS chunk URLs from HTML → for e
- LEARN: ACCEPTED MISCONFIG @ easybell.de: CT sweep (18:24 UTC, crt.sh DoH-verified) shows 18 live A-record subdomains never in inventory; "passive surface exhausted" wa
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de: Vite SPA bundle (index-BiM9ZwNg.js, 18:30 UTC) leaks `/api/` base, live POST-only `/api/apc/check` (GET→405), partn
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: `/authenticate` → OIDC redirect to external Keycloak (dstny.d4sp.com, client_id=coven, response_type=code) with in-sc
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: 200 → `/login` partner portal on main ingress (shared nginx) — unprobed surface
- LEARN: REJECTED MISCONFIG @ my.easybell.com: Laravel dotfile/debug surface DISPROVEN (18:21 UTC) — `/.env`, `/.git/config`, `/telescope`, `/horizon`, `/_ignition/healt
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: OpenAPI/swagger line closed (18:22 UTC) — `/api/v2/api-docs`, `/api/swagger-ui.html`, `/api/openapi.json`,
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS credentialed reflection live-reconfirmed (13:12 UTC) on `/api/account` — Origin `https://evil.example
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: `/api/{crm,ebit,strapi}` wildcard ACAO:* without ACAC:true remains secondary (token-gated) exfil path — unchanged
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api + my.easybell.com: BOLA + portal IDOR remain confirmed-class but credential-gated; no passive vector left to adv
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: program excludes auth-stuffing/brute-force/lockout — still no new information
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts

## RANKED HYPOTHESES 2026-09-05 22:40:34 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_bigpickle.txt)
- [75] order-form.easybell.de/api: order-form-unauth-api-data-exposure (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File the voip CORS report at bugs.olivermaicher.eu — primary finding voip-cors-cred-read-write; PoC = both OPTIONS preflight captures (ACAO:<evil-origin>
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET ≥6s from last probe (2026-09-05 18:33:33 UTC) → `GET https://order-form.easybell.de/` → extract all referenced JS chunk URLs from HTML → for e
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ easybell.de: CT sweep (18:24 UTC, crt.sh DoH-verified) shows 18 live A-record subdomains never in inventory; "passive surface exhausted" wa
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de: Vite SPA bundle (index-BiM9ZwNg.js, 18:30 UTC) leaks `/api/` base, live POST-only `/api/apc/check` (GET→405), partn
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: `/authenticate` → OIDC redirect to external Keycloak (dstny.d4sp.com, client_id=coven, response_type=code) with in-sc
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: 200 → `/login` partner portal on main ingress (shared nginx) — unprobed surface
- LEARN: REJECTED MISCONFIG @ my.easybell.com: Laravel dotfile/debug surface DISPROVEN (18:21 UTC) — `/.env`, `/.git/config`, `/telescope`, `/horizon`, `/_ignition/healt
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: OpenAPI/swagger line closed (18:22 UTC) — `/api/v2/api-docs`, `/api/v3/api-docs`, `/api/swagger-ui.html`, 
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS credentialed reflection live-reconfirmed (13:12 UTC) on `/api/account` — Origin `https://evil.example
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: `/api/{crm,ebit,strapi}` wildcard ACAO:* without ACAC:true remains secondary (token-gated) exfil path — unchanged
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api + my.easybell.com: BOLA + portal IDOR remain confirmed-class but credential-gated; no passive vector left to adv
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: program excludes auth-stuffing/brute-force/lockout — still no new information
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts

## RANKED HYPOTHESES 2026-09-06 00:15:09 UTC
- [78] order-form.easybell.de/api: order-form-unauth-api-data-exposure (from art/lead_nemotron3.txt)
- [40] partner.easybell.de: partner-portal-api-leak (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: Single GET `https://partner.easybell.de/login` → extract script/css asset paths → fetch referenced JS (read-only, ≥6s spacing, ≤1rps) → grep `/api/`, `VI
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET ≥6s from last probe (2026-09-05 18:33:33 UTC) → `GET https://order-form.easybell.de/` → extract all referenced JS chunk URLs from HTML → for e
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: ACCEPTED MISCONFIG @ easybell.de: CT sweep (18:24 UTC, crt.sh DoH-verified) shows 18 live A-record subdomains never in inventory; "passive surface exhausted" wa
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de: Vite SPA bundle (index-BiM9ZwNg.js, 18:30 UTC) leaks `/api/` base, live POST-only `/api/apc/check` (GET→405), partn
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: `/authenticate` → OIDC redirect to external Keycloak (dstny.d4sp.com, client_id=coven, response_type=code) with in-sc
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: 200 → `/login` partner portal on main ingress (shared nginx) — unprobed surface
- LEARN: REJECTED MISCONFIG @ my.easybell.com: Laravel dotfile/debug surface DISPROVEN (18:21 UTC) — `/.env`, `/.git/config`, `/telescope`, `/horizon`, `/_ignition/healt
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: OpenAPI/swagger line closed (18:22 UTC) — `/api/v2/api-docs`, `/api/v3/api-docs`, `/api/swagger-ui.html`, 
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS credentialed reflection live-reconfirmed (13:12 UTC) on `/api/account` — Origin `https://evil.example
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: `/api/{crm,ebit,strapi}` wildcard ACAO:* without ACAC:true remains secondary (token-gated) exfil path — unchanged
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api + my.easybell.com: BOLA + portal IDOR remain confirmed-class but credential-gated; no passive vector left to adv
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: program excludes auth-stuffing/brute-force/lockout — still no new information
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts

## RANKED HYPOTHESES 2026-09-06 04:48:17 UTC
- [78] order-form.easybell.de/api: order-form-unauth-api-data-exposure (from art/lead_nemotron3.txt)
- [50] order-form.easybell.de/api: order-form-unauth-business-logic (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write at bugs.olivermaicher.eu — PoC = OPTIONS preflight captures 22:37–22:38 UTC on /api/account + /api/subscribers (ACAO:<evil
- NEXT(hypotheses-nemotron3.txt): PROBE: Spaced GET ≥6s from last probe (2026-09-05 18:33:33 UTC) → `GET https://order-form.easybell.de/` → extract all referenced JS chunk URLs from HTML → for e
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: chunk audit (index-BiM9ZwNg.js + 20 lazy, 04:47 UTC) maps full anonymous API — GET plans/<code> 200 JSON tariff
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: ACCEPTED MISCONFIG @ easybell.de: CT sweep (18:24 UTC, crt.sh DoH-verified) shows 18 live A-record subdomains never in inventory; "passive surface exhausted" wa
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de: Vite SPA bundle (index-BiM9ZwNg.js, 18:30 UTC) leaks `/api/` base, live POST-only `/api/apc/check` (GET→405), partn
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: `/authenticate` → OIDC redirect to external Keycloak (dstny.d4sp.com, client_id=coven, response_type=code) with in-sc
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: 200 → `/login` partner portal on main ingress (shared nginx) — unprobed surface
- LEARN: REJECTED MISCONFIG @ my.easybell.com: Laravel dotfile/debug surface DISPROVEN (18:21 UTC) — `/.env`, `/.git/config`, `/telescope`, `/horizon`, `/_ignition/healt
- LEARN: REJECTED MISCONFIG @ voip-management.easybell.de/api: OpenAPI/swagger line closed (18:22 UTC) — `/api/v2/api-docs`, `/api/v3/api-docs`, `/api/swagger-ui.html`, 
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS credentialed reflection live-reconfirmed (13:12 UTC) on `/api/account` — Origin `https://evil.example
- LEARN: ACCEPTED MISCONFIG @ my.easybell.com/api: `/api/{crm,ebit,strapi}` wildcard ACAO:* without ACAC:true remains secondary (token-gated) exfil path — unchanged
- LEARN: ACCEPTED IDOR @ voip-management.easybell.de/api + my.easybell.com: BOLA + portal IDOR remain confirmed-class but credential-gated; no passive vector left to adv
- LEARN: REJECTED brute-force/lockout @ auth.easybell.de: program excludes auth-stuffing/brute-force/lockout — still no new information
- LEARN: REJECTED brute-force/lockout @ mail.easybell.de: Do not test Roundcube login/auth attempts

## RANKED HYPOTHESES 2026-09-06 09:16:14 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write at bugs.olivermaicher.eu — PoC = OPTIONS preflight captures 22:37–22:38 UTC on /api/account + /api/subscribers (ACAO:<evil
- NEXT(hypotheses-nemotron3.txt): HUMAN: File the voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes a
- LEARN: NO_DELTA — no new passive probes since 2026-09-05 18:33:33 UTC; all inventory + knowledge base unchanged; hypotheses stable.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.

## RANKED HYPOTHESES 2026-09-06 12:57:35 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write at bugs.olivermaicher.eu — PoC = OPTIONS preflight captures 22:37–22:38 UTC on /api/account + /api/subscribers (ACAO:<evil
- NEXT(hypotheses-nemotron3.txt): HUMAN: File the voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes a
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.

## RANKED HYPOTHESES 2026-09-06 16:06:00 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write at bugs.olivermaicher.eu — PoC = OPTIONS preflight captures 22:37–22:38 UTC on /api/account + /api/subscribers (ACAO:<evil
- NEXT(hypotheses-nemotron3.txt): HUMAN: File the voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes a
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; all inventory + knowledge base unchanged; hypotheses stable.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-06 18:05:28 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write at bugs.olivermaicher.eu — PoC = OPTIONS preflight captures 22:37-22:38 UTC on /api/account + /api/subscribers (ACAO:<evil
- NEXT(hypotheses-nemotron3.txt): HUMAN: File the voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes a
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; all inventory + knowledge base unchanged; hypotheses stable.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-06 20:12:49 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write at bugs.olivermaicher.eu — PoC = OPTIONS preflight captures 22:37-22:38 UTC on /api/account + /api/subscribers (ACAO:<evil
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; all inventory + knowledge base unchanged; hypotheses stable; no accept/reject deltas this cycle.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-06 22:10:24 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- [40] connectme-app.easybell.de: connectme-oidc-state-binding (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write at bugs.olivermaicher.eu — PoC = OPTIONS preflight captures 22:37–22:38 UTC on /api/account + /api/subscribers (ACAO:<evil
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; all inventory + knowledge base unchanged; hypotheses stable.
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; all inventory + knowledge base unchanged; hypotheses stable.
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; all inventory + knowledge base unchanged; hypotheses stable; no accept/reject deltas this cycle.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; inventory + knowledge base unchanged; hypotheses stable.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: flagship finding re-scored VALID by triage 19:19:02 UTC — formal validate-and-file gate is the only remain
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-06 23:59:05 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-07 03:19:31 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- [45] connectme-app-uat.easybell.de: connectme-uat-dev-misconfig (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — fields: (1) Title "Credentialed CORS read+write on voip-management.easybell.de/api (7 Sp
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: flagship finding re-scored VALID by triage 19:19:02 UTC — formal validate-and-file gate is the only remain
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; inventory + knowledge base unchanged; hypotheses stable.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-07 08:30:20 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — fields: (1) Title "Credentialed CORS read+write on voip-management.easybell.de/api (7 Sp
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; inventory + knowledge base unchanged; hypotheses stable; no accept/reject deltas this cycle.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-07 14:28:32 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — fields: (1) Title "Credentialed CORS read+write on voip-management.easybell.de/api (7 Sp
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; inventory + knowledge base unchanged; hypotheses stable; no accept/reject deltas this cycle.

## RANKED HYPOTHESES 2026-09-07 18:54:03 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-07 21:53:36 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — fields: (1) Title "Credentialed CORS read+write on voip-management.easybell.de/api (7 Sp
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: NO_DELTA — no new passive probes since 2026-09-06 04:48:35 UTC; inventory + knowledge base unchanged; hypotheses stable; no accept/reject deltas this cycle.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-07 23:54:26 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- [45] connectme-app-uat.easybell.de: connectme-uat-dev-misconfig (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): PROBE: single GET https://connectme-app-uat.easybell.de/.env (≥6s spacing from any prior request; capture status+content-type+body size; no auth headers). 200 t
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — primary finding: credentialed cross-origin READ + WRITE on 7 Spring-handled routes at vo
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: 18:52 run's "closed and rejected on both sub-lines" has no KB REJECTED entry — claim discarded as unverified
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~36h filing latency is the only ri
- LEARN: NO_DELTA — no live probes since 2026-09-06 04:48:35 UTC; inventory + KB unchanged; no accept/reject deltas this cycle beyond state-inconsistency correction.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-08 02:34:12 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` both return 404 (284KB custom error HTML, NOT SPA shell — different size from root 
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~36h+ filing latency is the only r
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: CORS preflights authorize credentialed cross-origin WRITE — Allow-Methods echoes any requested method (POS
- LEARN: ACCEPTED MISCONFIG @ partner.easybell.de: Laravel Blade partner portal (partnerportal_session cookie, Matomo siteId=2); app bundle leaks no /api/* surface (Sent
- LEARN: ACCEPTED MISCONFIG @ order-form.easybell.de/api: /api/plan-classes `type` is Laravel `in:`-whitelist validated (422 validation.in for business/private), partner
- LEARN: ACCEPTED OATH @ connectme-app.easybell.de: in-scope OIDC callback 200s with meta-refresh to the double-slash redirect path (+&refresh=1) while bare `//` path 40
- LEARN: ACCEPTED MISCONFIG @ survey.easybell.de: Caddy 200-empty sink on /, /admin, /index.php, /login (no content-type, CL:0) — abandoned/stub vhost; zero credential-l
- LEARN: ACCEPTED MISCONFIG @ backmon.easybell.de: nginx blanket 403 (146B, same family as voip ingress) on /, /metrics, /health, /status, /api, /index.html, /monitor — 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: /login-online-session-converged638e2/../login → 404 — nginx traversal-normalizes; earlier 200/404 split is SPA-s
- LEARN: REJECTED BUSLOGIC @ order-form.easybell.de/api: contract-summary is session-gated (404 PDF pre-session) — no anonymous contract disclosure; line closed.
- LEARN: REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // 
- LEARN: REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path

## RANKED HYPOTHESES 2026-09-08 07:34:36 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu.
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains sole unique unfiled HIGH/CRITICAL; ~37h filing latency is only r
- LEARN: NO_DELTA — no live probes since 2026-09-08 02:34:17 UTC; inventory + KB unchanged; all passive lines closed.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` both return 404 (284KB custom error HTML, NOT SPA shell — different size from root 
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6,
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~36h+ filing latency is the only r
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~36h+ filing latency is the only r
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` both return 404 (284KB custom error HTML, NOT SPA shell — different size from root 
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~36h+ filing latency is the only r
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.

## RANKED HYPOTHESES 2026-09-08 12:18:42 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains sole unique unfiled HIGH/CRITICAL; ~37h+ filing latency is only 
- LEARN: NO_DELTA — no live probes since 2026-09-08 02:34:17 UTC; inventory + KB unchanged; all passive lines closed.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` both return 404 (284KB custom error HTML, NOT SPA shell — different size from root 
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~37h filing latency is the only ri
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.

## RANKED HYPOTHESES 2026-09-08 16:46:18 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains sole unique unfiled HIGH/CRITICAL; ~37h+ filing latency is only 
- LEARN: NO_DELTA — no live probes since 2026-09-08 02:34:17 UTC; inventory + KB unchanged; all passive lines closed.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` both return 404 (284KB custom error HTML, NOT SPA shell — different size from root 
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~38h filing latency is the only ri
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.

## RANKED HYPOTHESES 2026-09-08 19:43:23 UTC
- [90] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains sole unique unfiled HIGH/CRITICAL; ~38h+ filing latency is only 
- LEARN: NO_DELTA — no live probes since 2026-09-08 02:34:17 UTC; inventory + KB unchanged; all passive lines closed.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` both return 404 (284KB custom error HTML, NOT SPA shell — different size from root 
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~38h filing latency is the only ri
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.

## RANKED HYPOTHESES 2026-09-08 22:18:05 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_bigpickle.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 22:16:53 UTC 09-08). Title: "Credentialed CORS read+write on
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu — Title: "Credentialed CORS read+write on voip-management.easybell.de/api (7 Spring routes
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 22:16:53 UTC 09-08 on /api/account (ACAO evil-origin + ACAC:
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` both return 404 (284KB custom error HTML, NOT SPA shell — different size from root 
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS does not resolve (curl error 6, NXDOMAIN). Host not externally reachable — line closed.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write (90) remains the sole unique unfiled HIGH; ~38h filing latency is the only ri
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable.

## RANKED HYPOTHESES 2026-09-09 00:21:33 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 2026-09-08 22:16:53 UTC). Title: "Credentialed CORS read+wri
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on /api/account (ACAO evil-origin + 
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable

## RANKED HYPOTHESES 2026-09-09 04:56:38 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 2026-09-08 22:16:53 UTC). Title: "Credentialed CORS read+wri
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on /api/account (ACAO evil-origin + 
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable

## RANKED HYPOTHESES 2026-09-09 09:22:44 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 2026-09-08 22:16:53 UTC). Title: "Credentialed CORS read+wri
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on /api/account (ACAO evil-origin + 
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable

## RANKED HYPOTHESES 2026-09-09 13:55:04 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 2026-09-09 04:53:30 UTC — 3rd independent capture). Title: "
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on /api/account (ACAO evil-origin + 
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable

## RANKED HYPOTHESES 2026-09-09 17:31:12 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 2026-09-09 04:53:30 UTC — 3rd independent capture). Title: "
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: NO_DELTA — no new passive probes since 04:53:30 UTC 09-09; inventory + KB unchanged; all passive lines closed; filing latency is the only rising program risk.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on /api/account (ACAO evil-origin + 
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable

## RANKED HYPOTHESES 2026-09-09 20:01:27 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-bigpickle.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW — platform confirmed live (200, 0.11s). Risk is 85 and rising with every hour of filin
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 2026-09-09 04:53:30 UTC — 3rd independent capture). Title: "
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: NO_DELTA — no new passive probes since 04:53:30 UTC 09-09; inventory + KB unchanged; all passive lines closed; filing latency is the only rising program risk.
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on /api/account (ACAO evil-origin + 
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable

## RANKED HYPOTHESES 2026-09-09 22:25:39 UTC
- [92] voip-management.easybell.de/api: voip-cors-cred-read-write (from art/lead_nemotron3.txt)
- NEXT(hypotheses-nemotron3.txt): HUMAN: File voip-cors-cred-read-write report at bugs.olivermaicher.eu NOW (finding reconfirmed live 2026-09-09 04:53:30 UTC — 3rd independent capture). Title: "
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 04:53:30 UTC 09-09 — 3rd independent capture proving persist
- LEARN: ACCEPTED MISCONFIG @ voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on /api/account (ACAO evil-origin + 
- LEARN: REJECTED MISCONFIG @ login.easybell.de: `?redirect=&next=&url=` not echoed; 302 → /login sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.
- LEARN: REJECTED MISCONFIG @ connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- LEARN: REJECTED MISCONFIG @ connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- LEARN: NO_DELTA — inventory + KB unchanged beyond connectme-uat/dev closure; all other hypotheses stable
