##Allm. info
Här används publik data kring covidvaccinationer i sveriges län och kommuner för 
att bland annat skapa visualiseringar med Shape Map i Power Bi. 
 - Shape Map
 - Bilder som URL till resurs på webben respektive i tabell konverterat till formatet BASE64
 - Ett exempel på tidsrealterad data och datumtabell i DAX
 - Sortering alfabetiskt enl svenska alfabetet
 - Enklare measures i DAX

##Prep av data för import mm

#Power Bi Shape Map för områden i Sverige
Data från SCB ger information om avgränsningar för län respektive kommuner.
Korrigering för kommunnamn: från "Malung" till "Malung-Sälen"

Informationen om hur länen ser ut innehåller inte länens hela namn, ordet "län" 
finns inte med, ex heter 'Dalarnas län' bara 'Dalarnas'.

#Data för koppling mellan län och kommun har före import poppulerats med kolumner för 
olika sätt att benämna län samt för att arbeta runt svårigheterna med att i 
Power BI sortera alfabetiskt efter det svenska alfabetet. I den här tabellen har även länk
till bild för respektive läns länsvapen lagts till.

#En tabell med bilder över respektive läns länsvapen. Nedladdning av .png biler från wikipedia länsvapen
och konvertering till BASE64 via av https://www.base64-image.de/ 

#En X-tra tabell för sortering av svenska alfabetet gjord direkt i M 
(används inte i senare i det här fallet, men kan vara bra att ha för klipp och 
klistra vid ett annat tillfälle...)


##Visualiseringar, measures etc

# Formatering av värden för att ange storhet samt underlätta läsning, 
ex uppdelning av större värden i set om tre siffror med mellanslag

# Datumtabell i DAX baserat på samtliga år som finns med i en specifik kolumn i en tabell. 
Datumtabellen innehåller samtliga datum från och med 1 januari till och med 31 December.

#Geografiskt - Shape Map för län respektive kommun - slicers och tooltip. Visining av valt län och länsvapen ( url till webbsida), tabell med information kring respektive kommun (listas i bokstavsordning) i valt områder alt. information om vald kommun. Slicer för ålderskategori.

#Åldersfördelning - bla TreeMap per län, information i Tooltip, defaultvärde för slicer med hjälp av bookmark

#ÖverTid -  bild som visar vaccinationer per län över tid - ger möjlighet till drill-down
(användning av datumtabellen)

#Länsvapen - tabell som visar län - länsvapen från tabell med BASE64  - och lista över kommuner i länet (bokstavsordning)



##Tabular Editor:

Populerar description med koden för varje Measure i modellen genom:
foreach (var m in Model.AllMeasures) { m.Description = m.Expression; } 
Det här gör att hela koden för ett Measure visas vid mouse-over.

