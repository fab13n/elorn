---
layout: post
title:  "Gestion de l'électricité sur Elorn"
date:   2014-05-03 12:00:00
categories: électricité
---

L'électricité à bord peut venir de quatre sources :

* la prise de quai ;
* le groupe électrogène ;
* les panneaux solaires ;
* les batteries.

Quand elle est disponible, l'électricité du quai est la plus facile et
illimitée, bon marché et silencieuse. Débranché, le groupe et les
panneaux ne fonctionnent pas en permanence, et pas forcément quand on
a besoin d'énergie ; ils ont donc vocation à remplir les batteries,
d'où on repompera l'énergie quand on en aura besoin.

## Groupe

Le groupe est fait pour générer 6kV, soit 5kW (à cause du
[cos phi](http://fr.wikipedia.org/wiki/Facteur_de_puissance)). Son
rendement optimal est autour de 3/4 de la puissance nominale,
soit 3.75kW, régime auquel il consomme environ 1.5l de fioul par
heure. Les batteries acceptent rarement plus de 50A en recharge,
soit 1.5kW, donc il est bon de profiter du lancement du groupe pour
faire fonctionner les autres appareils gros consommateurs :
lave-linge, lave-vaisselle, boost du frigo+congélateur, Kärcher et
outillage, éventuellement chauffe-eau...

Il tourne au fioul--on a encore le droit de fonctionner au fioul rouge
plutôt qu'au diesel pour le groupe, à l'inverse du moteur de traction.
L'essence est interdite en salle machines, car elle dégage des vapeurs
explosives. Ça signifie que si on veut remplacer le groupe actuel par
un petit groupe inverter silencieux à essence de 2kW, qui serait
pourtant parfaitement adapté à notre capacité de charge batteries, il
faudra le mettre sur le pont, et se renseigner sur les normes de
stockage de l'essence (je pense qu'un réservoir extérieur sera
obligatoire). Un tel changement n'a pas de sens économique
aujourd'hui, vu les prix comparés du fioul et de l'essence en
France. Il aurait un intérêt pour le silence, par contre : un groupe
essence insonorisé de petite puissance coûte 300€ pour un usage
occasionnel, 1000€ pour de la qualité pro ; compter 1500€ à 4000€ pour
un groupe diesel, qui en plus fera au moins 4kW !

## Chargeur-Onduleur

Les batteries sont gérées par un
[Victron Multiplus 3000W/24V/70A/16A](http://www.victronenergy.fr/inverters-chargers/multiplus-12v-24v-48v-800va-3kva/)
C'est un appareil qui combine charge des batteries depuis le 230V, et
retransformation de l'électricité batteries en 230V. L'intérêt de
combiner, c'est qu'il sait faire un certain nombre de choses
intelligentes :

* lisser la montée en charge : si d'un seul coup on pompe 3kW, ça peut
  faire caler le groupe électrogène. Si on le fait à travers le
  Victron, il va lisser cette montée grâce aux batteries, pour laisser
  le temps au groupe de monter en puissance.

* lisser les courants d'appel : les moteurs électriques monophasés,
  donc les pompes, ont un courant d'appel très fort quand ils
  démarrent (les bobines se comportent alors comme des
  fils). l'inverseur peut encaisser 6kW le temps qu'un moteur démarre
  et redescende à sa consommation nominale.

* limiter la comsommation à quai sans se priver à bord : si on est
  connectés de façon artisanale, avec des câbles trop longs et trop
  fins, une bonne partie de l'électricité s'évapore en échauffement de
  ces câbles lorsque la puissance monte (quand on multiplie la
  puissance demandée par 2, on multiplie par 4 les pertes dans les
  fils). On peut configurer le Victron pour qu'il limite la demande
  sur le quai : au lieu de pomper 3kW un quart du temps, il pompera
  750W en permanence, et utilisera les batteries pour temporiser.

* Et bien sûr, avec un onduleur de bone qualité, on récupère en sortie
  un signal parfait qui ne met pas l'électronique délicate en danger,
  même si notre vieux groupe produit un signal pas très régulier.

## Batteries

Pour le choix des batteries, nous avons opté pour un banc de 4
batteries
[6V semi-traction deep discharge](http://www.batterie-solaire.com/batterie-deep-cycle-us-6-v-430-ah-cr430-batterie-crown-c2x11755324),
contenant de 400Ah à 500Ah selon la vitesse de décharge, soit 10kWh à
12kWh. Pour faire 24V, elles sont montées en série, ce qui simplifie
la vie (la mise en parallèle de batteries est potentiellement
délicate).

Bien traité, ce banc de batteries doit tenir une dizaine d'années
avant de commencer à perdre en capacité. Il existe des batteries à
plaques tubulaires, deux fois plus durables et 2-3 fois plus chères,
mais nous avons choisi de ne pas investir là-dedans : en effet, d'ici
10 ans avec l'essor des véhicules électriques, le prix et les
performances des batteries auront sûrement radicalement changé, et les
batteries actuelles seront considérées comme obsolètes. Aujourd'hui
déjà, [Tesla](www.teslamotors.com) propose de préfinancer pour $12000
une batterie lithium 85kWh de rechange disponible dans 8 ans. Ça
signifie qu'ils espèrent d'ici là avoir fait baisser les prix en
dessous 140€/kWh, contre plutôt 700€/kWh aujourd'hui. Et tout ça sans
prendre en compte d'éventuelles nouvelles technologies, par exemple à
base de graphène, de super-condensateurs, de piles à combustible...

Le choix du voltage dans les batteries (on peut travailler en 12V, 24V
ou 48V) a été fait un peu par défaut, parce que la partie navigation
du bateau fonctionne en 24V. Un plus haut voltage permet une meilleure
efficacité, mais les appareillages sont moins communs. On peut
transformer facilement entre 12V, 24V et 48V avec des convertisseurs
DC/DC.

Le dimensionnement des batteries en kWh a été lui aussi fait un peu au
hasard : les batteries au plomb préfèrent ne pas être déchargées plus
qu'à moitié, soit 6kW pour nous. Ça correspond à 2 jours de
consommation estivale sans se priver aujourd'hui, sachant qu'on a des
facteurs d'économies futures, notamment si on installe un chauffe-eau
solaire.

Nous avons finalement choisi de ne pas enrichir le circuit 24V du
bateau, de garder les composants clef (frigos, pompes et lumière) en
230V. Ce qui nous a découragé de tenter le passage 24V :

* grosses intensités = gros échauffements = risques d'incendie, et
  nécéssité de passer de gros câbles. En particulier, l'hydrophore à
  l'avant du bateau peut faire des appels de courant considérables.

* l'offre en réfrigération 24V n'est pas terrible. À part le
  [Steca PF166](http://www.steca.com/index.php?Gefriertruhe_fr),
  malcommode du fait de sa forme bahut, les appareils sont plus
  optimisés pour gagner de la place que pour la consommation. Un
  [frigo congélateur 230V haut de gamme](http://www.bosch-home.fr/nos-produits/le-froid/refrigerateurs/KGE36AL40.html)
  consomme moins de 500Wh/j, soit autant que le Steca en mode
  congélateur, pour un frigo / congélo 1/3 plus grand et très
  ergonomique.

* les diodes 24V sont pénibles à trouver et chères, on aurait donc de
  toutes façon intercaler des transfos 24/12, ou faire des bricolages
  pour mettre des diodes 12V en série par 2.

* Au final, même si la baisse de rendement due au passage par le 230V
  nous coûte quelques centaines de Wh par jour, 100Wh dans les
  batteries c'est moins de 5 minutes de groupe électrogène, ou de
  panneaux en plein cagnard : on a choisi de s'offrir ce luxe !

## Panneaux

![Panneaux]({{ site.baseurl }}/img/electricite-panneaux-640.jpg)
_250kg de panneaux avant, pendant et après leur pose._

Les panneaux sont des
[thin-film](http://www.sharp.eu/cps/rde/xchg/eu/hs.xsl/-/html/product_details.htm?product=NAE135G5)
; ils ont un rendement moindre que les panneaux classiques cristallins
par mètre carré (pas forcément par euro au prix d'achat), mais une
production plus régulière. Ils captent surtout dans le rouge et le
proche infrarouge, des couleurs qui passent mieux les nuages et les
ombres partielles des arbres que le proche ultra-violet que préfèrent
les panneaux cristallins. Au top de leur forme, sous le soleil de
midi, les 12 panneaux peuvent produire 1200W.

Attention, il y a deux mesures pour la puissance des panneaux : celle
affichée en gros est mesurée sous 1kW/m2 d'ensoleillement avec le
panneau à 20°C, ce qui n'arrive jamais : on n'atteint pas 1kW, et sous
le soleil des panneaux noirs ne restent pas à 20°C. Leur rendement
baisse quand la température monte. Il faut chercher leur puissance
NOCT (Normal Operating Cell Temperature): mesure prise sous 800W/m2,
avec un air ambiant à 20°C et 1m/s de vent, et le panneau à sa
température réelle sous ces conditions. Mes panneaux sont a 135W
nominaux, mais 100W NOCT.

Derrière, il y a un MPPT, un appareil qui adapte son impédence en
entrée pour maximiser la puissance des panneaux, et retransforme ce
voltage côté batteries pour les charger le plus efficacement
possible. Nous avons pris un
[Victron](http://www.victronenergy.fr/solar-charge-controllers/mppt7550/),
pour être sûrs qu'il s'entende bien avec le MultiPlus et parce qu'ils
sort des infos de monitoring
[par une ligne série](http://www.victronenergy.com/upload/documents/Whitepaper-Data-communication-with-Victron-Energy-products_EN.pdf)(PDF),
qui permettront un jour d'automatiser la surveillance du système
électrique. Le moniteur de batteries et le chargeur/onduleur ont des
sorties comparables.

Les panneaux sont fixés sur des profilés en aluminium, eux-mêmes
collés au Sikaflex sur les écoutilles en acier galvanisé. Ils ne
peuvent être posés directement, n'ayant pas de cadre, et sur un
bateau, on essaie d'éviter les trous, surtout à la verticale : tôt ou
tard ils finissent par causer des infiltrations. Le Sika polyuréthane
colle bien les deux métaux, est suffisamment souple pour encaisser les
dilatations, absorbe les vibrations... Quand on considère en outre la
faible inclinaison des panneaux, donc leur faible propention à glisser
plus bas, c'est une solution simple et suffisante. De plus, si on
change un jour de format de panneaux (les technologies risquent
d'évoluer considérablement ces prochaines années, et les prix
pourraient continuer de s'effondrer), les supports seront
raisonnablement faciles à repositionner.

La connectique est standard : des fiches MC4 avec des duplicateurs et
des triplicateurs. Ce type de prise est étanche quand elles sont
connectées.

Pour les protéger contre le vol, il est bon de neutraliser certaines
vis de montage. Plusieurs techniques : coller le filetage, détruire
l'empreinte hexagonale à la perceuse, la remplir de pâte polymère
époxyde, mettre un roulement à bille pris dans la colle thermique (ça
a l'intérêt de pouvoir être démonté au décapeur thermique)... Mais le
poids des panneaux, leur surface, leur absence de cadre, leur voltage
atypique en font de toutes façons un butin difficile à prendre et
écouler.

### Pour résumer

![schema électrique]({{ site.baseurl }}/img/elect.png)
_Schéma de principe des sources électriques du bateau._

## Les consommateurs

Il est plus facile de ne pas consommer des watts que de les
produire. Nous changeons donc progressivement nos appareils pour
limiter cette consommation. Dans l'ordre, les plus gros consommateurs
sont le chaud (habitation et eau chaude sanitaire), puis le froid
(frigos, congélos, clim). La cuisine consomme fort mais peu de temps ;
de façon générale, on a tendance à surestimer la consommation des
appareils puissants mais d'usage ponctuel, et sous-estimer les
appareils peu puissants mais en fonctionnement permanent. Une paire de
boitiers Freebox Revolution consomme 200kWh par an, autant qu'une
machine à laver, et quatre fois plus qu'une bouilloire électrique...

### Froid

Nous avons déjà remplacé le frigo et le congélateur par
[ce que nous avons trouvé de plus efficace](http://www.bosch-home.fr/nos-produits/le-froid/refrigerateurs/KGE36AL40.html)
sans sacrifier le confort. Il y a moyen de mieux faire, surtout en se
passant de congélateur, mais nous ne sommes pas prềts à renoncer à ce
confort. La clim, comme le chauffage électrique, est bien sûr à
proscrire en navigation.

### Chaud

Le chauffage électrique est inenvisageable, même en pompe à chaleur
(cet hiver, très doux, elle prenait 20kWh par jour, alors qu'il n'y a
pas de soleil sur les panneaux). Nous avons actuellement un poêle très
joli et très inefficace (surdimensionné et vieux d'au moins 30
ans). Il va être remplacé par 1 ou 2 poêles. Idéalement, nous
mettrions un petit poêle à pellets programmable, et un
poêle-cuisinière à convection, pour chauffer vite et fort tout le
bateau et faire la cuisine. Si on s'en tient à un seul appareil, nous
ne sommes pas décidés. Le problème du poêle à pellets, c'est qu'il a
une consommation électrique non négligeable ; il est très difficile de
la retrouver dans les documents, et les vendeurs n'en savent rien. Il
existe bien quelques poêles sans électricité, mais s'ils sont non
programmables ils perdent l'essentiel de leur intérêt.

### Eau sanitaire

Nous espérons bientôt installer un chauffe-eau solaire ; si nous
décidons que nous voulons être autonomes l'hiver, il nous faudrait
passer le circuit caloporteur dans un bouilleur de poële, d'autant que
l'eau chaude n'est pas indispensable en été (la cuve d'eau est à
températuer ambiante). Il existe deux grandes variantes : le
thermosiphon sans électricité, et le système split, où une pompe
électrique fait circuler le caloporteur dans les panneaux. Le problème
du thermosiphon, c'est que la cuve doit être plus haute que les
panneaux, donc c'est moche et encombrant. Du reste, s'il y a assez de
soleil pour chauffer l'eau, les panneaux électriques sont sûrement en
train de produire aussi. Si le contrôleur de pompe n'est pas trop
idiot, il coupera la circulation par temps couvert.

En attendant, l'eau chaude au groupe électrogène est une aberration
écologique, mais moins ruineuse qu'il n'y parait. Le chauffe-eau fait
150l, 1800W, et la chaleur spécifique de l'eau est de 4200
J/kg/K. Donc il chauffe le contenu du ballon de 10°C/heure (1800[W] *
3600[s/h] / 4200[J/kg/°] / 150[kg]). Pour ça, on brûlera 1€ à 2€ de
fioul, et il nous restera 3kW d'électricité, pour mettre un peu plus
d'1kWh dans les batteries et faire tourner diverses machines.

### Autres appareils

L'essentiel de la consommation du lave-linge et du lave-vaisselle
servent à chauffer l'eau ; il serait donc bon soit de les alimenter en
eau chaude solaire, soit d'acheter des modèles à double entrée
d'eau. Pour l'instant, on se contentera de les faire tourner en cycles
courts, en même temps que le groupe. À noter, les mesures énergétiques
des lave-linges sont faites pour des cycles coton 60°C, ce qui ne
correspond pas du tout à nos habitudes (nous lavons surtout entre 30°C
et 30°C). Il est donc difficile de juger l'efficacité d'un appareil
sur papier, même sans prendre en compte l'eau chaude solaire.

Nous avons aussi un
[vélo-cargo](http://bakfiets.nl/eng/modellen/cargobike/short)
[électrifié](http://www.cyclone-tw.com/), pour emmener les enfants à
l'école et faire les courses. C'est une consommation vite éliminée :
il suffit de charger au boulot le jour plutôt qu'au bateau la nuit :)
L'ordre de grandeur est d'1kWh dans les batteries, en comptant large
(pertes dans le chargeur et âge canonique des batteries de récup) :
négligeable à quai, mais pas en amarrage sauvage.

![Panneaux]({{ site.baseurl }}/img/electricite-bakfiets-640.jpg)
_Notre seconde voiture électrique de bobos._

Pour la lumière, évidemment, diodes ou fluo-compactes partout. Le plus
difficile est d'éduquer les enfants, voir les adultes, à ne pas tout
laisser allumé inutilement. Placer des spots aux endroits stratégiques
devrait pas mal aider aussi. Il nous reste des 24V sur batteries du
propriétaire précédent, mais avec leurs ampoules à filament, elles ne
sont pas rentables. Elles ont un intérêt cependant : même si on éteint
l'onduleur la nuit, on a toujours de la lumière pour trouver les
toilettes :)
