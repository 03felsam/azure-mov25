## V35- Konfiguratoin av access <br/>
**Av Felix Samuelsson** </br>
**Kurs: Microsoft Azure** </br>
Github Repo: https://github.com/03felsam/azure-mov25

## Mål 

- Skapa Användare och roller
- Tilldela Roller
- Förbered en identititet för appen
- Verifiera 


## Skapa användare
Antingen sök på Entra ID -> Directory översikt -> Användare -> skapa ny användare

eller bara söka på användare

Skapa användaren är ganska självklart samma vibes som i Active directory 

Skapa grupper är liknande också och kan gå från office directory där du kan välja mellan Microsoft 365 eller security grupper. Security kommer att avnädas i detta fallet då det innebär hantering av acceses och resurser medans 365 är mer använt för sammarbete inom 365. 

## Tilldela roller
 Roller är en samling av behörigheter och är åtgärder som exempel att starta en VM. 
 
 De tre vanligaste är de följande rollerna men det finns självklart otroligt många men är oftast baserade på dessa och ändrar specifika val på den.

**Reader** : 
Får se allting ändra ingentin. Bra för insyn inom systemen.

 **Contrubutor** :
 Får skapa ändra och radera resurser. Dock får inte dela ut behörigheter.

 **Owner** :
Full kontroll inklusive att styra åtkomst. Ska nästan alldrig delas ut.

### Scopes
Scopes handlar om vad dina behörighet gäller på. Den rollen som assignas verkar bara på den scope som den är inställd på och inte utanför. De valen som finns för scopes är följande:<br/>
**Hel prenumeration** <br/>
**En resursgrupp** <br/>
**En resurs**  <br/>