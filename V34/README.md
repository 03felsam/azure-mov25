# V34 <br/>
## Azure V34<br/>
**Felix Samuelsson**


## Github: Commands </br> Ändra spara skicka
````
git status
````


````
git add .
````
 för alla filer kan annars manipuleras vilka filer som ska uppdateras

 ```` 
git commit -m"Exempel" 
 ````
 Commitar en lokal punt för alla filer du har lagt till i
```` 
git add 
 ````
-m är för messanget för din lokala commit

```` 
git push
````
skickar dina commits till din github online 

````
gitignore
````

## Skapa VM i Azure

Skapa resursgrupp

Skapa VM </br>
Storlek: **B2ats_v2** </br>
Namn konsekvent undvik åäö och mellanslag</br>
Samma Region som din resursgrupp</br>
SSH nyckel </br>


## Anslut till Ubuntu Server VM via SSH

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


## Ubuntu server tips

Starta med att uppdatera servern med 
````
sudo apt update
````

## Installera Nginx

````
sudo apt install nginx -y
````

browsa till public websida

Öppna port 80 /22
Vi andänder http inte https


## Redigera Nginx webbsida
mappen med Nginx ligge på /var/www/html

````
sudo nano index.html
````