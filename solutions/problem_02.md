# Probleme 2 : LE CHAPEAU DE L'ANNEE (coefficient 2)

## Enonce

En additionnant les trois nombres qui entourent chaque triangle, on doit toujours trouver 26.
Placez les nombres 7, 8, 9 et 11 dans les cases vides.

## Analyse du diagramme

Le chapeau est compose de 3 triangles relies en chaine, partageant des sommets :

```
  [12] --- [A] --- [6] --- [B] --- [C] --- [D] --- [10]
     \      /         \      /         \      /
      \    /           \    /           \    /
       \  /             \  /             \  /
       Triangle 1     Triangle 2      Triangle 3
```

- **Triangle 1** : sommets 12, A, 6
- **Triangle 2** : sommets 6, B, C
- **Triangle 3** : sommets C, D, 10

Sommets partages :
- Les triangles 1 et 2 partagent le sommet **6**
- Les triangles 2 et 3 partagent le sommet **C**

Nombres deja places : **12**, **6**, **10**
Nombres a placer : **7, 8, 9, 11** dans les positions A, B, C, D.

## Resolution

### Etape 1 : Triangle 1

Le triangle 1 donne l'equation :

> 12 + A + 6 = 26

Donc : A = 26 - 12 - 6 = **8**

### Etape 2 : Equations restantes

Les nombres restants a placer dans B, C, D sont : **{7, 9, 11}**.

Le triangle 2 donne :

> 6 + B + C = 26, soit B + C = 20

Le triangle 3 donne :

> C + D + 10 = 26, soit C + D = 16

### Etape 3 : Resolution du systeme

Parmi {7, 9, 11}, cherchons les valeurs de C et D telles que C + D = 16 :

| C  | D       | C + D | Valide ? |
|----|---------|-------|----------|
| 7  | 9       | 16    | oui, puis B = 20 - 7 = 13, pas dans {7, 9, 11} |
| 9  | 7       | 16    | oui, puis B = 20 - 9 = 11, dans {7, 9, 11} |
| 11 | 5       | 16    | non, 5 n'est pas disponible |

Seule solution : **C = 9**, **D = 7**, **B = 11**.

### Etape 4 : Verification

- Triangle 1 : 12 + **8** + 6 = **26**
- Triangle 2 : 6 + **11** + **9** = **26**
- Triangle 3 : **9** + **7** + 10 = **26**

Tous les nombres {7, 8, 9, 11} sont bien utilises exactement une fois.

## Schema de la solution

```
  [12] --- [8] --- [6] --- [11] --- [9] --- [7] --- [10]
     \      /         \       /         \      /
      \    /           \     /           \    /
       \  /             \   /             \  /
     Triangle 1       Triangle 2       Triangle 3
      = 26              = 26             = 26
```

## Reponse

Les nombres a placer dans les cases vides sont :

| Position | Nombre |
|----------|--------|
| A        | **8**  |
| B        | **11** |
| C        | **9**  |
| D        | **7**  |
