## V34 - Driftsättning av Novatrix webbsida<br/>
**Av Felix Samuelsson** </br>
**Kurs: Microsoft Azure**

## Mål 
Målet med denna veckans uppgift är att vänja sig med de system vi kommer jobba med framöver samt skapa en fungerande ärendeformulär genom de följande stegen:
 
 - Skapa en resursgrupp samt VM av Ubuntu server i Azure
 - Anslut via SSH
 - Installerade Nginx
 - Öppna port 80
 - Designa och verkställ webbsida
 - Verifiera att allting fungerar


## Github: Commands </br> Ändra spara skicka

Under denna kursens gång kommer Github att användas som en samlingsplats av alla alla genomgångar och bevis av uppgifter som har gjorts. Under labbningarnas gång kommer jag spara och anteckna vad jag har gjort och pusha det till github efter jag är klar för dagen. Detta kommer inte antecknas i denna README utan kommer beskriva processen och kommandon jag använder under tiden men det kommer inte noteras i genomgången.

##

````
git status
````
Git status används för att visa vilka filer som är med i den senaste git commit. 

````
git add .
````
 git add . markerar alla filer som har ändrats i ditt lokala repo och lägger till dom så de är redo att commitas.
 genom att manipulera vad som står efter git add får vi olika filer som läggs till i din commit. Genom att använda punkt så läggs alla filer som har ändrats med i din commit men annars kan specifika filer läggas till genom att skriva filnamnen. 

 ```` 
git commit -m"Exempel" 
 ````
 Commitar en lokal sparnings punkt för alla filer du har lagt till genom git add och sparar det lokalt vilket du kan senare pusha till git hub. </br>
-m är för messanget som hänger med din lokala commit vilket borde beskriva ändringarna på ett kort och enkelt sätt för enklare hantering av loggar.

```` 
git push
````
Skickar din senaste huvud commit till din github online och sparar allting i molnet 

````
git clone <repots-url>
````
Används första gången man skapar en anslutnign med din github repo online och ditt lokala repo genom att klona allting online och skapa mappar och filer lokalt. 

## Steg 1 : Skapa resurser i Azure

För att följa denna guide är förutsättningarna att den följande listan är klar :
- Azure konto uppsatt med en premuration eller inlagda krediter
- Git installerat
- Skapat github konto och repo
- Installera Visualstuido code
- Valfritt : installeraAzure CLI

</br>
Alla resurser inom Azure kommer ligga inom resursgrupper och är det första vi kommer skapa.
Detta gör vi genom att söka på resursgrupper inom Azure portalen samt kolla uppe i vänstra hörnet på ett plus där det står "skapa".


</br>
Skapa VM </br>
Storlek: **B2ats_v2** </br>
Namn konsekvent undvik åäö och mellanslag</br>
Samma Region som din resursgrupp</br>
SSH nyckel </br>


## Steg 2: Anslut till Ubuntu Server VM via SSH

Behörigheter med nyckel
````
icals.\din-nyckel.pem /inhertiance:r
````
````
icals .\din-nyckel.pem /grant:r "$($env:USERNAME):R"
````
````
ssh -i din-nyckel-pem azureuser@DUN-PUBLIKA-IP
````


## Steg 3 : Ubuntu server tips

Starta med att uppdatera servern med 
````
sudo apt update
````

##  Steg 4 : Installera Nginx

````
sudo apt install nginx -y
````

browsa till public websida

Öppna port 80 /22
Vi andänder http inte https


## Steg 5: Redigera Nginx webbsida
mappen med Nginx ligge på /var/www/html

````
sudo nano index.html
````