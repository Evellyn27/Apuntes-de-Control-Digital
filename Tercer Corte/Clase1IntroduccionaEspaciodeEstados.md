# Espacio de Estados
El espacio de estados es una representación matemática, la cual esta centrada en el análisis y diseño de sistemas dinámicos, donde toma en consideración tanto las entradas y salidas del sistema como sus variables internas, proporcionando una descripción completa de su comportamiento a lo largo del tiempo. Esta metodología es especialmente valiosa en el ámbito de los sistemas de control, ya que permite modelar de manera detallada sistemas dinámicos complejos, lo que facilita la comprensión de su evolución y la interacción entre sus componentes. Además, el enfoque de espacio de estados es particularmente útil para predecir el comportamiento de un sistema bajo diversas condiciones, permitiendo adaptar sus respuestas ante cambios en el entorno o en los parámetros del propio sistema. Esta capacidad de modelar y analizar sistemas con múltiples variables y entradas/salidas es esencial en aplicaciones que requieren alta precisión y flexibilidad, como en el control de procesos industriales, la automatización, y el diseño de sistemas embebidos, entre otros.

## Índice
1. Variables de Estado
2. Ecuaciones de Estado
3. Conversión de Ecuación Diferencial a Espacio de Estados
4. Ejercicios
5. Conclusiones
   

## 1. Variables de Estado
Las variables de estado son cruciales porque permiten capturar toda la información necesaria para entender y predecir el comportamiento de un sistema a lo largo del tiempo. A diferencia de otros enfoques, las variables de estado proporcionan una representación compacta y completa del sistema, sin necesidad de conocer su historial completo.

>🔑 *Variables de estados:* Son las variables internas que determinan el comportamiento dinámico de un sistema y permiten su descripción completa.
<p align="center">
  <img src="https://controlautomaticoeducacion.com/wp-content/uploads/2016/05/VE-300x148.png" />
</p>

Figura 1. Variables de estado

### 1.1. Consideraciones para la Selección de Variables de Estado
La selección de variables de estado es crucial para representar un sistema de forma efectiva, en ese sentido estas deben cumplir con las siguientes condiciones:
* Las variables de estado deben reflejar los aspectos clave del sistema.
* Deben ser suficientes para describir completamente el comportamiento del sistema.
* Solo se deben seleccionar variables que no sean redundantes.
* Las variables seleccionadas deben ser medibles o estimables fácilmente.

 💡**Ejemplo:** Sistema Masa-Resorte
 
En un sistema masa-resorte, las variables de estado podrían ser la posición y la velocidad de la masa, donde $$x_1(k)$$ representa la posición y $$x_2(k)$$ la velocidad.

- $$x_1(k) = x(k)$$ (posición de la masa)
- $$x_2(k) = v(k)$$ (velocidad de la masa)
  
## 2. Ecuaciones de Estado
Las ecuaciones de estado son fundamentales para el modelado de sistemas dinámicos, ya que permiten capturar su comportamiento a lo largo del tiempo. Estas ecuaciones expresan cómo el estado de un sistema, representado por un conjunto de variables, cambia en función de su estado anterior y de las entradas al sistema.

>🔑 *Estado:*Es un conjunto mínimo de variables necesarias para describir completamente su comportamiento en cualquier instante de tiempo.

### 2.1. Representación General
La representación general en espacio de estados utiliza un conjunto de ecuaciones para describir la evolución de las variables de estado. Este enfoque permite modelar tanto sistemas continuos como discretos:

* **Ecuación de estado:**
  
$$ X(k+1) = f(X(k), U(k), k)$$

* **Ecuación de salida:**
  
$$Y(k) = g(X(k), U(k), k) $$

### 2.2. Representación Matricial
Para sistemas lineales e invariantes en el tiempo (LTI), la representación en el espacio de estados se simplifica en forma matricial:

$$X(k+1) = A \cdot X(k) + B \cdot U(k)$$

Donde:
- $\( A \):$ Matriz de estado
- $\( B \):$ Matriz de control

$$Y(k) = C \cdot X(k) + D \cdot U(k)$$

Donde:
- $\( C \):$ Matriz de salida
- $\( D \):$ Matriz de transmisión directa


## 4. Procedimiento para Convertir una Ecuación en Diferencias a Espacio de Estados
Para representar una ecuación en diferencias en el espacio de estados, se sigue estos pasos:

**Paso 1: Despejar el Máximo Adelanto de la Ecuación en Diferencias**

Reorganiza la ecuación de modo que el término de máximo adelanto de la salida esté aislado en el lado izquierdo. Esto facilita identificar las relaciones entre las variables de estado y sus desplazamientos en el tiempo.
  
**Paso 2: Igualar la Salida a la Variable de Estado**

Define una variable de estado que represente la salida del sistema. Por ejemplo, si la salida es $y(k)$, establece $x_1=(k)$ donde $x_1$ será la primera variable de estado del sistema.

**Paso 3: Desplazar Sucesivamente para Obtener las Derivadas de las Variables de Estado**

Expresa las sucesivas variables de estado en función de los términos de adelanto o retardo. Esto implica identificar cómo cada variable de estado en $k+1$ o $k−1$ depende de otras variables de estado y de la entrada $u(k)$.

**Paso 4: Organizar los Términos en las Matrices A, B, C y D**

Una vez que se han obtenido las ecuaciones de primer orden para las variables de estado, se deben organizar los coeficientes en las matrices A, B, C y D para representar el sistema en espacio de estados. 

💡**Ejemplo:** 

La ecuación en diferencias es:

$$y(k+2) + y(k+1) + 0.16y(k) = 2u(k)$$

**Paso 1: Despejar la Máxima Derivada**

Despejamos  $y(k+2)$:

$$y(k+2) = -y(k+1) - 0.16y(k) + 2u(k)$$

**Paso 2: Igualar la Salida a la Variable de Estado**

Definimos las variables de estado. En este caso, seleccionamos $y(k)$ y $y(k+1)$ como nuestras variables de estado.

Definimos las siguientes variables de estado:

- $$y(k) = x_1(k)$$
- $$y(k+1) = x_2(k)$$

Entonces, tenemos:

$$y(k+1) = x_1(k+1) = x_2(k)$$

$$y(k+2) = x_2(k+1) = -x_2(k) - 0.16x_1(k) + 2u(k)$$

**Paso 3: Desplazar Sucesivamente para Obtener las Derivadas de las Variables de Estado**

Ahora desplazamos las ecuaciones para obtener las derivadas de las variables de estado. Esto se hace expresando las ecuaciones de primer orden para cada variable de estado, de modo que cada variable en k+1 dependa de sus valores anteriores y la entrada $$u(k)$$.

Para las variables de estado $$x_1 (k)$$ y $$x_2 (k):$$

$$x_1(k+1) = x_2(k)$$

$$x_2(k+1) = -x_2(k) - 0.16x_1(k) + 2u(k)$$

 **Paso 4: Organizar los Términos en las Matrices A, B, C y D**

Una vez obtenidas las ecuaciones de primer orden, organizamos los coeficientes en las matrices A, B, C y D para representar el sistema en espacio de estados.

$$X(k+1) = \begin{bmatrix} x_1(k+1) \\ x_2(k+1) \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ -0.16 & -1 \end{bmatrix} \begin{bmatrix} x_1(k) \\ x_2(k) \end{bmatrix} + \begin{bmatrix} 0 \\ 2 \end{bmatrix} u(k)$$

La salida $$y(k)$$ se expresa como:


$$y(k) = \begin{bmatrix} 1 & 0 \end{bmatrix} \begin{bmatrix} x_1(k) \\ x_2(k) \end{bmatrix} + [0] \cdot u(k)$$


## 5. Ejercicios
📚 **Ejercicio 1:** Convierte la siguiente ecuación en diferencias a su forma en espacio de estados:

$$y(k+2) - 0.5y(k+1) + 0.2y(k) = u(k)$$

Despejamos la derivada de mayor orden $$y(k+2)$$

$$y(k+2) = 0.5y(k+1) - 0.2y(k) + u(k)$$

Definimos las variables de estado. En este caso, seleccionamos $x_1(k)$ y $x_2(k)$ como nuestras variables de estado.

$$y(k) = x_1(k)$$

$$y(k+1) = x_2(k)$$

Entonces, tenemos:

$$y(k+1) = x_1(k+1) = x_2(k)$$

$$y(k+2) = x_2(k+1) = 0.5x_2(k) - 0.2x_1(k) + u(k)$$

Ahora desplazamos las ecuaciones para obtener:

$$x_1(k+1) = x_2(k)$$

$$x_2(k+1) = 0.5x_2(k) - 0.2x_1(k) + u(k)$$

Las ecuaciones se organizan de la siguiente forma para obtener el modelo en espacio de estados:

$$ X(k+1) = \begin{bmatrix} x_1(k+1) \\  x_2(k+1) \end{bmatrix} = \begin{bmatrix}   0 & 1 \\  -0.2 & 0.5 \end{bmatrix} 
\begin{bmatrix}  x_1(k) \\  x_2(k) \end{bmatrix} + \begin{bmatrix}   0 \\  1 \end{bmatrix} u(k)$$

La salida $y(k)$ se expresa como:

$$y(k) = \begin{bmatrix}   1 & 0 \end{bmatrix} \begin{bmatrix}   x_1(k) \\  x_2(k) \end{bmatrix} + [0] \cdot u(k)$$

📚 **Ejercicio 2:** Convierte la siguiente ecuación en diferencias a su forma en espacio de estados:

$$y(k+2) + 0.3y(k+1) + 0.5y(k) = 3u(k)$$

Despejamos la derivada de mayor orden $$y(k+2)$$

$$y(k+2) = -0.3y(k+1) - 0.5y(k) + 3u(k)$$

Definimos las variables de estado. En este caso, seleccionamos $x_1(k)$ y $x_2(k)$ como nuestras variables de estado.

$$y(k) = x_1(k)$$

$$y(k+1) = x_2(k)$$

Entonces, tenemos:

$$y(k+1) = x_1(k+1) = x_2(k)$$

$$y(k+2) = x_2(k+1) = -0.3x_2(k) - 0.5x_1(k) + 3u(k)$$

Ahora desplazamos las ecuaciones para obtener:

$$x_1(k+1) = x_2(k)$$

$$x_2(k+1) = -0.3x_2(k) - 0.5x_1(k) + 3u(k)$$

Las ecuaciones se organizan de la siguiente forma para obtener el modelo en espacio de estados:

$$X(k+1) = \begin{bmatrix}   x_1(k+1) \\  x_2(k+1) \end{bmatrix} = \begin{bmatrix}  0 & 1 \\  -0.5 & -0.3 \end{bmatrix} \begin{bmatrix}   x_1(k) \\  x_2(k) \end{bmatrix} + \begin{bmatrix}   0 \\  3 \end{bmatrix} u(k)$$

La salida $y(k)$ se expresa como:

$$y(k) = \begin{bmatrix}   1 & 0 \end{bmatrix} \begin{bmatrix}   x_1(k) \\  x_2(k) \end{bmatrix} + [0] \cdot u(k)$$

## 6. Conclusiones
Dentro de la temática del espacio de estados, se pueden destacar las siguientes conclusiones:

En primer lugar, el espacio de estados proporciona una representación matemática completa y versátil para modelar sistemas dinámicos complejos. Esta herramienta permite describir eficazmente sistemas con múltiples entradas y salidas, lo que facilita su análisis y control, ofreciendo una mayor claridad en la comprensión del comportamiento del sistema en función del tiempo.

Por otro lado, el espacio de estados ofrece una notable flexibilidad al permitir diversas representaciones para un mismo sistema, lo que permite adaptar el modelo según las necesidades específicas del diseño y control. Esta capacidad de transformar el sistema mediante cambios de coordenadas facilita la simplificación de su análisis, optimizando así la implementación de estrategias de control más efectivas y adaptadas al contexto.

Finalmente, se concluye que el uso del espacio de estados en el diseño de controladores resulta en soluciones más robustas y fiables. Al proporcionar una representación precisa de la dinámica del sistema, permite desarrollar estrategias de control que mejoran la estabilidad, la respuesta ante perturbaciones y la capacidad de adaptación del sistema, lo que es esencial en aplicaciones industriales y tecnológicas de alto rendimiento.

## Referencias

