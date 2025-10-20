# Inhaltsprüfung des QR-Repositorys (Stand: 2025-10-20)

## 1. Inventarübersicht

| Pfad | Inhalt | Bemerkungen |
| --- | --- | --- |
| `main.tex` | Hauptdokument, bindet Kapitel laut `order.txt` ein | Struktur vorhanden, alle Kapitel aktuell Platzhalter. |
| `macros.tex` | Globale Präambel | Enthält Standardpakete; doppelte Sprachumschaltung über `babel` ist vorbereitet. |
| `abstract.tex`, `intro.tex`, `theory/background.tex`, `methods/model.tex`, `results/main.tex`, `discussion/main.tex`, `conclusion/main.tex`, `appendix/A.tex` | Kapiteldateien | Konsistente Abschnittstitel, Inhalt noch nicht gefüllt. |
| `bibliography.tex` | Platzhalter-Literaturverzeichnis | Keine Einträge, Hinweis auf DOIs nötig. |
| `.github/workflows/latex.yml` | CI-Build für LaTeX mittels `latexmk` | Nutzt Secret `BLUE_QR_AUTOMATION`, erstellt PDF- und Log-Artefakte. |
| `.github/workflows/python-package.yml` | Standard-Python-Workflow | Für aktuelles Projekt ohne Python-Code potentiell überflüssig; würde mangels `pytest`-Zielen fehlschlagen. |
| `CHANGES.md` | Änderungsprotokoll | Dokumentiert initialen Projektaufbau. |
| `residualplot_qr_vs_lcdm.png`, `qr_v6_00_c.pdf`, `qr_v7.pdf`, `qr_v9.00.pdf` | Referenzmaterial | Müssen hinsichtlich Lizenz und Revisionsstand eingeordnet werden. |
| `logs/` | Build-Logs (leer, `.gitkeep`) | Wird von CI befüllt. |
| `.vscode/extensions.json` | Editor-Empfehlungen | Enthält nur OpenAI-Plugin. |

## 2. Konfliktmatrix

| Thema | Beobachtung | Betroffene Dateien |
| --- | --- | --- |
| CI-Abdeckung | LaTeX-Workflow erwartet lauffähiges Projekt, Kapitel enthalten aber ausschließlich Platzhalter, wodurch Builds leer bleiben | `main.tex` und Kapiteldateien |
| Python-Workflow | Workflow setzt Python-Teststruktur voraus, die nicht existiert; könnte bei Aktivierung scheitern | `.github/workflows/python-package.yml` |

Derzeit liegen keine inhaltlich widersprüchlichen Aussagen im Quelltext selbst vor; Hauptproblem ist der fehlende Inhalt.

## 3. Offene Punkte / Nachforderungen

1. Vollständige Kapitelinhalte: Originaltext oder freigegebene Quellen werden benötigt, um die Platzhalter zu ersetzen (`abstract.tex`, `intro.tex`, `theory/background.tex`, `methods/model.tex`, `results/main.tex`, `discussion/main.tex`, `conclusion/main.tex`, `appendix/A.tex`).
2. Literaturdatenbank: Verifizierte Referenzen mit DOI/BibTeX müssen bereitgestellt werden (`bibliography.tex`).
3. Empirische Datensätze: Messdaten (Planck, Pantheon+, KiDS, HALOGAS etc.) für Tabellen mit Prozentabweichungen fehlen.
4. Entscheid zu CI-Workflows: Klärung, ob der Python-Workflow deaktiviert oder auf projektbezogene Checks umgestellt werden soll.
5. Lizenz- und Versionsabgleich der eingebundenen PDFs und Grafiken (`qr_v6_00_c.pdf`, `qr_v7.pdf`, `qr_v9.00.pdf`, `residualplot_qr_vs_lcdm.png`).

## 4. Priorisierte To-do-Liste (nach wissenschaftlicher Relevanz)

1. **Inhaltliche Konsolidierung** – Kapiteltexte aus dem Referenzdokument übernehmen, inkl. mathematischer Herleitungen, empirischer Daten und Diskussion. Dabei konsistente Notation (macros.tex) sicherstellen.
2. **Literaturverzeichnis vervollständigen** – Alle Quellen mit DOI/BibTeX-Einträgen erfassen und interne Referenzen (`\cite{}`) vorbereiten.
3. **Empirische Vergleichstabellen erstellen** – Mess- vs. Modellwerte samt Prozentabweichungen in `results/main.tex` und ggf. Anhang dokumentieren.
4. **Workflow-Bereinigung** – Python-Workflow entfernen oder an tatsächliche Bedürfnisse anpassen; LaTeX-Workflow mit minimalem Paketset testen.
5. **Asset-Dokumentation** – Herkunft und Aktualität der PDF/Grafikdateien dokumentieren, ggf. Metadaten ins Repository aufnehmen (z. B. README-Ergänzung).

## 5. Hinweise zur weiteren Verarbeitung

- Platzhalter-TODOs sind in den Quelldateien bereits markiert und sollten beim Befüllen konkret adressiert oder entfernt werden.
- Beim Einpflegen neuer Inhalte ist auf konsistente deutsche Spracheinstellung (`\selectlanguage{ngerman}`) und notwendige englische Abschnitte zu achten.
- Vor dem nächsten Commit empfiehlt sich ein lokaler `latexmk`-Test, um Kompilierbarkeit sicherzustellen, sobald Inhalte ergänzt wurden.
