Installation de Apache 2
========================

Installation
------------

Installer le paquet `Apache2` via le gestionnaire de paquet.

.. code-block:: sh

    sudo apt-get install apache2

Pour vérifier que le serveur fonctionne il suffit d'aller sur http://localhost

Ajout d'alias 
-------------

Un alias est un un sous répertoire de notre domaine.

Par exemple dans le cas où nous possédons un site http://monsite.fr deux alias public/ et private/ nous permettra d'accéder à deux sites différents:

* https://monsite.fr/public/
* https://mons ite.fr/private/

Pour mettre ces alias en place il faut éditer le fichier **/etc/apache2/sites-available/default**.
Ajouter à la suite de </Directory>

.. code-block:: linux-config

   # pour la  partie private
   Alias /public/ /chemin/vers/mon/site/public/
   <Directory /chemin/vers/mon/site/public/>
       Option Indexes FollowSymLinks MultiViews
       AllowOverride All
       Order allow,deny
       Allow from all
   </Directory>
   Alias /public /chemin/vers/mon/site/public
   <Directory /cheminvers/mon/site/public>
       Option Indexes FollowSymLinks MultiViews
       AllowOverride All
       Order allow,deny
       Allow from all
   </Directory>

   # pour la partie private
   Alias /private/ /chemin/vers/mon/site/private/
   <Directory /chemin/vers/mon/site/private/>
       Option Indexes FollowSymLinks MultiViews
       AllowOverride All
       Order allow,deny
       Allow from all
   </Directory>
   Alias /private /chemin/vers/mon/site/private
   <Directory /chemin/vers/mon/site/private>
       Option Indexes FollowSymLinks MultiViews
       AllowOverride All
       Order allow,deny
       Allow from all
   </Directory>

Redémarrer apache2:

.. code-block:: sh

    sudo /etc/init.d/apache2 force-reload

Configuration SSL
-----------------

Prérequis
~~~~~~~~~

Le mod scgi pour apache2 :

.. code-block:: sh

    apt-get install libapache2-mod-scgi

Configuration
~~~~~~~~~~~~~

Activer les modes nécessaires pour apache2

.. code-block:: sh

    a2enmod ssl && a2enmod scgi

Editez le fichier de configuration de votre site apache (si on continue dans le meme fichier que dans la partie précédente c'est le fichier **/etc/apache2/sites-available/default**

.. code-block:: linux-config

    <IfModule mod_ssl.c>
    <VirtualHost *:443>
         ServerAdmin kevin.fardel@gmail.com
         DocumentRoot /var/www
         <Directory />
             Options FollowSymLinks
             AllowOverride None
         </Directory>
         SSLEngine on
         SSLCertificateFile /etc/apache2/apache2.pem
    </VirtualHost>
    </IfModule>

Ensuite il faut générer le certificat : 

.. code-block:: sh

    openssl req -new -out /etc/apache2/apache2.pem

Redémarrer apache2:

.. code-block:: sh

    sudo /etc/init.d/apache2 force-reload

Sécurisation d'un  site avec Digest
-----------------------------------

.. code-block:: sh

    a2enmod auth_digest

Ajouter dans la partie virtualhost de votre site (si c'est le meme fichier qu'au dessus **/etc/apache2/sites-available/default** ):

.. code-block:: linux-config

    <Directory /var/www/monsite/>
        AuthType Digest
        AuthName "real name"
        AuthUserFile /etc/apache2/htpasswd
        Require valid-user
    </Directory>

Ensuite il faut créer l'utilisateur avec la commande:

.. code-block:: sh

    htdigest -c /etc/apache2/htpasswd "real name" mon_login

Il vous demandera de créer un mot de passe au passage.
