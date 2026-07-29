# PokéClasse — Cartes esthétiques

Version basée sur la maquette visuelle validée.

## Changements

- écran Régions transformé en deux grandes cartes illustrées ;
- cartes Kanto et Johto découpées depuis la maquette esthétique ;
- progression et prochaine étape affichées sur chaque région ;
- cartes interactives conservées ;
- zones des badges cliquables sans ajouter de symboles par-dessus l’illustration ;
- toutes les fonctions précédentes restent présentes : leçons, arènes, lecture vocale, animations, combats, Pokédex et sauvegarde.

## Publication GitHub Pages

Copiez tous les fichiers de l’archive à la racine du dépôt en conservant le dossier `assets`.

Puis faites un commit et un push depuis GitHub Desktop.

## Correction 1.1.1

- les huit badges de chaque carte sont maintenant clairement visibles ;
- chaque badge est un véritable bouton cliquable ;
- les arènes verrouillées restent cliquables et expliquent comment les débloquer ;
- un cadenas distingue les arènes nécessitant encore l’entraînement de l’École ;
- les zones de clic ont été agrandies pour les écrans tactiles.

## Interface de carte premium 1.2.0

- carte principale plus grande et plus lisible ;
- marqueurs compacts intégrés à l’illustration ;
- panneau latéral détaillé pour l’arène sélectionnée ;
- bouton unique pour entrer dans l’arène ;
- états visuels accessibles, terminés et verrouillés ;
- barre de progression régionale ;
- école et Ligue intégrées comme destinations spéciales ;
- adaptation automatique aux écrans mobiles.

## Version 1.2.1 — Fonds Kanto et Johto

- intégration des cartes esthétiques de Kanto et Johto comme arrière-plans ;
- conservation des badges et marqueurs cliquables au-dessus des images ;
- les images utilisent `pointer-events: none` et ne bloquent donc jamais les clics ;
- ajout d’un voile léger pour améliorer la lisibilité des marqueurs ;
- compatibilité mobile conservée.

## Version 1.2.2 — Correction définitive des fonds

Les deux cartes sont maintenant intégrées directement dans `index.html` sous forme de données d’image. Elles ne dépendent plus d’un chemin de fichier externe.

Cette correction évite :
- les erreurs de chemin sur GitHub Pages ;
- les images absentes lors de l’aperçu du fichier HTML ;
- les problèmes liés au nom du dépôt ou à un sous-dossier ;
- certains problèmes de cache.

Les badges restent placés dans un calque supérieur et conservent leurs clics.

## Version 1.2.3 — Alignement précis

Les centres des huit symboles de chaque carte ont été mesurés directement sur les images Kanto et Johto.

Les marqueurs utilisent maintenant :
- des coordonnées propres à chaque région ;
- un positionnement par le centre grâce à `translate(-50%, -50%)` ;
- un léger déplacement uniquement au survol ou à la sélection ;
- les mêmes coordonnées proportionnelles sur ordinateur et mobile.


## Version 2.0 — Interface aventure
Nouvelle navigation, parcours lumineux, noms des villes, progression intégrée et panneau d’arène façon jeu vidéo.

## Version 1.2.5 — Correction structurelle de l’alignement

La correction ne repose plus sur une compensation approximative de `object-fit: cover`.

- les panneaux décoratifs inférieurs ont été retirés des deux images ;
- les fonds Kanto et Johto utilisent désormais exactement le même ratio que le calque interactif ;
- chaque bouton est positionné au centre mesuré du symbole correspondant ;
- le chemin lumineux utilise les mêmes coordonnées que les boutons ;
- le bouton École est nettement plus compact, en particulier sur Johto.

## Version 1.2.7 — Noms français des Pokémon

- `Caterpie` est maintenant affiché sous le nom **Chenipan** ;
- `Oddish` devient **Mystherbe** ;
- tous les Pokémon actuellement utilisés dans les arènes disposent d’un nom français ;
- pour tout futur Pokémon ajouté au jeu, PokéClasse tente automatiquement de récupérer son nom français via PokéAPI ;
- les identifiants anglais restent utilisés uniquement en interne afin de charger les images.
