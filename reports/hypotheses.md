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
