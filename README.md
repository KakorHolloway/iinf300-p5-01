# IINF300
## Connection au cluster Openshift
Pour vous connecter au cluster Openshift mis à disposition : 

Téléchargez sur votre machine le paquet OKD suivant : 
https://github.com/okd-project/okd/releases/download/4.15.0-0.okd-2024-03-10-010116/openshift-client-windows-4.15.0-0.okd-2024-03-10-010116.zip

Copiez le fichier oc.exe dans C:\Windows\System32

Allez sur l'url https://console-openshift-console.apps.openshift.kakor.ovh authentifiez-vous avec l'utilisateur ipi-gp-x (le x étant le numéro de groupe) en choisisant "KeystoneIDP".

Une fois authentifié (attention à ne pas recharger la page même si l'affichage prends du temps), allez en haut à droite de la page et sélectionnez l'option "Copy login Command" et réauthentifiez vous. 

Cliquez sur le lien Display Token et copiez dans votre terminal sur VScode la ligne de commande qui à été donné avec oc. 

Pour vérifier que vous êtes authentifiés, lancez la commande ```oc get pod```

# Partie I de IINF300 : Mise en place des NetPol

## Première partie du cours : 

Déployez l'environnement dans le projet de votre groupe tentez de vous connecter sur la bdd du groupe suivant en configurant mediawiki. 

N'oubliez pas de modifier le nom de la route.
(ex: gp 1 utilise gp 2....)

## Deuxième partie mise en place des règles d'ingress

Relancez la commande ``` oc replace --force -f exo1/``` pour reset l'environnement.

Dans votre propre namespace testez que la policy fonctionne bien et vous empêche de vous connecter sur le mysql de votre propre namespace. 

Une fois vérifié, créez la network policy pour autoriser votre pod mediawiki à accéder sur le port 3306 à votre base de donnée. 

Pour la syntaxe du fichier reprenez l'exemple de la documentation officielle (vous pouvez ignorer la partie CCIDR dans les deux cas) : https://kubernetes.io/docs/concepts/services-networking/network-policies/#networkpolicy-resource