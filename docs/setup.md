---
created: 2025-12-24
modified: 2025-12-24
author: Michell Cronberg
---
# Opsætning af udviklingsmiljø

Før vi går i gang med kurset, skal du have installeret nogle værktøjer på din computer. Denne guide hjælper dig igennem processen trin for trin.

!!! tip "Tag det roligt"
    Hvis du er ny til programmering, kan det virke overvældende med alle disse værktøjer. Tag det i dit eget tempo – du kan altid vende tilbage til denne guide.

## .NET 10 SDK

**.NET** er den platform, vi bruger til at bygge vores webapplikation på serveren (backend). Du skal installere **.NET 10 SDK** (Software Development Kit).

### Installation

1. Gå til [dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)
2. Vælg **.NET 10** (eller seneste version)
3. Download **SDK** til dit styresystem
4. Kør installationsfilen og følg vejledningen

### Verificer installationen

Åbn en terminal (på Windows brug Command Prompt, PowerShell eller macOS/Linux Terminal) og skriv:

```bash
dotnet --version
```

Du skulle se versionsnummeret, f.eks. `10.0.100`.

## Visual Studio Code

**Visual Studio Code** (VS Code) er en gratis og populær kodeeditor fra Microsoft. Det er den editor, vi bruger i kurset.

### Installation

1. Gå til [code.visualstudio.com](https://code.visualstudio.com/)
2. Klik på **Download**-knappen (den vælger automatisk den rigtige version til dit styresystem)
3. Kør installationsfilen og følg vejledningen
4. Åbn VS Code efter installationen

### Backend Extensions

Til backend-udvikling med C# og ASP.NET Core anbefales følgende extensions:

1. Åbn VS Code
2. Klik på **Extensions**-ikonet i venstre side (eller tryk ++ctrl+shift+x++)
3. Søg efter og installer følgende:

| Extension               | ID                        | Formål                                                                    |
| ----------------------- | ------------------------- | ------------------------------------------------------------------------- |
| **C# Dev Kit**          | `ms-dotnettools.csdevkit` | Komplet C# udvikling - IntelliSense, debugging, test runner, NuGet        |
| **GitHub Copilot Chat** | `github.copilot-chat`     | AI-assistent direkte i VS Code - få hjælp, forklaringer og kodegenerering |
| **REST Client**         | `humao.rest-client`       | Test REST APIs direkte i VS Code - alternativ til Postman/Swagger         |

!!! info "C# Dev Kit"
    C# Dev Kit er den primære extension til C# udvikling og inkluderer:
    
    - Syntaksfremhævning og IntelliSense
    - Debugging
    - Projektnavigation
    - Test Explorer
    - NuGet-pakkehåndtering

!!! tip "REST Client"
    Med REST Client kan du oprette `.http` eller `.rest` filer med HTTP requests og køre dem direkte i VS Code. Perfekt til at teste din API under udvikling!

### Frontend Extensions

Til frontend-udvikling (HTML, CSS, JavaScript) anbefales følgende extensions:

1. Åbn VS Code
2. Klik på **Extensions**-ikonet (eller tryk ++ctrl+shift+x++)
3. Søg efter og installer følgende:

| Extension                   | ID                                    | Formål                                                                |
| --------------------------- | ------------------------------------- | --------------------------------------------------------------------- |
| **HTMLHint**                | `htmlhint.vscode-htmlhint`            | Lint/validering af HTML kode - finder fejl og best practice issues    |
| **Stylelint**               | `stylelint.vscode-stylelint`          | Lint/validering af CSS/SCSS - finder fejl og styling problemer        |
| **ESLint**                  | `dbaeumer.vscode-eslint`              | Lint/validering af JavaScript - finder fejl og code quality issues    |
| **Live Server**             | `ritwickdey.liveserver`               | Live preview med auto-reload - se ændringer med det samme i browseren |
| **Edge DevTools** (valgfri) | `chromedevtools.vscode-edge-devtools` | Browser DevTools direkte i VS Code - debug uden at skifte vindue      |

!!! tip "Live Server"
    Live Server er særligt nyttig under udvikling. Når du har åbnet en HTML-fil, kan du højreklikke og vælge "Open with Live Server" - så opdateres browseren automatisk hver gang du gemmer en fil.

!!! note "Linters"
    Linters (HTMLHint, Stylelint, ESLint) hjælper dig med at skrive bedre kode ved at markere fejl og problemer, mens du koder. Det er som en stavekontrol for din kode!

## Git

**Git** er et versionskontrolsystem, der bruges til at holde styr på ændringer i kode. Det er essentielt for moderne softwareudvikling.

### Windows

1. Gå til [git-scm.com](https://git-scm.com/install/windows)
2. Klik på **Download for Windows**
3. Kør installationsfilen
4. Brug standardindstillingerne (bare klik **Next** hele vejen)
5. Genstart VS Code efter installationen

### macOS

Der er flere måder at installere Git på macOS:

**Via Homebrew (anbefalet):**

```bash
brew install git
```

**Via Xcode Command Line Tools:**

```bash
xcode-select --install
```

**Via installer:**

1. Gå til [git-scm.com](https://git-scm.com/)
2. Download macOS-versionen
3. Kør installationsfilen

### Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git
```

### Linux (Fedora)

```bash
sudo dnf install git
```

### Verificer installationen

Åbn en terminal (eller Command Prompt/PowerShell på Windows) og skriv:

```bash
git --version
```

Du skulle se noget i stil med `git version 2.43.0`.

### Konfigurer Git

Efter installation skal du konfigurere dit navn og email. Det gør du ved at køre følgende kommandoer i terminalen (på Windows Cmd eller Terminal eller PowerShell), hvor du erstatter med dit eget navn og email:

```bash
git config --global user.name "Dit Navn"
git config --global user.email "din@email.dk"
```

## Docker Desktop (Valgfrit)

**Docker Desktop** er ikke påkrævet for at deltage i kurset, men det kan være en god måde at forstå Docker-konceptet på ved at køre containere lokalt.

!!! info "Hvorfor valgfrit?"
    I kurset bruger vi Render.com til at hoste vores Docker-containere i skyen. Du behøver derfor ikke have Docker installeret lokalt. Men hvis du vil eksperimentere med Docker på din egen computer eller forstå containerisering bedre, er Docker Desktop et godt værktøj.

### Installation

1. Gå til [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
2. Download Docker Desktop til dit styresystem (Windows, macOS eller Linux)
3. Kør installationsfilen og følg vejledningen
4. Start Docker Desktop efter installationen

### Verificer installationen

Åbn en terminal og skriv:

```bash
docker --version
```

Du skulle se noget i stil med `Docker version 24.0.7`.

!!! note "Hvad kan du bruge Docker Desktop til?"
    - Køre backend-applikationen lokalt i en container
    - Teste Dockerfile før deployment
    - Lære om containerisering hands-on
    - Køre flere services lokalt (database, cache, etc.)

Et godt eksempel er at køre HTTPBin lokalt i en container:

```bash
docker run -d -p 8080:80 kennethreitz/httpbin
```

og så starte din browser og gå til `http://localhost:8080` for at se HTTPBin i aktion. Du behøver ikke installere nogen dependencies – alt kører inde i containeren - du behøver ikke engang vide hvilke teknologier der er brugt under motorhjelmen! Alt hvad du skal bruge er Docker samt et image (her `kennethreitz/httpbin`).

## GitHub konto

**GitHub** er en platform til at hoste og samarbejde om kode. Vi bruger GitHub til at dele kode og materiale i kurset.

### Opret en konto

1. Gå til [github.com](https://github.com/)
2. Klik på **Sign up**
3. Følg vejledningen for at oprette en gratis konto
4. Bekræft din email-adresse

### GitHub Copilot

**GitHub Copilot** er en AI-assistent, der hjælper dig med at skrive kode. Den er integreret i VS Code og kan spare dig for meget tid.

#### Abonnement

GitHub Copilot kræver et abonnement:

- **Gratis** for studerende og open source-vedligeholdere
- **$10/måned** eller **$100/år** for individuelle brugere
- **30 dages gratis prøveperiode** for nye brugere

#### Aktiver GitHub Copilot

1. Gå til [github.com/settings/copilot](https://github.com/settings/copilot)
2. Klik på **Enable GitHub Copilot**
3. Vælg dit abonnement eller start en prøveperiode

#### Installer i VS Code

Nedenstående extensions er muligvis allerede installeret som en del af VS Code installationen. Hvis ikke, så følg disse trin:

1. Åbn VS Code
2. Gå til **Extensions** (++ctrl+shift+x++)
3. Søg efter `GitHub Copilot`
4. Installer både **GitHub Copilot** og **GitHub Copilot Chat**
5. Log ind med din GitHub-konto når du bliver bedt om det

!!! warning "Husk at logge ind"
    Første gang du bruger Copilot i VS Code, skal du logge ind med din GitHub-konto. Følg vejledningen i VS Code.

Hvis du har tid bør du læse [dokumentationen for GitHub Copilot i VS Code](https://code.visualstudio.com/docs/copilot/overview) for at få mest muligt ud af værktøjet. Se også https://github.com/github/awesome-copilot for en liste med ressourcer og tips.


## Alternative AI-assistenter

Udover GitHub Copilot kan det være en fordel at have adgang til en eller flere alternative **Large Language Models (LLM'er)**. De kan bruges til at:

- Få forklaringer på kode og koncepter
- Generere kodesnippets
- Fejlfinde problemer
- Lære nye teknologier

Her er de mest populære muligheder:

| Tjeneste    | Beskrivelse                                                                                            | Link                                            |
| ----------- | ------------------------------------------------------------------------------------------------------ | ----------------------------------------------- |
| **ChatGPT** | OpenAI's populære AI-assistent. Gratis version tilgængelig, Plus-abonnement giver adgang til GPT-4.    | [chat.openai.com](https://chat.openai.com/)     |
| **Claude**  | Anthropic's AI-assistent. Kendt for gode forklaringer og længere kontekst. Gratis version tilgængelig. | [claude.ai](https://claude.ai/)                 |
| **Gemini**  | Googles AI-assistent. Integreret med Google-tjenester. Gratis version tilgængelig.                     | [gemini.google.com](https://gemini.google.com/) |

!!! tip "Gratis at prøve"
    Alle tre tjenester har gratis versioner, så du kan prøve dem og se, hvilken du foretrækker. Det kræver blot oprettelse af en konto.

