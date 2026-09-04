# hameefy.github.io

A minimal academic personal site, styled after
[hayoungchoi-knu.github.io](https://hayoungchoi-knu.github.io/): plain HTML/CSS, no build step,
same six-page structure (Home, Publications, People, News, Projects, Contact).

## Files

```
index.html          Home — bio, positions, education, service
publications.html   All 38 publications (2015–2026), from your CV
people.html         Students supervised, examinerships, collaborators
news.html           Index of the Computational Mathematics Research Digest
news/               Permanent pages for individual weekly digest issues
projects.html       CodeLaTeX, claude-latex-skill, outreach/video content
contact.html        Emails, offices, ORCID/Scopus/WoS/Scholar, social links
style.css           All styling (one shared stylesheet)
assets/hassan.jpg   Your portrait, cropped square from the uploaded photo
```

There is no framework, no npm install, and no build step — GitHub Pages serves these files exactly
as they are.

## What's confirmed vs. what's left

Everything on the site is now sourced from your CV (March 2026) or from things you confirmed directly
— publications, degrees, appointments, students, emails, identifiers. Two things worth knowing:

- **Personal details left off on purpose** — date of birth, marital status, nationality, mobile
  numbers, and your referees' personal contact details are in the CV but not published anywhere on
  the site. Say the word if you'd like your own mobile number added to Contact — everything else I'd
  leave off by default.
- **The CV stays private** — no PDF is linked or included in this site, and there's no "Download CV"
  button. If that changes later, just ask and I'll build a public-safe version.

Smaller open items:
- **news.html** now indexes the weekly Computational Mathematics Research Digest. Each issue has a
  permanent, shareable page under `news/`, with newest issues displayed first.
- **projects.html** — CodeLaTeX is marked "in development" with no public link, per your note that
  it's still under construction. Ask and I'll add a repo/demo link once it's ready to share.

## Adding your photo

Already done — `assets/hassan.jpg`, cropped square from your uploaded photo. To swap it for another
one later, just replace that file (keep the filename, or update the `src` in `index.html`).

## Deploying to GitHub Pages

**Option A — user site (recommended): `hameefy.github.io`**

```bash
# from this folder
git init
git remote add origin https://github.com/hameefy/hameefy.github.io.git
git add .
git commit -m "Initial site"
git branch -M main
git push -u origin main
```

Create the repo on GitHub first, named exactly `hameefy.github.io` (this exact name is what makes
GitHub serve it at that URL automatically — no extra Pages configuration needed). It will be live at
`https://hameefy.github.io/` within a minute or two of pushing.

**Option B — project site under an existing repo**

If you'd rather host this under a different repo name, push it there instead and enable Pages in
**Settings → Pages → Deploy from a branch**, choosing `main` and the `/ (root)` folder. The site will
then be served at `https://hameefy.github.io/<repo-name>/`.

## Keeping it updated

**New publication** — copy one `<li class="pub-item">…</li>` block in `publications.html`, fill in
authors/title/venue/link, and renumber every `<span class="pub-num">[N]</span>` above it by +1 (newest
paper = highest number, shown first — the `reversed` attribute on the `<ol>` just controls the visual
counting direction, so the numbers themselves still need to be right).

**Weekly digest publication** — the scheduled Computational Mathematics Digest publishes directly
to the `main` branch every Friday. It creates or updates the date-named permanent issue, adds exactly
one newest-first card to `news.html`, updates adjacent-issue navigation, and refetches changed files
for validation. The date-based workflow is idempotent, so retrying the same run must not create a
duplicate issue or card.

For a manual fallback, copy `news/digest-template.html`, rename it
`YYYY-MM-DD-computational-mathematics-digest.html`, replace the placeholders, add a new
`.digest-card` at the top of `news.html`, and update the previous issue's “Newer issue” link.

Each weekly issue should contain a highly selective shortlist of roughly 5–8 papers, using the first
online-publication date (including online-first articles). Cover numerical optimization, unconstrained
optimization, nonlinear least squares, nonlinear equations, and optimization methods for neural
networks and machine learning. Check Springer, Elsevier, Taylor & Francis, SIAM, Wiley, and strong
primary-source repositories. For every paper, include 2–4 author-attributed **Main result claims**
bullets that distinguish theorem-backed results from empirical claims and retain important assumptions,
baselines, metrics, and limitations. Publish fewer than five items instead of padding a weak week, and
note target topics or named publishers that produced no strong eligible item.

**New student / project** — copy the relevant `.person` or `.project` block in the corresponding
page and edit the text. No other page needs to change.

## Custom domain (optional)

If you'd like this at a domain you own instead of `hameefy.github.io`, add a `CNAME` file to this
folder containing just the domain name, and point a `CNAME` DNS record at `hameefy.github.io` — ask
if you'd like help with this once you have a domain in mind.
