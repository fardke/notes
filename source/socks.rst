Navigation web anonyme avec socks
=================================

Principe
--------

On ouvre un tunnel sécurisé entre un pc et mon serveur maison à travers ssh.
On dit à notre navigateur de faire passer toutes nos connexions à travers ce tunnel.

Du coup on peut naviguer de manière sur notre pc sans que l'on sache ce que l'on fait.
Toutes la navigation se passe sur le réseau de la maison.

Lancement tunnel
----------------

Sur le pc où vous souhaitez naviguez de manière anonyme:

.. code-block:: sh

    ssh -D 8080 -p 2201 -C -N prout@maison

Sur votre serveur maison il suffit d'avoir un démon ssh de lancé et d'avoir le port 22 d'ouvert
et de redirigé vers votre serveur ssh.

L'option -p permet de changer le port ssh, -C compresse les données, -N précise qu'on n'aura pas
la main pour lancer des commande ssh.

Configuration navigateur
------------------------

Firefox
~~~~~~~

Se rendre à l'adresse **about:config** et chercher socks. Modifier les configurations comme suit:


