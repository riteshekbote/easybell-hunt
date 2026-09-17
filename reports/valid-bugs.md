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

- 4 lead(s) marked VALID at 2026-09-13 06:49:16 UTC
  - | Q5 | Novel/unreported? | **Yes** — valid-bugs.md shows no prior report filed; finding persists across 10+ days |
  - **Verdict: VALID**
  - | Q7 | Would reasonable triager accept? | **No as standalone** — wildcard CORS without ACAC:true on Bearer-only endpoints is informational; only valid as chain amplifier with Finding 1 |
  - | 1 | voip-cors-cred-read-write | **VALID** | 8.1 | File at bugs.olivermaicher.eu |

- 2 lead(s) marked VALID at 2026-09-13 19:19:58 UTC
  - **Verdict: VALID**
  - | 1 | CORS credentialed reflection (7 routes) | **VALID** | 6.1 |

- 3 lead(s) marked VALID at 2026-09-14 07:52:29 UTC
  - **Verdict: VALID**
  - | Q3 Impact | No — 405 is a valid response indicating the endpoint exists but doesn't accept GET |
  - | voip-cors-cred-exfil-v2 | **VALID** | 6.5 |

- 2 lead(s) marked VALID at 2026-09-17 23:06:59 UTC
  - | 1 | `voip-cors-cred-read-write` (7 Spring routes, ACAO:attacker + ACAC:true) | **Already VALID** | 8.1 | 14+ independent captures through 2026-09-17; report **not yet filed** at bugs.olivermaicher.e
  - | 2 | `my-portal-api-proxy-wildcard` (ACAO:* on /api/crm,ebit,strapi) | **HOLD** | — | Standalone informational; only valid as chain amplifier with #1 |
