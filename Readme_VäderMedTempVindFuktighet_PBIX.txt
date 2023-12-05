Power Bi Desktop    
VäderMedTempVindFuktighet



#Backend, M language och Power Query

 Import av data från API samt från tabell på webbsida

 Funktion med användargränssnitt för API-anrop där en variabel kan väljas

 En faktatabell och fyra värdetabeller
 En tabell för att fånga senaste refresh datetime
 En tabell för att fånga fall där värden saknas (så att de inte visas i visualisering (tabell))

 Konvertering av unix datumformat (men används inte i visualiseringar, och data ser ut att fela en timme jfr med svensk vintertid)
 Hantering av problem med sortering i alfabetisk ordning med ÅÄÖ
 Skapa kolumn för rangordning (ranking)
 Skapa ny kolumn med värden utifrån range i en annan tabell
 Tillägg av kolumner med information, ex ikoner kopplade till värden


# Datamodel: *
  Definiera key column för ingående tabeller
  Samma nyckel för de flesta tabeller och 1 till 1 relation

# Frontend, Visualiseringar, formatering, Dax 
  Definiera datatyp, ex för positionsdata

  Formatering av värden för att visa enhet i tabell

  Dax measure för konstruktion av dynamisk rubrik
  Dax measures för uträkning kring datakvalitet
  Dax Calculated column för konvertering av unicode till visuella iconer

  Dynamisk rubirk (card)
  Knapp för återställning av alla filter(bookmark)
  Slicer med hierarki i alfabetisk ordning
  Knappar med bookmärken kopplade till sig för att visa: 
  Karta med formatering av prickar i förhållande till data och textbox med värden (DAX measures) och ikon
  Multi-row card med enkel information om data i en kolumn
  Tabell med olika tyer av formatering av bakgrund eller font färg beroend på värde, exempelvis är positiva gradtal röda medan de negativa är blå.
  Filtrering mellan en del, men inte alla visualiseringar på sidan.
  Filtrering för tabell och slicer så att bara stationer som har mätvärden visas etc
  Tabeller och kolumner som inte behövs i visualiseringar är dolda

#övriga kommentarer
 Fokus ligger på att hämta data och skapa en enkel modell där så mycket som möjligt av arbetet görs i M language eller Power query och bara det sista görs i DAX.
 Syftet är alltså inte att visa det bästa sättet att visualisera på.

 Refresh i visualiseringsvyn triggar inte API anrop mot datakälla, dvs refresh-datum i rubriken är inte det samma som när data hämtades från källan.

 Ingen hänsyn har tagits till ev färgblindhet eller dygligt vid val fäger, eller optimering av canvas-storlek till ex std skärm och upplösning

 Lite "buggigt" när det kommer till lokal-inställningar och hanteringen av skiljetecken för att skilja heltal från decimaler samt datumformat.

 Har inte tillräckligt många ikoner för att täcka samtliga vädersträck varför exempelvis Västnordväst har samma ikon som Väst.

 Har valt att inte arbeta med themes file, ex färger, typsnitt, x-tra ikoner för conditional formatting etc

 ...& nästa gång det ska väljas data får den väl innehålla historisk data med lite datum att leka med...











