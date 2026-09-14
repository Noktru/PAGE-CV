### 🎯 Mon premier objectif

Ce CV que j'ai réalisé avec l'aide d'une IA, représente pour moi un **premier objectif à atteindre**. 
Il constitue le point de départ de mon parcours et servira de base pour mesurer mes progrès. Au fur et à mesure de mon apprentissage, je souhaite être capable de l'améliorer et surtout de comprendre et réaliser par moi-même ce que j'ai construis aujourd'hui avec l'aide de l'IA.


# CV responsive - explication

## Fichiers utilisés

- `index2.html` contient toute la structure HTML de la page.
- `style2.css` contient toute la mise en forme responsive.
- `README.md` explique le fonctionnement du projet.

La page utilise les ressources déjà présentes dans le dossier :

- `images/background_wood.jpg` pour le fond ;
- `images/img_profil_cv_mini.png` pour la photo affichée ;
- `images/img_profil_cv.jpeg` pour la photo en grand format ;
- `PDF/cv_lettre_mr_billy_jarod.pdf` pour le téléchargement du CV.

## Structure HTML

La page est organisée en deux parties principales :

1. `.profile-panel` contient le profil, la photo, le métier, les boutons, les points forts, les hobbies et les coordonnées.
2. `.content-panel` contient la présentation, la formation et les expériences professionnelles.

Les balises sémantiques `main`, `section`, `article`, `aside` et `h1`/`h2`/`h3` rendent le contenu plus compréhensible pour les navigateurs, les moteurs de recherche et les lecteurs d'écran.

## Responsive design

Le CSS utilise une approche « mobile first » : les règles de base sont prévues pour les petits écrans, puis des media queries améliorent l'affichage sur les écrans plus larges.

- En dessous de `600px`, les éléments sont empilés pour rester lisibles sur un téléphone.
- À partir de `600px`, les points forts et les hobbies peuvent occuper deux colonnes. Les expériences utilisent également deux colonnes.
- À partir de `1024px`, le CV devient une grille à deux colonnes : une colonne de profil et une colonne de contenu.
- Au-delà de `1440px`, la colonne du profil est légèrement élargie.

Les dimensions utilisent `min()`, `clamp()`, `minmax()` et `rem`. Cela permet aux textes, aux espacements et à la photo de s'adapter sans imposer une largeur fixe à la page.

## Centrage sur les grands écrans

Cette règle répond à la demande de centrage lorsque la largeur dépasse `1024px` et que la hauteur dépasse `1366px` :

```css
@media (min-width: 1024px) and (min-height: 1367px) {
	.page-shell {
		align-items: center;
	}
}
```

La largeur et la hauteur sont exprimées en pixels CSS. La condition `min-height: 1367px` signifie donc « hauteur strictement supérieure à 1366px ».

## Téléchargement du PDF

Le bouton `Télécharger le CV` possède l'identifiant `downloadCv`. Le script JavaScript :

1. désactive temporairement le bouton ;
2. récupère le PDF avec `fetch()` ;
3. transforme la réponse en objet `Blob` ;
4. crée une adresse temporaire avec `URL.createObjectURL()` ;
5. crée un lien invisible avec l'attribut `download` ;
6. lance le téléchargement ;
7. libère l'adresse temporaire avec `URL.revokeObjectURL()`.

Si le téléchargement direct échoue, par exemple lorsque la page est ouverte dans un contexte local particulier, le script ouvre le PDF dans un nouvel onglet. Le fichier est alors toujours accessible.

## Bouton Portfolio

Le bouton `Portfolio` est déjà présent dans le HTML. Pour le moment, il affiche un message indiquant que la rubrique sera bientôt disponible. Plus tard, il pourra être relié à une page ou à une section réelle en remplaçant son comportement JavaScript par un lien vers cette destination.

## Lancer la page

Ouvrez `index2.html` dans un navigateur. Pour un fonctionnement plus fiable du téléchargement JavaScript, il est préférable d'utiliser un petit serveur local, par exemple l'extension **Live Server** de VS Code.

Le fichier PDF doit rester à cet emplacement relatif :

```text
PAGE-CV/
|-- index2.html
|-- style2.css
|-- PDF/
	|-- cv_lettre_mr_billy_jarod.pdf
```

Si le PDF est déplacé, modifiez la constante `pdfPath` dans `index2.html`.
