Utilisation de asciidoc
=======================

Prérequis
---------

Installer **asciidoc** http://sourceforge.net/projects/asciidoc/files/

.. code-block:: sh

    tar -xzf asciidoc-8.6.7.tar.gz
    cd asciidoc-8.6.7.tar.gz
    ./configure
    make
    sudo make install

Vérifier qu'il y a bien la commande +asciidoc+ et que vous avez **python**
dans /usr/bin

.. note:: Normalement sous **archlinux** il manque certaine dépendance pour avoir un style par défaut ou pour avoir les caractères accentués bien reconnus.

Utilisation
-----------

Ecrire son fichier **mon_fichier.asciidoc**. Pour le compiler :

.. code-block:: sh

    asciidoc -n -a toc -a toclevels=4 -a max-width=55em -a data-uri -a icons

Mémo synthaxe
-------------

liste :

.. code-block:: minid

    - item1
    - item2
    * item1
    * item2
    ** item1
    ** item2
