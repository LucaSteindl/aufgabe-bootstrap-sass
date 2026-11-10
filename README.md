# Studio Orange – Bootstrap & Sass

Responsive Testseite für die Übung **Webdevelopment Toolchain**. Das Projekt verwendet ein modulares Bootstrap-Setup, eigene Sass-Stile und Bootstrap Icons. npm-Scripts kompilieren das Stylesheet und starten einen Entwicklungsserver mit Live-Reload.

## Voraussetzungen

- Node.js ab **20.19.0**, inklusive npm. Getestet mit Node.js **24.21.0** und npm **12.2.2**.
- Git zum Klonen des Repositorys.
- Ein Browser und optional Visual Studio Code.

Die folgenden Befehle werden in PowerShell oder einem anderen Terminal ausgeführt.

## Installation

1. Auf GitHub dieses Repository öffnen, auf **Code → HTTPS** klicken und die Repository-URL kopieren.
2. In den gewünschten übergeordneten Ordner wechseln. Das Repository mit der kopierten URL klonen; `REPOSITORY-URL` ist ein Platzhalter und muss ersetzt werden:

   ```sh
   git clone REPOSITORY-URL bootstrap-sass-project
   cd bootstrap-sass-project
   ```

3. Die Produktions- und Entwicklungs-Abhängigkeiten installieren:

   ```sh
   npm install
   ```

   Alternativ installiert `npm ci` exakt die im mitgelieferten `package-lock.json` festgehaltenen Versionen.

4. Sass einmalig kompilieren:

   ```sh
   npm run scss:build
   ```

5. Den lokalen Server starten:

   ```sh
   npm run serve
   ```

   BrowserSync öffnet normalerweise den Browser unter `http://localhost:3000`. Falls der Port belegt ist, die im Terminal ausgegebene lokale Adresse verwenden.

Das Repository wird zunächst lokal verwaltet. Der Platzhalter oben kann nach dem Hochladen durch die tatsächliche GitHub-URL ersetzt werden.

## Entwicklung und Befehle

Alle Befehle müssen im Projektordner mit der `package.json` ausgeführt werden.

| Befehl | Funktion |
| --- | --- |
| `npm run scss:build` | Kompiliert `src/scss/style.scss` einmalig nach `dist/css/style.css`. |
| `npm run scss:watch` | Überwacht den Sass-Ordner und kompiliert Änderungen automatisch. |
| `npm run serve` | Startet BrowserSync und überwacht HTML sowie das kompilierte CSS. |

Für den vollständigen Live-Reload-Workflow zwei Terminals im selben Projektordner öffnen:

**Terminal 1:**

```sh
npm run scss:watch
```

**Terminal 2:**

```sh
npm run serve
```

Texte in `index.html` bearbeiten oder beispielsweise `$primary` in `src/scss/style.scss` ändern und speichern. Sass erzeugt bei Sass-Änderungen neues CSS; BrowserSync übernimmt CSS-Änderungen und lädt bei HTML-Änderungen die Seite neu. Beide Prozesse werden jeweils mit **Strg+C** beendet.

Die aktuelle Bootstrap-Version verwendet Sass-Syntax, für die der Compiler Veraltungshinweise ausgibt. Die Kompilierung funktioniert trotzdem.

## Projektstruktur

```text
bootstrap-sass-project/
├── src/
│   └── scss/
│       └── style.scss
├── dist/
│   └── css/
│       └── style.css
├── .gitignore
├── index.html
├── package.json
├── package-lock.json
└── README.md
```

## Gestaltung

- Responsives Bootstrap-Raster mit `container`, `row` und `col-md-6`.
- Eigene Primärfarbe und zusätzliche Stile in Sass.
- Modulare Bootstrap-Imports für die benötigten Komponenten und Utilities.
- Mehrere Button-Varianten und Bootstrap Icons, unter anderem Rakete, Raster und Palette.
- Navigation über Links zu den Abschnitten der Testseite.

## Versionsverwaltung

`node_modules/`, CSS-Source-Maps und `.DS_Store` werden durch `.gitignore` ausgeschlossen. Die Abhängigkeiten werden nach dem Klonen über npm wiederhergestellt. `package-lock.json` und das fertige `dist/css/style.css` bleiben im Repository.

Die Icon-Schriftdateien werden aus `node_modules/bootstrap-icons/font/fonts` geladen. Deshalb ist `npm install` auch dann erforderlich, wenn das fertige CSS bereits vorhanden ist. Für die Vorschau wird `npm run serve` verwendet.

Autor: Luca
