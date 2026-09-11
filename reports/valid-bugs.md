# Validated findings (running count 0)

- 3 lead(s) marked VALID at 2026-09-05 05:54:14 UTC
  - | Q5 | Novel/unreported? | Likely novel for this program (valid-bugs.md is empty, no prior report) |
  - **Verdict: VALID**
  - | 1 | voip-cors-cred-exfil-v3 | **VALID** | Report to bugs.olivermaicher.eu |

- 3 lead(s) marked VALID at 2026-09-06 17:09:59 UTC
  - ### Verdict: **VALID**
  - | voip-cors-cred-exfil-v3 | **VALID** | Credentialed CORS + ACAC:true on 7 authenticated API routes — HIGH impact, provable via OPTIONS |
  - | my-portal-api-proxy-wildcard | **HOLD** | Standalone wildcard CORS without ACAC:true is informational; only valid as chain amplifier |

- 2 lead(s) marked VALID at 2026-09-06 19:19:02 UTC
  - | voip-cors-cred-exfil-v3 | **VALID** | Credentialed CORS + ACAC:true on 7 authenticated API routes — HIGH impact, provable via OPTIONS |
  - | my-portal-api-proxy-wildcard | **HOLD** | Standalone wildcard CORS without ACAC:true is informational; only valid as chain amplifier |

- 2 lead(s) marked VALID at 2026-09-11 19:54:18 UTC
  - **Verdict: VALID**
  - | 1 | voip-management CORS (7 routes, read+write) | **VALID** | 8.1 | File at bugs.olivermaicher.eu |
