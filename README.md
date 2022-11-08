# Introduction à Windows 11

Workshop d'introduction au workflow sous Windows 11 - WSL2

## Prérequis

- Clé USB de 8Go minimum
- Une deuxième clé USB pour sauvegarder vos données
- Windows 11 (clés de produit disponibles sur le [portail Azure](https://portal.azure.com/#view/Microsoft_Azure_Education/EducationMenuBlade/~/software)
- Une bonne connexion internet

## Installation

1. Télécharger l'[outil de création de média](https://www.microsoft.com/fr-fr/software-download/windows11) et lancer l'installation
2. Lire ce qu'il se passe, éviter de wipe le disque dur
3. Profitez-en pour sauvegarder vos données utiles (clés SSH par exemple)
4. Eteindre le PC une fois la création du support terminée

## Configuration

1. Démarrer le PC avec la clé USB branchée, accéder au menu de démarrage
2. Lancer l'installation depuis le boot menu de l'ordinateur (F9 sur HP, potentiellement F2 ou échap sur d'autres marques)
3. Lancer l'installation de Windows 11
4. **Attention** au moment de partitionner le disque dur, vous allez perdre vos données
5. Lancer l'installation et aller boire un café
6. Une fois l'installation terminée, Windows va redémarrer et vous guider pour la procédure de configuration
7. Eviter de se connecter à un compte Microsoft, on va utiliser un compte local (pour éviter les problèmes de droits avec le compte epitech). Si vous avez déjà un compte Microsoft perso, vous pouvez l'utiliser sans soucis
8. Une fois la configuration terminée, vous pouvez ouvrir votre session
9. Installer les mises à jour Windows
10. Supprimer le bloatware installé par défaut (ClipChamp, TikTok, etc.)

## Configuration de l'environnement de travail

1. Installer [Visual Studio Code](https://code.visualstudio.com/)
2. Installer [Windows Terminal](https://www.microsoft.com/fr-fr/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab)
3. Installer [Git](https://git-scm.com/download/win)
4. Installer [Discord](https://discord.com/download)
5. Installer tous les trucs utiles qui vous semblent nécessaires (7zip, VLC, etc.)

## Configuration de WSL2

1. Ouvrir Windows Terminal
2. Installer WSL Ubuntu `wsl --install -d Ubuntu-20.04`
3. Définir le défaut sur la version 2 `wsl --set-default-version 2`
6. Lancer la commande `wsl --list --verbose`
7. Vérifier sur la liste que Ubuntu 20.04 est bien installé en version 2
8. Eteindre le système WSL `wsl --shutdown`
9. Rallumer le WSL `wsl`
10. Lancer les mises à jour `sudo apt update && sudo apt upgrade`
11. Installer les essentiels pour faire du dev `sudo apt install build-essential gdb gdbserver valgrind clang clang-format clang-tidy clang-tools clangd cmake make git curl wget`
12. Optionel : installer zsh `sudo apt install zsh` et  [Oh My Zsh](https://ohmyz.sh/) pour avoir un shell plus sympa

GG à vous, normalement vous avez un wsl2 fonctionnel avec un environnement de dev C/C++ complet

> **Note** : Je vous recommande fortement de faire un raccourci vers le dossier home de votre WSL dans l'explorateur de fichiers. Le dossier est normalement présent en tant que lecteur réseau `Ubuntu` sous le dossier `Linux`. Vous pouvez aussi utiliser le raccourci `\\wsl$\Ubuntu\home\*nom d'utilisateur*` pour accéder au dossier home de votre WSL

## Configuration de Git

1. Configurer git `git config --global user.name "John Doe"`
2. Configurer git `git config --global user.email "example.random@email.com"`
3. Configurer git `git config --global core.editor "code --wait"`
4. Générer une clé SSH `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
5. Lancer le ssh-agent `eval "$(ssh-agent -s)"`
6. Ajouter la clé SSH à l'agent `ssh-add ~/.ssh/id_rsa`
7. Copier la clé SSH `clip < ~/.ssh/id_rsa.pub`
8. Ajouter la clé SSH à votre compte Github (Profile > Settings > SSH and GPG keys > New SSH key)
9. Essayer de cloner un repo avec SSH pour vérifier que tout fonctionne

## Configuration de VSCode

1. Lancer `code .` dans le dossier de votre choix depuis WSL
2. VSCode devrait télécharger le serveur WSL et s'ouvrir
3. Vous pouvez vous connecter pour synchroniser vos extensions

> **Note:** Si vous n'avez pas synchronisé vos extensions, vous pouvez installer une petite séléction personnelle depuis `extensions.sh` présent dans le dossier `vscode` de ce repo. C'est une liste des extensions que j'utilise pour le développement C/C++. Vous pouvez également remplacer le fichier `settings.json` dans %APPDATA%\Code par celui présent dans le dossier `vscode` de ce repo pour avoir une configuration similaire à la mienne.

> **Note v2** : Attention à votre format d'EOL, il faut que ce soit LF et non CRLF. Vous pouvez le vérifier dans les settings de VSCode. Si vous avez des problèmes de compilation, c'est peut-être dû à ça.

#

### Et voilà, vous êtes prêts à travailler sous Windows 11 !
Normalement, vous devriez avoir un environnement de travail complet avec un shell sympa, un éditeur de texte, un terminal, un client git et un environnement de dev C/C++ complet. Vous pouvez maintenant cloner vos projets et commencer à bosser.
Si vous avez des questions, n'hésitez pas à me solliciter !

J'hésite également à faire un workshop sur la configuration des outils JetBrains (CLion, PyCharm, etc.) sous Windows 11, n'hésitez pas à me dire si ça vous intéresse.