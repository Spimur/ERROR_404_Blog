# KI-Dokumentation: Evaluation und Reflexion

**Projekt:** Error 404: Good Design Not Found
**Entwickler:** Timo Weiler

---

## 1. Evaluation und Nutzwertanalyse von KI-Werkzeugen

Vor und während der Entwicklung des Web-Projekts wurden zwei unterschiedliche KI-Werkzeuge evaluiert, um den Entwicklungsprozess im Bereich HTML, CSS und JavaScript zu unterstützen. 

Die evaluierten Werkzeuge waren:
1. **Google Gemini (Advanced)** (Kontextbasiertes LLM)
2. **ChatGPT (GPT-4)** (Kontextbasiertes LLM)

Um eine objektive Entscheidung zu treffen, wurde folgende Nutzwertanalyse durchgeführt (Gewichtung von 1 = unwichtig bis 5 = sehr wichtig; Erfüllungsgrad von 1 = ungenügend bis 5 = sehr gut):

| Kriterium | Gewichtung (G) | Gemini (Note N) | Gemini (G × N) | ChatGPT (Note N) | ChatGPT (G × N) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Code-Generierung (HTML/CSS/JS)** | 5 | 5 | **25** | 4 | **20** |
| **Kontextverständnis (Projekt-Historie)**| 4 | 5 | **20** | 4 | **16** |
| **Kreative Text-Generierung (Blogging)**| 3 | 4 | **12** | 5 | **15** |
| **Fehlerdiagnose / Debugging** | 5 | 4 | **20** | 4 | **20** |
| **Verfügbarkeit / Kostenfaktor** | 2 | 5 | **10** | 3 | **6** |
| **Total** | | | **87** | | **77** |

---

## 2. Begründung der Werkzeugwahl

Auf Basis der Nutzwertanalyse habe ich mich entschieden, primär **Google Gemini** für dieses Projekt zu nutzen. 

**Begründung:** Gemini zeigte eine herausragende Fähigkeit, den Kontext über einen sehr langen Chat-Verlauf hinweg zu behalten. Gerade bei der Arbeit mit reinem, statischem HTML mussten oft Querverweise zwischen der `style.css` und verschiedenen Detailseiten (`detail.html`) gezogen werden. Gemini konnte sich das von mir gewählte Design-System (Neo-Brutalismus) perfekt merken und konsistent anwenden. Zudem war das Tool völlig kostenlos und uneingeschränkt in Echtzeit nutzbar, was den Workflow stark beschleunigte.

---

## 3. Einsatz der KI im Projekt

Die KI wurde nicht als stumpfer "Code-Generator" eingesetzt, sondern als technischer Sparringspartner und Debugging-Assistent in folgenden Projektphasen:

* **Konzept- & Design-Entwicklung:** Generierung der CSS-Variablen für das brutalistische Farbschema (Schwarz, Weiss, starkes Rot) und das strukturelle Setup der Flexbox- und CSS-Grid-Systeme.
* **Inhalts-Engineering (Copywriting):** Formulierung von humorvollen, ironischen englischen Texten für die Blog-Artikel auf Basis meiner rohen Bild-Beschreibungen (z.B. für das "Spisy Seed Sad" Schild oder die "Avocado Hass").
* **Logik-Entwicklung (Workarounds):** Konzeption einer asynchronen JavaScript-Lösung (Fetch-API), um Bilder über eine externe API (ImgBB) hochzuladen, da der genutzte Formular-Dienst (Formspree) keine Dateiuploads im Free-Tier zuliess.
* **Refactoring:** Behebung von fehlerhaften CSS-Layouts (z.B. das ungewollte Dehnen von CSS-Grid-Cards).

---

## 4. Konkrete Beispiele (Prompt-Verlauf)

Anbei zwei markante Beispiele, wie die KI konkret zur Problemlösung genutzt wurde.

### Beispiel 1: Behebung des CSS-Grid-Bugs
* **Mein Prompt:** *"was mir noch aufgefallen ist, wenn man filtert ist die breite der einzelnen cards davon abhängig wie viele in dieser kategorie sind. zb wenns nur eins ist ist das sehr breit gestreckt. muss das so sein? und wie kann man es einheitlich machen?"*
* **KI Antwort (Zusammenfassung):** Die KI erklärte mir, dass dies ein typischer Nebeneffekt der Eigenschaft `auto-fit` im CSS-Grid sei. Sie lieferte den korrigierten Code-Snippet, in dem `auto-fit` zu `auto-fill` geändert wurde.
* **Lerneffekt:** Ich habe den genauen Unterschied zwischen `auto-fit` (streckt Elemente, um Platz zu füllen) und `auto-fill` (behält unsichtbare Spalten bei) gelernt.

### Beispiel 2: Umgehung der Formspree-Limitierung
* **Mein Prompt:** *"mir gefallen jetzt beide optionen nicht (file uploads deaktivieren). also keine files senden zu können macht das komplette konzept des kontakt formulars zunichte. kann man das nicht anderweitig umgehen? vielleicht anderer anbieter oder link zum foto oder so?"*
* **KI Antwort:** Die KI schlug vor, das Problem im Frontend mit JavaScript zu lösen. Sie generierte ein Skript, das ein eingereichtes Foto über die ImgBB-API hochlädt, den zurückgegebenen URL-Link abfängt, in ein verstecktes Formular-Feld schreibt und dieses dann an Formspree sendet.
* **Ergebnis:** Das Backend-Problem wurde elegant durch reines Frontend-Engineering (`async/await`, Fetch-API) gelöst.

---

## 5. Reflexion: Erfahrungen, Erkenntnisse, Stärken und Schwächen

Die Entwicklung dieses Projekts in enger Zusammenarbeit mit der KI war extrem aufschlussreich. 

**Stärken der KI:**
Die grösste Stärke lag im Debugging und in der Lösungsfindung für Architektur-Probleme (wie das Formspree-Limit). Wenn man das Problem detailliert beschreibt, liefert die KI nicht nur den Code, sondern auch die Erklärung, *warum* der alte Code nicht funktionierte. Das beschleunigt den eigenen Lernprozess massiv im Vergleich zu klassischen StackOverflow-Recherchen. Auch beim Schreiben der Blogtexte war die KI eine enorme Hilfe, um den gewünschten ironischen Tonfall in fliessendem Englisch zu treffen.

**Schwächen der KI:**
Eine deutliche Schwäche zeigte sich bei der manuellen DOM-Manipulation in statischen HTML-Dateien. Wenn ich lange HTML-Blöcke (wie die `detail.html`) mehrfach hin und her kopierte, generierte die KI teilweise leicht fehlerhaften Code mit doppelten Verschachtelungen (z.B. zwei `<article>`-Tags ineinander). 

**Persönliche Erkenntnis:**
Die KI ist ein unfassbar mächtiges Werkzeug, das die Entwicklungszeit halbiert. **Allerdings ersetzt sie kein grundlegendes Fachwissen.** Hätte ich im Web-Grundlagen-Modul nicht gelernt, wie CSS-Grids, DOM-Bäume und HTML-Verschachtelungen funktionieren, wäre ich nicht in der Lage gewesen, die Fehler der KI zu erkennen oder ihre Lösungsvorschläge sauber in mein bestehendes System zu integrieren. KI macht einen guten Programmierer schneller, aber sie nimmt einem das Denken nicht ab.