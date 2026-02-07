# Probleme 3 : TIRELIRE (coefficient 3)

## Enonce

Dans sa tirelire, Tom a 26 centimes d'euro avec des pieces de 5, 2 et 1 centime.
Combien de pieces a-t-il au minimum sachant qu'il a au moins une piece de chaque sorte ?

## Resolution

### Mise en equations

Notons :
- **a** le nombre de pieces de 5 centimes (a >= 1)
- **b** le nombre de pieces de 2 centimes (b >= 1)
- **c** le nombre de pieces de 1 centime (c >= 1)

On cherche a **minimiser** le nombre total de pieces **a + b + c** sous les contraintes :

- 5a + 2b + c = 26
- a >= 1, b >= 1, c >= 1

### Strategie

Pour minimiser le nombre de pieces, il faut utiliser en priorite les pieces de plus grande valeur (5 centimes), puis celles de 2 centimes, et enfin celles de 1 centime.

### Determination du nombre maximal de pieces de 5 centimes

Puisqu'il faut au moins une piece de 2 centimes et une piece de 1 centime, la somme couverte par ces deux pieces obligatoires est 2 + 1 = 3 centimes. Il reste donc 26 - 3 = 23 centimes a couvrir avec des pieces de 5 centimes (en priorite), de 2 centimes et de 1 centime.

- Si **a = 5** : 5 x 5 = 25 centimes pour les pieces de 5c. Il faudrait 2b + c = 26 - 25 = 1 avec b >= 1, or 2b >= 2 > 1. **Impossible.**
- Si **a = 4** : 4 x 5 = 20 centimes pour les pieces de 5c. Il reste 2b + c = 26 - 20 = 6 avec b >= 1 et c >= 1.

Donc le nombre maximal de pieces de 5 centimes est **a = 4**.

### Optimisation des pieces de 2 et 1 centime pour a = 4

Avec a = 4, on a la contrainte : 2b + c = 6, avec b >= 1 et c >= 1.

On veut minimiser b + c. Puisque remplacer une piece de 1 centime par une piece de 2 centimes diminue le nombre total de pieces (on retire 2 pieces de 1c pour ajouter 1 piece de 2c), il faut maximiser b.

| b | c = 6 - 2b | b + c | Valide ? |
|---|-----------|-------|----------|
| 1 | 4         | 5     | Oui      |
| 2 | 2         | 4     | Oui      |
| 3 | 0         | 3     | Non (c >= 1 requis) |

Le minimum est atteint pour **b = 2** et **c = 2**, donnant **b + c = 4**.

### Verification des autres cas (exhaustivite)

Pour confirmer qu'on ne peut pas faire mieux avec moins de pieces de 5c :

- **a = 3** : 2b + c = 26 - 15 = 11, b >= 1, c >= 1. Maximisons b : b = 5, c = 1. Total = 3 + 5 + 1 = **9 pieces**. Plus que 8.
- **a = 2** : 2b + c = 26 - 10 = 16, b >= 1, c >= 1. Maximisons b : b = 7, c = 2. Total = 2 + 7 + 2 = **11 pieces**. Plus que 8.
- **a = 1** : 2b + c = 26 - 5 = 21, b >= 1, c >= 1. Maximisons b : b = 10, c = 1. Total = 1 + 10 + 1 = **12 pieces**. Plus que 8.

### Preuve qu'on ne peut pas obtenir 7 pieces

Supposons a + b + c = 7 et 5a + 2b + c = 26.

En soustrayant la premiere equation de la seconde : 4a + b = 19.

De plus, c = 7 - a - b >= 1 impose a + b <= 6, donc b <= 6 - a.

En substituant dans 4a + b = 19 : 4a + (6 - a) >= 19, soit 3a >= 13, donc a >= 4.34, c'est-a-dire **a >= 5**.

Or si a = 5 : b = 19 - 20 = -1, ce qui est impossible.

**Il n'existe donc aucune solution avec 7 pieces. Le minimum est bien 8.**

### Verification de la solution

- 4 pieces de 5 centimes : 4 x 5 = 20 centimes
- 2 pieces de 2 centimes : 2 x 2 = 4 centimes
- 2 pieces de 1 centime : 2 x 1 = 2 centimes
- **Total** : 20 + 4 + 2 = **26 centimes**
- **Nombre de pieces** : 4 + 2 + 2 = **8 pieces**
- Au moins une piece de chaque sorte : 5c, 2c, 1c sont toutes presentes.

## Reponse

**Tom a au minimum 8 pieces** dans sa tirelire : 4 pieces de 5 centimes, 2 pieces de 2 centimes et 2 pieces de 1 centime.
