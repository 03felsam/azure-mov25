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

Verksamheten:
Nordvik förvaltar 48 fastigheter, cirka 3 200 uthyrningsenheter (lägenheter och lokaler) och cirka 5 500
hyresgäster. <br/>
- Portalens användare är hyresgästerna (felanmälan), cirka 40 förvaltare och cirka 6 på ekonomi.<br/>

Trafik till portalen:
- Vardagar cirka 1 800 inloggningar, med tydlig topp klockan 07 till 09 och 17 till 20, och nära noll trafik
00 till 06.<br/>
- Normalt 5 till 10 samtidiga användare, men upp mot 120 samtidiga vid månadsskiftet (hyresavier och
påminnelser) och vid större driftstörningar.<br/>

Felanmälningar:
- I snitt cirka 70 anmälningar per dygn, men mycket ojämnt fördelat: en vattenläcka eller ett strömavbrott
kan ge över 300 anmälningar på en timme.
- Varje anmälan ska sparas (bild plus uppgifter), ge en post i en lista och en notis till ansvarig
förvaltare. Akuta kategorier (värme, vatten, lås) ska dessutom ge ett mejl direkt.<br/>

Bilder och dokument:
- En felanmälan har oftast en bild på 2 till 5 MB, vilket blir i storleksordningen 5 till 10 GB nya bilder
per år.
- Kontrakt och besiktningsprotokoll är cirka 40 GB och läses sällan efter de tre första månaderna.
Tillgänglighet:
- Felanmälan är affärskritisk, särskilt akuta fel. Portalen ska vara uppe minst 99,5 procent på kontorstid
och tåla att en enskild instans faller bort.<br/>

Kostnad:
- Riktvärdet för portalmiljön är cirka 2 500 kronor per månad. Nordvik vill inte betala för kapacitet som
står oanvänd nattetid.<br/>

Tillväxt:
- Beståndet växer med 5 till 8 fastigheter per år, och Nordvik vill snabbt kunna resa en likadan test- eller
demomiljö.<br/>

Säkerhet och uppföljning:
- Portalen hanterar personuppgifter om hyresgäster, så lagringen får inte vara publikt åtkomlig och
åtkomsten ska styras per roll.
- Ekonomi vill kunna följa kostnad per fastighet och avdelning, så alla resurser ska vara taggade.