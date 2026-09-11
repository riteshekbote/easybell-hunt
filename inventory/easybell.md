# easybell GmbH inventory (discovery seed 2026-09-02)
# NOTE: hosts below are discovery candidates from passive DNS/CT; confirm in-scope vs program scope before active testing.
auth.easybell.de
dev.easybell.de
easybell.de
login.easybell.de
mail.easybell.de
portal.easybell.de
www.easybell.de

## PASSIVE RECON 2026-09-02 (read-only, non-intrusive)

> Recon observations only. These are NOT confirmed vulnerabilities; ownership/in-scope of each host must be confirmed against the program scope before any active testing. Hosts resolve + serve HTTP — investigation requires scoped authorization.

**Probed:** 7 hosts | **Live HTTP:** 0

| Host | Status | Server/Tech |
|---|---|---|

## 2026-09-02 21:54:05 UTC

## 2026-09-02 23:47:09 UTC

## 2026-09-03 02:32:15 UTC

## 2026-09-03 07:23:53 UTC

## 2026-09-03 12:16:38 UTC

## 2026-09-03 16:49:23 UTC

## 2026-09-03 19:45:37 UTC
- NEW my.easybell.com: real customer portal ("Easybell Kundenportal", Laravel 10 + Vue 3 Inertia SPA), 200 at /login, sets Laravel `ekp_session`+encrypted `XSRF-TOKEN`, `X-Inertia` header. Supersedes `porta
- NEW voip-management.easybell.de: nginx front with live JSON REST API at /api/ ; custom Spring-style error `{"code":404,"message":"/api/v2/<path>"}`. Referenced as `VITE_VOIP_MANAGEMENT_URL` in portal SPA.
- CHANGED inventory 0/7 "not live" is stale: www(200 TYPO3), easybell(301), login(302->my), my.easybell.com(200), mail->rcm(200 Roundcube), auth(404 nginx), shared-libs(404 asset CDN), matomo, voip-management(A
- CHANGED dev.easybell.de / portal.easybell.de: no DNS/route — effectively dead; top target shifts to my.easybell.com + voip-management.

## 2026-09-03 21:58:47 UTC
- NEW my.easybell.com: real customer portal ("Easybell Kundenportal", Laravel 10 + Vue 3 Inertia SPA), 200 at /login, sets Laravel `ekp_session`+encrypted `XSRF-TOKEN`, `X-Inertia` header. Supersedes `porta
- NEW voip-management.easybell.de: nginx front with live JSON REST API at /api/ ; custom Spring-style error `{"code":404,"message":"/api/v2/<path>"}`. Referenced as `VITE_VOIP_MANAGEMENT_URL` in portal SPA.
- CHANGED inventory 0/7 "not live" is stale: www(200 TYPO3), easybell(301), login(302->my), my.easybell.com(200), mail->rcm(200 Roundcube), auth(404 nginx), shared-libs(404 asset CDN), matomo, voip-management(A
- CHANGED dev.easybell.de / portal.easybell.de: no DNS/route — effectively dead; top target shifts to my.easybell.com + voip-management.
- NEW voip-management.easybell.de routing map resolved: `/api/<res>` → proxied to Spring backend (returns Spring JSON 404 `{"code":404,"message":"/api/v2/<res>"}` revealing internal v2 rewrite); `/api/` and
- CHANGED voip-management WAF: aggressive rate-limit confirmed. Bursts of >~8-10 rapid probes → empty/timed-out responses. Must space probes >=5-6s, back off 60s after block.
- CHANGED voip-api-v2-bola: no live (non-404) Spring resource discovered yet across customer/account/number/user/subscriber probes — all nginx-HTML or rate-limited. Backend is reachable and versioned but actual

## 2026-09-03 23:45:55 UTC
- NEW my.easybell.com: Confirmed live customer portal (Laravel 10 + Vue 3 Inertia SPA), 200 at /login, sets `ekp_session` + encrypted `XSRF-TOKEN`, `X-Inertia` header; `customerId` leaked in Matomo tracker 
- NEW voip-management.easybell.de: Live nginx→Spring JSON API at `/api/<res>` (rewrites to internal `/api/v2/<res>`, leaked via 404 body `{"code":404,"message":"/api/v2/<res>"}`). `/api/` and `/api/v2/` dir
- CHANGED dev.easybell.de / portal.easybell.de: No DNS/route — effectively dead (probe timeouts confirmed). Top targets shift to my.easybell.com + voip-management.
- CHANGED voip-management WAF: Aggressive rate-limit confirmed. Bursts >~8-10 probes → empty/timeouts. Mandates >=6s spacing, 60-120s backoff after block.
- CHANGED voip-api-v2-bola: No live (non-404) Spring resource discovered yet across customer/account/number/user/subscriber/trunk/line/contract/invoice/sip/device/tariff probes — all nginx-HTML 404 or rate-limi

## 2026-09-04 02:34:48 UTC
- NEW voip-management.easybell.de/api/customer → HTTP 404 (nginx HTML) at 2026-09-03 23:45:57 UTC; Spring v2 rewrite not triggered — resource name still unknown
- NEW No new live hosts; dev.easybell.de/portal.easybell.de remain non-routable; auth.easybell.de returns 404 on all well-known paths
- CHANGED voip-api-v2-bola enumeration continues: customer, account, user, number, subscriber, trunk, line, contract, invoice, sip, device, tariff all unconfirmed (404 or rate-limited); backend reachable via JS
- CHANGED my.easybell.com passive JS bundle mapping not yet performed; Inertia route table and API proxy endpoints uncataloged

## 2026-09-04 07:26:02 UTC
- NEW Current time 2026-09-04 07:25:00 UTC — >7h since last probe (2026-09-03 23:45:57); WAF backoff window long cleared
- CHANGED voip-api-v2-bola: 13 resource names probed (customer, account, user, number, extension, subscriber, trunk, line, contract, invoice, sip, device, tariff) — all nginx HTML 404 or rate-limited; Spring v2
- CHANGED my-portal-inertia-bola: Passive JS bundle mapping not yet performed; Inertia route table and API proxy endpoints uncataloged
- NEW No changes to dev.easybell.de/portal.easybell.de (non-routable), auth.easybell.de (404), mail.easybell.de (Roundcube)

## 2026-09-04 12:29:49 UTC
- NEW Current time 2026-09-04 12:15:55 UTC — >12h since last probe (2026-09-03 23:45:57); WAF backoff window long cleared
- NEW 9 additional resource names probed on voip-management.easybell.de/api (extension, trunk, line, contract, invoice, sip, device, tariff, subscribers via OPTIONS) — all nginx HTML 404 except subscribers 
- CHANGED voip-api-v2-bola: 22 resource names probed total — all nginx HTML 404; Spring v2 rewrite map confirmed but actual v2 resource names remain opaque
- CHANGED my-portal-inertia-bola: Passive JS bundle mapping completed; Inertia route table (100+ pages) and API proxy endpoints cataloged from public bundles
- NEW CORS misconfiguration CONFIRMED on voip-management.easybell.de/api/subscribers (plural Sipwise route): reflects arbitrary Origin with `Access-Control-Allow-Credentials: true`
- NEW my.easybell.com portal: `VITE_VOIP_MANAGEMENT_URL` = `https://voip-management.easybell.de/api/`; axios instance attaches Bearer token from `voipSession`; proxies plural Sipwise routes (accounts, subsc
- NEW No changes to dev.easybell.de/portal.easybell.de (non-routable), auth.easybell.de (404), mail.easybell.de (Roundcube)

## 2026-09-04 16:34:56 UTC
- CHANGED voip-management.easybell.de/api CORS: knowledge base claimed singular routes lock to my.easybell.com — **FALSE**. `account`, `subscriber`, `number` (singular) ALL return `ACAO: <evil.com> + ACAC:true`
- NEW my.easybell.com internal API proxy endpoints `/api/crm`, `/api/ebit`, `/api/strapi` — ALL return `Access-Control-Allow-Origin: *` (no ACAC:true) on both redirect and OPTIONS preflight. Accepts POST wi
- NEW Internal k8s hostname leaked in client JS bundle: `voip-management.k8s.easybell.de/api` — fallback value in `core.js` when `VITE_VOIP_MANAGEMENT_URL` env is unset.
- NEW `my.easybell.com/api/strapi` — Strapi CMS proxy endpoint confirmed, same wildcard CORS pattern.
- CHANGED voip-management.easybell.de/api CORS surface: Spring-handled routes confirmed (404 JSON): account, accounts, subscriber, subscribers, number, numbers, session. Nginx-only routes (HTML 404, no CORS): c
- NEW CORS credentialed misconfiguration CONFIRMED on voip-management.easybell.de/api/subscribers (plural Sipwise route): reflects arbitrary Origin with `Access-Control-Allow-Credentials: true`
- NEW my.easybell.com portal JS analysis complete: `VITE_VOIP_MANAGEMENT_URL` = `https://voip-management.easybell.de/api/`; axios attaches Bearer from `voipSession`; proxies 8 plural Sipwise routes (account
- NEW Passive JS bundle mapping completed for my.easybell.com: Inertia route table (100+ pages) and API proxy endpoints cataloged
- CHANGED voip-api-v2-bola: 22 resource names probed total — all nginx HTML 404; Spring v2 rewrite map confirmed (`/api/<res>` → `/api/v2/<res>` leaked via JSON 404) but actual v2 resource names remain opaque
- CHANGED WAF backoff window long cleared: >12h since last probe (2026-09-03 23:45:57 UTC); safe to resume spaced probing
- CHANGED Risk elevated to 70: confirmed credentialed CORS exfiltration vector on live authenticated endpoints

## 2026-09-04 19:13:07 UTC
- NEW CORS credentialed misconfiguration CONFIRMED on ALL Spring-handled routes at voip-management.easybell.de/api (account, accounts, subscriber, subscribers, number, numbers, session) — reflect arbitrary 
- NEW my.easybell.com internal API proxy endpoints `/api/crm`, `/api/ebit`, `/api/strapi` return `Access-Control-Allow-Origin: *` (no ACAC:true) on redirect + OPTIONS preflight; accept POST with `Authorizat
- NEW Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (`core.js`)
- NEW `my.easybell.com/api/strapi` — Strapi CMS proxy endpoint confirmed, same wildcard CORS pattern
- CHANGED voip-management.easybell.de/api CORS surface broader than KB: Spring-handled routes (7 endpoints) all credentialed-reflect; nginx-only routes (customer, user, extension, trunk, line, contract, invoice
- CHANGED voip-api-v2-bola: 22 resource names probed total — all nginx HTML 404; Spring v2 rewrite map confirmed (`/api/<res>` → `/api/v2/<res>` via JSON 404) but actual v2 resource names remain opaque
- CHANGED WAF backoff window long cleared: >12h since last probe (2026-09-03 23:45:57 UTC); safe to resume spaced probing
- CHANGED Risk elevated to 70 (nemotron3) / 68 (bigpickle): confirmed credentialed CORS exfiltration vector on 7 live authenticated endpoints

## 2026-09-04 21:34:53 UTC
- NEW CORS credentialed misconfiguration CONFIRMED on ALL 7 Spring-handled routes at voip-management.easybell.de/api (account, accounts, subscriber, subscribers, number, numbers, session) — reflect arbitrar
- NEW my.easybell.com internal API proxy endpoints `/api/crm`, `/api/ebit`, `/api/strapi` return `Access-Control-Allow-Origin: *` (no ACAC:true) on redirect + OPTIONS preflight; accept POST with `Authorizat
- NEW Internal k8s hostname `voip-management.k8s.easybell.de/api` leaked as fallback URL in client-side JS bundle (`core.js`)
- NEW `my.easybell.com/api/strapi` — Strapi CMS proxy endpoint confirmed, same wildcard CORS pattern
- CHANGED voip-management.easybell.de/api CORS surface broader than KB: Spring-handled routes (7 endpoints) all credentialed-reflect; nginx-only routes (customer, user, extension, trunk, line, contract, invoice
- CHANGED voip-api-v2-bola: 22 resource names probed total — all nginx HTML 404; Spring v2 rewrite map confirmed (`/api/<res>` → `/api/v2/<res>` via JSON 404) but actual v2 resource names remain opaque
- CHANGED WAF backoff window long cleared: >12h since last probe (2026-09-03 23:45:57 UTC); safe to resume spaced probing
- CHANGED Risk elevated to 70: confirmed credentialed CORS exfiltration vector on 7 live authenticated endpoints

## 2026-09-04 23:18:21 UTC
- NEW Passive DNS (2026-09-04 23:15 UTC): `voip-management.k8s.easybell.de` and `k8s.easybell.de` return NO public A record (NXDOMAIN/empty). Internal k8s hostname leak from core.js is NOT externally resolv
- NEW `my.easybell.com` and `voip-management.easybell.de` share public IP 62.27.117.123 (one nginx ingress); `easybell.de` → 62.27.117.125. The "cross-origin" split between portal and VoIP API is host-heade
- CHANGED Passive surface saturated: all three top leads (CORS exfil 92 / proxy-wildcard 78 / portal IDOR 55) are AUTH_HELPED and unchanged since 21:34. Only unprobed passive surface left = Spring actuator/rout
- NEW Live verification confirms CORS credentialed misconfiguration on ALL 7 Spring-handled routes at `voip-management.easybell.de/api` (account, accounts, subscriber, subscribers, number, numbers, session)
- NEW `my.easybell.com/api/{crm,ebit,strapi}` proxy endpoints confirmed: OPTIONS preflight returns `Access-Control-Allow-Origin: *` (wildcard, no ACAC:true) with `Allow: GET,HEAD` and `Vary: Access-Control-
- NEW `voip-management.easybell.de/api/v2/{accounts,subscribers,numbers,account,subscriber,number,session}` all return nginx HTML 404 (no CORS headers, `content-type: text/html`) — Spring v2 rewrite map lea
- NEW Internal k8s hostname `voip-management.k8s.easybell.de/api` (leaked in `core.js`) not resolvable externally — internal-only
- CHANGED WAF backoff window cleared: >23h since last probe (2026-09-03 23:45:57 UTC); safe for spaced probing (≥6s, 60-120s backoff)
- CHANGED Risk stable at 70: confirmed credentialed CORS exfiltration vector on 7 authenticated endpoints; limited by no victim creds for AUTH_HELPED verification, program auth/lockout exclusion

## 2026-09-05 01:07:06 UTC
- NEW Passive DNS confirms `voip-management.k8s.easybell.de` and `k8s.easybell.de` have NO public A record (NXDOMAIN) — internal hostname leak from `core.js` is not externally resolvable; downgraded from ac
- NEW `my.easybell.com` and `voip-management.easybell.de` share public ingress IP 62.27.117.123 (same nginx); "cross-origin" split is host-header-only at same ingress — undermines same-origin policy assumpt
- CHANGED WAF backoff window fully cleared: >23h since last live probe (2026-09-03 23:45:57 UTC); safe for spaced probing (≥6s, 60-120s backoff)
- CHANGED Passive surface saturated: all three top leads (CORS exfil 92 / proxy-wildcard 78 / portal IDOR 55) are AUTH_HELPED and unchanged since 2026-09-04 21:34; only unprobed passive surface left = Spring ac
- CHANGED `my.easybell.com/api/{crm,ebit,strapi}` proxy endpoints confirmed: OPTIONS preflight returns `Access-Control-Allow-Origin: *` (wildcard, no ACAC:true) with `Allow: GET,HEAD` and `Vary: Access-Control-
- CHANGED `voip-management.easybell.de/api/v2/{accounts,subscribers,numbers,account,subscriber,number,session}` all return nginx HTML 404 (no CORS headers, `content-type: text/html`) — Spring v2 rewrite map lea

## 2026-09-05 05:55:47 UTC
- NEW Last live probe was 2026-09-05 01:07:09 UTC (~4.7h ago); WAF backoff window fully cleared (>23h since last burst probe at 2026-09-03 23:45:57 UTC) — safe for spaced probing (≥6s, 60-120s backoff)
- CHANGED Passive surface remains saturated: three top leads (voip-cors-cred-exfil-v3 92, my-portal-api-proxy-wildcard-exfil 82, portal IDOR 55) all AUTH_HELPED, unchanged since 2026-09-04 21:34; only unprobed 
- CHANGED Confirmed: `my.easybell.com` + `voip-management.easybell.de` share ingress IP 62.27.117.123 (same nginx); "cross-origin" split is host-header-only — undermines same-origin policy assumption for CORS e
- CHANGED `voip-management.k8s.easybell.de` / `k8s.easybell.de` confirmed NXDOMAIN via passive DNS — internal hostname leak from `core.js` is info-disclosure only, not actionable
- CHANGED `voip-management.easybell.de/api/v2/{accounts,subscribers,numbers,account,subscriber,number,session}` all return nginx HTML 404 (no CORS, `content-type: text/html`) — Spring v2 rewrite map leaked but 

## 2026-09-05 09:51:21 UTC
- CHANGED Time since last live probe: ~8.7h (2026-09-05 01:07:09 UTC → 2026-09-05 09:49:10 UTC); WAF backoff fully cleared, safe for spaced probing (≥6s, 60-120s backoff)
- CHANGED Passive surface unchanged: three top leads (voip-cors-cred-exfil-v3 92, my-portal-api-proxy-wildcard-exfil 82, portal IDOR 55) all AUTH_HELPED, no new passive findings since 2026-09-04 21:34
- CHANGED Only unprobed passive vector remains: Spring actuator/route-map disclosure on voip-management ingress (`/api/actuator`, `/actuator/*`)

## 2026-09-05 13:13:48 UTC
- CHANGED Passive surface now fully exhausted: CORS exfil (92), proxy wildcard (78), portal IDOR (55) all unchanged; actuator line dead. All forward motion requires HUMAN session/creds or report filing.
- CHANGED Time since last live probe: ~8.7h (2026-09-05 01:07:09 UTC → now); WAF backoff fully cleared, safe for spaced probing (≥6s, 60-120s backoff)
- CHANGED Passive surface unchanged: three top leads (voip-cors-cred-exfil-v3 92, my-portal-api-proxy-wildcard-exfil 82, portal IDOR 55) all AUTH_HELPED, no new passive findings since 2026-09-04 21:34
- CHANGED Only unprobed passive vector remains: Spring actuator/route-map disclosure on voip-management ingress (`/api/actuator`, `/actuator/*`)

## 2026-09-05 16:10:13 UTC
- CHANGED Probe log 13:13:54 UTC re-confirms actuator line dead: /api/actuator, /api/actuator`, /api/account → nginx HTML 404. WAF cooldown cleared (~1h since last burst). No Spring JSON on any path.
- NEW Laravel misconfig surface on `my.easybell.com` (.env, /.git/config, /telescope, /horizon, /_ignition, /storage/logs) has ZERO coverage in all 4 days of probes/leads/triage (repo-wide grep = no matches
- NEW Spring OpenAPI/swagger (springfox `/v2/api-docs`, springdoc `/v3/api-docs`, `/swagger-ui.html`, `/openapi.json`) on the voip-management `/api/` proxy is likewise UNTRIED — distinct from the dead actua
- CHANGED RANKED HYPOTHESES header mis-score: `[92] voip-spring-actuator-route-map` is stale — actuator was 50 and is disproven; the 92 belongs to voip-cors-cred-exfil-v3. Reporting artifact, not a live line.
- CHANGED Spring actuator hypothesis DISPROVEN — all `/api/actuator*`, `/actuator*` return nginx HTML 404 (146B); no Spring JSON exposure
- CHANGED Passive surface fully exhausted: CORS exfil (92), proxy wildcard (82), portal IDOR (55) all AUTH_HELPED, unchanged since 2026-09-04 21:34
- CHANGED No unprobed passive vectors remain; all forward motion requires HUMAN session/creds or report filing

## 2026-09-05 18:33:14 UTC
- NEW CT sweep (18:23–18:24 UTC) surfaces 18 live A-record subdomains absent from all 4 days of inventory; ~6 never-probed web apps (order-form, connectme-app prod/UAT/dev, partner.easybell.de, survey) + ba
- CHANGED Prior "passive surface exhausted" verdict RETRACTED — exhaustion was relative to an incomplete 7-host seed inventory; fresh zero-credential breadth reopens.
- NEW order-form.easybell.de (on main ingress 62.27.117.123, shared with portal/voip-management): Vite/Vue SPA; bundle leaks `/api/` base + live POST endpoint `/api/apc/check` (GET→405, 18:30:44 UTC) + `par
- NEW connectme-app.easybell.de: nginx SPA; `/authenticate` → 200 + OIDC redirect to external Keycloak `dstny.d4sp.com`, `client_id=coven`, `response_type=code`, `redirect_uri=...//login-online-session-conv
- NEW partner.easybell.de: 200 → `/login` partner portal on main ingress (18:31:22 UTC).
- CHANGED my.easybell.com dotfile line DISPROVEN: `/.env`, `/.git/config`, `/telescope`, `/_ignition/health-check`, `/storage/logs/laravel.log`, `/horizon` all 200 = identical Inertia SPA catch-all shell, no fi
- CHANGED voip openapi line closed: `/api/v2/api-docs`, `/api/swagger-ui.html`, `/api/openapi.json`, `/api/swagger-ui/index.html` all nginx HTML 404 (18:22 UTC).
- NEW Laravel misconfig surface on `my.easybell.com` (.env, /.git/config, /telescope, /horizon, /_ignition, /storage/logs) has ZERO coverage in all prior cycles — new zero-credential passive line
- NEW Spring OpenAPI/swagger (springfox `/v2/api-docs`, springdoc `/v3/api-docs`, `/swagger-ui.html`, `/openapi.json`) on `voip-management.easybell.de/api/` proxy UNTRIED — distinct from dead actuator
- CHANGED Spring actuator hypothesis DISPROVEN — all `/api/actuator*`, `/actuator*` return nginx HTML 404 (146B); no Spring JSON exposure
- CHANGED Passive surface fully exhausted for CORS exfil (92), proxy wildcard (82), portal IDOR (55) — all AUTH_HELPED, unchanged since 2026-09-04 21:34
- CHANGED `voip-management.k8s.easybell.de` / `k8s.easybell.de` confirmed NXDOMAIN — internal hostname leak is info-disclosure only
- CHANGED `my.easybell.com` + `voip-management.easybell.de` share ingress IP 62.27.117.123 (same nginx); "cross-origin" split is host-header-only

## 2026-09-05 20:47:39 UTC
- NEW CT sweep (18:23–18:24 UTC, crt.sh DoH-verified) surfaces 18 live A-record subdomains absent from all 4 days of inventory; ~6 never-probed web apps (order-form, connectme-app prod/UAT/dev, partner, sur
- NEW order-form.easybell.de (on main ingress 62.27.117.123 shared with portal/voip): Vite/Vue SPA bundle (index-BiM9ZwNg.js) leaks `/api/` base, live POST-only `/api/apc/check` (GET→405), partner.easybell.
- NEW connectme-app.easybell.de: nginx SPA; `/authenticate` → 200 + OIDC redirect to external Keycloak `dstny.d4sp.com`, `client_id=coven`, `response_type=code`, in-scope `redirect_uri` with double-slash `/
- NEW partner.easybell.de: 200 → `/login` partner portal on main ingress
- CHANGED my.easybell.com dotfile/debug surface DISPROVEN (18:21 UTC) — `/.env`, `/.git/config`, `/telescope`, `/horizon`, `/_ignition/health-check`, `/storage/logs/laravel.log` all return 200 text/html = ident
- CHANGED voip-management OpenAPI/swagger line CLOSED (18:22 UTC) — `/api/v2/api-docs`, `/api/v3/api-docs`, `/api/swagger-ui.html`, `/api/openapi.json`, `/api/swagger-ui/index.html`, `/api/swagger-ui.html` all 
- CHANGED Prior "passive surface exhausted" verdict RETRACTED — was relative to incomplete 7-host seed; fresh zero-credential breadth reopens via CT sweep
- CHANGED `voip-management.k8s.easybell.de` / `k8s.easybell.de` confirmed NXDOMAIN — internal hostname leak is info-disclosure only
- CHANGED `my.easybell.com` + `voip-management.easybell.de` share ingress IP 62.27.117.123 (same nginx); "cross-origin" split is host-header-only

## 2026-09-05 22:40:34 UTC
- NEW order-form.easybell.de: Vite SPA on shared ingress 62.27.117.123; bundle index-BiM9ZwNg.js leaks `/api/` base, live POST-only `/api/apc/check` (GET→405), references partner.easybell.de + login.easybel
- NEW connectme-app.easybell.de (prod/uat/dev): nginx SPA; `/authenticate` → 200 + OIDC redirect to external Keycloak `dstny.d4sp.com` (client_id=coven, response_type=code) with in-scope `redirect_uri=https
- NEW partner.easybell.de: 200 → `/login` partner portal on main ingress (shared nginx), unprobed surface
- NEW survey.easybell.de, backmon.easybell.de: live A-records from CT sweep, zero prior coverage
- CHANGED my.easybell.com dotfile/debug surface DISPROVEN (18:21 UTC) — `/.env`, `/.git/config`, `/telescope`, `/horizon`, `/_ignition/health-check`, `/storage/logs/laravel.log` all return 200 text/html = ident
- CHANGED voip-management.easybell.de/api OpenAPI/swagger line CLOSED (18:22 UTC) — `/api/v2/api-docs`, `/api/v3/api-docs`, `/api/swagger-ui.html`, `/api/openapi.json`, `/api/swagger-ui/index.html` all nginx HT
- CHANGED Prior "passive surface exhausted" verdict RETRACTED — was relative to incomplete 7-host seed; fresh zero-credential breadth reopens via CT sweep (18 live subdomains)
- CHANGED `voip-management.k8s.easybell.de` / `k8s.easybell.de` confirmed NXDOMAIN via passive DNS — internal hostname leak from `core.js` is info-disclosure only
- CHANGED `my.easybell.com` + `voip-management.easybell.de` share ingress IP 62.27.117.123 (same nginx); "cross-origin" split is host-header-only

## 2026-09-06 00:15:09 UTC
- NEW order-form.easybell.de/api: Vite SPA bundle (index-BiM9ZwNg.js) leaks `/api/` base path and live POST-only endpoint `/api/apc/check` (GET→405 at 18:30:44 UTC); references partner.easybell.de + login.e
- NEW connectme-app.easybell.de (prod/uat/dev): nginx SPA; `/authenticate` → 200 + OIDC redirect to external Keycloak `dstny.d4sp.com` (client_id=coven, response_type=code) with in-scope `redirect_uri=https
- NEW partner.easybell.de: 200 → `/login` partner portal on main ingress (shared nginx 62.27.117.123), unprobed surface; Laravel Blade, partnerportal_session cookie, Matomo siteId=2
- NEW survey.easybell.de, backmon.easybell.de: live A-records from CT sweep (crt.sh DoH-verified), zero prior coverage
- CHANGED my.easybell.com dotfile/debug surface DISPROVEN (18:21 UTC) — `/.env`, `/.git/config`, `/telescope`, `/horizon`, `/_ignition/health-check`, `/storage/logs/laravel.log` all return 200 text/html = ident
- CHANGED voip-management.easybell.de/api OpenAPI/swagger line CLOSED (18:22 UTC) — `/api/v2/api-docs`, `/api/v3/api-docs`, `/api/swagger-ui.html`, `/api/openapi.json`, `/api/swagger-ui/index.html` all nginx HT
- CHANGED Prior "passive surface exhausted" verdict RETRACTED — was relative to incomplete 7-host seed; fresh zero-credential breadth reopens via CT sweep (18 live subdomains)
- CHANGED `voip-management.k8s.easybell.de` / `k8s.easybell.de` confirmed NXDOMAIN via passive DNS — internal hostname leak from `core.js` is info-disclosure only
- CHANGED `my.easybell.com` + `voip-management.easybell.de` share ingress IP 62.27.117.123 (same nginx); "cross-origin" split is host-header-only

## 2026-09-06 04:48:17 UTC
- NEW order-form.easybell.de/api: full anonymous API map recovered from 21 Vite chunks (index-BiM9ZwNg.js + 20 lazy): GET {auth,providers,plan-classes,plans/<code>,companies,translations/*} + mutations POST
- CHANGED order-form anonymous GET surface now fully enumerated + spot-verified; content caps at public catalog data (MEDIUM). The only HIGH-candidate remainder is the anonymous POST business-logic layer (money
- CHANGED nemotron3 order-form chunk NEXT executed (read-only); the last paved zero-credential passive line is closed.
- NEW No new live probes since 2026-09-05 18:33:33 UTC (order-form.easybell.de); WAF backoff fully cleared (>10h since last burst)
- CHANGED order-form.easybell.de/api hypothesis confidence 78 → unchanged; connectme-oidc-redirect-uri-doubleslash 82 → unchanged; partner-portal-unauth-api-surface 60 → parked awaiting probe
- CHANGED voip-management.easybell.de/api CORS credentialed reflection (92) + my.easybell.com proxy wildcard (78) + portal IDOR (55) all AUTH_HELPED, static since 2026-09-04 21:34
- CHANGED CT-sweep 18 live subdomains (order-form, connectme-app±uat/dev, partner, survey, backmon) now in inventory; prior "exhausted" verdict retracted
- CHANGED my.easybell.com dotfile/debug surface disproven (SPA catch-all); voip OpenAPI/swagger closed (all nginx HTML 404); k8s hostnames NXDOMAIN confirmed

## 2026-09-06 09:16:14 UTC
- CHANGED No new live probes since 2026-09-06 04:48:35 UTC (order-form.easybell.de chunk audit + connectme/partner spot checks); WAF backoff fully cleared (>4h since last burst, >10h since voip burst)
- CHANGED order-form.easybell.de/api anonymous GET surface fully enumerated from 21 Vite chunks; tariff catalog verified (GET /api/plans/SIPD 200 7987B), contract-summary session-gated (404); POST/PUT/DELETE mo
- CHANGED partner.easybell.de fingerprint confirmed: Laravel Blade login panel (partnerportal_session cookie, Matomo siteId=2), bundle leaks no /api/* surface (Sentry DSN only) — passive API-leak line closed cl
- CHANGED survey.easybell.de: Caddy 200-empty sink on /,/admin,/index.php,/login (no CT, CL:0) — abandoned stub vhost; closed
- CHANGED backmon.easybell.de: nginx blanket 403 (146B, voip ingress family) on /,/metrics,/health,/status,/api,/index.html,/monitor — IP-allowlist deny; closed
- CHANGED connectme-app.easybell.de: OIDC callback at //login-online-session-converged638e2 returns SPA shell 200 on state+code and +refresh=1; bare // path and traversal ../../ 404 — nginx normalizes; inconsis
- CHANGED voip-management.easybell.de/api: CORS credentialed read+write CONFIRMED on all 7 Spring routes (account,accounts,subscriber,subscribers,number,numbers,session) — OPTIONS preflights echo Allow-Methods 

## 2026-09-06 12:57:35 UTC
- CHANGED No new live probes since 2026-09-06 04:48:35 UTC (order-form chunk audit + connectme/partner spot checks); WAF backoff fully cleared (>4h since last burst, >10h since voip burst)
- CHANGED order-form.easybell.de/api anonymous GET surface fully enumerated from 21 Vite chunks; tariff catalog verified (GET /api/plans/SIPD 200 7987B), contract-summary session-gated (404); POST/PUT/DELETE mo
- CHANGED partner.easybell.de fingerprint confirmed: Laravel Blade login panel (partnerportal_session cookie, Matomo siteId=2), bundle leaks no /api/* surface (Sentry DSN only) — passive API-leak line closed cl
- CHANGED survey.easybell.de: Caddy 200-empty sink on /,/admin,/index.php,/login (no CT, CL:0) — abandoned stub vhost; closed
- CHANGED backmon.easybell.de: nginx blanket 403 (146B, voip ingress family) on /,/metrics,/health,/status,/api,/index.html,/monitor — IP-allowlist deny; closed
- CHANGED connectme-app.easybell.de: OIDC callback at //login-online-session-converged638e2 returns SPA shell 200 on state+code and +refresh=1; bare // path and traversal ../../ 404 — nginx normalizes; inconsis
- CHANGED voip-management.easybell.de/api: CORS credentialed read+write CONFIRMED on all 7 Spring routes (account,accounts,subscriber,subscribers,number,numbers,session) — OPTIONS preflights echo Allow-Methods 

## 2026-09-06 16:06:00 UTC
- CHANGED REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // path 404s" recordings were backtick-poll
- CHANGED REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path-normalization bypass surface
- CHANGED No new live probes since 2026-09-06 04:48:35 UTC (order-form chunk audit + connectme/partner spot checks); WAF backoff fully cleared (>4h since last burst, >10h since voip burst)
- CHANGED order-form.easybell.de/api anonymous GET surface fully enumerated from 21 Vite chunks; tariff catalog verified (GET /api/plans/SIPD 200 7987B), contract-summary session-gated (404); POST/PUT/DELETE mo
- CHANGED partner.easybell.de fingerprint confirmed: Laravel Blade login panel (partnerportal_session cookie, Matomo siteId=2), bundle leaks no /api/* surface (Sentry DSN only) — passive API-leak line closed cl
- CHANGED survey.easybell.de: Caddy 200-empty sink on /,/admin,/index.php,/login (no CT, CL:0) — abandoned stub vhost; closed
- CHANGED backmon.easybell.de: nginx blanket 403 (146B, voip ingress family) on /,/metrics,/health,/status,/api,/index.html,/monitor — IP-allowlist deny; closed
- CHANGED voip-management.easybell.de/api: CORS credentialed read+write CONFIRMED on all 7 Spring routes (account,accounts,subscriber,subscribers,number,numbers,session) — OPTIONS preflights echo Allow-Methods 

## 2026-09-06 18:05:28 UTC
- CHANGED No new live probes since 2026-09-06 04:48:35 UTC; WAF backoff fully cleared (>10h since voip burst, >4h since order-form burst)
- CHANGED voip-management.easybell.de/api CORS credentialed read+write CONFIRMED on all 7 Spring routes (account,accounts,subscriber,subscribers,number,numbers,session) — OPTIONS preflights echo Allow-Methods P
- CHANGED order-form.easybell.de/api anonymous GET surface fully enumerated from 21 Vite chunks; tariff catalog verified (GET /api/plans/SIPD 200 7987B), contract-summary session-gated (404); POST/PUT/DELETE mo
- CHANGED partner.easybell.de fingerprint confirmed: Laravel Blade login panel (partnerportal_session cookie, Matomo siteId=2), bundle leaks no /api/* surface (Sentry DSN only) — passive API-leak line closed cl
- CHANGED survey.easybell.de: Caddy 200-empty sink on /,/admin,/index.php,/login (no CT, CL:0) — abandoned stub vhost; closed
- CHANGED backmon.easybell.de: nginx blanket 403 (146B, voip ingress family) on /,/metrics,/health,/status,/api,/index.html,/monitor — IP-allowlist deny; closed
- CHANGED REJECTED OATH @ connectme-app.easybell.de: bare `//login-online-session-converged638e2` returns SPA shell 200 (09:16:21, 19765B) on clean probe; prior "bare // path 404s" were backtick-polluted URLs →
- CHANGED REJECTED MISCONFIG @ connectme-app.easybell.de: double-slash redirect_uri is cosmetic-but-functional (200 SPA shell identical to single-slash variants); no path-normalization bypass surface

## 2026-09-06 20:12:49 UTC

## 2026-09-06 22:10:24 UTC

## 2026-09-06 23:59:05 UTC

## 2026-09-07 03:19:31 UTC

## 2026-09-07 08:30:20 UTC

## 2026-09-07 14:28:32 UTC

## 2026-09-07 18:54:03 UTC

## 2026-09-07 21:53:36 UTC

## 2026-09-07 23:54:26 UTC
- CHANGED connectme-uat/dev state inconsistency: 2026-09-07 18:52 lead claims the UAT/dev dotfile line was "closed and rejected on both sub-lines" — but no matching REJECTED entry exists in the KB tail (all ent

## 2026-09-08 02:34:12 UTC
- CHANGED connectme-app-uat.easybell.de: `.env` → 404 (284KB custom error HTML, not SPA shell); `.git/config` → 404 (same 284KB); root = 200 (5KB SPA). No dotfile/debug disclosure — line closed.
- CHANGED connectme-app-dev.easybell.de: DNS does not resolve (curl error 6). Not externally reachable — line closed.

## 2026-09-08 07:34:36 UTC
- NEW connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- NEW connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write (90) remains sole unfiled HIGH; ~36h+ filing latency only rising program risk
- CHANGED No new passive probes since 2026-09-06 04:48:35 UTC; inventory + KB unchanged beyond connectme-uat/dev closure
- NEW connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- NEW connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write (90) remains sole unfiled HIGH; ~36h+ filing latency only rising program risk
- CHANGED No new passive probes since 2026-09-06 04:48:35 UTC; inventory + KB unchanged beyond connectme-uat/dev closure

## 2026-09-08 12:18:42 UTC
- NEW connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- NEW connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write (90) remains sole unfiled HIGH; ~37h filing latency only rising program risk
- CHANGED No new passive probes since 2026-09-06 04:48:35 UTC; inventory + KB unchanged beyond connectme-uat/dev closure

## 2026-09-08 16:46:18 UTC
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write (90) remains sole unfiled HIGH; ~38h filing latency only rising program risk
- CHANGED No new passive probes since 2026-09-06 04:48:35 UTC; inventory + KB unchanged beyond connectme-uat/dev closure

## 2026-09-08 19:43:23 UTC
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write (90) remains sole unfiled HIGH/CRITICAL; ~38h+ filing latency only rising program risk
- CHANGED No new passive probes since 2026-09-06 04:48:35 UTC; inventory + KB unchanged beyond connectme-uat/dev closure

## 2026-09-08 22:18:05 UTC
- NEW voip-management.easybell.de/api: live reconfirm 22:16:53 UTC 09-08 — OPTIONS /api/account returns 200, `ACAO: https://evil.example.at` + `ACAC: true` + `Allow-Methods: PUT` + `Allow-Headers: authoriza
- CHANGED login.easybell.de: `?redirect=&next=&url=` params NOT echoed in 302 (→ https://login.easybell.de/login); Laravel XSRF-TOKEN+ekp_session cookie family identical to my.easybell.com. No open-redirect / O
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write (90) remains sole unfiled HIGH/CRITICAL; ~38h+ filing latency only rising program risk
- CHANGED No new passive probes since 2026-09-06 04:48:35 UTC; inventory + KB unchanged beyond connectme-uat/dev closure

## 2026-09-09 00:21:33 UTC
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write (90) reconfirmed LIVE 2026-09-08 22:16:53 UTC on `/api/account` (ACAO:evil-origin + ACAC:true + Allow-Methods:PUT) — finding still exploit
- CHANGED login.easybell.de: `?redirect=&next=&url=` params NOT echoed in 302 (→ /login); sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.com); no open redirect / OAuth code-theft chain —
- CHANGED connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- CHANGED connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed

## 2026-09-09 04:56:38 UTC
- CHANGED voip-management.easybell.de/api: Credentialed CORS read+write reconfirmed LIVE 2026-09-08 22:16:53 UTC on `/api/account` (ACAO:evil-origin + ACAC:true + Allow-Methods:PUT) — finding exploitable ~3 day
- CHANGED login.easybell.de: `?redirect=&next=&url=` params NOT echoed in 302; sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.com); no open redirect / OAuth code-theft chain — line close
- CHANGED connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- CHANGED connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed

## 2026-09-09 09:22:44 UTC
- CHANGED voip-management.easybell.de/api: fresh OPTIONS capture at 04:53:30 UTC 09-09 reconfirms live CORS (ACAO evil-origin + ACAC:true + Allow-Methods:PUT) — 3rd independent reconfirmation since discovery.

## 2026-09-09 13:55:04 UTC
- CHANGED voip-management.easybell.de/api: fresh OPTIONS capture at 04:53:30 UTC 09-09 reconfirms live CORS (ACAO evil-origin + ACAC:true + Allow-Methods:PUT) — 3rd independent reconfirmation since discovery; ~
- CHANGED voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 3rd time at 04:53:30 UTC 09-09 (OPTIONS /api/account → ACAO:evil-origin + ACAC:true + Allow-Methods:PUT) — finding persis
- CHANGED connectme-app-uat.easybell.de: `.env` and `.git/config` return 404 (284KB custom error HTML, not SPA shell) — dotfile/debug line closed
- CHANGED connectme-app-dev.easybell.de: DNS NXDOMAIN — not externally reachable, line closed
- CHANGED login.easybell.de: `?redirect=&next=&url=` not echoed in 302; sets Laravel XSRF-TOKEN+ekp_session (same cookie family as my.easybell.com); no open redirect/OAuth code-theft — line closed cleanly

## 2026-09-09 17:31:12 UTC

## 2026-09-09 20:01:27 UTC

## 2026-09-09 22:25:39 UTC
- CHANGED voip-management.easybell.de/api: credentialed CORS read+write reconfirmed LIVE 3rd time at 2026-09-09 04:53:30 UTC (OPTIONS /api/account → ACAO:evil-origin + ACAC:true + Allow-Methods:PUT) — finding p

## 2026-09-10 00:37:11 UTC

## 2026-09-10 05:16:47 UTC

## 2026-09-10 09:52:18 UTC
- NEW 2026-09-10 09:49:42 UTC — No new passive probes since 2026-09-10 05:16:47 UTC; inventory + KB unchanged; all passive lines closed; filing latency only rising program risk.

## 2026-09-10 14:01:48 UTC

## 2026-09-10 17:49:21 UTC

## 2026-09-10 20:02:33 UTC

## 2026-09-10 22:39:09 UTC

## 2026-09-11 00:32:44 UTC

## 2026-09-11 05:11:59 UTC

## 2026-09-11 09:48:54 UTC

## 2026-09-11 14:01:54 UTC

## 2026-09-11 17:43:31 UTC

## 2026-09-11 20:08:59 UTC
- NEW voip-management.easybell.de/api: Credentialed CORS read+write reconfirmed LIVE 2026-09-11 20:03:43 UTC on all 7 Spring routes (account, accounts, subscriber, subscribers, number, numbers, session) — 7
- NEW my.easybell.com/api/{crm,ebit,strapi}: Wildcard CORS (ACAO:*) with POST+Authorization+Content-Type allowed from any origin reconfirmed LIVE 2026-09-11 20:07:30 UTC — 3 proxy endpoints, no ACAC:true (c
- CHANGED Filing latency for flagship CORS finding now ~126h post-triage-VALID (since 2026-09-06 19:19) / ~10.1 days post-discovery; evidence gates fully satisfied (7 captures + live tracker); only risk is repo
