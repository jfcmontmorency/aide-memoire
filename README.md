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

## Manipulation du DOM (HTML)

### Modifier du texte

```javascript
// Avant : <p id="monParagraphe">Avant</p>
const p = document.getElementById("monParagraphe");
p.textContent = "Après";
// Après : <p id="monParagraphe">Après</p>
```

### Modifier du HTML (ajouter du code HTML à l’intérieur)

```javascript
// Avant : <div id="monDiv">Avant</div>
const div = document.getElementById("monDiv");
div.innerHTML = "<strong>Texte en gras</strong>";
// Après : <div id="monDiv"><strong>Texte en gras</strong></div>
```

### Ajouter un élément

```javascript
// Avant : <ul id="maListe"></ul>
const liste = document.getElementById("maListe");
const item = document.createElement("li");
item.textContent = "Nouvel élément";
liste.appendChild(item);
// Après : <ul id="maListe"><li>Nouvel élément</li></ul>
```

### Supprimer un élément

```javascript
// Avant : <p id="aSupprimer">Texte à enlever</p>
const aSupprimer = document.getElementById("aSupprimer");
aSupprimer.remove();
// Après : (le <p> a disparu du DOM)
```

### Ajouter un supprimer une classes CSS

```javascript
// Avant : <div id="monDiv" class="ancien"></div>
const bloc = document.getElementById("monDiv");
bloc.classList.add("actif");
bloc.classList.remove("ancien");
// Après : <div id="monDiv" class="actif"></div>

console.log(bloc.classList.contains("actif")); 
// Résultat : true
```

!!! info "Différences à connaître"

    - `textContent` → texte brut (inclut le texte caché)  
    - `innerText` → texte visible seulement  
    - `innerHTML` → contenu HTML interne (avec balises)  
    - `outerHTML` → l’élément complet (balises + contenu)  

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
