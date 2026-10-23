# SONA Lernhub — Japanese Sushi & Kitchen Bar

Interne digitale Lernplattform, Wissensdatenbank und Schulungsportal für Küche, Tresen, Bar und Service.

---

## ⛩️ Übersicht

Der **SONA Lernhub** bündelt alle verbindlichen Markenwerte, Leitfäden, Warenkunden, Serviceabläufe und Schulungen der *SONA Japanese Sushi & Kitchen Bar*.

Die Anwendung ist als hochgradig optimierte **Single-File-Webanwendung** konzipiert, die sich ohne externe Build-Tools, Node-Server oder komplexe Deployments direkt öffnen oder nahtlos als HTML-Code in **Google Sites** einbetten lässt.

---

## 🔒 Zugangsdaten (Authentifizierung)

Der Lernhub schützt interne Abläufe durch eine vorgeschaltete Code-Abfrage:

| Rolle | Zugangscode | Berechtigungen |
| :--- | :--- | :--- |
| **Mitarbeiter** | `Sona.lernen` | Volltextsuche, Lesen aller Kapitel, Absolvieren von Wissens-Checks & Lernkontrollen, Fortschritts-Tracking |
| **Administrator** | `taste.the.passion` | Alle Mitarbeiter-Funktionen + Inhaltsverzeichnis verwalten, Module erstellen/editieren/löschen/verschieben, Inhaltsblöcke anlegen (Texte, Tabellen, Diagramme, Bilder, Links, Umfragen) |

*Hinweis: Auf dem Anmeldebildschirm steht für Test- und Präsentationszwecke zudem eine Direktwahl für beide Rollen zur Verfügung.*

---

## 🎨 Strenge Design-Regeln (SONA Brand Guidelines)

Gemäß der verbindlichen SONA-Markenidentität gelten absolute Design-Vorgaben:

1. **5 Farben (keine sechste):**
   - Brand Black: `#000000`
   - Charcoal Grey: `#121212`
   - Deep Grey: `#191919`
   - Cream Beige: `#F5ECD7`
   - Silk Beige: `#E3D5CA`
2. **Keine Schatten:** `box-shadow: none !important`, `text-shadow: none !important`.
3. **Keine Verläufe:** Alle Flächen und Hintergründe sind plan und monochrom.
4. **Keine Emojis:** Weder in Texten noch in der Benutzeroberfläche; stattdessen feine typografische Glyphen (`→`, `←`), Versalien-Kicker oder dezente SVG-Vektorlinien.
5. **Typografie:**
   - **Display / Überschriften:** Audrey (Web-Äquivalent: *Cormorant Garamond*, Versalien mit Sperrung `0.08em` bis `0.12em`).
   - **Fließtext / UI:** Neue Haas Display (Web-Äquivalent: *Inter* / *Helvetica Neue*).
   - **Claim:** Neue Haas Display Light, Versalien, Sperrung `0.42em` (`TASTE THE PASSION`).
   - **Kicker / Rubriken:** Versalien, Sperrung `0.3em`.
   - **Fließtext:** Durchgehend klein geschrieben (*lowercase*), 45 bis 75 Zeichen Zeilenlänge (`sona-prose`).
   - **Tabellarische Ziffern:** `tabular-nums` für Preise, Zeiten und Kennzahlen.

---

## 🌐 Live-URL & Google Sites Einbindung

- **Live-Webadresse (GitHub Pages):** [https://jhelmeke97-cyber.github.io/sona-lernhub/](https://jhelmeke97-cyber.github.io/sona-lernhub/)
- **Google Sites Editor:** [Google Sites Editor öffnen](https://sites.google.com/d/16Vf21bfSWX6LjTwRjgw7x20Ayi8ujc_G/p/1th87MPjxdjyDkTeEfy_J4YNje5mjH3aq/edit?pli=1)

### Einmalige Einbindung in Google Sites (mit automatischer Aktualisierung):
1. Öffne die Seite im [Google Sites Editor](https://sites.google.com/d/16Vf21bfSWX6LjTwRjgw7x20Ayi8ujc_G/p/1th87MPjxdjyDkTeEfy_J4YNje5mjH3aq/edit?pli=1).
2. Klicke rechts unter **Einfügen** auf **Einbetten** (oder bearbeite das bestehende Embed-Feld).
3. Wähle den Reiter **„Nach URL“** (nicht „Einbettungscode“).
4. Füge die Live-Adresse ein:
   ```
   https://jhelmeke97-cyber.github.io/sona-lernhub/
   ```
5. Ziehe den Rahmen auf die volle Seitenbreite und klicke oben rechts auf **Veröffentlichen**.
6. **Fertig!** Ab sofort synchronisieren sich alle zukünftigen `git push`-Änderungen vollautomatisch auf deiner Google Sites Seite!

---

## 📁 Dateistruktur

```
Sona-Lernhub/
├── index.html        # Vollständige autarke Single-File-Anwendung (HTML5, Tailwind, JS, SVGs)
├── GEMINI.md         # Feste Gestaltungs- und Entwicklungsregeln für KI-Assistenten
├── README.md         # Projekt-Dokumentation & Bedienungsanleitung
└── .gitignore        # Ausschluss von Betriebssystem- & Editor-Dateien
```

---

## 🚀 Lokale Nutzung

Die `index.html` benötigt keinen Build-Prozess. Sie kann per Doppelklick in jedem modernen Webbrowser geöffnet oder über einen simplen HTTP-Server bereitgestellt werden:

```bash
# Python
python -m http.server 8080

# Oder mit Node.js / npx
npx serve .
```

Anschließend im Browser aufrufen unter `http://localhost:8080`.
