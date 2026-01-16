---
created: 2026-01-10
modified: 2026-01-10
author: Michell Cronberg
---
# Backend

## Hent eksempel kode

Hele backend-koden er tilgængelig på GitHub, så du kan følge med, eksperimentere og køre applikationen lokalt.

### Clone repository

Åbn en terminal og kør:

```bash
git clone https://github.com/devcronberg/Northwind.App.Backend.git
cd Northwind.App.Backend
```

### Eller download som ZIP

Hvis du ikke har Git installeret, eller foretrækker at hente koden som en ZIP-fil:

1. Gå til [https://github.com/devcronberg/Northwind.App.Backend](https://github.com/devcronberg/Northwind.App.Backend)
2. Klik på den grønne **Code** knap
3. Vælg **Download ZIP**
4. Pak ZIP-filen ud på din computer
5. Åbn mappen i en terminal eller VS Code

### Kør applikationen

1. **Restore dependencies**

```bash
dotnet restore
```

2. **Kør applikationen**

```bash
dotnet run
```

3. **Åbn Swagger UI**

Gå til [http://localhost:5003/swagger](http://localhost:5003/swagger) i din browser.

### Test API'et

**Eksempel 1: Hent alle kunder (ingen authentication)**

```bash
curl http://localhost:5003/api/public/customers
```

**Eksempel 2: Login og få JWT token**

```bash
curl -X POST http://localhost:5003/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"admin","password":"admin"}'
```

**Eksempel 3: Brug JWT token til beskyttet endpoint**

```bash
curl http://localhost:5003/api/customers \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

### Live Demo

API'et er også deployed og tilgængeligt online:

🔗 **[https://northwind-backend-b088.onrender.com](https://northwind-backend-b088.onrender.com)**

- **Swagger UI**: [https://northwind-backend-b088.onrender.com/swagger](https://northwind-backend-b088.onrender.com/swagger)
- **Health Check**: [https://northwind-backend-b088.onrender.com/health/live](https://northwind-backend-b088.onrender.com/health/live)
- **Version**: [https://northwind-backend-b088.onrender.com/version](https://northwind-backend-b088.onrender.com/version)

!!! warning "Render.com Free Tier"
    Applikationen kører på Render.com's gratis tier, som automatisk "sover" efter 15 minutter uden aktivitet. Den første request efter søvn kan tage 30-50 sekunder, mens tjenesten vågner op. Dette er normalt for free-tier deployments.

### Demo Credentials

```json
{
  "username": "admin",
  "password": "admin"
}
```

eller

```json
{
  "username": "user",
  "password": "user"
}
```


## Hvad er en Backend?

En **backend** er den del af en webapplikation, der kører på en server og håndterer:

- **Data**: Gemmer og henter information fra en database
- **Forretningslogik**: Udfører beregninger, valideringer, og regler
- **Authentication**: Sikrer at kun autoriserede brugere har adgang
- **API**: Udstiller endpoints som frontend kan kalde


## Hvad er et REST API?

**REST** (Representational State Transfer) er en arkitektur for at bygge webservices. Et REST API bruger HTTP-protokollen til at kommunikere.

### HTTP Metoder (Verbs)

| Metode   | Formål               | Eksempel             |
| -------- | -------------------- | -------------------- |
| `GET`    | Hent data            | Hent liste af kunder |
| `POST`   | Opret nyt            | Opret ny kunde       |
| `PUT`    | Opdater eksisterende | Opdater kunde info   |
| `DELETE` | Slet                 | Slet en kunde        |

### HTTP Status Codes

| Kode                        | Betydning       | Eksempel                |
| --------------------------- | --------------- | ----------------------- |
| `200 OK`                    | Success         | Data hentet succesfuldt |
| `201 Created`               | Oprettet        | Ny kunde oprettet       |
| `400 Bad Request`           | Ugyldig request | Manglende felter        |
| `401 Unauthorized`          | Ikke logget ind | Manglende JWT token     |
| `404 Not Found`             | Findes ikke     | Kunde ID findes ikke    |
| `500 Internal Server Error` | Serverfejl      | Uventet exception       |

### RESTful Endpoints

Endpoints følger et konsistent mønster:

```
GET    /api/customers          → Hent alle kunder
GET    /api/customers/ALFKI    → Hent specifik kunde
POST   /api/customers          → Opret ny kunde
PUT    /api/customers/ALFKI    → Opdater kunde
DELETE /api/customers/ALFKI    → Slet kunde
```


## Projektets Teknologier

### 1. **.NET 10**
- Microsofts moderne, cross-platform framework
- Open source
- Kører på Windows, Linux, macOS

### 2. **ASP.NET Core Web API**
- Framework til at bygge HTTP APIs
- Hurtig, skalerbar, cloud-ready
- Indbygget dependency injection

### 3. **Entity Framework Core**
- ORM (Object-Relational Mapper)
- Mapper C# klasser til database tabeller
- LINQ queries i stedet for SQL
- Code-first approach

### 4. **SQLite**
- Filbaseret database (ingen server nødvendig)
- Perfekt til demos og udvikling
- Northwind.db filen i Assets mappen

### 5. **JWT (JSON Web Tokens)**
- Token-baseret authentication
- Stateless (server gemmer ingen session)
- Secure transmission af brugeridentitet

### 6. **Serilog**
- Struktureret logging library
- Logger til console (container-ready)
- Nemt at tilføje andre sinks (filer, Seq, Application Insights)

### 7. **Swashbuckle**
- Genererer OpenAPI/Swagger dokumentation
- Interaktiv API test interface
- Automatisk fra controller annotations

## Database og Entity Framework

### Northwind Database

Northwind er en klassisk demo-database fra Microsoft, der simulerer en importvirksomhed:

**Tabeller**:

- **Customers**: Kunder (CompanyName, ContactName, Country, etc.)
- **Orders**: Ordrer (OrderDate, CustomerID, ShipAddress, etc.)
- **Products**: Produkter (ProductName, UnitPrice, UnitsInStock, etc.)
- **Categories**: Kategorier (CategoryName, Description)
- **Suppliers**: Leverandører
- **Employees**: Medarbejdere
- **Shippers**: Fragtfirmaer

### Entity Framework Core

EF Core mapper database tabeller til C# klasser:

```csharp
// Models/EF/Customer.cs
public class Customer
{
    public string CustomerId { get; set; }      // Primary key: ALFKI
    public string CompanyName { get; set; }     // Alfreds Futterkiste
    public string ContactName { get; set; }     // Maria Anders
    public string Country { get; set; }         // Germany
    
    public ICollection<Order> Orders { get; set; }  // Navigation property
}
```

**DbContext** er forbindelsen til databasen:

```csharp
// Models/EF/NorthwindContext.cs
public class NorthwindContext : DbContext
{
    public DbSet<Customer> Customers { get; set; }
    public DbSet<Order> Orders { get; set; }
    public DbSet<Product> Products { get; set; }
    
    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlite("Data Source=Assets/Northwind.db");
    }
}
```

### Queries med LINQ

I stedet for SQL bruges LINQ (Language Integrated Query):

```csharp
// SQL: SELECT * FROM Customers WHERE Country = 'Germany'
var customers = await _context.Customers
    .Where(c => c.Country == "Germany")
    .ToListAsync();

// SQL: SELECT * FROM Customers JOIN Orders...
var customerWithOrders = await _context.Customers
    .Include(c => c.Orders)
    .FirstOrDefaultAsync(c => c.CustomerId == id);
```

**AsNoTracking()**: Bruges til read-only queries for performance:

```csharp
var customers = await _context.Customers
    .AsNoTracking()  // EF Core tracker ikke ændringer
    .ToListAsync();
```

---

## Controllers og Endpoints

### Hvad er en Controller?

En controller er en C# klasse, der håndterer HTTP requests og returnerer responses:

```csharp
[ApiController]
[Route("api/[controller]")]
public class CustomersController : ControllerBase
{
    private readonly NorthwindContext _context;
    private readonly ILogger<CustomersController> _logger;
    
    public CustomersController(NorthwindContext context, ILogger<CustomersController> logger)
    {
        _context = context;  // Dependency Injection
        _logger = logger;
    }
    
    [HttpGet]
    public async Task<ActionResult<IEnumerable<Customer>>> GetCustomers()
    {
        _logger.LogInformation("Fetching all customers");
        var customers = await _context.Customers.AsNoTracking().ToListAsync();
        return Ok(customers);  // 200 OK
    }
}
```

### Route Mapping

**Attributes** definerer hvordan URLs mapper til metoder:

```csharp
[Route("api/[controller]")]  // [controller] = "customers"
public class CustomersController : ControllerBase
{
    [HttpGet]                              // GET /api/customers
    public async Task<ActionResult> GetAll() { }
    
    [HttpGet("{id}")]                      // GET /api/customers/ALFKI
    public async Task<ActionResult> GetById(string id) { }
    
    [HttpPost]                             // POST /api/customers
    public async Task<ActionResult> Create([FromBody] Customer customer) { }
    
    [HttpPut("{id}")]                      // PUT /api/customers/ALFKI
    public async Task<ActionResult> Update(string id, [FromBody] Customer customer) { }
    
    [HttpDelete("{id}")]                   // DELETE /api/customers/ALFKI
    public async Task<ActionResult> Delete(string id) { }
}
```

### Dependency Injection

ASP.NET Core har indbygget DI (Dependency Injection):

**Registrering** (Program.cs):
```csharp
builder.Services.AddDbContext<NorthwindContext>();
builder.Services.AddScoped<IMyService, MyService>();
```

**Brug** (Controller):
```csharp
public class CustomersController : ControllerBase
{
    private readonly NorthwindContext _context;
    
    // ASP.NET Core injicerer automatisk NorthwindContext
    public CustomersController(NorthwindContext context)
    {
        _context = context;
    }
}
```

### Response Types

**ProducesResponseType** dokumenterer mulige responses til Swagger:

```csharp
[HttpGet("{id}")]
[ProducesResponseType(StatusCodes.Status200OK, Type = typeof(Customer))]
[ProducesResponseType(StatusCodes.Status404NotFound)]
public async Task<ActionResult<Customer>> GetById(string id)
{
    var customer = await _context.Customers.FindAsync(id);
    
    if (customer == null)
        return NotFound();  // 404
    
    return Ok(customer);    // 200
}
```

---

## Authentication med JWT

### Hvad er JWT?

**JWT (JSON Web Token)** er en sikker måde at transmittere information mellem parter.

**Struktur**: `header.payload.signature`

Eksempel JWT:
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.
eyJzdWIiOiJhZG1pbiIsInJvbGUiOiJBZG1pbiIsImV4cCI6MTYyMzQ1Njc4OX0.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

**Payload** (decoded):
```json
{
  "sub": "admin",
  "role": "Admin",
  "exp": 1623456789
}
```

### Token Flow

1. **Login**: Bruger sender username/password
2. **Validate**: Server checker credentials
3. **Generate**: Server genererer JWT token
4. **Return**: Token sendes til klient
5. **Store**: Klient gemmer token (localStorage/memory)
6. **Use**: Klient sender token i hver request: `Authorization: Bearer <token>`
7. **Validate**: Server validerer token ved hver request

### Access Token vs Refresh Token

**Access Token**:
- Kort levetid (60 minutter)
- Bruges til hver API request
- Indeholder brugerinfo (claims)

**Refresh Token**:
- Lang levetid (7 dage)
- Bruges kun til at få ny access token
- Kan revokes (logges ud)

### Login Endpoint

```csharp
[HttpPost("login")]
public async Task<ActionResult<LoginResponse>> Login([FromBody] LoginRequest request)
{
    // 1. Validate credentials (demo: hardcoded users)
    var user = ValidateUser(request.Username, request.Password);
    if (user == null)
        return Unauthorized("Invalid credentials");
    
    // 2. Generate tokens
    var accessToken = GenerateAccessToken(user);
    var refreshToken = GenerateRefreshToken();
    
    // 3. Store refresh token (in-memory for demo, database for production)
    _refreshTokens[refreshToken] = (user.Username, DateTime.UtcNow.AddDays(7));
    
    // 4. Return tokens
    return Ok(new LoginResponse
    {
        AccessToken = accessToken,
        RefreshToken = refreshToken,
        ExpiresIn = 3600,
        Username = user.Username,
        Role = user.Role
    });
}
```

### Protected Endpoints

**[Authorize]** attribute kræver valid JWT:

```csharp
[Authorize]  // Kræver valid access token
[HttpGet]
public async Task<ActionResult<IEnumerable<Customer>>> GetCustomers()
{
    // Denne metode kan kun kaldes med valid JWT token
    var username = User.Identity.Name;  // Fra token claims
    _logger.LogInformation("User {Username} fetching customers", username);
    
    var customers = await _context.Customers.AsNoTracking().ToListAsync();
    return Ok(customers);
}
```

### Configuration (appsettings.json)

```json
{
  "Jwt": {
    "Secret": "ThisIsASecretKeyForDemoOnlyChangeInProduction123!",
    "Issuer": "Northwind.App.Backend",
    "Audience": "Northwind.App.Frontend",
    "AccessTokenExpirationMinutes": 60,
    "RefreshTokenExpirationDays": 7
  }
}
```

⚠️ **Vigtigt**: I produktion skal `Secret` være en environment variable, ALDRIG hardcoded!

---

## Logging og Monitoring

### Structured Logging med Serilog

**Structured logging** logger data som strukturerede events i stedet for plain text:

❌ **Old way**:
```csharp
Console.WriteLine("User admin logged in at 2026-01-04");
// Svært at parse, søge, filtrere
```

✅ **New way**:
```csharp
_logger.LogInformation("User {Username} logged in at {Timestamp}", "admin", DateTime.UtcNow);
// Output: {"Username": "admin", "Timestamp": "2026-01-04T10:30:00Z", "Message": "User admin logged in"}
// Nemt at søge, filtrere, analysere
```

### Log Levels

| Level         | Hvornår bruges                 | Eksempel                              |
| ------------- | ------------------------------ | ------------------------------------- |
| `Trace`       | Meget detaljeret debugging     | "Entering method X with param Y"      |
| `Debug`       | Debugging info                 | "Query returned 5 rows"               |
| `Information` | Normal flow                    | "User logged in", "Customer created"  |
| `Warning`     | Noget uventet men ikke kritisk | "Slow query", "Deprecated API called" |
| `Error`       | Fejl der skal fixes            | "Database connection failed"          |
| `Critical`    | Alvorlige fejl                 | "Out of memory", "Data corruption"    |

### Configuration (appsettings.json)

```json
{
  "Serilog": {
    "Using": [ "Serilog.Sinks.Console" ],
    "MinimumLevel": {
      "Default": "Information",
      "Override": {
        "Microsoft": "Warning",
        "System": "Warning"
      }
    },
    "WriteTo": [
      { "Name": "Console" }
    ]
  }
}
```

**Forklaring**:
- `Default: Information`: Log alt på Information level og højere
- `Microsoft/System: Warning`: Reducer noise fra framework (kun warnings+)
- `WriteTo: Console`: Log til stdout (perfekt til containers)

### Logging i Controllers

```csharp
public class CustomersController : ControllerBase
{
    private readonly ILogger<CustomersController> _logger;
    
    public CustomersController(ILogger<CustomersController> logger)
    {
        _logger = logger;
    }
    
    [HttpGet]
    public async Task<ActionResult> GetCustomers()
    {
        _logger.LogInformation("Fetching all customers");
        
        try
        {
            var customers = await _context.Customers.ToListAsync();
            _logger.LogInformation("Retrieved {Count} customers", customers.Count);
            return Ok(customers);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Failed to retrieve customers");
            throw;  // Global error handler tager over
        }
    }
}
```

### Health Checks

Health checks fortæller om applikationen kører korrekt:

**Endpoints**:
- `/health` - Basic ASP.NET Core health check
- `/health/live` - Liveness probe (bruges af Kubernetes/Docker)
- `/health/ready` - Readiness probe (checker database connection)

**Kubernetes/Docker bruger disse til**:
- **Liveness**: Er container alive? (genstart hvis nej)
- **Readiness**: Er container klar til trafik? (fjern fra load balancer hvis nej)

---

## Swagger/OpenAPI Dokumentation

### Hvad er Swagger?

**Swagger UI** er en interaktiv webside, der:
- Viser alle API endpoints
- Dokumenterer request/response format
- Lader dig teste API'et direkte i browseren
- Genereres automatisk fra controller kode

**OpenAPI** er standarden, Swagger er implementationen.

### Adgang

Start applikationen og gå til: `https://localhost:5001/swagger`

### Features

1. **Endpoint liste**: Alle controllers og metoder
2. **Try it out**: Test API uden Postman
3. **Schemas**: Se request/response modeller
4. **Authentication**: Login og brug JWT token

### Annotations

Controllers bruger attributes til at dokumentere API'et:

```csharp
/// <summary>
/// Gets all customers from the database
/// </summary>
/// <returns>List of customers</returns>
/// <response code="200">Returns the list of customers</response>
[HttpGet]
[ProducesResponseType(StatusCodes.Status200OK, Type = typeof(IEnumerable<Customer>))]
public async Task<ActionResult<IEnumerable<Customer>>> GetCustomers()
{
    // ...
}
```

### JWT Authentication i Swagger

1. Klik på **"Authorize"** knap (lås-ikon)
2. Login via `/api/auth/login` endpoint
3. Kopier `accessToken` fra response
4. Indsæt i "Authorize" dialog: `Bearer <token>`
5. Nu kan du kalde protected endpoints

---

## Docker og Containerisering

### Hvad er en Container?

En **container** er en let, standalone pakke, der indeholder:
- Din applikation
- Runtime (.NET)
- Libraries
- Dependencies
- Configuration

**Fordele**:
- ✅ "Virker på min maskine" problem løst
- ✅ Samme miljø i development, test, production
- ✅ Hurtig deployment
- ✅ Nem skalering
- ✅ Isolation (hver app i sin container)

**Docker** vs **VM**:
- VM: Fuld OS, stor, langsom boot
- Container: Deler host OS kernel, lille, hurtig boot (sekunder)

### Dockerfile

**Dockerfile** er en opskrift på hvordan containeren bygges:

```dockerfile
# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src
COPY ["Northwind.App.Backend.csproj", "./"]
RUN dotnet restore
COPY . .
RUN dotnet build -c Release -o /app/build

# Stage 2: Publish
FROM build AS publish
RUN dotnet publish -c Release -o /app/publish /p:UseAppHost=false

# Stage 3: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS final
WORKDIR /app

# Security: Run as non-root user
RUN groupadd -g 1001 appuser && \
    useradd -r -u 1001 -g appuser appuser
USER appuser

COPY --from=publish /app/publish .

# Dynamic port binding
ENV PORT=8080
EXPOSE 8080

ENTRYPOINT ["dotnet", "Northwind.App.Backend.dll"]
```

**Multi-stage build** fordele:
- Stage 1: SDK image (stor, 700MB) - kun til build
- Stage 3: Runtime image (lille, 200MB) - til produktion
- Resultat: Mindre image, hurtigere deployment

### Docker Commands

**Build image**:
```bash
docker build -t northwind-backend .
```

**Run container**:
```bash
docker run -d -p 8080:8080 --name northwind northwind-backend
```

**View logs**:
```bash
docker logs northwind
```

**Stop container**:
```bash
docker stop northwind
```

**Remove container**:
```bash
docker rm northwind
```

### Environment Variables

I produktion overskrives config med environment variables:

```bash
docker run -d \
  -p 8080:8080 \
  -e Jwt__Secret="ProductionSecretKey123!" \
  -e ConnectionStrings__DefaultConnection="Server=..." \
  northwind-backend
```

---

## Cloud Deployment

### Render.com

Render er en moderne cloud platform (alternativ til Heroku):

**Features**:
- ✅ Git-baseret deployment (push to deploy)
- ✅ Automatisk SSL (HTTPS)
- ✅ Health checks
- ✅ Environment variables
- ✅ Auto-scaling
- ✅ Gratis tier (med begrænsninger)

### render.yaml (Blueprint)

```yaml
services:
  - type: web
    name: northwind-backend
    runtime: docker
    region: frankfurt
    plan: free
    
    healthCheckPath: /health/live
    
    envVars:
      - key: ASPNETCORE_ENVIRONMENT
        value: Production
      - key: Jwt__Secret
        generateValue: true
      - key: PORT
        value: 8080
```

**Deployment proces**:
1. Push kode til GitHub
2. Connect GitHub repo til Render
3. Render detekterer `render.yaml`
4. Bygger Docker image
5. Deployer til Frankfurt region
6. Applikation tilgængelig på `https://[app-name].onrender.com`

### Free Tier Begrænsninger

⚠️ **Render Free Tier**:
- Spinner ned efter 15 min inaktivitet
- Første request efter spin-down tager 30-60 sek
- 750 timer/måned gratis
- Perfekt til demos, ikke production

---

## Sikkerhed

### Implementerede Sikkerhedstiltag

✅ **JWT Authentication**
- Token-baseret, stateless
- Configurable expiration
- Refresh token rotation

✅ **HTTPS**
- TLS encryption
- Response compression kun over HTTPS

✅ **Non-root Container User**
- Kører som UID/GID 1001
- Begrænset systemadgang

✅ **Problem Details (RFC 7807)**
- Konsistent error format
- Ingen stack traces i produktion

✅ **Health Checks**
- Liveness/Readiness probes
- Monitoring integration

### Sikkerhedsforbedringer til Produktion

⚠️ **Nuværende begrænsninger (demo)**:

1. **JWT Secret hardcoded**
   ```csharp
   // appsettings.json - IKKE SIKKERT!
   "Jwt": {
     "Secret": "ThisIsASecretKeyForDemoOnlyChangeInProduction123!"
   }
   ```
   **Fix**: Brug environment variable eller Azure Key Vault

2. **In-memory Token Storage**
   ```csharp
   // AuthController.cs
   private static Dictionary<string, (string Username, DateTime Expiry)> _refreshTokens = new();
   ```
   **Problem**: Forsvinder ved restart, virker ikke med multiple instances
   **Fix**: Redis, database, eller distributed cache

3. **Hardcoded Demo Users**
   ```csharp
   if (request.Username == "admin" && request.Password == "admin")
   ```
   **Fix**: Database med hashed passwords (bcrypt, Argon2)

4. **CORS Allow All**
   ```csharp
   policy.AllowAnyOrigin()
   ```
   **Fix**: Specificer konkrete origins

5. **SQLite Database**
   - Filbaseret, ikke skalerbar
   **Fix**: PostgreSQL, SQL Server, eller Azure SQL

### Best Practices

**Environment-specific Configuration**:
```csharp
// Program.cs
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();  // Kun i development
}
else
{
    app.UseHsts();     // Kun i production
}
```

**Password Hashing**:
```csharp
// Brug aldrig plain text passwords!
using System.Security.Cryptography;
using Microsoft.AspNetCore.Cryptography.KeyDerivation;

string hashedPassword = Convert.ToBase64String(KeyDerivation.Pbkdf2(
    password: password,
    salt: salt,
    prf: KeyDerivationPrf.HMACSHA256,
    iterationCount: 100000,
    numBytesRequested: 256 / 8));
```

**Rate Limiting**:
```csharp
// .NET 7+ indbygget rate limiting
builder.Services.AddRateLimiter(options =>
{
    options.AddFixedWindowLimiter("fixed", options =>
    {
        options.PermitLimit = 10;
        options.Window = TimeSpan.FromSeconds(10);
    });
});
```

