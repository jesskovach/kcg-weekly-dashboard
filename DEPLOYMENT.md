# Deployment Guide

## Quick Start: Deploy to Vercel in 5 Minutes

### Prerequisites
- GitHub account (free)
- Vercel account (free, sign in with GitHub)
- This repository pushed to GitHub

### Step 1: Push Code to GitHub

```bash
# From your local kcg-weekly-dashboard directory
git init
git add .
git commit -m "Initial commit: KCG Weekly Dashboard MVP"

# Create a NEW repository at github.com
# Then run this (replace with your GitHub URL):
git remote add origin https://github.com/[YOUR-USERNAME]/kcg-weekly-dashboard.git
git push -u origin main
```

**First time with GitHub?**
1. Go to github.com → Sign in/create account
2. Click "+" icon (top right) → "New repository"
3. Name: `kcg-weekly-dashboard`
4. Click "Create repository"
5. Copy the HTTPS URL (looks like: `https://github.com/your-username/kcg-weekly-dashboard.git`)
6. Run the commands above with that URL

### Step 2: Deploy on Vercel

1. Go to **vercel.com** → Sign up (or log in with GitHub)
2. Click **"Add New..."** → **"Project"**
3. Select your `kcg-weekly-dashboard` repository
4. Click **"Import"** (keep all defaults)
5. Click **"Deploy"**
6. Wait 30 seconds → Your dashboard is live!

**Your live URL**: `https://kcg-weekly-dashboard.vercel.app` (or custom domain)

### Step 3: Set Custom Domain (Optional)

If you want `dashboard.kovachconsultants.com` instead:

1. In Vercel, go to your project → **Settings** → **Domains**
2. Enter your custom domain
3. Follow DNS setup instructions
4. Wait 24 hours for DNS propagation

## After Deployment

### Testing Live
1. Open your live URL in browser
2. Add a time block (click "+ Add Time Block" on any day)
3. Refresh the page → data still there? ✓ localStorage working
4. Update a workstream status → RAG dropdown changes? ✓ Editing works
5. Take screenshot for your case study

### Automatic Updates
From now on:
1. Make changes locally in `index.html`
2. Commit: `git add . && git commit -m "Update dashboard [description]"`
3. Push: `git push origin main`
4. Vercel auto-deploys in ~1 minute
5. Live URL updates automatically

No manual deployment needed.

## Troubleshooting

### "Permission denied" when pushing to GitHub
**Solution:** Use HTTPS instead of SSH. Your git remote should be:
```
https://github.com/your-username/kcg-weekly-dashboard.git
```
Not:
```
git@github.com:your-username/kcg-weekly-dashboard.git
```

### "Deployment failed" on Vercel
**Check:**
1. Is `index.html` in the root directory? (Not in a subfolder)
2. Does `index.html` open locally in your browser?
3. Check Vercel build logs (Project → Deployments → click failed deployment)

### Data not persisting after deployment
**Cause:** localStorage works per domain/origin. Your live domain is different from local.
**Solution:** This is expected. Data is separate for each domain:
- Local: http://localhost → has your test data
- Live: https://kcg-weekly-dashboard.vercel.app → starts fresh
- Solution: Re-enter your workstreams on the live version (one-time setup)

### Changes pushed but live URL not updating
**Solution:** Vercel caches. Try:
1. Hard refresh in browser (Ctrl+Shift+R or Cmd+Shift+R)
2. Wait 2-3 minutes for cache to clear
3. Check Vercel deployments tab to confirm it deployed

## Rollback (Undo a Bad Deployment)

If you push a bad version:

```bash
# See your commit history
git log --oneline

# Find the commit you want to go back to
# Then force push to revert (CAREFUL - only if you know what you're doing)
git revert [commit-hash]
git push origin main
```

Or in Vercel:
1. Go to your project → Deployments
2. Find the last good deployment
3. Click → "Redeploy"

## Next: Custom Domain (Optional)

If you own kovachconsultants.com:

1. Update your DNS provider (GoDaddy, Namecheap, etc.)
2. Add a CNAME record pointing to Vercel
3. Details: Vercel dashboard → Settings → Domains

This makes your dashboard live at `dashboard.kovachconsultants.com` instead of the Vercel domain.

---

**You're live!** Time to start using it. Friday 3pm: First status update ritual.
