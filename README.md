# Aide-mémoire

## JavaScript

### Variables

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

### Boucles

Boucle for : La boucle for est l'une des boucles les plus couramment utilisées. Elle permet de spécifier explicitement la condition de continuation et d'itérer sur un bloc de code un nombre prédéterminé de fois.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

Boucle while : La boucle while itère tant qu'une condition donnée est vraie. Elle est utilisée lorsque le nombre d'itérations n'est pas connu à l'avance.

```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

Boucle do...while : La boucle do...while est similaire à while, mais elle garantit au moins une exécution du bloc de code, même si la condition est fausse dès le départ.

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

Boucle for...in : La boucle for...in itère à travers les propriétés énumérables d'un objet. Elle est principalement utilisée pour parcourir des objets.

```javascript
const obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
  console.log(key, obj[key]);
}
```

Boucle for...of : La boucle for...of itère sur les éléments d'une structure de données itérable, telle qu'un tableau (array), une chaîne de caractères (string), ou un ensemble (set).

```javascript
const arr = [1, 2, 3];
for (const element of arr) {
  console.log(element);
}
```

Boucle forEach() : Cette méthode est spécifique aux tableaux (Array) et permet d'itérer sur chaque élément du tableau en utilisant une fonction de rappel.

```javascript
const arr = [1, 2, 3];
arr.forEach((element) => {
  console.log(element);
});
```
