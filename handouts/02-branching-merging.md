# Learning Git With Open Data
### Module 2 — Branching & Merging

In Module 1 you learned to save snapshots of your work with commits. In this module you'll
learn Git's superpower: **branches** — working on multiple versions of a project in
parallel, and merging them back together safely. This is the foundation of how teams (and
ODON) collaborate without stepping on each other's work.

---

## 1. Core concepts

A **branch** is a movable pointer to a commit. When you create a branch, you're not
copying files — you're just creating a new label that lets you build a separate line of
history. This makes branches in Git extremely cheap and fast, and it's why branching per
task is the normal workflow, not an exception.

The default branch is usually called **`main`**. The convention: `main` always contains
working, reviewed content; new work happens on **feature branches** (e.g.
`add-bike-data`, `fix-readme-typo`) and is merged back into `main` when ready.

**Merging** combines the history of two branches. Two cases:

- **Fast-forward merge:** if `main` hasn't changed since you branched off, Git simply
  moves the `main` pointer forward. No new commit is needed.
- **Merge commit:** if both branches have new commits, Git creates a *merge commit* that
  joins the two histories.

A **merge conflict** happens when both branches changed the *same lines* of the *same
file*. Git can't decide which version is right — so it asks you. Conflicts are normal,
not an error; resolving them is a routine skill you'll practice today.

## 2. Hands-on exercise

Continue in the `git-practice` repository from Module 1 (or create a fresh one with
`git init`).

### Step 1 — See where you are

```bash
git branch
```

This lists all branches; the `*` marks the branch you're currently on (probably `main`
or `master`).

### Step 2 — Create and switch to a new branch

```bash
git switch -c add-favorite-datasets
```

`git switch -c` creates a branch and switches to it in one step. (You may also see the
older `git checkout -b` — it does the same thing.)

### Step 3 — Make changes on the branch

Add a few lines to `notes.md` listing open datasets you find interesting, then commit:

```bash
git add notes.md
git commit -m "Add list of favorite open datasets"
```

### Step 4 — Switch back and observe

```bash
git switch main
```

Open `notes.md` — your new lines are gone! Don't panic: they're safe on the
`add-favorite-datasets` branch. Switching branches swaps the files in your working
directory to match that branch's latest commit.

### Step 5 — Merge the branch into main

```bash
git merge add-favorite-datasets
```

Since `main` didn't change in the meantime, this is a fast-forward merge. Your lines are
back in `notes.md`. Delete the branch, since it's merged and done:

```bash
git branch -d add-favorite-datasets
```

### Step 6 — Create a conflict on purpose

Now the important part — experiencing a conflict in a safe place:

```bash
git switch -c change-title
```

Edit the **first line** of `notes.md` (e.g. change the title to "ODON practice notes"),
commit, and switch back:

```bash
git add notes.md
git commit -m "Change title on branch"
git switch main
```

Now edit the **same first line** of `notes.md` on `main` to something *different* (e.g.
"My Git training notes") and commit:

```bash
git add notes.md
git commit -m "Change title on main"
```

### Step 7 — Trigger and resolve the conflict

```bash
git merge change-title
```

Git will report a conflict. Open `notes.md` — you'll see conflict markers:

```text
<<<<<<< HEAD
My Git training notes
=======
ODON practice notes
>>>>>>> change-title
```

Everything between `<<<<<<<` and `=======` is the version on your current branch
(`main`); between `=======` and `>>>>>>>` is the incoming version. **To resolve:** edit
the file so it contains exactly what you want (pick one version, or combine them), delete
all three marker lines, then:

```bash
git add notes.md
git commit
```

The merge is complete. Congratulations — you've resolved your first conflict.

### Step 8 — Visualize your history

```bash
git log --oneline --graph --all
```

The `--graph` view shows branches and merges as an ASCII diagram — very useful for
understanding what happened. Use it whenever you're unsure about the state of a repo.

## 3. Pair exercise (in the session)

You'll pair up: both partners branch off the same file in the shared practice repo, make
conflicting edits, then merge and resolve the conflict *together*. Conflict resolution
clicks much faster when experienced live than when read about.

## 4. Resources for this module

| Resource | Link |
|---|---|
| Learn Git Branching — "Branching" & "Merging" sequences (interactive, highly recommended) | [learngitbranching.js.org](https://learngitbranching.js.org/) |
| Pro Git book, Ch. 3 — Branching and Merging | [git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) |
| GitHub Docs — Resolving merge conflicts | [docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts) |
| GitHub Skills — hands-on courses catalogue | [github.com/skills](https://github.com/skills) |

## 5. Before Session 3 — final checklist

- [ ] I can create a branch and switch between branches with `git switch`
- [ ] I understand that a branch is a pointer, not a copy of the project
- [ ] I can merge a branch into `main` with `git merge`
- [ ] I know the difference between a fast-forward merge and a merge commit
- [ ] I have created and resolved a merge conflict myself
- [ ] I can read conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) and know what each section means
- [ ] I can visualize branch history with `git log --oneline --graph --all`
- [ ] I completed the "Branching" levels on learngitbranching.js.org

Questions before the session? Reach out any time at info@odon.at.

---

**Contact:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Module 2 Handout*

<br>

---
---

<br>

# Learning Git With Open Data
### Modul 2 — Branches & Merging

In Modul 1 hast du gelernt, Schnappschüsse deiner Arbeit mit Commits zu speichern. In
diesem Modul lernst du die Superkraft von Git kennen: **Branches** — paralleles Arbeiten
an mehreren Versionen eines Projekts und das sichere Zusammenführen. Das ist die
Grundlage dafür, wie Teams (und ODON) zusammenarbeiten, ohne sich gegenseitig in die
Quere zu kommen.

---

## 1. Grundlegende Konzepte

Ein **Branch** ist ein beweglicher Zeiger auf einen Commit. Wenn du einen Branch
erstellst, kopierst du keine Dateien — du erzeugst nur ein neues Label, mit dem du eine
separate Verlaufslinie aufbauen kannst. Deshalb sind Branches in Git extrem leichtgewichtig
und schnell — und deshalb ist ein Branch pro Aufgabe der normale Arbeitsablauf, keine
Ausnahme.

Der Standard-Branch heißt üblicherweise **`main`**. Die Konvention: `main` enthält immer
funktionierende, geprüfte Inhalte; neue Arbeit passiert auf **Feature-Branches** (z. B.
`add-bike-data`, `fix-readme-typo`) und wird zurück in `main` gemerged, wenn sie fertig ist.

**Merging** führt den Verlauf zweier Branches zusammen. Zwei Fälle:

- **Fast-Forward-Merge:** Wenn sich `main` seit deinem Abzweigen nicht geändert hat,
  bewegt Git einfach den `main`-Zeiger nach vorne. Kein neuer Commit nötig.
- **Merge-Commit:** Wenn beide Branches neue Commits haben, erzeugt Git einen
  *Merge-Commit*, der die beiden Verläufe verbindet.

Ein **Merge-Konflikt** entsteht, wenn beide Branches *dieselben Zeilen* *derselben Datei*
geändert haben. Git kann nicht entscheiden, welche Version richtig ist — also fragt es
dich. Konflikte sind normal, kein Fehler; sie zu lösen ist eine Routinefähigkeit, die du
heute übst.

## 2. Praktische Übung

Arbeite im `git-practice`-Repository aus Modul 1 weiter (oder erstelle mit `git init` ein
frisches).

### Schritt 1 — Sehen, wo du bist

```bash
git branch
```

Das listet alle Branches auf; das `*` markiert den Branch, auf dem du dich gerade
befindest (vermutlich `main` oder `master`).

### Schritt 2 — Neuen Branch erstellen und wechseln

```bash
git switch -c add-favorite-datasets
```

`git switch -c` erstellt einen Branch und wechselt in einem Schritt dorthin. (Du wirst
auch das ältere `git checkout -b` sehen — es macht dasselbe.)

### Schritt 3 — Änderungen auf dem Branch machen

Füge ein paar Zeilen zu `notes.md` hinzu, in denen du offene Datensätze auflistest, die
du interessant findest, und committe:

```bash
git add notes.md
git commit -m "Liste mit interessanten offenen Datensätzen hinzugefügt"
```

### Schritt 4 — Zurückwechseln und beobachten

```bash
git switch main
```

Öffne `notes.md` — deine neuen Zeilen sind weg! Keine Panik: Sie sind sicher auf dem
Branch `add-favorite-datasets`. Beim Branch-Wechsel tauscht Git die Dateien in deinem
Arbeitsverzeichnis gegen den letzten Commit des jeweiligen Branches aus.

### Schritt 5 — Branch in main mergen

```bash
git merge add-favorite-datasets
```

Da sich `main` in der Zwischenzeit nicht geändert hat, ist das ein Fast-Forward-Merge.
Deine Zeilen sind zurück in `notes.md`. Lösche den Branch, da er gemerged und erledigt ist:

```bash
git branch -d add-favorite-datasets
```

### Schritt 6 — Absichtlich einen Konflikt erzeugen

Jetzt der wichtige Teil — einen Konflikt an einem sicheren Ort erleben:

```bash
git switch -c change-title
```

Bearbeite die **erste Zeile** von `notes.md` (ändere z. B. den Titel zu "ODON
Übungsnotizen"), committe und wechsle zurück:

```bash
git add notes.md
git commit -m "Titel auf Branch geändert"
git switch main
```

Bearbeite jetzt **dieselbe erste Zeile** von `notes.md` auf `main` zu etwas *anderem*
(z. B. "Meine Git-Trainingsnotizen") und committe:

```bash
git add notes.md
git commit -m "Titel auf main geändert"
```

### Schritt 7 — Konflikt auslösen und lösen

```bash
git merge change-title
```

Git meldet einen Konflikt. Öffne `notes.md` — du siehst Konfliktmarkierungen:

```text
<<<<<<< HEAD
Meine Git-Trainingsnotizen
=======
ODON Übungsnotizen
>>>>>>> change-title
```

Alles zwischen `<<<<<<<` und `=======` ist die Version auf deinem aktuellen Branch
(`main`); zwischen `=======` und `>>>>>>>` steht die eingehende Version. **Zum Lösen:**
Bearbeite die Datei so, dass sie genau das enthält, was du willst (wähle eine Version
oder kombiniere sie), lösche alle drei Markierungszeilen, dann:

```bash
git add notes.md
git commit
```

Der Merge ist abgeschlossen. Gratulation — du hast deinen ersten Konflikt gelöst.

### Schritt 8 — Verlauf visualisieren

```bash
git log --oneline --graph --all
```

Die `--graph`-Ansicht zeigt Branches und Merges als ASCII-Diagramm — sehr hilfreich, um
zu verstehen, was passiert ist. Nutze sie immer, wenn du dir über den Zustand eines Repos
unsicher bist.

## 3. Partnerübung (in der Sitzung)

Ihr arbeitet zu zweit: Beide zweigen von derselben Datei im gemeinsamen Übungs-Repo ab,
macht widersprüchliche Änderungen und merged dann *gemeinsam* — inklusive
Konfliktlösung. Konfliktlösung versteht man viel schneller, wenn man sie live erlebt,
statt nur darüber zu lesen.

## 4. Ressourcen für dieses Modul

| Ressource | Link |
|---|---|
| Learn Git Branching — "Branching"- & "Merging"-Sequenzen (interaktiv, sehr empfohlen) | [learngitbranching.js.org](https://learngitbranching.js.org/) |
| Pro Git Buch, Kap. 3 — Branching und Merging | [git-scm.com/book/de/v2/Git-Branching-Branches-auf-einen-Blick](https://git-scm.com/book/de/v2/Git-Branching-Branches-auf-einen-Blick) |
| GitHub Docs — Merge-Konflikte lösen | [docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts) |
| GitHub Skills — Katalog mit praktischen Kursen | [github.com/skills](https://github.com/skills) |

## 5. Vor Sitzung 3 — Abschluss-Checkliste

- [ ] Ich kann einen Branch erstellen und mit `git switch` zwischen Branches wechseln
- [ ] Ich verstehe, dass ein Branch ein Zeiger ist, keine Kopie des Projekts
- [ ] Ich kann einen Branch mit `git merge` in `main` mergen
- [ ] Ich kenne den Unterschied zwischen Fast-Forward-Merge und Merge-Commit
- [ ] Ich habe selbst einen Merge-Konflikt erzeugt und gelöst
- [ ] Ich kann Konfliktmarkierungen (`<<<<<<<`, `=======`, `>>>>>>>`) lesen und weiß, was jeder Abschnitt bedeutet
- [ ] Ich kann den Branch-Verlauf mit `git log --oneline --graph --all` visualisieren
- [ ] Ich habe die "Branching"-Level auf learngitbranching.js.org abgeschlossen

Fragen vor der Sitzung? Melde dich jederzeit unter info@odon.at.

---

**Kontakt:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Modul 2 Handout*
