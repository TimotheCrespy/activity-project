# Vue Js - Interrogation

## Partie informatique

### Mise en place

Récupérer le projet `activity-project` disponible à cette URL : https://github.com/TimotheCrespy/activity-project

Installer toutes les dépendances requises dans le `package.json`.

Pour lancer le projet, utiliser un terminal et se rendre dans le répertoire du projet et lancer la commande `npm run serve`. Cette commande propose du « Hot-Module-Replacement (HMR) », permettant de recompiler tout le code dès qu'il est modifié, de la même manière que la commande `npm run watch` sur d'autres projets. Se rendre ensuite sur l'URL indiquée dans le terminal (le plus souvent, `http://localhost:8080/`) dans un navigateur.

Il s'agit d'un projet utilisant Vue CLI (https://cli.vuejs.org/guide/).

Installer `axios`(https://github.com/axios/axios).

Le design est à ignorer, sauf lorsque demandé explicitement.

Les bonnes pratiques sont à respecter : casse, indentation, orthographe, etc.

### Initialisation

Modifier le logo de Vue Js par le logo de chat ennuyé suivant, avec une hauteur de 250 pixels : http://kittentoob.com/wp-content/uploads/2015/02/872276176_c36c5f268c_z-640x428.jpg (si l'URL renvoie une erreur, utiliser un autre logo représentant l'ennui au choix).

L'application doit alors répondre correctement dans le navigateur, en affichant simplement le logo de chat ennuyé et le contenu de `HelloWorld.vue`.

### Page principale

Modifier le composant `HelloWorld.vue` pour le nommer `RandomActivity.vue`.

Dans ce composant `RandomActivity.vue`, récupérer lors de la création du composant via l'API Bored (https://www.boredapi.com/) un objet dans une variable du state comportant un activité aléatoire, sous cette forme :
```json
{
  "activity": "Take your cat on a walk",
  "type": "relaxation",
  "participants": 1,
  "price": 0.02,
  "link": "",
  "key": "5940465",
  "accessibility": 0.1
}
```

S'aider de la documentation de l'API pour déterminer l'URL complète à appeler : https://www.boredapi.com/documentation

Dans une propriété calculée du même composant, transformer la valeur de la propriété `price` en chaine de caractères selon le principe suivant :
- inférieur à `0.29` : "Coût raisonnable"
- entre `0.3` et `0.49` : "Coût modéré"
- supérieur à `0.5` : "Coût élevé"

Afficher le nom de l'activité, son type et son coût (issu de la propriété calculée) sous forme de liste HTML non ordonnée.

### Recherche avancée

Créer un nouveau composant `SearchActivity.vue`.
Dans `App.vue`, intégrer ce composant sous le composant `RandomActivity.vue`.

Dans ce composant `SearchActivity.vue`, créer un formulaire simple comportant les champs suivants :
- un champ de type range, modifiable entre `0.1` et `1.0`, intitulé « Budget maximum »
- une liste déroulante, intitulée « Type », comportant les clés et valeurs du tableau suivant :
```js
[{
    "busywork": "Occupation"
}, {
    "social": "Sociale"
}, {
    "diy": "Do it yourself"
}, {
    "cooking": "Cuisine"
}, {
    "relaxation": "Relaxante"
}, {
    "recreational": "Récréative"
}, {
    "music": "Musique"
}, {
    "charity": "Charité"
}, {
    "education": "Éducative"
}]
```
- un bouton de validation du formulaire, intitulé « Rechercher ».

Lors du clic sur le bouton « Rechercher », prendre en compte toutes les informations du formulaire pour récupérer via l'API une activité remplissant les critères, i.e. un objet dans une variable du state. La forme de cet objet est exactement la même que celle de l'activité aléatoire.

Toujours bien s'aider de la documentation de l'API pour déterminer l'URL complète à appeler : https://www.boredapi.com/documentation

Afficher ensuite seulement le nom de l'activité trouvée, ansi que son coût.

### Menu principal

Créer un nouveau composant `Title.vue` ayant en tant que prop une chaine de caractère obligatoire appelée `content`. Ce composant affiche le texte `content` dans un titre HTML de niveau 1, ayant la classe CSS `title`, comportant le CSS suivant :
```css
transform: skew(-8deg);
font-family: "Sarpanch", sans-serif;
font-size: 64px;
margin: 0;
padding: 8px;
color: #ff8c00;
text-shadow: 4px 4px 2px #000
```

Intégrer ce titre dans les deux composants `RandomActivity.vue` et `SearchActivity.vue`, avec pour chacun un titre pertinent de votre choix.