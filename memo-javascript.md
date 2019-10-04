# Mémo JavaScript

par *flashjaysan*

## Commentaires

Sur une seule ligne ou sur plusieurs lignes :

```javascript
// ceci est un commentaire sur une seule ligne
/* ceci est un
commentaire sur
plusieurs lignes. */
```

## Afficher un texte dans la console

```javascript
console.log(texte);
console.log(valeur_1, valeur_2, ..., valeur_n);
```

## Booléens

Les booléens ne peuvent prendre que deux valeurs :

```javascript
true;
false;
```

### Opérateurs sur les booléens

`&&` et logique
`||` ou logique
`!` non logique

## Nombres

Les entiers et nombres à virgule flottantes sont du type `number` :

```javascript
0;
10;
-1;
0.5;
```

La fonction `Number` convertit une donnée en nombre :

```javascript
un_nombre = Number(value)
```

### Opérateur sur les nombres

`+` addition
`-` soustraction
`*` multiplication
`/` division
`%` modulo ou reste

`===` égalité
`!==` différence
`<` inférieur à
`<=` inférieur ou égal à
`>` supérieur à
`>=` supérieur ou égal à

## Chaînes

Les chaînes de caractères s'écrivent entre guillemets simples ou doubles :

```javascript
'Une chaine.'
"Une autre chaine."
```

Encadrer une chaine d'un *backtick* permet d'y placer des expressions de la forme :

```javascript
`Une chaine ${expression}.` 
```

La fonction `String` convertit une donnée en chaîne :

```javascript
une_chaine = String(value)
```

# Déclarer une variable

```javascript
let nom_de_variable;
```

Une variable juste déclaré possède la valeur `undefined`.

# Déclarer une constante

```javascript
const PI = 3.14;
```
## Instruction conditionnelle

```javascript
if (condition_1) {
    // instructions_1
} else if (condition_2) {
    // instructions_2
} else {
    // instructions_3
}
```

```javascript
switch (expression) {
  case litteral_1:
    // instructions_1
    break;
  case litteral_2:
    // instructions_2
    break;
  default:
    // instructions par défaut
}

```

## Boucles

```javascript
while (condition) {
    // instructions
}
```

```javascript
for (let i = 0; i < max; i++) {
    // instructions
}
```

