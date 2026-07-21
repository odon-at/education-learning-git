# Learning Git With Open Data — ODON Intern Learning Agenda

*A hands-on course teaching version control and collaboration, built around ODON's real
GitHub organisation ([github.com/odon-at](https://github.com/odon-at)) and real open data.*

---

## 1. Goals & assumed format

**Goal:** by the end, interns can confidently use Git and GitHub to contribute to ODON's
projects (the Jekyll website, data pipelines, dashboards) — not just recite commands.

**Assumptions (adjust as needed):**
- 6 sessions, ~90 minutes each, one per week, small group (2–6 people), in person or hybrid.
- No prior Git experience assumed. Some participants may know spreadsheets/basic scripting, not more.
- Delivered live with a facilitator, but every session leaves behind self-paced material so
  it also works as an **asynchronous track for members** who can't attend live.
- Each session = short concept explainer (15–20 min) → guided hands-on exercise → open practice time.

If your real setup is different (single full-day bootcamp vs. spread over months, fully
remote/self-paced, larger cohort), the modules below can be compressed or stretched — the
sequence and exercises stay the same either way.

---

## 2. Course structure at a glance

| # | Module | Core skill | Duration |
|---|--------|-----------|----------|
| 0 | Setup & mental model | Install Git, GitHub account, why version control | 60 min (pre-work + session) |
| 1 | Git fundamentals | init, add, commit, status, log, diff, .gitignore | 90 min |
| 2 | Branching & merging | branches, merge, conflicts | 90 min |
| 3 | GitHub basics | remotes, clone, push/pull, README, Markdown | 90 min |
| 4 | Collaboration workflow | Issues, Pull Requests, code review, GitHub Flow | 90 min |
| 5 | Working with open data | real dataset exercise in the practice repo | 90 min |
| 6 | Capstone + stretch topics | small real contribution, optional: Actions, Pages | 90–120 min |

---

## 3. Module details, with learning material

### Module 0 — Setup & Why Version Control

**Concepts:** what version control solves, local vs. remote repos, Git vs. GitHub, the
`git` command line vs. GitHub's web UI.

**Setup checklist (send before session 1):**
- Install Git ([git-scm.com/downloads](https://git-scm.com/downloads))
- Create a GitHub account
- Install VS Code (or your editor of choice) with its built-in Git support
- Configure identity:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```
- Set up SSH key or a Personal Access Token for authentication (GitHub now requires this
  instead of password auth over HTTPS)

**Resources:**
- [Pro Git book](https://git-scm.com/book/en/v2) — free, canonical reference (Ch. 1 for this module)
- [GitHub Docs: Git and GitHub learning resources](https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources) — curated overview of official material
- Video: [Git & GitHub Crash Course for Beginners (2026)](https://www.youtube.com/watch?v=mAFoROnOfHs)

---

### Module 1 — Git Fundamentals (Working Locally)

**Concepts:** repository, working directory / staging area / commit history, the commit
as a snapshot, `.gitignore`.

**Commands covered:** `git init`, `git status`, `git add`, `git commit`, `git log`,
`git diff`, `git restore`.

**Exercise:** each intern initialises a local repo, adds a small text/CSV file, makes 3–4
commits with meaningful messages, and inspects history with `git log --oneline`.

**Resources:**
- [Learn Git Branching](https://learngitbranching.js.org/) — interactive, visual, does the
  "Introduction Sequence" for commits before branching (use this again in Module 2)
- [Scrimba: Command Line Basics](https://scrimba.com/) (free) — useful if terminal itself is unfamiliar
- Video: any chapter-timestamped intro from the crash course linked above covers `add`/`commit`/`status` well

---

### Module 2 — Branching & Merging

**Concepts:** branches as pointers, why branch per feature/task, fast-forward vs. merge
commits, resolving conflicts.

**Commands covered:** `git branch`, `git switch`/`git checkout`, `git merge`, conflict
markers, `git log --oneline --graph --all`.

**Exercise:** two interns pair up, both branch off the same file, make conflicting edits,
merge and resolve the conflict together — conflict resolution "clicks" much faster when
experienced live rather than described.

**Resources:**
- [Learn Git Branching](https://learngitbranching.js.org/) — the "Branching" and "Merging" level sequences are built exactly for this
- [GitHub Skills: Resolve merge conflicts](https://github.com/skills) — official GitHub Skills catalogue includes a dedicated conflict-resolution exercise, worth checking their current catalogue for the exact repo name

---

### Module 3 — GitHub Basics: Remotes, Clone, Push & Pull

**Concepts:** local repo vs. remote (GitHub), `clone` vs `init` + `remote add`, `push`/`pull`,
forking, README files, GitHub-flavoured Markdown.

**Exercise:** each intern clones the ODON practice repository (see §4 below), creates a
personal branch, edits a data file and the README, commits, and pushes their branch to GitHub.

**Resources:**
- [GitHub Skills](https://github.com/skills) — free, official, interactive: "Introduction to GitHub" and "Communicate using Markdown" are the two courses to assign here; taught inside GitHub Issues via GitHub Actions, so interns learn by doing it on real GitHub
- [GitHub Docs: Get Started](https://docs.github.com/en/get-started) — repositories, commits, pull requests, issues, kept current by GitHub itself

---

### Module 4 — Collaboration: Issues, Pull Requests & Code Review

**Concepts:** Issues for tracking work, Pull Requests as the review/discussion unit, the
GitHub Flow (branch → commit → PR → review → merge), requesting and giving reviews.

**Exercise:** each intern opens an Issue describing a small improvement to the practice
repo (e.g. "add a filter for column X"), does the work on a branch, opens a PR referencing
the issue, and another intern reviews and approves it.

**Resources:**
- [GitHub Skills: "Introduction to GitHub"](https://github.com/skills) covers this end-to-end inside real Issues/PRs
- [Understanding the GitHub flow (GitHub Docs)](https://docs.github.com/en/get-started/using-github/github-flow)

---

### Module 5 — Working with Open Data

This is where the course becomes ODON-specific. Interns apply everything so far to a
dataset similar to the ones ODON already publishes (bike share, street safety, mobility data).

**Exercise ideas (pick 1–2):**
- Add a new row/record to a CSV dataset in the practice repo, following the existing schema,
  via the full branch → PR → review flow
- Fix a data quality issue (missing field, inconsistent formatting) and explain the fix in
  the PR description — ties directly into ODON's own ODMM technical-openness criteria (T2 → T3)
- Write a short Markdown data dictionary / README section describing the dataset's fields,
  license, and update frequency (again mirrors ODMM documentation indicators)

**Resources:**
- Reuse ODON's own [Open Data page](https://odon.at/en/open-data/) and ODMM as the framework
  for discussing *why* good structure/documentation matters — connects the Git exercise back
  to something they already know from ODON's mission

---

### Module 6 — Capstone + stretch topics

**Capstone:** each intern makes one real, small contribution to an actual ODON repository
(e.g. a typo fix or content update on the Jekyll website, or a data file in a real project),
through a proper PR that a board member or mentor reviews and merges.

**Stretch topics (optional, for members or interns who want more):**
- Rebasing and cleaning up commit history — [Learn Git Branching](https://learngitbranching.js.org/) "Rebase" sequence
- GitHub Actions basics (relevant since ODON's Google Forms → Sheet workflow could eventually
  be complemented by automation) — [GitHub Skills catalogue](https://github.com/skills)
- GitHub Pages / Jekyll specifics, since that's literally what odon.at runs on —
  [GitHub Docs: GitHub Pages](https://docs.github.com/en/pages)
- [GitHub Copilot Bootcamp](https://github.com/skills) style courses, if AI-assisted coding is of interest later

---

## 4. The practice repository

The dedicated, low-stakes practice repo already exists in the `odon-at` organisation, separate
from production repos, so interns can safely break things:
**[github.com/odon-at/education-github-playground](https://github.com/odon-at/education-github-playground)**.

### 4.1 Repository facts & setup steps

1. **The repo already exists** at `github.com/odon-at/education-github-playground`.
   - Visibility: **private.** Interns ask their mentor to add them as a collaborator before
     they can commit to it — it is not a public artifact.
   - Initialise with a README and a `.gitignore` (choose a general template, e.g. "Python" or "Node" depending on what tools you'll use for any scripts).
   - License: pick an open license (e.g. MIT or CC0 for the data) so it's consistent with ODON's own open-data ethos.

2. **Seed it with real(ish) open data**, ideally something already familiar from ODON's own
   published work, e.g.:
   - A small extract from the *Bike Share & Sustainable Mobility* dataset
   - A trimmed sample from the *Street Safety* dataset
   - Or genuinely public data from Vienna's own open data portal (`data.gv.at`) — small
     enough (a few hundred rows) that diffs are readable and conflicts are easy to create on purpose

   Folder structure suggestion:
   ```
   education-github-playground/
   ├── README.md              ← course intro + how to use this repo
   ├── data/
   │   └── bike-share-mini.csv
   ├── exercises/
   │   ├── 01-first-commit.md
   │   ├── 02-branch-and-merge.md
   │   ├── 03-open-a-pr.md
   │   └── 04-fix-the-data.md
   ├── .github/
   │   ├── ISSUE_TEMPLATE/
   │   │   └── exercise-task.md
   │   └── PULL_REQUEST_TEMPLATE.md
   └── LICENSE
   ```

3. **Write exercise files as Issues, not just docs.** Since GitHub Skills' whole model is
   "teach inside Issues via Actions," you can mirror that: create an Issue template
   (`exercise-task.md`) and open a real Issue per exercise per intern (or let them self-assign
   from a shared backlog). This makes Module 4 (Issues/PRs) feel identical to the earlier modules
   instead of a jump to a new tool.

4. **Protect `main`.** Turn on branch protection (Settings → Branches) requiring at least one
   review before merging into `main`. This forces the PR-review habit from day one rather than
   letting interns push straight to `main`.

5. **Add each intern as a collaborator** (or, better, have them fork the repo if you want to
   also teach the fork + PR-across-repos workflow used for external open-source contributions —
   useful since ODON may eventually take community contributions to its own datasets/API).

6. **Reset between cohorts.** Keep a `template` branch or use GitHub's "template repository"
   setting so you can spin up a fresh copy for each new intern cohort without manually cleaning
   up old branches/PRs.

### 4.2 Making it reusable for members, not just interns

- Mark the repo as a **GitHub template repository** (Settings → "Template repository" toggle),
  so any member with access can click "Use this template" to get their own sandbox copy instantly.
- Publish the module list (this document, trimmed) on the ODON website under Education, since
  the statutes already list "conveying practices in open data processing... to pupils and
  students" and "promoting knowledge... among members" as explicit means (§3) — this course
  satisfies both directly.
- Consider pairing it with ODON's existing internship tracks: this course is a natural
  prerequisite/companion to the "APIs and Data Engineering" and "Data Analysis and Storytelling"
  internship tracks already described on the website.

---

## 5. Suggested schedule (6 weeks, 90 min/session)

| Week | Module | Homework before next session |
|------|--------|-------------------------------|
| 1 | 0 + 1: Setup, fundamentals | Do 2 more `Learn Git Branching` intro levels |
| 2 | 2: Branching & merging | Finish `Learn Git Branching` branching levels |
| 3 | 3: GitHub basics | Complete GitHub Skills "Introduction to GitHub" |
| 4 | 4: Issues & PRs | Complete GitHub Skills "Communicate using Markdown" |
| 5 | 5: Open data exercise | Draft their capstone PR |
| 6 | 6: Capstone review + stretch topics | — |

---

## 6. Quick resource list (all in one place)

- [Pro Git book](https://git-scm.com/book/en/v2) — free reference
- [Learn Git Branching](https://learngitbranching.js.org/) — interactive visual tool, best single resource for branching/merging/rebasing
- [GitHub Skills](https://github.com/skills) — free, official, hands-on courses taught inside real Issues/Actions/PRs
- [GitHub Docs: Get Started](https://docs.github.com/en/get-started) — official docs, always current
- [GitHub Docs: Git and GitHub learning resources](https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources) — GitHub's own curated list, good as a fallback/refresher page
- Video: [Git & GitHub Crash Course for Beginners (2026)](https://www.youtube.com/watch?v=mAFoROnOfHs)
- ODON's own [Open Data page & ODMM](https://odon.at/en/open-data/) — for tying Module 5 back to ODON's mission

---

*Suggested next step: I can turn this into a Word or PDF handout, or scaffold the actual
`education-github-playground` repo structure (README, exercise files, issue templates) as ready-to-upload files — just say which.*
