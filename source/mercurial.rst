Astuces Mercurial
=================

Pusher une nouvelle branche
---------------------------

Si on créé une nouvelle branche sur notre dépôt local on a une erreur.

Pour ne plus l'avoir:

.. code-block:: python

    hg push --new-branch

Coloration des diff
-------------------

Pour avoir un diff coloré ajouter ces lignes à **$HOME/.hgrc** :

.. code-block:: linux-config

    [extensions]
    color =

    [color]
    status.modified = magenta bold
    status.added = green bold
    status.removed = red bold
    status.deleted = cyan bold
    status.unknown = blue bold
    status.ignored = black bold

Utiliser dirdiff pour faire un diff
-----------------------------------

Pour pouvoir utiliser le plugin dirdiff pour faire un diff il faut installer le plugin 
(:ref:`installation plugin DirDiff<dirdiff>`), ensuite ajouter ces lignes à **$HOME/.hgrc** :

.. code-block:: linux-config

    [extensions]
    extdiff =

    [extdiff]
    cmd.vimdiff = vim
    opts.vimdiff = -f '+next' '+execute "DirDiff" fnameescape(argv(0)) fnameescape(argv(1))'

Ensuite il suffit de remplacer **hg diff** par **hg vimdiff**.

Ajout graphlog
--------------

On peut utiliser aussi **hg glog** au lieu de **hg log**. Ajouter ces lignes à **$HOME/.hgrc**:

.. code-block:: linux-config

    [extensions]
    graphlog =
