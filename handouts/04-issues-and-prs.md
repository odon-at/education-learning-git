# Learning Git With Open Data
### Module 4 — Collaboration: Issues, Pull Requests & Code Review

You can now branch, commit, push, and pull. In this module the pieces come together into
the workflow real teams use every day: describing work in **Issues**, proposing changes
in **Pull Requests**, and improving each other's work through **code review**. This is
exactly how contributions to ODON's website, datasets, and tools are made.

---

## 1. Core concepts

An **Issue** is a tracked unit of work: a bug report, a task, an idea, a question. Issues
live on GitHub (not in Git) and give every piece of work a number, a discussion thread,
and a status (open/closed). Good issues describe *what* and *why* — the *how* is worked
out in the pull request.

A **Pull Request (PR)** says: "here is a branch with my changes — please review and merge
it." A PR is much more than a merge button: it shows the full diff, hosts a discussion,
collects review feedback, and documents forever *why* a change was made. PRs are the
heart of collaboration on GitHub.

**Code review** is reading someone else's proposed change and giving feedback before it's
merged. It catches mistakes, spreads knowledge through the team, and keeps quality high.
Review culture matters: comments address the *work*, not the *person* — and "looks good
to me" (LGTM) plus an approval is a perfectly good review for a solid change.

The **GitHub Flow** ties it all together:

1. Pick or open an **Issue** describing the work
2. Create a **branch** for it
3. **Commit** your changes
4. Open a **Pull Request** (linking the issue)
5. **Review** — discuss, improve, push more commits if needed
6. **Merge** into `main`, delete the branch, the issue closes

Small, frequent PRs beat huge ones: they're easier to review, faster to merge, and less
likely to conflict.

## 2. Hands-on exercise

Work in the ODON practice repository. Each person completes the full loop once as
*author* and once as *reviewer*.

### Step 1 — Open an Issue

On github.com, go to the practice repo → **Issues** → **New issue**. Describe a small,
concrete improvement, for example:

> **Title:** Add a short description to the bike-share dataset section
> **Body:** The README lists the dataset but doesn't explain the columns. Add 1–2
> sentences describing what the data contains and where it comes from.

Note the issue number GitHub assigns (e.g. `#12`).

### Step 2 — Branch and do the work

```bash
git switch main
git pull
git switch -c yourname/issue-12-dataset-description
```

Make the change, then commit — mentioning the issue number connects the commit to the
issue:

```bash
git add README.md
git commit -m "Add dataset description to README (#12)"
git push -u origin yourname/issue-12-dataset-description
```

### Step 3 — Open the Pull Request

After pushing, GitHub shows a "Compare & pull request" button — click it (or go to
**Pull requests** → **New pull request**). Fill in:

- **Title:** short summary of the change
- **Description:** what you changed and why. Include the line `Closes #12` — this links
  the PR to the issue *and* auto-closes the issue when the PR is merged.
- **Reviewer:** select your training partner on the right side

### Step 4 — Review your partner's PR

You'll receive a review request for your partner's PR. Open it and go to **Files
changed**:

- Read the diff. Hover over a line and click the **+** to leave a comment on that
  specific line.
- Ask at least one genuine question or make one suggestion (e.g. wording, a typo, a
  clarification).
- Finish via **Review changes**: choose **Comment** (feedback only), **Approve** (good
  to merge), or **Request changes** (needs work before merging).

### Step 5 — Respond to review and update the PR

Back on your own PR: reply to comments, and make any agreed changes locally:

```bash
git add README.md
git commit -m "Clarify data source in description"
git push
```

The new commit appears in the PR automatically — no new PR needed. This
push-more-commits loop *is* the review process.

### Step 6 — Merge and clean up

Once approved, click **Merge pull request** (the default "merge commit" option is fine
for now) → **Confirm**. Then click **Delete branch**. Check that your issue closed
automatically. Finally, update your local `main`:

```bash
git switch main
git pull
```

The loop is complete: Issue → Branch → PR → Review → Merge. This is the rhythm of all
collaborative work at ODON.

## 3. What makes a good PR (and a good review)

**As an author:**

- Keep PRs small and focused — one issue, one PR
- Write a description a teammate can understand without asking you
- Link the issue (`Closes #N`), respond to every comment
- Never take review feedback personally — it's about the change, not you

**As a reviewer:**

- Be timely — a PR waiting days blocks your teammate
- Be specific: point to lines, suggest concrete alternatives
- Be kind and assume good intent; praise what's good, too
- Approve when it's good *enough* — perfect is not the bar

## 4. Resources for this module

| Resource | Link |
|---|---|
| GitHub Skills — "Review pull requests" (interactive) | [github.com/skills](https://github.com/skills) |
| GitHub Docs — Understanding the GitHub flow | [docs.github.com/en/get-started/using-github/github-flow](https://docs.github.com/en/get-started/using-github/github-flow) |
| GitHub Docs — About pull requests | [docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) |
| GitHub Docs — Linking a PR to an issue | [docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue) |
| Google's code review guidelines (advanced reading) | [google.github.io/eng-practices/review/](https://google.github.io/eng-practices/review/) |

## 5. Before Session 5 — final checklist

- [ ] I opened an Issue with a clear title and description
- [ ] I created a branch for the issue and pushed my commits
- [ ] I opened a Pull Request with a description and `Closes #N`
- [ ] I requested a review and responded to review comments
- [ ] I reviewed someone else's PR and left at least one line comment
- [ ] I updated a PR by pushing additional commits
- [ ] I merged a PR, deleted the branch, and saw the issue close automatically
- [ ] I can describe the six steps of the GitHub Flow from memory

Questions before the session? Reach out any time at info@odon.at.

---

**Contact:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Module 4 Handout*

<br>

---
---

<br>

# Learning Git With Open Data
### Modul 4 — Zusammenarbeit: Issues, Pull Requests & Code Review

Du kannst jetzt branchen, committen, pushen und pullen. In diesem Modul fügen sich die
Teile zu dem Workflow zusammen, den echte Teams täglich nutzen: Arbeit in **Issues**
beschreiben, Änderungen in **Pull Requests** vorschlagen und die Arbeit der anderen durch
**Code Review** verbessern. Genau so entstehen Beiträge zu ODONs Website, Datensätzen und
Tools.

---

## 1. Grundlegende Konzepte

Ein **Issue** ist eine nachverfolgte Arbeitseinheit: ein Fehlerbericht, eine Aufgabe,
eine Idee, eine Frage. Issues leben auf GitHub (nicht in Git) und geben jeder Arbeit eine
Nummer, einen Diskussionsverlauf und einen Status (offen/geschlossen). Gute Issues
beschreiben das *Was* und *Warum* — das *Wie* wird im Pull Request ausgearbeitet.

Ein **Pull Request (PR)** sagt: "Hier ist ein Branch mit meinen Änderungen — bitte prüfen
und mergen." Ein PR ist viel mehr als ein Merge-Knopf: Er zeigt den vollständigen Diff,
beherbergt eine Diskussion, sammelt Review-Feedback und dokumentiert für immer, *warum*
eine Änderung gemacht wurde. PRs sind das Herz der Zusammenarbeit auf GitHub.

**Code Review** bedeutet, die vorgeschlagene Änderung von jemand anderem zu lesen und
Feedback zu geben, bevor sie gemerged wird. Das fängt Fehler ab, verteilt Wissen im Team
und hält die Qualität hoch. Die Review-Kultur ist wichtig: Kommentare beziehen sich auf
die *Arbeit*, nicht auf die *Person* — und "sieht gut aus" (LGTM) plus eine Freigabe ist
ein völlig legitimes Review für eine solide Änderung.

Der **GitHub Flow** verbindet alles:

1. Ein **Issue** auswählen oder eröffnen, das die Arbeit beschreibt
2. Einen **Branch** dafür erstellen
3. Änderungen **committen**
4. Einen **Pull Request** eröffnen (mit Verweis auf das Issue)
5. **Review** — diskutieren, verbessern, bei Bedarf weitere Commits pushen
6. In `main` **mergen**, Branch löschen, das Issue schließt sich

Kleine, häufige PRs schlagen riesige: Sie sind leichter zu reviewen, schneller gemerged
und geraten seltener in Konflikte.

## 2. Praktische Übung

Arbeite im ODON-Übungs-Repository. Jede:r durchläuft die komplette Schleife einmal als
*Autor:in* und einmal als *Reviewer:in*.

### Schritt 1 — Issue eröffnen

Gehe auf github.com im Übungs-Repo zu **Issues** → **New issue**. Beschreibe eine
kleine, konkrete Verbesserung, zum Beispiel:

> **Titel:** Kurzbeschreibung zum Bike-Share-Datensatz ergänzen
> **Text:** Die README listet den Datensatz auf, erklärt aber die Spalten nicht. Ergänze
> 1–2 Sätze dazu, was die Daten enthalten und woher sie stammen.

Merke dir die Issue-Nummer, die GitHub vergibt (z. B. `#12`).

### Schritt 2 — Branchen und die Arbeit machen

```bash
git switch main
git pull
git switch -c deinname/issue-12-datensatz-beschreibung
```

Mache die Änderung und committe — die Erwähnung der Issue-Nummer verbindet den Commit
mit dem Issue:

```bash
git add README.md
git commit -m "Datensatzbeschreibung zur README ergänzt (#12)"
git push -u origin deinname/issue-12-datensatz-beschreibung
```

### Schritt 3 — Pull Request eröffnen

Nach dem Push zeigt GitHub einen Button "Compare & pull request" — klicke ihn (oder gehe
zu **Pull requests** → **New pull request**). Fülle aus:

- **Titel:** kurze Zusammenfassung der Änderung
- **Beschreibung:** was du geändert hast und warum. Füge die Zeile `Closes #12` ein —
  das verknüpft den PR mit dem Issue *und* schließt das Issue automatisch beim Merge.
- **Reviewer:** wähle rechts deine:n Übungspartner:in aus

### Schritt 4 — Den PR deines Partners/deiner Partnerin reviewen

Du bekommst eine Review-Anfrage für den PR deines Gegenübers. Öffne ihn und gehe zu
**Files changed**:

- Lies den Diff. Fahre über eine Zeile und klicke das **+**, um einen Kommentar zu
  genau dieser Zeile zu hinterlassen.
- Stelle mindestens eine echte Frage oder mache einen Vorschlag (z. B. Formulierung,
  Tippfehler, Klarstellung).
- Schließe über **Review changes** ab: wähle **Comment** (nur Feedback), **Approve**
  (bereit zum Mergen) oder **Request changes** (braucht Überarbeitung vor dem Merge).

### Schritt 5 — Auf das Review reagieren und den PR aktualisieren

Zurück auf deinem eigenen PR: Antworte auf Kommentare und setze vereinbarte Änderungen
lokal um:

```bash
git add README.md
git commit -m "Datenquelle in der Beschreibung präzisiert"
git push
```

Der neue Commit erscheint automatisch im PR — kein neuer PR nötig. Diese Schleife aus
weiteren Commits *ist* der Review-Prozess.

### Schritt 6 — Mergen und aufräumen

Nach der Freigabe klicke **Merge pull request** (die Standardoption "merge commit" ist
für den Anfang gut) → **Confirm**. Dann **Delete branch**. Prüfe, dass sich dein Issue
automatisch geschlossen hat. Aktualisiere zum Schluss dein lokales `main`:

```bash
git switch main
git pull
```

Die Schleife ist komplett: Issue → Branch → PR → Review → Merge. Das ist der Rhythmus
aller gemeinsamen Arbeit bei ODON.

## 3. Was einen guten PR (und ein gutes Review) ausmacht

**Als Autor:in:**

- Halte PRs klein und fokussiert — ein Issue, ein PR
- Schreibe eine Beschreibung, die Teamkolleg:innen ohne Rückfragen verstehen
- Verlinke das Issue (`Closes #N`), antworte auf jeden Kommentar
- Nimm Review-Feedback nie persönlich — es geht um die Änderung, nicht um dich

**Als Reviewer:in:**

- Sei zeitnah — ein tagelang wartender PR blockiert dein Gegenüber
- Sei konkret: verweise auf Zeilen, schlage konkrete Alternativen vor
- Sei freundlich und unterstelle gute Absicht; lobe auch, was gut ist
- Gib frei, wenn es gut *genug* ist — Perfektion ist nicht der Maßstab

## 4. Ressourcen für dieses Modul

| Ressource | Link |
|---|---|
| GitHub Skills — "Review pull requests" (interaktiv) | [github.com/skills](https://github.com/skills) |
| GitHub Docs — Den GitHub Flow verstehen | [docs.github.com/en/get-started/using-github/github-flow](https://docs.github.com/en/get-started/using-github/github-flow) |
| GitHub Docs — Über Pull Requests | [docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) |
| GitHub Docs — Einen PR mit einem Issue verknüpfen | [docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue) |
| Googles Code-Review-Richtlinien (weiterführend) | [google.github.io/eng-practices/review/](https://google.github.io/eng-practices/review/) |

## 5. Vor Sitzung 5 — Abschluss-Checkliste

- [ ] Ich habe ein Issue mit klarem Titel und klarer Beschreibung eröffnet
- [ ] Ich habe einen Branch für das Issue erstellt und meine Commits gepusht
- [ ] Ich habe einen Pull Request mit Beschreibung und `Closes #N` eröffnet
- [ ] Ich habe ein Review angefragt und auf Review-Kommentare reagiert
- [ ] Ich habe den PR von jemand anderem reviewt und mindestens einen Zeilenkommentar hinterlassen
- [ ] Ich habe einen PR durch zusätzliche Commits aktualisiert
- [ ] Ich habe einen PR gemerged, den Branch gelöscht und gesehen, wie sich das Issue automatisch schließt
- [ ] Ich kann die sechs Schritte des GitHub Flow aus dem Gedächtnis beschreiben

Fragen vor der Sitzung? Melde dich jederzeit unter info@odon.at.

---

**Kontakt:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Modul 4 Handout*
