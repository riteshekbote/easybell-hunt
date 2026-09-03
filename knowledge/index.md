# Knowledge Base (seed)
- 2026-09-03 REJECTED brute-force/lockout @ auth.easybell.de: Program explicitly excludes brute-force/rate-limit/lockout policy testing. Do not propose auth-stuffing or credential-stuffing hypotheses.
- 2026-09-03 ACCEPTED MISCONFIG @ dev.easybell.de: Dev/staging environments commonly misconfigured; high priority for initial probe.
- 2026-09-03 ACCEPTED IDOR @ portal.easybell.de: Customer portals are prime IDOR targets; retain pending auth context.
- 2026-09-03 ACCEPTED IDOR @ voip-management.easybell.de/api: unused high-value live API backend discovered via SPA env leak; versioned /api/v2 map is prime BOLA surface.
- 2026-09-03 ACCEPTED IDOR @ my.easybell.com: portal.easybell.de replaced by actual portal my.easybell.com; top IDOR candidate pending auth.
- 2026-09-03 REJECTED brute-force/lockout @ mail.easybell.de: do not test Roundcube login/auth attempts.
