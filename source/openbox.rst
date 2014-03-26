Configuration openbox
=====================

Installation
------------

.. code-block:: sh

   pacman -S openbox
   mkdir $HOME/.config/openbox
   cp /etc/xdg/openbox/* $HOME/.config/openbox/


Outils externes
---------------

Tint2
~~~~~

Barre de status. Installation :

.. code-block:: sh

    pacman -S tint2

Configuration:

.. code-block:: sh

    vi $HOME/.config/tint2/tint2rc

Intégration à Openbox: 
Dans le fichier $HOME/.config/openbox/autostart ajouter:

.. code-block:: linux-config

    (sleep2 & tint2)

Volumeicon
~~~~~~~~~~

Télécharger les souces sur le repo :

.. todo:: à venir

Aller dans les sources:

.. code-block:: sh

    autoreconf -vfi
    ./configure
    make 
    make install

Il faut **alsamixer** tiré par le paquet **alsautils**.
