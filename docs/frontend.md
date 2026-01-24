---
created: 2026-01-10
modified: 2026-01-24
author: Michell Cronberg
---
# Frontend

## Hent eksempel kode

Hele frontend-koden er tilgængelig på GitHub, så du kan følge med, eksperimentere og køre applikationen lokalt.

### Clone repository

Åbn en terminal og kør:

```bash
git clone https://github.com/devcronberg/Northwind.App.Frontend.git
cd Northwind.App.Frontend
```

### Eller download som ZIP

Hvis du ikke har Git installeret, eller foretrækker at hente koden som en ZIP-fil:

1. Gå til [https://github.com/devcronberg/Northwind.App.Frontend](https://github.com/devcronberg/Northwind.App.Frontend)
2. Klik på den grønne **Code** knap
3. Vælg **Download ZIP**
4. Pak ZIP-filen ud på din computer
5. Åbn mappen i en terminal eller VS Code

### Kør applikationen

Du har flere muligheder for at køre frontend-applikationen lokalt:

**Mulighed 1: VS Code Live Server extension**

1. Højreklik på `index.html` i VS Code
2. Vælg **"Open with Live Server"** (se [setup](setup.md))
3. Browseren åbner automatisk på [http://localhost:5500](http://localhost:5500) eller lignende port.

**Mulighed 2: http-server (Node.js)**

Kræver Node.js installeret - se [setup](setup.md).

```bash
npx http-server -p 8080
```

Åbn [http://localhost:8080](http://localhost:8080) i browseren (port kan variere).

**Mulighed 3: Python**

Kræver Python installeret - se [setup](setup.md).

```bash
python -m http.server 8080
```

Åbn [http://localhost:8080](http://localhost:8080) i browseren (port kan variere).

### Live Demo

Frontend-applikationen er også deployed og tilgængelig online:

🔗 **[https://devcronberg.github.io/Northwind.App.Frontend](https://devcronberg.github.io/Northwind.App.Frontend)**

gennem Github Pages som en statisk site.

Den kommunikerer med backend API'et på:

- **Swagger**: [https://northwind-backend-b088.onrender.com/swagger](https://northwind-backend-b088.onrender.com/swagger)

!!! warning "Backend Cold Start"
    Backend API'et kører på Render.com's free tier, som automatisk "sover" efter 15 minutter uden aktivitet. Den første request efter søvn kan tage 30-50 sekunder, mens tjenesten vågner op. Dette er normalt for free-tier deployments.

## Hvad er en Frontend?

En **frontend** er den del af en webapplikation, som brugeren ser og interagerer med i browseren. Frontenden håndterer:

- **Visning**: Præsenterer data på en brugervenlig måde
- **Interaktion**: Håndterer brugerinput (klik, formularer, navigation)
- **Kommunikation**: Sender requests til backend og modtager responses
- **State Management**: Holder styr på applikationens tilstand
- **Responsivt Design**: Tilpasser sig forskellige skærmstørrelser

## Multi-Page Application (MPA)

Vores applikation er bygget som en **Multi-Page Application** – en traditionel webapplikation med separate HTML-filer for hver side:

- `index.html` - Dashboard med top customers
- `customers.html` - Customer management med CRUD operationer
- `about.html` - Om applikationen (eksempel)
- Hver side er en komplet HTML-fil
- Navigation mellem sider indlæser en ny HTML-fil
- Backend leverer data via REST API (JSON)

### Single Page Application (SPA) – Et Alternativ

Aternativet er en **SPA** (Single Page Application) er en moderne applikationsarkitektur, hvor:

- Kun **én HTML-fil** indlæses (typisk `index.html`)
- **JavaScript håndterer navigation** – ingen page refreshes
- Dynamisk opdatering af indhold uden at genindlæse siden
- **Client-side routing** – URL'er håndteres af JavaScript
- Backend leverer kun data (JSON), aldrig HTML

!!! info 
    Se evt her: https://mcronberg.github.io/web/introwebapp.html#pure-server-side-applications

#### SPA vs Multi-Page Application

| Multi-Page App (MPA)          | Single Page App (SPA)        |
| ----------------------------- | ---------------------------- |
| Flere HTML-filer              | Én HTML-fil                  |
| Server håndterer routing      | JavaScript håndterer routing |
| Page refresh ved navigation   | Ingen page refresh           |
| Simpel SEO                    | Kræver ekstra SEO-arbejde    |
| Simpel struktur               | Kræver routing-framework     |
| Hurtig initial load           | Langsommere initial load     |
| Browser-history virker native | Kræver History API           |

#### Hvordan bygges en SPA?

**Med moderne frameworks:**

En SPA bygges typisk med et JavaScript framework eller library:

| Framework/Library | Beskrivelse                                | Lærings-kurve |
| ----------------- | ------------------------------------------ | ------------- |
| **React**         | Mest populære. Component-baseret (JSX)     | Mellem        |
| **Vue.js**        | Progressiv framework. Nem at lære          | Let           |
| **Angular**       | Komplet framework fra Google. TypeScript   | Svær          |
| **Svelte**        | Compiler-baseret. Ingen virtual DOM        | Let-Mellem    |
| **Next.js**       | React framework med server-side rendering  | Mellem-Svær   |
| **Nuxt.js**       | Vue framework med SSR og static generation | Mellem        |

**Vanilla JavaScript SPA:**

Det er også muligt at bygge en SPA uden framework ved at bruge:

- **History API** - Håndter browser-historik (`pushState`, `replaceState`)
- **Fetch API** - Hent data fra backend
- **DOM Manipulation** - Opdater siden dynamisk
- **Event Listeners** - Fang navigation clicks og håndter dem med JavaScript
- **Template Literals** - Generer HTML fra JavaScript

#### Hvornår vælge SPA?

**SPA er godt når:**

- Du bygger en kompleks webapp med meget interaktion
- Brugeren navigerer meget rundt i applikationen
- Du vil have desktop-app-lignende oplevelse
- Performance efter initial load er vigtig
- Du har et dedikeret frontend-team

**Multi-Page er godt når:**

- Du bygger en simpel webapp eller website
- SEO er kritisk (nyheder, blogs, e-commerce)
- Du vil have hurtig initial load
- Du har et lille team eller begrænset JavaScript-erfaring
- Browser-kompatibilitet er vigtig (ældre browsere)

## Projektets Teknologier

### 1. **HTML5**
- Semantiske tags (`<header>`, `<main>`, `<footer>`, `<nav>`)
- Tilpassede elementer (Web Components)
- Tilgængelighed (ARIA attributter)

### 2. **CSS3**
- Flexbox og Grid layouts
- CSS variabler
- Media queries (responsivt design)
- Overgange og animationer

### 3. **JavaScript ES6+**
- Moduler (`import`/`export`)
- Arrow funktioner
- Template literals
- Destructuring
- Async/await
- Klasser

### 4. **Fomantic UI**
- CSS framework (fork af Semantic UI)
- Responsivt grid system
- Forstylede komponenter
- Ikon font
- jQuery afhængighed

### 5. **Web Components API**
- Tilpassede elementer
- Shadow DOM (valgfri)
- HTML skabeloner
- Kræver ikke et framework

### 6. **Fetch API**
- Moderne HTTP klient
- Promise-baseret
- Indbygget i browsere
- Erstatter XMLHttpRequest

### 7. **GitHub Pages**
- Gratis statisk site hosting
- Automatisk deployment via GitHub Actions
- HTTPS indbygget
- Understøttelse af tilpasset domæne

---

## Projektstruktur

Projektet er organiseret i en klar mappestruktur:

- **HTML-filer** i roden (index.html, customers.html, about.html)
- **CSS** i `css/` mappen
- **JavaScript** i `js/` mappen med undermapper for components og config
- **Assets** (ikoner, billeder) i `assets/` mappen
- **GitHub Actions** workflow i `.github/workflows/`
- **Konfigurationsfiler** i roden (package.json, eslint.config.mjs, etc.)

### Filstruktur 

**HTML filer:**
- `index.html` - Dashboard med top customers by revenue
- `customers.html` - Customer management med CRUD operationer
- `about.html` - Om applikationen (eksempel)

**CSS:**
- Fomantic UI (CDN)
- `styles.css` - Custom overrides og utilities

**JavaScript:**
- Organiseret i modules
- Components i separat folder
- Config isoleret i egen fil

## HTML Struktur

### Semantisk HTML

Vi bruger **semantiske HTML5 tags** for at give mening til strukturen:

**Semantiske tags:**
- `<header>` - Top navigation
- `<main>` - Hovedindhold (kun én per side)
- `<footer>` - Bundsektion
- `<nav>` - Navigation links
- `<section>` - Tematisk gruppering
- `<article>` - Selvstændigt indhold

### Meta Tags

**Viewport meta tag:**
- Essentiel for responsive design
- Sikrer at siden tilpasser sig enhedens bredde
- Forhindrer zoom ved load på mobile enheder

**Character encoding:**
- UTF-8 understøtter alle sprog og specialtegn
- Standard for moderne webapplikationer

### Script Loading

**ES6 Modules:**
- Brug `type="module"` attribut på script tags
- Aktiverer import/export funktionalitet
- Automatisk strict mode
- Kører efter DOM er loaded (deferred)
- Isoleret scope - ingen globale variabler

**Eksterne biblioteker:**
- jQuery indlæses fra CDN (påkrævet af Fomantic UI)
- Fomantic UI JavaScript fra CDN
- Indlæses før vores egne scripts

---

## CSS og Styling

### Fomantic UI Framework

**Fomantic UI** er et CSS framework der giver:
- Responsive grid system
- Pre-stylede komponenter
- Konsistent design language
- Icon library (>900 ikoner)

### Grid System

Fomantic UI bruger et **16-kolonne grid system**:

- Container klasse til centreret indhold med max-width
- Kolonner fra `one wide` til `sixteen wide`
- Stackable grid - kolonner stables på mobile enheder
- Automatisk responsive breakpoints

### Responsive Design

**Breakpoints:**
- Mobile: < 768px
- Tablet: 768px - 991px
- Computer: > 992px
- Large screen: > 1200px
- Widescreen: > 1920px

**Device targeting:**
- Specifikke klasser for forskellige enheder
- `mobile`, `tablet`, `computer` osv.
- Stackable grids til automatisk mobil-layout

### Komponenter

**Buttons:**
- Primary, secondary, colored variants
- Forskellige størrelser
- Icon buttons
- Loading states

**Tables:**
- Celled, striped, compact varianter
- Selectable rows
- Sortable headers
- Responsive på mobile

**Forms:**
- Strukturerede form layouts
- Input validation styling
- Error og success states
- Inline og stacked layouts

**Messages og Alerts:**
- Success, warning, error, info
- Dismissable
- Med headers og ikoner

### Icons

Fomantic UI inkluderer et stort icon library:
- Over 900 ikoner
- Forskellige størrelser (small, large, huge)
- Farvevarianter
- Bruges til navigation, buttons, headers

### Custom CSS

Vores tilpassede styling:

**CSS Variables:**
- Defineret i `:root`
- Farver, størrelser, spacing
- Let at ændre tema

**Layout:**
- Flexbox til page layout
- Sticky header
- Footer i bunden
- Main content fylder tilgængelig plads

**Utilities:**
- Responsive helpers
- Spacing utilities
- Text alignment
- Display helpers

---

## JavaScript og ES6+ Modules

### Module System

**ES6 Modules** giver os:
- Import/export functionality
- Organiseret kode i separate filer
- Ingen global scope pollution
- Tree-shaking (unused code removal)

**Named exports:**
- Eksporter flere items fra samme fil
- Import med curly braces
- Kan omdøbes ved import

**Default exports:**
- Én default export per fil
- Import uden curly braces
- Bruges til hovedfunktionalitet

### Moderne JavaScript Features

**Arrow Functions:**
- Kortere syntaks
- Lexical `this` binding
- Implicit return for simple funktioner

**Template Literals:**
- String interpolation med `${}`
- Multi-line strings
- Bruges til HTML generation

**Destructuring:**
- Udtræk værdier fra objekter og arrays
- Med default værdier
- I function parameters

**Spread Operator:**
- Kopier arrays og objekter
- Kombiner arrays
- Merge objekter

**Async/Await:**
- Moderne håndtering af asynkrone operationer
- Erstatter `.then()` callbacks
- Bedre error handling med try/catch
- Mere læsbar kode

**Classes:**
- Syntaktisk sukker over prototyper
- Constructor og methods
- Extends til inheritance
- Bruges til Web Components

---

## Web Components

### Hvad er Web Components?

**Web Components** er en browser standard til at lave reusable, encapsulated custom HTML elements.

**Fordele:**
- ✅ No framework needed
- ✅ Browser native
- ✅ Reusable across projects
- ✅ Encapsulated (styles og logic isolated)
- ✅ Standard-based (ikke vendor-locked)

**Core Technologies:**
1. **Custom Elements** - Define nye HTML tags
2. **Shadow DOM** - Encapsulated DOM/CSS (valgfrit)
3. **HTML Templates** - Reusable markup
4. **ES Modules** - Component imports

### Custom Elements API

**Opbygning af en Web Component:**
- Extend `HTMLElement` klassen
- Definer constructor for initial setup
- Implementer lifecycle callbacks
- Registrer komponenten med `customElements.define()`

**Lifecycle callbacks:**
- `constructor()` - Element oprettes
- `connectedCallback()` - Tilføjes til DOM
- `disconnectedCallback()` - Fjernes fra DOM
- `attributeChangedCallback()` - Attribut ændres
- `adoptedCallback()` - Flyttes til nyt dokument

### Vores Web Components

**App Header Component:**
- Fælles navigation på alle sider
- Bruges med `<app-header></app-header>`
- Indeholder logo og menu links
- Fixed position i toppen

**App Footer Component:**
- Fælles footer på alle sider
- Copyright og links
- Dynamisk år (altid current year)

**Customer Revenue Table:**
- Viser top customers by revenue
- Accepterer `limit` attribut
- Henter data fra API
- Loading states og error handling

**Customer Table:**
- Full CRUD funktionalitet
- Tabel med edit og delete knapper
- Event delegation for dynamiske elementer
- Form til oprettelse og redigering

**Form Text Input:**
- Reusable form input komponent
- Label, input, validation
- Attribut-baseret konfiguration

**Fordele ved Web Components:**
- Reusable på alle sider
- Én kodeændring opdaterer alle steder
- Clean HTML markup
- Encapsulated functionality
- Standard-baseret (ingen framework låsning)

## Progressive Web App (PWA)

Applikationen er bygget som en **Progressive Web App**, hvilket betyder at den kan installeres på både desktop og mobile enheder og fungere som en native app.

### Hvad er en PWA?

En **Progressive Web App** er en webapplikation, der bruger moderne web-teknologier til at levere en app-lignende oplevelse:

**Fordele:**
- 📱 **Installerbar** - Kan installeres på hjemmeskærmen
- 🚀 **Hurtig** - Optimeret loading og performance
- 🎨 **App-lignende** - Åbnes i eget vindue uden browser UI
- 🔔 **Engagerende** - Kan bruge push notifications (hvis implementeret)
- 📴 **Offline** - Kan fungere uden internetforbindelse (hvis cache implementeret)
- 🔄 **Altid opdateret** - Automatisk opdateringer via service worker

### PWA Krav

For at være en valid PWA skal applikationen opfylde:

1. ✅ **HTTPS** - Serveret over sikker forbindelse
2. ✅ **Web App Manifest** - `manifest.json` fil
3. ✅ **Service Worker** - Registreret og aktiv
4. ✅ **Responsive** - Fungerer på alle skærmstørrelser
5. ✅ **App Icons** - Ikoner i forskellige størrelser

### Installation af PWA

**På Desktop (Chrome/Edge):**

1. Åbn applikationen i browseren
2. Klik på install-ikonet i adresselinjen (⊕ symbol)
3. Eller klik på "..." menu → "Install Northwind Traders"
4. Appen åbnes i et selvstændigt vindue uden browser chrome

**På Mobile (Android):**

1. Åbn applikationen i Chrome
2. Tryk på menu (⋮) → "Add to Home Screen"
3. Eller følg install-prompt nederst på siden
4. Appen vises som et ikon på hjemmeskærmen

**På Mobile (iOS):**

1. Åbn applikationen i Safari
2. Tryk "Share" knappen (◻↑)
3. Vælg "Add to Home Screen"
4. Appen vises som et ikon på hjemmeskærmen

### PWA vs Native Apps

| Feature           | PWA                    | Native App       |
| ----------------- | ---------------------- | ---------------- |
| Installation      | Via browser            | App Store        |
| Distribution      | URL link               | App Store review |
| Opdateringer      | Automatisk             | App Store update |
| Størrelse         | Meget lille            | Større download  |
| Offline           | Kan implementeres      | Standard         |
| Platform          | Cross-platform         | Per platform     |
| Udvikling         | Web tech (HTML/CSS/JS) | Native code      |
| Adgang til device | Begrænset              | Fuld adgang      |
| Performance       | God                    | Bedre            |
| Cost              | Lavere                 | Højere           |

**Hvornår vælge PWA:**
- Cross-platform deployment vigtig
- Hurtig time-to-market
- Frequent updates nødvendige
- Begrænset budget
- Web-baseret content

**Hvornår vælge Native:**
- Høj performance kritisk
- Dyb device integration nødvendig
- Kompleks offline funktionalitet
- Platform-specifik UI vigtig
- App Store distribution foretrukket

---

## Fetch API og REST Integration

### Fetch API

Moderne JavaScript API til HTTP requests:

**Fordele:**
- Promise-baseret
- Indbygget i browsere
- Cleaner syntaks end XMLHttpRequest
- Understøtter async/await

**Response håndtering:**
- `response.ok` - Check for success (200-299)
- `response.status` - HTTP status code
- `response.json()` - Parse JSON body
- `response.text()` - Få raw text

### HTTP Methods og CRUD

Vores applikation bruger REST API med standard HTTP methods:

**GET - Hent data:**
- Læs liste af customers
- Læs enkelt customer
- Query parameters til filtering og pagination

**POST - Opret ny:**
- Opret ny customer
- Send JSON i request body
- Content-Type header: application/json

**PUT - Opdater eksisterende:**
- Opdater customer data
- Send hele objektet i body
- Identificer med ID i URL

**DELETE - Slet:**
- Slet customer
- ID i URL
- Confirmation dialog til brugeren

### Request Headers

**Content-Type:**
- `application/json` for JSON data
- Fortæller serveren hvad vi sender

**Authorization:**
- Ville indeholde JWT token (ikke implementeret i vores demo)
- Format: `Bearer <token>`

### Error Handling

**Strategier:**
- Try/catch omkring fetch calls
- Check `response.ok` før parsing
- User-friendly error beskeder
- Fallback UI ved fejl
- Console logging til debugging

**Fejltyper:**
- Network errors (ingen forbindelse)
- HTTP errors (404, 500, etc.)
- Parsing errors (invalid JSON)
- Timeout errors

### Loading States

**Visuelt feedback:**
- Spinner/loader mens data hentes
- Disable buttons under submit
- Skeleton screens
- Progress indicators

**UI States:**
1. Initial state (tom/placeholder)
2. Loading state (spinner vises)
3. Success state (data vises)
4. Error state (fejlbesked vises)

### Query Parameters

**Pagination:**
- `take` - Antal records
- `skip` - Antal at springe over

**Filtering:**
- `country` - Filtrer efter land
- `city` - Filtrer efter by

**Sorting:**
- `orderBy` - Sorter efter felt
- `ascending` - Sorteringsretning

**URL konstruktion:**
- URLSearchParams hjælper
- String interpolation
- Encoding af special characters

---

## Code Quality Tools

### ESLint - JavaScript Linting

**ESLint** analyserer JavaScript-kode for fejl og style issues.


**Common rules:**
- `no-unused-vars` - Warn about unused variables
- `no-console` - Disallow console.log (off in dev)
- `semi` - Require semicolons
- `quotes` - Enforce single quotes
- `indent` - Enforce consistent indentation
- `no-undef` - Disallow undefined variables

### HTMLHint - HTML Validation

**HTMLHint** checker HTML for fejl og best practices.

**Run HTMLHint:**
```bash
npm run lint:html
```

**Common rules:**
- `tagname-lowercase` - `<DIV>` → `<div>`
- `attr-value-double-quotes` - `href='...'` → `href="..."`
- `tag-pair` - Check closing tags
- `id-unique` - No duplicate IDs
- `doctype-first` - <!DOCTYPE html> first

### Stylelint - CSS Linting

**Stylelint** analyserer CSS for fejl og conventions.

**Run Stylelint:**
```bash
npm run lint:css
```

**Common rules:**
- `color-hex-case` - `#FFF` → `#fff`
- `color-hex-length` - `#ffffff` → `#fff`
- `indentation` - Enforce consistent indentation
- `no-duplicate-selectors` - Warn about duplicates
- `declaration-block-trailing-semicolon` - Require semicolons

### Lint All

**Run all linters:**
```bash
npm run lint
```

## GitHub Actions og Deployment

### Continuous Deployment

**GitHub Actions** automatiserer deployment:

1. Push code til GitHub
2. Workflow triggers
3. Install dependencies
4. Run linting
5. Deploy til GitHub Pages

---

## TypeScript som Alternativ til JavaScript

**TypeScript** er et programmeringssprog udviklet af Microsoft, der bygger ovenpå JavaScript ved at tilføje statisk typning.

### Hvad er TypeScript?

TypeScript kompileres til almindelig JavaScript, men giver udvikleren mulighed for at definere typer på variabler, funktioner og objekter:

```typescript
// JavaScript
function greet(name) {
  return "Hello " + name;
}

// TypeScript
function greet(name: string): string {
  return "Hello " + name;
}
```

### Fordele ved TypeScript

- **Type Safety** - Fang fejl ved kompilering i stedet for runtime
- **Bedre IDE support** - Autocomplete, refactoring og inline dokumentation
- **Større projekter** - Lettere at vedligeholde og refaktorere kompleks kode
- **API klienter** - Automatisk generering fra OpenAPI/Swagger med fuld type safety
- **Teamwork** - Typer fungerer som dokumentation og kontrakter mellem komponenter

### Ulemper ved TypeScript

- **Læringskurve** - Kræver forståelse af type system
- **Ekstra kompleksitet** - Build step og konfiguration nødvendig
- **Mindre fleksibilitet** - JavaScript's dynamiske natur begrænses
- **Overkill for små projekter** - Overhead kan overstige fordele i simple applikationer
- **Compile time** - Ekstra step mellem kode og resultat

### Hvornår bruge TypeScript?

**TypeScript er smart når:**
- Du arbejder i et team med flere udviklere
- Projektet er stort eller forventes at vokse
- Du integrerer med eksterne API'er (type safety fra OpenAPI/Swagger)
- Lang vedligeholdelsesperiode

**JavaScript er nok når:**
- Små prototyper eller proof-of-concepts
- Hurtig udvikling og eksperimentering er prioritet
- Teamet har begrænset TypeScript erfaring
- Projektet er simpelt og overskueligt

---

## Hvad mangler i en produktionsapplikation?

Dette er en uddannelsesapplikation. I en professionel produktionsapplikation ville du også overveje:

- **Tests** - Unit tests, integration tests og end-to-end tests
- **Sikkerhed** - Input validering, XSS beskyttelse, Content Security Policy
- **Performance** - Caching strategi, lazy loading, code splitting, asset optimization
- **Error tracking** - Centraliseret logging og monitoring (f.eks. Sentry)
- **Environment management** - Adskillelse af development, staging og production
- **Build process** - Minification, bundling og optimering af assets

