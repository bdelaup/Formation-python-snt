# Les types 
## Introduction 

Les types sont des modèles algorithmiques de représentation des données. Ils sont indépendant des langages de programmation.

!!! definition "Définition : type théorique"
    Un type théorique est défini par :

    - un nom
    - les opérations qu'il supporte

Les langages de programmation définissent des types de données. Ils sont dérivé des types théorique mais leur implémentation s'en éloigne et/ou apportent des limitations.
Les langages s'éloignent des types théoriques notamment pour "coller" à la "philosophie" du langage : pour facilité son écriture il faut parfois interdire des usages.
Les limitations s'explique notamment par le fait que les programme s'exécute sur des machines possédant des limitations physiques. Chaque langage gère ces limites de sa propre façon.

Les langages gère de façon différentes le typage dans les programmes.

!!! example
    Python est un langage dont le typage est dynamique et implicite.

    ``` py title="En python" linenums="1"
    valeur = True # valeur est alors dynamiquement typé bool et initialisé à True
   
    valeur = 42 # valeur est alors automatique typé int et initialisé à 42.

    ```

    C++ est un langage dont le typage est statique et explicite.

    ``` c++ title="En C++" linenums="1"
    bool valeur = true; // valeur est statiquement typé bool et initialisé à true.    
    ...
    valeur = 42; // Impossible, il n'est pas possible de changer 
                 // dynamiquement le type d'une variable. 
                 // Il faudra en créer une autre.
    ```

## Types de bases

Parmi les types de bases on retiendra :

- les nombres entiers
- les nombres réels
- les booléen
- les chaînes de caractères


| Type théorique | Types python | Opérations                                                                 | Exemple python                     |
| -------------- | ------------ | -------------------------------------------------------------------------- | ---------------------------------- |
| Entiers        | `int`        | Opérations arithmétiques (+,-,/,* ,//,%) et logique (==, !=, >, <, <=, >=) | `a = 5*4/2`                        |
| Réels          | `float`      | Opérations arithmétiques (+,-,/,* ) et logique (==, !=, >, <, <=, >=)      | `b = 5/3x4.2`                      |
| Booléen        | `bool`       | Opérations booléenne (NOT, OR, AND) et logiques (==, !=)                   | `c = True AND NOT(False)== FALSE ` |
| Chaîne         | `str`        | Concaténation et opérations logiques (==, !=)                              | `d = "Bon"+"jour"`                 |


## Types construits
### Introduction
Les types construits sont des types qui agrègent plus plusieurs données. Ces données peuvent être d'un type de base, mais également d'un type construit.
Nous verrons les listes `list`, les dictionnaires `dict`, les tuples `tuple`.

Il existe beaucoup d'autres types natifs en python : `set`, `range`, `bytes`, `bytearray` ...

### Les **tuple** *(p-uplets)*

!!! definition
    Un `tuple` est un ensemble de valeurs de types **identiques ou différents**. Chaque élément est **accessible par sa position** dans le `tuple`.

**En python**

Le type `tuple` est souvent le type retenu pour travailler avec des éléments du type théorique `p-uplet`.
Attention, en python le `tuple` est immuable : une fois défini il est impossible de le modifier. 
 
Dans le cas ou il serait nécessaire de modifier une valeur, il s'agira de créer un nouveau `tuple` ou d'utiliser le type `list`.


``` py title="Exemple de tuple en python" linenums="1"
personnage = ("Haddock", "Alcoolique", 45) # Nom, métier, age
age = personnage[2]
personnage[1] = "Sobre" # Impossible en python,
                        # le capitaine reste alcoolique...    
```

!!! note
    Les indices des tuple commencent à 0. 
    
    Le tuple est reconnaissable par ses **parenthèses ( )**.

    ```
                perso[0]      perso[1]       perso[2]
                   |              |             |
    perso = (   "Haddock",     "Capitaine",    45)
    ```



### Les dictionnaire **dict** *(p-uplet nommés)*

!!! definition
    Un `dict` est un ensemble de valeurs de **types identiques ou différents**. Chaque élément est associé à une **clé par laquelle on accède à la valeur**.
    
    Autrement dit, un `dict` est un ensemble de couple "clé -> valeur".
    
    Les élément d'un `dict` ne sont pas ordonnés.

**En python**

Le type dictionnaire `dict` est le plus proche du type théorique p-uplet nommé.

``` py linenums="1" title="Exemple de dictionnaire en Python"

personnage = {"nom" : "Haddock", "metier" : "Alcoolique", "age" : 45}
age = personnage["age"]
personnage["metier"] = "capitaine" # Avec les dictionnaires en python,
                                    # le capitaine devient sobre ...
```

!!! note
    On accède à une valeur grâce à sa clé. 
    
    Le tuple est reconnaissable par ses **accolades { }**.

    En python la clé permettant d'accéder à une valeur doit être **immuable** : `int`, `float`, `tuple`, `str`. 

    ```
                    perso["nom"]         perso["metier"]    perso["age"]
                        |                        |              |
    perso = {"nom" : "Haddock", "metier" : "capitaine", "age" : 45}
    ```


### Les listes **list** *(tableau)*

!!! definition
    Les éléments d'une `list` peuvent être de même type ou de type différent    
    Une `list` possède une taille qui correspond au nombre d'éléments présents dans la `list`.
    Chaque élément est **accessible par un indice** qui correspond à son emplacement dans la `list`.
       

**En python**

Le type `list` est ce qui se rapproche le plus du tableau théorique en python. Le type `list` de python dépasse largement la définition théorique du tableau où les éléments y sont de même type par exemple.


``` py linenums="1" title="Exemple de list en Python"

# Création d'une list de 3 chaîne vide
taille_tab = 3
top3_prenom_fille = [""] * taille_tab     

# ou, si on veut une list initialisé
top3_prenom_garçon = ["Jo", "Jack", "William"]  

# ou une list vide
l_vide = []                                     

garcon =  top3_prenom_garcon[1]   # garcon contiendra "Jack"
top3_prenom_fille[0] = "Barbie" # top3_prenom_fille -> ["Barbie", "Emma", "Louise"]
top3_prenom_garçon[3] = "Awrell" # INTERDIT !!! la liste ne contient que 3 éléments

taille_tableau = len(top3_prenom_garçon) # taille_tableau -> 3
```

!!! note
    Les indices d'une `list` commencent à 0. 
    
    La `list` est reconnaissable par ses **crochets [ ]**.

    La fonction `len()` permet de connaître le nombre d'élément dans une `list`

    ```
                perso[0]      perso[1]       perso[2]
                   |              |             |
    perso = [   "Haddock",     "Capitaine",    45]
    ```

!!! note
    Il est possible d'ajouter des éléments à une `list` grace à la méthode `append()`

    ``` py linenums="1" title="Append"
    l = []
    l.append("a")
    l.append("bb")
    l.append(42)
    ```

    La list (comme le tuple) est itérable. On peut parcourir une list de la façon suivante : 

    === "Code"
        ``` py linenums="1" title="Itération sur les éléments d'une list"
        for elt in range(l):
            print(elt)
        ```

    === "Affichage"
        ```
        a
        bb
        42
        ```

## A retenir

Python est un langage dont le typage est dynamique et implicite : il est décidé automatiquement au moment de l'affectation par l’interpréteur. 

Il est possible de connaître le type d'un élément :
=== "Code"
    ``` py linenums="1"
    a = "abc"
    b = 1
    c = True
    print(type(a), type(b), type(c))
    ```
=== "Affichage"
    ```
    <class 'str'> <class 'int'> <class 'bool'>
    ```

**Type de base**

| Type théorique | Types python | Opérations                                                                 | Exemple python                     |
| -------------- | ------------ | -------------------------------------------------------------------------- | ---------------------------------- |
| Entiers        | `int`        | Opérations arithmétiques (+,-,/,* ,//,%) et logique (==, !=, >, <, <=, >=) | `a = 5*4/2`                        |
| Réels          | `float`      | Opérations arithmétiques (+,-,/,* ) et logique (==, !=, >, <, <=, >=)      | `b = 5/3x4.2`                      |
| Booléen        | `bool`       | Opérations booléenne (NOT, OR, AND) et logiques (==, !=)                   | `c = True AND NOT(False)== FALSE ` |
| Chaîne         | `str`        | Concaténation et opérations logiques (==, !=)                              | `d = "Bon"+"jour"`                 |

**Type construit**

| #            | Type python | Initialisation                                            |
| ------------ | ----------- | --------------------------------------------------------- |
| **Tuple**        | `tuple`       | `val = ("haddock", "capitaine", 42)`                      |
| **Dictionnaire** | `dict`        | `val = {"nom":"haddock", "metier":"capitaine", age : 42}` |
| **Liste**        | `list`        | `val = ["haddock", "capitaine", 42]`                      |

| #            | Mise à jour       | Accès au métier          | Ajouter un élément   |
| ------------ | ----------------- | ------------------------ | -------------------- |
| **Tuple**        | *Impossible*        | `valeur = val[1]`        | *Impossible*           |
| **Dictionnaire** | `val["age"] = 51` | `valeur = val["metier"]` | `val["barbu"] =True` |
| **Liste**        | `val[2] = 51`     | `valeur = val[1]`        | `val.append(True)`   |

**Les *list***

Il est possible d'itérer sur les éléments d'une `list` :
=== "Code"
    ```py linenums="1"
    ma_liste = ["a", "bb", 42]
    for elt in ma_liste:
        print(elt)
    ```
=== "Affichage"
    ```
    a
    bb
    42
    ```

Il est possible de connaître le nombre d'élément dans une `liste` :
=== "Code"
    ```py linenums="1"
    ma_liste = ["a", "bb", 42]
    print("Taille : ", len(ma_liste))
    ```
=== "Affichage"
    affichera `3`

Il est possible de créer un "tableau" de valeur pour itérer sur une `list`.
=== "Code"
    ```py linenums="1"
    ma_liste = ["a", "bb", 42]
    for i in range(3):
        print(i, ma_liste[i])
    ```
=== "Affichage"
    ```
    0 a
    1 bb
    2 42
    ```

## La gestion de la mémoire par python

Python (et Micropython) gère la mémoire à l'aide d'un **ramasse-miettes** (*garbage collector* en Anglais). 
En python, les variables contienne l'adresse des objets vers lesquels ils pointent. Chaque objet possède un compteur de référence. Lorsque l'objet est pointé par une nouvelle variable, le compteur est incrémenté, lorsqu'une variable est supprimé, le compteur est décrémenté. 

Lorsque l'interpréteur est inactif, c'est à dire pendant les appels à `sleep()` par exemple, la machine virtuelle  (ou Virtual Machine **VM**) visite toutes les objets et lorsqu'il trouve un objet dont le compteur de référence vaut 0, il libère la mémoire utilisée pour stocker l'objet.

En cas de problème de saturation de la mémoire, on peut forcer la VM python à ramasser les miettes en appelant la fonction `gc_collect()`
