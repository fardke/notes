Configuration pour connexion internet via smartphone
====================================================

Prérequis
---------

Avoir le module usbnet.
Avoir un smartphone sous Android

Configuration samrtphone
------------------------

Paramètre -> Sans fils et Réseaux -> Partage connexion/point d'accès

Cocher **Via USB**

Configurer ordinateur
---------------------

Vérifier que le module usbnet ne soit pas déjà chargé:

.. code-block:: sh

    lsmod | grep usbnet

S'il ne l'est pas :

.. code-block:: sh

    modprobe usbnet

Vérifier que l'interface usb0 existe :

.. code-block:: sh

    ifconfig -a

Activer l'interface réseau et obtenir une adresse ip automatiquement :

.. code-block:: sh

    ifconfig usb0 up
    dhcpcd usb0
