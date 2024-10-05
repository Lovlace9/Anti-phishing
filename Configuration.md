## Introduction


Dans ce tutoriel, nous allons vous guider à travers les étapes nécessaires pour installer et configurer une solution anti-phishing en utilisant pfSense. Nous couvrirons l'installation de modules essentiels tels que Squid, SquidGuard et pfBlockerNG, ainsi que leur configuration pour garantir une protection efficace contre les tentatives de phishing.

## Pré-requis
Assurez-vous que pfSense est correctement installé et configuré sur votre réseau. Vous devriez avoir accès à l'interface web de pfSense pour effectuer les étapes suivantes.

![image](https://github.com/user-attachments/assets/7f233cfe-10f7-40f1-84d6-ec01223c31d6)

## Étape 1 : Installation des modules

### 1.1. Accéder au gestionnaire de paquets
Connectez-vous à l'interface web de pfSense.
Allez dans le menu System.
Sélectionnez Package Manager.
Cliquez sur l'onglet Available Packages.

### 1.2. Installer les modules
Recherchez et installez les modules suivants : Squid, SquidGuard et pfBlockerNG.
Les modules installés apparaîtront dans l'onglet Installed Packages

![image](https://github.com/user-attachments/assets/d72c0e76-2309-4dfa-bd6d-2fe1d1ad1323)


## Étape 2 : Configuration de Squid

### 2.1. Accéder aux paramètres de Squid
Allez dans le menu Services.
Sélectionnez Squid Proxy Server.

### 2.2. Configurer Squid
Activez le proxy.
Spécifiez l'interface du proxy.

![image](https://github.com/user-attachments/assets/25b7fcef-08fe-4361-b05f-be31ed7c25f2)

Autorisez les utilisateurs sur l'interface .
Activez le mode transparent et son interface .

![image](https://github.com/user-attachments/assets/8555c8d6-4557-49d7-ad1a-56ca640b10fc)

Activez la journalisation.
Cliquez sur Save pour enregistrer les modifications.

![image](https://github.com/user-attachments/assets/5fa85561-75dd-43f0-9cfd-a4474973242f)




### 2.3. Activer l'inspection SSL
Accédez au gestionnaire de certificats dans le menu System puis Cert Manager.
Créez une nouvelle autorité de certification.
Installez ce certificat sur les machines clientes du réseau.

![image](https://github.com/user-attachments/assets/1a4d8f8b-eec4-4a54-8175-cb226deb6539)



## Étape 3 : Configuration de SquidGuard

### 3.1. Accéder aux paramètres de SquidGuard
Allez dans le menu Services.
Sélectionnez SquidGuard Proxy Filter.

### 3.2. Configurer SquidGuard
Activez le service.
Activez les logs pour le suivi.
Chargez la blacklist.

![image](https://github.com/user-attachments/assets/22b93e18-a36e-47af-ba2f-5a4bbec35c0f)


Spécifiez les catégories à bloquer.

![image](https://github.com/user-attachments/assets/0a1e9749-2cc3-4d9e-8c6e-970ad1917e57)

Spécifiez la page de redirection pour la sensibilisation.

![image](https://github.com/user-attachments/assets/3f879bb8-fa36-4fb4-a355-7ac7f5a53043)



## Étape 4 : Configuration de pfBlockerNG
### 4.1. Activer le résolveur DNS
Cliquez sur le menu Services.
Sélectionnez DNS Resolver.
Configurez les paramètres généraux du résolveur DNS :
Port d'écoute DNS (port 53).
Interfaces réseau sur lesquelles le résolveur DNS doit écouter (LAN et Localhost).
Port de sortie (WAN).

### 4.2. Configurer pfBlockerNG
Accédez à la page de configuration de pfBlockerNG sous le menu Firewall puis pfBlockerNG.
Spécifiez les listes noires DNS au niveau de l'onglet DNSBL.

![image](https://github.com/user-attachments/assets/e8eca5a9-6f54-451f-8f07-4e283a7934d1)

Configurez l'interface d'écoute DNSBL sur LAN.
Définissez les actions à effectuer lorsqu'un flux DNSBL fournit des adresses IP (généralement "Refuser").

Cliquez sur Save pour enregistrer chaque configuration.


La page de sensibilisation en question : 

![image](https://github.com/user-attachments/assets/4a1e478b-2bec-47d8-8aaf-8495458dbc0a)


## Conclusion
En suivant ces étapes, vous avez réussi à mettre en place une solution anti-phishing basée sur pfSense, incluant les modules Squid, SquidGuard et pfBlockerNG. Cette configuration permet de bloquer efficacement l'accès à des ressources malveillantes, offrant une protection renforcée à votre réseau.
