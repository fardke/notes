Transparence dans divers composants
===================================

Prérequis
---------

Installer xcompmgr:

.. code-block:: sh

    pacman -S xcompmgr

Tint2
-----

Par défault transparence déjà mise en place.

Urxvt
-----

Dans le fichier **.Xdefault** rajouter les deux lignes suivantes:

.. code-block:: linux-config

    urxvt*depth:            32
    urxvt*background:       rgba:0000/0000/0200/c800

Vérifier  que les deux lignes suivantes ne sont pas déjà présente:

.. code-block:: linux-config

    urxvt*shading:          30
    urxvt*transparency:     true

