# Mettre à jour PokéClasse sur GitHub

Le dossier de cette archive constitue la version complète à publier.

## Méthode recommandée avec GitHub Desktop

1. Décompressez l’archive.
2. Ouvrez votre dépôt local dans **GitHub Desktop**.
3. Dans l’Explorateur de fichiers, ouvrez le dossier local de votre dépôt :
   - dans GitHub Desktop : **Repository → Show in Explorer** ;
4. Supprimez dans ce dossier les anciens éléments publiés :
   - l’ancien `index.html` ;
   - l’ancien `README.md` ;
   - l’ancien dossier `assets`, s’il existe.
5. Copiez à leur place tout le contenu du dossier décompressé :
   - `index.html` ;
   - `README.md` ;
   - `VERSION.txt` ;
   - `.nojekyll` ;
   - le dossier `assets`.
6. Revenez dans GitHub Desktop.
7. Vérifiez la liste des fichiers modifiés.
8. Dans **Summary**, écrivez par exemple :
   `Version finale animée`
9. Cliquez sur **Commit to main**.
10. Cliquez sur **Push origin**.

## Vérifier GitHub Pages

Dans GitHub :

1. ouvrez **Settings** ;
2. ouvrez **Pages** ;
3. vérifiez que la source est :
   - **Deploy from a branch** ;
   - branche `main` ;
   - dossier `/root`.
4. Patientez généralement une ou deux minutes.
5. Rechargez l’adresse du site avec `Ctrl + F5`.

## Important

Ne copiez pas le dossier parent `pokeclasse-release-finale` dans le dépôt.

Les fichiers doivent être directement à la racine :

```text
index.html
README.md
VERSION.txt
.nojekyll
assets/
```

Le dossier `assets` doit conserver exactement cette structure :

```text
assets/
├── maps/
│   ├── kanto.png
│   └── johto.png
└── ui/
    └── dashboard-inspiration.png
```

## En cas d’ancien affichage après la mise à jour

Le navigateur peut conserver une copie en cache.

Essayez :

- `Ctrl + F5` sous Windows ;
- `Cmd + Shift + R` sur Mac ;
- ou ouvrez le site dans une fenêtre privée.

La sauvegarde du joueur reste dans le navigateur grâce à `localStorage`.
