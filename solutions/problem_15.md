# Probleme 15 : Sa revue preferee (coefficient 15)

## Enonce

Mathias a detache les agrafes de sa revue preferee, qui compte moins de 100 pages assemblees en un seul cahier, et les quadruples pages (imprimees au recto et au verso) se sont eparpillees. Il a devant lui une des feuilles et voit une double page dont le produit des numeros est egal a 900.

**Question :** Quel est le produit des numeros de pages figurant au verso de cette double page ?

---

## Solution

### Modelisation d'un cahier (booklet)

Une revue assemblee en un seul cahier de N pages (N multiple de 4) est constituee de N/4 feuilles physiques imbriquees les unes dans les autres. Chaque feuille porte 4 numeros de page : 2 au recto et 2 au verso.

Pour un cahier de N pages, la k-ieme feuille (k = 1 pour la feuille la plus exterieure, k = N/4 pour la plus interieure) porte les pages suivantes :

- **Face exterieure** (gauche, droite) : (N + 2 - 2k, 2k - 1)
- **Face interieure** (gauche, droite) : (2k, N + 1 - 2k)

**Propriete fondamentale :** Sur chaque face d'une feuille, la somme des deux numeros de page vaut toujours N + 1. De plus, la page de gauche est toujours paire et la page de droite est toujours impaire.

*Verification avec N = 16 (4 feuilles) :*

| Feuille | Face exterieure | Face interieure |
|---------|----------------|-----------------|
| k = 1   | (16, 1)        | (2, 15)         |
| k = 2   | (14, 3)        | (4, 13)         |
| k = 3   | (12, 5)        | (6, 11)         |
| k = 4   | (10, 7)        | (8, 9)          |

### Recherche des solutions

On cherche deux numeros de page p (pair, a gauche) et q (impair, a droite) tels que :

- p x q = 900
- p + q = N + 1
- N < 100 et N est divisible par 4
- La paire (p, q) correspond effectivement a une face valide d'une feuille du cahier

**Decompositions de 900 en produit (pair x impair) :**

| Paire (p, q) | p + q | N = p + q - 1 | N < 100 ? | N mod 4 = 0 ? | Valide ? |
|-------------|-------|---------------|-----------|---------------|----------|
| (900, 1)    | 901   | 900           | Non       | --            | Non      |
| (300, 3)    | 303   | 302           | Non       | --            | Non      |
| (4, 225)    | 229   | 228           | Non       | --            | Non      |
| (180, 5)    | 185   | 184           | Non       | --            | Non      |
| (100, 9)    | 109   | 108           | Non       | --            | Non      |
| (12, 75)    | 87    | 86            | Oui       | Non (86/4 = 21.5) | Non |
| (60, 15)    | 75    | 74            | Oui       | Non (74/4 = 18.5) | Non |
| **(20, 45)**| **65**| **64**        | **Oui**   | **Oui (64/4 = 16)** | **Oui** |
| **(36, 25)**| **61**| **60**        | **Oui**   | **Oui (60/4 = 15)** | **Oui** |

### Analyse des deux solutions

#### Solution 1 : N = 60 pages

La revue a 60 pages (15 feuilles). La face visible est (36, 25), qui est la **face exterieure de la feuille k = 13** :

- Verification : N + 2 - 2k = 60 + 2 - 26 = 36, et 2k - 1 = 25. Correct.
- Produit du recto : 36 x 25 = 900. Correct.
- **Verso** (face interieure) : (2k, N + 1 - 2k) = (26, 35)
- **Produit du verso : 26 x 35 = 910**

#### Solution 2 : N = 64 pages

La revue a 64 pages (16 feuilles). La face visible est (20, 45), qui est la **face interieure de la feuille k = 10** :

- Verification : 2k = 20, et N + 1 - 2k = 64 + 1 - 20 = 45. Correct.
- Produit du recto : 20 x 45 = 900. Correct.
- **Verso** (face exterieure) : (N + 2 - 2k, 2k - 1) = (46, 19)
- **Produit du verso : 46 x 19 = 874**

---

## Reponse

**Nombre de solutions : 2**

Les deux produits possibles des numeros de pages figurant au verso sont :

- **874** (pour une revue de 64 pages : verso = pages 46 et 19)
- **910** (pour une revue de 60 pages : verso = pages 26 et 35)
