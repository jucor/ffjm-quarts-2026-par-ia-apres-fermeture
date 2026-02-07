# Probleme 12 : L'ESCALIER ROULANT (coefficient 12)

**Categories :** C2 (4e-3e), L1 (lycee), GP (grand public), L2 (etudiants), HC (haute competition)

---

## Enonce

Lorsque Mathias prend cet escalier roulant descendant, en restant immobile sur la premiere marche du haut, il met 25 secondes pour arriver en bas.
Lorsqu'il prend le meme escalier en descendant les marches a une allure constante, il ne met que 10 secondes pour arriver en bas.
S'il prend l'escalier roulant a contresens, combien de temps mettra-t-il pour arriver en haut, sachant que sur un escalier fixe sa vitesse en montant est egale aux 4/5 de sa vitesse en descendant ?

(Repondre 0 si sa vitesse en montee ne lui permet pas d'arriver en haut.)

---

## Resolution detaillee

### Definition des variables

Soit :

- **L** = longueur de l'escalier roulant (distance totale a parcourir)
- **v_e** = vitesse de l'escalier roulant (vers le bas)
- **v_d** = vitesse de marche de Mathias en descente
- **v_m** = vitesse de marche de Mathias en montee = (4/5) * v_d

### Scenario 1 : Mathias immobile sur l'escalier descendant

Mathias reste immobile. Seul l'escalier le transporte vers le bas. Il met 25 secondes.

$$\frac{L}{v_e} = 25 \implies v_e = \frac{L}{25}$$

### Scenario 2 : Mathias marche en descendant sur l'escalier descendant

Les deux vitesses s'additionnent (meme sens). Il met 10 secondes.

$$\frac{L}{v_e + v_d} = 10 \implies v_e + v_d = \frac{L}{10}$$

### Calcul de v_d (vitesse de descente a pied)

En substituant v_e :

$$v_d = \frac{L}{10} - v_e = \frac{L}{10} - \frac{L}{25}$$

$$v_d = L\left(\frac{1}{10} - \frac{1}{25}\right) = L\left(\frac{5 - 2}{50}\right) = \frac{3L}{50}$$

### Calcul de v_m (vitesse de montee a pied)

On sait que sur un escalier fixe, la vitesse de montee de Mathias vaut 4/5 de sa vitesse de descente :

$$v_m = \frac{4}{5} \times v_d = \frac{4}{5} \times \frac{3L}{50} = \frac{12L}{250} = \frac{6L}{125}$$

### Scenario 3 : Mathias monte l'escalier a contresens

Mathias monte (vitesse v_m vers le haut) tandis que l'escalier descend (vitesse v_e vers le bas). La vitesse effective de Mathias vers le haut est :

$$v_{\text{effective}} = v_m - v_e = \frac{6L}{125} - \frac{L}{25}$$

$$v_{\text{effective}} = \frac{6L}{125} - \frac{5L}{125} = \frac{L}{125}$$

Puisque v_effective = L/125 > 0, Mathias avance bien vers le haut : il est capable d'atteindre le sommet.

### Calcul du temps

$$t = \frac{L}{v_{\text{effective}}} = \frac{L}{\dfrac{L}{125}} = 125 \text{ secondes}$$

---

## Verification

| Scenario | Vitesse effective | Temps |
|---|---|---|
| Immobile sur escalier descendant | v_e = L/25 | 25 s |
| Marche en descendant sur escalier | v_e + v_d = L/25 + 3L/50 = 5L/50 = L/10 | 10 s |
| Montee a contresens | v_m - v_e = 6L/125 - 5L/125 = L/125 | 125 s |

Les deux premiers scenarios correspondent bien aux donnees de l'enonce. Le calcul est coherent.

---

## Reponse

- **Nombre de solutions : 1**
- **Reponse : 125 secondes**
