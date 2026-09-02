# easybell-hunt

24/7 deep multi-model bug-hunting automation for **easybell GmbH** (Oliver Maicher bug-bounty hub).

Scope: All company-owned infrastructure, DSL services, VoIP platforms, SIP systems, APIs, customer portals, applications, and domains operated by easybell GmbH
(full exclusion + rules list in `scope.yml`)

Pipeline (all workflows run every 20 minutes):

- **Deep Hunt** (`hunt.yml`): analyst hunts the discovered inventory + hypotheses, emits structured
  leads, chains primitives, self-critiques. Models: mimo.
- **Triager** (`triage.yml`): second-model 7-Question Gate validation + live passive probe; keeps
  running count in `reports/valid-bugs.md`.
- **Reposcan** (`reposcan.yml`): deep source scan of any public GitHub org (if configured).
- **Sync Issues** (`sync-issues.yml`): mirrors leads to GitHub issues.

Testing discipline: rate-limited (1 rps), no DoS/account-lockout, writes only on non-prod/test
assets, no exposure of customer/employee/financial/auth data, secrets committed only as hashes.

> IMPORTANT: the pipeline produces CANDIDATE leads. A reportable, validated finding requires
> human triage + proof against the program's gate. No finding is fabricated; scanner output alone
> is never accepted. Active testing is gated behind the in-scope hosts in `inventory/easybell.md` and
> must stay within the program's published scope.

Artifacts:

| Artifact | Purpose |
|---|---|
| `leads/` | Candidate findings (UNVALIDATED) |
| `triage/` | Validation verdicts |
| `reports/valid-bugs.md` | Validated findings + running count |
| `scope.yml` | Program scope and exclusions (edit to adjust) |

Program description: German provider of internet, VoIP, and cloud telephony solutions for business and residential customers
