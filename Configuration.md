Introduction


Dans ce tutoriel, nous allons vous guider à travers les étapes nécessaires pour installer et configurer une solution anti-phishing en utilisant pfSense. Nous couvrirons l'installation de modules essentiels tels que Squid, SquidGuard et pfBlockerNG, ainsi que leur configuration pour garantir une protection efficace contre les tentatives de phishing.

Pré-requis
Assurez-vous que pfSense est correctement installé et configuré sur votre réseau. Vous devriez avoir accès à l'interface web de pfSense pour effectuer les étapes suivantes.

Étape 1 : Installation des modules
1.1. Accéder au gestionnaire de paquets
Connectez-vous à l'interface web de pfSense.
Allez dans le menu System.
Sélectionnez Package Manager.
Cliquez sur l'onglet Available Packages.
1.2. Installer les modules
Recherchez et installez les modules suivants : Squid, SquidGuard et pfBlockerNG.
Les modules installés apparaîtront dans l'onglet Installed Packages (Figure 2.4).

Étape 2 : Configuration de Squid
2.1. Accéder aux paramètres de Squid
Allez dans le menu Services.
Sélectionnez Squid Proxy Server.
2.2. Configurer Squid
Activez le proxy (Figure 2.5).
Spécifiez l'interface du proxy (Figure 2.5).
Autorisez les utilisateurs sur l'interface (Figure 2.7).
Activez le mode transparent et son interface (Figure 2.7).
Activez la journalisation (Figure 2.6).
Cliquez sur Save pour enregistrer les modifications.



2.3. Activer l'inspection SSL
Accédez au gestionnaire de certificats dans le menu System puis Cert Manager.
Créez une nouvelle autorité de certification (Figure 2.8).
Installez ce certificat sur les machines clientes du réseau.

Étape 3 : Configuration de SquidGuard
3.1. Accéder aux paramètres de SquidGuard
Allez dans le menu Services.
Sélectionnez SquidGuard Proxy Filter.
3.2. Configurer SquidGuard
Activez le service.
Activez les logs pour le suivi.
Chargez la blacklist (Figure 2.10).
Spécifiez les catégories à bloquer (Figure 2.9).
Spécifiez la page de redirection pour la sensibilisation (Figure 2.11).



Étape 4 : Configuration de pfBlockerNG
4.1. Activer le résolveur DNS
Cliquez sur le menu Services.
Sélectionnez DNS Resolver.
Configurez les paramètres généraux du résolveur DNS :
Port d'écoute DNS (port 53).
Interfaces réseau sur lesquelles le résolveur DNS doit écouter (LAN et Localhost).
Port de sortie (WAN).
4.2. Configurer pfBlockerNG
Accédez à la page de configuration de pfBlockerNG sous le menu Firewall puis pfBlockerNG.
Spécifiez les listes noires DNS au niveau de l'onglet DNSBL (Figure 2.12).
Configurez l'interface d'écoute DNSBL sur LAN.
Définissez les actions à effectuer lorsqu'un flux DNSBL fournit des adresses IP (généralement "Refuser").

Cliquez sur Save pour enregistrer chaque configuration.
Conclusion
En suivant ces étapes, vous avez réussi à mettre en place une solution anti-phishing basée sur pfSense, incluant les modules Squid, SquidGuard et pfBlockerNG. Cette configuration permet de bloquer efficacement l'accès à des ressources malveillantes, offrant une protection renforcée à votre réseau.
