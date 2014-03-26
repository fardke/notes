Astuce urxvt
============

Prérequis
---------

Installer **urxvt**

.. code-block:: sh

    sudo apt-get install rxvt-unicode

Configuration
-------------

La configuration se fait dans le fichier **.Xdefaults**.

Onglets renommables
-------------------

Il faut ajouter le script **tabbedex** dans le répertoire : **/usr/lib/urxvt/perl/**.

On peut télécharger le script https://raw.github.com/stepb/urxvt-tabbedex/master/tabbedex

Puis on ajoute :

.. code-block:: linux-config

    urxvt*perl-ext-common: tabbedex

au fichier **.Xdefaults**.

Ensuite pour utiliser ce terminal, il faut utiliser shift+fleche_vers_le_bas pour ajouter un onglet et shift+fleche_vers_le_haut pour le renommer.

