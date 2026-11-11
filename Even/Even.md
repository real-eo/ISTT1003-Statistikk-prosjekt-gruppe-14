## Data

### Kilde
*Hvor dataene kommer fra (Zomato via Kaggle), hva en rad er, og hvor mange
restauranter og kolonner rådataene har.*
Vi hentet datasettet vårt fra Kaggle. Datasettet var en oversikt over resturanter i flere ulike land med informasjon som pris, vurdering og tjenester tilbudt. Dette ble hentet fra Zomato som er en indisk plattform for resurantvurderinger. Deretter renset vi datasettet for å gjøre analysen mulig. For dette kjørte vi en rensekode i python som skulle fjerne unødvendig kolloner, feilaktig data og irrelevant data. Datasettet besto orginalt av 9551 elementer med 21 ulike kolloner med informasjon. Etter rensing ble dette til 6504 elementer med 10 kolonner med gammel og ny data. 

Kilde: https://www.kaggle.com/datasets/... (lim inn lenken dere brukte)

### Avgrensning og rensing
*Én setning per steg: hvorfor bare India, hvorfor vurdering 0 = manglende,
hvorfor pris 0 fjernes. Nevn også hvilke kolonner som ble droppet og hvorfor.*


Det urensede datasettet inneholdt vurderinger fra flere land. Vi har valgt å fjerne alle som ikke var i India. Dette er fordi det kan være upolitlihet assosiert med å sammenligne på tvers av landegrenser. Det samme gjelder alt som ikke er oppgitt i samme valuta. Ulik kurs og lokal økonomi gjør en slik sammenligning svært omfatende og utenfor det vi ønsket å undersøke. Vi opplevde også at 18 resturanter hadde 0 i pris. 9 av disse overlever rensingen basert på land og valuta. Vi fjerner også disse resturantene fra analysen fordi 0 pris økonomisk sett ikke mulig over lang tid. At disse stemmer er svært usannsynlig. Vi opplevde også at et stort antall (2148) resturanter hadde 0 i vurdering. Zomato skalaen går kun fra 1-5 så en vurdering på 0 er åpenbart feil. Zomato har trolig brukt verdien 0 til å representere manglende data. Derfor fjerner vi disse. I tilegg droppet vi kolonnen for "Switch to order menu". Denne var lik for alle resturanter og var dermed ikke et interesant datapunkt. "Is delivering now" ble droppet fordi den er tidsavhening. Det vil si at informasjonen i kolonnen vil variere utifra om resturanten tilbød tjesten i det øyeblikket datasettet orginalt ble samlet. "Rating text" ble droppet fordi det ikke forteller oss noe "Aggregate rating" ikke allerede gjør.

| Steg | Antall rader |
|---|---|
| Rådata | 9 551 |
| Bare India | 8 652 |
| Fjernet ikke-vurderte (vurdering 0) | 6 513 |
| Fjernet pris 0 | 6 504 |

### Variabler
*Si hva som er respons, og hva som er forklaringsvariabler.*

For vurderingen vår ser vi på både respons-og forklaringsvariabler. Responsvariablen vi ser på er vurderingen. For regresjonsanalysen bruker vi vurderingen slik den kommer, altså på en skala fra 1-5. I klassifikajsonen bruker vi den binære varianten hvor en høy vurdering (minst 3.5) tar verdien 1, og en lav vurdering tar verdien 0. Forklaringsvariablene våre er pris, antall stemmer, bordbestilling, nettlevering, og by. 

| Variabel | Betydning | Type / enhet |
|---|---|---|
| `rating` | Gjennomsnittlig Zomato-vurdering | Kontinuerlig, 1–5 |
| `high_rating` | 1 hvis `rating` ≥ 3,5 | Binær |
| `cost` / `log_cost` | Gjennomsnittspris for to personer / log av den | Rupi / log(rupi) |
| `votes` / `log_votes` | Antall vurderinger / log av det | Antall / log(antall) |
| `table_booking` | Tilbyr bordbestilling | Binær |
| `online_delivery` | Tilbyr nettlevering | Binær |
| `city` | New Delhi, Gurgaon, Noida eller Other | Kategorisk |

### Transformasjoner
*Hvorfor log av pris og stemmer, hvorfor de dyre restaurantene beholdes,
hvorfor price_range ikke brukes (korrelasjon 0,89), og hvorfor grensen
for høy vurdering er 3,5 (41 % av restaurantene).*

For å avgjøre om datasettet skulle kuttes av på ekstremalverdiene gjorde vi en rekke vurderinger. Den dyreste resturanten kostet 8000 rupee for 2 personer. Det er dyrt sammenlignet med medianverdien på 500 rupee, men ikke noe som får oss til å tro det er noe feil i datasettet. Det var 40 resturanter som ble ansett som dyre med grense på over 4000 rupee for 2. Vi bruker den naturlig logaritmen av prisen for å passe på at ekstremalverdiene ikke har uproposjonal påvirkning på resultatene våre. Vi bruker også logtransformasjon for antall stemmer siden fordi de er enda mer skjevfordelt med varisjon fra 4 til nesten 11 000, med median på 49. Logtransformasjonen er derfor en løsning på å gjøre høyreforskjøvet data mer symetriske. Vi får da mindre innflytelse fra ekstremalverdiene og mer lineær sammenheng. For klyngeanalyse og andre avstandsbaserte analysemetoder som KNN vil vi også se kortere avstander over hele datasettet, men avstandene blir mer komprimert jo større de er. Det gjør at enkelte verdier ikke dominerer på samme måte.Utover de tekniske grunnene til å ikke fjerne de dyreste resturantene mener vi også at å beholde dem er nødvendig for å svare på H1. Vi vil få bedre svar på det vi satt ut for å finne av ved å inkludere dem.


*Train/test-splitt: 80/20, stratifisert på high_rating, 5 203 og 1 301 rader.*

### Begrensninger
*Bare Delhi-området. Antall stemmer favoriserer etablerte restauranter.*
