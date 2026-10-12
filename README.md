# AWO Brief- & Urkunden-Generator

Ein moderner, modularer Web-Generator zur Erstellung von DIN-5008-konformen Geburtstagsbriefen und Ehrenurkunden aus CSV-Mitgliederlisten. Speziell entwickelt für die **AWO Oberlar e. V.**

---

## 🌟 Features

- **DIN 5008 Konformität**: Exakte Platzierung des Anschriftfeldes für DL-Fensterumschläge, inklusive Falz- und Lochmarken auf A4-Format.
- **100% Code-Freie Vorlagen (No-Code Templates)**: Neue Vorlagen (wie Urkunden, Bestätigungen oder Briefe) können rein deklarativ über die `templates.json` registriert werden.
- **Live-Textanpassung**: Betreffzeile und Textabsätze können direkt im Web-Interface vor der PDF-Erstellung live editiert werden.
- **Benutzerfreundliche Platzhalter**: Automatische Grammatikanpassung (z. B. `[Dir/Ihnen]`, `[Dein/Ihr]`, `[erhältst/erhalten]`) passend zur Briefanrede (Du-Form vs. Sie-Form).
- **Dynamisches Interface-Branding (Theme Sync)**: Die Benutzeroberfläche passt ihre Farben (z. B. Rot für Geburtstage, Gold für Urkunden) dynamisch an das ausgewählte Template an.

---

## 🛠️ Technologie-Stack

- **Frontend & Backend**: Next.js (React) mit API Routes für CSV-Parsing und PDF-Generierung.
- **PDF-Rendering**: `@react-pdf/renderer` – vollständig serverseitig, keine externen Dienste.
- **Containerisierung**: Docker & Docker Compose.

---

## 🏗️ Systemarchitektur

```mermaid
graph TD
    A[Next.js Web-Interface] -->|1. CSV hochladen & Text anpassen| B[Next.js API Routes]
    B -->|2. CSV-Parsing & Encoding-Erkennung| C[csvParser]
    B -->|3. Grammatik-Ersetzung & PDF-Rendering| D[@react-pdf/renderer]
    D -->|4. PDF-Stream| B
    B -->|5. PDF-Download im Browser| A
```

---

## 🚀 Installation & Start

### Voraussetzungen
- **Node.js** (v18+)

---

### 💻 Start (Empfohlen)

```bash
npm install
npm run dev
```

Die App ist unter `http://localhost:3000` erreichbar. Beenden mit `Ctrl + C`.

---

### 🐳 Starten mit Docker (Alternativ)

```bash
docker-compose up --build
```

---

## 📁 CSV-Struktur & Pflichtspalten

Je nach gewähltem Template werden unterschiedliche Spalten in der hochgeladenen CSV-Datei benötigt:

### 1. Standard-Geburtstagsbrief (`birthday_standard`)
Die Tabelle muss folgende Spaltennamen enthalten:
- `Vorname`
- `Nachname`
- `Briefanrede` (z. B. *Lieber Daniel*, *Sehr geehrte Frau Müller*)
- `Geburtsdatum` (Format: `TT.MM.JJJJ`)
- `Straße`
- `Postleitzahl`
- `Ort`

### 2. Urkunde (`urkunde_standard`)
Erfordert lediglich:
- `Vorname`
- `Nachname`
- `Briefanrede` (Optional, für die dynamische Anrede `[Dir/Ihnen]`)

---

## 📄 Lizenz
Dieses Projekt ist lizenziert unter der MIT-Lizenz.