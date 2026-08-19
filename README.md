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
