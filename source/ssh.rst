Utilisation ssh
===============

Créer sa clé ssh
----------------

.. code-block:: sh

    ssh-keygen 

Ajouter sa clé ssh au serveur
-----------------------------

Il suffit de copier le contenue du fichier **$HOME/.ssh/id_rsa.pub** (si vous avez bien généré une clé rsa) et de mettre 
le contenue dans le fichier **$HOME/.ssh/authorized_keys** du serveur.

Normalement à la suite de ça vous pouvez connecter votre utilisateur en ssh à votre serveur.

Alias de connexion ssh
----------------------

Editez le fichier **$HOME/.ssh/config**

.. code-block:: linux-config

    Host maison
    HostName kevin-fardel.hd.free.fr
    User kevin

