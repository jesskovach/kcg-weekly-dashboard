# KCG Weekly Dashboard

A professional project status dashboard for tracking six workstreams using PMBOK methodology and RAG (Red-Amber-Green) status tracking.

## What It Does

Displays a unified week-at-a-glance calendar view with:
- **Time blocks** — Writing, study, planning, review, and work sessions (color-coded by type)
- **Deadlines** — Workstream obligations with days-remaining indicators
- **Workstream table** — Full status tracking with RAG dropdown, phase, priority, and next actions
- **KPI bar** — Real-time summary: total workstreams, status counts, overdue, high priority, closed
- **Archive section** — Completed workstreams
- **Interactive editing** — Click any block to update; inline editing for workstreams

## Live Features

✓ Week navigation (Previous/Next/Today buttons)
✓ Time block management (add/edit/delete per day)
✓ Deadline tracking with visual prominence
✓ localStorage persistence (data survives refresh)
✓ Print-optimized CSS (landscape letter-size)
✓ Responsive design (mobile-friendly grid)
✓ No external dependencies (vanilla HTML/CSS/JS)

## Data Structure

All data persists in browser localStorage with these keys:

```javascript
// Workstreams (6 items)
STORAGE_KEY = "kcg_workstreams_data"
// Example:
[
  {
    id: "WS-01",
    name: "KCG Platform",
    phase: "Development",
    rag: "GREEN",
    priority: "High",
    deadline: "2026-04-15",
    nextAction: "Complete API testing",
    closed: false
  }
]

// Time blocks (daily entries)
BLOCKS_KEY = "kcg_time_blocks"
// Example:
[
  {
    date: "2026-03-27",
    label: "Writing Block",
    workstreamId: "WS-08",
    startTime: "09:00",
    endTime: "11:00",
    type: "writing"
  }
]
```

## Getting Started

### Local Development
1. Clone the repo: `git clone https://github.com/[your-username]/kcg-weekly-dashboard.git`
2. Open `index.html` in your browser
3. Start adding time blocks and updating workstream status

### Weekly Update Ritual (30 minutes)
Every Friday at 3:00 PM:
1. Open the dashboard
2. Review the current week (time blocks should be complete)
3. For each workstream, assess:
   - Schedule health (on track? behind? ahead?)
   - Budget status (under? on? over?)
   - Quality metrics (passing gates? new risks?)
   - Risk status (blockers? mitigations working?)
4. Click workstream row → update RAG status + next action
5. Update deadline if it has slipped
6. Take a screenshot for your case study documentation

**Time allocation**: 20-30 minutes for status update + screenshot

## Deployment

### Option A: Vercel (Recommended)
**Why**: Free, automatic deployments on every git push, custom domain support

Steps:
1. Create GitHub repo (see instructions below)
2. Sign up at vercel.com
3. Import your GitHub repo into Vercel
4. Vercel auto-deploys on each push (no manual steps needed)
5. Get a live URL (e.g., `kcg-dashboard.vercel.app`)

### Option B: Alternative Hosting
- **GitHub Pages**: Free, but no backend (localStorage only works)
- **Your own server**: Use existing hosting if available
- **Netlify**: Similar to Vercel, free tier available

## GitHub Setup

```bash
# Initialize git (first time only)
git init

# Configure git user (if not already done)
git config user.name "Your Name"
git config user.email "your-email@example.com"

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: KCG Weekly Dashboard MVP"

# Add remote (replace with your GitHub repo URL)
git remote add origin https://github.com/[your-username]/kcg-weekly-dashboard.git

# Push to GitHub
git push -u origin main
```

**First time on GitHub?** Create a new repo at github.com → click "+" → "New repository" → name it `kcg-weekly-dashboard` → copy the HTTPS URL above.

## File Structure

```
kcg-weekly-dashboard/
├── index.html          # Complete dashboard (single file)
├── README.md           # This file
├── .gitignore          # Git ignore rules
└── vercel.json         # (optional) Vercel config
```

## Customization

### Colors (Design System)
Open `index.html`, find `:root { --plum: #5A496B; ... }` and adjust:
- `--plum`: Primary brand color
- `--ink`: Dark text
- `--lavender`: Accent
- `--red`, `--amber`, `--green`: RAG status colors

### Workstream Names
In `index.html`, search for `const WORKSTREAMS = [` and update the six workstream objects:
```javascript
{ id: "WS-01", name: "Your Workstream Name", phase: "Phase", ... }
```

### Time Block Types
The five block types are color-coded. To add more, update the CSS `.week-event.block-[type]` classes.

## Keyboard Shortcuts

- **Tab**: Navigate between workstreams and blocks
- **Enter**: Open edit modal for selected block
- **Escape**: Close any open modal
- **Ctrl+P** (or **Cmd+P**): Open print preview

## Accessibility

✓ WCAG 2.1 AA compliant
✓ Keyboard navigable (Tab through all elements)
✓ Color + icon for RAG status (not color-only)
✓ Focus ring visible on interactive elements
✓ Semantic HTML with ARIA labels
✓ Screen reader friendly

Tested with:
- Chrome accessibility audits (Lighthouse)
- Manual keyboard navigation
- Color contrast verification (WebAIM)

## Browser Support

| Browser | Support | Notes |
|---------|---------|-------|
| Chrome | ✓ | Primary development target |
| Safari | ✓ | iOS 12+ |
| Firefox | ✓ | Latest versions |
| Edge | ✓ | Chromium-based |
| Mobile | ✓ | Touch-friendly UI |

## Data Backup

Since data lives in localStorage (browser storage), it persists locally but is not synced across devices.

**To backup your data:**
1. Open Developer Tools (F12)
2. Go to Application → Storage → Local Storage
3. Find `kcg_workstreams_data` and `kcg_time_blocks`
4. Copy the values to a safe location

**To restore:**
1. Open the dashboard
2. Open Developer Tools → Console
3. Paste: `localStorage.setItem('kcg_workstreams_data', '[...]')`

## Roadmap (Phase 2)

- [ ] Google Calendar integration (auto-sync time blocks)
- [ ] GitHub API integration (auto-pull PR/issue status)
- [ ] Notion integration (sync workstream data)
- [ ] Email notifications (weekly status summary)
- [ ] Slack integration (post updates to channel)
- [ ] Dark mode toggle
- [ ] Export to PDF/Excel

## Support & Questions

For issues, create a GitHub issue with:
1. What happened
2. What you expected
3. Steps to reproduce
4. Browser/OS info

## License

Personal use / Consulting business proof point. Modify freely for your own use.

---

**Last updated:** March 27, 2026
**Version:** 1.0 (MVP)
**Status:** Production-ready for solo use and prospect demonstrations
