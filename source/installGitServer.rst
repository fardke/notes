Installation d'un serveur git privé
===================================

Installer serveur git
---------------------

.. code-block:: sh

    adduser git

Installer git-core

.. code-block:: sh

    sudo pacman -S git-core

Configuration SSH
-----------------

Créer le fichier **autorized_keys** :

.. code-block:: sh

    sudo mkdir /home/git/.ssh
    sudo touch /home/git/.ssh/authorized_keys

Une fois que nous aurons généré la clé rsa publique de notre dev sur sa machine de dev
il faudra l'ajouter à la liste des **authorized_key** avec la commande :

.. code-block:: sh

    echo "ma cle" >> /home/git/.ssh/authorized_keys

Vérifier les droits de nos fichiers de configuration ssh :

.. code-block:: sh

    chmod 755 ~/.ssh
    chmod 644 ~/.ssh/authorized_keys

Créer un repo vide
------------------

Créer le répo :

.. code-block:: sh

    sudo mkdir /home/git/myrepo.git

Initialiser le repo :

.. code-block:: sh

    sudo cd /home/git/myrepo.git
    sudo git --bare init

Configurer sur ses machines de devs
-----------------------------------

Voir documentation ssh pour créer sa clef ssh.

Initialiser le repo git:

.. code-block:: sh

    git clone git@kevin-fardel.hd.free.fr:myrepo.git
    git commit -m "mon message"
    git push origin master

