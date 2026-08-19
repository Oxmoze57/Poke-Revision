# PokéClasse — Version finale 1.5.2

Cette version regroupe l’ensemble des fonctionnalités validées :

- Kanto : révisions de français CE1 ;
- Johto : révisions de mathématiques CE1 ;
- Hoenn : programme CE2 avec 8 arènes ;
- École des Dresseurs, leçons et entraînements ;
- lecture automatique sauf pour la leçon et l’arène 1 de Hoenn ;
- arènes rejouables avec forte variété de questions ;
- système anti-répétition des questions ;
- Pokédex Kanto /151, Johto /100 et Hoenn /135 ;
- noms des Pokémon en français ;
- cartes interactives avec accès direct aux arènes ;
- Ligues finales ;
- Défi des Légendaires après chaque Ligue ;
- 10 à 20 questions aléatoires par Défi des Légendaires ;
- combats légendaires animés avec attaques, impacts et barres de PV ;
- capture de Pokémon légendaires ;
- Rayquaza chromatique noir comme rencontre ultra-rare à Hoenn ;
- sauvegarde locale compatible avec les versions précédentes.

## Publication sur GitHub Pages

Copiez tout le contenu de cette archive à la racine de votre dépôt GitHub.

Puis, dans GitHub Desktop :

1. ouvrez le dépôt ;
2. remplacez les anciens fichiers par ceux de cette version ;
3. saisissez comme résumé de commit : `Version finale 1.5.2`;
4. cliquez sur **Commit to main** ;
5. cliquez sur **Push origin** ;
6. attendez le déploiement GitHub Pages ;
7. rechargez le site avec `Ctrl + F5`.

Le Défi des Légendaires d’une région reste verrouillé tant que sa Ligue n’a pas été remportée.

## Version 1.5.3 — Correction des Ligues

Le combat de Ligue ne peut plus se terminer avant que toutes les questions aient été posées.

- Ligue Kanto : **16 questions obligatoires**, réussite à partir de **10/16**.
- Ligue Johto : **16 questions obligatoires**, réussite à partir de **10/16**.
- Ligue Hoenn CE2 : **20 questions obligatoires**, réussite à partir de **15/20**.
- Les barres de PV pendant une Ligue sont désormais visuelles et ne provoquent plus une fin prématurée.
- L’objectif est affiché clairement sous le titre du combat.
- Les arènes normales conservent leur fonctionnement actuel.

## Version 1.5.4 — Accès rapide à la Ligue

Le panneau d’accès direct de chaque région contient maintenant un bouton **Ligue Pokémon** juste sous les 8 arènes.

- Tant que les 8 badges ne sont pas obtenus, le bouton indique le nombre de badges manquants.
- Dès que les 8 badges sont obtenus, le bouton devient actif.
- Kanto et Johto affichent clairement : **16 questions • objectif 10/16**.
- Hoenn affiche : **20 questions • objectif 15/20**.
- Une Ligue déjà remportée reste accessible et rejouable depuis ce même bouton.

## Version 1.5.5 — Correction de l’accès rapide à la Ligue de Johto

Le bouton de Ligue est maintenant lié explicitement à la région active.

Un cas de compatibilité avec les anciennes sauvegardes a aussi été corrigé :
si une Ligue avait déjà été remportée dans une ancienne version, elle reste
rejouable même si les huit indicateurs d’arène n’avaient pas tous été enregistrés.

Au chargement, PokéClasse remet également en cohérence les badges et arènes
d’une région dont la Ligue a déjà été gagnée.

## Version 1.5.6 — Bouton Ligue fiabilisé

Le bouton d'accès rapide à la Ligue utilise maintenant un démarrage asynchrone
sécurisé et affiche « Préparation de la Ligue… » dès le clic.

Le démarrage est explicitement lié à la région affichée (Kanto, Johto ou Hoenn).

Si PokéAPI ou le chargement d'un Pokémon adverse échoue, la Ligue démarre quand
même avec un adversaire de secours. Une panne réseau ne peut donc plus donner
l'impression que le bouton ne fonctionne pas.

Les règles restent :
- Kanto : 16 questions, victoire à 10/16 ;
- Johto : 16 questions, victoire à 10/16 ;
- Hoenn : 20 questions, victoire à 15/20 ;
- toutes les questions de Ligue sont toujours posées.

## Version 1.5.7 — Test automatique Ligue Johto

Un test automatique s'exécute après le chargement de l'application.

Il vérifie précisément le scénario problématique :

1. simulation d'une ancienne sauvegarde où la Ligue Johto est remportée mais où plusieurs arènes ne sont plus enregistrées ;
2. relecture de cette sauvegarde depuis `localStorage`, comme après un rechargement de page ;
3. exécution de la migration de compatibilité ;
4. vérification que les 8 arènes Johto sont restaurées ;
5. utilisation du vrai chemin `quickOpenLeague → openLeague` ;
6. vérification que l'écran de combat s'ouvre en mode Ligue ;
7. vérification que la Ligue Johto contient exactement 16 questions.

Le chargement réseau de PokéAPI est remplacé uniquement pendant le test afin que le diagnostic vérifie le bouton et la navigation sans dépendre d'Internet.

Le test restaure ensuite intégralement la sauvegarde et l'écran du joueur.

Résultat disponible dans la console :
`window.POKECLASSE_TEST_RESULTS.johto_league_button_legacy_save_reload`

Un bouton **🧪 Tester la Ligue Johto** est aussi disponible dans l'écran Progrès.

## Version 1.5.8 — Correction définitive Ligue Johto

Le diagnostic a montré deux causes possibles :

1. les anciennes versions pouvaient enregistrer un badge dans `state.badges` sans
   conserver exactement le même état dans `state.arenas` ;
2. le test automatique lancé 700 ms après l'ouverture de la page pouvait lui-même
   modifier temporairement la navigation pendant que le joueur utilisait l'application.

Corrections :
- le test Johto ne s'exécute plus automatiquement pendant une partie ;
- il reste disponible manuellement dans **Progrès → Tester la Ligue Johto** ;
- les anciennes sauvegardes sont migrées dès le démarrage réel de l'application ;
- un badge obtenu compte désormais comme une arène terminée même si l'ancien
  indicateur `state.arenas` est absent ;
- le bouton, la carte et la Ligue utilisent maintenant exactement la même fonction
  de vérification ;
- une Ligue déjà gagnée est toujours rejouable ;
- le démarrage de la Ligue reste fonctionnel même si PokéAPI est momentanément indisponible.

## Version 1.5.9 — Ligue Johto : chemin dédié

Les deux boutons de Ligue de Johto (sur la carte et dans l'accès rapide)
utilisent maintenant une fonction dédiée indépendante du lanceur générique.

Quand Johto possède 8 badges ou que sa Ligue a déjà été gagnée :
- le clic force explicitement la région `math` ;
- le combat de Ligue démarre directement ;
- il contient toujours 16 questions ;
- l'objectif reste 10/16 ;
- le chargement ne dépend pas du choix dynamique d'un adversaire via PokéAPI.

Cette modification cible uniquement Johto afin de supprimer les conflits
résiduels entre le changement de région, les anciennes sauvegardes et le
lanceur générique de Ligue.

## Version 1.6.0 — Navigation simplifiée des régions

Les cartes de Kanto, Johto et Hoenn ne servent plus de boutons.

- les marqueurs, l'École et la Ligue dessinés sur la carte sont décoratifs ;
- un seul panneau **Accès rapide** est placé sous la carte ;
- les 8 arènes sont accessibles par de grands boutons faciles à utiliser ;
- l'École des Dresseurs possède son propre bouton ;
- la Ligue Pokémon possède un grand bouton unique sous les arènes ;
- la même logique est utilisée pour Kanto, Johto et Hoenn ;
- cela élimine les conflits liés aux zones de clic superposées sur les cartes.

## Version 1.6.1 — Accès rapide Johto vérifié

Tous les clics de l'accès rapide sont maintenant gérés par des événements JavaScript dédiés, sans `onclick` inline.

Pour Johto, le panneau contient :
- 1 bouton École des Dresseurs ;
- 8 boutons d'arènes ;
- 1 bouton Ligue Pokémon.

La carte est strictement décorative : ses marqueurs d'arène, l'École et la Ligue ont `pointer-events: none`.

Le bouton Ligue affiche maintenant un message de confirmation seulement après que l'écran de combat a réellement été ouvert :
`✅ Ligue de JOHTO ouverte • objectif 10/16`

Un contrôle interne `verifyJohtoQuickAccessStructure()` vérifie également :
- la présence du bouton École ;
- la présence des 8 boutons d'arènes ;
- les indices 0 à 7 des arènes ;
- la présence du bouton Ligue ;
- l'absence d'interaction sur les éléments de la carte.

## Version 1.6.2 — Ouverture garantie de la Ligue Johto

La Ligue Johto utilise maintenant un lanceur totalement séparé.

Dès que l'accès rapide affiche les 8 arènes comme terminées :
- la Ligue est considérée comme accessible ;
- le clic ne dépend plus de PokéAPI ;
- le combat est créé immédiatement en mémoire ;
- l'écran de combat est ouvert de façon synchrone ;
- la Ligue contient exactement 16 questions ;
- l'objectif est 10/16 ;
- un message confirme : `✅ Ligue de JOHTO ouverte`.

Le bouton possède aussi un gestionnaire direct de secours. Ainsi, même si le
gestionnaire d'événement général de l'accès rapide rencontrait un problème,
le clic Johto dispose encore d'un chemin indépendant.

## Version 1.6.3 — Correction des combats d'arènes

La simplification précédente de la navigation avait créé un conflit entre le
gestionnaire de clic global et les boutons recréés dynamiquement.

Corrections :
- chaque bouton d'arène possède désormais son propre clic direct ;
- une arène déjà gagnée est toujours rejouable, même avec une ancienne sauvegarde
  où le drapeau de l'École est absent ;
- le bouton ouvre directement le combat après une courte transition ;
- un message confirme l'ouverture du combat ;
- si PokéAPI échoue, un adversaire de secours permet quand même de jouer ;
- la carte reste totalement décorative et n'est jamais utilisée pour lancer un combat.

## Version 1.6.4 — Correction trouvée pendant le test du parcours complet

Le test réel du parcours a mis en évidence une régression : les fonctions de
lancement des combats écrivaient dans `battleObjective`, mais cet élément avait
disparu de l'écran de combat. Une exception JavaScript interrompait alors
l'ouverture des combats d'arène.

Correction :
- restauration de `battleObjective` dans l'écran de combat ;
- accès à cet élément rendu défensif pour éviter qu'une future modification
  graphique ne bloque à nouveau un combat.

## Version 1.6.5 — Correction du clic Ligue et des transitions

Deux problèmes ont été identifiés pendant le test du parcours complet :

1. le `onclick` du bouton Ligue Johto contenait des antislashs littéraux autour
   de `math`, ce qui rendait le gestionnaire inline invalide dans le navigateur ;
2. l'application vérifiait parfois l'ouverture d'un combat immédiatement alors
   que la transition visuelle entre écrans dure 170 ms.

Corrections :
- le bouton Ligue utilise désormais simplement `routeOpenLeague(this)` ;
- il n'existe plus de gestionnaire concurrent pour ce bouton ;
- les contrôles d'ouverture des arènes et des Ligues attendent la fin de la
  transition avant de conclure à un échec ;
- le même comportement est utilisé pour Kanto, Johto et Hoenn.

## Version 1.6.6 — Ligue Johto HD et variée

La version de secours de la Ligue Johto utilisait un Tyranocif fixe avec un petit sprite,
ce qui expliquait à la fois la baisse de qualité visuelle et les rencontres répétitives.

Corrections :
- illustrations `official-artwork` HD rétablies dans la Ligue ;
- adversaire Johto choisi aléatoirement parmi Pharamp, Mentali, Noctali, Scarhino,
  Démolosse, Hyporoi, Donphan, Porygon2, Écrémeuh et Tyranocif ;
- le jeu évite de proposer deux fois de suite le même adversaire ;
- les noms sont affichés en français ;
- les Pokémon légendaires restent réservés au Défi des Légendaires ;
- le lancement de la Ligue reste indépendant de PokéAPI pour éviter les blocages.
