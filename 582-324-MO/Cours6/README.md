# Cours 6 - 29 septembre

## Ordre du jour 

- Pas de cours la semaine prochaine 
- Retour sur le PS2 
- Wooclap : https://app.wooclap.com/TRCTKC
- Bases JavaScript, la suite 
- Exercices 
- Devoir PS3.1 

## JavaScript

Boucles
> https://smnarnold.com/cours/javascript/boucle-for 

Sélecteurs et manipulation 
>https://smnarnold.com/cours/javascript/queryselector  
>https://smnarnold.com/cours/javascript/classlist 

Événements 
> https://smnarnold.com/cours/javascript/attribut-onclick 

Manipulation du DOM 
> https://smnarnold.com/cours/javascript/manipulation-des-contenus 

Bonne pratiques 
> https://smnarnold.com/cours/javascript/nommer-ses-variables  

Aide-mémoire 

## Exercices

## Devoir PS3.1 (Jeu v1.0)

Aperçu du résultat

### Consignes

Dans la fonction "goToChapter", là où vous affichez les informations du chapitre dans la console, vous devez utiliser les mêmes valeurs, mais au lieu de les afficher dans la console, elles seront affichées dans votre gabarit.

Pour ce faire, vous devrez modifier le titre de la page, la description, l'image et modifier les boutons. Toutes ces valeurs proviennent du même object «chapters» que vous avez créé dans le devoir PS2.

Pour les boutons, il faudra leur assigner un événement "click". Au clic d'un bouton, il faut appeler la fonction goToChapter() et passer en paramètre la clé du chapitre associé au bouton cliqué.

Concernant la twist. Vous aurez à ajouter une nouvelle variable booléenne. Soit  

```javascript
let twist = false;
```

Dans la fonction «goToChapter», lorsque le chapitre reçu en paramètre correspond au chapitre susceptible de modifier la twist (ex: le chapitre "maison" est le chapitre où on trouve la clé), vous devrez modifier la valeur de twist à «true». Ainsi, dans un chapitre final, on pourra récupérer cette valeur et décider en programmation le sort réservé au joueur.

Faites un commit de vos changement et poussez les sur votre compte GitHub.

À faire pour le prochain cours.

Remise officielle 19 octobre