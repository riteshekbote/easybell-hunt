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
