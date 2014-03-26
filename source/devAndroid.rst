Développement Android sous vim
==============================

Prérequis
---------

Installer java:

.. code-block:: sh

    pacman -S jre7-openjdk

Récupérer le plugin
vjde_ pour faire du
java sur vim. Pour l'installer desarchivez le dans votre répertoire .vim
:

.. code-block:: sh

    cd $HOME/.vim
    tar -xvf /rep/ou/on/a/dl/vjde.tgz

Récupérer le sdk d'android sur le site officiel d'Android. Pour
l'installer il suffit de désarchiver le tgz téléchargé, et de lancer
SDK/tools/android. Ensuite choisir ce qu'on souhaite installer. 

.. warning:: Avec l'encodage UTF-8 il y a un warning à l'ouverture de vim. A regarder.

.. note::

    Pour ne pas vous embêter par la suite faire des liens des outils
    répertoire SDK/tools/ dans votre répertoire bin.


Développer sur un terminal physique
-----------------------------------

Pour travailler sur une vrai plateforme il faudra installer **apache-ant**

.. code-block:: sh

    sudo pacman -S apache-ant

Une fois que c'est fait il faut créer une règle udev :

.. code-block:: sh

    sudo vi /etc/udev/rules.d/51-android.rules

Dans lequel on met la ligne suivante :

.. code-block:: guess

    SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666"

où **0bb4** est l'id vedeur de la marque **HTC**. Il faut adapter cet id au
vendeur de votre terminal. Vous trouverez ces id sur la page de
documentation `Android devices`_.

Une fois que c'est terminé pour vérifier si ça a foncitonné lancez la
commande :

.. code-block:: sh

    adb devices

Cette commande  va lancer le démon +adb+ fournis par le sdk android.

.. note:: Pour que cette commande fonctionne il faut avoir fait un lien symbolique
        entre SDK/platform-tools/adb vers votre répertoire bin/. Si vous ne
        trouvez pas l'exécutable **adb** c'est probablement que vous n'avez pas
        installer de target android.

.. note:: Si quand vous exécutez cette commande vous vous retrouvez avec **?????? no
        permission** c'est soit que vous êtes trompé dans le fichier udev ou
        alors essayer de lancer adb devices en root. Avant de le relancer penser
        à tuer le premier démon. 

Créer un projet android
-----------------------

Pour créer un nouveau projet android il faut exécuter la commande
suivante :

.. code-block:: sh

    android create project --target <target_id> --name \
    <project_name> --path <path_to_your_project> --activity \
    <activity_name> --package<package_name>

.. warning:: Si vous n'avez pas fait de liens entre le répertoire **tools/** du sdk et
            votre répertoire **bin/** il faudra renseigner le chemin entier vers
            l'exécutable android.

Builder et lancer l'exécutable
------------------------------

Normalement une fois votre projet créé vous pouvez le builder et
l'installer sur votre target. Pour ce faire placer vous à la racine de
votre projet et lancez la commande suivante :

.. code-block:: sh

    ant debug

Si tout se passe bien cela devrait vous générer des .apk dan le
répertoire bin/ de votre projet. 
Ensuite pour lancer l'exécutable sur votre terminal:

.. code-bloc k:: sh

    adb -d install bin/votre_apk.apk

.. _vjde: http://www.vim.org/scripts/script.php?script_id=1213
.. _`Android devices`: http://developer.android.com/tools/device.html
