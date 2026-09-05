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
