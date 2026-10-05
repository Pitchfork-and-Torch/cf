---
"cf": patch
---

fix: read `CLOUDFLARE_COMPLIANCE_REGION` before loading `cloudflare.config.ts`

Account-level API commands call `getComplianceRegion()` on every request. Loading a broken project config aborted those commands even when `CLOUDFLARE_ACCOUNT_ID` and `CLOUDFLARE_COMPLIANCE_REGION` were already set. The environment region is now resolved first (matching `CLOUDFLARE_ACCOUNT_ID`), and an unloadable config is ignored when the env supplies the region. Conflict warnings against a loadable config are unchanged.
