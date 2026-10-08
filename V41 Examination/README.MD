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
Att portalen finns på en uppskapad VM innebär att du har en hel dator som du behöver underhålla. Detta innebär mycket driftansvar samt hög flexibilitet när det gäller konfiguration. Dock innebär det även att företagen behöver ha kvalificerade arbetare som vet hur man tar hand om en VM och ser till att den kan underhållas under ett flertal år. Dessutom är VM kostnaden en konstant kostnad så länge den är uppskapad vilket innebär att det är en kostnad som kommer att finnas under nattetid. Detta var specifikt nämnt i budgeten att **Nordvik vill inte betala för kapacitet som
står oanvänd nattetid.** vilket är en av anledningarna som jag tror att detta är fel val när det gäller att ha en VM som en host för portalen. En annan anlednign till att en VM inte skulle passa är för att upfylla kravet att ha 99.95% upptime under kontorstid behöver vi enligt [**Microsoft learns Availability sets overview**](https://learn.microsoft.com/en-us/azure/virtual-machines/availability-set-overview) Två VM för att nå kraven. Slutligen är skalningen avn en VM ganska bra men blir ganska komplicerat efter flertal had laggt tills.

### Container

### Serverless

