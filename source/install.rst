============
Installation
============

Pendant nos ateliers, nous allons utiliser un interpréteur de langage Python, en version 3.5+. Vous trouverez ci-dessous quelques conseils pour vérifier si vous avez déjà l'interpréteur avec la "bonne version" ou bien, dans le cas contraire, pour l'installer ainsi que quelques outils complémentaires.

Windows
=======

Vous pouvez télécharger une version Windows de l'interpéteur Python directement depuis `python.org`_.
Une fois que vous avez récupéré le fichier d'installation, portant l'extension ``.msi``, il vous suffit de l'exécuter et de suivre les instructions.
Retenez bien le chemin d'installation - c'est-à-dire le dossier dans lequel vous avez installé Python. Vous aurez besoin de cette information par la suite, au moment de l':ref:`installation des outils <tools>`.


Linux (Ubuntu, Fedora, etc.) ou Mac OS X
========================================

Pour vérifier la version de Python installée sur votre système, entrez la commande suivante dans votre terminal :

.. code-block:: sh

    $ python --version
    Python 2.7.12+
    $ python3 --version
    Python 3.5.2+

Si la commande ``python`` n'est pas disponible, ou si une version inférieure est détectée :

Ubuntu
------

Tapez la commande suivante::

    sudo apt install python3.5 python3.5-dev python3-venv

Fedora
------

Entrez la commande suivante::

    sudo yum install python3.5

Mac OS X
--------

Téléchargez et installez la version de Python correspondant à votre version d'OS X depuis `python.org`_ .

Autres
------

Utilisez le gestionnaire de paquets adapté à votre distribution. S'il n'existe pas de système adéquat, ou si vous n'y trouvez pas Python, vous pouvez l'installer en le compilant depuis les fichiers sources disponibles sur le site `python.org`_. Un compilateur sera alors requis, ainsi que la librairie ``readline``.

Officieusement, nous partons du principe que des utilisateurs de distributions moins populaires (mais tout aussi valables !) réussiront sans problème à accomplir cette tâche :)


.. _tools:

Outils complémentaires
======================

Console Windows
---------------

Nous allons effectuer la majeure partie de notre travail en saisissant des lignes de commande dans la console Windows.
Pour la démarrer, appuyez sur les touches ``Win+R``. Dans la fenêtre qui apparaît alors, tapez ``cmd`` puis cliquez sur ``OK``. Une nouvelle fenêtre fait alors son apparition, avec du texte blanc sur fond noir :

.. code-block:: bat

    Microsoft Windows [Version 6.1.7601]
    Copyright (c) 2009 Microsoft Corporation. All rights reserved.


    C:\Users\Name>

Le texte peut être légèrement différent selon la version de Windows que vous utilisez.

``C:\Users\Name>`` est une invite de commande, que l'on désigne aussi parfois par le terme anglophone "prompt". Cette invite nous informe du répertoire dans lequel nous nous trouvons actuellement et attend la saisie d'une commande.

.. note::

    Petite précision de vocabulaire : dans le cadre de notre atelier, nous emploierons souvent le terme "répertoire". C'est un synonyme de ce que les versions récentes de Windows appellent "dossier", mais il est davantage utilisé dans le contexte du développement informatique.

Plus loin dans cette documentation, nous abrègerons souvent ``C:\Users\Name>`` en ``~$``, qui est une forme canonique d'invite de commande dans les environnements Linux et Mac OS X.

À l'aide de ligne de commande, vous pouvez vous déplacer dans le contenu de votre disque dur, comme vous le feriez via l'icône ``Mon ordinateur``. Il suffit pour cela de saisir des commandes et d'appuyer sur ``Entrée``.
Les commandes suivantes seront utilisées au cours de l'atelier :

``dir``
    Affiche le contenu du répertoire courant. Par exemple, si l'invite de commande indique ``C:\Users\Name``, la commande ``dir`` affiche le contenu de votre répertoire personnel.

``cd directory``
    Change le répertoire courant. Par exemple, si vous êtes dans le répertoire ``C:\Users\Name``, le fait de saisir la commande ``cd Documents`` vous permettra d'accéder au répertoire contenant vos documents. Pour vous en convaincre, tapez alors la commande ``dir``, vous verrez alors des fichiers familiers.
    La commande ``cd..`` vous permet de remonter au répertoire supérieur dans l'arborescence.

``mkdir directory``
    Crée un nouveau répertoire.


Environnement virtuel
---------------------

Vous devez maintenant choisir le répertoire dans lequel installer votre environnement virtuel. Celui-ci va vous permettre d'isoler votre travail des autres parties du système. Par exemple, vous pouvez choisir votre répertoire personnel.

Sous Windows 7, le chemin du répertoire personnel de l'utilisatrice ``Yara`` est le suivant :
``C:\Users\Yara\``. Vous êtes libre de choisir un répertoire différent, mais il est important de garder celui-ci en mémoire. En outre, il doit être facilement accessible car nous allons l'utiliser très souvent. 

Par exemple, si votre répertoire personnel est ``C:\Users\Yara``, la ligne de commande à saisir sera la suivante :

.. code-block:: bat

    :: Windows
    C:\Users\Yara> C:\Python35\python -m venv workshops

.. code-block:: sh

    # Linux or Mac
    ~$ python3.5 -m venv workshops

Après ces manipulations, un nouveau répertoire nommé ``workshops`` est présent dans votre répertoire personnel, contenant ce que l'on appelle un "environnement virtuel". Il convient maintenant d'activer celui-ci.

.. code-block:: bat

    :: Windows
    C:\Users\Yara> workshops\Scripts\activate

.. code-block:: sh

    # Linux or Mac
    ~$ source workshops/bin/activate

La commande ``python``, dès lors, permet de lancer la version adéquate de l'interpréteur Python, il n'est donc pas nécessaire de saisir le chemin complet vers celui-ci.

Assurez-vous maintenant que votre terminal est bien configuré :

.. code-block:: bat

    :: Windows
    (workshops) C:\Users\Yara>where python
    C:\Users\Yara\workshops\Scripts\python.exe
    ...

    (workshops) C:\Users\Yara>where pip
    C:\Users\Yara\workshops\Scripts\pip.exe
    ...

    (workshops) C:\Users\Yara>python --version
    3.5.3

.. code-block:: sh

    # Linux or Mac
    (workshops) ~$ which python
    /home/yara/workshops/bin/python
    (workshops) ~$ which pip
    /home/yara/workshops/bin/pip
    ...

    (workshops) ~$ python --version
    3.5.2+


.. _python.org: https://www.python.org/downloads/release/python-353/

.. note::
    Il est possible que la commande ``pip`` soit déjà disponible sur votre système. Dans ce cas, il convient de vérifier que la version de ``pip`` est la bonne, avec la commande ``pip --version``. Elle peut être exécutée des façons suivantes :

    .. code-block:: sh

        pip --version
        pip3 --version
        pip3.5 --version

    Ceci vous indique votre version de ``pip`` ainsi que le chemin vers le répertoire contenant votre environnement virtuel.

    Si vous ne trouvez pas ``pip`` ou si la commande ``which pip`` (ou bien ``where pip`` sous Windows) vous signale un problème, vous devez peut-être réinstaller ``pip`` :

    .. code-block:: sh

        python -m pip uninstall pip
        python -m ensurepip

	Si vous trouvez la commande ``pip`` dans une version inférieure à ``9.x``, vous pouvez la mettre à jour à l'aide de la commande :

	.. code-block:: sh

		pip install -U pip

En résumé
---------

Pour **installer un nouvel environnement virtuel** :

.. code-block:: bat

    :: Windows
    C:\Users\Yara> C:\Python35\python -m venv workshops

.. code-block:: sh

    # Linux or Mac
    python3.5 -m venv workshops

Pour **activer un environnement virtuel** :

.. code-block:: bat

    :: Windows
    C:\Users\Yara> workshops\Scripts\activate

.. code-block:: sh

    # Linux or Mac
    source workshops/bin/activate

Pour **vérifier la version de Python** :

.. code-block:: sh

    (workshops) ~$ python --version
    3.5.2+


IPython
-------

Si vous le souhaitez, vous pouvez installer le logiciel ``IPython``, qui améliore l'aspect et le confort d'utilisation de l'interpréteur Python. Pour cela, saisissez la commande suivante une fois votre environnement virtuel activé :

.. code-block:: sh

    (workshops) ~$ pip install ipython
