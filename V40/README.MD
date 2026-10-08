# V41 – Examination,  Konfigurering av Nordvik

**Av Felix Samuelsson**

**Kurs: Microsoft Azure**

GitHub Repo: [https://github.com/03felsam/azure-mov25](https://github.com/03felsam/azure-mov25)
## Mål
- Kör appen på minst en alternativ nivå
- Förklara vm, containers, serverless och skillnaderna 
- Vilar på förklaring det är den som bedöms.

Bindings kopplar data  in och ut <br/>
Cold start<br/>
Kostnad skalning och drift skillnader <br/>
Motivera valet efter novatrix's behov <br/>

## Dockerfile

FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

## Saker jag tog från lektion
Resursgruppen måste finnas. Skapa den först (alla kommandon pekar på den) 
az group create --name rg-novatrix --location swedencentral


Registrera resursleverantörerna (en gång per prenumeration)
az provider register --namespace Microsoft.ContainerInstance
az provider register --namespace Microsoft.Web
az provider register --namespace Microsoft.Storage
az provider register --namespace microsoft.insights

Slå på admin-konto (om ni inte vill använda hanterad identitet)
az acr update --name novatrixacr --admin-enabled true



Hämta lösenord för admin-kontot
az acr credential show --name novatrixacr

Skapa containern (byt ut den fetstilta texten mot era egna värden)
````
az container create --resource-group rg-novatrix --name novatrix-app --image novatrixacr.azurecr.io/novatrix-app:v1 --os-type Linux --cpu 1 --memory 1 --ports 80 --dns-name-label novatrix-app --registry-username novatrixacr --registry-password "Lägg in ett av lösenorden här"
````
 ## Enligt video checka loggar och etc


az acr repository list --name novatrixacr --output table

az acr credential show --name novatrixacr

**kan byta fqnd till ip** <br/>
az container show --resource-group rg-novatrix --name novatrix-app --query ipAdress.fqdn -o tsv


**för loggar** <br/>
az container longs --resource-group rg-novatrix --name novatrix-app


## skapa function app

**storage accoutn skapning** <br/>
az storage account create --resource-group rg-novatrix --name novatrixstorage --location swedencentral -sku Standard LRS

az functionapp create --resource-group rg-novatrix --name novatrix-fn --storage account stnovatrix --consumption-plan-location swedencentral --runtime node --functions-version 4 --os-type Windows

az functionapp show --resource-group rg-novatrix --name novatrix-fn -o table

Skapa upp funktioner i portalen för novatrix-fn appen **Overview -> Functions -> Create in azure portal**

Skapa en HTTP trigger som template med ett relevant namn som arende-HTTP-trigger

Där kan du lägga in javascript kod lärarens exempel 
````
module.exports = async function (context,req) (
    context.log("Novatrix arendemottagning kordes.");
    context.res = {status: 200, body: "Arende mottaget, tack"};
);
````

Du kan göra detta genom kod genom att trycka ut detta som pyton kod till din webbapp 

## Verifiering
 i http trigger vi satte upp finns det ett get function URL (Default(Function key)) där du kan kopiera en länk och pastea den i webbläsaren för att se vilket svar man får vid inlämning av ett ärende 

 Därefter kan du gå in på loggs och refresha function keyn URL och se på loggs om det fungerar.

 kan köras från terminal genom att göra:
 ````
 curl PASTE-URL-HERE 
 ```` 
 Verifiera att du får rätt svar och det fungerar!

