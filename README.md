# Aide-mémoire JavaScript

![](./assets/images/split1.jpg)

## Variables

### Différence entre var et let

```javascript
// Utilisation de var
function exempleVar() {
  if (true) {
    var message = "Hello, var!";
  }

  console.log(message); // "Hello, var!" est affiché, même à l'extérieur du bloc if
}

exempleVar();

// Utilisation de let
function exempleLet() {
  if (true) {
    let message = "Hello, let!";
  }

  // console.log(message); // Cela générera une "ReferenceError" car message n'est pas défini ici
}

// exempleLet();
```

```javascript
// Réaffectation de la variable
function exempleReaffectation() {
  var x = 10;
  var x = 20; // La réaffectation avec "var" est autorisée

  console.log(x); // Affiche 20
}

exempleReaffectation();

// Réaffectation de la variable avec let
function exemplePasReaffectation() {
  let y = 10;
  // let y = 20; // Cela générera une "SyntaxError" car vous ne pouvez pas réaffecter une variable "let" dans la même portée
}

// exemplePasReaffectation();
```
![](./assets/images/split2.jpg)

## Sélecteurs

### getElementById

```javascript
// <div id="monElement"></div>
const element = document.getElementById("monElement");
// Type : Element
```

### getElementsByClassName

```javascript
// <div class="maClasse"></div>
// <div class="maClasse"></div>
const elements = document.getElementsByClassName("maClasse");
// Type : HTMLCollection
```

### getElementsByTagName

```javascript
// <p>Paragraphe 1</p>
// <p>Paragraphe 2</p>
// <p>Paragraphe 3</p>
const paragraphs = document.getElementsByTagName("p");
// Type : HTMLCollection
```

### querySelector

```javascript
// <div class="maClasse"></div> <- Sélectionné
// <div class="maClasse"></div> <- Non sélectionné
const element = document.querySelector(".maClasse");
// Type : Element
```

### querySelectorAll

```javascript
// <div class="maClasse"></div>
// <div class="maClasse"></div>
const elements = document.querySelectorAll(".maClasse");
// Type : NodeList
```

### getElementsByName

```javascript
// <input type="text" name="monNom" value="Input avec nom">
const element = document.getElementsByName("monNom")[0];
// Type : NodeList (utilisé principalement pour les éléments de formulaire)
```

### children

```javascript
// <div id="parent">
//   <div>Enfant 1</div>
//   <div>Enfant 2</div>
// </div>
const parentElement = document.getElementById("parent");
const enfants = parentElement.children;
// Type : HTMLCollection
```

![](./assets/images/split4.jpg)

## Boucles

### Boucle for
La boucle for est l'une des boucles les plus couramment utilisées. Elle permet de spécifier explicitement la condition de continuation et d'itérer sur un bloc de code un nombre prédéterminé de fois.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

### Boucle while
La boucle while itère tant qu'une condition donnée est vraie. Elle est utilisée lorsque le nombre d'itérations n'est pas connu à l'avance.

```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

### Boucle do...while
La boucle do...while est similaire à while, mais elle garantit au moins une exécution du bloc de code, même si la condition est fausse dès le départ.

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

### Boucle for...in
La boucle for...in itère à travers les propriétés énumérables d'un objet. Elle est principalement utilisée pour parcourir des objets.

```javascript
const obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
  console.log(key, obj[key]);
}
```

### Boucle for...of
La boucle for...of itère sur les éléments d'une structure de données itérable, telle qu'un tableau (array), une chaîne de caractères (string), ou un ensemble (set).

```javascript
const arr = [1, 2, 3];
for (let element of arr) {
  console.log(element);
}
```

### Boucle forEach()
Cette méthode est spécifique aux tableaux (Array) et permet d'itérer sur chaque élément du tableau en utilisant une fonction de rappel.

```javascript
const arr = [1, 2, 3];
arr.forEach((element) => {
  console.log(element);
});
```

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

* beforebegin : Avant le elementlui-même.
* afterbegin : Juste à l'intérieur du element, avant son premier enfant.
* beforeend : Juste à l'intérieur du element, après son dernier enfant.
* afterend : Après le elementlui-même.

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
