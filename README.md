# SpeedCooking: Visualisation for Cooking


### Context 
Whoever having never made any mistake in the kitchen ever, please show off proudly! Cooking combines *Artistry* and *Punctiliousness*: it is the Science of *Sequences* and *Details*. But most of us simply follow the recipe to the letter, carefully written by Old Granny. And despite all the attention, patatras! the disaster has come: the yeast is forgotten!

But was this recipe as carefully written as it was thought to be? Has anyone been as attentive as The Grand Paul Bocuse would have ordered?

While the traditional numbered-list recipe is used by 58% of the population to prepare food[<sup>1</sup>](https://www.reportlinker.com/insight/americans-cooking-habits.html), should not some attention be paid to it? It seems indeed rather difficult to handle the representation of complex, lengthy processes, comprising several major steps in the form of a list of immutable linearity.

Our [project](https://tblondelle.github.io/DataVisualisationProject/), under the auspices of the Ecole Centrale de Lyon in partnership with the Institute Paul Bocuse, aims at nothing less than **reimagining the cooking recipe in a more structured, explicit and mistake-impervious way**. The solution we developped (@456lumen, @Hugues-Moreau and @tblondelle) is notably based on GitHub progress graphs and relies on the D3.js visualization technology.

### Problem
Recipes are often represented as a succession of several steps in a cooking book. In the case of complex cooking recipes, this representation doesn't show which steps can be performed simultaneously. This representation also doesn't show where must be located the preparation. In order to prepare a recipe efficiently, things must be organised in space and time. We are looking for an alternative way to represent recipes that shows clearly simultaneous tasks and where does they happen as a tool to simplify organisation.

### State of the art

We can find recepies in cooking books or on specialised websites. The way recipes are represented on websites or in cooking books is similar : 

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


The possibilities given by interactivity of the internet are not used in the visualisation : a recipe from a website can be printed without making any difference. 


### Solution

The idea we had is to visualise recipes like a tree. Several sub-recipes are represented as branches and then merge to create the final product. We had the idea to use this representation, similar to github's networks graphs. 

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



### Choice of design
We wanted originally to represent time on the x axis. However, some actions requires more time (example : waiting) than others. We could have chosen a non linear time scale in order to split the different steps more evenly a throughout the screen, but the same problem would have occurred in the case of parrallelized tasks sharing the same x axis. In order to keep the visualisation readable, we used a sequential representation.  Space is represented on the y axis : each line represent a location in the kitchen : the oven, the cooking plate etc.


### Technical choices
Translating one numbered-list recipe into a complete and finalized graph as shown in this project is no easy thing. In fact, it is all about understanding the recipe structure, inferring workplace and logic chaining. Building an algorithm fed with a simple list and providing the end result is thus ruled out. (At least, for this project). We have then chosen to divide it in two separate task. 

The first one is about preprocessing the recipe, formatting it in a way that an simple d3 program can understand. This task is described more thoroughly in section XX. 

The second task is about building the d3 program that can grab the preprocessed recipe and display it quickly and unambiguously. The details about the d3 program in charge of this can be found in the `index.html` file. Once this is done, we have added a simple web interface with the Bootstrap v4 library.



### Data

Our data come from cooking websites like http://www.marmiton.org/ or http://www.750g.com/. Chosen recipe are formatted in a the file recettes.json. Each recipe contains a list of steps. Each step has a number as indentifier, a location (where should it be displayed), a list of parents a list of children. Each step also a type (determines what icon will be used), a short description (always shown) and a long description (shown on mouseover). 


### Description of the visualisation 
Idees ques j'ai eu mais qui vont en fait plus dans cette partie : 
* Recette en plein ecran car on ne choisit qu'une seule recette
* Pour ne pas surcharger l'ecran, on ne voit qu'un resumé de chaque étape
* Chaque etape a une icone pour etre visuelle
*   ajouter les icones
* alternance de couleurs 

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


### Results 


### Resources
- [Syllabus MOS5.5 2018 (Romain Vuillemot)](https://github.com/LyonDataViz/MOS5.5-Dataviz)
- M. Monroe. Classic Techniques in New Domains: An Alternative Recipe, Eurographics Conference on Visualization (EuroVis) 2016 [[link]](https://diglib.eg.org/bitstream/handle/10.2312/eurovisshort20161172/119-123.pdf?sequence=1&isAllowed=y)
