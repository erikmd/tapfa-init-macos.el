# Environnement de TP pour OCaml et Coq (avec Emacs)

Cette configuration nécessite d'installer Emacs et
[opam](https://ocaml.org/) (*the OCaml package manager*).

La procédure ci-dessous concerne uniquement macOS.

Pour GNU/Linux, consulter
<https://github.com/erikmd/tapfa-init.el#readme>.

Pour Windows 10, consulter
<https://github.com/erikmd/tapfa-init-win64.el#readme>.

## Installation sous macOS

1. Installer [Aquamacs](http://aquamacs.org) (version GUI, recommandé)
   ou [Emacs avec Homebrew](https://formulae.brew.sh/formula/emacs)
   (version TTY).

1. Installer `gpatch`, `pkg-config` et `openssl` 1.1 avec Homebrew :

        brew install gpatch      # comme opam utilise des options GNU
        brew install pkg-config
        brew install openssl@1.1 # suivre les instructions si besoin

1. Installer `opam` 2.0 avec Homebrew :

        brew install opam

1. Configurer `opam` puis installer `merlin` et `coq` :

        opam init --auto-setup --yes --compiler=ocaml-base-compiler.4.05.0
        eval $(opam env)
        opam install -y merlin
        
        opam repo add --all-switches --set-default coq-released https://coq.inria.fr/opam/released
        opam pin add -n -k version coq 8.11.0
        opam install -j 2 coq

1. **Ne pas exécuter `opam user-setup install`**.

## Installation des modes Emacs pour OCaml et Coq

(*Reprendre à cette étape si vous travaillez sur un PC de l'UPS.*)

Pour installer automatiquement les modes
[tuareg](https://github.com/ocaml/tuareg),
[merlin-eldoc](https://github.com/Khady/merlin-eldoc),
[company](https://github.com/company-mode/company-mode),
[learn-ocaml](https://github.com/pfitaxel/learn-ocaml.el),
[ProofGeneral](https://github.com/ProofGeneral/PG) et
[company-coq](https://github.com/cpitclaudel/company-coq) :

1. Téléchargez et placez le fichier `.emacs` fourni à la racine de
   votre *homedir* (`~/`) :

        cd                    # pour revenir à la racine du homedir (~/)
        mv -f .emacs .emacs~  # pour sauvegarder votre fichier
        # si la ligne précédente renvoie une erreur, ne pas en tenir compte
        curl -fOL https://github.com/erikmd/tapfa-init-macos.el/raw/master/.emacs

    > *Note* : Si vous n'utilisez pas `curl` mais la fonctionnalité de
    > téléchargement de votre navigateur, veillez à ce que celui-ci
    > n'enlève pas le point au début du fichier
    > ([`.emacs`](https://github.com/erikmd/tapfa-init-macos.el/raw/master/.emacs),
    > pas `emacs`).

1. Si vous n'utilisez pas GNU Emacs mais *Aquamacs*, pour éviter un
   souci de connexion TLS avec MELPA (le gestionnaire de paquets
   d'Emacs), vous pourriez avoir besoin d'exécuter :

        brew install libressl
        brew install gnutls

    puis d'ajouter ces deux lignes au début du fichier `~/.emacs` :

        (with-eval-after-load 'tls
          (push "/usr/local/etc/libressl/cert.pem" gnutls-trustfiles))

    (*Source* : [davidswelt/aquamacs-emacs#133](https://github.com/davidswelt/aquamacs-emacs/issues/133))

1. Lancer Aquamacs (ou Emacs).

    L'installation des modes Emacs pour OCaml et Coq devrait se lancer
    automatiquement et durer environ 2'30.

    En cas de souci, faites
    <kbd>M-x package-install-selected-packages RET</kbd>
    (<kbd>M-x</kbd> désignant <kbd>Alt+X</kbd>
    et <kbd>RET</kbd> la touche Entrée) et redémarrez emacs.

    Vous pouvez alors **créer ou ouvrir un fichier OCaml** en tapant
    <kbd>C-x C-f tp1.ml RET</kbd>

## Remarque

En cas de problème avec cette configuration, ouvrez une [issue](https://github.com/erikmd/tapfa-init-macos.el/issues) ou envoyez-moi un [e-mail](https://github.com/erikmd).
