# Probleme 11 : LES AGES CROISES (coefficient 11)

## Enonce

Un pere fetera son anniversaire le 1er mai, et sa fille fetera le sien le 31 mai. Le 2 mai, l'age du pere en annees sera egal a l'age de sa fille en mois.
On sait que le pere avait au moins 25 ans et au plus 45 ans au moment de la naissance de sa fille.
Quel age (en annees) avait-il exactement au moment de cette naissance ?

## Solution

### Mise en place des variables

Soit l'annee courante $Y$, et soit $N$ le nombre d'annees calendaires entre l'annee de naissance de la fille et l'annee courante (la fille est nee en l'annee $Y - N$).

- **Le pere** fete son anniversaire le 1er mai. Le 2 mai de l'annee $Y$, il vient d'avoir $P$ ans (il a eu $P$ ans la veille).
- **La fille** fete son anniversaire le 31 mai. Le 2 mai de l'annee $Y$, elle n'a pas encore fete son anniversaire de cette annee.

### Calcul de l'age de la fille en mois

La fille est nee le 31 mai de l'annee $Y - N$. Son dernier anniversaire (en annees) etait le 31 mai de l'annee $Y - 1$, ou elle a eu $N - 1$ ans.

Du 31 mai de l'annee $Y - 1$ au 2 mai de l'annee $Y$, comptons les mois revolus. Les anniversaires mensuels d'une personne nee le 31 tombent le 31 de chaque mois (ou le dernier jour du mois si celui-ci a moins de 31 jours) :

| Mois | Date anniversaire mensuel | Mois revolus depuis le 31 mai |
|------|---------------------------|-------------------------------|
| Juin $Y-1$ | 30 juin | 1 |
| Juillet $Y-1$ | 31 juillet | 2 |
| Aout $Y-1$ | 31 aout | 3 |
| Septembre $Y-1$ | 30 septembre | 4 |
| Octobre $Y-1$ | 31 octobre | 5 |
| Novembre $Y-1$ | 30 novembre | 6 |
| Decembre $Y-1$ | 31 decembre | 7 |
| Janvier $Y$ | 31 janvier | 8 |
| Fevrier $Y$ | 28/29 fevrier | 9 |
| Mars $Y$ | 31 mars | 10 |
| Avril $Y$ | 30 avril | 11 |

Le 2 mai de l'annee $Y$, on a depasse le 30 avril (11 mois) mais pas encore atteint le 31 mai (12 mois). Donc la fille a exactement **11 mois revolus** depuis son dernier anniversaire annuel.

Son age total en mois revolus est donc :

$$F = 12(N - 1) + 11 = 12N - 1$$

### Equation fondamentale

La condition du probleme est $P = F$, soit :

$$P = 12N - 1$$

### Age du pere a la naissance de la fille

Le pere est ne le 1er mai de l'annee $Y - P$. La fille est nee le 31 mai de l'annee $Y - N$.

Le 1er mai de l'annee $Y - N$, le pere a fete ses $(Y - N) - (Y - P) = P - N$ ans. Au 31 mai de cette meme annee (date de naissance de la fille), le pere a toujours $P - N$ ans revolus.

Notons $D = P - N$ l'age du pere a la naissance de sa fille. En substituant $P = 12N - 1$ :

$$D = P - N = (12N - 1) - N = 11N - 1$$

### Application de la contrainte

On impose $25 \leq D \leq 45$, soit :

$$25 \leq 11N - 1 \leq 45$$

$$26 \leq 11N \leq 46$$

$$\frac{26}{11} \leq N \leq \frac{46}{11}$$

$$2{,}36\ldots \leq N \leq 4{,}18\ldots$$

Comme $N$ est un entier positif (la fille doit etre nee avant le 2 mai de l'annee courante), les valeurs possibles sont :

$$N = 3 \quad \text{ou} \quad N = 4$$

### Les deux solutions

**Solution 1 : $N = 3$**
- Age de la fille en mois : $F = 12 \times 3 - 1 = 35$ mois (soit 2 ans et 11 mois).
- Age du pere en annees : $P = 35$ ans.
- Age du pere a la naissance : $D = 11 \times 3 - 1 = 32$ ans.
- Verification : $25 \leq 32 \leq 45$. $\checkmark$

**Solution 2 : $N = 4$**
- Age de la fille en mois : $F = 12 \times 4 - 1 = 47$ mois (soit 3 ans et 11 mois).
- Age du pere en annees : $P = 47$ ans.
- Age du pere a la naissance : $D = 11 \times 4 - 1 = 43$ ans.
- Verification : $25 \leq 43 \leq 45$. $\checkmark$

### Verification detaillee

**Verification de la solution 1 ($D = 32$) :**
Supposons que le pere soit ne le 1er mai 1991 et la fille le 31 mai 2023. Le 2 mai 2026 :
- Le pere a fete ses 35 ans le 1er mai 2026. Son age en annees : **35**.
- La fille, nee le 31 mai 2023, a 35 mois revolus le 2 mai 2026 (du 31 mai 2023 au 30 avril 2026 = 35 mois, et le 2 mai 2026 est avant le 31 mai). Son age en mois : **35**. $\checkmark$
- Age du pere a la naissance (31 mai 2023) : il avait 32 ans. $\checkmark$

**Verification de la solution 2 ($D = 43$) :**
Supposons que le pere soit ne le 1er mai 1979 et la fille le 31 mai 2022. Le 2 mai 2026 :
- Le pere a fete ses 47 ans le 1er mai 2026. Son age en annees : **47**.
- La fille, nee le 31 mai 2022, a 47 mois revolus le 2 mai 2026 (du 31 mai 2022 au 30 avril 2026 = 47 mois, et le 2 mai 2026 est avant le 31 mai). Son age en mois : **47**. $\checkmark$
- Age du pere a la naissance (31 mai 2022) : il avait 43 ans. $\checkmark$

## Reponse

**Nombre de solutions : 2**

Les deux ages possibles du pere au moment de la naissance de sa fille sont :

- **32 ans** (le pere a alors 35 ans et la fille 35 mois)
- **43 ans** (le pere a alors 47 ans et la fille 47 mois)
