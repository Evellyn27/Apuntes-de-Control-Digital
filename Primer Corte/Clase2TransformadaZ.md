# Transformada Z de adelantos y atrasos
Una herramienta matemática fundamental para el análisis y diseño de sistemas de control digital es la Transformada Z. La Transformada Z permite convertir ecuaciones en diferencias, que describen la dinámica de sistemas discretos, en expresiones algebraicas más sencillas, de manera similar a la aplicación de la Transformada de Laplace en sistemas continuos. Esto facilita el diseño de controladores digitales que operan en tiempo discreto y el análisis de características del sistema como la estabilidad y el comportamiento transitorio. En el campo de la ingeniería, la Transformada Z es esencial para comprender cómo reaccionan los sistemas a diversas entradas y maximizar su rendimiento en aplicaciones donde las señales se muestran y procesan digitalmente, como en microcontroladores y sistemas de control automatizados.

## Indice
1. Representación matemática de los sistemas discretos
2. Solucion de Ecuaciones en Diferencias
3. Transformada Z
4. Sistemas Causales y no causales
5. Tiempo muerto en sistemas discretos
6. Conclusiones
7. Referencias

## 1. Representación matemática de los sistemas discretos
### 1.1. Ecuación en Diferencias: 
Una ecuación que muestra la relación entre los valores consecutivos de una secuencia y las diferencias entre ellos. A menudo se reorganizan como una fórmula recursiva para que la salida de un sistema pueda calcularse a partir de la señal de entrada y salidas pasadas. [1]

### 1.2. Ecuaciones en Diferencias No Lineales:
Las ecuaciones en diferencias lineales son aquellas en las que la relación entre las variables es lineal. Esto significa que cada término de la ecuación es una función lineal de la variable de estado o de entrada.[2] 

Estas ecuaciones se pueden expresar en una forma general como:

$$\[y(k) + a_1 y(k-1) + a_2 y(k-2) + \dots + a_n y(k-n) = b_0 u(k) + b_1 u(k-1) + \dots + b_m u(k-m)\]$$

>Donde:
* y(k) es la salida en el instante k.
* u(k) es la entrada en el instante k.
* $$\[ y(k) + a_1 y(k-1) + a_2 y(k-2) + \dots + a_n y(k-n) = b_0 u(k) + b_1 u(k-1) + \dots + b_m u(k-m) \]$$

### 1.3. Ecuaciones en Diferencias Lineales:
Las ecuaciones en diferencias no homogéneas incluyen un término que no depende de la variable de estado, como una entrada o una fuerza externa. Su forma general es:
$$y(k) + a_1 y(k-1) + a_2 y(k-2) + \dots + a_n y(k-n) = b_0 u(k) + b_1 u(k-1) + \dots + b_m u(k-m)$$
Las ecuaciones homogéneas describen sistemas que no tienen una entrada externa y son útiles para estudiar la respuesta natural del sistema.

### 1.4. Ecuaciones en Diferencias No Homogéneas:
Las ecuaciones en diferencias no homogéneas incluyen un término que no depende de la variable de estado, como una entrada o una fuerza externa. Su forma general es:
$$y(k) + a1 * y(k-1) + a2 * y(k-2) + ... + an * y(k-n) = b0 * u(k) + b1 * u(k-1) + ... + bm * u(k-m)$$
Donde f(k) es una función que representa la entrada o una perturbación externa. Estas ecuaciones describen sistemas que responden a un estímulo externo

## 2. Solucion de Ecuaciones en Diferencias
### 2.1. *Métodos Iterativos:*
Este método consiste en calcular los valores sucesivos de la variable de estado de manera recursiva, utilizando los valores iniciales conocidos y aplicando la ecuación en diferencias repetidamente. Es especialmente útil para ecuaciones en diferencias lineales de primer orden o de bajo orden.
Ejemplo: Si tienes una ecuación en diferencias de primer orden:
$$y(k) = 0.5 \cdot y(k-1) + u(k)$$
Puedes calcular $y(k)$ para $k = 1, 2, 3 ...$ usando un valor inicial $y(0)$ y la secuencia de valores de $u(k)$

### 2.2. *Transformada Z de ecuacioens en diferencias*
La Transformada Z es una herramienta poderosa para resolver ecuaciones en diferencias, especialmente en el análisis de sistemas de control digital. Este método convierte la ecuación en diferencias en una ecuación algebraica en el dominio Z, que es más fácil de manipular.

####  Pasos básicos:
* Aplicar la Transformada Z: Conviertes la ecuación en diferencias en una ecuación en términos de la variable Z.
* Resolver la ecuación algebraica: Despejas la variable de interés en el dominio Z.
* Aplicar la Transformada Z inversa: Conviertes la solución obtenida en el dominio Z de vuelta al dominio del tiempo discreto, obteniendo la secuencia de valores de la variable de estado.

💡**Ejemplo 1:** Para la ecuación en diferencias 
$$yh(k) - 0.5 \cdot y(k-1) = u(k)$$
La solución general de la ecuación homogénea asociada es:
$$Y(z) - 0.5z^{-1} Y(z) = U(z)$$
Despejando $Y(z)$:
$$Y(z) = \frac{U(z)}{1 - 0.5z^{-1}}$$
Luego, aplicamos la Transformada Z inversa para encontrar $y(k)$

## 3. Transformada Z
### 3.1. Transformada Z de un Atraso
La Transformada Z es una herramienta matemática utilizada en el análisis y diseño de sistemas discretos. Es particularmente útil en el procesamiento digital de señales y en el control de sistemas discretos.

Dada una secuencia de tiempo discreto $x[n]$, la Transformada Z de $x[n]$ se define como:

$$X(z) = \sum_{n=-\infty}^{\infty} x[n] z^{-n}$$

donde $Z$ es una variable compleja.

### 3.2. Atraso de una Secuencia
Un atraso de $k$ unidades en una secuencia discreta $x[n]$ se representa como $x[n−k]$. Esto significa que cada valor de la secuencia se retrasa $k$ pasos en el tiempo.
Para encontrar la Transformada Z de la secuencia retrasada $x[n−k]$, utilizamos la propiedad del atraso de la Transformada Z:

$$\mathcal{Z}\{x[n - k]\} = z^{-k} X(z)$$

>Donde
* $Z{⋅}$ denota la Transformada Z
* $x[n−k]$ es la secuencia original retrasada por $k$ unidades
* $X(z)$ es la Transformada Z de la secuencia original $x[n]%
* $z^{-k}$ es un factor de escala que representa el atraso.

### 3.2. Transformada Z de un Adelanto
En el contexto de señales y sistemas discretos, un adelanto en una secuencia se refiere a la operación en la que cada valor de la secuencia se avanza o se adelanta en el tiempo. Dada una secuencia discreta $x[n]$, un adelanto de $k$ unidades en la secuencia se representa como $x[n+k]$. Esto significa que cada valor de la secuencia se adelanta 
$k$ pasos en el tiempo.

Para encontrar la Transformada Z de la secuencia adelantada  $x[n+k]$, utilizamos la propiedad del adelanto de la Transformada Z:

$$\mathcal{Z}\{x[n + k]\} = z^k X(z)$$

>Donde
* $Z{⋅}$ denota la Transformada Z
* $x[n+k]$ es la secuencia original adelantada por $k$ unidades
* $X(z)$ es la Transformada Z de la secuencia original $x[n]%
* $z^{k}$ es un factor de escala que representa el adelanto.


### 3.3 Funcion de tranferencia discreta
La función de transferencia de un sistema discreto es una representación matemática que relaciona la entrada y la salida del sistema en el dominio Z. Se define como el cociente entre la Transformada Z de la salida y la Transformada Z de la entrada, bajo condiciones iniciales nulas.
Si $X(z)$ es la Transformada Z de la entrada $x[n]$ y $Y(z)$ es la Transformada Z de la salida $y[n]$, la función de transferencia $H(z)$ se define como:
$$H(z) = \frac{Y(z)}{X(z)}$$

>Donde
* $Y(z)$ es la Transformada Z de la salida del sistema.
* $X(z)$ es la Transformada Z de la entrada del sistema.

### 3.4 Pasar de una función de transferencia en atraso a adelanto
Se tiene una función de transferencia en el dominio Z que involucra un atraso. 
La función de transferencia en atraso es:

$$H(z) = \frac{Y(z)}{X(z)}$$

donde $Y(z)$ y $X(z)$ están relacionadas a través del atraso en el tiempo.
$z^{-k} \text{ a } \frac{a}{z^k}$ donde $k$ es el número de unidades de tiempo en el que se adelanta la secuencia.

#### 3.4.1 Proceso 
Se tiene una función de transferencia en atraso que tiene el siguiente formato:
$$H(z) = \frac{b_0 + b_1 z^{-1} + b_2 z^{-2}}{1 + a_1 z^{-1} + a_2 z^{-2}}$$

Aquí, los coeficientes 

$$H(z) = \frac{b_0 + b_1 z^{-1} + b_2 z^{-2}}{1 + a_1 z^{-1} + a_2 z^{-2}}$$

determinan la función de transferencia.

#### Multiplica por Potencias de z:
Para convertir el atraso en adelanto, multiplica el numerador y el denominador por $z^k$ donde $k$ es el número de unidades de adelanto. Si, por ejemplo, deseas adelantar la función por $k=2$ unidades, multiplicas por $z^2$ :

$$H(z) = \frac{z^2 (1 + a_1 z^{-1} + a_2 z^{-2})}{z^2 (b_0 + b_1 z^{-1} + b_2 z^{-2})}$$

Simplificando, obtiene:

$$\[ H(z) = \frac{1 + a_1 z + a_2 z^2}{b_0 z^2 + b_1 z + b_2} \]$$

Esta es la función de transferencia equivalente que ahora está en el formato de adelanto.

## 4. Sistemas Causales y no causales
>🔑 *Causales:*
Un sistema causal es aquel cuyo comportamiento en cualquier instante de tiempo depende únicamente de valores presentes y pasados de la entrada. En otras palabras, un sistema es causal si no reacciona a eventos futuros. Esta propiedad es fundamental en sistemas físicos y de procesamiento de señales reales porque no se puede anticipar el futuro.

### Caracteristicas:
* Pueden ser implementados en hardware y software de manera práctica.
* Ejemplos incluyen filtros digitales en procesamiento de señales y sistemas de control.
 
>🔑 *No Causales:*
Un sistema no causal es aquel cuyo comportamiento puede depender de valores futuros de la entrada. En otras palabras, un sistema no causal puede anticipar los valores futuros de la entrada para producir una salida en el presente. Los sistemas no causales son más teóricos en muchos contextos porque no son realizables en la práctica; requieren conocimiento de la entrada futura.

### Caracteristicas:
* A menudo utilizados en análisis y diseño teórico.
* Pueden ser aproximados mediante técnicas como el "retardo causal" para hacerlos realizables.

## 5. Tiempo muerto en sistemas discretos

El tiempo muerto en sistemas discretos se refiere al tiempo que transcurre entre la aplicación de una entrada y la observación de una respuesta correspondiente en la salida del sistema. Es una característica importante a tener en cuenta en el análisis y diseño de sistemas discretos, especialmente en sistemas de control y procesamiento de señales.

## 6. Conclusiones
* La representación matemática de los sistemas discretos proporciona una manera precisa de modelar y analizar cómo un sistema responde a las entradas. Utiliza herramientas como ecuaciones en diferencias y funciones de transferencia para describir el comportamiento dinámico del sistema. La representación matemática permite la aplicación de técnicas de análisis y diseño en el dominio z, facilitando la comprensión de cómo el sistema maneja las señales discretas.
* La Transformada Z es una herramienta crucial en el análisis de sistemas discretos, proporcionando una representación en el dominio z de señales y sistemas. Permite transformar ecuaciones en diferencias en funciones algebraicas más manejables, facilitando el análisis de estabilidad, control de sistemas. La Transformada Z es análoga a la Transformada de Laplace en sistemas continuos, y su uso simplifica el diseño y análisis de sistemas en el dominio de la frecuencia discreta. 

## 7. Referencias
[1] CHAPRA, S.C. y CANALE, R.P M´etodos Numéricos para Ingenieros. McGraw-Hill, 1987.

[2]  "Linear Systems and Signals" por B.P. Lathi (2ª edición, 2005).

[3]  "Discrete-Time Signal Processing" por Alan V. Oppenheim, Ronald W. Schafer y John R. Buck (3ª edición, 2010).

[4] "Modern Control Engineering" por Ogata Katsuhiko (5ª edición, 2010).

