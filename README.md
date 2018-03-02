# SpeedCooking: Visualisation for Cooking
By [@456lumen](https://github.com/456lumen), [@Hugues-Moreau](https://github.com/Hugues-Moreau) and [@tblondelle](https://github.com/tblondelle) - École Centrale de Lyon - 2018

<table border="0">
  <tr>
    <td>
      <a href="https://tblondelle.github.io/DataVisualisationProject/" title="See it now!"><img src="/img/capture d'ecran visualisation.png" style="width: 200px;"></a>
    </td>
  </tr>
  <tr>
    <td align="center" bgcolor="EFEFEF">
    SpeedCooking visualisation
    </td>
  </tr>
</table>


### 1. Cooking with a list-style recipe: improving the representation
Whoever having never made any mistake in the kitchen ever, please show off proudly! Cooking combines *Artistry* and *Punctiliousness*: it is the Science of *Sequences* and *Details*. But most of us simply follow the recipe to the letter, carefully written by Old Granny. And despite all the attention, patatras! the disaster has come: the yeast is forgotten!

But was this recipe as carefully written as it was thought to be? Has anyone been as attentive as The Grand Paul Bocuse would have ordered?

While the traditional numbered-list recipe is used by 58% of the population to prepare food[<sup>1</sup>](https://www.reportlinker.com/insight/americans-cooking-habits.html), should not some attention be paid to it? It seems indeed rather difficult for a list of immutable linearity to handle complex and lengthy processes, to inform the cook of the major parts of a recipe, to represent simultaneous steps or to help organizing things in space and time.

Our [project](https://tblondelle.github.io/DataVisualisationProject/), under the auspices of the Ecole Centrale de Lyon in partnership with the Institute Paul Bocuse, aims at nothing less than **reimagining the cooking recipe as a new structured, explicit and mistake-impervious way**. The solution we developped is notably based on GitHub progress graphs and relies on the D3.js visualization technology.


### 2. State of the art

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


### 3. Solution

The idea we had is to visualise recipes like a tree. Several sub-recipes are represented as branches and then merge to create the final product. We had the idea to use this representation, similar to github's networks graphs.

<table>
  <tr>
    <td>
      <img src="/img/structure github.JPG" style="width: 200px;">
    </td>
  </tr>
  <tr>
    <td>
     Screenshot of the network graph of this github project. In a cooking recepie, there are no forks, only merges and commits.
    </td>
  </tr>
</table>



### 4. Choice of design
We wanted originally to represent time on the x axis. However, some actions requires more time (example : waiting) than others. We could have chosen a non linear time scale in order to split the different steps more evenly a throughout the screen, but the same problem would have occurred in the case of parrallelized tasks sharing the same x axis. In order to keep the visualisation readable, we used a sequential representation.  Space is represented on the y axis : each line represent a location in the kitchen : the oven, the cooking plate etc.


### 5. Technical choices
Translating one numbered-list recipe into a complete and finalized graph as shown in this project is no easy thing. In fact, it is all about understanding the recipe structure, inferring workplace and logic chaining. Building an algorithm fed with a simple list and providing the end result is thus ruled out. (At least, for this project). We have then chosen to divide it in two separate task.

The first one is about preprocessing the recipe, formatting it in a way that an simple d3 program can understand. This task is described more thoroughly in section 6.

The second task is about building the d3 program that can grab the preprocessed recipe and display it quickly and unambiguously. The details about the d3 program in charge of this can be found in the `index.html` file. Once this is done, we have added a simple web interface with the Bootstrap v4 library.



### 6. Data

Our data come from cooking websites like http://www.marmiton.org/ or http://www.750g.com/. Chosen recipe are formatted in a the file [recettes.json](https://github.com/tblondelle/DataVisualisationProject/blob/master/recettes.json) . Each recipe contains a list of steps. Each step has a number as indentifier, a location (where should it be displayed), a list of parents a list of children. Each step also a type (determines what icon will be used), a short description (always shown) and a long description (shown on mouseover).

### 7. Description of the visualisation

At the top of the screen is a bar with a menu allowing the user to choose the recipe to display. Upon selecting a recipe, the tree will be created with an animation that make the steps of the recipe appear in the order they should be executed.
Each step has a defined place of execution (in the oven, in a pan, etc.), defining its position on the y axis. Dull-colored zebra stripes make the distinction between different places easier.  The steps also have a type (adding aan ingredient, waiting, generic preparation, etc.) represented by a SVG icon on the tree. A short description is provided under each icon, but as some steps require explanations which would have been too long for display, a more detailed description can be found either by pointing the mouse over an icon or by selecting the chosen step using the arrow keys. A selected icon appears slightly bigger than the others. The dependency between the different steps is represented by the links between them. The overall graph created this way is a tree, which leaves are the leftmost nodes, the steps that must be completed first; and the rightmost node is the root, a 'finished' icon.



### 8. Results

This type a representation has several assets a classic, linear recipe lacks:
- the structure of the recipe can be understood easily: How many sub-preparations (paste, icing, ...) are there ? Is the recipe complex ? How much room is required to prepare it ?
- if several cooks are present, the work can easily be divided between each of them.

However, this step-wise representation does not show the time required by each step : some may be fast (peeling or cutting a fruit, others may be longer (cooking a compote).

### 9. Resources
- [Syllabus MOS5.5 2018 (Romain Vuillemot)](https://github.com/LyonDataViz/MOS5.5-Dataviz)
- M. Monroe. Classic Techniques in New Domains: An Alternative Recipe, Eurographics Conference on Visualization (EuroVis) 2016 [[link]](https://diglib.eg.org/bitstream/handle/10.2312/eurovisshort20161172/119-123.pdf?sequence=1&isAllowed=y)
