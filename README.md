# SpeedCooking: Data Visualisation for cooking recipes

## Project

[in progress]

This project aims to represent an alternative way to understand recipes when cooking. The classic succession of steps, despite its indisputable simplicity, may not be the ultimate tool to master complex recipes processes.

Our [project](https://tblondelle.github.io/DataVisualisationProject/) solves this problem with a clear visualisation of the required tasks. It thus allows a quick parallelisation of the work.


## Team members
@456lumen, @Hugues-Moreau, @tblondelle


## Context 


## Problem
Recipes are often represented as a succession of several steps in a cooking book. In the case of complex cooking recipes, this representation doesn't show which steps can be performed simultaneously. This representation also doesn't show where must be located the preparation. In order to prepare a recipe efficiently, things must be organised in space and time. We are looking for an alternative way to represent recipes that shows clearly simultaneous tasks and where does they happen as a tool to simplify organisation.

## State of the art

We can find recepies in cooking books or on specialised websites. The way recepies are represented on websites or in cooking books is similar : 

* List of ingredients
* List of tools
* Number of portions
* Other informations
* List of different steps to perform

<table border="0">
  <tr>
    <td>
      <img src="/img/recette_brookie_marmiton.JPG" style="width: 200px;">
    </td>
  </tr>
  <tr>
    <td align="center" bgcolor="EFEFEF">
     Screenshot of the website www.marmiton.org . We can see a list of tasks to perform that doesn't let us see that this recepie can be parralelized. 
    </td>
  </tr>
</table>


The possibilities given by interactivity of the internet are not used in the visualisation : a recepie from a website can be printed without making any difference. 


## Solution

The idea we had is to visualise recepies like a tree. Several sub-recepies are represented as branches and then merge to create the final product. We had the idea to use this representation, similar to github's networks graphs. 

<table border="0">
  <tr>
    <td>
      <img src="/img/structure github.JPG" style="width: 200px;">
    </td>
  </tr>
  <tr>
    <td align="center" bgcolor="EFEFEF">
     Screenshot of the network graph of this github project. In a cooking recepie, there are no forks, only merges and commits.
    </td>
  </tr>
</table>



## Choice of design
We wanted originally to represent time on the x axis. However, some actions requires more time (example : waiting) than others. We could have chosen a non linear time scale in order to split the different steps more evenly a throughout the screen, but the same problem would have occurred in the case of parrallelized tasks sharing the same x axis. In order to keep the visualisation readable, we used a sequential representation.  Space is represented on the y axis : each line represent a location in the kitchen : the oven, the cooking plate etc.


## Technical choices

## Data
# Provenance des données

 Les données proviennent de sites de cuisine, comme http://www.marmiton.org/, ou http://www.750g.com/. Chacune d'entre elles est entrée à la main dans le fichier recettes.json, qui contiendra toutes les recettes. Nous nous sommes avant tout souciés de nous faciliter le travail une fois que nous aurons à utiliser ces données : comme nous voulons représenter les différentes suites d'étapes sous la forme d'arbres, nous avons donné, pour chaque étape, une liste des étapes requises, ainsi qu'un lieu (l'idée étant d'afficher une suites d'étapes similaires à la même hauteur). Toutes les autres informations sont directement disponibles sur les sites en question.
Au vu de la faible quantité de données à traiter, nous ne nous sommes pas souciés des éventuelles redondances que nous pourrions introduire.

Recettes : liste d'objets JSON, de la forme :

			nom : string,
	    ingrédients : list of strings, (un ingrédient n'est représenté que par une string, ex "4 oeufs")
			tps_cuisson : int, (en minutes)
			tps_preparation : int, (en minutes)
			nombre_personnes: int
			source: string (à priori, nous n'en aurons pas besoin, mais nous ne pouvons pas en être sûrs)
			(éventuellement, autres métadonnées)
			étapes : liste d'objets JSON, de la forme :

				identifiant : int    (l'identifiant est égal à la position dans la liste)
				descriprion_courte : string  (à afficher sur l'écran)
				descriprion_longue : string  (à afficher sur mouseOver)
				enfants : list of ints (les indices des enfants)
        parent : int
        type : "ajout"|"merge"|"decoupe"|"cuisson_plaque"|"cuisson_four"|"patienter"|"autre"
				lieu : string (ex #: 'four','saladier_2', ...)

Remarque : Il n'y a pas d'entiers à proprement parler en JSON,  "int" signifie seulement que l'on pourra directement convertir la donnée en entier depuis le Javascript.


## Description of the visualisation 
Idees ques j'ai eu mais qui vont en fait plus dans cette partie : 
Recette en plein ecran car on ne choisit qu'une seule recette
Pour ne pas surcharger l'ecran, on ne voit qu'un resumé de chaque étape
Chaque etape a une icone pour etre visuelle
  ajouter les icones
alternance de couleurs 

<table border="0">
  <tr>
    <td>
      <img src="/img/capture d'ecran visualisation.JPG" style="width: 200px;">
    </td>
  </tr>
  <tr>
    <td align="center" bgcolor="EFEFEF">
    klsdfklqsdgfq
    </td>
  </tr>
</table>


## Results 

## Resources
- [Syllabus MOS5.5 2018 (Romain Vuillemot)](https://github.com/LyonDataViz/MOS5.5-Dataviz)
- M. Monroe. Classic Techniques in New Domains: An Alternative Recipe, Eurographics Conference on Visualization (EuroVis) 2016 [[link]](https://diglib.eg.org/bitstream/handle/10.2312/eurovisshort20161172/119-123.pdf?sequence=1&isAllowed=y)
