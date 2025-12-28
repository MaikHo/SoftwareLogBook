# SoftwareLogBook

## Sprachen
- Englisch (Standard)
- [Deutsch](README.de.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- [日本語](README.ja.md)

SoftwareLogBook ist ein Logbuch für Softwaresysteme auf Basis von Markdown-Dateien mit YAML-Frontmatter.

## Motivation und Einordnung
SoftwareLogBook dokumentiert Software-Tools, deren Deployments und Lebenszyklusereignisse in einer Form, die ohne spezielle Werkzeuge gelesen und geprüft werden kann.

Warum Dateien + Markdown + Git:
- Klartext ist leicht zu lesen, zu diffen und zu prüfen.
- Git bietet Historie, Nachvollziehbarkeit und Append-only-Disziplin.
- Die Struktur bleibt auch in Umgebungen mit wenig Tooling nutzbar.

Geeignete Szenarien:
- Kleine bis mittlere Bestände interner oder externer Tools.
- Teams, die einen einzigen, auditierbaren Ort für Releases, Incidents und Wartungsnotizen wollen.
- Umgebungen, in denen ein leichtgewichtiges, repository-basiertes Logbuch ausreicht.

Was dies nicht ist:
- Keine CMDB.
- Kein Ticket-System.
- Kein Monitoring-System.

## Zentrale Konzepte (High-Level)
- Software: ein Datensatz, der ein Tool und seinen Kontext zur Verantwortlichkeit beschreibt.
- Deployment: eine installierte Instanz eines Software-Tools in einer Umgebung.
- Entry: ein Append-only-Ereigniseintrag (z. B. Release, Incident, Wartung).
- Global entry: ein Ereignis oder eine Richtlinie, die für alle Tools gilt.
- Corrections: ein eigener Eintrag, der auf den zu korrigierenden Eintrag verweist.

## Repository-Struktur
- `software/<softwareKey>/`: Ordner pro Tool.
- `software/<softwareKey>/software.md`: Software-Datensatz.
- `software/<softwareKey>/deployments/`: Deployment-Datensätze.
- `software/<softwareKey>/entries/<YYYY>/`: Tool-spezifische Logbuch-Einträge nach Jahr.
- `_global/entries/<YYYY>/`: globale Logbuch-Einträge nach Jahr.
- `taxonomy/`: gemeinsame Enumerationen und Referenztypen.
- `templates/`: Startvorlagen für neue Datensätze.

## Minimaler Workflow
1. Erstelle einen neuen Software-Datensatz mit `../templates/software.template.md`.
2. Füge Deployment-Datensätze mit `../templates/deployment.template.md` hinzu.
3. Füge Einträge mit `../templates/entry.template.md` hinzu (Release, Incident, Wartung).
4. Wenn etwas korrigiert werden muss, füge einen neuen Eintrag mit `type: correction` hinzu, der auf den ursprünglichen Eintrag verweist.

## Weiterführende Dokumente
- `../SPEC.md`: maßgebliche Quelle für Struktur und Regeln.
- `../CONTRIBUTING.md`: Hinweise zu Benennung, Eindeutigkeit und Append-only.
- `../GUARDRAILS.md`: empfohlene Validierungsprüfungen und Hygiene-Hinweise.

## Viewer und Tooling (optional)
Das Repository ist ohne Tooling vollständig nutzbar. Viewer oder CLI-Tools können darauf aufbauen, sind aber nicht Teil des Standards.

## Lizenz
MIT (siehe `../LICENSE`)

## Translation note
This text was translated by ChatGPT.
