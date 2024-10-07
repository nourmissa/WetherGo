# WetherGo
une application d'étude des températures observées sur toute la planète depuis une centaine d'années à peu près,
L'idée est de pouvoir observer les variations de température en fonction de plusieurs critères et de pouvoir afficher ça,
simplement en demande. On veut donc, avoir une application où l'utilisateur puisse entrer des paramètres, 
quelle observation il veut regarder et avoir en affichage un tableau à deux dimensions.
On va identifier trois entrées qui vont être les filtres, donc, il peut filtrer soit sur une station, 
une période temporelle ou avoir une mesure exacte. Dire qu'il veut la température moyenne ou la température minimale de chaque journée, 
il va demander deux dimensions d'observation. Ça va être les dimensions sur lesquelles on va grouper les valeurs, par exemple les coordonnées géographiques,
les mesures, les périodes temporelles, etc et il va demander, donc, une opération d'agrégation : la somme, la moyenne, l'écart type, etc. Par exemple, prenons donc,
un premier exemple : un utilisateur veut connaître, pour chaque mois, le « range » de température moyenne de chaque journée, c'est-à-dire, 
l'écart entre la température la plus haute et la température la plus basse sur tout le long du mois, pour la température moyenne de chaque jour.
Ainsi donc, il va filtrer en disant qu'il veut uniquement la mesure température moyenne : TAVG. Il va demander les deux dimensions,
donc, la première dimension ça sera Month et la seconde dimmension VOID, cest-à-dire qu'elle n'existe pas, il n'y aura pas de seconde dimension.
 Et il va demander l'opération RANGE qui permettra de connaître sur la plage de température demandée 
 quel est le plus gros écart et il va obtenir un tableau comme celui affiché à droite, c'est-à-dire pour janvier 2016 : 10°C, pour février 2016 : 19°C, etc.
 Un autre exemple serait de vouloir connaître pour chaque année, la moyenne de chaque mesure entre 2010 et 2011, donc, cette fois-ci on ne filtre plus sur une mesure précise,
 on va prendre toutes les mesures, mais on va filtrer, par exemple, sur une période. On va demander de début 2010 à fin 2011. On va choisir comme deux dimensions,
 donc, la première dimension ça sera les mesures et la seconde dimension, ça sera l'année. On va grouper en fonction de ces deux dimensions,
 toutes nos données et on va réaliser une moyenne à chaque fois, pour chaque mesure chaque année. Ainsi donc,
 on va obtenir le tableau disponible à droite qui nous dira que la moyenne des températures moyennes sur 2010 sera de 10°C,
 la moyenne des températures moyennes sur 2011 de 11°C, la moyenne des températures minimales de chaque journée sur 2010 de 5°C, etc.
 L'idée est de fournir un outil d'analyse adapté aux températures que nous allons développer au sein de cette application. 
 Découpons à présent cette application afin de pouvoir voir comment nous allons la concevoir. Nous allons partir toujours,
 donc, d'un utilisateur qui sera sur Internet, ça sera un internaute qui va remplir un formulaire pour exprimer son besoin. Il veut, 
 donc, on a dit, la moyenne des températures moyennes sur chaque année. 
 On va en PHP récupérer les paramètres transmis par le formulaire de l'internaute, on va procéder en première étape aux filtrages des données à utiliser, 
 on va enregistrer ensuite les données aggrégées dans MySQL avant de les récupérer en PHP et de les afficher dans le navigateur web.
 Alors, voyons d'où vont venir nos données. Nos données d'abord vont venir d'internet. Forcément, on va avoir les données qui vont être disponibles sur internet,
 on va les récupérer via du cUrl, on va les importer dans l'HDFS, dans le Système de Fichiers distribués d'Adobe.
 A partir de là, on va faire un import en MapReduce Dans HBase et ça sera HBase qui fera l'agrégation des données et donc, le groupe, selon les dimensions demandées,
 pour mettre les résultats dans MySQL. MySQL sera alors interrogé par PHP pour faire les traitements et l'affichage graphique directement en web.

https://www.ncei.noaa.gov/pub/data/ghcn/daily/  

