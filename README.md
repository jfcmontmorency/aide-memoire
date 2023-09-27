# jfcmontmorency.github.io

# Aide mémoire

## Javascript

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
