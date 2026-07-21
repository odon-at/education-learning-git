# Learning Git With Open Data
### Module 3 — GitHub Basics: Remotes, Clone, Push & Pull

So far everything happened on your own computer. In this module your local Git meets
GitHub: you'll connect a local repository to a **remote**, get a copy of ODON's practice
repository with **clone**, and exchange work with **push** and **pull**. From here on,
your work becomes visible to — and shareable with — the rest of the team.

---

## 1. Core concepts

A **remote** is a copy of your repository hosted somewhere else — for us, on GitHub. Your
local repo and the remote are linked but independent: they only synchronize when you
explicitly tell them to. The default remote is conventionally named **`origin`**.

The four commands that move work around:

- **`git clone <url>`** — copy an existing remote repository to your computer (including
  its full history). This is how you'll start working on any existing ODON project.
- **`git push`** — upload your local commits to the remote.
- **`git fetch`** — download new commits from the remote *without* changing your files.
- **`git pull`** — download new commits *and* merge them into your current branch
  (effectively `fetch` + `merge`).

A **fork** is your own copy of *someone else's* repository on GitHub — used when you
don't have write access to the original (typical for open-source contributions). Inside
ODON's own organisation you usually won't need forks; you'll work on branches in the
shared repo instead.

A **README.md** is the front page of every repository — written in **Markdown**, a
lightweight formatting syntax (`# heading`, `**bold**`, `- list item`, `` `code` ``).
GitHub renders it automatically. Every serious repo has one; for open-data repos it's
where the data documentation lives.

## 2. Hands-on exercise

For this module you need the URL of ODON's practice repository —
[`https://github.com/odon-at/education-github-playground`](https://github.com/odon-at/education-github-playground)
— and your GitHub account added as a collaborator (it's a private repo; ask your mentor to
add you).

### Step 1 — Clone the practice repository

```bash
git clone https://github.com/odon-at/education-github-playground.git
cd education-github-playground
```

You now have the complete repository — all files and full history. Check with
`git log --oneline`.

### Step 2 — Inspect the remote

```bash
git remote -v
```

You'll see `origin` listed with the GitHub URL, for both fetch and push. Cloning set this
up automatically.

### Step 3 — Create your personal branch

Never work directly on `main` in a shared repo. Create a branch named after yourself:

```bash
git switch -c yourname/first-steps
```

The `yourname/` prefix is a common convention that keeps everyone's branches organized
and avoids name collisions.

### Step 4 — Make a change and commit it

Open the repo's `README.md` (or the file your mentor points you to) and add one line —
for example, add your name to a participant list. Then:

```bash
git add README.md
git commit -m "Add <your name> to participants list"
```

### Step 5 — Push your branch to GitHub

```bash
git push -u origin yourname/first-steps
```

`-u` links your local branch to the remote branch, so future pushes are just `git push`.
Now open the repository on github.com — your branch is there, visible to the whole team.

### Step 6 — Experience pull

Ask your training partner (or mentor) to push a small change to `main`. Then fetch and
inspect it before merging:

```bash
git fetch
git log --oneline main..origin/main
```

This shows commits that exist on the remote but not locally. Now bring them in:

```bash
git switch main
git pull
```

**Habit to build:** run `git pull` on `main` at the start of every working session, so
you always build on the latest state.

### Step 7 — Explore the GitHub web interface

On github.com, find in the practice repo:

1. The **commit history** (Commits tab) — click a commit to see its diff
2. Your **branch** in the branch dropdown
3. The rendered **README.md** on the repo front page
4. The **blame view** of a file (Blame button) — shows who last changed each line

These views answer most "who changed what, when, and why?" questions without any command
line.

## 3. Common pitfalls

- **`git push` rejected ("fetch first")?** Someone pushed before you. Run `git pull`,
  resolve any conflict (Module 2!), then push again.
- **Committed on `main` by accident?** It happens. Tell your mentor — it's fixable, and
  it's exactly what the training repo is for.
- **HTTPS asks for a password?** Use your Personal Access Token instead (Module 0), or
  switch to the SSH URL (`git@github.com:odon-at/...`).

## 4. Resources for this module

| Resource | Link |
|---|---|
| GitHub Skills — "Introduction to GitHub" (interactive, do this one) | [github.com/skills](https://github.com/skills) |
| GitHub Skills — "Communicate using Markdown" | [github.com/skills](https://github.com/skills) |
| GitHub Docs — About remote repositories | [docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories) |
| Markdown reference (GitHub-flavored) | [docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) |
| Pro Git book, Ch. 2.5 — Working with Remotes | [git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes) |

## 5. Before Session 4 — final checklist

- [ ] I cloned the ODON practice repository to my computer
- [ ] I understand what a remote is and what `origin` refers to
- [ ] I created a personal branch (`yourname/...`) and pushed it to GitHub
- [ ] I can see my branch and commits on github.com
- [ ] I know the difference between `git fetch` and `git pull`
- [ ] I pulled changes made by someone else into my local `main`
- [ ] I can write basic Markdown (headings, bold, lists, code)
- [ ] I completed the GitHub Skills course "Introduction to GitHub"

Questions before the session? Reach out any time at info@odon.at.

---

**Contact:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Module 3 Handout*

<br>

---
---

<br>

# Learning Git With Open Data
### Modul 3 — GitHub-Grundlagen: Remotes, Clone, Push & Pull

Bisher ist alles auf deinem eigenen Computer passiert. In diesem Modul trifft dein
lokales Git auf GitHub: Du verbindest ein lokales Repository mit einem **Remote**, holst
dir mit **clone** eine Kopie von ODONs Übungs-Repository und tauschst Arbeit mit **push**
und **pull** aus. Ab jetzt wird deine Arbeit für das restliche Team sichtbar — und teilbar.

---

## 1. Grundlegende Konzepte

Ein **Remote** ist eine Kopie deines Repositories, die woanders gehostet wird — bei uns
auf GitHub. Dein lokales Repo und das Remote sind verbunden, aber unabhängig: Sie
synchronisieren sich nur, wenn du es ausdrücklich anstößt. Das Standard-Remote heißt per
Konvention **`origin`**.

Die vier Befehle, die Arbeit hin- und herbewegen:

- **`git clone <url>`** — kopiert ein bestehendes Remote-Repository auf deinen Computer
  (inklusive vollständigem Verlauf). So startest du die Arbeit an jedem bestehenden
  ODON-Projekt.
- **`git push`** — lädt deine lokalen Commits zum Remote hoch.
- **`git fetch`** — lädt neue Commits vom Remote herunter, *ohne* deine Dateien zu ändern.
- **`git pull`** — lädt neue Commits herunter *und* merged sie in deinen aktuellen Branch
  (praktisch `fetch` + `merge`).

Ein **Fork** ist deine eigene Kopie *eines fremden* Repositories auf GitHub — genutzt,
wenn du keinen Schreibzugriff auf das Original hast (typisch für
Open-Source-Beiträge). Innerhalb von ODONs eigener Organisation brauchst du
üblicherweise keine Forks; du arbeitest stattdessen auf Branches im gemeinsamen Repo.

Eine **README.md** ist die Startseite jedes Repositories — geschrieben in **Markdown**,
einer leichtgewichtigen Formatierungssyntax (`# Überschrift`, `**fett**`,
`- Listenpunkt`, `` `Code` ``). GitHub rendert sie automatisch. Jedes ernsthafte Repo hat
eine; bei Open-Data-Repos lebt dort die Datendokumentation.

## 2. Praktische Übung

Für dieses Modul brauchst du die URL von ODONs Übungs-Repository —
[`https://github.com/odon-at/education-github-playground`](https://github.com/odon-at/education-github-playground)
— und dein GitHub-Konto muss als Collaborator hinzugefügt sein (es ist ein privates Repo;
bitte deine Mentorin/deinen Mentor, dich hinzuzufügen).

### Schritt 1 — Übungs-Repository klonen

```bash
git clone https://github.com/odon-at/education-github-playground.git
cd education-github-playground
```

Du hast jetzt das vollständige Repository — alle Dateien und den kompletten Verlauf.
Prüfe mit `git log --oneline`.

### Schritt 2 — Remote inspizieren

```bash
git remote -v
```

Du siehst `origin` mit der GitHub-URL, jeweils für fetch und push. Das Klonen hat das
automatisch eingerichtet.

### Schritt 3 — Persönlichen Branch erstellen

Arbeite in einem gemeinsamen Repo nie direkt auf `main`. Erstelle einen Branch mit
deinem Namen:

```bash
git switch -c deinname/first-steps
```

Das Präfix `deinname/` ist eine gängige Konvention, die die Branches aller Beteiligten
organisiert hält und Namenskollisionen vermeidet.

### Schritt 4 — Änderung machen und committen

Öffne die `README.md` des Repos (oder die Datei, auf die deine Mentorin/dein Mentor
verweist) und füge eine Zeile hinzu — trage dich z. B. in eine Teilnehmerliste ein. Dann:

```bash
git add README.md
git commit -m "<Dein Name> zur Teilnehmerliste hinzugefügt"
```

### Schritt 5 — Branch zu GitHub pushen

```bash
git push -u origin deinname/first-steps
```

`-u` verknüpft deinen lokalen Branch mit dem Remote-Branch, sodass künftige Pushes nur
noch `git push` sind. Öffne jetzt das Repository auf github.com — dein Branch ist da,
sichtbar für das ganze Team.

### Schritt 6 — Pull erleben

Bitte deine:n Übungspartner:in (oder Mentor:in), eine kleine Änderung auf `main` zu
pushen. Dann hole und inspiziere sie, bevor du mergst:

```bash
git fetch
git log --oneline main..origin/main
```

Das zeigt Commits, die auf dem Remote existieren, aber lokal noch nicht. Jetzt hole sie
herein:

```bash
git switch main
git pull
```

**Gewohnheit aufbauen:** Führe zu Beginn jeder Arbeitssitzung `git pull` auf `main`
aus, damit du immer auf dem neuesten Stand aufbaust.

### Schritt 7 — GitHub-Weboberfläche erkunden

Finde auf github.com im Übungs-Repo:

1. Den **Commit-Verlauf** (Commits-Tab) — klicke einen Commit an, um seinen Diff zu sehen
2. Deinen **Branch** im Branch-Dropdown
3. Die gerenderte **README.md** auf der Repo-Startseite
4. Die **Blame-Ansicht** einer Datei (Blame-Button) — zeigt, wer jede Zeile zuletzt
   geändert hat

Diese Ansichten beantworten die meisten Fragen nach "Wer hat was wann und warum
geändert?" ganz ohne Kommandozeile.

## 3. Häufige Stolperfallen

- **`git push` abgelehnt ("fetch first")?** Jemand hat vor dir gepusht. Führe `git pull`
  aus, löse ggf. den Konflikt (Modul 2!) und pushe erneut.
- **Aus Versehen auf `main` committet?** Passiert. Sag deiner Mentorin/deinem Mentor
  Bescheid — es ist reparierbar, und genau dafür ist das Übungs-Repo da.
- **HTTPS fragt nach einem Passwort?** Verwende stattdessen dein Personal Access Token
  (Modul 0) oder wechsle zur SSH-URL (`git@github.com:odon-at/...`).

## 4. Ressourcen für dieses Modul

| Ressource | Link |
|---|---|
| GitHub Skills — "Introduction to GitHub" (interaktiv, unbedingt machen) | [github.com/skills](https://github.com/skills) |
| GitHub Skills — "Communicate using Markdown" | [github.com/skills](https://github.com/skills) |
| GitHub Docs — Über Remote-Repositories | [docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories) |
| Markdown-Referenz (GitHub-flavored) | [docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) |
| Pro Git Buch, Kap. 2.5 — Mit Remotes arbeiten | [git-scm.com/book/de/v2/Git-Grundlagen-Mit-Remotes-arbeiten](https://git-scm.com/book/de/v2/Git-Grundlagen-Mit-Remotes-arbeiten) |

## 5. Vor Sitzung 4 — Abschluss-Checkliste

- [ ] Ich habe das ODON-Übungs-Repository auf meinen Computer geklont
- [ ] Ich verstehe, was ein Remote ist und wofür `origin` steht
- [ ] Ich habe einen persönlichen Branch (`deinname/...`) erstellt und zu GitHub gepusht
- [ ] Ich sehe meinen Branch und meine Commits auf github.com
- [ ] Ich kenne den Unterschied zwischen `git fetch` und `git pull`
- [ ] Ich habe Änderungen von jemand anderem in mein lokales `main` gepullt
- [ ] Ich kann grundlegendes Markdown schreiben (Überschriften, fett, Listen, Code)
- [ ] Ich habe den GitHub-Skills-Kurs "Introduction to GitHub" abgeschlossen

Fragen vor der Sitzung? Melde dich jederzeit unter info@odon.at.

---

**Kontakt:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Modul 3 Handout*
