## V36- Konfiguration av Virtuella nätverk och internet access <br/>
**Av Felix Samuelsson** </br>
**Kurs: Microsoft Azure** </br>
Github Repo: https://github.com/03felsam/azure-mov25

##
Bygg nätverk först sedan säkerhet
Sök på Virtuella networks  
Skapa Vnet med 10.0.0.0 /16 utrymme och undernät med storlek 10.0.0.0 /24 

Gå sedan in på resurs du skapade och skapa fler subnät med /24 och med konsekvant namn i mitt fall valde jag Snet-web och en till /24 snet-db


##
Från nätverk till säker trafik

 NSG Nätverks security group

Nätverksgrund | Nätverkssäkerhetsgrupper
Skapa en ny grupp i mitt fall döper jag den till nsg-web

Skapa inbound rule med settings
Service Tag
Internet
*
Any
Custom
80,443
TCP
Allow

Skapa sedan en till rule för limiting SSH
My ipadress
*
Any
SSH
Allow
Priority  200

sedan ska vi koppla NSG till subnät
lägg till i undernät
Då den snet-web som vi skapade ska vara i rätt vnet-novatrix

Skapa ny network interface 
Med vnet du skapade och välj rätt subnet för att få det att fungera.

verifiera genom att 
surfa till servern publika IP sidan ska visas

Anslut med SSH från din adress ska fungera

mål är att webbtrafik 80/443 ska släppas igenom 
SSH 22 från min adress går igenom 
SSH 22 från annan adress blir denied
Allt annat blockas