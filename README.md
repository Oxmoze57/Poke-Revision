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
