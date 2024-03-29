---
author: Cedric
cover: babun-banner.png
date: '2014-10-01'
tags:
- Shell
- Windows
- Tips
title: Babun un shell sous Windows
url: /2014/10/01/babun/
aliases: 2014/10/01/babun.html
---


## Oh non, mon client m'oblige à être sous Windows
Malheureusement, il est fréquent que nous soyons forcés de travailler sous un environnement que nous n'aimons pas. Les raisons sont souvent diverses mais sont presque toujours inflexibles. Le problème est que lorsqu'on est habitué à une ligne de commande puissante, le fait d'être sous Windows devient un réel handicap.


## Donnez moi un shell !
Bien sûr, la plupart d'entre vous connaîssent Cygwin, qui permet de résoudre bien des problèmes, mais qui en créé aussi un paquet avant d'avoir une installation complète et qui fonctionne comme attendu.

Heureusement,  [Tom Bujok](https://twitter.com/tombujok) s'est penché sur le souci et a pris le temps de faire une configuration aux petits oignons d'un Cygwin complet, avec `zsh` et `oh-my-zsh` pour avoir une bonne configuration. De plus, pour faire comme si on était sous un unix, on a même un package manager qui permet d'installer les outils nécessaires.

## Installation et configuration
Il suffit de récupérer le zip sur le site officiel [http://babun.github.io](http://babun.github.io/) de le dézipper et de lancer le script `install.bat`. Ce qui est bien, c'est qu'il est possible de lancer le script d'installation et donc d'utiliser babun sans disposer des droits d'administrateur sur sa machine.

Une fois la _longue_ installation terminée, vous disposez d'un shell bien configuré avec la plupart des outils nécessaires bien configurés.

Cependant vous voudrez certainement personnaliser votre environnement avec quelques alias. Pour ceci, il suffit de créer un fichier contenant vos alias dans `~/.oh-my-zsh/custom/aliases.zsh` (le nom est libre, le fichier doit porter l'extension  `zsh` pour qu'il soit automatiquement chargé). Il ne s'agit ni plus ni moins de la configuration permise par oh-my-zsh (vous pouvez vous référer [à cet article]({{< relref "2014-09-17-ohMyZsh.md" >}}) pour plus de détails)

<div style="text-align:center;margin:50px">
 <a style="display: inline" href="/images/posts/2014-10-01-babun/babun.png" data-lightbox="image-0" title="Babun et tmux">
         <img class="medium" src="/images/posts/2014-10-01-babun/babun.png" alt="Babun et tmux"/>
 </a>
</div>

## Conseils pratiques
Depuis quelques temps, nous sommes quelques membres de l'équipe à __devoir__ travailler  sous Windows. Nous avons rapidement ajouté `tmux` à la liste des outils indispensables (la gestion des terminaux Windows n'étant pas optimale) ainsi que `irssi` en tant que client IRC.

    $ pact install tmux irssi

Puisque c'est ni plus ni moins qu'une installation de Cygwin, l'accès à vos disque se fera par le montage `/cygdrive/c/` pour le disque `C:` par exemple. Veuillez noter également que l'emplacement de votre `home` sera en fait `/cygdrive/c/Users/$USER/.babun/cygwin/home/$USER`


Maintenant, vous serez presque aussi productifs sous Windows que sous un système "agréable" !
