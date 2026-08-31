# Alpicar – Website (zwei Entwürfe zur Auswahl)

Statische Website für **Alpicar SRL** (Eppan an der Weinstraße, Südtirol).
Aktuell **nur auf Deutsch**. Die italienische Version folgt, sobald ein
Entwurf final ist (siehe unten).

## Struktur

```
alpicar-website/
├── index.html            Auswahlseite: verlinkt beide Entwürfe zum Vergleich
├── entwurf-1/             Dunkles, premium Design (Icons, ruhige Karten)
│   ├── index.html
│   ├── impressum.html
│   └── assets/
├── entwurf-2/             Helles "Alpin"-Design (Foto-Platzhalter, Marken-Übersicht)
│   ├── index.html
│   ├── impressum.html
│   └── assets/
└── README.md
```

Reines HTML/CSS/JS ohne Build-Schritt. Zum Vergleichen einfach
`index.html` im Browser öffnen und zwischen den beiden Entwürfen klicken.

## Die beiden Entwürfe im Überblick

- **Entwurf 1** — dunkel, Akzentfarbe Grün (aus dem Logo), vier Leistungs-
  Karten mit Icons, kompakt und ruhig.
- **Entwurf 2** — hell/warm ("Alpin"-Anmutung), zusätzlich: eine
  Marken-/Lieferanten-Übersicht (Reifenmarken + Fahrzeugmarken als
  Text-Badges) sowie Foto-Platzhalter in Hero, Leistungskarten, Über-uns
  und Kontakt.

Sobald ihr euch für einen entschieden habt, entferne ich den anderen
Entwurf und hebe den gewählten auf die oberste Ebene (`index.html` direkt
im Repo-Root statt der Auswahlseite).

## Inhalte / offene Punkte zum Prüfen

- Öffnungszeiten / Terminvergabe – aktuell nur „nach Vereinbarung" formuliert.
- Impressum: Handelsregister-/REA-Nummer und ggf. Datenschutzhinweise ergänzen.
- Echte Fotos fehlen noch (Platzhalter markiert mit "Foto folgt") – einfach
  Dateien in `entwurf-x/assets/img/` legen und im jeweiligen `index.html`
  gegen den `.photo-placeholder`-Block austauschen.
- Marken-Logos in Entwurf 2 sind aktuell **Text-Badges**, keine echten
  Logo-Dateien der Hersteller (Michelin, Pirelli, Porsche usw.) – dafür
  bräuchte es offizielle Logo-Freigaben/-Dateien der jeweiligen Marken
  (z. B. aus Händlerunterlagen), sonst Vorsicht wegen Markenrechten.
- Logo: aus `logo/LogoAlpicar verde.pdf` freigestellt (Vektor-Version, hohe
  Auflösung) – helle Variante für Entwurf 1 (dunkler Header), dunkle
  Variante für Entwurf 2 (heller Header).
- Referenzkunden (z. B. Golfclubs) wurden bewusst nicht namentlich genannt,
  da im Ordner keine Freigabe dafür vorlag – kann bei Bedarf ergänzt werden.

## Italienische Version (nächster Schritt)

Sobald ein Entwurf final ist:

1. Neuen Ordner `it/` im gewählten Entwurf anlegen, `index.html` und
   `impressum.html` hineinkopieren und übersetzen (Design/CSS/JS bleiben
   unverändert, einfach mitverlinken: `../assets/...`).
2. Auf jeder Seite eine Sprachumschaltung ergänzen (Link `index.html` ↔ `it/index.html`).
3. `<html lang="de">` in der IT-Version auf `lang="it"` ändern.

## Auf GitHub veröffentlichen

Lokales Repo ist bereits initialisiert (siehe `git log`). Um es auf GitHub
als neues Repository **alpicar-website** zu veröffentlichen (im Ordner
`alpicar-website` ausführen):

```bash
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
`main` (Ordner `/root`) auswählen. Die Auswahlseite ist danach unter
`https://<dein-account>.github.io/alpicar-website/` erreichbar.
