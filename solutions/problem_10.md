# Probleme 10 : DIVISEURS (coefficient 10)

## Enonce

Max remarque que le nombre 24 et son retourne 42 ont ensemble au moins un diviseur commun different de 1 : le nombre 6.
Combien y a-t-il de paires de nombres a deux chiffres AB et BA qui ont au moins un diviseur positif commun different de 1 ?

*Note : A et B sont deux chiffres differents non nuls.*

## Solution

### Mise en place

On considere les nombres a deux chiffres $\overline{AB} = 10A + B$ et $\overline{BA} = 10B + A$, ou $A$ et $B$ sont des chiffres distincts appartenant a $\{1, 2, \ldots, 9\}$. On cherche les paires $\{A, B\}$ (non ordonnees) telles que $\gcd(10A+B,\; 10B+A) > 1$.

Le nombre total de telles paires (sans condition sur le pgcd) est $\binom{9}{2} = 36$.

### Analyse theorique

Posons $d = \gcd(10A+B,\; 10B+A)$. On observe que :

- $10A + B + 10B + A = 11(A + B)$, donc $d \mid 11(A+B)$.
- $10A + B - (10B + A) = 9(A - B)$, donc $d \mid 9(A-B)$.

Soit $p$ un diviseur premier de $d$. Alors $p \mid 10A+B$ et $p \mid 10B+A$.

**Cas $p = 2$ :** On a $2 \mid (10A + B)$ si et seulement si $B$ est pair, et $2 \mid (10B + A)$ si et seulement si $A$ est pair. Donc $2 \mid d$ si et seulement si **$A$ et $B$ sont tous les deux pairs**.

**Cas $p = 3$ :** On a $10A + B \equiv A + B \pmod{3}$, et de meme $10B + A \equiv A + B \pmod{3}$. Donc $3 \mid d$ si et seulement si **$3 \mid (A + B)$**.

**Cas $p = 5$ :** Il faudrait $5 \mid B$ et $5 \mid A$ (car $10A + B \equiv B \pmod{5}$ et $10B + A \equiv A \pmod{5}$). Cela impose $A, B \in \{5\}$, ce qui contredit $A \neq B$. Impossible.

**Cas $p = 7$ :** De $p \mid 11(A+B)$ et $\gcd(7, 11) = 1$, on tire $7 \mid (A+B)$. De $p \mid 9(A-B)$ et $\gcd(7, 9) = 1$, on tire $7 \mid (A-B)$. Alors $7 \mid 2A$ et $7 \mid 2B$, donc $7 \mid A$ et $7 \mid B$, ce qui impose $A = B = 7$, contradiction.

**Cas $p \geq 11$ :** On a $10A + B \leq 98$, donc $p \leq 97$. Mais $p \mid 11(A+B)$ avec $A + B \leq 17$. Si $p = 11$, alors $11 \mid (10A+B)$ equivaut a $11 \mid 11A + (B-A)$, soit $11 \mid (B - A)$. Comme $|B - A| \leq 8$, c'est impossible sauf si $A = B$. Pour $p = 13$, on aurait $13 \mid (A+B)$ (car $\gcd(13,11)=1$) donc $A + B = 13$, et $13 \mid (A - B)$ (car $\gcd(13,9)=1$) donc $A = B$, contradiction. De meme pour tout $p \geq 11$.

**Conclusion theorique :** Les seuls facteurs premiers possibles de $\gcd(10A+B, 10B+A)$ sont **2 et 3**. Donc :

$$\gcd(10A+B,\; 10B+A) > 1 \iff \text{($A$ et $B$ sont tous deux pairs) ou ($3$ divise $A + B$)}.$$

### Denombrement par inclusion-exclusion

On compte les paires verifiant au moins l'une des deux conditions.

**Condition 1 : $A$ et $B$ tous deux pairs.**
Les chiffres pairs non nuls sont $\{2, 4, 6, 8\}$ (4 chiffres).
Nombre de paires : $\binom{4}{2} = 6$.

Ce sont : $\{2,4\}$, $\{2,6\}$, $\{2,8\}$, $\{4,6\}$, $\{4,8\}$, $\{6,8\}$.

**Condition 2 : $3 \mid (A + B)$.**
Les chiffres de $\{1, \ldots, 9\}$ selon leur reste modulo 3 :
- Reste 0 : $\{3, 6, 9\}$ -- 3 chiffres
- Reste 1 : $\{1, 4, 7\}$ -- 3 chiffres
- Reste 2 : $\{2, 5, 8\}$ -- 3 chiffres

Pour que $A + B \equiv 0 \pmod{3}$ :
- Les deux chiffres sont dans le groupe de reste 0 : $\binom{3}{2} = 3$ paires.
- Un chiffre de reste 1 et un de reste 2 : $3 \times 3 = 9$ paires.
- Total : $3 + 9 = 12$ paires.

Ce sont : $\{1,2\}$, $\{1,5\}$, $\{1,8\}$, $\{2,4\}$, $\{2,7\}$, $\{3,6\}$, $\{3,9\}$, $\{4,5\}$, $\{4,8\}$, $\{5,7\}$, $\{6,9\}$, $\{7,8\}$.

**Intersection des deux conditions : $A$ et $B$ pairs ET $3 \mid (A+B)$.**
Parmi les chiffres pairs $\{2, 4, 6, 8\}$, les restes modulo 3 sont :
- $2 \equiv 2$, $4 \equiv 1$, $6 \equiv 0$, $8 \equiv 2$.

Paires de pairs dont la somme est divisible par 3 :
- Reste $0 + 0$ : un seul chiffre (6), donc 0 paires.
- Reste $1 + 2$ : chiffre de reste 1 parmi les pairs = $\{4\}$, de reste 2 = $\{2, 8\}$, soit $1 \times 2 = 2$ paires : $\{2,4\}$ et $\{4,8\}$.
- Total : **2 paires**.

**Par inclusion-exclusion :**

$$N = 6 + 12 - 2 = \boxed{16}$$

### Verification exhaustive

Voici le tableau complet des 36 paires, avec le pgcd de $\overline{AB}$ et $\overline{BA}$ :

| Paire | $\overline{AB}$ | $\overline{BA}$ | pgcd | $> 1$ ? |
|-------|------:|------:|-----:|:-------:|
| {1,2} |    12 |    21 |    3 |   oui   |
| {1,3} |    13 |    31 |    1 |   non   |
| {1,4} |    14 |    41 |    1 |   non   |
| {1,5} |    15 |    51 |    3 |   oui   |
| {1,6} |    16 |    61 |    1 |   non   |
| {1,7} |    17 |    71 |    1 |   non   |
| {1,8} |    18 |    81 |    9 |   oui   |
| {1,9} |    19 |    91 |    1 |   non   |
| {2,3} |    23 |    32 |    1 |   non   |
| {2,4} |    24 |    42 |    6 |   oui   |
| {2,5} |    25 |    52 |    1 |   non   |
| {2,6} |    26 |    62 |    2 |   oui   |
| {2,7} |    27 |    72 |    9 |   oui   |
| {2,8} |    28 |    82 |    2 |   oui   |
| {2,9} |    29 |    92 |    1 |   non   |
| {3,4} |    34 |    43 |    1 |   non   |
| {3,5} |    35 |    53 |    1 |   non   |
| {3,6} |    36 |    63 |    9 |   oui   |
| {3,7} |    37 |    73 |    1 |   non   |
| {3,8} |    38 |    83 |    1 |   non   |
| {3,9} |    39 |    93 |    3 |   oui   |
| {4,5} |    45 |    54 |    9 |   oui   |
| {4,6} |    46 |    64 |    2 |   oui   |
| {4,7} |    47 |    74 |    1 |   non   |
| {4,8} |    48 |    84 |   12 |   oui   |
| {4,9} |    49 |    94 |    1 |   non   |
| {5,6} |    56 |    65 |    1 |   non   |
| {5,7} |    57 |    75 |    3 |   oui   |
| {5,8} |    58 |    85 |    1 |   non   |
| {5,9} |    59 |    95 |    1 |   non   |
| {6,7} |    67 |    76 |    1 |   non   |
| {6,8} |    68 |    86 |    2 |   oui   |
| {6,9} |    69 |    96 |    3 |   oui   |
| {7,8} |    78 |    87 |    3 |   oui   |
| {7,9} |    79 |    97 |    1 |   non   |
| {8,9} |    89 |    98 |    1 |   non   |

On compte bien **16 paires** avec un pgcd strictement superieur a 1.

### Les 16 paires

1. $\{1,2\}$ : $\gcd(12, 21) = 3$
2. $\{1,5\}$ : $\gcd(15, 51) = 3$
3. $\{1,8\}$ : $\gcd(18, 81) = 9$
4. $\{2,4\}$ : $\gcd(24, 42) = 6$
5. $\{2,6\}$ : $\gcd(26, 62) = 2$
6. $\{2,7\}$ : $\gcd(27, 72) = 9$
7. $\{2,8\}$ : $\gcd(28, 82) = 2$
8. $\{3,6\}$ : $\gcd(36, 63) = 9$
9. $\{3,9\}$ : $\gcd(39, 93) = 3$
10. $\{4,5\}$ : $\gcd(45, 54) = 9$
11. $\{4,6\}$ : $\gcd(46, 64) = 2$
12. $\{4,8\}$ : $\gcd(48, 84) = 12$
13. $\{5,7\}$ : $\gcd(57, 75) = 3$
14. $\{6,8\}$ : $\gcd(68, 86) = 2$
15. $\{6,9\}$ : $\gcd(69, 96) = 3$
16. $\{7,8\}$ : $\gcd(78, 87) = 3$

## Reponse

**Le nombre de paires est : 16**

Deux exemples de paires : $\{2,4\}$ (car $\gcd(24, 42) = 6 > 1$) et $\{4,8\}$ (car $\gcd(48, 84) = 12 > 1$).
