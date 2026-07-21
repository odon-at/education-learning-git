# Learning Git With Open Data
### Module 5 — Working with Open Data (Final Module)

You now master the full workflow: Issue → Branch → PR → Review → Merge. In this final
module you apply it to what ODON actually does — **open data**. You'll version a tiny
real dataset, improve its quality, and document it properly. Along the way you'll see
why Git and GitHub are not just for code: they bring transparency, review, and history
to *data* work too.

---

## 1. Why version data with Git?

Datasets change: new records arrive, errors get fixed, schemas evolve. Without version
control, a dataset is just "the latest file" — nobody knows what changed, when, or why.
With Git, every change to a dataset is:

- **Traceable** — `git log` and `git blame` show who changed which value and why
- **Reviewable** — a PR diff makes data corrections visible before they land
- **Reversible** — a bad import can be rolled back like any bad commit

This maps directly to ODON's **Open Data Maturity Model (ODMM)**: the *Technical
Openness* dimension (T1–T4) rewards consistent structure, metadata, and versioning —
exactly what a Git-based workflow provides.

**Rules of thumb for data in Git:**

- Git works best with **text formats**: CSV, JSON, GeoJSON — not XLSX (binary files
  don't diff).
- **One record per line** (CSV) makes diffs readable: one changed value = one changed
  line.
- **Never commit secrets** — API tokens, credentials, personal data. Check twice; Git
  history is forever.

## 2. Hands-on exercise

Both tasks run through the full Module 4 loop: **open an Issue, branch, change, PR,
review, merge**. The practice repo contains a small sample file,
[`bike-share-mini.csv`](../data/bike-share-mini.csv) — 15 rows, under 1 KB, so every diff in
this exercise stays short and easy to read end to end.

### Task A — Add a record and fix a data quality issue (one PR)

The file contains a few deliberate quality problems your mentor seeded on purpose:

- Inconsistent date formats in `last_updated` (`2026-03-01` vs `01.03.2026`)
- A stray text value in the numeric `bikes_available` column (`several`, `n/a`)
- Inconsistent capitalization in `district` (`neubau`, `JOSEFSTADT` vs `Neubau`)

1. Open an Issue: *"Add a station record and normalize `district`/`last_updated`
   formatting"*. Be specific about the target format (e.g. dates as ISO 8601
   `YYYY-MM-DD`, districts in Title Case).
2. On a branch, do **both** in one small commit: add one plausible new row at the end,
   and fix the formatting issues you described.

```bash
git switch -c yourname/issue-N-fix-and-add
# edit data/bike-share-mini.csv
git add data/bike-share-mini.csv
git commit -m "Add station record and normalize formatting (#N)"
git push -u origin yourname/issue-N-fix-and-add
```

3. Open a PR (`Closes #N`) explaining your correction rule in the description.
4. Your reviewer checks: is the new row consistent with the schema? Was the formatting
   rule applied everywhere it should be — and nowhere it shouldn't?

Because the file is tiny, the whole diff fits on one screen — a good habit to notice:
small datasets make small, reviewable PRs even easier.

### Task B — Write a mini data dictionary

A dataset without documentation is hard to trust or reuse, no matter how clean the
values are. On a branch, add a short section to `README.md` (or `data/README.md`)
with just three things:

- **Source** — where the data (hypothetically) comes from, and its **license**
- **Columns** — one line per column: name, type, short description
- **Example row** — one row from the file, to make the structure concrete

PR, review, merge — as always. Keep it to a few lines; this is meant to take minutes,
not an hour.

**Why this matters:** documenting the license is the *Legal Openness* dimension
(L1–L4) of the ODMM. A dataset without a stated license is L1 (Closed/Undefined) —
even if it's technically perfect. Documentation is what makes data *legally* usable,
not just technically.

## 3. Group discussion (in the session)

Pick one real dataset from [data.gv.at](https://www.data.gv.at) (Austria's open data
portal) and assess it together against the ODMM: which Legal level (L1–L4)? Which
Technical level (T1–T4)? What single change would raise its level?

## 4. Resources for this module

| Resource | Link |
|---|---|
| ODON — Open Data page & ODMM | [odon.at/en/open-data/](https://odon.at/en/open-data/) |
| data.gv.at — Austria's open data portal | [data.gv.at](https://www.data.gv.at) |
| Open Data Handbook (Open Knowledge Foundation) | [opendatahandbook.org](https://opendatahandbook.org/) |
| GitHub Docs — About large files on GitHub | [docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github) |

## 5. Course completion checklist

- [ ] I added a record and fixed a data quality issue in a single reviewed PR
- [ ] I can read a CSV diff and explain exactly what changed
- [ ] I wrote a short data dictionary with source, license, and columns
- [ ] I can explain why a dataset's license matters (ODMM Legal dimension)
- [ ] I know which file formats work well in Git (CSV/JSON) and which don't (XLSX)
- [ ] I know never to commit secrets or personal data
- [ ] I can explain the full loop — Issue, branch, commit, push, PR, review, merge —
  without notes

**That's the course.** You've gone from installing Git to opening, reviewing, and
merging real pull requests — including on real open data. Keep the habit going with
small, frequent contributions; that's the best way to stay sharp. Questions any time:
info@odon.at.

---

**Contact:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Module 5 Handout*

<br>

---
---

<br>

# Learning Git With Open Data
### Modul 5 — Arbeiten mit Open Data (Letztes Modul)

Du beherrschst jetzt den vollständigen Workflow: Issue → Branch → PR → Review → Merge.
In diesem letzten Modul wendest du ihn auf das an, was ODON tatsächlich macht — **Open
Data**. Du versionierst einen winzigen echten Datensatz, verbesserst seine Qualität und
dokumentierst ihn richtig. Dabei siehst du, warum Git und GitHub nicht nur für Code
sind: Sie bringen Transparenz, Review und Historie auch in die *Daten*arbeit.

---

## 1. Warum Daten mit Git versionieren?

Datensätze ändern sich: neue Einträge kommen dazu, Fehler werden behoben, Schemata
entwickeln sich weiter. Ohne Versionskontrolle ist ein Datensatz nur "die neueste
Datei" — niemand weiß, was sich wann und warum geändert hat. Mit Git ist jede Änderung
an einem Datensatz:

- **Nachvollziehbar** — `git log` und `git blame` zeigen, wer welchen Wert geändert
  hat und warum
- **Reviewbar** — ein PR-Diff macht Datenkorrekturen sichtbar, bevor sie landen
- **Umkehrbar** — ein fehlerhafter Import lässt sich zurückrollen wie jeder
  fehlerhafte Commit

Das passt direkt zu ODONs **Open Data Maturity Model (ODMM)**: Die Dimension
*Technische Offenheit* (T1–T4) belohnt konsistente Struktur, Metadaten und
Versionierung — genau das, was ein Git-basierter Workflow liefert.

**Faustregeln für Daten in Git:**

- Git funktioniert am besten mit **Textformaten**: CSV, JSON, GeoJSON — nicht XLSX
  (Binärdateien lassen sich nicht diffen).
- **Ein Datensatz pro Zeile** (CSV) macht Diffs lesbar: ein geänderter Wert = eine
  geänderte Zeile.
- **Niemals Geheimnisse committen** — API-Tokens, Zugangsdaten, personenbezogene
  Daten. Zweimal prüfen; die Git-Historie ist für immer.

## 2. Praktische Übung

Beide Aufgaben laufen durch die vollständige Schleife aus Modul 4: **Issue eröffnen,
branchen, ändern, PR, Review, mergen**. Das Übungs-Repo enthält eine kleine
Beispieldatei, [`bike-share-mini.csv`](../data/bike-share-mini.csv) — 15 Zeilen, unter
1 KB, sodass jeder Diff in dieser Übung kurz und von Anfang bis Ende leicht lesbar
bleibt.

### Aufgabe A — Einen Eintrag hinzufügen und ein Datenqualitätsproblem beheben (ein PR)

Die Datei enthält ein paar absichtliche Qualitätsprobleme, die deine Mentorin/dein
Mentor eingebaut hat:

- Inkonsistente Datumsformate in `last_updated` (`2026-03-01` vs. `01.03.2026`)
- Ein verirrter Textwert in der numerischen Spalte `bikes_available` (`several`,
  `n/a`)
- Inkonsistente Groß-/Kleinschreibung in `district` (`neubau`, `JOSEFSTADT` vs.
  `Neubau`)

1. Eröffne ein Issue: *"Stationseintrag hinzufügen und Formatierung von
   `district`/`last_updated` normalisieren"*. Sei konkret zum Zielformat (z. B.
   Daten als ISO 8601 `YYYY-MM-DD`, Bezirke in Title Case).
2. Mache auf einem Branch **beides** in einem kleinen Commit: füge eine plausible
   neue Zeile am Ende hinzu und behebe die Formatierungsprobleme, die du beschrieben
   hast.

```bash
git switch -c deinname/issue-N-fix-und-add
# data/bike-share-mini.csv bearbeiten
git add data/bike-share-mini.csv
git commit -m "Stationseintrag hinzugefügt und Formatierung normalisiert (#N)"
git push -u origin deinname/issue-N-fix-und-add
```

3. Eröffne einen PR (`Closes #N`) und erkläre in der Beschreibung deine
   Korrekturregel.
4. Deine Reviewer:in prüft: Ist die neue Zeile konsistent mit dem Schema? Wurde die
   Formatierungsregel überall angewendet, wo sie sollte — und nirgends, wo nicht?

Da die Datei winzig ist, passt der ganze Diff auf einen Bildschirm — eine gute
Beobachtung: kleine Datensätze machen kleine, reviewbare PRs noch einfacher.

### Aufgabe B — Ein Mini-Data-Dictionary schreiben

Ein Datensatz ohne Dokumentation ist schwer zu vertrauen oder wiederzuverwenden, egal
wie saubere die Werte sind. Füge auf einem Branch einen kurzen Abschnitt zur
`README.md` (oder `data/README.md`) hinzu, mit nur drei Dingen:

- **Quelle** — woher die Daten (hypothetisch) stammen, und ihre **Lizenz**
- **Spalten** — eine Zeile pro Spalte: Name, Typ, kurze Beschreibung
- **Beispielzeile** — eine Zeile aus der Datei, um die Struktur konkret zu machen

PR, Review, Merge — wie immer. Halte es kurz; das soll Minuten dauern, keine Stunde.

**Warum das wichtig ist:** Die Dokumentation der Lizenz betrifft die Dimension
*Rechtliche Offenheit* (L1–L4) des ODMM. Ein Datensatz ohne angegebene Lizenz ist L1
(Geschlossen/Undefiniert) — selbst wenn er technisch perfekt ist. Dokumentation macht
Daten *rechtlich* nutzbar, nicht nur technisch.

## 3. Gruppendiskussion (in der Sitzung)

Wählt gemeinsam einen echten Datensatz von [data.gv.at](https://www.data.gv.at)
(Österreichs Open-Data-Portal) und bewertet ihn anhand des ODMM: Welches rechtliche
Level (L1–L4)? Welches technische Level (T1–T4)? Welche einzelne Änderung würde sein
Level anheben?

## 4. Ressourcen für dieses Modul

| Ressource | Link |
|---|---|
| ODON — Open-Data-Seite & ODMM | [odon.at/en/open-data/](https://odon.at/en/open-data/) |
| data.gv.at — Österreichs Open-Data-Portal | [data.gv.at](https://www.data.gv.at) |
| Open Data Handbook (Open Knowledge Foundation) | [opendatahandbook.org](https://opendatahandbook.org/) |
| GitHub Docs — Über große Dateien auf GitHub | [docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github) |

## 5. Abschluss-Checkliste des Kurses

- [ ] Ich habe einen Eintrag hinzugefügt und ein Datenqualitätsproblem in einem reviewten PR behoben
- [ ] Ich kann einen CSV-Diff lesen und genau erklären, was sich geändert hat
- [ ] Ich habe ein kurzes Data Dictionary mit Quelle, Lizenz und Spalten geschrieben
- [ ] Ich kann erklären, warum die Lizenz eines Datensatzes wichtig ist (rechtliche ODMM-Dimension)
- [ ] Ich weiß, welche Dateiformate gut mit Git funktionieren (CSV/JSON) und welche nicht (XLSX)
- [ ] Ich weiß, dass ich niemals Geheimnisse oder personenbezogene Daten committen darf
- [ ] Ich kann die komplette Schleife — Issue, Branch, Commit, Push, PR, Review, Merge — ohne Notizen erklären

**Das war der Kurs.** Du bist von der Git-Installation zum Eröffnen, Reviewen und
Mergen echter Pull Requests gekommen — auch bei echten offenen Daten. Bleib mit
kleinen, häufigen Beiträgen in Übung; das ist der beste Weg, es zu vertiefen. Fragen
jederzeit an: info@odon.at.

---

**Kontakt:** [odon.at](https://odon.at) · [info@odon.at](mailto:info@odon.at) · [github.com/odon-at](https://github.com/odon-at)

*ODON – Offene Daten für Offene Nutzung · Learning Git With Open Data – Modul 5 Handout*
