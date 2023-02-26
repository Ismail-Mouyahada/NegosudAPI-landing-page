
# Déploiement page d'acceuil de Negosud Vue.js 2


## 1. Générer les fichiers de production

Le premier pas consiste à générer les fichiers de production de votre application Vue.js 2. Pour ce faire, exécutez la commande suivante dans votre terminal :

```
npm run build

```

Cette commande va générer les fichiers de production de votre application dans un dossier `dist`.

## 2. Configuration du serveur

Pour déployer votre application, vous devez configurer un serveur web. Il existe de nombreuses options pour les serveurs, mais nous allons utiliser [Apache](https://httpd.apache.org/) pour cet exemple.

Assurez-vous que Apache est installé sur votre serveur. Si ce n'est pas le cas, installez-le en exécutant la commande suivante :

```
sudo apt-get install apache2

```

Ensuite, vous devez activer le module `mod_rewrite` en exécutant la commande suivante :

```
sudo a2enmod rewrite

```

Redémarrez ensuite Apache pour que les modifications prennent effet :

```
sudo service apache2 restart

```

## 3. Configuration du virtual host

Maintenant que le serveur est configuré, vous devez configurer le virtual host pour votre application Vue.js 2. Pour ce faire, vous devez créer un fichier de configuration pour votre virtual host. Créez un fichier `monapp.conf` dans le répertoire `/etc/apache2/sites-available/` en utilisant la commande suivante :

```
sudo nano /etc/apache2/sites-available/monapp.conf

```

Ajoutez les lignes suivantes au fichier de configuration :

```
<VirtualHost *:80>
   ServerName negosud-api.com
   DocumentRoot /var/www/negosud.fr/dist
   <Directory /var/www/negosud.fr/dist>
      Options Indexes FollowSymLinks MultiViews
      AllowOverride All
      Order allow,deny
      allow from all
      Require all granted
   </Directory>
   ErrorLog /var/log/apache2/negosud_error.log
   LogLevel warn
   CustomLog /var/log/apache2/negosud_access.log combined
</VirtualHost>

```

Assurez-vous de remplacer `monapp.com` par le nom de votre domaine et `/var/www/negosud.fr/dist` par le chemin absolu vers le dossier `dist` que vous avez généré à l'étape 1.

Enregistrez et fermez le fichier.

## 4. Activer le virtual host

Maintenant que le fichier de configuration pour votre virtual host est créé, vous devez l'activer en exécutant la commande suivante :

```
sudo a2ensite negosud.conf

```

Redémarrez ensuite Apache pour que les modifications prennent effet :

```
sudo service apache2 restart

```

## 5. Accéder à votre application

Votre application est maintenant déployée et accessible à l'adresse de votre choix pour un demo voyez :`http://195.154.113.18`. Testez votre application en accédant à cette adresse dans votre navigateur web.

Félicitations, vous avez maintenant déployé votre page d'accueil Negosud en Vue.js 2 !
  
  
![pageaccuk](https://user-images.githubusercontent.com/66369128/221434044-066f37c9-4f9f-4569-abb3-53f7b9617f71.png)
