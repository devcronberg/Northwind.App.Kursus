---
created: 2026-01-14
modified: 2026-01-15
author: Michell Cronberg
---
# Eventuelle spørgsmål

Brug denne formular til at stille spørgsmål eller komme med feedback. Jeg spørger for at opdatere denne sider med både spørgsmål og svar.

<form id="my-form" action="https://formspree.io/f/xojjqzpq" method="POST" style="width: 100%;">
  
  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px;">Navn:</label>
    <input type="text" name="name" style="width: 100%; display: block; padding: 10px; box-sizing: border-box; border: 2px solid #777; background-color: #fff; color: #000; border-radius: 4px;" />
  </div>

  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px;">Spørgsmål:</label>
    <textarea name="message" style="width: 100%; display: block; min-height: 150px; padding: 10px; box-sizing: border-box; border: 2px solid #777; background-color: #fff; color: #000; border-radius: 4px; font-family: inherit;"></textarea>
  </div>

  <button id="my-form-button" style="padding: 10px 24px; background-color: #e91e63; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 1rem; font-weight: bold;">Send</button>
  <p id="my-form-status"></p>
</form>

<!-- Place this script at the end of the body tag -->
<script>
  var form = document.getElementById("my-form");
  
  async function handleSubmit(event) {
    event.preventDefault();
    var status = document.getElementById("my-form-status");
    var data = new FormData(event.target);
    fetch(event.target.action, {
      method: form.method,
      body: data,
      headers: {
          'Accept': 'application/json'
      }
    }).then(response => {
      if (response.ok) {
        status.innerHTML = "Tak - dit spørgsmål er modtaget!";
        form.reset()
      } else {
        response.json().then(data => {
          if (Object.hasOwn(data, 'errors')) {
            status.innerHTML = data["errors"].map(error => error["message"]).join(", ")
          } else {
            status.innerHTML = "Ups! Der opstod et problem med at sende din formular"
          }
        })
      }
    }).catch(error => {
      status.innerHTML = "Ups! Der opstod et problem med at sende din formular"
    });
  }
  form.addEventListener("submit", handleSubmit)
</script>

----

!!! tip "Opdater siden"
    For at sikre at du ser alle spørgsmål og svar, så opdater siden (ctrl+f5) i din browser efter hver session.


## Spørgsmål fra 14/1-2026 sessionen

### Spørgsmål om Git installation

Jeg ser frem til at deltage i Prosa's C# kursus, der starter i dag. Du skriver at vi skal bruge standard (Next) hele vejen ved Git Inslallation, de anbefaler man bruger anden editor, fx Visual Studio Code, i stedet for standard Vim. Er VS Code ikke bedre ?

> Jo - VS Code er absolut bedre end alternativerne efter min mening. Men det er jo nærmest religion om man er til VIM, Notepad++, VSC, Notepad eller lign. I sidste ende er det jo bare tekst, men de muligheder VSC stiller til rådighed gør det hele meget nemmere.

### Spørgsmål om AI sikkerhed

Er der tid til at komme ind på sikkerhed ifbm brug af AI en af de kommende gange?
Jeg tænker det er relevant og at mange virksomheder holder sig tilbage fordi de ikke vil have deres kode spredt og gjort tilgængelig for andre....

> Ja, det er et utroligt vigtigt emne, som vi helt sikkert vil berøre. Vi ser på, hvordan man bruger disse værktøjer ansvarligt, og hvad forskellen er på privat og professionel brug (Enterprise), hvor netop datasikkerhed er i højsædet.

### Spørgsmål om portnummer i backend README

Til dem der referer til README filen for backend, vær opmærksom på at den pt. foreslår brug af "localhost:5000" - hvorimod konfigurationen i launch settings er localhost:5033 - Urlen der benyttes til test skal bare rettes, ellers kan det ændres i launch settings ;-)

> Det har jeg rettet nu - tak for tippet!

### Spørgsmål om PWA opdateringer

PWA, hvis man laver det og efterfølgende retter siden/appliktionen, kan systemet så selv finde ud af at den skal opdateres eller skal man lave et eller andet tricky?

> Det sker heldigvis automatisk, men processen er lidt anderledes end ved almindelige hjemmesider. Browseren opdager selv ændringen via appens "Service Worker", men som standard opdateres appen først, når brugeren har lukket alle instanser af appen og åbner den igen. Dette gøres for at undgå fejl midt i brug. Man kan dog kode sig ud af det, så brugeren får en besked om at "En ny version er klar" med en opdater-knap, præcis som man kender det fra mange moderne web apps.

### Spørgsmål om Visual Studio vs VS Code

Synes der er voldsomt meget fokus på VS code - sidder lidt og mangler referencerne til visual studio - har lidt svært ved at forstå om man kan de samme ting, som der fortælles om....?

> Det er et bevidst valg for at sikre at alle kan være med uanset platform (Windows, Mac, Linux), hvor VS Code fungerer ens på tværs. Du kan sagtens bruge det "store" Visual Studio, som kan det samme og mere til - menuerne sidder bare nogle andre steder. VS Code er desuden valgt fordi det er "letvægt" og super effektivt til netop denne type webudvikling vi gennemgår.

### Spørgsmål om værktøjer i Visual Studio

Er der nogen væsentlige forskelle på brug af de nævnte værktøjer hvis man bruger Visual Studio fremfor VS Code?

> Nej - teknisk set kan du det samme. Visual Studio har typisk indbyggede grafiske menuer til tingene (f.eks. Docker og Git), hvor vi i VS Code oftere bruger terminal-kommandoer eller extensions. Men resultatet er det samme.

### Spørgsmål om .NET version

Er det nødvendigt med .NET 10 eller kan vi også bruge .NET 9 i forløbet?

> Nej, du kan sagtens bruge .NET 9. Det kræver blot en enkelt lille rettelse i backend-projektets fil (fra `net10.0` til `net9.0`) - men ellers er koden den samme.

### Spørgsmål om installation, Docker og Git

Jeg har installeret det hele (næsten), men Min Docker Desktop vil ikke starte, jeg kan godt komme til den i web (den er selvfølgelig tom). Du skriver vi skal logge ind på Git i Visual Studio Code; hvor/hvordan? Hvor skal jeg hente kode, når Git fungerer? Vil det være en fordel at hente en GUI til GIT, eller er det lige meget nu?

> **Docker Desktop:** Fortvivl ikke. Docker Desktop er valgfrit på dette kursus, så hvis det driller lokalt, kan du sagtens gennemføre alligevel.
> **Git Login:** Du skal ikke "logge ind" i selve VS Code for at bruge Git lokalt. Du skal blot sikre dig, at du har angivet dit navn og din email i terminalen som beskrevet i opsætningsguiden.
> **Hent kode:** Du finder links til al koden på GitHub under siden [Overblik](overblik.md).
> **Git GUI:** Det er ikke nødvendigt (eller ligegyldigt, om man vil). VS Code har fantastiske indbyggede værktøjer til Git, så en separat GUI er overflødig.

### Spørgsmål om Mac vs Windows

Er der nogle afgørende forskelle i at køre MAC med VS Code i stedet for Windows som du demonstrerer det hele på idag? Altså: giver det overhovedet mening at arbejde på MAC med VS code eller spænder man ben for sig selv?

> Nej, slet ikke. Mac fungerer præcis på samme måde som Windows når det gælder VS Code og de værktøjer vi bruger. Du spænder bestemt ikke ben for dig selv (mange vil endda mene det modsatte) - du kan roligt fortsætte på din Mac.

### Spørgsmål om lokal sikkerhed

Er der noget af al det her, som du beskriver, som gør at man skal være opmærksom på sikkerheden på den lokale pc/mac - altså skal man hele tiden sørge for at alt er opdateret for ikke er have lokale sikkerhedshuller?

> Man skal altid sørge for at holde sit operativsystem, .NET framework og udviklingsværktøjer opdateret – det er "best practice" uanset hvad man arbejder med. Vær også opmærksom på, at den kode vi producerer på kurset primært er "begynderkode" med fokus på læring. Vi skærer nogle hjørner for at gøre det forståeligt, hvilket betyder at der kan være sikkerhedsmæssige mangler (f.eks. ift. SQL injection eller input validering), som man ville håndtere anderledes i et professionelt produktionsmiljø.

### Spørgsmål om Entity Framework og SQL

Ift. Entity Framework og ORM generelt - findes der mulighed for at skrive SQL selv i EF (eller andre ORM), hvis nu man havde nogle queries der var kompliceret og skabte performance problemer?

> Ja, det kan man sagtens! Selv om Entity Framework (EF) er lavet til at man ikke *behøver* skrive SQL, så har det en indbygget funktion til at udføre "rå" SQL (Raw SQL). Det er meget udbredt at bruge netop til komplekse forespørgsler eller performance-tunge operationer, hvor man gerne vil optimere helt nede i databasen. Så du er ikke låst fast.
