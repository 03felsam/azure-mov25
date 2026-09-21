# V38 – IAC med ARM templates

**Av Felix Samuelsson**

**Kurs: Microsoft Azure**

GitHub Repo: [https://github.com/03felsam/azure-mov25](https://github.com/03felsam/azure-mov25)


## git

klona github in i bash azure 

gh auth login

gör guide

clone repo 
browsa till v38/ där du har json filerna för deployment


## Exempel på skapning.
skapa storage account genom cloudshell json azuredeploy-enkel.json med unik parameter stnovatrix1706 i detta fallet <br/>

````
az deployment group create -g rg-novatrix-v34 --template-file azuredeploy-enkel.json --parameters storageName=stnovatrix1706
````
Verifiera sedan om det fungerade genom **"provisioningState": "Succeeded",**
och sedan manuell verifiering att allting skapades på rätt sätt i portalen

eller genom följande kod som listar all deployment i resursgruppne du specifierar
```` 
az deployment group list --resource-group rg-novatrix-v34 -o table
````

### Steg att göra innnan deploymnet

Verifiering genom kod 

Du kan göra en **what if** vilket kör en teoretisk verision av vad som skulle hända.
````
az deployment group validate
````
````
az deployment group what if
````
## Kod 