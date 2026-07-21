# Learning Git With Open Data
### Module 0 — Setup & Why Version Control

This handout is your preparation guide for Session 1 of ODON's *Learning Git With Open Data*
course. Work through the steps below **before** the session so we can dive straight into
hands-on practice together. Budget about 45–60 minutes, and don't worry if something doesn't
work perfectly — we'll troubleshoot together as a group.

---

## 1. Why version control?

Version control is a system that tracks changes to files over time, so you can see what
changed, who changed it, and why — and go back to an earlier version if something breaks.
**Git** is the version control tool itself, running on your computer. **GitHub** is a
website that hosts copies of Git repositories online, so people can share their work and
collaborate on it together.

Think of it like this: Git is your personal, detailed "track changes" history for an
entire project folder, not just one document. GitHub is where your team's shared copy of
that project lives, so everyone can contribute, review each other's changes, and merge
them together safely.

At ODON, Git and GitHub are used for the website, data pipelines, and the APIs you'll be
working with — so this is a core skill for everything that follows in your internship.

## 2. Setup checklist

### Step 1 — Install Git

Download and install Git for your operating system from the official site:
[git-scm.com/downloads](https://git-scm.com/downloads)

Windows: run the installer with default options. macOS: install via the downloaded
package, or run `git --version` in Terminal to trigger the Xcode Command Line Tools
prompt. Linux: use your package manager, e.g. `sudo apt install git`.

### Step 2 — Create a GitHub account

If you don't already have one, sign up at [github.com](https://github.com). Use a
professional username — you may end up using this account beyond your internship. Let
your mentor know your username so you can be added as a collaborator on the practice
repository.

### Step 3 — Install a code editor

We recommend Visual Studio Code (free), which has Git support built in:
[code.visualstudio.com](https://code.visualstudio.com). If you already use another editor
you're comfortable with, that's fine too.

### Step 4 — Set your Git identity

Open a terminal (or the terminal inside VS Code) and set your name and email — this gets
attached to every change you make:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use the same email address you used for your GitHub account.

### Step 5 — Set up authentication (SSH key or token)

GitHub no longer accepts your account password when connecting from the command line.
Choose **one** of the following:

- **SSH key (recommended):** generate one with
  `ssh-keygen -t ed25519 -C "you@example.com"`, then add the public key to your GitHub
  account under Settings → SSH and GPG keys. Guide: docs.github.com → "Connecting to
  GitHub with SSH".
- **Personal Access Token (alternative):** create one under GitHub Settings → Developer
  settings → Personal access tokens, and use it in place of a password when Git prompts
  you.

### Step 6 — Verify everything works

Run these commands in your terminal and confirm you get sensible output (a version
number and your configured name/email):

```bash
git --version
git config --global user.name
git config --global user.email
```

## 3. Resources for this module

| Resource | Link |
|---|---|
| Pro Git book (free reference, Ch. 1) | [git-scm.com/book/en/v2](https://git-scm.com/book/en/v2) |
| GitHub Docs — Git & GitHub learning resources | [docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources](https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources) |
| Video: Git & GitHub Crash Course for Beginners | [youtube.com/watch?v=mAFoROnOfHs](https://www.youtube.com/watch?v=mAFoROnOfHs) |
| Connecting to GitHub with SSH (official guide) | [docs.github.com/en/authentication/connecting-to-github-with-ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) |

## 4. Before Session 1 — final checklist

- [ ] Git is installed and `git --version` works
- [ ] GitHub account created, username shared with your mentor
- [ ] Code editor (e.g. VS Code) installed
- [ ] Git identity configured (name + email)
- [ ] SSH key or Personal Access Token set up
- [ ] I can explain, in my own words, the difference between Git and GitHub

Questions before the session? Reach out any time at info@odon.at.

---

**Contact:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Module 0 Handout*

<br>

---
---

<br>

# Learning Git With Open Data
### Modul 0 — Einrichtung & Warum Versionskontrolle

Dieses Handout ist deine Vorbereitung für die erste Sitzung des Kurses *Learning Git With
Open Data* von ODON. Arbeite die folgenden Schritte **vor** der Sitzung durch, damit wir
direkt mit der praktischen Arbeit starten können. Plane etwa 45–60 Minuten ein — falls etwas
nicht sofort funktioniert, lösen wir das gemeinsam in der Gruppe.

---

## 1. Warum Versionskontrolle?

Versionskontrolle ist ein System, das Änderungen an Dateien im Zeitverlauf nachverfolgt,
sodass du siehst, was geändert wurde, von wem und warum — und zu einer früheren Version
zurückkehren kannst, falls etwas nicht funktioniert. **Git** ist das
Versionskontroll-Werkzeug selbst, das lokal auf deinem Computer läuft. **GitHub** ist eine
Website, die Kopien von Git-Repositories online bereitstellt, damit Menschen ihre Arbeit
teilen und gemeinsam daran zusammenarbeiten können.

Man kann es sich so vorstellen: Git ist deine persönliche, detaillierte
"Änderungsverfolgung" für einen ganzen Projektordner, nicht nur für ein einzelnes
Dokument. GitHub ist der Ort, an dem die gemeinsame Kopie eures Projekts liegt, sodass
alle beitragen, die Änderungen der anderen überprüfen und sie sicher zusammenführen können.

Bei ODON werden Git und GitHub für die Website, Datenpipelines und die APIs verwendet, mit
denen du arbeiten wirst — diese Fähigkeit ist daher grundlegend für alles Weitere in
deinem Praktikum.

## 2. Einrichtungs-Checkliste

### Schritt 1 — Git installieren

Lade Git für dein Betriebssystem von der offiziellen Seite herunter und installiere es:
[git-scm.com/downloads](https://git-scm.com/downloads)

Windows: Installer mit Standardeinstellungen ausführen. macOS: über das heruntergeladene
Paket installieren, oder `git --version` im Terminal ausführen, um die Installation der
Xcode Command Line Tools anzustoßen. Linux: über den Paketmanager, z. B.
`sudo apt install git`.

### Schritt 2 — GitHub-Konto erstellen

Falls du noch keins hast, registriere dich auf [github.com](https://github.com). Verwende
einen professionellen Benutzernamen — du wirst dieses Konto vermutlich auch über dein
Praktikum hinaus nutzen. Teile deinen Benutzernamen deiner Mentorin/deinem Mentor mit,
damit du als Mitwirkende:r im Übungs-Repository hinzugefügt werden kannst.

### Schritt 3 — Code-Editor installieren

Wir empfehlen Visual Studio Code (kostenlos), das eine integrierte Git-Unterstützung
mitbringt: [code.visualstudio.com](https://code.visualstudio.com). Falls du bereits einen
anderen Editor nutzt, mit dem du dich wohlfühlst, ist das auch in Ordnung.

### Schritt 4 — Git-Identität einrichten

Öffne ein Terminal (oder das Terminal in VS Code) und lege Namen und E-Mail-Adresse fest —
diese werden jeder Änderung zugeordnet, die du machst:

```bash
git config --global user.name "Dein Name"
git config --global user.email "du@beispiel.com"
```

Verwende dieselbe E-Mail-Adresse, die du für dein GitHub-Konto genutzt hast.

### Schritt 5 — Authentifizierung einrichten (SSH-Schlüssel oder Token)

GitHub akzeptiert über die Kommandozeile kein Passwort mehr. Wähle **eine** der folgenden
Optionen:

- **SSH-Schlüssel (empfohlen):** erzeuge einen mit
  `ssh-keygen -t ed25519 -C "du@beispiel.com"` und füge den öffentlichen Schlüssel unter
  Settings → SSH and GPG keys zu deinem GitHub-Konto hinzu. Anleitung: docs.github.com →
  "Connecting to GitHub with SSH".
- **Personal Access Token (Alternative):** erstelle eines unter GitHub Settings →
  Developer settings → Personal access tokens und verwende es anstelle eines Passworts,
  wenn Git danach fragt.

### Schritt 6 — Alles überprüfen

Führe diese Befehle im Terminal aus und prüfe, ob eine sinnvolle Ausgabe erscheint (eine
Versionsnummer sowie dein konfigurierter Name/E-Mail):

```bash
git --version
git config --global user.name
git config --global user.email
```

## 3. Ressourcen für dieses Modul

| Ressource | Link |
|---|---|
| Pro Git Buch (kostenlose Referenz, Kap. 1) | [git-scm.com/book/de/v2](https://git-scm.com/book/de/v2) |
| GitHub Docs — Git- & GitHub-Lernressourcen | [docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources](https://docs.github.com/en/get-started/start-your-journey/git-and-github-learning-resources) |
| Video: Git & GitHub Crash Course for Beginners | [youtube.com/watch?v=mAFoROnOfHs](https://www.youtube.com/watch?v=mAFoROnOfHs) |
| Connecting to GitHub with SSH (offizielle Anleitung) | [docs.github.com/en/authentication/connecting-to-github-with-ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) |

## 4. Vor Sitzung 1 — Abschluss-Checkliste

- [ ] Git ist installiert und `git --version` funktioniert
- [ ] GitHub-Konto erstellt, Benutzername mit Mentor:in geteilt
- [ ] Code-Editor (z. B. VS Code) installiert
- [ ] Git-Identität eingerichtet (Name + E-Mail)
- [ ] SSH-Schlüssel oder Personal Access Token eingerichtet
- [ ] Ich kann in eigenen Worten den Unterschied zwischen Git und GitHub erklären

Fragen vor der Sitzung? Melde dich jederzeit unter info@odon.at.

---

**Kontakt:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Modul 0 Handout*
