# Puzzle site
 
Ik wil een website maken, die een dagelijkse puzzel heeft. Wanneer je de puzzel oplost wordt je score opgeslagen en op een leaderboard laten zien.

## User stories
UC01 Als speler wil ik dat er een puzzel op de hoofdpagina staat.

UC02 Als speler wil ik dat er elke dag een nieuwe puzzel is, zodat ik opnieuw wordt uitgedaagd.

UC03 Als speler wil ik zien hoe hoog ik op een puzzel gescoord heb, om te beoordelen hoe ik het gedaan heb.

UC04 Als speler wil ik zien hoe hoog mijn dagelijkse score is vergeleken met andere spelers, zodat ik mijn niveau vergeleken met andere weet.

UC05 Als speler wil ik een algemene score gebaseerd op meerdere recent op geloste puzzels, zodat ik weet wat mijn algemene niveau is.

UC06 Als speler wil ik zien hoe hoog mijn algemene score is vergeleken met andere spelers, zodat ik mijn niveau vergeleken met andere weet.

UC07 Als speler wil ik kunnen zien, wat mijn recente dagelijkse scores waren, zodat ik weet hoe ik op welke dag gescoord heb.

UC08 Als speler wil ik een naam kunnen invoeren die mij op het scorebord vertegenwoordigd, zodat ik kan zien hoe hoog ik op de ranglijst sta.

## Design 
Op basis van de user stories ben ik tot dit design gekomen.
![image](https://user-images.githubusercontent.com/49039524/174486089-3629245c-6512-4408-afb5-971de10a2692.png)

### Puzzle-service
UC01 en UC02 vallen onder de puzzle-service. In de database staan puzzels klaar met bij behorende datums. Wanneer de home page geladen wordt, wordt er een get request naar de puzzle-service gestuurd en levert dan de puzzel. Wanneer er een antwoord wordt gegeven, wordt die eerst door de puzzle-service gecontrolleerd.

### Leaderboard-service
 UC03, UC04, UC05 en UC07 vallen oner de leaderboard-service. 
 
#### UC03 en UC04
Wanneer er een juist antwoord geweest is gegeven door de speler, wordt er vanaf de home page een post request naar de leaderboard-service gestuurd. In de request staan de naam van de speler, de behaalde score en de datum van de puzzel. Wanneer je de leaderboard page opent wordt er automatisch een get request gestuurd. Die geeft alle scores van vandaag waaronder die van de speler terug. Deze worden op de webpage laten zien.

### UC05
Wanneer je de leaderboard page opent wordt er nog een get request automatisch gestuurd. Deze vraagt de leaderboard-service alle scores in de database per naam op te tellen. Deze totale scores worden terug gestuurd en laten zien op de webpage.

### UC07
Persoonlijke recente scores vind ik eigenlijk niet bij het leaderboard passen. Daarom vraag ik ze niet op bij de leaderboard page. Deze wil ik later nog op een andere page plaatsen.

### Name-service
UC08 valt onder deze service. Ik heb met firebase gemaakt dat je kan inloggen met google op mijn home page. Wanneer je dit gedaan hebt, kun je een naam invoeren. Deze wordt samen met je email door een post request naar de name-service verstuurd. Daar wordt hij opgeslagen in een database. Wanneer je een puzzel oplost wordt je naam door middel van een get request opgevraagt en met je score mee gestuurd naar de leaderboard-service.


