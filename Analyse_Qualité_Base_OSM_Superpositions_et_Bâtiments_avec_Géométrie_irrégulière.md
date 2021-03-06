
# 2018-08-27 Analyse Qualité Base OSM: Superpositions et Bâtiments avec Géométrie irrègulière - Comparaison de différents projets
Dans un [premier article](Analyse_de_la_géométrie_des_bâtiment_pour_une_meilleure_qualité_OpenStreetMap.md) sur ce Blog le 8 août, nous avons présenté notre classification de la forme des bâtiments. À titre d'exemple, nous avons examiné les données de bâtiments de la base OSM ajoutés pour la réponse Ebola au Nord-Kivu et mesuré la proportion de bâtiments de forme irrégulière.  Ceux-ci sont généralement en petit nombre. 

Des proportions élevées d'immeubles de forme irrégulière dans une zone sont une indication qu'il est nécessaire de valider la qualité du tracage des contours de bâtiments dans la zone.  Dans les milieux urbains denses, le défi est grand pour tracer avec précision le contour des immeubles et les allées entre ces immeubles. La situation se complique également
lorsque les images disponbiles sont sombres ou floues ou encore si différentes images ne sont pas parfaitement alignées. Les mapathons où un grand nombre de débutants participent sont aussi susceptible de causer des problèmes de qualité de la donnée OSM.


*Figure 1 Polygones non valides / Outil Qualité*
![Figure 1 Polygones non valides](img/Kisenso_test_self_overlap_polygon_vs_osmose_flag.png)

Dans de nombreux projets, le Gestionnaire de tâches OSM a pour rôle de répartir la tâche entre un grand nombre de contributeurs simultanés  et éviter les collisions et conflits d'édition. Les coordonnateurs d'un projet de cartographie s'assurent de couvrir systématiquement le territoire lors des étapes de cartographie et de validation des données de la zone. Les différents outils Qualité permettent également d'identifier les problèmes de la zone et de les corriger. Cependant, nous constatons souvent qu'après un mapathon, les données peuvent rester inchangées pendant des années parce qu'il n'y a pas assez de contributeurs pour parcourir la zone et corriger les données.  Aussi certains aspects de la coordination ne sont pas couverts par ces outils. Les indicateurs de suivi du gestionnaire de tâches sont assez limités avec une simple indication qu'un carré est complété et validé. Aucune évaluation des données ajoutées si ajoutées.  Nous devons compter sur les validateurs. Mais soit les contributeurs inexpérimentés valident, soit les contributeurs expérimentés sont de plus en plus démotivés lorsqu'il n'y a pas d'amélioration de la qualité des données.

Nous proposons d'utiliser l'analyse topologique des données extraites pour une zone géographique pour assurer le suivi de la qualité des données et avoir la possibilité de signaler des objets pour révision. Les outils de Qualité de données tels Osmose, KeepRight, OSM Inspector et le validateur JOSM fournissent déjà beaucoup d'informations de ce type. Mais nous avons besoin d'une certaine flexibilité pour obtenir rapidement les données de la zone et assurer un meilleur suivi.  L'accès à ces outils via des API pourrait également permettre éventuellement d'extraire de telles données pour des zones géographiques données. 

*Figure 2 Polygones non valides - Repérage* ![Figure 2 Polygones non valides - Repérage](img/po-Topologie-FB-Overpass-Kisenso-Polygones-non-valides.png)

Dans notre projet, les statistiques produites sur les objets marqués pour un examen plus approfondi permettent de mesurer l'ampleur du phénomène et faire des comparaisons avec des projets cartographiques dans des zones similaires. Cet outil fournit également un fichier contenant les bâtiments et autres objets à valider/corriger à l'aide d'éditeurs tels JOSM. Dans ce cas, le greffon ToDO permet de réviser un à un les objets contenus dans le fichier, valider et corriger si nécessaire. L'identification des bâtiments de forme irrégulière présentait une première mesure. Les polygones de bâtiments invalides (voir figure 1) ont aussi été identifiés. 

Dans ce deuxième article sur l'analyse topologique, nous ajoutons le repérage des objets superposés (ie. bâtiments, routes, cours d'eau, polygones occupation du sol, etc) à la liste des objets signalés pour une évaluation plus poussée.

Le démarrage récemment du projet Open Cities Africa avec 12 villes participantes offre une opportunité intéressante pour comparer la réalité de différentes territoires. La comparaison ci-dessous présente les données de ces 12 villes et offre la possibilité de comparer la base de données de OSM à travers l'Afrique.  La comparaison des données Qualité de ces villes est intéressante pour voir comment de tels outils peuventt aider à améliorer la base de données OSM. Nous proposons une approche analytique qui, nous l'espérons, contribuera aux discussions sur la qualité des données et le développement d'OSM dans diverses localités. 
 
 
## Analyse Qualité - Superposition des Bâtiments et autres objets
Des bâtiments, routes et autres objets tracés avec imprécision ou encore des erreurs lors de l'édition déplaçant un point auront souvent pour effet de superposer des polgyones (bâtiments, occupation du sol, cours d'eau, limites territoriales, etc) et des lignes tels routes et chemins de fer.  La figure 3 illustre ces superpositions, montrant des bâtiments et routes qui se superposent. Divers projets au cours des dernières années, souvent dans des contexte de crises ou désastres naturels ont cartographié en partie les villes faisant partie de cette liste. Malgré les validations, de nombreuses erreurs ne sont pas encore corrigées. Les outils Qualité listent ces erreurs mais il est difficile d'avoir une vue d'ensemble et de mesurer l'importance de ces signalements.

*Figure3 Immeubles et routes superposées*
![Figure 3](img/po-Topologie-XB-XO-Overpass-Kisenso-Vixualise-Immeubles-et-Routes-se-superposant.png)


Notre outil d'analyse topologique permet d'identifier chaque immeuble ou autre objet tel route, cours d'eau etc. qui superposé à un autre.  Une statistique est produite et une liste de ID OSM est aussi disponible. Une requête Overpass utilisant cette liste (voir figure 4) permet de produire des fichiers de données OSM contenant les objets concernés. Cela permet ensuite d'importer le fichier dans JOSM pour analyse et correction. Les visualisations cartographiques à partir des fichiers GeoJSON, présentés ci-dessous pour chaque ville, offrent une vue d'ensemble des objets marqués pour analyse. Il est aussi possible de se déplacer dans la carte pour examiner plus en détail.

*Figure 4 Requête Overpass - Id signalés Analyse Qualité*
![Figure 4](img/Overpass_Turbo_Kisenso_Immeubles_formes_irreg.png)



## «State of the Map» Comparaison, différentes villes du projet Open Cities Africa
Pour fin de comparaison, nous avons sélectionné des villes participantes au projet Open Cities Africa et sélectionné des tâches à l'aide du gestionnaire de tâches OSM lorsque disponible sinon une zone correspondant au projet.  La zone sélectionnée peut couvrir un territoire plus vaste que le projet Open Cities mais représente néanmoins une bonne indication de l'État de la carte, de la qualité de la donnée OSM dans la zone.  Chacune zone à son histoire, réponse rapide à un désastre ou autre, qualité d'imagerie très variable, organisation de mapathons avec des débutants, etc. L'architecture d'une ville à l'autre peut aussi varier et dans certaines villes on peut identifier un nombre plus élevé de bâtiments qui ont effectivement une forme irrégulière.  Par exemple, lors de l'épidémie d'Ebola à, Monrovia, la ville a dû être cartographiée rapidement pour aider les équipes humanitaires, et cela malgré la mauvaise qualité de l'imagerie disponible. Les images manquant encore de précision, les projets récente n'ont pas réussi à améliorer sensiblement la qualité.  À Ngaoundere, suite à un projet de cartographie récent, beaucoup de doublons et d'immeubles superposés ont été ajoutés. Des outils d'analyse topologique permettent de le détecter rapidement et apporter les corrections nécessaires.

Le tableau 1 présente une comparaison des résultats obtenus avec l'analyse topologique. Les sections suivantes pour chaque commune / ville, fournissent des liens vers les cartes vectorielles contenant les signalements. Ces signalements sont regroupés selon
- Immeubles - Géométrie irrégulière et polygones non valides
- Superposition d'immeubles (avec autres immeubles ou autres objets)

En moyenne, on observe un taux de signalement de 27,8% des immeubles avec géométrie irrégulière et 5,6% de superpositions  en proportion du total des immeubles. Au total, il y a 33,4% de signalements (objets à valider) en proportion des immeubles. Mais plutôt que la moyenne, ce sont les grands écarts dans les taux qui sont à retenir.  Comment expliquer ces écarts allant  De Kisenso  avec un taux de signalements de 3,6% à Victoria avec un taux de 74,8%.  Les erreurs topologiques (Superpositions + Polygones invalides ne représentent pas la part la plus importante des signalements. Par contre, on doit s'interroger sur le taux élevé d'immeubles avec formes irrégulières dans certaines zones.  Les architectures de forme irrégulière peuvent-elles varier autant? Peut-on expliquer les écarts par des architectures différentes dans les zones d'urbanisme informel?  Et pour certains villes, divers mapathons organisés à distance peuvent avoir augmenté sensiblement les taux de signalement. 

Ces cartes représentent la situation actuelle pour chacune des villes (ie The State of the Map). Le manque de qualité à certains endroits représente un défi supplémentaire et il faudra sûrement réfléchir à comment amélioer la base OSM pour la zone toute en réussissant à faire progresser le projet.

*Tableau 1 : Comparaison, Signalements Analyse topologique en % des bâtiments de la zone, 6 projets Open Cities Africa*

|	Localité	|	Bâtiments	|	Avertissement Géométrie Irreg	|	%	|	Erreurs Superpositions +Polygone non valide	|	%	|	Total Signalements % |
|	:------------------------------------------	|	--------:	|	------:	|	--------:	|	------:	|	------:	|	------:	|
|	Kisenso 2018-08-16	|	20089	|	324	|	1.6%	|	391	|	1.9%	|	3.6%	|
|	Kampala 2018-04-07	|	11327	|	1001	|	8.8%	|	343	|	3.0%	|	11.9%	|
|	Ngaoundere 2018-08-06	|	73609	|	9998	|	13.6%	|	4439	|	6.0%	|	19.6%	|
|	Monrovia 2018-08-25	|	4107	|	751	|	18.3%	|	441	|	10.7%	|	29.0%	|
|	Accra 2018-08-25	|	7699	|	1396	|	18.1%	|	13	|	0.2%	|	18.3%	|
|	Dar Es Sallaam 2018-08-25	|	2579	|	334	|	13.0%	|	80	|	3.1%	|	16.1%	|
|	Saint-Louis 2018-08-27	|	25970	|	6548	|	25.2%	|	3814	|	14.7%	|	39.9%	|
|	Victoria 2018-08-27	|	37299	|	27015	|	72.4%	|	898	|	2.4%	|	74.8%	|
|	Antananarivo 2018-08-27	|	10282	|	5932	|	57.7%	|	330	|	3.2%	|	60.9%	|
|	Pointe-Noire 2018-08-27	|	765	|	265	|	34.6%	|	186	|	24.3%	|	59.0%	|
|	Brazzaville 2018-08-27	|	1239	|	208	|	16.8%	|	30	|	2.4%	|	19.2%	|
|	Stone Town 2018-08-27	|	2392	|	1022	|	42.7%	|	178	|	7.4%	|	50.2%	|
|	Total projets analysés	|	197357	|	54794	|	27.8%	|	11143	|	5.6%	|	33.4%	|

Pour chaque commune / ville, nous retrouvons les hyperliens vers les cartes vectorielles des objets signalés pour évaluation. Nous retrouvons également une image illustrant cette zone géographique.  Le titre indique à quelle date on été extraites les données vectorielles pour une commune / ville.  Lorsque nous visualisons la carte GeoJSON, les données vectorielles apparaissent en ble et la carte de fond représente les données OSM actuelles. Par exemple, si une route a été modifiée dans la base OSM depuis l'extraction pour analyse pour éviter de la superposer sur un immeuble, vous observerez une différence entre la carte vectorielle et la carte de fond.


## Kisenso, Kinshasa 2018-08-16, (polygone limites de Kisenso)
* [Kisenso, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-kisenso-2018-08-16.geojson)
* [Kisenso, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-kisenso-2018-08-16.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Kisenso](img/po-geojsjon-Kisenso-overlap.png)


## Kampala, 2018-04-07, Task 4360, hotosm

* [Kampala, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-OC_Kampala_hotosm_4360_2018_04_07.geojson) 
* [Kampala, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-OC_Kampala_hotosm_4360_2018_04_07.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Kampala](img/po-geojsjon-Kampala-Form.png)


## Ngaoundere, 2018-08-06, Task 4800, hotosm

* [Ngaoundere, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-OC_Ngaoundere_hotosm_4800_2018_08_06.geojson) 
* [Ngaoundere, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-OC_Ngaoundere_hotosm_4800_2018_08_06.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Ngaoundere](img/po-geojsjon-Ngaoundere-Overlaps.png)


## Monrovia, 2018-08-25, Task 4366, hotosm

* [Monrovia, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-OC_monrovia_hotosm_4866_2018_08_25.geojson) 
* [Monrovia, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-oc_monrovia_hotosm_4866_2018_08_25.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Monrovia](img/po-geojsjon-Monrovia-Form.png)


## Accra, 2018-08-25, Task 4969, hotosm

* [Accra, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-OC_Accra_hotosm_4969_2018_08_25.geojson)
* [Accra, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-OC_Accra_hotosm_4969_2018_08_25.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Accra](img/po-geojsjon-Accra-Form.png)


## Dar Es Salaam, 2018-08-25, Task 5012, hotosm

* [Dar Es Salaam, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-OC_DarEsSalaam_hotosm_5012.geojson)
* [Dar Es Salaam, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-OC_DarEsSalaam_hotosm_5012.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Dar Es Salaam](img/po-geojsjon-DarEsSalaam-Form.png)


## Saint-Louis, 2018-08-27

* [Saint-Louis, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-oc_saint_louis_2018_08_27.geojson)
* [Saint-Louis, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-oc_saint_louis_2018_08_27.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Saint-Louis](img/po-geojson-Saint-Louis-Overlaps.png)


## Victoria, 2018-08-27

* [Victoria, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-form-oc_victoria_2018_08_27.geojson.zip)
* [Victoria, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-oc_victoria_2018_08_27.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Victoria](img/po-geojson-Victoria-Overlaps.png)


## Antananarivo 2018-08-27

* [Antananarivo, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-form-oc_antananarivo_2018_08_27.geojson)
* [Antananarivo, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-oc_antananarivo_2018_08_27.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Antananarivo](img/po-geojsjon-Antanarivo-Irregular-Forms.png)


## Pointe-Noire 2018-08-27

* [Pointe-Noire, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-forms-oc_pointe_noire_2018_08_27.geojson)
* [Pointe-Noire, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-oc_pointe_noire_2018_08_27.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Pointe-Noire](img/po-geojsjon-Pointe-Noire-Overlaps.png)


## Brazzaville 2018-08-27

* [Brazzaville, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-form-oc_brazzaville_2018_08_27.geojson)
* [Brazzaville, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-oc_brazzaville_2018_08_27.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Brazzaville](img/po-geojsjon-Brazzaville-Irregular-Forms.png)


## Stone Town 2018-08-27

* [Stone Town, Immeubles avec géométrie irrégulière](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-irregular-form-oc_stone_town_2018_08_27.geojson)
* [Stone Town, Superpositions Immeubles/Autres objets](https://github.com/opendatalabrdc/Documentation/blob/master/topology/topology-overlap-oc_stone_town_2018_08_27.geojson)

Source: OpenDataLabRDC [Ⓒ OpenStreetMap, OdBL](https://www.openstreetmap.org/copyright)
![Stone Town](img/po-geojsjon-Stone-Town-Irregular-Forms.png)

</br></br>

*Pierre Béland*
