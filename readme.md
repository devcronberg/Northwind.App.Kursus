# Byg en moderne webapplikation med C#

Dette projekt indeholder dokumentation og vejledninger til webinaret "Byg en moderne webapplikation med C#" afholdt for Prosa i 2026.

## Om projektet

Dokumentationen er bygget med MkDocs Material og indeholder artikler og vejledninger, der understøtter webinarforløbet, hvor deltagerne lærer at bygge en komplet, moderne webapplikation med C# og ASP.NET Core MVC.

## Teknologier

### MkDocs

MkDocs er en hurtig og simpel generator til statiske websites, specielt designet til projektdokumentation. Dokumentationen skrives i Markdown-format, og MkDocs konverterer disse filer til et komplet, statisk website.

### Material for MkDocs

Material for MkDocs er et populært og moderne tema til MkDocs, der giver en professionel og responsiv brugerflade. Temaet inkluderer mange avancerede funktioner som mørk tilstand, navigation, søgning og kodehøjdning.

### Plugins

Projektet bruger følgende plugins:

- **mkdocs-awesome-pages-plugin**: Giver bedre kontrol over navigation og siderækkefølge
- **mkdocs-video**: Understøtter indlejring af videoer direkte i dokumentationen
- **mkdocs-document-dates**: Viser oprettelses- og ændringsdatoer for sider
- **pymdown-extensions**: Tilføjer ekstra Markdown-funktioner som admonitions, tabeller og kodehøjdning

## Installation

### Forudsætninger

- Python 3.8 eller nyere
- pip (Python package manager)

### Trin for trin

1. Klon repository:
   ```bash
   git clone https://github.com/devcronberg/Northwind.App.Kursus.git
   cd Northwind.App.Kursus
   ```

2. Installér nødvendige pakker:
   ```bash
   pip install -r requirements.txt
   ```

3. Start den lokale udviklingsserver:
   ```bash
   mkdocs serve
   ```

4. Åbn din browser og gå til `http://127.0.0.1:8000`

Dokumentationen opdateres automatisk, når du gemmer ændringer i markdown-filerne.

## Byg statisk website

For at bygge det statiske website til produktion:

```bash
mkdocs build
```

Dette opretter en `site/` mappe med alle de nødvendige HTML-, CSS- og JavaScript-filer.

## Struktur

```
.
├── mkdocs.yml           # Konfigurationsfil for MkDocs
├── requirements.txt     # Python-afhængigheder
├── docs/               # Dokumentationsfiler (Markdown)
│   ├── index.md
│   ├── setup.md
│   ├── backend.md
│   ├── frontend.md
│   └── assets/         # Statiske ressourcer (CSS, JS)
└── overrides/          # Tilpassede templates
```

## Læs mere

- [MkDocs dokumentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Markdown Guide](https://www.markdownguide.org/)

## Forfatter

Michell Cronberg
