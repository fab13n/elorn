---
layout: post
title:  "Gestion de l'eau en autonomie"
date:   2014-04-24 12:00:00
categories: plomberie
---

Pour ne pas dépendre d'un robinet à quai, nous avons conçu et installé
notre propre système de gestion de l'eau. Pour rester économiques,
nous avons faits quelques choix.

## Baisser la consommation

Tout d'abord, nous éliminons la chasse d'eau, qui représente
typiquement 1/3 de la consommation d'une maison. L'idée qu'un tiers de
ce qu'on potabilise nous sert à chier dedans dit quelque chose sur
notre société, qui me fait penser
[à ça](http://posters-for-good.tumblr.com/post/13199697341/just-wash-the-spoon)...
En dehors des toilettes sèches, qui règlent le problème des eaux
noires, nous ne conservons qu'un urinoir, qui utilise l'eau du canal
brute. Pour nous conformer à l'actuelle législation incomplète, il est
relié à une cuve de stockage ; nous déciderons comment la mettre en
œuvre le jour où les textes réglementaires seront clarifiés.

## Ne pas en faire trop

Ensuite, nous ne potabilisons pas plus que nécéssaire : le circuit
principal du bateau ne contient que de l'eau domestique. Elle est
filtrée contre les sédiments, au charbon actif pour arrêter les
réactifs chimiques, puis aux UV pour tuer tout ce qui contient de
l'ADN. Ça suffit pour les machines à laver, la douche, les
robinets. Puis nous avons un
[appareil à osmose inverse](http://www.osmoseur-optima.fr/PBSCCatalog.asp?ItmID=4100340),
qui fabrique de l'eau réellement potable, pour la cuisine et la
boisson. C'est l'unique robinet d'eau potable de la maison, que nous
complétons avec une bouteille à la salle de bains pour se laver les
dents.

[PHOTO]

_Les filtres à eau domestique._

L'eau potable est fabriquée par une membrane à osmose inverse. Elle
est protégée elle aussi par des filtres sédimentaires et à charbon ;
elle aussi a un débit très limité, mais un réservoir sous pression de
4 gallons (15l) nous permet d'en avoir toujours assez pour quelques
casseroles, une carafe d'eau et une cafetière. Nous ne savons pas à
quelle vitesse elle travaille, juste que nous n'avons jamais été à
court, donc la réponse est : assez vite ! Attention, si la pression
d'eau à bord est en dessous de 3-4 bars, l'osmose inverse ne marche
pas ; prévoir alors une pompe booster.

![Installation sous l'évier]({{ site.url }}/img/eau-evier-640.jpg)
_Installation sous l'évier : osmoseur, réservoir, chauffe-eau, vase
d'expansion, pompe de relevage, vanne 3-voies._

J'ai entendu des histoires comme quoi l'eau distillée (ou l'eau
osmosée, c'est pareil) serait problématique, pour cause de carances en
minéraux. J'ai cherché à creuser le sujet, savoir si les minéraux
contenus dans la nourriture, l'eau qu'on boit occasionnellement hors
du bateau palieraient cet éventuel problème. J'ai échoué à trouvé
quoique ce soit qui ne soit pas des répétitions de on-dits non
vérifiés, des cris hystériques de technophobes en manque de guerre
sainte, ou des confusions avec le phénomène réel mais presque sans
rapport du choc osmotique de réhydratation. Jusqu'à plus ample
informé, je pars donc du principe que le vin nous tuera avant l'eau
distillée :)

## Filtrer toute une cuve d'un coup

Les systèmes de filtrage en flux tendu coûtent relativement
cher--plusieurs milliers d'euros--et les consommables, des filtres de
20 pouces de haut, également. On peut arriver à des coûts de
fonctionnement proches du coût de l'eau de ville. Après quelques
expériences infructueuses, nous sommes arrivés à une solution meilleur
marché. Nous utilisons des filtres et des porte-filtres 10 pouces,
nettement moins chers ; leur débit étant moindre, nous produisons pas
l'eau en flux tendu, mais nous remplissons toute la cuve de 1500l d'un
coup, ce qui prend une dizaine d'heures. Une fois la cuve pleine, nous
rinçons les filtres (en les mettant dans un porte-filtre branché à
l'envers, qui fait passer dedans de l'eau filtrée en sens inverse), ce
qui multiplie leur durée de vie. Nous avons observé que cette durée de
vie était encore améliorée en laissant les filtres au sec entre deux
remplissages (soit 10 à 15 jours).

Le filtrage comprend donc dans l'ordre:

* la grille du
  [surpresseur](http://www.karcher.fr/document/pi/fr_FR/1.645-281.0_PI_fr_FR.pdf),
  qui siphonne et met sous pression l'eau du canal; les trous doivent
  faire environ 1/4mm
* un filtre bobiné 5µm;
* un filtre polypropylène 1µm;
* un filtre à charbon actif;
* une lampe à UV 6W.

La tuyauterie du système fait 1/4 de pouce, soit environ 6mm de
diamètre. Ça serait grossièrement inadapté pour une consommation en
temps réel, mais puisqu'il y a la cuve en aval, nous avons tout notre
temps. Par contre, une fois passé le dernier étage (la lampe UV),
mieux vaut mettre du tube plus large pour rejoindre la cuve, ça évite
une perte de charge inutile.

Les filtres les plus chers sont les filtres à charbon, qui luttent
contre les produits chimiques et les odeurs de vase. C'est parce
qu'ils sont les plus chers que nous les mettons en dernier, après le
filtre 1µm. De nombreux vendeurs proposent par défaut le montage en
ordre inverse. De plus, nous nous sommes aperçus qu'une cartouche vide
remplie de charbon actif en vrac faisaient parfaitement l'affaire,
pour un coût de revient nettement moindre.

Tout compris, le remplissage d'une cuve prend une dizaine de
minutes, essentiellement en nettoyage à la fin. Pour nous simplifier
la vie, nous avons mis les filtres au-dessus de la baignoire : ainsi
on ne craint pas les éclaboussures, et on peut combiner le lavage des
filtres avec une douche !

## Pression d'eau

Il y a trois pompes de pressurisation d'eau sur le bateau : le
surpresseur d'eau froide, qui alimente les filtres à eau, la chasse
d'eau et le Kärcher ; le surpresseur d'eau domestique, qui mainient la
pression dans les robinets entre 3 et 4 bars, en pompant l'eau de la
cuve ; et un surpresseur pour l'osmoseur, qui en améliore le rendement
(mais ne s'avère pas indispensable).

L'eau domestique est contrôlée par 2 vannes :

* Une vanne en sortie de surpresseur, qui permet de le désactiver. Il
  n'y a alors plus de pression à bord, à moins que le réseau d'eau de
  ville ne le fournisse ;

* Une vanne de remplissage de cuve, qui vide le circuit sous pression
  dans la cuve.

Il y a une entrée d'eau à tribord dans la salle de bains arrière. Si
elle est branchée à l'eau de la ville, c'est celle-ci qui pressurise
le bateau, et il faut désactiver le surpresseur.

**Attention :** la plupart des naufrages de bateaux-logement sont dus à
l'eau de la ville ! Un tuyau qui gèle, éclate et remplit le fond de cale,
ou encore un bloc de lest balladeur qui arrache un joint... Donc on ne
laisse jamais un bateau sans surveillance connecté au réseau ! Même
avant d'avoir la potabilisation, nous ne laissions l'eau de ville
allumée que le temps de remplir la cuve.

* Pour remplir la cuve : fermer le surpresseur, ouvrir la vanne de
  remplissage de cuve, ouvrir l'entrée d'eau de ville.

* Pour fonctionner sur la pression de la ville: fermer le surpresseur,
  fermer le remplissage de cuve, ouvrir l'entrée d'eau de ville.

* Pour fonctionner sur la cuve : fermer le remplissage de cuve, ouvrir
  la vanne du surpresseur.

## Pour résumer

![Diagramme général plomberie]({{ site.url }}/img/eau-diagramme.png)
_Schéma de principe._

![Plan de la plomberie]({{ site.url }}/img/eau-plan-640.png)
_Plan de la plomberie à l'avant du bateau._



## Améliorations possibles

### Dispositif anti-débordements

Il nous reste à installer une coupure automatique de la pompe lorsque
la cuve est pleine ; aujourd'hui nous n'avons qu'une alarme
anti-débordement, ce qui nous force à rester à portée d'oreille.
Plusieurs pistes possibles :

* Soit une électrovanne et une pile, reliées au relai de l'alarme où à
un vieux pressostat de lave-linge ;

* Éventuellement, un robinet-flotteur de chasse d'eau, mais difficile
  à glisser dans la cuve, et pas forcément très fiable ;

* Un système électronique, couplé à un monitoring de la production et
  de l'usage de l'eau, à base
  d'[Arduino](http://www.arduino.cc). _Overkill_, mais nettement plus
  rigolo à fabriquer :)

### Contrôle depuis l'habitacle

Autre aménagement mineur : pouvoir éteindre l'hydrophore depuis
l'habitacle (ce genre de pompe surchauffe quand elle tourne à vide
parce qu'on a oublié de remplir la cuve). Il faut aujourd'hui aller le
débrancher dans le peak avant.

Pour ne pas oublier de la remplir, il serait bon d'avoir une jauge
visible de l'habitacle. Aujourd'hui, il faut aller coller une forte
lampe contre la cuve, au fin fond d'un placard, pour voir le
niveau. Plusieurs possibilités :

* un contacteur cuve vide / cuve pleine de machine à laver. Défaut :
  ça ne donne qu'une indication binaire.

* une jauge de carburant à flotteur (un flotteur au bout d'une ficelle
  tire plus ou moins sur l'aiguille d'un indicateur). Le résultat est
  analogique, mais pour mettre l'indicateur hors du cagibis, il faut
  un bricolage avec poulies.

* une jauge tube transparent. Soit il faut trouer le fond de la cuve,
  et créer une source de panne potentielle, soit amorcer un siphon. Il
  faut en outre que le tube soit au même niveau que la cuve, donc dans
  la chambre avant (le sol de la salle de bains est 50cm au-dessus de
  la cuve). C'est probablement la solution la plus simple.

### Amélioration de la filtration

Toujours parmi les pistes que nous n'avons pas encore étudiées, un
premier étage de décantation devrait pas mal épargner les filtres à
sédiments : au lieu de pousser directement l'eau turbide du canal,
relier un tonneau au canal par un siphon, avec un brise-jet et
éventuellement un lit de sable ; ainsi, une bonne partie de la vase se
dépose au fond, notamment les particules fines qui encrassent les
filtres fins. Il faut faire très attention à ce que ce tonneau ne
puisse pas se renverser, sans quoi le siphon remplirait l'avant du
bateau !  Prévoir également du rab entre la ligne de flottaison et le
rebord du tonneau, et désamorcer ou fermer le siphon en navigation et
en hivernage.

Une autre piste est le filtre à sable auto-lavant pour piscines, en
plus ou à la place des filtres à sédiments. Certains bateaux les
utilisent avec succès, mais leur coût élevé fait que nous n'avons pas
essayé. À vérifier aussi, leur consommation électrique. Enfin, ils
sont faits pour traiter des eaux moins chargées que celles d'un canal,
et les vendeurs sont incapables de nous renseigner sur les finesses de
filtrage ; s'attendre donc à pas mal de tâtonnements avant de les
faire bien fonctionner.

## Coût de revient

### Consommables

Il faudra faire le bilan du coût total au mètre cube, en
consommables et en kWh. Il est pour l'instant difficile à évaluer,
nos expérimentations ayant pas mal affecté l'espérance de vie des
filtres. À la louche, compter :

* un filtre 1µm (3-4€) pour 5 à 15 cuves de 1500l
(ça dépend si l'eau est chargée, donc s'il a plu récemment) ;
* le charbon en vrac tient au moins aussi longtemps, et ne coûte pas grand
chose ;
* rajouter environ 1kWh d'électricité pour la pompe et la lampe à
UV.

On doit arriver autour de €0.50 le mètre cube.

### Investissement

Pour l'installation initiale, compter:

* 200€ pour un
[surpresseur correct](http://www.karcher.fr/document/pi/fr_FR/1.645-281.0_PI_fr_FR.pdf)
;
* à peu près autant en
[porte-filtres](http://www.osmoseur-optima.fr/PBSCCatalog.asp?ItmID=4100361) ;
* entre 150€ et 250€ pour
  l'[osmoseur](http://www.osmoseur-optima.fr/osmoseur-purificateur-d-eau-5-etapes-pompe-booster50gpd-c2x4100345),
  selon qu'on a besoin d'une pompe booster ou pas (nous aurions pu
  nous en passer, mais nous ne le savions pas).
* 50€ à 100€ de fournitures de plomberie diverses.

Nous avions déjà la cuve, et nous n'avons pas posé de passe-coque :
nous passons un tuyau annelé en siphon dans un
[écubier désaffecté](http://fr.wikipedia.org/wiki/%C3%89cubier). Nous
poserons probablement une vanne sous l'eau à la prochaine cale sèche.

Si on arrondi le mètre cube bateau à €0.50, le
[mètre cube d'eau potable à Toulouse à €3.50](http://www.ladepeche.fr/article/2013/10/29/1741811-prix-de-l-eau-potable-toulouse-peut-mieux-faire.html),
l'installation à €1000, et la consommation à
[150l/jour/personne](http://www.arpe-mip.com/files/EAU/DIAG_EAU_FICHES2011_PDF/III_PR-QUANT8_conso_domestique.pdf),
pour une famille de trois, on amorti le système en deux ans, sans même
prendre en compte le gain d'autonomie et la réduction des
risques. Autant dire que même au port, nous continuons à faire notre
eau nous-mêmes ! :)

