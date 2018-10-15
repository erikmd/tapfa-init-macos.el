# Configuration de GNU Emacs pour Coq

Ces instructions supposent que les logiciels suivants sont déjà
installés sur votre système, par exemple avec le gestionnaire de
paquets de votre distribution GNU/Linux :

* [Coq](https://coq.inria.fr/download)
* [GNU Emacs](https://www.gnu.org/software/emacs/) (ou [Emacs Modified for Windows](https://vigou3.gitlab.io/emacs-modified-windows/))

## Installation des modes Emacs pour Coq

Pour installer automatiquement
[ProofGeneral](https://github.com/ProofGeneral/PG) et
et [company-coq](https://github.com/cpitclaudel/company-coq) :

1. Téléchargez et placez ce fichier [.emacs](./.emacs) à la racine de
   votre homedir (`~/`)

    Notez que vous pouvez effectuer cette étape en ligne de commande :

        cd && mv .emacs .emacs.bak  # sauvegarder votre fichier si nécessaire
        curl -fSOL https://github.com/erikmd/coq-init.el/raw/master/.emacs


2. Lancez GNU Emacs en exécutant la commande `emacs &` dans un
   terminal.

    L'installation des modes Emacs pour Coq devrait se lancer
    automatiquement et durer environ 2'30.

    En cas de souci, faites
    <kbd>M-x package-install-selected-packages RET</kbd>
    (<kbd>M-x</kbd> désignant <kbd>Alt+X</kbd>
    et <kbd>RET</kbd> la touche Entrée) et redémarrez emacs.
