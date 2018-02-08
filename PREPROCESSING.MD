# Traitement des métadonnées

La plupart des informations (nom de la recette, ingrédients, temps de préparation et de cuisson, description complète des étapes) proviennent directement du site sur lequel la recette a été trouvée.
Le traitement des données que nous avons effectué se résume à :
- mettre la recette sous la forme d'un .JSON
- ajouter un résumé de la description lorsque celle-ci est trop longue, pour ne pas encombrer l'écran.
- lister les étapes, s'assurer qu'elles aient bien le même niveau de granularité (en fusionnant deux étapes courtes ou en séparant une étape en plusieurs)
- ajouter les dépendances (filiations dans l'arbre) entre étapes
- ajouter un lieu, pour garder une cohérence visuelle (il faut que deux étapes qui concernent la même préparétion (pâte, garniture, ...) soient au même niveau)
