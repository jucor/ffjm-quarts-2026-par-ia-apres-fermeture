# Probleme 18 : LE BOIS DU PERE LUCIEN (coefficient 18)

**Categories :** L2 (etudiants), HC (haute competition)

---

## Enonce

Le Pere Lucien possede un bois triangulaire ACE divise en trois parcelles ABD, BDE et BCE, tel que :
- les angles ABD et ACE sont droits ;
- BD = DE = 1 km ;
- l'aire du triangle ABD est double de celle du triangle BCE.

**Question :** Quelle est la mesure de CE ?

On donnera la reponse arrondie au metre le plus proche et si necessaire on prendra 1,732 pour racine de 3.

---

## Resolution detaillee

### Analyse de la configuration geometrique

D'apres la figure, le triangle ACE a pour sommets A (en haut), C (en bas a gauche) et E (en bas a droite). Les trois parcelles ABD, BDE et BCE partitionnent le triangle ACE. Pour que cette partition soit valide :

- **B est sur le segment AC** (car ABD + BDE forment le triangle ABE, et ABE + BCE = ACE avec B sur AC)
- **D est sur le segment AE** (car ABD et BDE partagent le cote BD, et leur reunion forme le triangle ABE)

L'angle ACE = 90 degres signifie que l'angle en C du grand triangle est droit. L'angle ABD = 90 degres signifie que BD est perpendiculaire a AB, donc BD est perpendiculaire a AC au point B.

### Mise en place du repere

On place C a l'origine du repere :

- C = (0, 0)
- A = (0, a) sur l'axe des ordonnees (a > 0)
- E = (e, 0) sur l'axe des abscisses (e > 0), puisque l'angle ACE = 90 degres

Puisque B est sur le segment AC :

- B = (0, b) avec 0 < b < a

L'angle ABD = 90 degres au sommet B signifie que BD est perpendiculaire a BA. Comme BA est dirige selon l'axe vertical (de B vers A), BD doit etre horizontal. Donc :

- D = (d, b) pour un certain d > 0

### Exploitation de BD = 1

BD = d = 1, donc **D = (1, b)**.

### Exploitation de D sur le segment AE

La droite AE va de A = (0, a) a E = (e, 0). Un point parametre sur ce segment s'ecrit :

(t . e, a(1 - t)) pour t dans [0, 1]

Le point D = (1, b) doit verifier :

- t . e = 1, donc t = 1/e
- a(1 - 1/e) = b, donc **a = b . e / (e - 1)** ... (I)

### Exploitation de DE = 1

DE = distance de D = (1, b) a E = (e, 0) :

DE^2 = (e - 1)^2 + b^2 = 1

Donc : **(e - 1)^2 + b^2 = 1** ... (II)

### Calcul des aires

**Aire du triangle ABD :** Les sommets sont A = (0, a), B = (0, b), D = (1, b).

La base BD est horizontale de longueur 1. La hauteur est la distance verticale de A a la droite BD, soit (a - b).

Aire(ABD) = (1/2) x 1 x (a - b) = **(a - b) / 2**

**Aire du triangle BCE :** Les sommets sont B = (0, b), C = (0, 0), E = (e, 0).

La base CE est horizontale de longueur e. La hauteur est la distance verticale de B a la droite CE, soit b.

Aire(BCE) = (1/2) x e x b = **e . b / 2**

### Application de la condition sur les aires

L'aire du triangle ABD est double de celle du triangle BCE :

(a - b) / 2 = 2 x (e . b / 2)

a - b = 2 . e . b

**a = b(1 + 2e)** ... (III)

### Resolution du systeme

En combinant (I) et (III) :

b . e / (e - 1) = b(1 + 2e)

On divise par b (non nul) :

e / (e - 1) = 1 + 2e

e = (e - 1)(1 + 2e)

e = e + 2e^2 - 1 - 2e

e = 2e^2 - e - 1

0 = 2e^2 - 2e - 1

### Resolution de l'equation du second degre

2e^2 - 2e - 1 = 0

Le discriminant vaut : Delta = 4 + 8 = 12

e = (2 +/- racine(12)) / 4 = (2 +/- 2.racine(3)) / 4 = (1 +/- racine(3)) / 2

Les deux racines sont :

- e = (1 + racine(3)) / 2 ≈ (1 + 1,732) / 2 = 2,732 / 2 = 1,366
- e = (1 - racine(3)) / 2 ≈ (1 - 1,732) / 2 = -0,732 / 2 = -0,366

Puisque e > 0 (longueur), seule la premiere racine convient :

**CE = e = (1 + racine(3)) / 2**

### Verification

Avec e = (1 + racine(3)) / 2 :

**Verification de la contrainte DE = 1 :**

(e - 1)^2 = ((racine(3) - 1) / 2)^2 = (3 - 2.racine(3) + 1) / 4 = (4 - 2.racine(3)) / 4 = (2 - racine(3)) / 2

b^2 = 1 - (e - 1)^2 = 1 - (2 - racine(3))/2 = (2 - 2 + racine(3))/2 = racine(3)/2

Donc b = racine(racine(3)/2) > 0. Correct.

(e - 1)^2 + b^2 = (2 - racine(3))/2 + racine(3)/2 = 2/2 = 1. Correct.

**Verification de la condition sur les aires :**

De (I) : a = b . e / (e - 1)
De (III) : a = b(1 + 2e)

e / (e - 1) = 1 + 2e
e = (1 + 2e)(e - 1) = e - 1 + 2e^2 - 2e = 2e^2 - e - 1
2e^2 - 2e - 1 = 0. Correct (c'est bien l'equation que l'on a resolue).

**Verification que D est a l'interieur du triangle ACE :**

D = (1, b) avec 0 < 1 < e ≈ 1,366 et b > 0. Le point D se trouve bien a l'interieur du triangle, et sur le segment AE par construction.

### Calcul numerique

CE = (1 + racine(3)) / 2

En utilisant racine(3) = 1,732 :

CE = (1 + 1,732) / 2 = 2,732 / 2 = 1,366 km = 1366 m

---

## Reponse

- **Nombre de solutions : 1**
- **CE = (1 + racine(3)) / 2 km ≈ 1,366 km = 1366 metres**
