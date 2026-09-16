# Documentation du CV

## 1. Présentation du projet

Ce dossier contient une page web présentant le curriculum vitae de Mr.Billy Jarod.

C'est mon projet principal, il évoluera en même temps que moi. Au fur et à mesure des compétences que je vais acquérir, je continuerai d'améliorer le CV et je publierai des commits (version par version) sur ce repository.

Ce CV a été entièrement réalisé grâce à mes connaissances et à des recherches sur Internet, notamment sur les sites [MDN Web Docs](https://developer.mozilla.org/fr/) et [W3Schools](https://www.w3schools.com/). Aucune IA n'a réalisé la moindre ligne de code. J'ai simplement questionné l'IA de Google lorsque je ne comprenais vraiment pas une propriété.

L'écriture de ce fichier README.md lui a été réalisée par le Copilot IA GitHub (beaucoup trop long à écrire et c'était clairement moins bien expliqué). :D

============ EXPLICATIONS ============

La page est composée de deux fichiers principaux :

- `index.html` : contient le contenu et la structure de la page ;
- `style.css` : contient l'apparence visuelle et les règles d'adaptation aux différentes tailles d'écran.

Les images utilisées sont placées dans le dossier `images` et le fichier PDF du CV dans le dossier `PDF` n'est pas disponible, afin de ne pas divulguer mes informations personnelles : **adresse et numéro de téléphone**

## 2. Explication du fichier `index.html`

### 2.1 Déclaration du document

Le fichier commence par :

```html
<!DOCTYPE html>
```

Cette déclaration indique au navigateur que le document utilise la version HTML5.

La balise suivante précise que le contenu est en français :

```html
<html lang="fr">
```

L'attribut `lang="fr"` est utile pour l'accessibilité, la lecture vocale et le référencement.

### 2.2 La partie `<head>`

La section `<head>` contient les informations qui ne sont pas directement affichées dans la page.

```html
<meta charset="utf_8">
```

Cette ligne doit définir l'encodage des caractères. Elle est actuellement écrite avec un caractère `_` et devrait être écrite ainsi :

```html
<meta charset="UTF-8">
```

Cette correction évite les problèmes d'affichage avec les accents comme `é`, `è`, `à` et `ô`.

La balise viewport permet à la page de s'adapter aux écrans mobiles :

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

`width=device-width` utilise la largeur réelle de l'appareil et `initial-scale=1.0` évite un zoom initial automatique.

Deux balises `preconnect` préparent la connexion vers Google Fonts. La balise suivante charge la police Figtree :

```html
<link href="https://fonts.googleapis.com/css2?family=Figtree:ital,wght@0,300..900;1,300..900&display=swap" rel="stylesheet">
```

Enfin, cette balise relie le HTML au fichier CSS :

```html
<link href="style.css" rel="stylesheet">
```

### 2.3 Le `<body>`

Le `<body>` contient tous les éléments visibles de la page.

Le `<header>` et le `<footer>` sont actuellement vides. Ils peuvent être supprimés s'ils ne servent pas, ou être utilisés plus tard pour ajouter une navigation, des liens ou des informations complémentaires.

La balise `<main>` contient le contenu principal du CV :

```html
<main>
	 <section class="display">
```

La classe `.display` est utilisée par le CSS pour transformer le CV en grille sur les grands écrans.

### 2.4 La colonne personnelle

La première section est une colonne dédiée aux informations personnelles :

```html
<section class="display_info_perso">
```

Elle contient :

- la photo de profil ;
- le nom et le métier ;
- le bouton de téléchargement du CV ;
- les points forts ;
- les hobbies ;
- les coordonnées.

La photo est placée dans un lien :

```html
<a href="images/img_profil_cv.jpeg">
	 <img src="images/img_profil_cv_mini.png" ...>
</a>
```

L'image miniature est affichée dans la page. Un clic ouvre l'image plus grande. L'attribut `alt` décrit la photo pour les personnes qui utilisent un lecteur d'écran.

Le nom est placé dans une balise `<h1>` :

```html
<h1>BILLY JAROD</h1>
```

Une page doit normalement avoir un seul titre principal `<h1>`. C'est correct ici pour identifier la personne présentée.

Le bouton actuel est en réalité un lien :

```html
<a href="PDF/cv_lettre_mr_billy_jarod.pdf" ... download="cv_lettre_mr_billy_jarod.pdf">
	 Télécharger le CV
</a>
```

L'attribut `download` demande au navigateur de télécharger le fichier au lieu de simplement l'afficher. Le fonctionnement dépend toutefois du navigateur et de la façon dont la page est ouverte. Le fichier PDF doit rester dans le chemin indiqué.

Les listes `<ul>` présentent les points forts et les hobbies. Chaque élément est déclaré avec `<li>`, ce qui est adapté à ce type d'information.

Les coordonnées sont présentées avec des paragraphes `<p>`. Le mot important est entouré d'une balise `<span>` pour pouvoir lui appliquer un soulignement en CSS.

### 2.5 La colonne générale

La seconde section contient les informations professionnelles :

```html
<section class="display_info_generale">
```

Elle est divisée en trois parties :

1. `a_propos` présente le profil professionnel ;
2. `formation_pro` présente les formations ;
3. `experience_pro` présente les expériences professionnelles.

Les titres de ces parties utilisent des balises `<h1>` et `<h2>`. Pour une hiérarchie HTML plus logique, le titre `A PROPOS DE MOI` devrait plutôt être un `<h2>`, car le nom de la personne est déjà le `<h1>` principal.

Les classes suivantes permettent de cibler les informations avec le CSS :

- `.type_formation` pour le nom d'une formation ;
- `.lieu_formation` pour le lieu et les dates ;
- `.type_lieu_emplois` pour le nom d'une entreprise ;
- `.duree_poste` pour la durée d'un emploi ;
- `.poste` pour les fonctions réalisées.

## 3. Explication du fichier `style.css`

### 3.1 Règle générale

La règle suivante s'applique à tous les éléments :

```css
* {
	 box-sizing: border-box;
}
```

Avec `border-box`, la largeur et la hauteur incluent les bordures et les espacements internes. Cela rend les dimensions plus faciles à contrôler.

### 3.2 Style du corps de la page

La règle `body` définit :

- la police Figtree ;
- la taille de texte générale ;
- l'image de fond en bois ;
- la suppression des marges par défaut ;
- des ombres internes pour donner du relief.

```css
background-image: url(images/background_wood.jpg);
background-size: cover;
background-position: center;
```

`cover` agrandit l'image pour couvrir toute la zone disponible. Une partie de l'image peut être recadrée afin de conserver les proportions.

### 3.3 Style de la structure principale

La règle `main` utilise Flexbox et occupe au minimum la hauteur de la fenêtre :

```css
display: flex;
flex-direction: column;
min-height: 100dvh;
```

`100dvh` correspond à la hauteur dynamique de la fenêtre. Cette unité est adaptée aux navigateurs mobiles modernes.

### 3.4 Photo et identité

`.photo_prenom` utilise une taille calculée avec `clamp()` :

```css
width: clamp(10rem, 6.57rem + 17.14vw, 20rem);
height: clamp(10rem, 6.57rem + 17.14vw, 20rem);
```

La taille minimale est `10rem`, la taille maximale est `20rem` et la valeur intermédiaire évolue selon la largeur de l'écran.

```css
border-radius: 50%;
overflow: hidden;
```

Ces propriétés créent une photo ronde et empêchent l'image de dépasser de son conteneur.

### 3.5 Bouton de téléchargement

`.bouton_download` transforme le lien PDF en bouton visuel. Il définit son espacement, sa couleur, sa taille de texte et ses coins arrondis.

La règle `:active` réduit légèrement le bouton au moment du clic :

```css
.bouton_download:active {
	 transform: scale(0.98);
}
```

Cela donne un retour visuel à l'utilisateur.

### 3.6 Informations générales

Les règles `.display_info_generale`, `.introduction p` et `.formation p` contrôlent l'alignement du texte et les espacements.

```css
text-align: justify;
```

Cette propriété aligne le texte sur les deux côtés. Sur un petit écran, elle peut parfois créer de grands espaces entre les mots. `text-align: left` peut être plus confortable sur mobile.

### 3.7 Media query tablette

Cette règle s'applique entre 767px et 1023px :

```css
@media (min-width: 767px) and (max-width:1023px) {
```

La taille des textes est augmentée et la classe `.space_between_points_fort_coordo` devient une ligne Flexbox avec `display: flex`.

### 3.8 Media query écran moyen

Cette règle s'applique entre 1024px et 1439px.

La classe `.display` devient une grille à deux colonnes :

```css
.display {
	 display: grid;
	 grid-template-columns: 15rem 1fr;
	 min-height: 100dvh;
	 overflow-y: auto;
}
```

La première colonne mesure `15rem` et la seconde prend l'espace restant.

`overflow-y: auto` ajoute une barre verticale lorsque le contenu dépasse la hauteur disponible. C'est utile pour accéder au contenu, mais cela peut créer une deuxième barre de défilement en plus de celle du navigateur.

### 3.9 Media query grand écran

À partir de 1440px, la colonne personnelle est élargie à `22rem`, les textes sont agrandis et le contenu général reçoit davantage d'espacement.

La règle suivante conserve une hauteur maximale d'écran pour `.display` :

```css
max-height: 100dvh;
overflow-y: auto;
```

Elle crée un défilement interne si le CV est plus haut que la fenêtre.

## 4. Erreurs et points à améliorer

### 4.1 Erreurs dans `index.html`

1. **Encodage incorrect**

	La valeur `utf_8` n'est pas la bonne écriture HTML. Il faut utiliser `UTF-8`.

2. **Absence de JavaScript**

	Il n'y a pas de fonction JavaScript dédiée au téléchargement. Le lien avec `download` peut suffire dans de nombreux cas, mais un script permettrait de gérer les erreurs et d'afficher un retour à l'utilisateur.

3. **Hiérarchie des titres perfectible**

	Le titre `A PROPOS DE MOI` est un deuxième `<h1>`. Il serait préférable de garder un seul `<h1>` et d'utiliser des `<h2>` pour les grandes rubriques.

4. **Éléments vides**

	`<header>` et `<footer>` sont vides. Ils peuvent être supprimés tant qu'ils ne contiennent aucune information.

5. **Contact non interactif**

	L'adresse e-mail est affichée comme du texte. Un lien `mailto:jarod.billy@hotmail.com` permettrait d'ouvrir directement le logiciel de messagerie.

### 4.2 Erreurs dans `style.css`

1. **Flexbox incomplet dans `.emplois_entete`**

	Cette règle contient `flex-direction` et `align-items`, mais pas `display: flex` :

	```css
	.emplois_entete {
		 flex-direction: column;
		 align-items: flex-start;
	}
	```

	Ces propriétés ne produisent pas l'effet attendu sans :

	```css
	display: flex;
	```

2. **Barre de défilement interne**

	`overflow-y: auto` est présent sur `.display` dans les règles desktop. Le contenu peut donc avoir sa propre barre de défilement, tandis que le navigateur possède déjà la barre principale.

	Si le défilement interne n'est pas voulu, il est possible de supprimer `overflow-y: auto` et de laisser la page entière défiler naturellement. Si le défilement interne est voulu, il faut conserver une hauteur contrôlée et expliquer visuellement cette organisation.

3. **Hauteurs minimales et maximales difficiles à combiner**

	`main`, `.display` et les media queries utilisent plusieurs fois `100dvh`. Selon la taille du contenu, cela peut provoquer un dépassement vertical ou une barre de défilement supplémentaire.

4. **Largeur de `main` sur desktop**

	`main` mesure `75%` sur les grands écrans. Cette valeur est acceptable, mais elle peut devenir trop étroite ou trop large selon la résolution. Une largeur limitée avec `max-width` serait plus stable :

	```css
	width: min(75%, 1200px);
	margin-inline: auto;
	```

5. **Responsive incomplet sur les très petits écrans**

	Les règles mobiles sont peu nombreuses. Les textes longs, les adresses e-mail et les noms d'entreprises peuvent dépasser la largeur disponible. Il serait utile d'ajouter :

	```css
	overflow-wrap: anywhere;
	```

	sur les zones contenant des mots longs.

## 5. Recommandations d'amélioration

Pour améliorer le projet, il faudrait :

- corriger `UTF-8` et `fit-content` ; FAIT
- ajouter `display: flex` à `.emplois_entete` ; FAIT
- choisir entre un défilement global ou un défilement interne ;
- ajouter le script JavaScript de téléchargement du PDF ; 
- rendre l'adresse e-mail cliquable ;
- utiliser un seul `<h1>` ;
- tester la page sur mobile, tablette, ordinateur portable et grand écran ;
- vérifier les chemins des images et du fichier PDF après tout déplacement de dossier ;
- ajouter des états `:hover` et `:focus-visible` accessibles aux liens et aux boutons.

## Conclusion

Le projet possède déjà une base correcte : le HTML sépare les informations personnelles du contenu professionnel et le CSS utilise Flexbox, Grid, `clamp()` et des media queries pour commencer à rendre le CV responsive. La structure est donc exploitable et peut être améliorée sans être entièrement reconstruite.

Les principales erreurs techniques sont l'encodage `utf_8`, la valeur CSS invalide `fit_content` et l'utilisation de propriétés Flexbox sans activer Flexbox. Le point qui explique le plus probablement l'apparition d'une barre sur la page est `overflow-y: auto` associé à `min-height` ou `max-height: 100dvh`. Cette combinaison crée un défilement à l'intérieur du CV, en plus du défilement normal du navigateur.

Les améliorations prioritaires sont de corriger ces erreurs, de simplifier la gestion des hauteurs, puis de tester le résultat sur plusieurs écrans. Ensuite, le projet pourra recevoir le bouton Portfolio et une fonction JavaScript de téléchargement plus complète. Le site sera alors plus fiable, plus accessible et plus agréable à utiliser.
