# GEMINI SYSTEM GUIDELINES — SONA LERNHUB

Dieses Dokument definiert die verbindlichen architektonischen, typografischen und visuellen Gestaltungsregeln für das Projekt **SONA Lernhub** (Japanese Sushi & Kitchen Bar). Alle weiteren Änderungen, Erweiterungen und Code-Generierungen MÜSSEN sich exakt an diese Regeln halten.

---

## 1. Farbpalette (5 Farben — Keine sechste)

Es dürfen ausnahmslos NUR die folgenden fünf Farbtöne verwendet werden. Keine Akzentfarben (kein Blau, kein Rot, kein Grün für Status oder Benachrichtigungen):

| Farbname | Hex-Code | Verwendung |
| :--- | :--- | :--- |
| **Brand Black** | `#000000` | Tiefster Hintergrund, Header/Footer, Kontrastflächen, Login-Hintergrund |
| **Charcoal Grey** | `#121212` | Standard-Hintergrund der Applikation (`body`), Modalkörper |
| **Deep Grey** | `#191919` | Kartenhintergründe, Infoboxen, Tabellenköpfe, abgesetzte Container |
| **Cream Beige** | `#F5ECD7` | Primäre Textfarbe, aktive Buttons, Haarlinien, Logo-SVG, Fokusrahmen |
| **Silk Beige** | `#E3D5CA` | Sekundäre Textfarbe, Kicker, Untertitel, Beschreibungen, dezentere Rahmen |

**Transparenzen:**
- Für feine Haarlinien (`hairline-*`) und Trennlinien ist Cream Beige mit Transparenz gestattet: `rgba(245, 236, 215, 0.18)` bis `rgba(245, 236, 215, 0.3)`.

---

## 2. Strikte visuelle Verbote

- **Keine Schatten:** Weder Schlagschatten (`box-shadow`), noch Textschatten (`text-shadow`) oder Elevations. Alles ist plan. Im CSS global verankert:
  ```css
  * {
      box-shadow: none !important;
      text-shadow: none !important;
  }
  ```
- **Keine Verläufe (Gradients):** Weder lineare noch radiale Farbverläufe. Alle Farbflächen sind einfarbig/monochrom.
- **Keine Emojis:** Keine bunten Symbole oder Standard-Emojis (wie 🍣, 🍱, ❌, ✅) im UI oder in den Fließtexten. Zur visuellen Führung werden ausschließlich verwendet:
  - Typografische Zeichen (`→`, `←`, `[X]`, `+`, `↑`, `↓`)
  - Ausgeschriebene Status in eckigen Klammern: `[ KORREKT BEANTWORTET ]`, `[ GELESEN ]`
  - Minimalistische Vektor-SVGs in Cream Beige (`#F5ECD7`)

---

## 3. Typografie & Schriften

Das Corporate Design von SONA basiert auf zwei Schriftfamilien und strengen Satzregeln:

### Schriftarten
1. **Display & Titel:**
   - **Audrey** (Web-Äquivalent: `Cormorant Garamond`, Georgia, serif)
   - Schnitte: Regular (`400`), Semi-Bold (`600`)
   - Immer in Versalien (Großbuchstaben) gesetzt, Sperrung `0.08em` bis `0.12em`.
2. **Text, Claim & UI:**
   - **Neue Haas Display** (Web-Äquivalent: `Inter`, Helvetica Neue, Arial, sans-serif)
   - Schnitte: Light (`300`), Regular (`400`), Medium (`500`)

### Typografische Hierarchien & Klassen
- **Claim:**
  - Wortlaut: `TASTE THE PASSION`
  - Stil: Neue Haas Display Light, Versalien, Sperrung `0.42em`, Schriftgröße ca. `0.7rem`.
  - CSS: `.sona-claim`
- **Kicker / Rubriken:**
  - Stil: Neue Haas Display Light, Versalien, Sperrung `0.3em`, Schriftgröße ca. `0.6875rem`, Farbe Silk Beige (`#E3D5CA`).
  - CSS: `.sona-kicker`
- **Positionsnamen & Zwischenüberschriften:**
  - Stil: Neue Haas Display Medium, Versalien, Sperrung `0.18em`, Schriftgröße ca. `0.85rem`.
  - CSS: `.sona-item-title`
- **Fließtext & Beschreibungen:**
  - Stil: Durchgehend klein geschrieben (*lowercase*), ruhige Tonalität, keine Ausrufezeichen, keine Superlative.
  - Zeilenlänge: 45 bis maximal 75 Zeichen (`max-w-[68ch]`, `.sona-prose`).
- **Zahlen & Messwerte:**
  - Zahlen werden immer mit tabellarischen Ziffern formatiert: `.tabular-nums` (`font-variant-numeric: tabular-nums`).
  - Preise ohne Währungszeichen (z. B. `24` oder `7.50`).

---

## 4. Logo & Bildsprache

### Enso-Primärlogo
- Der offene Pinselkreis (Enso) in Cream Beige (`#F5ECD7`) symbolisiert handwerkliche Konzentration und japanische Ästhetik.
- **Schutzraum:** Mindestens 1/4 des Kreisdurchmessers ringsum freihalten.
- Der offene Kreis darf nie geschlossen, verzerrt oder farblich verändert werden.
- Die Wortmarke `SONA` steht im offenen Kreis auf der optischen Mittelachse.

### Bildsprache
- Fotos sind warm, ruhig und punktuell beleuchtet (2700 Kelvin Lichtstimmung).
- Gedämpfte Sättigung, kein Blitzlicht:
  ```css
  .sona-image {
      filter: brightness(0.72) contrast(1.08) saturate(0.75) sepia(0.12);
  }
  ```
- Motive: Handwerk am Tresen, Teller von oben oder in 45-Grad-Perspektive, Hände bei der Arbeit. Gäste wenn überhaupt nur unscharf im Hintergrund.

---

## 5. Single-File-Architektur für Google Sites Embed

Das gesamte Projekt ist darauf ausgelegt, als **autarke Single-File-HTML-Datei** zu funktionieren:

1. **Keine separaten lokalen Asset-Dateien:**
   - Alle Styles sind im `<style>`-Tag der `index.html` definiert (zusammen mit Tailwind via CDN).
   - Logos und Icons sind Inline-SVGs.
   - Alle Schriften werden via Google Fonts CDN geladen (`Cormorant Garamond` & `Inter`).
2. **Kein Server / Kein Backend erforderlich:**
   - Datenhaltung der Module und Lernstände erfolgt über `localStorage` (`sona_lernhub_catalog_v1` und `sona_lernhub_read_v1`).
   - Im Admin-Modus getätigte Änderungen bleiben im Browser persistent.
3. **Google Sites Integration:**
   - Ziel-Site: `https://sites.google.com/d/16Vf21bfSWX6LjTwRjgw7x20Ayi8ujc_G/p/1th87MPjxdjyDkTeEfy_J4YNje5mjH3aq/edit?pli=1`
   - Die Anwendung enthält einen Export-Assistenten (`copyFullHtmlForGoogleSites()`), der das gesamte HTML inklusive des aktuellen Bearbeitungsstands in die Zwischenablage legt, damit es in Google Sites über den Reiter „Einbetten > Einbettungscode“ eingefügt werden kann.

---

## 6. Rollen & Zugänge

- **Mitarbeiter-Modus:**
  - Code: `Sona.lernen`
  - Reines Lese-, Such- und Lernkontroll-Recht.
- **Admin-Modus:**
  - Code: `taste.the.passion`
  - Ermöglicht das Erstellen, Bearbeiten, Löschen und Neusortieren von Themen sowie das Hinzufügen von Inhaltsblöcken (Texte, Tabellen, Diagramme, Bilder, Links, Umfragen).
