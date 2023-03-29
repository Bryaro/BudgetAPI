BudgetApp
BudgetApp är i grunden en bak- och front-end (i Node.js respektive React) applikation för budgethantering. Vi har lagt till inloggnings-, utloggnings- och autentiseringsmoduler, samt bakänds-funktioner för att skapa, uppdatera, visa och radera inkomster och utgifter. Användare kan även se totala inkomster och utgifter.

Innehållsförteckning
Författare och bidragsgivare
Hur man deployar applikationen
Använda resurser
Mål
<a name="deploy-app"></a>2. Hur man testar applikationen?
Följ stegen nedan för att testa bakänds-API:

Postman Collection-länk: https://www.getpostman.com/collections/2250806e9bda9762ee18
URL: https://budgetapp-api.herokuapp.com
(Endast Create User och Login kräver inte autentisering. Alla andra förfrågningar kräver autentisering.)
Request Routes:
Skapa användare

Typ: POST
Endpoint: URL/budget/users/signup
Body: { "email": "xyz@gmail.com", "password": "xyz" }
(Minsta lösenordslängd är 5)
Användarlogin

Typ: POST
Endpoint: URL/budget/users/login
Body: { "email": "xyz@gmail.com", "password": "xyz" }
Svarsheader: Kopiera värdet för nyckeln auth som kommer att användas för autentisering och ställ in detta värde i miljön med nyckeln Authorization och ställ in den nyckeln i huvudet för alla andra förfrågningar från och med nu.
Ny post

Typ: POST
Endpoint: URL/budget/add
Request Body: { "type": "Income", "description": "Första inkomsten", "amount": 400 }
Request Header: Authorization: JWT token värde (från svarsheadern hitta 'auth')
Hämta all data

Typ: GET
Endpoint: URL/budget/all
(Ställ in förfrågningshuvudet)
Hämta enskild inkomst

Typ: GET
Endpoint: URL/budget/income/:id (t.ex. id -> 5969902e3989c2063b925d4a)
(Ställ in förfrågningshuvudet)
Hämta enskild utgift

Typ: GET
Endpoint: URL/budget/expense/:id (t.ex. id -> 5969902e3989c2063b925d4a)
(Ställ in förfrågningshuvudet)
Uppdatera enskild inkomst

Typ: PUT
Endpoint: URL/budget/income/:id (t.ex. id -> `5969902e3989c2063b925d4