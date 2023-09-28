# Aide-mémoire

## JavaScript

### Variables

#### Différence entre var et let

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

### Sélecteurs

#### getElementById

```javascript
// <div id="monElement"></div>
const element = document.getElementById("monElement");
// Type : string
```

#### getElementsByClassName

```javascript
// <div class="maClasse"></div>
// <div class="maClasse"></div>
const elements = document.getElementsByClassName("maClasse");
// Type : HTMLCollection
```

#### getElementsByTagName

```javascript
// <p>Paragraphe 1</p>
// <p>Paragraphe 2</p>
// <p>Paragraphe 3</p>
const paragraphs = document.getElementsByTagName("p");
// Type : HTMLCollection
```

#### querySelector

```javascript
// <div class="maClasse"></div>
const element = document.querySelector(".maClasse");
// Type : Element
```

#### querySelectorAll

```javascript
// <div class="maClasse"></div>
// <div class="maClasse"></div>
const elements = document.querySelectorAll(".maClasse");
// Type : NodeList
```

#### getElementsByName

```javascript
// <input type="text" name="monNom" value="Input avec nom">
const element = document.getElementsByName("monNom")[0];
// Type : NodeList (utilisé principalement pour les éléments de formulaire)
```

#### querySelector

```javascript
// <div id="monElement"></div>
const element = document.querySelector("#monElement");
// Type : Element
```

#### querySelectorAll

```javascript
// <div data-custom="valeur"></div>
const elements = document.querySelectorAll("[data-custom]");
// Type : NodeList
```

#### 

```javascript children
// <div id="parent">
//   <div>Enfant 1</div>
//   <div>Enfant 2</div>
// </div>
const parentElement = document.getElementById("parent");
const enfants = parentElement.children;
// Type : HTMLCollection
```

### Élément(s) du DOM

#### HTMLCollection
Les HTMLCollection sont similaires aux tableaux (arrays) mais ne possèdent pas toutes les méthodes de tableau. Vous pouvez accéder à leurs éléments en utilisant l'index comme vous le feriez avec un tableau.

```javascript
const elements = document.getElementsByClassName("maClasse");
const premierElement = elements[0]; // Accès au premier élément
const deuxiemeElement = elements[1]; // Accès au deuxième élément, etc.
```

#### NodeList
Les NodeList sont également similaires aux tableaux, et vous pouvez accéder à leurs éléments de la même manière.

```javascript
const elements = document.querySelectorAll(".maClasse");
const premierElement = elements[0];
const deuxiemeElement = elements[1];
```

#### Element
Les Element représentent un seul élément du DOM, et pour recueillir des informations, vous pouvez utiliser les propriétés et méthodes spécifiques à cet élément. Par exemple, vous pouvez utiliser textContent pour obtenir le contenu textuel de l'élément.

```javascript
const element = document.getElementById("monElement");
const contenuTextuel = element.textContent;
```

### Boucles

#### Boucle for
La boucle for est l'une des boucles les plus couramment utilisées. Elle permet de spécifier explicitement la condition de continuation et d'itérer sur un bloc de code un nombre prédéterminé de fois.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

#### Boucle while
La boucle while itère tant qu'une condition donnée est vraie. Elle est utilisée lorsque le nombre d'itérations n'est pas connu à l'avance.

```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

#### Boucle do...while
La boucle do...while est similaire à while, mais elle garantit au moins une exécution du bloc de code, même si la condition est fausse dès le départ.

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

#### Boucle for...in
La boucle for...in itère à travers les propriétés énumérables d'un objet. Elle est principalement utilisée pour parcourir des objets.

```javascript
const obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
  console.log(key, obj[key]);
}
```

#### Boucle for...of
La boucle for...of itère sur les éléments d'une structure de données itérable, telle qu'un tableau (array), une chaîne de caractères (string), ou un ensemble (set).

```javascript
const arr = [1, 2, 3];
for (let element of arr) {
  console.log(element);
}
```

#### Boucle forEach()
Cette méthode est spécifique aux tableaux (Array) et permet d'itérer sur chaque élément du tableau en utilisant une fonction de rappel.

```javascript
const arr = [1, 2, 3];
arr.forEach((element) => {
  console.log(element);
});
```

### Manipulation du DOM

#### Changer le contenu textuel d'un élément

```javascript
// Avant : <p id="monParagraphe">Texte avant la modification</p>
const paragraphe = document.getElementById("monParagraphe");
paragraphe.textContent = "Texte après la modification";
// Après : <p id="monParagraphe">Texte après la modification</p>
```

#### Modifier le contenu HTML d'un élément 

```javascript
// Avant : <div id="monDiv">Contenu avant la modification</div>
const div = document.getElementById("monDiv");
div.innerHTML = "<p>Contenu après la modification</p>";
// Après : <div id="monDiv"><p>Contenu après la modification</p></div>
```

#### Ajouter un nouvel élément

```javascript
// Avant : <ul id="maListe"></ul>
const liste = document.getElementById("maListe");
const nouvelElement = document.createElement("li");
nouvelElement.textContent = "Nouvel élément ajouté";
liste.appendChild(nouvelElement);
// Après : <ul id="maListe"><li>Nouvel élément ajouté</li></ul>
```

#### Supprimer un élément 

```javascript
// Avant : <p id="aSupprimer">Texte à supprimer</p>
const elementASupprimer = document.getElementById("aSupprimer");
elementASupprimer.parentNode.removeChild(elementASupprimer);
// Après : (l'élément <p> est supprimé du DOM)
```

#### Modifier les attributs d'un élément

```javascript
// Avant : <img id="monImage" src="image.jpg" alt="Image">
const image = document.getElementById("monImage");
image.src = "nouvelle-image.jpg";
image.alt = "Nouvelle image";
// Après : <img id="monImage" src="nouvelle-image.jpg" alt="Nouvelle image">
```

#### Ajouter ou supprimer des classes CSS

```javascript
// Avant : <div id="monDiv" class="ancienneClasse"></div>
const div = document.getElementById("monDiv");
div.classList.remove("ancienneClasse");
div.classList.add("nouvelleClasse");
// Après : <div id="monDiv" class="nouvelleClasse"></div>
```
