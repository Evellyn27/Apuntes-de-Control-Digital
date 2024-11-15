# Observadores de estados y error de estado estacionario
Los observadores de estados son herramientas fundamentales en la teoría y práctica del control de sistemas dinámicos, ya que permiten la estimación precisa de los estados internos de un sistema cuando estos no pueden ser medidos directamente. En muchos sistemas reales, debido a limitaciones en los sensores o a la complejidad inherente al sistema, los estados que determinan su comportamiento dinámico no siempre están disponibles. En este sentido, los observadores de estados ofrecen una solución eficaz al reconstruir estos estados a partir de las entradas y salidas observables del sistema. De este modo, posibilitan el diseño de controladores capaces de mantener un desempeño óptimo y estable, incluso en ausencia de mediciones directas de los estados. Además, la capacidad de estimar correctamente los estados internos de un sistema se convierte en un factor crucial para garantizar la precisión y la eficiencia del control, especialmente en sistemas complejos, donde la estabilidad y el rendimiento a largo plazo dependen directamente de una adecuada estimación de dichos estados.
## Índice
1. Eliminación de error de estado estacionario
2. Observadores de estados
3. Ejercicios
4. Conclusiones

## 1. Eliminación de Error de Estado Estacionario
El error de estado estacionario es la diferencia persistente entre la salida real y la salida deseada en un sistema de control. Este error puede ocurrir incluso después de que la respuesta transitoria ha decaído, dejando solo la respuesta en estado estable. Para asegurar que el sistema alcance y mantenga el valor objetivo sin desviaciones, se utilizan técnicas de control como **regulación** y **servo**.

> 🔑 *Error de estado estacionario:* Es el error residual que permanece después de que las dinámicas transitorias han desaparecido, afectando la precisión en el estado estable.

### 1.1. Cálculo del Error de Estado Estacionario
La ecuación que describe el error de estado estacionario en un sistema de control es:

$$
e_{ss} = r_{ss} - y_{ss}
$$

donde:
- \( e_{ss} \) es el error de estado estacionario,
- \( r_{ss} \) es la referencia en estado estable, y
- \( y_{ss} \) es la salida en estado estable.

### 1.2. Técnicas para la Eliminación del Error de Estado Estacionario
Existen dos métodos principales para abordar el error de estado estacionario en sistemas de control:

**Regulación:** La regulación es una técnica en la que la referencia del sistema se establece en cero, buscando que todos los estados se mantengan en valores de equilibrio. Esto significa que el sistema debe controlar las salidas para que:
 
  $$
  r(t) = 0
  $$
  
**Servo:** A diferencia de la regulación, en un sistema de tipo servo, la referencia no es cero. En este caso, el objetivo es que el sistema siga una referencia deseada, de modo que la salida alcance y se mantenga en ese valor de referencia en estado estable. En este caso, se busca que:
 
  $$
  y_{\infty} = r_{\infty}
 $$

En ambos casos, el objetivo final es minimizar el error de estado estacionario, logrando que:

$$
e_{ss} = 0
$$

### 1.3. Seguimiento Integral con Vector de Ganancias $F$
Para lograr la eliminación del error de estado estacionario en sistemas donde es necesario que la salida siga una referencia específica, se emplea el seguimiento integral, esta técnica incorpora un término integral en la ley de control, permitiendo que el sistema ajuste continuamente su salida hasta igualar la referencia, incluso si ésta es distinta de cero.  En esencia, el seguimiento integral es especialmente útil en sistemas tipo servo, donde el objetivo es que la salida del sistema alcance y mantenga una referencia constante distinta de cero. A continuación se presentan los pasos clave para implementar esta técnica.

#### Definición de la Ley de Control
La ley de control propuesta incluye un término de retroalimentación de los estados y un término adicional que aplica el vector de ganancias $F$ a la referencia:

$$
u(k) = -Kx(k) + Fr(k)
$$

donde:

- \( K \) es el vector de ganancias de los estados,
- \( F \) es el vector de ganancias aplicado a la referencia $r(k)$, que ayuda a guiar la salida hacia el valor deseado.

#### Incorporación de la Ley de Control en las Ecuaciones de Estado
La ecuación de estado inicial del sistema sin control es:

$$
x(k+1) = Ax(k) + Bu(k)
$$

Sustituyendo $u(k) = -Kx(k) + Fr(k),$ la ecuación de estado se convierte en:

$$
x(k+1) = A x(k) + B(-Kx(k) + Fr(k))
$$

Simplificando, obtenemos:

$$
x(k+1) = (A - BK)x(k) + BFr(k)
$$

La salida del sistema está dada por:

$$
y(k) = Cx(k)
$$

#### Variable de Estado Adicional $v(k)$
Para mejorar el control y compensar la referencia, se introduce una nueva variable de estado \( v(k) \) que acumula el error entre la referencia y la salida. Esta variable permite un ajuste continuo que ayuda a eliminar el error de estado estacionario.

La ecuación para $v(k)$ es:

$$
v(k+1) = v(k) + (r(k) - y(k))
$$

donde:

- \( v(k+1) \) es el nuevo valor de \( v \) en el tiempo \( k+1 \),
- \( r(k) \) es la referencia en el instante \( k \),
- \( y(k) \) es la salida en el instante \( k \).

#### Reemplazando la Salida \( y(k) \) en la Ecuación de Estados
Al reemplazar la expresión de \( y(k) = Cx(k) \) en la ecuación del estado integral, obtenemos:

$$
v(k+1) = v(k) + r(k) - Cx(k)
$$

Integrando la nueva variable de estado $v(k)$ en el sistema, las ecuaciones de estado se amplían de la siguiente forma:
Para el estado $x(k)$:
 
   $$
   x(k+1) = Ax(k) + Bu(k)
   $$
   
 Para el estado \( v(k) \):
 
   $$
   v(k+1) = v(k) + (r(k) - y(k))
   $$
   
 La salida \( y(k) \) es:
 
   $$
   y(k) = Cx(k)
   $$

#### Representación del Sistema en Forma Matricial
Combinando las ecuaciones anteriores, obtenemos el sistema ampliado en forma matricial:

$$
\begin{bmatrix} x(k+1) \\
v(k+1) \end{bmatrix} = \begin{bmatrix} A & 0 \\
-C & 1 \end{bmatrix} \begin{bmatrix} x(k) \\
v(k) \end{bmatrix} + \begin{bmatrix} B \\
0 \end{bmatrix} u(k) + \begin{bmatrix} 0 \\
1 \end{bmatrix} r(k)
$$

La ecuación de salida es:

$$
y(k) = \begin{bmatrix} C & 0 \end{bmatrix} \begin{bmatrix} x(k) 
\\ v(k) \end{bmatrix}
$$

#### Redefinición de la Ley de Control con el Seguimiento Integral

Al incluir el estado $v(k)$ en la ley de control, la señal de entrada $u$ se redefine como:

$$
u = -Kx + K_i v
$$

donde \( K_i \) es la ganancia asociada al estado integral \( v \). De forma ampliada, la ley de control se representa como:

$$
u = -[K \quad K_i] \begin{bmatrix} x \\ v \end{bmatrix}
$$

#### Reescritura del Sistema con Matrices Ampliadas

Para implementar el seguimiento integral, se reescribe el sistema utilizando matrices ampliadas que incluyen tanto los estados originales como el estado integral.

**Sistema Ampliado con Ley de Control Aplicada:**

Con la ley de control  $u = -K_a x_a + B_r r$ 

donde:

$$x_a =\begin{bmatrix} x \\ v \end{bmatrix}$$

es el vector de estados ampliado, el sistema se puede expresar como:

$$x_a(k+1) = A_a x_a + B_a u + B_r r$$

y la salida es:
     
$$
y(k) = C_a x_a
$$

Donde:
    
$$A_a = \begin{bmatrix} A & 0 \\
-C & 1 \end{bmatrix} ,$$
     
$$B_a = \begin{bmatrix} B \\
 0 \end{bmatrix} ,$$
 
$$C_a = \begin{bmatrix} C & 0 \end{bmatrix} ,$$
     
$$B_r = \begin{bmatrix} 0 \\
 1 \end{bmatrix}$$

**Sustitución de la Ley de Control en el Sistema Ampliado:**

 Al aplicar la ley de control $$u = -K_a x_a $$ en la ecuación del sistema ampliado, obtenemos:
 
$$
x_a(k+1) = A_a x_a + B_a(-K_a x_a) + B_r r
$$

**Expansión de la Ecuación de Estados:**

Simplificando la ecuación de estados, tenemos:

$$
x_a(k+1) = A_a x_a - B_a K_a x_a + B_r r
$$

**Forma Simplificada del Sistema Ampliado:**

Finalmente, la ecuación de estados ampliada se puede expresar como:

$$
x_a(k+1) = (A_a - B_a K_a)x_a + B_r r
$$

**Salida del Sistema Ampliado:**

La salida \( y(k) \) en función del estado ampliado es:

$$
y(k) = C_a x_a
$$

### 2. Observadores de Estados  
En sistemas dinámicos, los controladores por retroalimentación de estados requieren información de todas las variables internas para operar eficazmente, sin embargo, medir todas las variables puede ser impráctico debido a limitaciones técnicas o económicas, en ese sentido, los observadores de estados resuelven este problema al estimar las variables internas no medibles, utilizando únicamente las entradas $u(k)$ y las salidas  $y(k)$ conocidas del sistema, donde se ajusta continuamente estas estimaciones mediante retroalimentación del error entre la salida medida y la salida estimada, este ajuste dinámico garantiza que las estimaciones converjan rápidamente a los valores reales, proporcionando precisión y estabilidad al sistema controlado.  

### 2.1. Dinámica del Error de Estimación

La efectividad de un observador de estados se evalúa a través de la dinámica del error de estimación, definida como la diferencia entre el estado real del sistema $x(k)$ y el estado estimado $\hat{x}(k):$

$$
e(k) = x(k) - \hat{x}(k)
$$

Para analizar la evolución de este error, consideramos las ecuaciones del sistema y del observador:

**Ecuación del sistema original:**

$$
x(k+1) = A x(k) + B u(k)
$$

**Ecuación del observador:**

$$
\hat{x}(k+1) = A \hat{x}(k) + B y(k) + K_p \left( y(k) - C \hat{x}(k) \right)
$$

En esta última ecuación, $K_p$ representa la matriz de ganancias del observador, y el término $K_p \left( y(k) - C \hat{x}(k) \right)$ corrige continuamente la estimación del estado. Esta corrección se basa en la diferencia entre la salida medida $y(k)$ y la salida estimada $C \hat{x}(k),$ lo que permite ajustar el estado estimado para reducir el error de estimación.

La ecuación dinámica del error se obtiene restando las ecuaciones del sistema y del observador:

$$
x(k+1) - \hat{x}(k+1) = A x(k) + B u(k) - \left( A \hat{x}(k) + B u(k) + K_p (y(k) - C \hat{x}(k)) \right)
$$

Simplificando, se obtiene:

$$
e(k+1) = (A - K_p C) e(k)
$$

Esta ecuación muestra que la dinámica del error de estimación depende de la matriz $A - K_p C.$ La elección de la ganancia $K_p$ es clave, ya que determina la rapidez con la que el error de estimación se reduce y el observador logra una convergencia hacia el estado real del sistema.

### 2.2. Procedimiento de Diseño del Observador

Para diseñar un observador de estados, se sigue un procedimiento sistemático que asegura que la estimación del estado sea precisa y estable. Este procedimiento incluye los siguientes pasos:

#### Comprobar la Observabilidad

Es indispensable que el sistema sea observable para que el diseño de un observador sea viable. La observabilidad de un sistema se verifica mediante la matriz de observabilidad $\mathcal{O}:$

$$
\mathcal{O} = \begin{bmatrix} C \\
 C A \\
 C A^2 \\
 \vdots \\
 C A^{n-1} \end{bmatrix}
$$

Si el rango de la matriz $\mathcal{O}$ es igual al número de estados $n,$ el sistema es observable y es posible diseñar un observador que estime con precisión el estado.

#### Determinación de los Coeficientes del Polinomio Característico

Para el diseño de la matriz de ganancias $K_p,$ se debe calcular el polinomio característico del sistema descrito por la matriz $A.$ Este polinomio se obtiene al resolver:

$$
\det(sI - A) = s^n + a_1 s^{n-1} + \dots + a_n
$$

#### Cálculo de la Matriz $Q$

La matriz $Q$ se utiliza para transformar el sistema en una forma canónica observable si es necesario. Para sistemas en forma canónica observable, se establece que $Q = I.$ En otros casos, la matriz $Q$ se calcula multiplicando matrices de transformación $W$ y $V$ como sigue:

$$
Q = W \cdot V
$$

#### Selección del Polinomio Deseado

Para lograr que el error de estimación converja rápidamente a cero, se seleccionan los polos deseados del observador. Estos polos deben colocarse en posiciones que aseguren una convergencia rápida del observador. El polinomio deseado del observador se expresa como:

$$
P_{\text{deseado}}(z) = (z + \alpha_1)(z + \alpha_2) \dots (z + \alpha_n)
$$

#### Cálculo de la Matriz de Ganancias del Observador

Finalmente, la matriz de ganancias $K_p$ se calcula utilizando el polinomio deseado y el polinomio característico del sistema. La fórmula para $K_p$ es:

$$
K_p = Q^{-1} \begin{bmatrix} \alpha_n - a_n \\
\alpha_{n-1} - a_{n-1} \\
\vdots \\
\alpha_1 - a_1 \end{bmatrix}
$$

### 2.3. Consideraciones Clave en el Diseño del Observador

| **Aspecto**             | **Importancia**                                                                                 |
|--------------------------|-----------------------------------------------------------------------------------------------|
| **Observabilidad**       | El sistema debe ser observable para garantizar una estimación confiable de los estados.       |
| **Ubicación de polos**   | Los polos del observador deben ser más rápidos que los del sistema para asegurar la convergencia del error. |
| **Modelo del sistema**   | Es fundamental conocer las matrices \( A, B, C \) para construir el observador.                |
| **Ganancias \( K_p \)**  | La matriz de ganancias \( K_p \) ajusta la dinámica del error, garantizando la estabilidad y rapidez de la estimación. |

💡**Ejemplo:**

#### 1. Sistema:
$$A = \begin{bmatrix} 1.799 & -0.8025 \\ 1 & 0 \end{bmatrix}$$
$$B = \begin{bmatrix} 0.01563 \\ 0 \end{bmatrix}$$
$$C = \begin{bmatrix} 0.01191 & 0.01107 \end{bmatrix}$$

#### 2. Ubicación de Polos:
$$z = -0.2,$$   $$z = -0.2$$

#### 3. Comprobación de Observabilidad:
La matriz de observabilidad 

$$O = \begin{bmatrix} C \\
CA \end{bmatrix} = \begin{bmatrix} 0.01191 & 0.01107 \\
0.03245 & -0.00955 \end{bmatrix}$$

$$\text{det}(O) = -0.00047,$$

Por lo que el sistema es observable.

#### 4. Polinomio Característico:
$$P(z) = z^2 - 1.799z + 0.8$$

#### 5. Polinomio Deseado:
$$(z + 0.2)^2 = z^2 + 0.4z + 0.04,$$ con $$\alpha_1 = 0.4,$$  $$\alpha_2 = 0.04$$

#### 6. Cálculo de Ganancias del Observador:
$$K_e = \begin{bmatrix} 0.0111 & -0.0295 \\
0.0119 & 0.0111 \end{bmatrix}$$

## 3. Ejercicio
📚 **Ejercicio 1:**

**Datos**:

$$A = \begin{bmatrix} 2.1 & -0.5 \\
1 & 0 \end{bmatrix}$$

$$B = \begin{bmatrix} 0.02 \\
0 \end{bmatrix}$$

$$C = \begin{bmatrix} 0.015 & 0.009 \end{bmatrix}$$

### Ubicación de Polos del Observador

Polos deseados: $$z = -0.3,$$  $$z = -0.3$$

### Comprobación de Observabilidad
Matriz de observabilidad:

$$
O = \begin{bmatrix} C \\
CA \end{bmatrix}, \quad CA = \begin{bmatrix} 0.0405 & -0.0075 \end{bmatrix}, \quad O = \begin{bmatrix} 0.015 & 0.009 \\
0.0405 & -0.0075 \end{bmatrix}
$$

Determinante:

$$
\det(O) = -0.000477 \quad (\text{observable})
$$

### Polinomio Característico de $A$

$$
P(z) = z^2 - 2.1z + 0.5
$$

### Matriz $Q$

Matriz $W:$

$$
W = \begin{bmatrix} 1 & 2.1 \\
0 & 1 \end{bmatrix}
$$

$$
Q = W = \begin{bmatrix} 1 & 2.1 \\
0 & 1 \end{bmatrix}
$$

### Polinomio Deseado
$$
(z + 0.3)^2 = z^2 + 0.6z + 0.09
$$

Coeficientes: 

$$\alpha_1 = 0.6,$$

$$\alpha_2 = 0.09.$$

### Cálculo de $K_e$

$$
K_e = Q^{-1} \begin{bmatrix} \alpha_2 - a_2 \\
\alpha_1 - a_1 \end{bmatrix} = \begin{bmatrix} 2.74 \\
-1.5 \end{bmatrix}
$$

## 4. Conclusiones
Conclusiones sobre el diseño de observadores de estados indican que:

En primer lugar, los observadores de estados permiten estimar todas las variables de estado de un sistema únicamente a partir de las medidas de su salida y las entradas conocidas. Esto resulta especialmente relevante en sistemas donde la medición directa de todas las variables de estado no es viable debido a limitaciones técnicas o económicas.

Además, es importante destacar que el diseño de un observador de estados depende de la condición de observabilidad del sistema. Esto implica que debe ser posible reconstruir los estados a partir de las entradas y salidas disponibles. En este sentido, cuando el sistema se encuentra en su forma canónicamente observable, los cálculos asociados al diseño del observador, como la determinación de las ganancias, se simplifican considerablemente, optimizando el proceso.

Por último, los observadores de estados representan una herramienta esencial en el control de sistemas dinámicos, ya que amplían las posibilidades de monitoreo y control en situaciones donde las mediciones directas son limitadas. Su correcta implementación garantiza un rendimiento eficiente y una mayor precisión en la estimación de estados críticos.



## Referencias
Agregue un subtítulo al final donde pueda poner todas las referencias consultadas incluyendo el origen o fuente de los ejercicios planteados. Tambien dentro del texto referencie los textos o artículos consultados y las figuras y tablas dentro de la explicación de las mismas.
