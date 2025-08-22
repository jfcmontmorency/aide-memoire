# Aide-mémoire JavaScript

![](./assets/images/split1.jpg)

## Variables

Une **variable** c'est comme une boîte dans laquelle on range une valeur.

- `var` : (ancienne façon) La variable existe partout dans la fonction
- `let` : La variable n’existe **que dans le bloc** où elle est créée. Plus sécuritaire.  
- `const` : La variable agit comme let, mais ne peut être remplacée par une autre valeur dans le code.

```javascript
// Exemple avec var
function exempleVar() {
  if (true) {
    var message = "Hello, var!";
  }
  console.log(message); // fonctionne malgré tout
}

// Exemple avec let
function exempleLet() {
  if (true) {
    let message = "Hello, let!";
  }
  // console.log(message); // Erreur ! message n’existe plus
}
```

![](./assets/images/split2.jpg)

## Sélecteurs

Les sélecteurs servent à **sélectionner un élément du HTML** pour le modifier avec JavaScript.

Voici un exemple de code HTML de départ :

```html
<div id="parent">
  <p class="texte">Blade</p>
  <p class="texte">Runner</p>
  <span name="auteur">Ridley Scott</span>
</div>
```

### `getElementById("id")`

Sélectionne **un seul élément** avec l’`id` indiqué.

```javascript
const parent = document.getElementById("parent");
console.log(parent); 
// Résultat : <div id="parent">...</div>
```

### `getElementsByClassName("classe")`

Sélectionne **tous les éléments qui ont la même classe**. Retourne une liste (HTMLCollection) !

```javascript
const textes = document.getElementsByClassName("texte");
console.log(textes[0]);
// Résultat : <p class="texte">Blade</p>
console.log(textes[1]);
// Résultat : <p class="texte">Runner</p>
```

### `querySelector(".classe")`

Sélectionne **le premier élément** qui correspond au sélecteur CSS.

```javascript
const texte = document.querySelector(".texte");
console.log(texte); 
// Résultat : <p class="texte">Blade</p>
```

### `querySelectorAll(".classe")`

Sélectionne **tous les éléments** qui correspondent au sélecteur CSS. Retourne une liste (NodeList) !

```javascript
const textes = document.querySelectorAll(".texte");
console.log(textes[0]); 
// Résultat : <p class="texte">Blade</p>
console.log(textes[1]); 
// Résultat : <p class="texte">Runner</p>
```

### `children`
Sélectionne les **enfants directs** d’un élément parent. Retourne une liste (HTMLCollection) !

```javascript
const parent = document.getElementById("parent");
const enfants = parent.children; 
console.log(enfants[0]); 
// Résultat : <p class="texte">Blade</p>
console.log(enfants[1]); 
// Résultat : <p class="texte">Runner</p>
```


![](./assets/images/split4.jpg)

## 3. Boucles

Une boucle sert à **répéter une action** plusieurs fois.

### Boucle for

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}

// Résultat :
// 0
// 1
// 2
// 3
// 4
```

### Boucle for...of (tableaux, chaînes, etc.)

```javascript
const fruits = ["🍎", "🍌", "🍇"];
for (let fruit of fruits) {
  console.log(fruit);
}

// Résultat :
// 🍎
// 🍌
// 🍇
```

### forEach (méthode des tableaux)

```javascript
const fruits = ["🍎", "🍌", "🍇"];
fruits.forEach((fruit) => console.log(fruit));

// Résultat :
// 🍎
// 🍌
// 🍇
```

Les boucles [while](https://www.w3schools.com/js/js_loop_while.asp) fonctionnent aussi très bien, mais elles sont généralement moins utilisées.

![](./assets/images/split5.jpg)

## Manipulation du DOM

### textContent : Changer le contenu textuel d'un élément

```javascript
// Avant : <p id="monParagraphe">Texte avant la modification</p>
const paragraphe = document.getElementById("monParagraphe");
paragraphe.textContent = "Texte après la modification";
// Après : <p id="monParagraphe">Texte après la modification</p>
```

### innerHTML : Changer le contenu HTML d'un élément 

```javascript
// Avant : <div id="monDiv">Contenu avant la modification</div>
const div = document.getElementById("monDiv");
div.innerHTML = "<p>Contenu après la modification</p>";
// Après : <div id="monDiv"><p>Contenu après la modification</p></div>
```

### insertAdjacentText: Ajouter du contenu avec insertAdjacentText

#### Exemples

```javascript
// Avant : <div id="monElement">Texte existant</div>
var element = document.getElementById('monElement');
element.insertAdjacentText('beforebegin', 'Texte avant l’élément');
// Après : 
// Texte avant l'élément
// <div id="monElement">Texte existant</div>
```

```javascript
// Avant : <div id="monElement">Texte existant</div>
var element = document.getElementById('monElement');
element.insertAdjacentText('afterbegin', 'Texte avant l’élément');
// Après : 
// <div id="monElement">Texte avant l'élémentTexte existant</div>
```

- beforebegin : À l'extérieur de l'element, avant
- afterbegin : À l'intérieur de l'element, avant son premier enfant ou texte.
- beforeend : À l'intérieur de l'element, après son dernier enfant ou texte.
- afterend : À l'extérieur de l'element, après

### Ajouter un nouvel élément

```javascript
// Avant : <ul id="maListe"></ul>
const liste = document.getElementById("maListe");
const nouvelElement = document.createElement("li");
nouvelElement.textContent = "Nouvel élément ajouté";
liste.appendChild(nouvelElement);
// Après : <ul id="maListe"><li>Nouvel élément ajouté</li></ul>
```

### Supprimer un élément 

```javascript
// Avant : <p id="aSupprimer">Texte à supprimer</p>
const elementASupprimer = document.getElementById("aSupprimer");
elementASupprimer.parentNode.removeChild(elementASupprimer);
// Après : (l'élément <p> est supprimé du DOM)
```

### Supprimer des enfants

```javascript
// Avant : <div id="boutons"><button>Bouton1</button><button>Bouton2</button><button>Bouton3</button></div>
const parent = document.getElementById("boutons");
while (parent.firstChild) {
  parent.removeChild(parent.firstChild);
}
// Après : <div id="boutons"></div>
```

### Supprimer tout sous un parent 

```javascript
// Avant : <div id="boutons"><button>Bouton1</button><button>Bouton2</button><button>Bouton3</button></div>
const parent = document.getElementById("boutons");
parent.innerHTML = '';
// Après : <div id="boutons"></div>
```

### Modifier les attributs d'un élément

```javascript
// Avant : <img id="monImage" src="image.jpg" alt="Image">
const image = document.getElementById("monImage");
image.src = "nouvelle-image.jpg";
image.alt = "Nouvelle image";
// Après : <img id="monImage" src="nouvelle-image.jpg" alt="Nouvelle image">
```

### Ajouter, supprimer ou questionner la présence de classe CSS

```javascript
// Avant : <div id="monDiv" class="ancienneClasse"></div>
const div = document.getElementById("monDiv");
div.classList.remove("ancienneClasse");
div.classList.add("nouvelleClasse");
// Après : <div id="monDiv" class="nouvelleClasse"></div>

const monBool = div.classList.contains("nouvelleClasse");
// retourne : true
```

![](./assets/images/split3.jpg)

## Événements 

### addEventListener

```javascript
function clicHandler() {
  console.log('Ça fonctionne! 🔥')
}

// <button id="monBouton">Cliquez-moi</button>
const bouton = document.getElementById("monBouton");
bouton.addEventListener("click", clicHandler);
```

### removeEventListener

Pour retirer un EventListener il faut spécifier la fonction.

```javascript
bouton.removeEventListener("click", clicHandler);
```

## This

`this` est un mot-clé en JavaScript qui fait référence à l'objet actuel sur lequel une fonction est appelée. Son comportement dépend du contexte d'appel.

```javascript
//<div id="monElement">Cliquez sur moi !</div>
const monElement = document.getElementById('monElement');
monElement.addEventListener('click', function() {
  const id = this.id; // 'monElement'
  this.classList.add('highlight'); // Ajoute une classe "highlight" à l'élément
});
```
