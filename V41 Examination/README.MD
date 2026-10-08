# V41 – Examination,  Konfigurering av Nordvik

**Av Felix Samuelsson**

**Kurs: Microsoft Azure**

GitHub Repo: [https://github.com/03felsam/azure-mov25](https://github.com/03felsam/azure-mov25)

## Mål
Del 1 Dokumentation : Redogör Miljön samt val

- Vm - Ska hantera mellan 70 anmälningar per dygn och 300 under stress, samt 1800 inloggningar per dag till portalen (storlek på VM samt månadskostnad och uppetid)

- Budget 2500 kr per månad vill inte betala för kapacitet som står oanvänd nattetid, Ekonomi vill kunna följa kostnad per fastiget så resurser ska vara taggade?

- Lagring: 5-10 GB per år av aktivt använda bilder för ärenden
40 gig för sällan använda kontrakt (hot and cold storage med två olika containrar) 

- Uptime ska vara 99,,5% av kontorstid (vet inte riktigt)

- Tillväxt ska kunna resa en likadant test eller demomiljö snabbt (gör kod)  

- Säkerhet RBAC och begränsad access till bland annat VM samt blobstorage




Del 2 Praktisk del






##

För valen av Central azure tjänst för portalen kan vi välja mellan att använda en VM, Container eller Serverless lösning. För att välja vilken typ som passar best för Nordviks miljö behöver vi göra ett flertal listor med positiva och negativa delar.

### VM

Att portalen finns på en uppsatt VM innebär att du har en hel dator som du behöver underhålla. Detta innebär mycket driftansvar samt hög flexibilitet när det gäller konfiguration. Dock innebär det även att företaget behöver ha kvalificerad personal som vet hur man tar hand om en VM och ser till att den kan underhållas under ett flertal år.

Dessutom är VM-kostnaden en konstant kostnad så länge den är uppsatt, vilket innebär att det är en kostnad som kommer att finnas även under nattetid. Detta var specifikt nämnt i budgeten där **Nordvik vill inte betala för kapacitet som står oanvänd nattetid**, vilket är en av anledningarna till att jag tror att detta är fel val när det gäller att ha en VM som host för portalen.

En annan anledning till att en VM inte skulle passa är att för att uppfylla kravet på 99,95 % uptime under kontorstid behöver vi enligt [Microsoft Learn – Availability sets overview](https://learn.microsoft.com/en-us/azure/virtual-machines/availability-set-overview) använda två VM:ar för att nå kravet. Detta skulle göra lösningen både dyrare och mer komplicerad.

Slutligen är skalningen av en VM ganska bra, men den blir mer komplicerad när flera VM:ar behöver läggas till och hanteras. Därför tycker jag att en VM blir mer arbete och kostnad än vad Nordvik behöver för denna portal.

### Container

En container innebär att portalen körs som en applikation på Azures servrar, vilket betyder att du främst behöver ha koll på själva appen medan operativsystemskärnan och den underliggande infrastrukturen hanteras av Azure.

En container bygger på en Image som berättar för systemet hur appen ska köras. Allting som behövs för att köra applikationen finns därför inbyggt i imagen och kan enkelt flyttas eller startas på nytt. Detta gör det även enkelt att skapa nya instanser av applikationen utan att behöva ändra på själva huvudversionen.

Denna applikation kan även ändra hur mycket resurser den behöver beroende på hur många som använder portalen genom att skapa repliker. Detta ökar kapaciteten under stressiga tider, exempelvis om det kommer in över 300 felanmälningar under en timme. Den kan även konfigureras så att antalet repliker minskar när trafiken är låg, vilket gör att Nordvik inte behöver betala för lika mycket oanvänd kapacitet under nattetid.

Därför tycker jag att container passar bra för Nordvik eftersom trafiken kan variera väldigt mycket under dagen.

### Serverless

Serverless fungerar på sättet att man kör kod utan att själv behöva hantera någon server. Detta görs automatiskt genom molnet och den körmiljö som molnleverantören tillhandahåller.

Serverless fungerar så att varje gång koden körs används resurser och man betalar utifrån användningen. Detta är otroligt simpelt att använda eftersom man inte behöver tänka lika mycket på servrar, operativsystem eller underhåll.

För Nordvik hade serverless därför kunnat vara ett bra alternativ eftersom trafiken varierar mycket och är nära noll under natten. Då kan kostnaden minska när applikationen inte används. Nackdelen är däremot att serverless passar bättre för mindre separata funktioner än för en hel webbportal. Därför tycker jag att container passar bättre som huvudlösning för Nordviks portal, medan serverless-lösningar kan användas för vissa delar av systemet.
