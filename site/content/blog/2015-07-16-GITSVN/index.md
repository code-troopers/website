---
author: Florian
cover: git-banner.png
date: '2015-07-16'
tags:
- GIT
- GIT-SVN
- Outils
- Productivité
title: GIT-SVN comment survivre dans un environnement hostile
url: /2015/07/16/gitsvn/
aliases: 2015/07/16/GITSVN.html
---


Git c’est cool, Git c’est Hype, Git c’est tout récent ([enfin presque](http://git-scm.com/book/fr/v1/D%C3%A9marrage-rapide-Une-rapide-histoire-de-Git)) et c’est pour ça qu’on aime bien.
Mais pour beaucoup Git c’est nouveau, donc c’est le changement, donc c’est compliqué, et c’est pour ça que plein de boîtes préfèrent garder leur serveur svn.

Je vais tenter ici, de vous donner les principales commandes de `Git-SVN`. Ainsi si vous vous trouvez dans une boîte qui ne veut pas changer son scm mais que vous, vous avez envie de changement,
vous pourrez donc utiliser la puissance de Git.
Et ce sans aucun impact sur le gestionnaire de sources de la société dans laquelle vous êtes. C'est génial non ?



## Prérequis

- Avoir Git-SVN d'installé ! Et ce qui est bien fait, c'est que Git-SVN fait partie intégrante de Git. C'est donc Git que vous allez installer : [www.git-scm.com](http://www.git-scm.com)
- Un accès au svn (l'url du projet qui vous intéresse fera largement l'affaire)
- Un terminal
- Un tout petit peu de courage


## Init du Projet
Le cas le plus courant est celui où tout le monde travaille sur le trunk du projet, et je vais partir de ce cas pour ce guide.
Si ce n'est pas le cas, il n'y a pas de gros changement, mais je vous invite à consulter plus en détail [la doc](https://git-scm.com/docs/git-svn)


Donc si on se met dans la situation où tout le monde travaille sur le trunk, pour récupérer les sources du projet dans un nouveau répertoire vous devrez faire un :

    git svn clone http://maboite/svn/monBeauProjet/ -s

Par contre dès que le repo svn est un peu vieux (i.e. avec plein de commits) ça va mettre 3h ! En effet, Git va prendre les révisions une par une afin de créer son historique local.
Si vous n’avez pas besoin de tout l’historique des révisions ce que vous pouvez faire c’est :

    git svn clone http://maboite/svn/monBeauProjet/ -s -r4000:HEAD

ainsi il ne crééra l’histo qu’à partir de la révision 4000 du svn. Je vous conseille donc de prendre le 4000 le plus proche de la dernière révision.

À partir de là c’est bon, vous avez votre projet qui est géré par Git. La preuve vous pouvez tester via ces différentes commandes

    git status
    git branch -a
    git log -n5


## Travailler sur le projet (en local)
Vous pouvez donc dès à présent commencer à travailler offline ou bien sans vous soucier des commits de vos collègues.
Et cela avec tous les avantages que Git apporte.

    git commit -m"Ajout de la modification du mot de passe par l'admin"
    git stash save “Début de ma tâche prioritaire”
    ... // un peu de travail urgent
    git stash pop

On peut même faire des branches Git (en local) sans que cela n'impacte le serveur.

    git checkout -b myLocalBranch
    ... // du travail avec plein de petits commits
    git checkout master
    git merge myLocalBranch


## Commiter sur le svn
Ensuite pour se synchroniser avec vos collègues (c'est mieux) les deux commandes indispensables sont

    git svn rebase
    git svn dcommit

Le `git svn rebase` va faire l'équivalent d'un svn update quant au `git svn dcommit` ça sera un svn commit.


## Bonus : Utiliser des branches
Bon soyons honnêtes si vous utilisez un svn il y a quand même peu de chances que les branches soient vraiment utilisées (ou alors peut-être que vous aimez la douleur). Mais si ça arrive, voilà comment les utiliser.

Mettre à jour toutes les branches du svn :

    git svn fetch

Changer de branche :

    git checkout -b <brancheDistante> <nomDeBrancheLocale>

Et maintenant vous pouvez naviguer entre vos branches normalement via Git  :

    git checkout master
    git checkout nomDeBrancheLocale
    git checkout -

et par exemple pour recopier un commit d'une branche à une autre sans copier manuellement le fichier.

    git cherry-pick


Voilà vous avez maintenant les bases pour utiliser Git alors que de premier abord cela ne semblait pas possible.
Il ne vous reste plus qu'à forcer un peu plus pour remplacer l'ancien serveur svn par un nouveau sous Git et comme ça toute votre boîte pourra en profiter.
<br/>
<br/>
Pour connaître les principales commandes Git, je vous invite à consulter [la page tutoriel de Git](http://git-scm.com/docs/gittutorial) ou alors de chercher sur [internet](http://lmgtfy.com/?q=git+commands).
