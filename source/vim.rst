Vim
===

Tips
----

+-----------------+------------------------------------------------------------------------+
| set path=**     | Cherche dans le répertoire courant.                                    |
+-----------------+------------------------------------------------------------------------+
| ts /ma fonction | Cherche la fonction dans tous les  fichiers sources.                   |
+-----------------+------------------------------------------------------------------------+
| set mouse=v     | Fais des sélections avec la souris pour coller dans une autre fenêtre. |
+-----------------+------------------------------------------------------------------------+

Plugins
-------

XML
~~~

Le plugin matchit permet d'utiliser % pour les balises. Pour
l'installer il suffit de télécharger
http://www.vim.org/scripts/script.php?script_id=39 et l'extraire dans **.vim/**.

Le plugin xml permet de fermer automatiquement les balses.
Pour l'installer il suffit de télécharger le fichier 
http://www.vim.org/scripts/script.php?script_id=1397 et de le mettre dans
**.vim/ftplugin** et dans **.vim/indent**. Si à la suite de ça on n'a plus la coloration
synthaxique il suffit de faire :set filetype=xml dans vim.


Asciidoc
~~~~~~~~

Le plugin asciidoc permet d'avoir la coloration syntaxique pour 
les fichiers asciidoc. Pour l'installer il faut télécharger le fichier
https://github.com/dagwieers/asciidoc-vim et le mettre 
dans le **.vim/syntax** et mettre dans **.vimrc**

.. code-block:: linux-config

    set syntax=asciidoc

Seqdiag and Blockdiag
~~~~~~~~~~~~~~~~~~~~~

Ces plugins permettent d'avoir la coloration syntaxique pour les fichiers sources pour les diagrammes
de séquence et les diagrammes de block.

Pour les installer il faut télécharger les fichiers
https://raw.github.com/adogear/vim-blockdiag-series/master/syntax/seqdiag.vim et
https://raw.github.com/adogear/vim-blockdiag-series/master/syntax/blockdiag.vim et les
mettre dans **.vim/syntax** et mettre dans **.vimrc**.

.. code-block:: linux-config

    au BufRead,BufNewFile *.seqdiag setfiletype seqdiag
    au BufRead,BufNewFile *.blockdiag setfiletype seqdiag

Il faudra ensuite mettre l'extension **.seqdiag** pour les fichiers sources des diagrammes de séquence 
et l'extension **.blockdiag** pour les diagramme de block.

.. _dirdiff:

DirDiff
~~~~~~~

Le plugin dirdiff permet de faire un diff entre 2 répertoires.
Télécharger http://www.vim.org/scripts/download_script.php?src_id=16171 et le
mettre dans le répertoire **.vim/plugin/**.

Modifier **.vimrc** :

.. code-block:: linux-config

    let g:DirDiffDynamicDiffText = 1

Pour une bonne utilisation avec mercurial.

Configuration
-------------

Pour une bonne indentation et coloration syntaxique
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: linux-config

    set encoding=utf-8
    let g:load_doxygen_syntax=1
    set modeline
    set autoindent
    set cindent
    set expandtab
    set ts=8
    set sts=4
    set sw=4
    set fo+=ro
    set cinoptions=N-s,g0

Meilleure gestion de la complétion des paths
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: linux-config

    set wildmode=longest,full
    set wildmenu

Fold
----

Pour avoir les replis dans notre code source il faut ajouter : 

.. code-block:: linux-config

    set foldmethod=syntax

dans notre fichier **.vimrc**.

On peut également utiliser les replis avec les balises xml en ajoutant :

.. code-block:: linux-config

    let g:xml_syntax_folding=1
    au FileType xml setlocal foldmethod=syntax

Recherche intelligente
~~~~~~~~~~~~~~~~~~~~~~

Ajouter à votre **.vimrc** :

.. code-block:: linux-config

    set hlsearch
    set incsearch
    set ignorecase
    set smartcase

Colorer certains templates
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: linux-config

    hi def link Todo TODO
    syn keyword Todo TODO FIXME XXX DEBUG

Utilisation de taglist 
~~~~~~~~~~~~~~~~~~~~~~

+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| <Enter> ou double-clic | Saut vers l'endroit où est défini le tag situé sous le curseur                                                                 |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| o                      | Saut vers l'endroit où est définit le tag situé sous le curseur dans une nouvelle fenêtre                                      |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| t                      | Saut vers un tag en ouvrant un nouvel onglet, si le fichier est déjà ouvert dans un onglet alors on se déplace dans cet onglet |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Ctrl-t                 | Saut vers un tag dans un nouvel onglet                                                                                         |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| u                      | Mise à jour des tags listés dans la fenêtre                                                                                    |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| d                      | Supprime le tag ou le fichier sous le curseur                                                                                  |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| x                      | Zoom + ou Zoom - sur la fenêtre des tags                                                                                       |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| \+                     | Ouvre un pli                                                                                                                   |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| \-                     | Ferme un pli                                                                                                                   |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| \*                     | Ouvre tous les plis                                                                                                            |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| \=                     | Ferme tous les plis                                                                                                            |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| q                      | Ferme la fenêtre des tags                                                                                                      |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| <F1>                   | Affiche l'aide                                                                                                                 |
+------------------------+--------------------------------------------------------------------------------------------------------------------------------+

Orthographe
~~~~~~~~~~~

Pour activer la correction orthographique en anglais:

.. code-block:: sh

    :set spelllang=en spell

Il doit y avoir un répertoire **$HOME/.vim/spell/** qui contient :

- http://ftp.vim.org/vim/runtime/spell/en.utf-8.spl
- http://ftp.vim.org/vim/runtime/spell/en.utf-8.sug

+----+------------------------------+
| ]s | Va au prochain mot erronné.  |
+----+------------------------------+
| [s | Va au mot erronné précédent. |
+----+------------------------------+
| z= | Ouvre les possibilité.       |
+----+------------------------------+

