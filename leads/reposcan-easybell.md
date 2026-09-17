## REPOSCAN 2026-09-03 17:13:30 UTC
[HYP] No Candidate Repositories
class: OTHER
asset: github.com/orgs/easybell
confidence: 100
reasoning: GitHub API returns 404 for org "easybell" — either the org name is different, all repos are private, or the org does not exist on GitHub.
impact: None — no code to audit
verify_steps: Verify correct GitHub org name; check if repos are private/forked under different accounts
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-03 19:57:44 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-03 22:30:15 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-04 00:34:21 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-04 05:06:07 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-04 09:46:22 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-04 14:06:57 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-04 17:41:45 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-04 19:56:45 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-04 22:15:27 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 00:11:31 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 04:41:22 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 08:43:41 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 12:05:04 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 15:21:08 UTC
[HYP] No org candidates configured
class: OTHER
asset: N/A
confidence: 100
reasoning: |
impact: N/A — cannot perform source audit without target repos
verify_steps: |
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 17:37:36 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 19:31:08 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 21:44:59 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-05 23:40:16 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 01:21:26 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 06:33:14 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 11:20:53 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 14:25:29 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 17:24:14 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 19:30:21 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 21:42:20 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-06 23:39:54 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-07 01:25:57 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-07 06:13:06 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-07 12:47:37 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-07 18:11:12 UTC
[HYP] No Public GitHub Repositories Available for Source Audit
class: OTHER
asset: github.com/orgs/easybell
confidence: 100
reasoning: |
impact: None — no source code available to audit for secrets/insecure patterns
verify_steps: |
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-07 21:36:34 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-07 23:46:04 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-08 03:55:30 UTC
[HYP] No In-Scope Source Code on GitHub
class: OTHER
asset: github.com/easybell-gmbh
confidence: 100
reasoning: All 17 public repos are forks of open-source PHP/Laravel packages, not original easybell application code. No easybell-specific secrets, credentials, or configuration found. The program scope explicitly lists github_orgs: "none-configured".
impact: None — no proprietary source available for audit
verify_steps: N/A — confirmed via GitHub API (org repos endpoint) + shallow clone + regex sweep of all 17 repos
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-08 08:48:59 UTC
[HYP] (none)
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-08 13:26:52 UTC
[HYP] No Candidate Repositories for Source Audit
class: OTHER
asset: N/A
confidence: 100
reasoning: |
impact: None — no source code in scope for this audit channel
verify_steps: N/A — source audit is a no-op without target repos
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-08 17:31:32 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-08 20:18:28 UTC
[HYP] (none) — no candidate repos; nothing to audit
class: N/A
asset: N/A
confidence: 0
reasoning: cands.txt confirms "no org candidates". reposcan workflow is disabled. No application source code is present.
impact: N/A
verify_steps: N/A
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-08 22:46:07 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-09 01:11:17 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-09 06:08:07 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-09 11:35:05 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-09 15:18:04 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-09 18:44:34 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-09 21:33:47 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-09 23:33:09 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-10 01:29:03 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-10 06:40:17 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-10 11:50:38 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-10 16:08:16 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-10 19:10:07 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-10 21:43:04 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-10 23:51:54 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-11 03:54:13 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-11 08:48:16 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-11 13:24:50 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-11 17:14:34 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-11 19:50:27 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-11 22:22:00 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 00:37:23 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 05:03:49 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 09:31:34 UTC
class: SECRET
asset: `easybell-gmbh/collision/tests/LaravelApp/.env:7`
confidence: 30
reasoning: File contains `APP_KEY=base64:IquyT8ji6DMPqygLc19MXORzrU7SkS5+tLZxyY5Fh1Y=` — a real base64-encoded 32-byte Laravel application key. However, this is in the `tests/LaravelApp/` directory of a fork of `nunomaduro/collision` (a well-known Laravel error handler package). The `.env` file is a standard test fixture inherited from the upstream repo. The `APP_DEBUG=true` and placeholder DB creds are also present but are default upstream values.
impact: LOW — test fixture only, inherited from upstream, not easybell-specific
verify_steps: Check if `https://github.com/nunomaduro/collision/blob/main/tests/LaravelApp/.env` contains the identical APP_KEY (likely yes). If identical, it's upstream-originated and not a real leak. If unique to easybell, rotate immediately.
class: MISCONFIG
asset: `easybell-gmbh/laravel-redirect/phpunit.xml:23`
confidence: 25
reasoning: `<env name="APP_KEY" value="AckfSECXIvnK5r28GVIWUAxmbBSjTsmF"/>` is set in the PHPUnit config. This is a well-known Laravel test/default key used across many packages (this is the `laravel-redirect` fork). It's only injected during test runs via phpunit.xml's `<php>` block and is not a production credential.
impact: LOW — test-only configuration, standard Laravel test key pattern
verify_steps: Confirm this same key appears in the upstream `mattkingshaw/laravel-redirect` phpunit.xml. If unique to easybell, still low risk as it's test-only.
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 13:09:04 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 16:25:26 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 18:45:28 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 21:19:19 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-12 23:08:59 UTC
[HYP] Committed .env with encoded Laravel APP_KEY
class: SECRET
asset: collision/tests/LaravelApp/.env (line 7)
confidence: 65
reasoning: .env file is git-tracked (not in .gitignore) and contains APP_KEY=base64:IquyT8ji6DMPqygLc19MXORzrU7SkS5+tLZxyY5Fh1Y=. This is a real base64-encoded 32-byte key (Laravel 5.x format). While this is a test fixture for the collision package (fork of nunomaduro/collision), the key could be copy-pasted into production apps. The .gitignore at collision/tests/LaravelApp/.gitignore explicitly does NOT exclude .env. Impact is mitigated because (a) this is a test-only Laravel skeleton, (b) the key is likely auto-generated for test purposes, and (c) no other env vars contain real credentials.
impact: low
verify_steps: 1. Check if any easybell production .env uses this same APP_KEY value. 2. Confirm the collision test suite is only run in CI (not deployed). 3. Add .env to .gitignore in collision/tests/LaravelApp/.
[HYP] Debug dump() left in test code
class: OTHER
asset: laravel-deepl/tests/Feature/TranslatorServiceTest.php:85
confidence: 40
reasoning: Contains dd(config('laravel-deepl.enable_on_the_fly_translation'), ...) — a Laravel debug-and-die call. While this is in a test file and won't execute in production, dd() in committed code is a code smell and could mask test failures. Not a direct security issue.
impact: low
verify_steps: 1. Confirm this is not called in CI test runs (dd() would halt execution and fail the test). 2. Replace with proper assertions if needed.
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-13 01:09:29 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-13 06:19:52 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-13 12:07:46 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-13 16:27:38 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-13 18:59:40 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-13 21:26:27 UTC
class: MISCONFIG
asset: easybell-gmbh/php-sip/tests/PhpSipTest.php
confidence: 65
reasoning: >
impact: low
verify_steps: >
class: OTHER
asset: easybell-gmbh/laravel-redirect/phpunit.xml
confidence: 20
reasoning: >
impact: informational
verify_steps: >
class: OTHER
asset: easybell-gmbh/collision/tests/LaravelApp/.env
confidence: 20
reasoning: >
impact: informational
verify_steps: >
TARGET_ORG not configured for easybell; skipping public-org deep scan.

## REPOSCAN 2026-09-13 23:30:00 UTC
Source audit of all 17 public repos under github.com/easybell-gmbh.
All repos confirmed as forks. Organization identified as `easybell-gmbh` (scope.yml had `easybell`).
17 repos cloned, full regex sweep completed for: AKIA*, AIza*, ghp_*, sk_live_*, sk-us*, -----BEGIN PRIVATE KEY, password=, api_key, secret, token, client_secret, S3/GCS/Azure storage endpoints.

### Findings:

[HYP] Mock SIP responses in php-sip test leak infrastructure details
class: OTHER
asset: easybell-gmbh/php-sip/tests/PhpSipTest.php:55-90
confidence: 70
reasoning: |
  The test file contains hardcoded Mockery mock responses that appear to be captured real SIP traffic.
  Mock responses reveal: (1) sip.easybell.de - SIP server domain, (2) Sipwise NGCP Proxy 7.X -
  backend proxy software and version, (3) internal IPs 192.168.144.2 and 192.168.251.44,
  (4) public IP 79.140.179.49 in Via headers, (5) SIP account number 00493050931632
  (test account on easybell), (6) Sipgate peering account 3195388t0 at sipconnect.sipgate.de,
  (7) digest auth nonce (one-time, not reusable). Passwords used are literal 'secret' placeholders.
  This is easybell's own library (easybell-libs/php-sip, authored by easybell GmbH) and the scope
  explicitly includes VoIP/SIP systems.
impact: low
  No real passwords leaked. Infrastructure fingerprinting value only. Internal IPs not externally
  reachable. Public IP 79.140.179.49 may be a real server but provides no attack surface by itself.
  SIP account numbers are test accounts with placeholder passwords.
verify_steps: |
  1. Confirm 79.140.179.49 resolves to easybell infrastructure (passive DNS lookup).
  2. Confirm sip.easybell.de is the live SIP domain (passive DNS/SRV lookup).
  3. Confirm Sipwise NGCP is the production backend (informational).
  4. No action required - these are mock test fixtures, not live credentials.

[HYP] Committed .env with Laravel APP_KEY in collision test fixture
class: OTHER
asset: easybell-gmbh/collision/tests/LaravelApp/.env:7
confidence: 15
reasoning: |
  .env contains APP_KEY=base64:IquyT8ji6DMPqygLc19MXORzrU7SkS5+tLZxyY5Fh1Y=.
  Verified identical to upstream nunomaduro/collision .env. This is a test fixture inherited from
  the upstream repository, not easybell-specific. Per scope: "Disclosure of known public files or
  directories (e.g. robots.txt)" is explicitly out of scope.
impact: none
  Upstream test fixture, not easybell's own credential. Identical in the parent repo.
verify_steps: |
  1. Compare with https://github.com/nunomaduro/collision tests/LaravelApp/.env.
  2. No action required.

[HYP] Debug dd() in laravel-deepl test
class: OTHER
asset: easybell-gmbh/laravel-deepl/tests/Feature/TranslatorServiceTest.php:85
confidence: 10
reasoning: |
  dd() call at line 85 is inside a test marked ->skip("TODO: ..."), so it never executes.
  This is a development artifact, not a backdoor or debug endpoint exposed to users.
impact: none
  Non-executing code in a skipped test. Not a security issue.
verify_steps: |
  1. Confirm test is skipped in CI (it is - has ->skip() annotation).
  2. Replace with proper assertion if test is unskipped.

[HYP] Hardcoded APP_KEY in phpunit.xml
class: OTHER
asset: easybell-gmbh/laravel-redirect/phpunit.xml:23
confidence: 10
reasoning: |
  <env name="APP_KEY" value="AckfSECXIvnK5r28GVIWUAxmbBSjTsmF"/> is a well-known default
  Laravel test key used across many open-source packages. This is test-only configuration
  injected via phpunit.xml <php> block and never used in production. The same key pattern
  appears in upstream laravel-redirect and many Laravel test suites.
impact: none
  Standard Laravel test key pattern. Test-only, not a production credential.
verify_steps: |
  1. Confirm this same key appears in upstream phpunit.xml (likely yes).
  2. No action required.

### Summary:
- 17 repos audited (all forks of open-source PHP/Laravel packages)
- 1 easybell-original repo found: php-sip (SIP user agent library)
- 0 high-severity findings (no leaked production credentials, no API keys, no private keys)
- 1 low-confidence informational finding (SIP infrastructure details in mock test responses)
- 3 negligible findings (upstream test fixtures, non-executing code, standard test config)
- No SSRF-prone URL builders, no JWT weak validation, no IDOR-prone endpoints, no debug backdoors found
- No AKIA, AIza, ghp_, sk_live_, sk-us, or private key patterns detected across all 17 repos

### Recommendation:
The public GitHub surface for easybell is minimal - 17 forks of open-source packages with
no proprietary application code exposed. The php-sip test reveals some infrastructure details
(Sipwise NGCP, SIP domain) but no exploitable credentials. The program scope covers live
VoIP/SIP infrastructure, so network-level testing of sip.easybell.de would be more productive
than source code analysis of these public repos.
## REPOSCAN 2026-09-13 23:34:27 UTC
[HYP] Mock SIP responses in php-sip test leak infrastructure details
class: OTHER
asset: easybell-gmbh/php-sip/tests/PhpSipTest.php:55-90
confidence: 70
reasoning: |
impact: low
verify_steps: |
[HYP] Committed .env with Laravel APP_KEY in collision test fixture
class: OTHER
asset: easybell-gmbh/collision/tests/LaravelApp/.env:7
confidence: 15
reasoning: |
impact: none
verify_steps: |
[HYP] Debug dd() in laravel-deepl test
class: OTHER
asset: easybell-gmbh/laravel-deepl/tests/Feature/TranslatorServiceTest.php:85
confidence: 10
reasoning: |
impact: none
verify_steps: |
[HYP] Hardcoded APP_KEY in phpunit.xml
class: OTHER
asset: easybell-gmbh/laravel-redirect/phpunit.xml:23
confidence: 10
reasoning: |
impact: none
verify_steps: |
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-14 01:39:36 UTC
[HYP] No In-Scope Source Code Available
class: OTHER
asset: github.com/easybell-gmbh (17 public repos)
confidence: 100
reasoning: |
impact: None — no source code in scope for this audit channel
verify_steps: N/A
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-14 07:08:51 UTC
[HYP] No candidate repositories for source-code audit
class: OTHER
asset: N/A
confidence: 100
reasoning: |
impact: None — no source code in scope for this audit channel
verify_steps: |
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-14 14:15:29 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-14 19:38:49 UTC
[HYP] No findings — clean scan
class: N/A
asset: easybell-gmbh/* (17 public repos)
confidence: 95
reasoning: Exhaustive grep of all 17 repos + 5 third-party refs for AKIA, AIza, ghp_, sk_live_, BEGIN PRIVATE, password=, api_key, secret, token, client_secret, S3/GCS/Azure, .env, hardcoded URLs, JWT, IDOR, SSRF patterns. All custom commits are functional patches with no embedded secrets. Config files use env() with empty defaults.
impact: None
verify_steps: Re-run `rg -rn "AKIA[A-Z0-9]{16}|AIza[A-Za-z0-9_-]{35}|ghp_[A-Za-z0-9]{36}|sk_live_[A-Za-z0-9]{24,}|-----BEGIN (RSA |EC |OPENSSH )?PRIVATE KEY" /tmp/opencode/repos/` to confirm clean scan.
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-14 22:52:14 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-15 01:18:48 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-15 06:15:10 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-15 11:54:32 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-15 16:52:52 UTC
[HYP] Hardcoded SIP Infrastructure Details in Test Code
class: MISCONFIG
asset: easybell-gmbh/php-sip/tests/PhpSipTest.php
confidence: 45
reasoning: php-sip is the only original (non-fork) repo authored by thomas.busch@easybell.de. The test file contains what appear to be real easybell SIP infrastructure details in mock SIP responses: internal IPs (192.168.144.2, 192.168.251.44), a public IP (79.140.179.49), the SIP domain (sip.easybell.de), a SIP phone number (00493050931632), and the infrastructure vendor/version (Sipwise NGCP Proxy 7.X). The password is a test placeholder ('secret'). While these are in mock/test code that never connects to real servers, the use of what appears to be real infrastructure data in tests suggests these values may reflect actual deployment details.
impact: Low - reveals internal network topology and SIP infrastructure vendor/version to attackers; could aid targeted attacks against their SIP platform
verify_steps: 1) Resolve sip.easybell.de to confirm it's active; 2) Check if 79.140.179.49 responds on SIP ports (5060/UDP); 3) Verify if 00493050931632 is a valid SIP account via passive enumeration; 4) Check if Sipwise NGCP version 7.X has known CVEs
[HYP] SIP Digest Auth Using MD5
class: OTHER
asset: easybell-gmbh/php-sip/src/PhpSip.php:475-482
confidence: 15
reasoning: The calculateResponse() method uses MD5 for SIP digest authentication. While MD5 is cryptographically broken, this is the standard algorithm mandated by SIP RFC 2617. This is an inherent protocol limitation, not an easybell-specific vulnerability.
impact: Informational - standard SIP practice, not actionable
verify_steps: N/A - protocol-level issue
[HYP] Committed .env File with APP_KEY
class: SECRET
asset: easybell-gmbh/collision/tests/LaravelApp/.env:17
confidence: 5
reasoning: The collision fork contains a committed .env file with APP_KEY=base64:IquyT8ji6DMPqygLc19MXORzrU7SkS5+tLZxyY5Fh1Y=. However, this file was added by upstream (Nuno Maduro, commit 795a1cf), not by easybell. It's in a test fixture directory with default/empty values. Not an easybell-specific issue.
impact: Negligible - upstream test fixture, not deployed
verify_steps: Confirm this key is not used in any easybell production deployment
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-15 19:51:07 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-15 22:49:25 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-16 01:11:35 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-16 06:10:07 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-16 11:49:46 UTC
[HYP] <none> — no candidates to evaluate
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-16 16:31:29 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-16 19:41:44 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-16 22:46:45 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-17 01:13:55 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-17 06:17:21 UTC
[HYP] pipe-to-bash installer in CI workflows
class: OTHER
asset: .github/workflows/hunt.yml:46, reposcan.yml:35, triage.yml:35
confidence: 30
reasoning: >
impact: low — supply-chain risk on CI tooling only; does not touch in-scope assets
verify_steps: >
[HYP] Overly broad GitHub Actions permissions
class: MISCONFIG
asset: .github/workflows/hunt.yml:9-10
confidence: 60
reasoning: >
impact: low — CI pipeline hardening concern, not an in-scope finding
verify_steps: >
[HYP] REDACTED: No hardcoded secrets detected
class: N/A
asset: all files
confidence: 100
reasoning: >
impact: none
verify_steps: N/A — clean scan
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-17 11:54:08 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
## REPOSCAN 2026-09-17 16:36:36 UTC
TARGET_ORG not configured for easybell; skipping public-org deep scan.
