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
