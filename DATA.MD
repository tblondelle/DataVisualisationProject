Recettes : liste d'objets JSON, de la forme :

			nom : string,
	    	ingrédients : list of strings,
			tps_cuisson : int,
			tps_preparation : int,
			(autres métadonnées)
			étapes : liste d'objets JSON, de la forme :
				
				identifiant : int    (l'identifiant est égal à la position dans la liste)
				descriprion_courte : string  (à afficher sur l'écran)
				descriprion_longue : string  (à afficher sur mouseOver)
				enfants : list of ints (les indices des enfants)
				lieu : string (ex : 'four','saladier2', ...)
				

