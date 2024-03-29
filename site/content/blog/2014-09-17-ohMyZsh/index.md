---
author: Matthieu
cover: ohmyzsh-banner.png
date: '2014-09-17'
description: Présentation de oh-my-zsh l'outil qui facilite la configuration du shell zsh
tags:
- zsh
- shell
- oh-my-zsh
title: 'oh-my-zsh : l''outil indispensable pour avoir un zsh bien configuré.'
url: /2014/09/17/ohmyzsh/
aliases: 2014/09/17/ohMyZsh.html
---


## Introduction
Que l'on soit dev, ops, sysadmin ou autre pour effectuer nos tâches répétitives et quotidiennes on a généralement deux possibilités : une première communément appelée "clic-clic" qui consiste à utiliser les interfaces graphiques aussi souvent que possible (afin de perdre un maximum de temps) ; et une seconde qualifiée de "barbue" qui elle est orientée ligne de commande, scripting et automatisation.
Nous les Code-Troopers, on est plutôt technique de barbus ! Et donc peut importe l'OS qu'on utilise on cherche toujours à avoir le meilleur terminal possible.
Par défaut sous linux ou mac OS on trouvera souvent _bash_, sous windows ce sera _powershell_ mais il en existe d’autres comme _csh_, _ksh_ ou dans le cas qui nous intéresse _zsh_.
_zsh_ est puissant mais ce n’est pas le sujet du jour de dire pourquoi il serait mieux qu’un autre. En revanche, qui dit puissance dit difficultés de paramétrage ;
d’ailleurs à la première utilisation lorsque l’on n’a pas de fichier de configuration il commence par dire qu’il peut en créer un pour nous mais qu’il faudra le modifier à la main.
Ce sera inutile grâce à _oh-my-zsh_.



## Installation
C'est très simple, il suffit de cloner le dépôt
`git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh`
Et de mettre le fichier de configuration dans son home
`cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc`

## Les thèmes
Premièrement, les couleurs. Chacun ses goûts mais comme tout  informaticien fan de  matrix on a tendance à configurer son terminal pour obtenir du vert sur fond noir donc on choisira un thème en conséquence pour avoir des couleurs claires (ce qui est le cas de presque tous les thèmes) Vous pouvez voir un aperçu des thèmes ici : [http://zshthem.es/all/](http://zshthem.es/all/)

Deuxièmement le prompt. Toujours sur le site [http://zshthem.es](http://zshthem.es), vous pouvez voir qu’en plus des couleurs, chaque thème a un prompt différent. C'est ce qui s'affiche à chaque ligne donc il doit être beau, rapide et fonctionnel.
J'utilisais [https://github.com/nojhan/liquidprompt](https://github.com/nojhan/liquidprompt) pendant un temps, j'ai donc fait un thème qui ressemble pour les fonctionnalités qui me manquaient. Les fonctionnalités que je trouve pratique :

 - l'heure à droite : je veux savoir à quelle heure j'ai lancé une commande et à quelle heure elle s'est finie. C'est utile de temps en temps.
 - l'utilisateur courant : je veux savoir avec quel utilisateur je suis connecté, simplement parce que je veux que ça crie si je suis en root pour éviter de faire des bêtises
 - le hostname : je veux savoir sur quelle machine je suis connecté, de préférence uniquement lorsque je suis en ssh sinon c'est pas utile, toujours dans le but d'éviter les bêtises.
 - un path de taille limitée : pas besoin d'afficher `/home/mattboll/workspace/projetSecret/java/com/codetroopers/projetxx/machin/bean` il me suffit de lire `~/.../machin/bean` pour savoir où je suis et ça permet de toujours avoir un prompt de taille raisonnable, c'est plus agréable.
 - des infos git : sur quelle branche je suis, est-ce que je suis synchro, est-ce que je dois merger, combien j'ai de commits en attente d'être pushé etc.
 - le code retour de la commande : parfois des commandes sont en erreur mais on n’a pas de message, donc on ne sait pas si la commande s’est bien exécutée, et en supposant qu’elle soit mal exécutée on ne sait pas quelle était l’erreur (l’équivalent des erreurs 404, 503 etc. des erreurs http)

Pour choisir le thème il faut éditer le fichier `~/.zshrc` et modifier la ligne
`ZSH_THEME=”nom_du_theme”` où nom du thème correspond au nom de fichier que l’on peut trouver dans `~/.oh-my-zsh/themes`. Du coup, pour réaliser un thème personnel c’est simple il suffit de créer un fichier qui s’appelle nom.zsh-theme et de le mettre dans le même répertoire que les autres.
Voici ce que cela donne avec mon thème (adapté du thème sunrise), que vous pouvez trouver  sur [GitHub](https://raw.githubusercontent.com/mattboll/zshrc/master/mattboll.zsh-theme) :

<div style="text-align:center;margin:50px">
<a style="display: inline" href="/images/posts/2014-09-17-ohMyZsh/oh-my-zsh-theme.png" data-lightbox="image-0" title="Thème oh-my-zsh">
        <img class="medium" src="/images/posts/2014-09-17-ohMyZsh/oh-my-zsh-theme.png" alt="Thème oh-my-zsh"/>
</a>
</div>

## Les plugins
Les plugins permettent d'incorporer des fonctions spécifiques. Ce sont en général de simples alias mais il arrive aussi de tomber sur des fonctions utiles auxquelles on ne pense pas, par exemple en activant le plugin GitHub, on accède à la commande `empty_gh` qui prend en paramètre le nom du dépôt et qui va créer le répertoire, faire un git init, ajouter un readme vide et faire le premier commit.
Pour ajouter des plugins, il faut évidemment éditer le fichier `~/.zshrc` et modifier la ligne `plugins=(liste des plugins)`
Vous trouverez la liste des plugins dans `~/.oh-my-zsh/plugins` À l’heure où j’écris il y en a 172, de git à symfony en passant par heroku. Pour savoir à quoi ça correspond, le plus simple est de lire le code source, en général il y a un fichier par plugin et les noms sont assez explicites pour savoir ceux qui nous seront utiles ou pas.

## Les libs
Si vous voulez créer un plugin ou que vous voulez voir un peu plus les fonctionnalités de oh-my-zsh, vous pouvez parcourir le répertoire lib, ne serait-ce que pour le fichier aliases.zsh qui définit des alias de base, par exemple `“…”=”cd ../..”` ou les habituels `la`, `ll` etc. C’est aussi dans ce répertoire que sont définies des fonctions génériques comme celle qui permet de savoir si le dépôt git est “dirty” et qui est utilisée dans certains prompts.


Si vous voulez plus d’informations sur zsh je vous invite à commencer par l’article de [gcu-squad](http://wiki.gcu.info/doku.php?id=unix:zsh_le_z_shell). Pour oh-my-zsh vous pouvez allez voir le projet sur [GitHub](https://github.com/robbyrussell/oh-my-zsh). Enfin, si vous avez d’autres questions, n’hésitez pas à poster un commentaire ou à en parler sur twitter [@codetroopers](http://twitter.com/codetroopers) ou [@mattboll](http://twitter.com/mattboll)


----------
