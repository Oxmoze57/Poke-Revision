# PokéClasse — Édition complète

Version intégrant les éléments discutés :

- page d’accueil entièrement repensée comme un tableau de bord illustré ;
- grandes cases avec raccourcis vers Kanto, Johto, l’École, les arènes, le Pokédex, les badges, la progression et le défi du jour ;
- profil du partenaire, XP, étoiles, badges et captures sur l’accueil ;
- bouton « Continuer l’aventure » et indication de la prochaine étape ;
- cartes de Kanto et Johto fournies par l’utilisateur ;
- arènes représentées par des symboles de badges colorés plutôt que par des images de stades ;
- nom de la ville et du badge accessible au survol ;
- badges gagnés marqués d’une coche, badges verrouillés grisés ;
- lecture automatique des questions et des réponses ;
- bouton « Réécouter » dans les entraînements et les combats ;
- animations, particules, sons et transitions ;
- arènes rejouables, Ligues, Pokédex et sauvegarde locale.

## Installation GitHub Pages

Envoyez `index.html` ainsi que le dossier `assets` à la racine du dépôt.

Activez ensuite :

`Settings → Pages → Deploy from a branch → main → /root`

Il est indispensable de conserver les chemins :

- `assets/maps/kanto.png`
- `assets/maps/johto.png`
- `assets/ui/dashboard-inspiration.png`

Les illustrations Pokémon sont chargées depuis PokéAPI et nécessitent une connexion Internet.

## Mise à jour v2

Les deux grandes cartes Kanto et Johto ont été retirées de la page d’accueil. Elles sont remplacées par un seul raccourci **Régions** qui ouvre l’écran de sélection.
