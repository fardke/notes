Mutt
====

Prérequis
---------

Installer mutt avec sidebar :

.. code-block:: sh

    yaourt -S mutt-sidebar

Installer lbdb pour intégrer ldap.

.. code-block:: sh

    yaourt -S lbdb

Imap gmail
----------

Ajouter les lignes suivantes à votre **$HOME/.mutt/comptes/accountrc**:

.. code-block:: sh

   set from=user@gmail.com
   set realname="Kevin Fardel"
   set reverse_name=yes
   set reverse_realname=no
   set imap_user = 'user@gmail.com'
   set spoolfile = imaps://imap.gmail.com:993/INBOX
   set smtp_url="smtp://user@smtp.gmail.com:587/"
   set folder = "imaps://imap.gmail.com:993"
   set record="+Sent"
   set postponed="+Drafts"

Carnet d'adresse gmail
----------------------

Installer **goobook**:

.. code-block:: sh

   sudo easy_install goobook

Configurer goobook avec le fichier **$HOME/.netrc**:

.. code-block:: linux-config

   machine google.com
        login user@gmail.com
        password ****

Récupérer les contacts existants:

.. code-block:: sh

   goobook reload

Enfin ajoutez dans le fichier **.muttrc**:

.. code-block:: linux-config

    set query_command="goobook query '%s'"
    bind editor <Tab> complete-query
    macro index,pager a "<pipe-message>goobook add<return>" "add the sender address to Google contacts"

