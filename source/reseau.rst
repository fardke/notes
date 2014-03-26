Outils réseau intéressants
==========================

Prérequis
---------

Installer nmap, net-tools

.. code-block:: sh

    pacman -S net-tools nmap

NMap
----

Pour trouver tous les ports TCP ouvert sur une ip du reseau :

.. code-block:: sh

    nmap -Ss 192.168.x.x

Pour trouver toutes les adresses ip ouverte sur un meme intervalle d'adresse ip :

.. code-block:: sh

    nmap 192.168.1.0-255

Cette commande trouvera toutes les adresse ip des machines connecté sur le sous réseau 192.168.1.0/24

netstat
-------

Voir toutes connections active sur le serveur

.. code-block:: sh

    netstat -lapute

