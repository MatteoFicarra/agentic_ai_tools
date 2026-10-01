# Cover Letter Writer: cover letters with Claude, in your own voice

A setup kit (a Claude skill) that builds you a personal cover-letter writer inside Claude.

You answer a short interview once: your CV, a few of your own past cover letters, where you keep your applications, and your rules (format, length, language). The kit then builds **your personal skill**, `cover-letter-<yourname>`, which writes every letter with the same careful method:

1. **The full posting first.** It saves the complete job posting in the letter's folder before anything else. If it can't read the page, it asks you to save it.
2. **Posting analysis:** requirements (required vs preferred), tasks, the ideal candidate, and the keywords a screening tool would look for.
3. **Your own letters as references.** During setup it sorts your past letters into categories that make sense for your field. For each new job it reads three or four of them, the most recent first, to follow your structure and voice. Letters drafted with Claude are never used as references.
4. **Match matrix.** Each requirement is matched against your real record: hard skills, relevant experience and provable results first. Things every applicant has are left out.
5. **It asks instead of guessing** when it isn't sure how your experience fits a requirement.
6. **Two independent checks** before saving: a simulated recruiter screening tool scores the letter against the posting, and a simulated AI-writing detector flags passages that read as machine-written. Revisions use true evidence only, never invented claims or stuffed keywords.
7. **Your format and length**, built from one of your own letters as the layout template, and checked on the exported file.

It works for any field and any country: the categories, format and voice all come from your own letters.

---

## Use it on its own, or with Morning Job Run

- **On its own:** give it a link, a PDF or pasted text: *"Write a cover letter for this posting."*
- **With [Morning Job Run](../morning_job_run)** (the daily job-search kit in this repository): it can pick up the jobs you mark **Apply** on your dashboard (*"Write the letters for the Apply jobs"*) and log each letter in your application tracker.

You can install either kit without the other.

---

## What you need

### Required

- [ ] **A Claude plan with skills, code execution and file creation.** Turn on code execution and file creation in Claude's settings.
- [ ] **Your CV** (PDF or Word).
- [ ] **Your own past cover letters.** Five or more is best; two works. With none (e.g. a first job search), setup asks a few questions about format and tone instead, and the skill improves as you add the letters you send.

### Recommended

- [ ] **The Claude desktop app with your applications folder connected** (or Claude Code with local files). In a web chat it still works: you upload the posting and files and download the letters.
- [ ] **A PDF converter in the session** (LibreOffice), to export PDFs and check the length in pages. Without it, letters are delivered as Word files and the length is checked in words.

### Optional

- [ ] **Claude in Chrome**, to read job postings that block automated reading.
- [ ] **An application tracker** (Excel, CSV, or a Google Sheet with a connector), to log each letter.
- [ ] **A Morning Job Run dashboard**, to write letters for the jobs you mark Apply.

---

## Install

1. Download `cover-letter-setup.zip` from this folder. Or zip the `cover-letter-setup` folder yourself: the ZIP must contain the folder, with `SKILL.md` inside it.
2. In Claude, open the skills settings and upload the ZIP. Its location varies by version (currently **Customize → Skills** or **Settings → Capabilities → Skills**). See Anthropic's help article [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude).
3. Make sure the skill is switched on.

## Set up

Open a new chat and say:

> Set up my cover letter writer.

Claude walks you through: checklist, folders, CV and fact bank, past letters (format, voice, categories), rules (language, length, output format, how to handle gaps), optional tracker and dashboard. It shows a summary to confirm, then builds your skill. Click **Save skill** on the card, or upload the file in the skills settings.

## Daily use

- *"Write a cover letter for <link / file>."*
- *"Write the letters for these three postings."* (one batched round of questions for all of them)
- *"Write the letters for the Apply jobs."* (with Morning Job Run)
- *"Redo the letter for <employer>."* (saved as `_v2`, never over the old one)

Each run ends with a short report: the category it chose, the reference letters it used, the screening score, the detector verdict, and what you should check before sending.

## Change your settings

Say, for example, *"update my cover letter writer: add my new letters"*, *"add these facts to my fact bank"*, or *"letters should be at most one page"*. The setup kit's update mode changes only what you asked and gives you a new version of your skill to install.

---

## Privacy

- **Your personal skill contains your CV details and a catalogue of your letters.** It lives in your Claude account. Don't share it, and never commit it to a public repository.
- The skill never reads or changes files outside the folders you give it, and never edits or deletes your existing files.
- **Shared Claude accounts:** if someone else uses the same Claude account, tell the kit at the start. It names everything after you and never touches the other person's skills or files.

## Limitations and cautions

- **Read every letter before you send it.** Claude can misread a posting or your record.
- **The checks are simulations.** They make letters more specific and more natural, but they don't predict what a real employer's software or recruiter will decide.
- **No invented claims.** The skill only uses your CV, your own letters (facts confirmed with you at setup) and your answers. When something is missing, it asks or leaves it out.
- **No actions on your behalf.** It never submits applications, creates accounts or contacts anyone.
- Product names, menus and features in Claude change. The kit looks up current steps where it can.

---

## Repository contents

```
cover-letter-setup/                the skill to install
├── SKILL.md                       the guided setup and update mode
└── references/
    ├── personal_skill_template.md the letter-writing skill, filled in during setup
    ├── placeholders.md            what fills each placeholder, and the final checks
    └── integrations.md            optional tracker and Morning Job Run links
cover-letter-setup.zip             the same folder, ready to upload
```

## Contributing

Issues and pull requests are welcome, especially reports of steps that no longer match Claude's current interface, and ideas for fields where the default letter structure doesn't fit.

## License

MIT. See [LICENSE](LICENSE).

This is an independent project, not affiliated with or endorsed by Anthropic.
