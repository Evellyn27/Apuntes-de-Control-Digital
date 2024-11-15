# Retroalimentación del Parcial Segundo Corte

Dada la función de transferencia \( G(z) \):

$$
G(z) = \frac{1.61 \times 10^{-7} z^3 + 6.25 \times 10^{-7} z^2 + 4.15 \times 10^{-7}}{z^3 - 2.87z^2 + 2.75z - 0.88}
$$

**Los polos son:**

$$P_1 = -100$$

$$P_2 = -100$$

$$P_3 = -100$$

$$P_4 = -2 + 2.73j$$

$$P_5 = -2 - 2.73j$$

La expresión del denominador se construye multiplicando los factores correspondientes a cada polo:

$$
(z + 100)(z + 100)(z + 100)(z + 2 - 2.73j)(z + 2 + 2.73j)
$$

**Expandiendo el término complejo:**

$$
(z + 2 - 2.73j)(z + 2 + 2.73j) = (z + 2)^2 - (2.73j)^2
$$

Calculamos cada término:

$$(z + 2)^2 = z^2 + 4z + 4$$
$$(2.73)^2 = 7.4529$$

Por lo tanto:

$$
(z + 2 - 2.73j)(z + 2 + 2.73j) = z^2 + 4z + 4 + 7.4529 = z^2 + 4z + 7.4529
$$

Ahora multiplicamos todos los términos del denominador:

$$
(z + 100)(z + 100)(z + 100)(z^2 + 4z + 7.4529)
$$

Multiplicamos primero $$(z + 100)^3:$$

$$
(z + 100)(z + 100)(z + 100) = z^3 + 300z^2 + 30000z + 1000000
$$

Luego multiplicamos esto por $$(z^2 + 4z + 7.4529):$$

$$z^3 \cdot (z^2 + 4z + 7.4529) = z^5 + 4z^4 + 7.4529z^3$$

$$300z^2 \cdot (z^2 + 4z + 7.4529) = 300z^4 + 1200z^3 + 2235.87z^2$$

$$30000z \cdot (z^2 + 4z + 7.4529) = 30000z^3 + 120000z^2 + 223587z$$

$$1000000 \cdot (z^2 + 4z + 7.4529) = 1000000z^2 + 4000000z + 7452900$$

Sumando todos los términos:

$$
z^5 + 304z^4 + 31210z^3 + 1120000z^2 + 4380000z + 11452900
$$


La función de transferencia $$G_0(z)$$ se expresa como:

$$
G_0(z) = \frac{1}{z^5 + 304z^4 + 31210z^3 + 1120000z^2 + 4380000z + 11452900}
$$

## 📚Ejercicio 1

Calculo del controlador por Método de igualación por modelo

$$
C(z) = \frac{G_0(z)}{G(z) \cdot (1 - G(z))}
$$

Para calcular \( 1 - G(z) \), tenemos que restar $G(z)$ de 1:

$$
1 - G(z) = 1 - \frac{1.61 \times 10^{-7} z^3 + 6.25 \times 10^{-7} z^2 + 4.15 \times 10^{-7}}{z^3 - 2.87z^2 + 2.75z - 0.88}
$$

Esto da lugar a:

$$
1 - G(z) = \frac{(z^3 - 2.87z^2 + 2.75z - 0.88) - (1.61 \times 10^{-7} z^3 + 6.25 \times 10^{-7} z^2 + 4.15 \times 10^{-7})}{z^3 - 2.87z^2 + 2.75z - 0.88}
$$


Sustituyendo $G_0(z),$ $G(z),$ y $1 - G(z)$ en la fórmula del controlador:

$$
C(z) = \frac{\frac{1}{z^5 + 304z^4 + 31210z^3 + 1120000z^2 + 4380000z + 11452900}}{\frac{1.61 \times 10^{-7} z^3 + 6.25 \times 10^{-7} z^2 + 4.15 \times 10^{-7}}{z^3 - 2.87z^2 + 2.75z - 0.88} \cdot \frac{z^3 - 2.87z^2 + 2.75z - 0.88 - (1.61 \times 10^{-7} z^3 + 6.25 \times 10^{-7} z^2 + 4.15 \times 10^{-7})}{z^3 - 2.87z^2 + 2.75z - 0.88}}
$$
## 📚Ejercicio 2
Calculo del controlador por Método de igualación por coeficientes

