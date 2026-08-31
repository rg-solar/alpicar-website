# Alpicar – Website (Entwurf)

Einfache, statische Website für **Alpicar SRL** (Eppan an der Weinstraße, Südtirol).
Aktuell **nur auf Deutsch**. Die italienische Version folgt in einem zweiten Schritt (siehe unten).

## Struktur

```
alpicar-website/
├── index.html          Startseite (Hero, Leistungen, Über uns, Kontakt)
├── impressum.html       Impressum
├── assets/
│   ├── css/style.css    gesamtes Design (Farben als CSS-Variablen in :root)
│   ├── js/main.js        Menü-Toggle, Jahr im Footer
│   └── img/              (leer – Platz für echte Fotos/Logo)
└── README.md
```

Reines HTML/CSS/JS ohne Build-Schritt – einfach die Dateien öffnen oder per
GitHub Pages hosten.

## Inhalte / offene Punkte zum Prüfen

Die Texte basieren auf den Infos aus dem E-Mail-Export und den Unterlagen im
Ordner. Bitte vor Veröffentlichung kurz gegenchecken:

- Öffnungszeiten / Terminvergabe – aktuell nur „nach Vereinbarung" formuliert.
- Impressum: Handelsregister-/REA-Nummer und ggf. Datenschutzhinweise ergänzen.
- Bilder/Logo fehlen noch (Platzhalter-Icons statt Fotos) – einfach Dateien in
  `assets/img/` legen und in `index.html` einbinden.
- Referenzkunden (z. B. Golfclubs) wurden bewusst nicht namentlich genannt,
  da im Ordner keine Freigabe dafür vorlag – kann bei Bedarf ergänzt werden.
- Logo: aus `logo/LogoAlpicar verde.pdf` freigestellt (Vektor-Version, hohe Auflösung)
  und für den dunklen Header eingefärbt (Schriftzug hell, Bergsilhouette im Original-Grün).

## Italienische Version (nächster Schritt)

Sobald die deutsche Version final ist:

1. Neuen Ordner `it/` anlegen, `index.html` und `impressum.html` hineinkopieren
   und übersetzen (Design/CSS/JS bleiben unverändert, einfach mitverlinken:
   `../assets/...`).
2. Auf jeder Seite eine Sprachumschaltung ergänzen (Link `index.html` ↔ `it/index.html`).
3. `<html lang="de">` in der IT-Version auf `lang="it"` ändern.

## Auf GitHub veröffentlichen

Lokales Repo ist bereits initialisiert (siehe `git log`). Um es auf GitHub
als neues Repository **alpicar-website** zu veröffentlichen:

```bash
# im Ordner alpicar-website ausführen
gh repo create alpicar-website --public --source=. --remote=origin --push
```

Falls `gh` nicht installiert/eingeloggt ist, alternativ über die GitHub-Weboberfläche:

1. Auf github.com ein neues, leeres Repository `alpicar-website` anlegen (ohne README).
2. Dann lokal:
   ```bash
   git remote add origin https://github.com/<dein-account>/alpicar-website.git
   git branch -M main
   git push -u origin main
   ```

### Hosting via GitHub Pages

Nach dem Push: im Repo unter **Settings → Pages** als Quelle den Branch
`main` (Ordner `/root`) auswählen. Die Seite ist danach unter
`https://<dein-account>.github.io/alpicar-website/` erreichbar.
