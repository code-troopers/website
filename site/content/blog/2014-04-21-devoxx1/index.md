---
author: Florian
cover: devoxx1-banner.png
date: '2014-04-21'
tags:
- devoxx
- Intellj
- live-coding
title: 'Retour de devoxx : Améliorer son live-coding'
url: /2014/04/21/devoxx1/
aliases: 2014/04/21/devoxx1.html
---


Je suis un développeur passionnné<sup><a href="#note1">1</a></sup> et, lors des conférences, JUG (ou toutes autres présentations) j'aime bien quand le speaker présente un petit bout de code pour illustrer ses propos.
Lorsque c'est du live coding, c'est encore mieux.
Le seul problème c'est que quand on n'est pas au Mariott et qu'il n'y a pas un vidéoproj de malade, en général dans l'audience, passé le 3<sup>ème</sup> rang, plus personne n'y voit rien.


Avant la présentation <a href="http://cfp.devoxx.fr/devoxxfr2014/talk/TYC-384/42%20IntelliJ%20IDEA%20tips%20and%20tricks%20in%2045%20minutes">42 IntelliJ IDEA tips and tricks</a> de Hadi Hariri (<a href="https://twitter.com/@hhariri">twitter</a>)
 la solution c'était de fermer toutes les views autour de la classe ouverte puis de faire un ctrl+scroll pour zoomer.
Cette époque est maintenant révolue, en effet, IntellJ possède un mode présentation qui s'occupe de faire tout cela.

Le résultat en deux screens de comparaison : utilisation classique vs mode présentation


<div style="text-align:center;margin:50px">
    <a href="/images/posts/2014-04-21-devoxx1/normalView.png" data-lightbox="group-1" title="Mode normal"  class="inlineBoxes">
        <img class="medium" src="/images/posts/2014-04-21-devoxx1/normalView.png" alt="Mode normal"/>
    </a>
    <a href="/images/posts/2014-04-21-devoxx1/presentationView.png" data-lightbox="group-1" title="Mode présentation"  class="inlineBoxes">
        <img class="medium" src="/images/posts/2014-04-21-devoxx1/presentationView.png" alt="Mode présentation"/>
    </a>
</div>


Pour activer le mode présentation ça se passe dans le menu `View` > `Enter Presentation Mode`. Et pour le quitter `View` > `Exit Presentation Mode`.

<div style="text-align:center;margin:50px">
    <a href="/images/posts/2014-04-21-devoxx1/menu1.png" data-lightbox="group-1" title="Menu pour passer en mode présentation" class="inlineBoxes">
        <img class="medium" src="/images/posts/2014-04-21-devoxx1/menu1.png" alt="Accès Menu présentation"/>
    </a>
    <a href="/images/posts/2014-04-21-devoxx1/menu2.png" data-lightbox="group-1" title="Menu pour quitter en mode présentation" class="inlineBoxes">
            <img class="medium" src="/images/posts/2014-04-21-devoxx1/menu2.png" alt="Retour normal"/>
    </a>
</div>


Bien évidement, assigner un raccourci clavier permettra d'être encore plus fluide pour switcher de mode.

<div style="text-align:center;margin:50px;">
    <a href="/images/posts/2014-04-21-devoxx1/settingShortcut.png" data-lightbox="group-1" title="Settings pour affecter un raccourci à l'action présentation">
        <img class="medium" src="/images/posts/2014-04-21-devoxx1/settingShortcut.png" alt="Settings pour raccourci"/>
    </a>
</div>


<div id="note1">[1] Une jolie faute d'orthographe sur le tshirt officiel de Devoxx que personne n'avait vu, mais qui a été révélée lors de la première keynote :-)</div>

PS : Les sources github visibles dans les screens ne sont pas de moi, vous pouvez les consulter à cet endroit <a href="https://github.com/winterbe/java8-tutorial">https://github.com/winterbe/java8-tutorial</a>.
