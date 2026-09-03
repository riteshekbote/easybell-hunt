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
