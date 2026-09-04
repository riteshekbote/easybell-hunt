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
