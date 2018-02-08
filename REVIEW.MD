# Review du projet ParisLumiere

## Objectifs du projet
Le projet Paris lumière, disponible à l'adresse https://github.com/alexandrospopov/parisLumiere, permet de visualiser des lieux de tournage de films effectués à Paris. 
La base de donnée utilisée est une liste de tournages effectués en 2016 à Paris.
Pour chaque tournage sont disponibles les éléments suivants :
[Titre, Realisateur, Adresse, Organisme Demandeur, Type de Tournage, Arrondissement, Date début, Date fin, [latitude longitude]] 

L'objectif ambitieux est de pouvoir parcourir cette base de donnée temporellement, spacialement et qualitativement. 

## Choix de la visualisation
La visualisation proposée consiste en trois zones : 
- Une zone où l'on choisit les critères des tournages que l'on veut représenter dans les deux prochaines zones. Cela fonctionne sous forme de filtre
- Une carte de paris où chaque tournage correspondant au filtre est représenté par un point. Lorsque l'on survole ce point, les informations s'affichent. 
- Un histogramme représentant le nombre de tournages correspondants au filtre par mois 

## Remarques
- La base de données est fournie et complète, c'est un très bon point de départ
- Il y a beaucoup de critères pour chaque tournage. Il n'est peut etre pas utile de tous les implémenter en fonction du message que vous voulez faire passer. Je pense nottament à l'arrondissement et l'adresse qui font double emploi avec la latitude et longitude. 
- Regrouper les tournages par mois (et non par jour) est une bonne idée car cela permet d'avoir un histograme qui ressemble à quelque chose. Cependant, plutot que de compter le nombre de tournages par mois, (prenez vous la date de début? de fin? Si un tournage s'étale sur deux mois, dans lequel compte il?), il serait plus représentatif de compter le nombre de jours de tournages cumulés par mois.
- Dans le cas où il y aurait un seul film de sélectionné, l'idée du Gantt sur la feuille 2 a l'avantage de montrer les dates de début et de fin de tournage, et permet de visualiser la manière dont se sont deplacées les equipes. Une idée pourrait être, lorqu'un seul film est selectionné, de remplacer l'histograme (utile pour donner une idée globale, lorsque l'on compare par exemple plusieurs films) par le Gantt, qui permet de mieux visualiser ce qu'il se passe au cours du tournage d'un unique film.
- L'utilisation d'une échelle de couleur n'est pas adaptée pour représenter une échelle temporelle, ce serait illisible. D'autant que vous prevoyez déjà de représenter l'échelle temporelle sur la carte en mettant en surbrillance les lieux de tournage quand on passe la souris sur une barre de l'histogramme. 
