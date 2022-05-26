# ETUDE_ECOLE_LYON
l’étude d’une répartition optimale des écoles élémentaires et primaires de la métropole de Lyon
I.	RESUME

Notre projet porte sur l’étude d’une répartition optimale des écoles élémentaires et primaires de la métropole de Lyon. 
Est-ce que les écoles primaires et élémentaires qui sont présentent actuellement pourront satisfaire la population urbaine grandissante ? 
Peut-on améliorer la disposition géographique des écoles de la métropole avec la construction ou bien la suppression de ces dernières à des endroits stratégiques, afin d’en optimiser la répartition ? 
Nous avons décidé d’essayer d’apporter un début de solution à ces problèmes. Nous avons dans un premier temps collecté les données nécessaires à la mise en œuvre de notre projet (données sur les écoles de la métropole, IRIS, recensement de la population, …), nous les avons ensuite nettoyées, couplées et analysées afin d’en extraire les informations pertinentes. 
Ces informations nous ont permis d’établir un Dashboard interactif avec des cartes de la métropole de Lyon et les données relatives aux écoles. Nous pouvons accéder aux informations de chaque école grâce à une première carte et au nombre optimale d’école par zone IRIS grâce à une autre.


II.	INTRODUCTION

Aujourd'hui, 55 % de la population mondiale vit dans des zones urbaines, une proportion qui devrait passer à 68 % d'ici 2050. Les projections montrent que l'urbanisation, le déplacement progressif de la résidence de la population humaine des zones rurales vers les zones urbaines, combinée à la croissance de la population mondiale pourrait ajouter 2,5 milliards de personnes supplémentaires aux zones urbaines d'ici 2050. Cette croissance nous amène à nous questionner sur le futur de nos villes. 
Celles-ci doivent être prêt à faire face à cette inflation de la population dans tous les domaines. Et pour ce faire, nous avons commencé la transformation de nos villes en “smart city”.
La ville intelligente (“smart city”) est un nouveau concept de développement urbain. Il s’agit d’améliorer la qualité de vie des citadins en rendant la ville plus adaptative et efficace, à l’aide de nouvelles technologies qui s’appuient sur un écosystème d’objets et de services. Le périmètre couvrant ce nouveau mode de gestion des villes inclut notamment : infrastructures publiques (bâtiments, mobiliers urbains, domotique, etc.), réseaux (eau, électricité, gaz, télécoms) ; transports (transports publics, routes et voitures intelligentes, covoiturage, mobilités dites douces - à vélo, à pied, etc.) ; les e-services et e-administrations.
Nous avons décidé de nous pencher dans le domaine des infrastructures publiques, et plus particulièrement dans celui des écoles. Est-il possible d’optimiser le placement des écoles dans la métropole de Lyon afin d’avoir une distribution homogène par IRIS (découpe infra-communale) en fonction du nombre d’élèves ? 
C’est à cette question que nous allons essayer de répondre avec ce projet.

III.	DEMARCHE


1.	Collecte des données :

Nous avons dans un premier temps récupéré les données sur les écoles maternelles, élémentaires et primaire du département du Rhône pour les rentrées scolaires de 2019 à 2021 sur https://data.education.gouv.fr/explore/dataset/fr-en-ecoles-effectifs-nb_classes sous forme de CSV. Ce CSV contient des informations comme le nombre total d’élèves, le nombre total de classes, l’adresse des écoles, etc.
Cependant nous nous intéressons seulement à la métropole de Lyon, et nous avons donc ensuite scrapper toutes les communes qui composent cette métropole sur le site http://comersis.com/geo/geo/export-epci.php?dpt=69&epci=200046977 ,afin de pouvoir filtrer nos données uniquement sur ces communes.
Nous avons également collecté les données de recensement de la population de 2017 de l’INSEE (https://www.insee.fr/fr/statistiques/4799309). Ces données sont segmentées en ISIS (coupe infra-communale). 
Afin de pouvoir localiser ces IRIS, nous avons téléchargé un geojson qui contient les coordonnées de tous les IRIS de la métropole de Lyon (https://geo.data.gouv.fr/fr/datasets/12f369707684363538e617c8a60da3649a78d387)
Et enfin, afin de pouvoir localiser les écoles sur une carte et les attribués au bon ISIS, nous avons besoin des coordonnées de celles-ci. Nous les avons récupérés grâce à leurs adresses en faisant du scrapping sur ce site : https://www.coordonnees-gps.fr/ 



2.	Traitement et analyse des données

En nettoyant et en couplant toutes les données listées précédemment, nous avons réussi à obtenir un jeu de donnée avec le nombre d’écoles élémentaires (en 2021) ainsi que le potentiel nombres d’élèves (de 6 à 11 ans en 2023) contenus dans chaque ISIS.
Le nombre d’élèves en 2023 a été calculé avec le recensement de 2017.
Nous avons ensuite calculé la “densité” d’école par rapport au nombre d’élèves dans chaque IRIS puis la moyenne. Pour une répartition parfaite des écoles, il faudrait que leur “densité” par rapport au nombre d’élèves soit le plus proche de la moyenne possible. De ce fait, la répartition serait quasi homogène.
On va donc chercher le nombre d’écoles idéales dans chaque IRIS, et comparer avec le nombre d’écoles existants (en 2021). Cela va nous permettre de voir localement où il faudrait construire de nouvelles écoles élémentaires ou au contraire où il faudrait en supprimer.


3.	Création d’un Dashboard interactif

Afin de visualiser les données et de pouvoir les interpréter plus facilement, nous avons ensuite réalisé un Dashboard interactif à l’aide de Power BI. 
Power BI est un logiciel de data visualisation développé par Microsoft qui offre de nombreuses possibilités. Nous avons choisi ce logiciel car il nous permet de combiner plusieurs types de graphiques sur une même page (diagramme circulaire, carte, …) et pour son interactivité qui correspond à ce que l’on souhaite réaliser : carte interactive.
Ce Dashboard se compose de 2 pages :
•	Une page où l’on trouve le nombre total d’élèves, le nombre total de classe, la répartition en secteur public/privé et une carte avec toutes les écoles de la métropole. On peut filtrer par rentrée scolaire (2019/2020/2021) ou par école en cliquant sur la carte

•	Une deuxième page où l’on trouve le nombre d’école élémentaire, l’estimation de la modification que l’on doit apporter à ce nombre, le taux d’élèves de 6 à 11 ans dans la population estimé pour 2023.






IV.	RESULTATS


 Voici la première page du Dashboard (ici l’année 2021 est sélectionnée)
![image](https://user-images.githubusercontent.com/47990414/170431345-1c7f5f95-2af6-491a-942d-f146e01b579a.png) 
On peut avoir des informations sur une école précise en cliquant dessus sur la carte :

 ![image](https://user-images.githubusercontent.com/47990414/170431399-2a662322-94a9-4505-9c0d-46537d52ac04.png)

![image](https://user-images.githubusercontent.com/47990414/170431424-e08d864e-dc08-4878-b8a3-c9e5e9351ca0.png)

 

On peut également trier par secteur (ici privé et en 2020) :
![image](https://user-images.githubusercontent.com/47990414/170431474-ad144bcd-9d49-4cec-9644-3cb2171df5a9.png)


Voici maintenant la deuxième page du tableau de bord :

 ![image](https://user-images.githubusercontent.com/47990414/170431512-3989493c-caaa-4009-9a6a-4ff288ade7be.png)


On remarque qu’au total, pour une bonne répartition des écoles, il faudrait en construire 160.
On peut ensuite également trier par ISIS:
![image](https://user-images.githubusercontent.com/47990414/170431536-5bb70124-3994-41c6-b3db-6c3d31c787fa.png)

 

De cette manière, on remarque qu’à Genay il faudrait construire une deuxième école.
![image](https://user-images.githubusercontent.com/47990414/170431635-8ddc3c49-0fd3-4cb9-94dd-1cafa1e0257c.png)

 
Alors qu’au contraire à Essarts Nord, il faudrait en enlever 1
![image](https://user-images.githubusercontent.com/47990414/170431661-ea621852-f9eb-4f40-89a1-d5ed56902fd9.png)

 
Et à Fays-Bon Coin, il ne faudrait rien changer

V.	INTERPRETATION

Ici, le nombre d’écoles optimales par IRIS est calculé de manière statistique. Cependant, nous pourrions imaginer pouvoir le calculer de façon plus précise et plus juste à l’aide du machine learning ou du deep learning. 
En couplant cette information avec la prévision du taux d'élèves des écoles élémentaires dans quelques années, ces données pourraient être exploités afin d’identifier les lieux idéaux pour accueillir la construction de nouvelles écoles.
Cela aurait pour conséquence d’éviter d’avoir des IRIS qui comprennent 5 écoles pour 100 élèves ou alors 1 école pour 1000 et ainsi participer à une homogénéisation de la distribution des écoles sur le territoire.



















VI.	CONCLUSION

En conclusion dans cette étude, nous avons collecté données sur les écoles de la métropole, IRIS, recensement de la population et plusieurs autres informations, ces informations nous ont permis de faire une analyse pour voir la repartions des écoles et le nombre d’élèves pas écoles dans la métropole a travers un Dashboard interactif. Cette étude nous permet de dire qu’il y’a des zones dans la métropole de Lyon ou il faut penser à construire une école, et dans d’autre zone où il faut détruire. Nous pouvons allez plus loin dans cette étude et aussi intégrer par exemple le nombre optimal de maternité ou d’hôpital dans la métropole de Lyon. Ce qui permettra au gouvernement d’être plus efficace dans le long terme sur les investissements publics.
