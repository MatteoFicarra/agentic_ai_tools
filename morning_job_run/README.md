# Morning Job Run: a daily job search with Claude

A setup kit (a Claude skill) that builds you a personal, automated job search inside Claude.

You answer a guided interview once: your CV, the roles you want, what matters to you (contract, salary, remote work, seniority, location…), the employers you'd like to work for. The kit then builds:

- **Your dashboard**: a private page in your Claude account where new openings appear every morning, graded **A–D** and sorted. You mark each job **Apply**, **Maybe** or **✕**, and leave notes. The next run learns from them.
- **Your personal daily-run skill** (`morning-job-run-<yourname>`): it reads your LinkedIn job alerts, checks the career sites on your watchlist, confirms each posting is still live on the employer's site, scores it, and adds it to the dashboard.
- **LinkedIn job alerts** designed from your profile, which you set up with Claude's step-by-step help.
- **A scheduled morning run**, so the dashboard is up to date when you wake up.

It works for any field: you define what a good job looks like, and the scoring is built around your answers.

---

## How it works

```
LinkedIn alert emails ─┐
Employer career sites ─┼─► daily run ─► screen ─► confirm live ─► score ─► dashboard
Job boards (leads) ────┘                                                    │
                                    your Apply / Maybe / ✕ and notes ◄──────┘
```

**Scoring.** Every job gets:

- **Appeal (0–100)**: how much you'd want it. Points from the criteria you chose (role is always one; you might add employer type, contract, salary, work mode…), rescaled to 100.
- **Fit (0–100)**: how likely you are to get it, given your record.
- **A grade (A–D)** from appeal and fit, then lowered by any **caps** you set. For example, "a job in a tier-2 city can be at most a B", or "on-site can be at most a C".

Each preference you care about becomes one of: a **deal-breaker** (the job is never shown), **points** (it adds to appeal), a **cap** (it limits the grade), or nothing.

**Confirmation.** Job boards often keep ads online long after they've closed. A job is only marked *confirmed* when it's live on the employer's own site or the employer's own LinkedIn posting. Otherwise it's marked *to be checked*. When you're at your computer you can ask Claude to "check the dashboard", and it verifies those postings in your browser.

---

## What you need

### Required

- [ ] **A Claude plan with skills, code execution and file creation.** Turn on code execution and file creation in Claude's settings.
- [ ] **The Artifact tool with its database capability**, used for the dashboard. The kit checks this first and tells you if it's missing on your account or plan.
- [ ] **Your CV** (PDF or Word).

### Strongly recommended

- [ ] **Gmail connected to Claude**, for the mailbox where your job alerts arrive. Without email the run still works, but it finds fewer jobs, later.
- [ ] **A LinkedIn account**, for job alerts. The kit designs the alerts with you and walks you through creating them.
- [ ] **Scheduled tasks** in your Claude plan or app, for the unattended morning run. Without it, you start each run yourself by saying "run my job search".

### Optional

- [ ] **Claude in Chrome**, for the verification pass on employer sites and LinkedIn.
- [ ] **The Claude desktop app with a connected folder**, for two optional modules: an **application tracker** (Claude adds jobs to your spreadsheet) and **cover letters** (drafted in the style of your past letters).
- [ ] **A list of contacts** at employers you're interested in. The dashboard flags jobs where you know someone.

### Good to have ready before you start

Setup takes about 20–40 minutes. It goes faster if you've thought about:

- the 2–3 kinds of roles you're aiming for, and the job titles they go by;
- where you'd work, and whether you'd relocate or work remotely;
- contract type (permanent, temporary, freelance), hours, and the salary you'd need and would like;
- your seniority level and years of experience;
- the employers or sectors you'd most like to work in, and any you'd never consider.

---

## Install

1. Download `job-search-setup.zip` from the [Releases](../../releases) page. Or zip the `job-search-setup` folder yourself: the ZIP must contain the folder, with `SKILL.md` inside it.
2. In Claude, open the skills settings and upload the ZIP. Its location varies by version (currently **Customize → Skills** or **Settings → Capabilities → Skills**). See Anthropic's help article [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude).
3. Make sure the skill is switched on.

## Set up your job search

Open a new chat and say:

> Set up my job search.

Claude walks you through the steps: checklist, email, CV, target roles, preferences, location, exclusions, watchlist, contacts, optional modules, LinkedIn alerts, run time. It shows you a summary to confirm before building anything.

At the end you'll do three things yourself:

1. **Create the LinkedIn alerts**, following Claude's plan.
2. **Install your personal skill**: click **Save skill** on the card Claude shows, or upload the file in the skills settings.
3. **Create the scheduled task**, with Claude's instructions.

## Daily use

- **Morning:** open your dashboard (it's in your artifacts list as "Morning Job Run – <Name>"). Review new jobs, then mark them Apply, Maybe or ✕ and add notes.
- **"Run my job search"** in a chat runs the search on demand.
- **"Check the dashboard"**, with Chrome connected, verifies the *to be checked* postings.
- **"Write a cover letter for …"** and **"add … to my tracker"** work if you turned those modules on.

## Change your settings

Say, for example, "update my job search: add Vienna as a tier-1 city" or "I'd now accept fixed-term contracts". The setup kit's update mode changes only what you asked. It also proposes matching changes to your LinkedIn alerts, and gives you a new version of your skill to install.

---

## Privacy

- **Your personal skill contains your CV details** (profile, preferences, contacts). It lives in your Claude account. Don't share it, and never commit it to a public repository. The `.gitignore` here excludes generated `morning-job-run-*` files, in case you work from a clone.
- Your dashboard is private to your Claude account unless you choose to share it.
- The daily run only reads job-alert and job-related emails in the mailbox you confirm. It never sends, deletes or changes email.
- **Shared Claude accounts:** if someone else uses the same Claude account, tell the kit at the start. It then tags everything with your name, never touches the other person's skills or files, and checks whose mailbox is connected before reading it.

## Limitations and cautions

- **Always check a posting yourself before applying.** Claude can misread postings, miss jobs, or score them differently than you would. The dashboard helps you triage; it doesn't decide for you.
- **No actions on your behalf.** The skills never apply, sign in, create accounts or contact anyone. In the browser they only read pages.
- **LinkedIn and other sites restrict automated access** in their terms. The verification pass is designed to run read-only, at human pace, while you're present. Its use is your responsibility. If you'd rather not use it, skip Chrome: the daily run works without it.
- **Career sites often block automated reading.** Some employers on your watchlist can't be checked each day; the run lists them.
- **Usage limits:** a daily run with many employers uses a fair amount of your Claude usage. Trim the watchlist if it runs into limits.
- Product names, menus and features in Claude and LinkedIn change. The kit looks up current steps where it can.

---

## Repository contents

```
job-search-setup/                  the skill to install
├── SKILL.md                       the guided setup and update mode
├── references/
│   ├── preferences.md             preference questions → deal-breakers / points / caps
│   ├── linkedin_alerts.md         designing and creating LinkedIn alerts
│   ├── defaults.md                neutral starting points shown during setup
│   ├── personal_skill_template.md the daily-run skill, filled in during setup
│   ├── optional_modules.md        tracker and cover-letter modules
│   └── placeholders.md            what fills each template placeholder
└── assets/
    └── dashboard_template.html    the dashboard page
examples/
└── economist.md                   a worked example configuration
```

## Contributing

Issues and pull requests are welcome. Especially useful:

- **Worked examples for other fields** in `examples/` (role bands, typical employer types, exclusions, sample alerts). Keep them anonymous.
- Reports of setup steps that no longer match Claude's or LinkedIn's current interface.

## License

MIT. See [LICENSE](LICENSE).

This is an independent project, not affiliated with or endorsed by Anthropic or LinkedIn.
