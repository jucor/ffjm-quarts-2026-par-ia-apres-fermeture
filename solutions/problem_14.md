# Probleme 14 : RAPPORTEUR (coefficient 14)

## Enonce

Le rapporteur de Mathilde a la forme d'un demi-disque de diametre 12 cm. Il peut etre range a plat dans une boite carree.
Quelle est, au minimum, la longueur du cote de cette boite ?

On prendra 1,4142 pour racine de 2, et on donnera la reponse en cm arrondie au centieme.

## Nombre de solutions

**1 solution unique.**

## Solution detaillee

### Donnees

- Le rapporteur est un demi-disque de diametre $d = 12$ cm, soit un rayon $R = 6$ cm.
- On cherche le cote minimal $s$ d'un carre dans lequel ce demi-disque peut etre place a plat.

### Placement sans inclinaison

Si l'on pose le rapporteur a plat sans l'incliner, avec le diametre le long d'un cote du carre :

- La largeur necessaire est $d = 12$ cm (longueur du diametre).
- La hauteur necessaire est $R = 6$ cm (rayon, hauteur de l'arc).

Il faudrait alors un carre de cote **12 cm**. Mais on peut faire mieux en inclinant le rapporteur.

### Placement optimal par inclinaison

On incline le demi-disque d'un angle $\theta$ par rapport a l'horizontale a l'interieur du carre. On cherche la boite englobante (bounding box) alignee sur les axes du carre.

**Parametrisation.** On place le centre du diametre en un point $M = (c_x, c_y)$. Le diametre fait un angle $\theta$ avec l'horizontale. Les exremites du diametre sont :

$$A = (c_x + R\cos\theta,\; c_y + R\sin\theta), \quad B = (c_x - R\cos\theta,\; c_y - R\sin\theta)$$

L'arc de cercle (partie courbe) s'etend du cote perpendiculaire au diametre. Les points de l'arc sont parametres par :

$$P(\varphi) = M + R\cos\varphi\,\vec{u} + R\sin\varphi\,\vec{v}, \quad \varphi \in [0, \pi]$$

ou $\vec{u} = (\cos\theta, \sin\theta)$ est la direction du diametre et $\vec{v} = (-\sin\theta, \cos\theta)$ la direction perpendiculaire (vers l'arc).

Cela donne :

$$x(\varphi) = c_x + R\cos(\varphi + \theta), \quad y(\varphi) = c_y + R\sin(\varphi + \theta)$$

pour $\varphi \in [0, \pi]$, soit $\varphi + \theta \in [\theta, \pi + \theta]$.

**Calcul des extremes.** Pour $\theta \in [0, \pi/2]$ :

| Extreme | Valeur | Atteint en |
|---------|--------|------------|
| $x_{\min}$ | $c_x - R$ | point de l'arc ($\varphi = \pi - \theta$) |
| $x_{\max}$ | $c_x + R\cos\theta$ | extremite $A$ ($\varphi = 0$) |
| $y_{\min}$ | $c_y - R\sin\theta$ | extremite $B$ ($\varphi = \pi$) |
| $y_{\max}$ | $c_y + R$ | point de l'arc ($\varphi = \pi/2 - \theta$) |

Les dimensions de la boite englobante sont donc :

$$\text{Largeur}(\theta) = x_{\max} - x_{\min} = R\cos\theta + R = R(1 + \cos\theta)$$

$$\text{Hauteur}(\theta) = y_{\max} - y_{\min} = R + R\sin\theta = R(1 + \sin\theta)$$

**Verification aux cas limites :**
- $\theta = 0$ : Largeur $= 2R = 12$, Hauteur $= R = 6$, carre de cote 12. Correct.
- $\theta = \pi/2$ : Largeur $= R = 6$, Hauteur $= 2R = 12$, carre de cote 12. Correct.

### Optimisation

Le cote du carre doit verifier $s \geq \max\bigl(R(1+\cos\theta),\; R(1+\sin\theta)\bigr)$.

Pour minimiser ce maximum :

- $R(1 + \cos\theta)$ est decroissante sur $[0, \pi/2]$.
- $R(1 + \sin\theta)$ est croissante sur $[0, \pi/2]$.

Le minimum de $\max(f, g)$ ou $f$ est decroissante et $g$ est croissante est atteint au point ou $f = g$, c'est-a-dire :

$$R(1 + \cos\theta) = R(1 + \sin\theta) \implies \cos\theta = \sin\theta \implies \theta = \frac{\pi}{4}$$

### Calcul du cote minimal

A $\theta = \pi/4$ :

$$s = R\left(1 + \cos\frac{\pi}{4}\right) = R\left(1 + \frac{\sqrt{2}}{2}\right) = R \cdot \frac{2 + \sqrt{2}}{2} = \frac{R(2 + \sqrt{2})}{2}$$

Soit, de maniere equivalente :

$$s = 3(2 + \sqrt{2}) = 6 + 3\sqrt{2}$$

### Verification de la configuration

Avec $\theta = \pi/4$ et $s = 6 + 3\sqrt{2}$, le demi-disque touche les quatre cotes du carre :

| Cote du carre | Point de contact | Coordonnees |
|---------------|-----------------|-------------|
| Cote gauche ($x = 0$) | Point sur l'arc | $(0;\; 3\sqrt{2})$ |
| Cote droit ($x = s$) | Extremite $A$ du diametre | $(6 + 3\sqrt{2};\; 6\sqrt{2})$ |
| Cote inferieur ($y = 0$) | Extremite $B$ du diametre | $(6 - 3\sqrt{2};\; 0)$ |
| Cote superieur ($y = s$) | Point sur l'arc | $(6;\; 6 + 3\sqrt{2})$ |

Le demi-disque est entierement contenu dans le carre et touche chacun de ses quatre cotes, confirmant que c'est bien la configuration optimale.

### Application numerique

Avec $\sqrt{2} = 1{,}4142$ :

$$s = 6 + 3 \times 1{,}4142 = 6 + 4{,}2426 = 10{,}2426$$

Arrondi au centieme :

$$\boxed{s = 10{,}24 \text{ cm}}$$

## Reponse

**Nombre de solutions : 1**

**La longueur minimale du cote de la boite est de 10,24 cm.**
