# Learning Git With Open Data
### Module 1 — Git Fundamentals (Working Locally)

In Module 0 you set up Git and GitHub. In this module you'll use Git for real: creating a
repository, saving snapshots of your work, and understanding the three-stage model that
everything else in Git builds on.

---

## 1. Core concepts

A **repository** ("repo") is just a project folder that Git is watching. Inside it, Git
thinks in three stages:

- **Working directory** — the files as you see and edit them normally.
- **Staging area (the "index")** — a holding area where you pick exactly which changes
  you want to include in your next snapshot.
- **Commit history** — the permanent, saved snapshots you've taken over time.

A **commit** is a snapshot of the whole project at a point in time, with a message
explaining what changed and why — not just a list of edits. Good commit messages matter:
"fix typo in README" is far more useful later than "update".

A **`.gitignore`** file tells Git which files to never track (e.g. temporary files,
credentials, downloaded data caches) — important once you start working with data files
and API tokens at ODON.

## 2. Hands-on exercise

Work through these steps in order. Use the terminal inside VS Code, or your regular
terminal.

### Step 1 — Create and initialize a repository

```bash
mkdir git-practice
cd git-practice
git init
```

`git init` turns the folder into a Git repository (it creates a hidden `.git` folder that
stores all history — don't touch it directly).

### Step 2 — Check the status

```bash
git status
```

Run this often — it tells you what's changed, what's staged, and what Git is currently
tracking. Right now it should say the working directory is clean (empty repo, no files yet).

### Step 3 — Create a file and stage it

```bash
echo "# My practice notes" > notes.md
git add notes.md
```

`git add` moves a change from the working directory into the staging area — you're
saying "include this in my next commit."

### Step 4 — Make your first commit

```bash
git commit -m "Add initial notes file"
```

This saves a permanent snapshot including everything currently staged.

### Step 5 — Edit the file and see the diff

Add a line to `notes.md`, then run:

```bash
git diff
```

This shows exactly what changed in the working directory compared to the last commit —
line by line. Stage and commit the change:

```bash
git add notes.md
git commit -m "Add a second line to notes"
```

### Step 6 — Ignore files you don't want tracked

Create a `.gitignore` file:

```bash
echo "*.log" > .gitignore
echo ".DS_Store" >> .gitignore
git add .gitignore
git commit -m "Add .gitignore"
```

Anything matching a pattern in `.gitignore` will no longer show up in `git status`, even
if it exists in the folder.

### Step 7 — Review your history

```bash
git log --oneline
```

You should see your three commits listed, newest first. Try `git log` (without
`--oneline`) to see full commit details — author, date, and message.

## 3. Resources for this module

| Resource | Link |
|---|---|
| Learn Git Branching — "Introduction Sequence" (interactive) | [learngitbranching.js.org](https://learngitbranching.js.org/) |
| Pro Git book, Ch. 2 — Git Basics | [git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository) |
| GitHub Docs — "Git and GitHub learning resources" | [docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources](https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources) |
| gitignore.io — generate `.gitignore` templates | [www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore) |

## 4. Before Session 2 — final checklist

- [ ] I can initialize a new repository with `git init`
- [ ] I can stage changes with `git add` and commit them with `git commit`
- [ ] I understand the difference between the working directory, staging area, and commit history
- [ ] I can view project history with `git log`
- [ ] I can see uncommitted changes with `git diff`
- [ ] I know what `.gitignore` does and created one
- [ ] I can explain, in my own words, the difference between `git status`, `git diff`, and `git log`

Questions before the session? Reach out any time at info@odon.at.

---

**Contact:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Module 1 Handout*

<br>

---
---

<br>

# Learning Git With Open Data
### Modul 1 — Git-Grundlagen (Lokal arbeiten)

In Modul 0 hast du Git und GitHub eingerichtet. In diesem Modul nutzt du Git wirklich:
Du erstellst ein Repository, speicherst Schnappschüsse deiner Arbeit und verstehst das
Drei-Stufen-Modell, auf dem alles Weitere in Git aufbaut.

---

## 1. Grundlegende Konzepte

Ein **Repository** ("Repo") ist einfach ein Projektordner, den Git überwacht. Git denkt
dabei in drei Stufen:

- **Arbeitsverzeichnis (Working Directory)** — die Dateien, wie du sie normal siehst und bearbeitest.
- **Staging-Bereich (der "Index")** — ein Zwischenbereich, in dem du genau auswählst,
  welche Änderungen in deinen nächsten Schnappschuss einfließen sollen.
- **Commit-Verlauf** — die dauerhaft gespeicherten Schnappschüsse, die du im Zeitverlauf
  erstellt hast.

Ein **Commit** ist ein Schnappschuss des gesamten Projekts zu einem bestimmten Zeitpunkt,
mit einer Nachricht, die erklärt, was sich geändert hat und warum — nicht nur eine Liste
von Bearbeitungen. Gute Commit-Nachrichten sind wichtig: "Tippfehler in README behoben" ist
später deutlich nützlicher als "Update".

Eine **`.gitignore`**-Datei sagt Git, welche Dateien niemals verfolgt werden sollen (z. B.
temporäre Dateien, Zugangsdaten, heruntergeladene Daten-Caches) — wichtig, sobald du bei
ODON mit Datendateien und API-Tokens arbeitest.

## 2. Praktische Übung

Arbeite die folgenden Schritte in dieser Reihenfolge durch. Nutze das Terminal in VS Code
oder dein normales Terminal.

### Schritt 1 — Repository erstellen und initialisieren

```bash
mkdir git-practice
cd git-practice
git init
```

`git init` macht aus dem Ordner ein Git-Repository (es erzeugt einen versteckten
`.git`-Ordner, der den gesamten Verlauf speichert — diesen nicht direkt bearbeiten).

### Schritt 2 — Status prüfen

```bash
git status
```

Führe das häufig aus — es zeigt dir, was geändert wurde, was gestaged ist und was Git
aktuell verfolgt. Aktuell sollte es ein leeres, "sauberes" Repository ohne Dateien anzeigen.

### Schritt 3 — Datei erstellen und stagen

```bash
echo "# Meine Übungsnotizen" > notes.md
git add notes.md
```

`git add` verschiebt eine Änderung vom Arbeitsverzeichnis in den Staging-Bereich — du
sagst damit: "Diese Änderung soll in meinen nächsten Commit."

### Schritt 4 — Ersten Commit erstellen

```bash
git commit -m "Notizdatei hinzugefügt"
```

Damit wird ein dauerhafter Schnappschuss aller aktuell gestagten Änderungen gespeichert.

### Schritt 5 — Datei bearbeiten und den Unterschied ansehen

Füge eine Zeile zu `notes.md` hinzu und führe dann aus:

```bash
git diff
```

Das zeigt genau, was sich im Arbeitsverzeichnis im Vergleich zum letzten Commit geändert
hat — Zeile für Zeile. Änderung stagen und committen:

```bash
git add notes.md
git commit -m "Zweite Zeile zu Notizen hinzugefügt"
```

### Schritt 6 — Dateien ignorieren, die nicht verfolgt werden sollen

Erstelle eine `.gitignore`-Datei:

```bash
echo "*.log" > .gitignore
echo ".DS_Store" >> .gitignore
git add .gitignore
git commit -m ".gitignore hinzugefügt"
```

Alles, was einem Muster in `.gitignore` entspricht, taucht nicht mehr in `git status` auf
— selbst wenn es im Ordner existiert.

### Schritt 7 — Verlauf ansehen

```bash
git log --oneline
```

Du solltest deine drei Commits sehen, neueste zuerst. Probiere auch `git log` (ohne
`--oneline`) für vollständige Commit-Details — Autor, Datum und Nachricht.

## 3. Ressourcen für dieses Modul

| Ressource | Link |
|---|---|
| Learn Git Branching — "Introduction Sequence" (interaktiv) | [learngitbranching.js.org](https://learngitbranching.js.org/) |
| Pro Git Buch, Kap. 2 — Git-Grundlagen | [git-scm.com/book/de/v2/Erste-Schritte-Ein-Repository-anlegen](https://git-scm.com/book/de/v2/Erste-Schritte-Ein-Repository-anlegen) |
| GitHub Docs — "Git and GitHub learning resources" | [docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources](https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources) |
| gitignore.io — Vorlagen für `.gitignore` generieren | [www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore) |

## 4. Vor Sitzung 2 — Abschluss-Checkliste

- [ ] Ich kann ein neues Repository mit `git init` erstellen
- [ ] Ich kann Änderungen mit `git add` stagen und mit `git commit` committen
- [ ] Ich verstehe den Unterschied zwischen Arbeitsverzeichnis, Staging-Bereich und Commit-Verlauf
- [ ] Ich kann den Projektverlauf mit `git log` ansehen
- [ ] Ich kann nicht committete Änderungen mit `git diff` ansehen
- [ ] Ich weiß, was `.gitignore` bewirkt, und habe eine erstellt
- [ ] Ich kann in eigenen Worten den Unterschied zwischen `git status`, `git diff` und `git log` erklären

Fragen vor der Sitzung? Melde dich jederzeit unter info@odon.at.

---

**Kontakt:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Modul 1 Handout*
