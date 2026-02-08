# Probleme 4 : LES INTRUS (coefficient 4)

## Enonce

Parmi ces cinq nombres affiches sur des ecrans a sept segments (style calculatrice), trois se deduisent l'un de l'autre en les tournant (rotation) ou en les retournant (symetrie). Quels sont les deux intrus ?

Les cinq nombres sont :

```
15182    18152    28151    58121    58151
```

## Resolution

### Affichage a sept segments : rappel

Chaque chiffre est forme de 7 segments disposes ainsi :

```
 _a_
|   |
f   b
|_g_|
|   |
e   c
|_d_|
```

Les chiffres utilises dans ce probleme activent les segments suivants :
- **0** : a, b, c, d, e, f
- **1** : b, c
- **2** : a, b, d, e, g
- **5** : a, c, d, f, g
- **8** : a, b, c, d, e, f, g (tous)
- **9** : a, b, c, d, f, g

### Les trois transformations geometriques

#### 1. Rotation de 180 degres

On retourne physiquement l'afficheur. Les segments se transforment : a <-> d, b <-> e, c <-> f, g <-> g. On obtient :

| Chiffre original | Segments                | Apres rotation            | Chiffre obtenu |
|-------------------|-------------------------|---------------------------|----------------|
| 0                 | a, b, c, d, e, f       | d, e, f, a, b, c = memes  | **0**          |
| 1                 | b, c                   | e, f                      | **1**          |
| 2                 | a, b, d, e, g          | d, e, a, b, g = memes     | **2**          |
| 5                 | a, c, d, f, g          | d, f, a, c, g = memes     | **5**          |
| 8                 | tous                   | tous                      | **8**          |
| 6                 | a, c, d, e, f, g       | d, f, a, b, c, g          | **9**          |
| 9                 | a, b, c, d, f, g       | d, e, f, a, c, g          | **6**          |

**Regle** : on inverse l'ordre des chiffres, et chaque chiffre se transforme selon : 0->0, 1->1, 2->2, 5->5, 8->8, 6->9, 9->6.

#### 2. Symetrie verticale (miroir gauche-droite)

On place un miroir a droite (ou a gauche) de l'afficheur. Les segments se transforment : a -> a, b <-> f, c <-> e, d -> d, g -> g. On obtient :

| Chiffre original | Segments                | Apres miroir              | Chiffre obtenu |
|-------------------|-------------------------|---------------------------|----------------|
| 0                 | a, b, c, d, e, f       | a, f, e, d, c, b = memes  | **0**          |
| 1                 | b, c                   | f, e                      | **1**          |
| 2                 | a, b, d, e, g          | a, f, d, c, g             | **5**          |
| 5                 | a, c, d, f, g          | a, e, d, b, g             | **2**          |
| 8                 | tous                   | tous                      | **8**          |

**Regle** : on inverse l'ordre des chiffres, et chaque chiffre se transforme selon : 0->0, 1->1, 2<->5, 8->8.

#### 3. Symetrie horizontale (miroir haut-bas)

C'est la composee de la rotation 180 degres et du miroir gauche-droite. Les segments se transforment : a <-> d, b <-> c, e <-> f, g -> g. On obtient les memes correspondances entre chiffres (0->0, 1->1, 2<->5, 8->8), mais **l'ordre des chiffres est conserve** (pas d'inversion).

### Application aux cinq nombres

#### Rotation 180 degres (inverser l'ordre + transformer les chiffres)

| Nombre | Inverse  | Apres transformation | Present dans la liste ? |
|--------|----------|----------------------|--------------------------|
| 15182  | 28151    | 28151                | **Oui**                  |
| 18152  | 25181    | 25181                | Non                      |
| 28151  | 15182    | 15182                | **Oui** (confirme la paire) |
| 58121  | 12185    | 12185                | Non                      |
| 58151  | 15185    | 15185                | Non                      |

**Resultat** : 15182 et 28151 sont images l'un de l'autre par rotation 180 degres.

#### Symetrie verticale / miroir gauche-droite (inverser l'ordre + 2<->5)

| Nombre | Inverse  | Apres transformation (2<->5) | Present dans la liste ? |
|--------|----------|-------------------------------|--------------------------|
| 15182  | 28151    | 58121                         | **Oui**                  |
| 18152  | 25181    | 52181                         | Non                      |
| 28151  | 15182    | 12185                         | Non                      |
| 58121  | 12185    | 15182                         | **Oui** (confirme la paire) |
| 58151  | 15185    | 12182                         | Non                      |

**Resultat** : 15182 et 58121 sont images l'un de l'autre par miroir gauche-droite.

#### Symetrie horizontale / miroir haut-bas (meme ordre + 2<->5)

| Nombre | Apres transformation (2<->5, meme ordre) | Present dans la liste ? |
|--------|-------------------------------------------|--------------------------|
| 15182  | 12185                                     | Non                      |
| 18152  | 18125                                     | Non                      |
| 28151  | 58121                                     | **Oui**                  |
| 58121  | 28151                                     | **Oui** (confirme la paire) |
| 58151  | 28121                                     | Non                      |

**Resultat** : 28151 et 58121 sont images l'un de l'autre par miroir haut-bas.

### Le groupe de trois

Les trois nombres **15182**, **28151** et **58121** forment un groupe ou chacun se deduit des deux autres :

```
          rotation 180 degres
  15182  <--------------------->  28151
    |                                |
    |  miroir                miroir  |
    |  gauche-droite         haut-bas|
    |                                |
    v                                v
                  58121
```

- **15182** tourne de 180 degres donne **28151**
- **15182** retourne par miroir gauche-droite donne **58121**
- **28151** retourne par miroir haut-bas donne **58121**

Les deux autres nombres, **18152** et **58151**, ne produisent aucun des cinq nombres de la liste par rotation ni par symetrie. Ce sont les intrus.

## Reponse

**Les deux intrus sont 18152 et 58151.**

Les trois nombres 15182, 28151 et 58121 se deduisent les uns des autres par rotation de 180 degres et par symetrie (miroir).
