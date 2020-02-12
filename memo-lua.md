# Mémo Lua

par *flashjaysan*

## Les tables

Lua ne propose qu'une seule structure de donnée appelée *table*. Celle-ci peut être utilisée de bien des manières et fournit de puissantes possibilités. Cela peut cependant provoquer une confusion dans l'esprit d'un débutant.

### Utiliser une table comme une structure de donnée

```lua
local structure = {}
structure.element_x = valeur_a
structure.element_y = valeur_b
structure.element_z = valeur_c
```

Vous pouvez également utiliser la notation entre crochets (moins pratique et source de confusion si vous n'êtes pas habitué aux tableaux) :

```lua
local structure = {}
structure["element_x"] = valeur_a
structure["element_y"] = valeur_b
structure["element_z"] = valeur_c
```

Vous pouvez également initialiser directement la table lors de sa création :

```lua
local structure = {element_x = valeur_a, element_y = valeur_b, element_z = valeur_c}
```

**Attention !** Pensez bien à donner un nom à chaque élément de la table et à l'initialiser avec une valeur. Si vous ne précisez pas de nom d'élément, vous créerez un tableau.

Pour accéder au contenu d'un élément de la table, utilisez le nom de la variable suivi d'un point et du nom de l'élément.

```lua
tableau.element_y == valeur_b
```

### Utiliser une table comme un tableau

En Lua, les tables peuvent être utilisées comme des tableaux.

```lua
local tableau = {}
tableau[1] = valeur_a
tableau[2] = valeur_b
tableau[3] = valeur_c
tableau[4] = valeur_d
```

Vous pouvez également initialiser directement la table lors de sa création :

```lua
local tableau = {valeur_a, valeur_b, valeur_c, valeur_d}
```

**Remarque :** En Lua, le premier élément d'un tableau porte l'indice `1` et non `0`.

Pour connaitre la taille du tableau, utilisez le signe `#` devant le nom de la variable.

```lua
#tableau == 4
```

Pour accéder au contenu d'une case du tableau, utilisez le nom de la variable suivi de l'indice (entre crochets) du tableau.

```lua
tableau[2] == valeur_b
```

**Attention :** Une table peut à la fois contenir des éléments représentés sous forme de tableau et des éléments représentés sous forme de structure de données. Vous pouvez même associer des fonctions aux éléments d'une table. Soyez donc prudent et raisonnable lorsque vous utilisez les tables.

```lua
local tableau = {}
tableau[1] = valeur_a
tableau[2] = valeur_b
tableau[3] = valeur_c
tableau[4] = valeur_d
tableau.element_x = valeur_e
tableau.element_y = valeur_f
tableau.element_z = valeur_g
tableau.affiche_bonjour = function ()
  print("Bonjour.")
end
```

### Utiliser une table comme un tableau à deux dimensions

Pour bien comprendre les tableaux à deux dimensions, nous allons voir trois façons différentes de définir un tableau à deux dimensions. Chaque méthode donne le même résultat. Un tableau à deux dimensions est simplement un tableau contenant lui-même des tableaux.

- Vous pouvez définir une table contenant elle-même une liste de tables initialisées avec des éléments.

```lua
local tableau_2d = {
    {valeur_a, valeur_b, valeur_c},
    {valeur_d, valeur_e, valeur_f},
    {valeur_g, valeur_h, valeur_i},
    {valeur_j, valeur_k, valeur_l}
}
```

- Vous pouvez également définir une table vide pour représenter un tableau englobant. Créez ensuite une table initialisée avec des élements pour chaque case du tableau englobant.

```lua
local tableau_2d = {}
tableau_2d[1] = {valeur_a, valeur_b, valeur_c}
tableau_2d[2] = {valeur_d, valeur_e, valeur_f}
tableau_2d[3] = {valeur_g, valeur_h, valeur_i}
tableau_2d[4] = {valeur_j, valeur_k, valeur_l}
```

- Enfin, vous pouvez définir une table vide pour représenter un tableau englobant. Puis associer à chaque case de ce tableau une table vide pour représenter un tableau interne. Et enfin affecter une valeur à chaque case de chaque tableau interne.

```lua
local tableau_2d = {}
tableau_2d[1] = {}
tableau_2d[1][1] = valeur_a
tableau_2d[1][2] = valeur_b
tableau_2d[1][3] = valeur_c
tableau_2d[2] = {}
tableau_2d[2][1] = valeur_d
tableau_2d[2][2] = valeur_e
tableau_2d[2][3] = valeur_f
tableau_2d[3] = {}
tableau_2d[3][1] = valeur_g
tableau_2d[3][2] = valeur_h
tableau_2d[3][3] = valeur_i
tableau_2d[4] = {}
tableau_2d[4][1] = valeur_j
tableau_2d[4][2] = valeur_k
tableau_2d[4][3] = valeur_l
```

Pour connaitre la taille du tableau englobant, utilisez le signe `#` devant le nom de la variable.

```lua
#tableau_2d == 4
```

Pour connaître la taille d'un tableau interne, utilisez le sign `#` devant le nom de la variable suivi de l'indice (entre crochets) du tableau interne.

```lua
#tableau_2d[2] == 3
```

Pour accéder au contenu d'une case du tableau, utilisez le nom de la variable suivi de l'indice (entre crochets) du tableau interne et de l'indice (entre crochets) de l'élément du tableau interne.

```lua
tableau_2d[2][3] == valeur_f
```

### Les tables sont des références

Vous devez absolument garder à l'esprit que, contrairement aux types de base de Lua, les tables sont des références.

Si vous affectez à une nouvelle variable une table existante, cette dernière n'est pas copiée. En réalité, vous donnez à la nouvelle variable une référence à la table d'origine.

```lua
local point = {x = 30, y = 70} -- création d'une table point
local nouveau_point = point -- affectation à nouveau_point de la référence à la table point
nouveau_point.x = 10 -- modification de l'élément x de nouveau_point
point.x ~= 30 -- mais cela se répercute sur point
```

Si vous passez une table à une fonction, la fonction ne prend pas une copie de la table mais travail sur une référence à la table. Si vous modifiez la table dans la fonction, c'est la table d'origine que vous modifiez.

```lua
local point = {x = 30, y = 70} -- création d'une table point

function change_x(some_point)
  some_point.x = 10 -- modifie l'élément x de la table point
end
```

Pour résoudre ce genre de problème, il faut copier en profondeur les tables lorsque vous souhaitez vraiment créer une nouvelle copie. Consultez le [wiki de Lua](http://lua-users.org/wiki/CopyTable) pour plus d'informations.

