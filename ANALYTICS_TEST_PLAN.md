# Vercel Web Analytics - Comprehensive Test Plan

**Project:** KCG Weekly Dashboard
**Domain:** https://kcg-weekly-dashboard.vercel.app
**Date Created:** 2026-03-27
**Last Updated:** 2026-03-27

---

## Overview

This document provides step-by-step verification procedures for the Vercel Web Analytics implementation. The analytics system is designed to track page views, performance metrics, and user interactions automatically.

---

## Pre-Deployment Verification (Before Pushing to Main)

### Phase 1: Local Environment Checks

**1.1 Code Inspection**
- [ ] Open `index.html` in text editor
- [ ] Search for `<!-- Vercel Web Analytics`
- [ ] Verify script block exists before `</head>` tag
- [ ] Confirm script includes:
  - `window.__vercelAnalyticsLoaded` flag
  - Production environment check
  - Error event listeners
  - `defer` attribute on script tag

**1.2 verify vercel.json Configuration**
```bash
# Run this command in the kcg-weekly-dashboard directory
cat vercel.json | grep -A5 "Content-Security-Policy"
```
- [ ] CSP header includes `https://cdn.vercelinsights.com`
- [ ] CSP header includes `connect-src` rule for insights domain
- [ ] No syntax errors in JSON (validate with `jq` or online validator)

**1.3 File Size Verification**
```bash
# Confirm analytics script doesn't significantly increase file size
wc -c index.html
# Should be approximately 57,000-58,000 bytes
```
- [ ] File size is reasonable (analytics script adds ~1KB)

---

## Post-Deployment Verification (After Deploying to Vercel)

### Phase 2: Deployment Confirmation (Immediate - 5 minutes)

**2.1 Deployment Success Check**
- [ ] Go to https://vercel.com/dashboard
- [ ] Navigate to **kcg-weekly-dashboard** project
- [ ] Confirm latest deployment status: **Ready**
- [ ] Deployment should have completed in < 2 minutes
- [ ] Check deployment logs for any errors

**2.2 Live Site Access**
- [ ] Navigate to https://kcg-weekly-dashboard.vercel.app
- [ ] Page loads without errors
- [ ] Dashboard renders correctly (all KPIs, tables visible)
- [ ] No console errors visible in DevTools

---

### Phase 3: Network Request Verification (5-15 minutes)

**3.1 Browser DevTools - Network Tab**
1. Open the live site in Chrome/Firefox
2. Press `F12` to open Developer Tools
3. Go to **Network** tab
4. Refresh the page (`Ctrl+R`)
5. Look for analytics requests:

- [ ] Request to `https://cdn.vercelinsights.com/v1/script.js`
  - **Status:** Should be `200 OK` (not 404 or 403)
  - **Size:** ~5-10KB
  - **Type:** `script`
  - **Initiator:** Should show as coming from `index.html`

- [ ] Request to `https://cdn.vercelinsights.com/...` (data collection)
  - **Status:** Should be `200 OK` or `204 No Content`
  - **Type:** `xhr` or `fetch`
  - **Headers:** Should include `Authorization` header from Vercel

**3.2 Console Verification**
1. Go to **Console** tab
2. Filter for messages containing "Analytics"
3. Expected logs:
   - [ ] `[Analytics] Vercel Web Analytics loaded successfully` (success message)
   - [ ] OR `[Analytics] Development environment - analytics disabled` (if testing locally)

**3.3 CSP Header Validation**
1. Go to **Network** tab
2. Click on the main document request (`index.html`)
3. Go to **Response Headers**
4. Locate `Content-Security-Policy` header
5. Verify it contains:
   - [ ] `script-src 'self' https://cdn.vercelinsights.com`
   - [ ] `connect-src 'self' https://cdn.vercelinsights.com`

---

### Phase 4: Vercel Dashboard Analytics Section (15-60 minutes)

⚠️ **Note:** Analytics data may take 2-5 minutes to appear in the Vercel dashboard after the first page view.

**4.1 Access Analytics in Vercel**
1. Go to https://vercel.com/dashboard
2. Click on **kcg-weekly-dashboard** project
3. Navigate to **Analytics** tab (top navigation)
4. You should see one of:
   - "Enable Web Analytics" button (if not yet enabled) → Click it
   - Analytics dashboard with metrics

**4.2 First Page View Metrics (after 5 minutes)**
- [ ] "Requests" metric shows at least `1`
- [ ] "Average Response Time" displays a value
- [ ] "Status Codes" section shows HTTP 200
- [ ] One page URL appears in the list (`/` or `/index.html`)

**4.3 Monitor for 1 Hour**
Perform the following actions and monitor the dashboard:

- [ ] Load the page 3-5 times from different browsers/tabs
- [ ] Each page load should increment the request counter
- [ ] Wait 5 minutes between each load
- [ ] Observe Core Web Vitals appearing:
  - LCP (Largest Contentful Paint)
  - FID (First Input Delay)
  - CLS (Cumulative Layout Shift)

**4.4 Performance Metrics Check**
After 1 hour, analytics should show:
- [ ] **Requests:** At least 3-5 entries
- [ ] **Edge Region:** Shows deployment region (e.g., `sfo1`, `iad1`)
- [ ] **Response Time:** Average < 500ms
- [ ] **Status Codes:** Primarily 200s, no significant 4xx/5xx errors
- [ ] **Top Pages:** Shows `/` with request count

---

## Verification Checklist Summary

| Phase | Component | Expected Result | Status |
|-------|-----------|-----------------|--------|
| 1 | Local code check | Analytics script present in HTML | ☐ |
| 1 | vercel.json syntax | Valid JSON, no errors | ☐ |
| 2 | Deployment success | Vercel dashboard shows "Ready" | ☐ |
| 2 | Live site access | Page loads without errors | ☐ |
| 3 | CDN script load | HTTP 200, ~5-10KB script | ☐ |
| 3 | Console messages | Success log appears | ☐ |
| 3 | CSP headers | Content-Security-Policy present and valid | ☐ |
| 4 | Analytics enabled | Vercel dashboard shows analytics data | ☐ |
| 4 | Page view tracking | Request count increases on refresh | ☐ |
| 4 | Core Web Vitals | LCP, FID, CLS metrics appear | ☐ |

---

## Troubleshooting Guide

### Issue: "Analytics script failed to load" error in console

**Cause:** CDN unreachable or network blocked
**Solutions:**
1. Check your internet connection
2. Verify the domain `cdn.vercelinsights.com` is accessible:
   ```bash
   curl -I https://cdn.vercelinsights.com/v1/script.js
   # Should return HTTP 200 OK
   ```
3. If behind corporate firewall, add domain to whitelist
4. Clear browser cache and hard refresh (`Ctrl+Shift+R`)

### Issue: "Development environment - analytics disabled" in console

**Expected behavior** when accessing from:
- `localhost`
- `127.0.0.1`
- File system (`file://`)

**To test:** Deploy to Vercel and access the live URL only.

### Issue: No analytics data appears in Vercel dashboard after 1 hour

**Debug steps:**
1. Verify Vercel project name matches domain exactly
2. Check that you're looking at the correct Vercel project:
   ```bash
   # From your project directory
   vercel --prod --show-builders
   ```
3. Confirm CSP headers aren't blocking requests:
   - DevTools → Network → Look for failed `vercelinsights` requests
4. Check Vercel project settings → Web Analytics tab:
   - Ensure Web Analytics is "Enabled"
5. Verify deployment linked to GitHub repository:
   - Vercel Dashboard → Project Settings → Git Integration

### Issue: CSP header errors in browser console

**Error message:** `Refused to load the script ... because it violates the Content Security Policy`

**Solution:**
1. Verify `vercel.json` has correct CSP header (see Phase 3.3)
2. Redeploy the project:
   ```bash
   git push origin main
   # Vercel will automatically redeploy
   ```
3. Hard refresh browser after 2-3 minutes

### Issue: Multiple analytics scripts loading (duplicate calls)

**Indicator:** Network tab shows multiple requests to `vercelinsights.com`

**Fix (already implemented):**
- The `window.__vercelAnalyticsLoaded` flag prevents this
- If still occurring, check:
  1. That `index.html` only has ONE analytics script block
  2. That you haven't added the script multiple times
  3. Clear browser cache

---

## Performance Impact Assessment

After analytics are running for 24 hours, verify performance:

**Metrics to Monitor:**
- [ ] Page load time remains < 1.5s (check Vercel Analytics dashboard)
- [ ] No increase in Core Web Vitals
- [ ] No JavaScript errors related to analytics
- [ ] Server response time stable

**If performance degrades:**
1. Check Vercel dashboard for any error spikes
2. Verify analytics CDN requests aren't timing out
3. See rollback steps below

---

## Rollback Procedure (If Issues Occur)

If analytics cause problems, rolling back is simple:

**Step 1: Remove analytics from HTML**
```bash
cd kcg-weekly-dashboard
# Edit index.html and remove the analytics script block
# Or restore from backup:
cp index.html.backup index.html
```

**Step 2: Revert CSP headers** (optional)
```bash
# Edit vercel.json and remove the headers section
# Or restore original:
git checkout vercel.json
```

**Step 3: Commit and deploy**
```bash
git add -A
git commit -m "Rollback: Remove Vercel Web Analytics"
git push origin main
```

**Step 4: Verify rollback**
- [ ] Deployment completes on Vercel
- [ ] Live site loads without issues
- [ ] Analytics no longer appear in Vercel dashboard (within 5-10 minutes)

**Time to rollback:** < 5 minutes

---

## Success Criteria

Analytics implementation is successful when:

1. ✅ `index.html` contains the analytics script block
2. ✅ `vercel.json` has CSP headers allowing Vercel insights domain
3. ✅ Deployment succeeds without errors
4. ✅ Live site loads normally
5. ✅ Browser Network tab shows HTTP 200 for `cdn.vercelinsights.com/v1/script.js`
6. ✅ Console logs success message `[Analytics] Vercel Web Analytics loaded successfully`
7. ✅ Vercel dashboard Analytics section shows incoming page view data
8. ✅ Core Web Vitals metrics (LCP, FID, CLS) appear in dashboard
9. ✅ Performance metrics remain stable (no regression)
10. ✅ Rollback procedure works if needed

---

## Next Steps

### Immediate (Today)
1. Deploy changes to Vercel (`git push origin main`)
2. Complete Phases 2-3 verification within 15 minutes
3. Verify Phase 4 data appears within 1 hour

### Short-term (Next 24 hours)
- Monitor analytics dashboard for normal operation
- Check for any error spikes
- Verify Core Web Vitals tracking

### Long-term (This week)
- Set up alerts in Vercel for analytics anomalies
- Document analytics insights for team
- Plan for using analytics data in weekly reviews

---

## Support & Questions

If you encounter issues not covered in this guide:

1. **Check Vercel documentation:**
   - https://vercel.com/docs/analytics/quickstart
   - https://vercel.com/docs/analytics/package

2. **Debug with curl:**
   ```bash
   # Verify CDN accessibility
   curl -v https://cdn.vercelinsights.com/v1/script.js
   ```

3. **Contact:** Refer to Vercel support at https://vercel.com/support

---

**Document Version:** 1.0
**Last Verified:** 2026-03-27
