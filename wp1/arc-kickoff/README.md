
# Présentation de l'application Arc

- [Objectif de l'application](#objectif-de-lapplication)
- [Flux d’information](#flux-dinformation)
- [Acteurs](#acteurs)
- [Documentation utile](#documentation-utile)

## Objectif de l'application

Le module d’accueil-réception-mise au format constitue la première étape du traitement des données de la future chaîne applicative Siera 2. Ce module propose une solution d’accueil des données administratives stable même lors des changements de norme de la déclaration administrative, d’effectuer un certain nombre de contrôles afin de vérifier la qualité des données, et d’assurer la transformation de ces données dans un schéma exploitable par la suite par les applications clientes de traitements statistiques.

Ce module permet de charger et d’exploiter n’importe quel type de donnée administrative. Le paramétrage du chargement (fichier plat, fichier XML, csv), la reconnaissance des normes associées à des déclarations, les contrôles appliqués aux
données et la transformation des données administratives en données statistiques (le « mapping » rennomé en « format ») peuvent être modifiés et améliorés au cours du temps par l’interactif, soit par le responsable informatique de l’application (RIA), soit par l’administrateur d’application (AA) lui même, qui disposent alors d’un cadre de travail pour faire évoluer les paramètres sans toucher au coeur de l’application.

Compte tenu des possibilités de modification des traitements directement par  l’interactif et des risques qu’une mauvaise spécification pourrait avoir sur la production et étant donné les volumes de données très importants à traiter, les acteurs qui l’utilisent disposent d’espaces de tests similaires à l’espace de production mais distincts, afin de tester, qualifier les nouvelles règles spécifiées et mesurer leur impact sur les données chargées avant leur mise en production.

Les principaux objectifs du module fonctionnel sont les suivants :
  
* accueillir et charger en base des données administratives, quel que soit leur format ou leur destination dans le futur Siera ;
* identifier la source des données chargées (norme et version de la déclaration,   validité de la déclaration) et réaliser des contrôles afin de vérifier l’adéquation entre   les données transmises et les variables et modalités attendues ;
* transformer les données administratives contrôlées en données statistiques, c’est-à dire  réaliser des transformations des données de la source vers un ensemble de  variables statistiques stables ;
* permettre à l’administrateur d’application et au RIA de modifier, compléter ou   supprimer les paramètres transmis à la chaîne de production, de la réception des   fichiers jusqu’à leur mise à disposition des applications clientes ;
* alimenter les applications clientes de traitements statistiques avec les données   statistiques élémentaires, sur le périmètre fonctionnel qui leur est dévolu ;
* fournir un environnement sécurisé permettant de tester les modifications apportées  aux paramètres avant leur mise en production, dans un environnement équivalent à  celui de production ;
* permettre aux utilisateurs de l’application de consulter, modifier et charger/ décharger des fichiers de données ;
  
Les données administratives seront conservées sur une durée limitée : la durée de  conservation des données administratives transmises par les partenaires sera d’un an à  compter de leur réception, et de trois ans pour les données « normées » (ie après  chargement en base et identification de la norme et de sa version). La conservation des  données administratives transmises par les partenaires est nécessaire afin de corriger et  recharger des fichiers qui s’avèreraient erronés. La conservation des données « normées »  est nécessaire afin de pouvoir mettre ponctuellement à disposition des unités métier, les  variables chargées mais non-exploitées par les applications clientes, afin de les étudier et le  cas échéant, d’améliorer les traitements statistiques.

Enfin en tant que module d’infrastructure, il permettra de gérer les nomenclatures et tables de passage métiers utiles aux traitements dans les applications clientes. Ces métadonnées seront transmises aux processus clients en même temps que les données elles-mêmes.
  
## Flux d’information

**En entrée**, le module est alimenté par deux types de données :
  
* les données des déclarations transmises par les partenaires et déposées automatiquement sur des espaces de réception dédiés à un fournisseur et un type de donnée ;
* les données corrigées ou créées par les utilisateurs, déposées via l’interactif dans les espaces de réception pertinents.

Dans un premier temps, deux espaces de chargement seront mis en place : un espace pour les données DSN au format XML transmises par la Cnav ; un espace pour les données DADS issues du Frontal N4DS. Les deux espaces de réception de l’application pourront être complétés par l’équipe projet ou le futur RIA de l’application par d’autres espaces si des fichiers de format différent devaient être amenés à être utilisés.
  
  
**En sortie**, deux types de données seront générés :
  
* les données statistiques élémentaires, c’est-à-dire le résultat de la transformation des variables déclarées en variables statistiques (recodifications, filtrage, re-calculs ad hoc). Ces données élémentaires, dites « mappées », sont stockées dans des bases de données, et pourront être transférées aux processus clients via un webservice. Dès lors qu’elles auront été récupérées par le processus client, elles seront transférées dans les espaces de conservation (pour une durée d’un an) et supprimées des bases de données en production ;
* les données administratives chargées à l’état « normé », mises à disposition des équipes métier sous AUS en vue d’exploitations ponctuelles, pour une durée de trois ans.

## Acteurs

En dehors des acteurs techniques qui mettent à disposition les données transmises par les   partenaires (SEF), ou ceux qui récupèrent les données pour leurs traitements (applications   clientes, dont le module fonctionnel « traitements élémentaires »), seuls l’administrateur   d’application (sous la responsabilité de la division EFA) et le RIA auront accès à l’applicatif et   ses fonctionnalités. Les deux acteurs disposent tous deux de toutes les fonctionnalités de  l’interactif. Un mode de travail collaboratif devra être mis en place entre ces deux acteurs.
  
# Traitements

Le processus cible du module fonctionnel est subdivisé en deux sous-processus.

**Le sous-processus « charger les données »** prend en charge les traitements depuis la réception des données administratives jusqu’à leur mise au format statistique. Ce sousprocessus se subdivise lui-même en cinq cas d’utilisation principaux :
  
* l'identitifation du type de donnée. Cela permet de déterminer la norme du fichier, et le format de fichier associer pour savoir quel chargeur utiliser par la suite ;
* le chargement en base des données reçues à l’aide du chargeur adéquat ;
* la phase de transformation, qui consiste à mettre en forme de table le fichier si cela est nécessaire ;
* la phase de contrôle de données. Les contrôles sont spécifiques à un type de déclaration et une version de norme. Ils peuvent faire l’objet de versions successives pour une même version de la norme selon les validités de déclarations. Il existe trois types de contrôles : les contrôles de cardinalité entre variables, les contrôles de format et les contrôles de condition sur la valeur des variables. Si une règle de contrôle n’est pas satisfaite, la ligne de déclaration est exclue mais pas le reste du fichier. Lorsqu’un fichier comporte un nombre significatif de lignes de déclarations en anomalie, l’ensemble du fichier est exclu de la suite du traitement et devra faire l’objet d’une correction manuelle ;
* la phase de filtrage ou d’exclusion. À cette étape, une partie des données peuvent être exclues si une partie des variables ou du champ déclaré ne doit pas être transmis aux applications clientes.
* la phase de mise au format statistique. Les données non-exclues sont transférées, parfois après transformations, dans des tables métier qui correspondent aux objets qui seront transférées aux applications clientes.
  
Chacune de ces phases fait l’objet d’un paramétrage par l’utilisateur de l’application : la façon  de détecter la version de la norme et la validité, les jeux de contrôles, les règles d’exclusion  ou encore les règles de « mapping » sont autant de paramètres qui sont spécifiés via  l’interactif par les utilisateurs.

## Documentation utile

- [Diagramme de base de données](Arc-BDD.pdf)
- [Docuementation sur les services de ARC](Documentation-service-ARC.pdf)
- [Dossier d'architecture de 2014](dossier-architecture-SiaspONP-old.pdf)
- [Etude préalable](Dossier-détude-préalable-du-projet-Pirénés-lot1.pdf)
- [Dossier de modélisation](Siasp-ONP-Dossier-modelisation-vFinale.pdf)