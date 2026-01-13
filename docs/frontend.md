---
created: 2026-01-10
modified: 2026-01-10
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
2. Vælg **"Open with Live Server"**
3. Browseren åbner automatisk på [http://localhost:5500](http://localhost:5500)

**Mulighed 2: http-server (Node.js)**

```bash
npx http-server -p 8080
```

Åbn [http://localhost:8080](http://localhost:8080) i browseren.

**Mulighed 3: Python**

```bash
python -m http.server 8080
```

Åbn [http://localhost:8080](http://localhost:8080) i browseren.

### Live Demo

Frontend-applikationen er også deployed og tilgængelig online:

🔗 **[https://devcronberg.github.io/Northwind.App.Frontend](https://devcronberg.github.io/Northwind.App.Frontend)**

Den kommunikerer med backend API'et på:

- **Backend**: [https://northwind-backend-b088.onrender.com](https://northwind-backend-b088.onrender.com)
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
- Hver side er en komplet HTML-fil
- Navigation mellem sider indlæser en ny HTML-fil
- Backend leverer data via REST API (JSON)

### Web Components til Genbrug

Selvom vi har flere HTML-sider, genbruger vi kode via **Web Components**:

- `<app-header>` - Fælles header på alle sider
- `<app-footer>` - Fælles footer på alle sider
- `<customer-table>` - Tabel-komponent til kunde-visning
- `<customer-revenue-table>` - Dashboard-tabel
- `<form-text-input>` - Genanvendelig form-input

Web Components giver os **modulær og genanvendelig kode** uden behov for et framework.

### Single Page Application (SPA) – Et Alternativ

En **SPA** (Single Page Application) er en moderne applikationsarkitektur, hvor:

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
- Custom Elements (Web Components)
- Accessibility (ARIA attributes)

### 2. **CSS3**
- Flexbox og Grid layouts
- CSS Variables
- Media queries (responsive design)
- Transitions og animations

### 3. **JavaScript ES6+**
- Modules (`import`/`export`)
- Arrow functions
- Template literals
- Destructuring
- Async/await
- Classes

### 4. **Fomantic UI**
- CSS framework (fork af Semantic UI)
- Responsive grid system
- Pre-stylede komponenter
- Icon font
- jQuery dependency

### 5. **Web Components API**
- Custom Elements
- Shadow DOM (optional)
- HTML Templates
- No framework needed

### 6. **Fetch API**
- Modern HTTP client
- Promise-based
- Built into browsers
- Erstatter XMLHttpRequest

### 7. **GitHub Pages**
- Gratis static site hosting
- Automatisk deployment via GitHub Actions
- HTTPS built-in
- Custom domain support

---

## Projektstruktur

```
Northwind.App.Frontend/
├── index.html                    # Dashboard side
├── customers.html                # Customer management side
├── package.json                  # NPM dependencies og scripts
├── eslint.config.mjs             # ESLint konfiguration
├── .htmlhintrc                   # HTMLHint konfiguration
├── .stylelintrc.json             # Stylelint konfiguration
├── assets/
│   └── favicon.svg               # App ikon
├── css/
│   └── styles.css                # Custom styling
├── js/
│   ├── app.js                    # Application entry point
│   ├── config/
│   │   └── settings.js           # API og app konfiguration
│   └── components/
│       ├── app-header.js         # Header komponent
│       ├── app-footer.js         # Footer komponent
│       ├── customer-table.js     # Customer liste tabel
│       ├── customer-revenue-table.js  # Revenue dashboard tabel
│       └── form-text-input.js    # Reusable form input
└── .github/
    └── workflows/
        └── deploy.yml            # GitHub Actions workflow
```

### Filstruktur forklaret

**HTML filer:**
- `index.html` - Dashboard med top customers by revenue
- `customers.html` - Customer management med CRUD operationer

**CSS:**
- Fomantic UI (CDN)
- `styles.css` - Custom overrides og utilities

**JavaScript:**
- Organiseret i modules
- Components i separat folder
- Config isoleret i egen fil

---

## HTML Struktur

### Semantisk HTML

Vi bruger **semantiske HTML5 tags** for at give mening til strukturen:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Northwind Traders</title>
    
    <!-- Fomantic UI -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/fomantic-ui@2.9.3/dist/semantic.min.css">
    
    <!-- Custom CSS -->
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <!-- Header Component -->
    <app-header></app-header>

    <!-- Main Content -->
    <main class="main-content">
        <div class="ui container">
            <!-- Page content -->
        </div>
    </main>

    <!-- Footer Component -->
    <app-footer></app-footer>

    <!-- Scripts -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/fomantic-ui@2.9.3/dist/semantic.min.js"></script>
    
    <!-- App Components -->
    <script type="module" src="js/components/app-header.js"></script>
    <script type="module" src="js/components/app-footer.js"></script>
    <script type="module" src="js/components/customer-revenue-table.js"></script>
    <script type="module" src="js/app.js"></script>
</body>
</html>
```

**Semantiske tags:**
- `<header>` - Top navigation
- `<main>` - Hovedindhold (kun én per side)
- `<footer>` - Bundsektion
- `<nav>` - Navigation links
- `<section>` - Tematisk gruppering
- `<article>` - Selvstændigt indhold

### Meta Tags

**Viewport meta tag:**
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
- Essentiel for responsive design
- `width=device-width` - Brug enhedens bredde
- `initial-scale=1.0` - Ingen zoom ved load

**Character encoding:**
```html
<meta charset="UTF-8">
```
- UTF-8 understøtter alle sprog og special characters

### Script Loading

**Type="module":**
```html
<script type="module" src="js/app.js"></script>
```
- Aktiverer ES6 modules (`import`/`export`)
- Automatic strict mode
- Deferred by default (kører efter DOM er loaded)
- Egen scope (ingen global pollution)

**CDN Libraries:**
```html
<!-- jQuery (required by Fomantic UI) -->
<script src="https://cdn.jsdelivr.net/npm/jquery@3.7.1/dist/jquery.min.js"></script>

<!-- Fomantic UI -->
<script src="https://cdn.jsdelivr.net/npm/fomantic-ui@2.9.3/dist/semantic.min.js"></script>
```
- jQuery er legacy, men Fomantic UI kræver det
- Loaded før vores custom scripts

---

## CSS og Styling

### Fomantic UI Framework

**Fomantic UI** er et CSS framework der giver:
- Responsive grid system
- Pre-stylede komponenter
- Konsistent design language
- Icon library (>900 icons)

### Grid System

Fomantic UI bruger et 16-column grid:

```html
<div class="ui container">
    <div class="ui grid">
        <div class="eight wide column">
            <!-- 50% width -->
        </div>
        <div class="eight wide column">
            <!-- 50% width -->
        </div>
    </div>
</div>
```

**Container:**
- `.ui.container` - Fixed width, responsive
- Max width: 1127px på desktop
- Automatisk padding

**Column widths:**
- `one wide` til `sixteen wide`
- `four wide` = 25%
- `eight wide` = 50%
- `twelve wide` = 75%

### Responsive Breakpoints

```html
<div class="ui stackable grid">
    <div class="eight wide computer sixteen wide mobile column">
        <!-- 50% på desktop, 100% på mobil -->
    </div>
</div>
```

**Device targeting:**
- `mobile` - < 768px
- `tablet` - 768px - 991px
- `computer` - > 992px
- `large screen` - > 1200px
- `widescreen` - > 1920px

**Stackable:**
- `.ui.stackable.grid` - Columns stacker på mobil

### Komponenter

**Buttons:**
```html
<button class="ui primary button">Primary</button>
<button class="ui secondary button">Secondary</button>
<button class="ui green button">Success</button>
<button class="ui red button">Danger</button>
```

**Tables:**
```html
<table class="ui celled table">
    <thead>
        <tr>
            <th>Name</th>
            <th>Email</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John Doe</td>
            <td>john@example.com</td>
        </tr>
    </tbody>
</table>
```

**Modifiers:**
- `.celled` - Borders mellem celler
- `.striped` - Zebra striping
- `.compact` - Less padding
- `.selectable` - Hover effekt på rows
- `.sortable` - Sortable headers

**Segments:**
```html
<div class="ui segment">
    <h2>Section Title</h2>
    <p>Content goes here</p>
</div>
```

**Messages:**
```html
<div class="ui success message">
    <div class="header">Success!</div>
    <p>Your action was completed.</p>
</div>

<div class="ui error message">
    <div class="header">Error!</div>
    <p>Something went wrong.</p>
</div>
```

### Icons

Fomantic UI inkluderer et stort icon library:

```html
<i class="user icon"></i>
<i class="chart line icon"></i>
<i class="home icon"></i>
<i class="settings icon"></i>
```

**Sizes:**
```html
<i class="small icon"></i>
<i class="large icon"></i>
<i class="huge icon"></i>
```

**Colors:**
```html
<i class="red heart icon"></i>
<i class="blue info icon"></i>
<i class="green check icon"></i>
```

### Custom CSS

Vores `styles.css` tilføjer custom styling:

```css
:root {
    --primary-color: #2185d0;
    --header-height: 60px;
    --footer-height: 50px;
}

body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

.main-content {
    flex: 1;
    padding: 2rem 0;
}

/* Responsive table */
@media (max-width: 768px) {
    .ui.table {
        font-size: 0.9em;
    }
}
```

**CSS Variables:**
- Defineres i `:root`
- Bruges med `var(--variable-name)`
- Nemt at ændre tema

**Flexbox layout:**
- `display: flex` på body
- `flex-direction: column` - Vertikal layout
- `flex: 1` på main - Fylder tilgængelig plads
- Footer skubbes til bunden

---

## JavaScript og ES6+ Modules

### Module System

**ES6 Modules** giver os:
- Import/export functionality
- Organiseret kode i separate filer
- Ingen global scope pollution
- Tree-shaking (unused code removal)

**Export:**
```javascript
// config/settings.js
export const API_CONFIG = {
    BASE_URL: 'https://northwind-backend-b088.onrender.com/api',
    TIMEOUT: 30000,
};

export const APP_CONFIG = {
    NAME: 'Northwind Traders',
    VERSION: '1.0.0',
};
```

**Import:**
```javascript
// components/customer-table.js
import { API_CONFIG } from '../config/settings.js';

console.log(API_CONFIG.BASE_URL);
```

**Named exports** (som ovenfor):
- Export multiple items
- Import med curly braces `{ }`
- Kan rename: `import { API_CONFIG as config }`

**Default export:**
```javascript
// utils.js
export default function formatDate(date) {
    return new Date(date).toLocaleDateString();
}

// Import without braces
import formatDate from './utils.js';
```

### Modern JavaScript Features

**Arrow Functions:**
```javascript
// Traditional function
function add(a, b) {
    return a + b;
}

// Arrow function
const add = (a, b) => a + b;

// With body
const multiply = (a, b) => {
    const result = a * b;
    return result;
};
```

**Template Literals:**
```javascript
const name = 'John';
const age = 30;

// Old way
const message = 'My name is ' + name + ' and I am ' + age + ' years old.';

// Template literal
const message = `My name is ${name} and I am ${age} years old.`;

// Multi-line
const html = `
    <div class="card">
        <h2>${name}</h2>
        <p>Age: ${age}</p>
    </div>
`;
```

**Destructuring:**
```javascript
// Object destructuring
const { BASE_URL, TIMEOUT } = API_CONFIG;

// Array destructuring
const [first, second] = ['apple', 'banana', 'cherry'];

// With defaults
const { BASE_URL, PORT = 3000 } = API_CONFIG;
```

**Spread Operator:**
```javascript
// Array spread
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// Object spread
const config = { ...API_CONFIG, TIMEOUT: 5000 };
```

**Async/Await:**
```javascript
// Old way with promises
fetch('/api/customers')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));

// Modern way with async/await
async function getCustomers() {
    try {
        const response = await fetch('/api/customers');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

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

**Basic struktur:**
```javascript
class MyElement extends HTMLElement {
    constructor() {
        super();
        // Initial setup
    }

    connectedCallback() {
        // Called when element is added to DOM
        this.render();
    }

    render() {
        // Build and insert HTML
        this.innerHTML = `<p>Hello from my-element!</p>`;
    }
}

// Register the custom element
customElements.define('my-element', MyElement);
```

**Lifecycle callbacks:**
- `constructor()` - Element created
- `connectedCallback()` - Added to DOM
- `disconnectedCallback()` - Removed from DOM
- `attributeChangedCallback()` - Attribute changed
- `adoptedCallback()` - Moved to new document

### App Header Component

**HTML usage:**
```html
<app-header></app-header>
```

**JavaScript implementation:**
```javascript
// components/app-header.js
class AppHeader extends HTMLElement {
    connectedCallback() {
        this.render();
    }

    render() {
        this.innerHTML = `
            <header class="ui fixed menu">
                <div class="ui container">
                    <a href="index.html" class="header item">
                        <i class="home icon"></i>
                        Northwind Traders
                    </a>
                    <a href="customers.html" class="item">
                        <i class="users icon"></i>
                        Customers
                    </a>
                </div>
            </header>
        `;
    }
}

customElements.define('app-header', AppHeader);
```

**Hvorfor Web Component?**
- Reusable på alle sider
- Én kodeændring opdaterer alle steder
- Clean HTML (bare `<app-header>`)
- Encapsulated functionality

### App Footer Component

**HTML usage:**
```html
<app-footer></app-footer>
```

**JavaScript:**
```javascript
// components/app-footer.js
class AppFooter extends HTMLElement {
    connectedCallback() {
        this.render();
    }

    render() {
        const year = new Date().getFullYear();
        this.innerHTML = `
            <footer class="ui inverted vertical footer segment">
                <div class="ui container">
                    <div class="ui center aligned container">
                        <p>&copy; ${year} Northwind Traders. All rights reserved.</p>
                    </div>
                </div>
            </footer>
        `;
    }
}

customElements.define('app-footer', AppFooter);
```

**Dynamic content:**
- `new Date().getFullYear()` - Always current year
- Template literal injekterer værdi

### Customer Revenue Table Component

**HTML usage med attributter:**
```html
<customer-revenue-table limit="5"></customer-revenue-table>
```

**JavaScript:**
```javascript
import { API_CONFIG } from '../config/settings.js';

class CustomerRevenueTable extends HTMLElement {
    connectedCallback() {
        this.render();
        this.loadData();
    }

    render() {
        const limit = this.getAttribute('limit') || 10;
        
        this.innerHTML = `
            <div class="ui segment">
                <h2 class="ui header">
                    <i class="chart line icon"></i>
                    <div class="content">
                        Top ${limit} Customers by Revenue
                        <div class="sub header">Sorted by total revenue</div>
                    </div>
                </h2>
                <div class="ui active centered inline loader" id="loader"></div>
                <div id="tableContainer" style="display: none;">
                    <table class="ui celled striped table">
                        <thead>
                            <tr>
                                <th>Customer ID</th>
                                <th>Company Name</th>
                                <th>Contact Name</th>
                                <th>Total Revenue</th>
                            </tr>
                        </thead>
                        <tbody id="tableBody"></tbody>
                    </table>
                </div>
                <div class="ui error message" id="errorMessage" style="display: none;"></div>
            </div>
        `;
    }

    async loadData() {
        const limit = this.getAttribute('limit') || 10;
        const loader = this.querySelector('#loader');
        const tableContainer = this.querySelector('#tableContainer');
        const errorMessage = this.querySelector('#errorMessage');
        const tableBody = this.querySelector('#tableBody');

        try {
            const url = `${API_CONFIG.BASE_URL}/public/customers-with-revenue?take=${limit}`;
            const response = await fetch(url);
            
            if (!response.ok) {
                throw new Error(`HTTP error! status: ${response.status}`);
            }

            const customers = await response.json();

            // Hide loader, show table
            loader.style.display = 'none';
            tableContainer.style.display = 'block';

            // Populate table
            tableBody.innerHTML = customers.map(customer => `
                <tr>
                    <td>${customer.customerId}</td>
                    <td>${customer.companyName}</td>
                    <td>${customer.contactName || '-'}</td>
                    <td>$${customer.totalRevenue.toFixed(2)}</td>
                </tr>
            `).join('');

        } catch (error) {
            console.error('Error loading customers:', error);
            loader.style.display = 'none';
            errorMessage.style.display = 'block';
            errorMessage.textContent = 'Failed to load customer data. Please try again later.';
        }
    }
}

customElements.define('customer-revenue-table', CustomerRevenueTable);
```

**Key features:**

**Attributes:**
- `this.getAttribute('limit')` - Læs HTML attribut
- Gør komponenten configurable

**Loading states:**
```javascript
// 1. Show loader
loader.style.display = 'none';

// 2. Show content
tableContainer.style.display = 'block';

// 3. Or show error
errorMessage.style.display = 'block';
```

**Error handling:**
- Try/catch around fetch
- Check `response.ok`
- User-friendly error messages

**Dynamic HTML generation:**
```javascript
tableBody.innerHTML = customers.map(customer => `
    <tr>
        <td>${customer.customerId}</td>
        <td>${customer.companyName}</td>
    </tr>
`).join('');
```

**Array.map():**
- Transform array items to HTML strings
- `.join('')` - Combine to single string
- Set as innerHTML

### Customer Table Component (CRUD)

**Full CRUD operations:**
```javascript
class CustomerTable extends HTMLElement {
    connectedCallback() {
        this.render();
        this.loadCustomers();
        this.attachEventListeners();
    }

    async loadCustomers() {
        // GET all customers
        const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers`);
        const customers = await response.json();
        this.renderTable(customers);
    }

    async createCustomer(customerData) {
        // POST new customer
        const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(customerData),
        });

        if (response.ok) {
            this.loadCustomers(); // Refresh
        }
    }

    async updateCustomer(id, customerData) {
        // PUT update customer
        const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers/${id}`, {
            method: 'PUT',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(customerData),
        });

        if (response.ok) {
            this.loadCustomers(); // Refresh
        }
    }

    async deleteCustomer(id) {
        // DELETE customer
        if (confirm('Are you sure you want to delete this customer?')) {
            const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers/${id}`, {
                method: 'DELETE',
            });

            if (response.ok) {
                this.loadCustomers(); // Refresh
            }
        }
    }

    attachEventListeners() {
        // Event delegation for dynamically created elements
        this.addEventListener('click', (e) => {
            if (e.target.classList.contains('delete-btn')) {
                const id = e.target.dataset.customerId;
                this.deleteCustomer(id);
            }
        });
    }
}
```

**Event Delegation:**
- Attach listener til parent element
- Check `e.target` for actual clicked element
- Virker for dynamically added elements

**Data attributes:**
```html
<button class="delete-btn" data-customer-id="ALFKI">Delete</button>
```
```javascript
const id = e.target.dataset.customerId; // "ALFKI"
```

---

## Fetch API og REST Integration

### Fetch Basics

**Fetch** er en moderne API til HTTP requests:

```javascript
// Simple GET
const response = await fetch('https://api.example.com/data');
const data = await response.json();
```

**Response properties:**
- `response.ok` - Boolean (true if 200-299)
- `response.status` - HTTP status code (200, 404, 500)
- `response.statusText` - Status message ("OK", "Not Found")
- `response.headers` - Response headers
- `response.json()` - Parse JSON body
- `response.text()` - Get raw text

### HTTP Methods

**GET - Fetch data:**
```javascript
async function getCustomers() {
    try {
        const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers`);
        
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        
        const customers = await response.json();
        return customers;
    } catch (error) {
        console.error('Error fetching customers:', error);
        throw error;
    }
}
```

**POST - Create new:**
```javascript
async function createCustomer(customerData) {
    try {
        const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(customerData),
        });

        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }

        const newCustomer = await response.json();
        return newCustomer;
    } catch (error) {
        console.error('Error creating customer:', error);
        throw error;
    }
}
```

**PUT - Update existing:**
```javascript
async function updateCustomer(id, customerData) {
    try {
        const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers/${id}`, {
            method: 'PUT',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(customerData),
        });

        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }

        return await response.json();
    } catch (error) {
        console.error('Error updating customer:', error);
        throw error;
    }
}
```

**DELETE - Remove:**
```javascript
async function deleteCustomer(id) {
    try {
        const response = await fetch(`${API_CONFIG.BASE_URL}/public/customers/${id}`, {
            method: 'DELETE',
        });

        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }

        return true;
    } catch (error) {
        console.error('Error deleting customer:', error);
        throw error;
    }
}
```

### Request Headers

**Content-Type:**
```javascript
headers: {
    'Content-Type': 'application/json',
}
```
- Fortæller server at body er JSON

**Authorization (for protected endpoints):**
```javascript
headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${token}`,
}
```

### Query Parameters

**Add parameters to URL:**
```javascript
const limit = 10;
const skip = 0;
const url = `${API_CONFIG.BASE_URL}/public/customers?take=${limit}&skip=${skip}`;

const response = await fetch(url);
```

**URLSearchParams helper:**
```javascript
const params = new URLSearchParams({
    take: 10,
    skip: 0,
    country: 'Germany',
});

const url = `${API_CONFIG.BASE_URL}/public/customers?${params}`;
// Result: .../customers?take=10&skip=0&country=Germany
```

### Error Handling

**Comprehensive error handling:**
```javascript
async function fetchWithErrorHandling(url, options = {}) {
    try {
        const response = await fetch(url, options);

        // HTTP errors (4xx, 5xx)
        if (!response.ok) {
            if (response.status === 404) {
                throw new Error('Resource not found');
            } else if (response.status === 500) {
                throw new Error('Server error. Please try again later.');
            } else {
                throw new Error(`HTTP error! status: ${response.status}`);
            }
        }

        return await response.json();

    } catch (error) {
        // Network errors (no connection, timeout)
        if (error instanceof TypeError) {
            throw new Error('Network error. Please check your connection.');
        }
        // Re-throw other errors
        throw error;
    }
}
```

**Display errors to user:**
```javascript
async function loadData() {
    const errorDiv = document.getElementById('error');
    
    try {
        const data = await fetchWithErrorHandling(url);
        // Success
    } catch (error) {
        errorDiv.textContent = error.message;
        errorDiv.style.display = 'block';
    }
}
```

### Loading States

**Show spinner while loading:**
```javascript
async function loadCustomers() {
    const loader = document.getElementById('loader');
    const content = document.getElementById('content');
    
    // Show loader
    loader.style.display = 'block';
    content.style.display = 'none';
    
    try {
        const customers = await fetch(url).then(r => r.json());
        
        // Hide loader, show content
        loader.style.display = 'none';
        content.style.display = 'block';
        
        renderCustomers(customers);
    } catch (error) {
        loader.style.display = 'none';
        showError(error.message);
    }
}
```

### Timeout Handling

**Add timeout to fetch:**
```javascript
async function fetchWithTimeout(url, options = {}, timeout = 30000) {
    const controller = new AbortController();
    const id = setTimeout(() => controller.abort(), timeout);

    try {
        const response = await fetch(url, {
            ...options,
            signal: controller.signal,
        });
        clearTimeout(id);
        return response;
    } catch (error) {
        clearTimeout(id);
        if (error.name === 'AbortError') {
            throw new Error('Request timeout');
        }
        throw error;
    }
}
```

---

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

### PWA Filer

**manifest.json:**
```json
{
    "name": "Northwind Traders",
    "short_name": "Northwind",
    "description": "Customer management system",
    "start_url": "./",
    "scope": "./",
    "display": "standalone",
    "background_color": "#2185d0",
    "theme_color": "#2185d0",
    "orientation": "any",
    "icons": [
        {
            "src": "./assets/icon-192.png",
            "sizes": "192x192",
            "type": "image/png",
            "purpose": "any maskable"
        },
        {
            "src": "./assets/icon-512.png",
            "sizes": "512x512",
            "type": "image/png",
            "purpose": "any maskable"
        }
    ]
}
```

**Manifest properties:**
- `name` - Fuldt applikationsnavn (bruges ved installation)
- `short_name` - Kort navn (bruges under app ikon)
- `start_url` - URL der åbnes når appen startes
- `display: "standalone"` - Åbner uden browser UI
- `theme_color` - Farve til status bar og UI
- `background_color` - Splash screen baggrund
- `icons` - App ikoner i forskellige størrelser

**Service Worker (sw.js):**
```javascript
// Minimal Service Worker for PWA installation
self.addEventListener('install', () => {
    console.log('Service Worker: Installed');
    self.skipWaiting();
});

self.addEventListener('activate', (event) => {
    console.log('Service Worker: Activated');
    event.waitUntil(self.clients.claim());
});

self.addEventListener('fetch', (event) => {
    // Pass through to network (no caching)
    event.respondWith(fetch(event.request));
});
```

**Service Worker lifecycle:**
1. **Install** - Downloades og installeres
2. **Activate** - Aktiveres og tager kontrol
3. **Fetch** - Intercepter network requests

**Registrering i app.js:**
```javascript
// Register Service Worker
async function registerServiceWorker() {
    if ('serviceWorker' in navigator) {
        try {
            const registration = await navigator.serviceWorker.register('./sw.js');
            console.log('✅ Service Worker registered:', registration);
        } catch (error) {
            console.error('❌ Service Worker registration failed:', error);
        }
    }
}

// Initialize on page load
document.addEventListener('DOMContentLoaded', () => {
    registerServiceWorker();
});
```

### PWA Meta Tags

**HTML head-sektion:**
```html
<head>
    <!-- Basic Meta -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Northwind Traders Customer Dashboard">
    
    <!-- PWA Manifest -->
    <link rel="manifest" href="manifest.json">
    
    <!-- Theme Color (Android) -->
    <meta name="theme-color" content="#2185d0">
    
    <!-- Mobile Web App Capable (Android) -->
    <meta name="mobile-web-app-capable" content="yes">
    
    <!-- Apple Mobile Web App (iOS) -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="default">
    
    <!-- Icons -->
    <link rel="icon" type="image/x-icon" href="assets/favicon.ico">
    <link rel="icon" type="image/svg+xml" href="assets/favicon.svg">
    <link rel="apple-touch-icon" href="assets/apple-touch-icon.png">
    
    <title>Northwind Traders - Customer Dashboard</title>
</head>
```

**Meta tag forklaring:**
- `theme-color` - Browser toolbar farve (Android/Chrome)
- `mobile-web-app-capable` - Aktivér "Add to Home Screen" (Android)
- `apple-mobile-web-app-capable` - Aktivér webapp mode (iOS)
- `apple-mobile-web-app-status-bar-style` - iOS status bar styling

### App Ikoner

**Forskellige størrelser:**
- `favicon.ico` - 32x32 - Browser tab
- `favicon.svg` - Scalable - Moderne browsere
- `icon-192.png` - 192x192 - Android, PWA minimum
- `icon-512.png` - 512x512 - Android, PWA anbefalet
- `apple-touch-icon.png` - 180x180 - iOS

**Icon design best practices:**
- Simple, recognizable designs
- Solid background (ingen transparens for maskable)
- Center logo med safe zone (80% af ikon)
- Test på både lys og mørk baggrund

### PWA Begrænsninger i Dette Projekt

⚠️ **Ingen Offline Funktionalitet**

Vores implementation har en **minimal service worker** uden caching:
- ✅ Installbar på alle platforme
- ✅ Åbner i eget vindue
- ✅ App-lignende oplevelse
- ❌ Ingen offline support
- ❌ Ingen cache af assets
- ❌ Kræver aktiv internetforbindelse

**Hvorfor ingen cache?**

Dette projekt fokuserer på grundlæggende PWA-koncepter. En fuld cache-strategi ville kræve:
- Cache af HTML, CSS, JavaScript files
- Cache af API responses
- Update strategier (Cache First, Network First, Stale While Revalidate)
- Version management af cached assets
- Håndtering af cache-størrelse

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

## Code Quality Tools

### ESLint - JavaScript Linting

**ESLint** analyserer JavaScript-kode for fejl og style issues.

**Configuration (eslint.config.mjs):**
```javascript
import js from '@eslint/js';
import globals from 'globals';

export default [
    js.configs.recommended,
    {
        languageOptions: {
            ecmaVersion: 2022,
            sourceType: 'module',
            globals: {
                ...globals.browser,
                customElements: 'readonly',
            },
        },
        rules: {
            'no-unused-vars': 'warn',
            'no-console': 'off', // Allow console.log in development
            'semi': ['error', 'always'],
            'quotes': ['error', 'single'],
        },
    },
];
```

**Run linting:**
```bash
npm run lint:js
```

**Common rules:**
- `no-unused-vars` - Warn about unused variables
- `no-console` - Disallow console.log (off in dev)
- `semi` - Require semicolons
- `quotes` - Enforce single quotes
- `indent` - Enforce consistent indentation
- `no-undef` - Disallow undefined variables

**Fix automatically:**
```bash
npx eslint . --fix
```

### HTMLHint - HTML Validation

**HTMLHint** checker HTML for fejl og best practices.

**Configuration (.htmlhintrc):**
```json
{
    "tagname-lowercase": true,
    "attr-lowercase": true,
    "attr-value-double-quotes": true,
    "doctype-first": true,
    "tag-pair": true,
    "spec-char-escape": true,
    "id-unique": true,
    "src-not-empty": true,
    "attr-no-duplication": true,
    "title-require": true
}
```

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

**Configuration (.stylelintrc.json):**
```json
{
    "extends": "stylelint-config-standard",
    "rules": {
        "indentation": 4,
        "color-hex-case": "lower",
        "color-hex-length": "short",
        "declaration-block-trailing-semicolon": "always",
        "selector-pseudo-element-colon-notation": "double"
    }
}
```

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

**Package.json scripts:**
```json
{
    "scripts": {
        "lint:html": "htmlhint \"**/*.html\"",
        "lint:css": "stylelint \"**/*.css\"",
        "lint:js": "eslint .",
        "lint": "npm run lint:html && npm run lint:css && npm run lint:js"
    }
}
```

---

## GitHub Actions og Deployment

### Continuous Deployment

**GitHub Actions** automatiserer deployment:

1. Push code til GitHub
2. Workflow triggers
3. Install dependencies
4. Run linting
5. Deploy til GitHub Pages

### Workflow Configuration

**.github/workflows/deploy.yml:**
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install dependencies
        run: npm ci

      - name: Run linting
        run: npm run lint

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

**Workflow triggers:**
- `push` til `main` branch
- `workflow_dispatch` - Manuel trigger

**Jobs:**
1. **Checkout** - Clone repository
2. **Setup Node.js** - Install Node.js 20
3. **Install dependencies** - `npm ci`
4. **Run linting** - Quality check
5. **Setup Pages** - Configure GitHub Pages
6. **Upload artifact** - Package files
7. **Deploy** - Publish to GitHub Pages

### Linting Gate

**Stop deployment hvis linting fejler:**
```yaml
- name: Run linting
  run: npm run lint
```

Hvis `npm run lint` returnerer error code (non-zero exit):
- Workflow stopper
- Deployment afbrydes
- Du ser fejl i GitHub Actions tab

**Fordele:**
- ✅ Ingen dårlig kode i produktion
- ✅ Tvinger code quality
- ✅ Fanger fejl før brugerne

### Manual Trigger

**Run workflow manually:**
1. Gå til repository på GitHub
2. Click **Actions** tab
3. Select **Deploy to GitHub Pages** workflow
4. Click **Run workflow**
5. Select branch og click **Run workflow**

### Deployment URL

Efter første succesfulde deployment:

🔗 **https://{username}.github.io/{repo-name}**

Eksempel: `https://devcronberg.github.io/Northwind.App.Frontend`

---

## Progressive Web App (PWA)

### Hvad er en PWA?

En **Progressive Web App** er en webapp med app-lignende features:

- 📱 **Installable** - Add to home screen
- 🔄 **Offline capable** - Works without internet
- 🚀 **Fast** - Caches assets
- 🔔 **Push notifications** - Engage users
- 📲 **Native feel** - Runs in own window

### Web App Manifest

**manifest.json:**
```json
{
    "name": "Northwind Traders",
    "short_name": "Northwind",
    "description": "Customer management application",
    "start_url": "/",
    "display": "standalone",
    "background_color": "#ffffff",
    "theme_color": "#2185d0",
    "orientation": "portrait-primary",
    "icons": [
        {
            "src": "/assets/icon-192.png",
            "sizes": "192x192",
            "type": "image/png"
        },
        {
            "src": "/assets/icon-512.png",
            "sizes": "512x512",
            "type": "image/png"
        }
    ]
}
```

**Link i HTML:**
```html
<link rel="manifest" href="/manifest.json">
```

**Properties:**
- `name` - Full app name
- `short_name` - Name på home screen
- `start_url` - URL når app åbnes
- `display` - `standalone`, `fullscreen`, `minimal-ui`
- `theme_color` - Toolbar color
- `icons` - App icons (192px og 512px)

### Service Worker (Valgfrit)

**Service Workers** enabler offline functionality:

**sw.js:**
```javascript
const CACHE_NAME = 'northwind-v1';
const urlsToCache = [
    '/',
    '/index.html',
    '/customers.html',
    '/css/styles.css',
    '/js/app.js',
    '/js/config/settings.js',
];

// Install - cache assets
self.addEventListener('install', event => {
    event.waitUntil(
        caches.open(CACHE_NAME)
            .then(cache => cache.addAll(urlsToCache))
    );
});

// Fetch - serve from cache
self.addEventListener('fetch', event => {
    event.respondWith(
        caches.match(event.request)
            .then(response => {
                // Cache hit - return response
                if (response) {
                    return response;
                }
                // Fetch from network
                return fetch(event.request);
            })
    );
});

// Activate - cleanup old caches
self.addEventListener('activate', event => {
    event.waitUntil(
        caches.keys().then(cacheNames => {
            return Promise.all(
                cacheNames.map(cacheName => {
                    if (cacheName !== CACHE_NAME) {
                        return caches.delete(cacheName);
                    }
                })
            );
        })
    );
});
```

**Register i app.js:**
```javascript
if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('/sw.js')
        .then(registration => {
            console.log('Service Worker registered:', registration);
        })
        .catch(error => {
            console.log('Service Worker registration failed:', error);
        });
}
```

### Install Prompt

**Prompt user to install:**
```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
    // Prevent default prompt
    e.preventDefault();
    // Save for later
    deferredPrompt = e;
    // Show custom install button
    document.getElementById('installBtn').style.display = 'block';
});

document.getElementById('installBtn').addEventListener('click', async () => {
    if (deferredPrompt) {
        // Show prompt
        deferredPrompt.prompt();
        // Wait for user choice
        const { outcome } = await deferredPrompt.userChoice;
        console.log(`User ${outcome} the install prompt`);
        deferredPrompt = null;
    }
});
```

### HTTPS Requirement

PWAs **kræver HTTPS** (eller localhost):

- ✅ GitHub Pages (automatic HTTPS)
- ✅ Localhost (development)
- ❌ HTTP sites (not allowed)

---

## Best Practices

### 1. **Separation of Concerns**

**Bad:**
```html
<button onclick="deleteCustomer('ALFKI')">Delete</button>

<script>
function deleteCustomer(id) {
    // Logic mixed with HTML
}
</script>
```

**Good:**
```html
<button class="delete-btn" data-customer-id="ALFKI">Delete</button>

<script type="module">
// Separate JavaScript file
import { deleteCustomer } from './api.js';

document.addEventListener('click', (e) => {
    if (e.target.classList.contains('delete-btn')) {
        const id = e.target.dataset.customerId;
        deleteCustomer(id);
    }
});
</script>
```

### 2. **Async/Await over Promises**

**Old way:**
```javascript
fetch(url)
    .then(response => response.json())
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error(error);
    });
```

**Modern way:**
```javascript
try {
    const response = await fetch(url);
    const data = await response.json();
    console.log(data);
} catch (error) {
    console.error(error);
}
```

### 3. **Error Handling**

**Always handle errors:**
```javascript
async function loadData() {
    try {
        const response = await fetch(url);
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        const data = await response.json();
        return data;
    } catch (error) {
        // Log for developers
        console.error('Error loading data:', error);
        // Show user-friendly message
        showErrorMessage('Failed to load data. Please try again.');
        throw error;
    }
}
```

### 4. **Loading States**

**Always show feedback:**
```javascript
async function loadCustomers() {
    showLoader();
    
    try {
        const customers = await fetchCustomers();
        hideLoader();
        renderCustomers(customers);
    } catch (error) {
        hideLoader();
        showError(error.message);
    }
}
```

### 5. **Responsive Design**

**Mobile-first approach:**
```css
/* Base styles (mobile) */
.container {
    width: 100%;
    padding: 1rem;
}

/* Tablet and up */
@media (min-width: 768px) {
    .container {
        max-width: 750px;
    }
}

/* Desktop and up */
@media (min-width: 992px) {
    .container {
        max-width: 970px;
    }
}
```

### 6. **Accessibility**

**Use semantic HTML:**
```html
<!-- Bad -->
<div class="button" onclick="submit()">Submit</div>

<!-- Good -->
<button type="submit">Submit</button>
```

**Add ARIA labels:**
```html
<button aria-label="Delete customer">
    <i class="trash icon"></i>
</button>
```

**Keyboard navigation:**
```javascript
element.addEventListener('keypress', (e) => {
    if (e.key === 'Enter' || e.key === ' ') {
        handleAction();
    }
});
```

### 7. **Performance**

**Debounce search input:**
```javascript
function debounce(func, wait) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, args), wait);
    };
}

const searchInput = document.getElementById('search');
searchInput.addEventListener('input', debounce((e) => {
    performSearch(e.target.value);
}, 300));
```

**Lazy load images:**
```html
<img src="placeholder.jpg" data-src="real-image.jpg" loading="lazy" alt="Description">
```

### 8. **Security**

**Sanitize user input:**
```javascript
function sanitizeHTML(str) {
    const div = document.createElement('div');
    div.textContent = str;
    return div.innerHTML;
}

// Use textContent instead of innerHTML when possible
element.textContent = userInput; // Safe
element.innerHTML = userInput;    // Dangerous (XSS)
```

**HTTPS only:**
```javascript
// Check for HTTPS in production
if (location.protocol !== 'https:' && location.hostname !== 'localhost') {
    location.replace(`https:${location.href.substring(location.protocol.length)}`);
}
```

---

## Debugging

### Browser DevTools

**Console:**
```javascript
console.log('Simple log');
console.error('Error message');
console.warn('Warning message');
console.table(customers); // Pretty table
console.time('operation'); // Start timer
console.timeEnd('operation'); // End timer
```

**Debugger statement:**
```javascript
function processData(data) {
    debugger; // Execution pauses here
    const result = data.map(item => item.value);
    return result;
}
```

**Network tab:**
- View all HTTP requests
- Check request/response headers
- See response body
- Monitor load times

**Elements tab:**
- Inspect HTML structure
- View computed styles
- Edit CSS live
- Check event listeners

### Common Issues

**CORS errors:**
```
Access to fetch at 'https://api.example.com' from origin 'http://localhost:8080' 
has been blocked by CORS policy
```

**Solution:** Backend må enable CORS:
```csharp
// Backend C# code
builder.Services.AddCors(options => {
    options.AddDefaultPolicy(builder => {
        builder.AllowAnyOrigin()
               .AllowAnyMethod()
               .AllowAnyHeader();
    });
});
```

**Module not found:**
```
Failed to load module script: Expected a JavaScript module script
```

**Solution:** Check import paths:
```javascript
// Wrong
import { API_CONFIG } from './settings.js'; // Missing '../'

// Correct
import { API_CONFIG } from '../config/settings.js';
```

**Fetch fails silently:**
```javascript
// Always check response.ok
const response = await fetch(url);
if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
}
```

---

## Testing (Fremtidig udvidelse)

Vores projekt inkluderer ikke automatiseret testing endnu, men her er hvad man typisk ville tilføje:

### Unit Testing med Vitest

```javascript
// customer.test.js
import { describe, it, expect } from 'vitest';
import { formatCustomerName } from './utils.js';

describe('formatCustomerName', () => {
    it('should format name correctly', () => {
        const result = formatCustomerName('John', 'Doe');
        expect(result).toBe('Doe, John');
    });

    it('should handle missing last name', () => {
        const result = formatCustomerName('John', null);
        expect(result).toBe('John');
    });
});
```

### E2E Testing med Playwright

```javascript
// e2e/customers.spec.js
import { test, expect } from '@playwright/test';

test('should load customer list', async ({ page }) => {
    await page.goto('http://localhost:8080/customers.html');
    
    await expect(page.locator('h1')).toContainText('Customers');
    await expect(page.locator('table tbody tr')).toHaveCount(10);
});

test('should create new customer', async ({ page }) => {
    await page.goto('http://localhost:8080/customers.html');
    
    await page.click('button.add-customer');
    await page.fill('input[name="companyName"]', 'Test Company');
    await page.fill('input[name="contactName"]', 'Test Contact');
    await page.click('button[type="submit"]');
    
    await expect(page.locator('.success.message')).toBeVisible();
});
```

---

## Videre Læring

### Anbefalede ressourcer

**MDN Web Docs:**
- [JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
- [Web APIs](https://developer.mozilla.org/en-US/docs/Web/API)
- [Web Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components)

**Fomantic UI:**
- [Documentation](https://fomantic-ui.com/)
- [Components](https://fomantic-ui.com/introduction/getting-started.html)

**GitHub Pages:**
- [Documentation](https://docs.github.com/en/pages)
- [Custom domains](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

**PWA:**
- [Google PWA Guide](https://web.dev/progressive-web-apps/)
- [Service Workers](https://developers.google.com/web/fundamentals/primers/service-workers)

### Næste skridt

1. **Tilføj flere features:**
   - Søgning og filtering
   - Sortering på kolonner
   - Pagination
   - Form validation
   - Toast notifications

2. **Forbedre PWA:**
   - Implementer service worker
   - Add offline functionality
   - Enable push notifications

3. **Performance:**
   - Implementer lazy loading
   - Add caching strategy
   - Optimize bundle size

4. **Testing:**
   - Add unit tests (Vitest)
   - Add E2E tests (Playwright)
   - Add visual regression tests

5. **Advanced features:**
   - Routing (for multi-page SPA)
   - State management
   - Authentication UI
   - Real-time updates (WebSockets)

---

**Happy Coding! 🚀**

*Dette er en uddannelsesapplikation designet til at demonstrere moderne frontend best practices. For produktionsbrug, overvej at tilføje mere omfattende error handling, security measures, testing og monitoring.*
