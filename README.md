# demo_exail
demo unreal pour exail


## Vidéo démo##

https://drive.google.com/file/d/1dznVqXAkvT8SFcsnX7dwWkzjrA5hm0lY/view?usp=sharing


## Choix Techniques

Liste des choix techniques en fonction des contraintes :
- Compétences : Mes compétences en codage temps réel 3D sont encore limitées (pas encore abordé la partie code sur unreal) j'ai choisi d'utiliser les blueprint pour le codage plustôt que C++.
- Compte tenu du matériel à disposition (PC vieillissant CG 3Go), j'avais choisi d'apprendre à coder sur Unity (et de revenir plus tard sur Unreal) afin de pallier les problématiques de performances. Etant contraint par Unreal 5.7 et ces éléments techniques j'ai choisi de :
	- limiter l'import d'objet externe au stricte minimum (import d'un robot de livraison compatible UE5.7)
	- supprimer les éléments couteux de l'environnement (nuages)
	- mettre tous les paramètres d'affichage dans l'espace de travail UNREAL au minimum
	- rester sur un objet simple à animer
- Pour être conforme à l'esprit de l'exercice j'ai choisi de :
	- ne pas partir sur du code existant à recopier (profiter de l'exercice pour expérimenter l'IA dans ce contexte et apprendre le fonctionnement des blueprint)
	- démarrer avec un projet vide (le moteur génère un plan avec la lumière et c'est tout)
- Je suis parti au début avec un mouvement de type gauche droite pour faire bouger l'objet cependant le comportement était mauvais quand il s'agissait de passer sur un obstacle, j'ai donc changé la logique pour tout adapter à la gravité et aux impacts.
- Les mouvements et accélérations ne sont pas "binaires" mais progressifs bien que cela soit subtile pour le joueur (cela complexifie les blueprint mais rends les comportements plus plaisants)
- L'objet initial étant représenté par "une box" pour l'aspect collision, le paramétrage a été assez complexe pour obtenir des mouvements propres, en effet les contraintes physiques réalistes ne sont pas cohérentes avec une boite frottant sur le sol...

=> Un mouvement pertinant aurait été obtenu avec une gestion plus poussée des contraintes physiques comme la gestion des roues indépendantes (et leur système de collision adhérence friction adapté) mais les délais ne me permettaient pas de comprendre et reproduire un tel système rapidement et de l'implémenter sur un objet qu'il aurait fallu retravailler.

- Il résulte de ces contraintes un mouvement qui parait assez cahotique quand on accélère (balancement droite gauche) dû aux microfrictions de la box avec le sol. Il faut stopper l'objet et attendre un peu pour que cela soit moins présent mais cela n'empêche pas de jouer avec l'objet.
- Compte tenu du poids d'un projet buildé et également du temps requis pour l'optimisation des performance je n'ai poussé que les éléments pertinents sur git.
- Je vous laisse le soin d'importer dans votre environnement unreal les objets sur git et de lancer le mode exécution de la scène Main
- Vous avez aussi voire une vidéo du jeu via le lien transmis si jamais un problème technique indépendant de ma volonté vous empêche d'importer les éléments déposer sur git.


## Procédure pour lancer le projet

### Procédure d'import
- Récupérer les fichiers sous forme d'archive depuis git :
	- https://github.com/MiniLightW/Exail_demo
	- code => download zip
- Créer un nouveau projet Unreal 5.7 vide. (afin de disposer en local des fichiers du moteur qui n'ont pas été poussés sur git (poids))
- Déposer les fichiers concernés à la racine du projet créé.

**Notes :**
- Le dossier important est "Content" et devrait être le seul utile mais je n'ai jamais testé de migration de fichier Unreal auparavant pour le confirmer.
- Il est possible que le répertoire "config" ne soit pas pertinent et écrase la configuration locale de l'utilisateur il est donc souhaitable de le retirer (je vous laisse juge selon votre expérience).
- Sur ma machine dépassée j'ai lancé le jeu en réduisant les performance de l'environnement au minimum et cela fonctionnait bien.

=> Si jamais une erreur technique empêche de lire le projet je vous invite à consulter la vidéo démo dont le lien est transmis un peu plus haut dans ce document.

### COMMANDES DE JEU
| Touche | Action |
|--------|--------|
| **Z / S** | Avancer / Reculer |
| **Q / D** | Rotation gauche / droite |
| **ESPACE** | Réinitialiser la position (si le véhicule est tombé ou mal orienté) |


## Outils et ressources utilisées

- Outils interne unreal :
	- Utilisation de Fab pour trouver l'objet à animer (gratuit + compatible UE 5.7) : robot de livraison
		- dossier : /Content/BendylabStudios
	- Modeleur Unreal + gestion auto des colisions par box :
		- dossier : /_GENERATED/damin/Mesh
	- Materials pour les couleurs :
		- dossier : /_GENERATED/damin/Materials
	- Blueprint pour le codage
		- dossier : /Input/Blueprint
	- Gestion des Commandes utilisateur avec : Input_Action et Input Mapping Context
		- dossier : input/InputAction
	- Texte explicatif dans HUD :
		- dossier : /_GENERATED/damin/HUD

- Utilisation de l'IA pour l'aide au codage du blueprint : Claude AI (le test avec duck AI étant peu concluant pour ce besoin).

- Utilisation du moteur de recherche Google pour certaines questions hors IA.

- Utilisation des projets exemples fournis avec Unity pour vérifier certains points.


## Enjoy :-)

```
      \O/   \O/   \O/
       |     |     |
      / \   / \   / \
```
