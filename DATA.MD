# Provenance des données

Les données proviennent de sites de cuisine, comme http://www.marmiton.org/, ou http://www.750g.com/. Chacune d'entre elles est entrée à la main dans le fichier recettes.json, qui contiendra toutes les recettes. Nous nous sommes avant tout souciés de nous faciliter le travail une fois que nous aurons à utiliser ces données : comme nous voulons représenter les différentes suites d'étapes sous la forme d'arbres, nous avons donné, pour chaque étape, une liste des étapes requises, ainsi qu'un lieu (l'idée étant d'afficher une suites d'étapes similaires à la même hauteur). Toutes les autres informations sont directement disponibles sur les sites en question.
Au vu de la faible quantité de données à traiter, nous ne nous sommes pas souciés des éventuelles redondances que nous pourrions introduire.



Recettes : liste d'objets JSON, de la forme :

			nom : string,
	    ingrédients : list of strings, (un ingrédient n'est représenté que par une string, ex " 4oeufs")
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
				lieu : string (ex : 'four','saladier2', ...)

Remarque : Il n'y a pas d'entiers à proprement parler en JSON,  "int" signifie seulement que l'on pourra directement convertir la donnée en entier depuis le Javascript.
