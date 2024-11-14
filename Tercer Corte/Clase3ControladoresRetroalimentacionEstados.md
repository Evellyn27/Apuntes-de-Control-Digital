# Controladores por retroalimentación de estados
La retroalimentación de estados es una técnica utilizada en el control de sistemas dinámicos para influir en el comportamiento del sistema a través de las variables de estado. En este método, la señal de control se genera en función de los estados del sistema, lo que permite asignar los polos de lazo cerrado a ubicaciones específicas mediante ganancias proporcionales. Esto es útil en sistemas controlables y observables, donde se pueden establecer condiciones precisas para la estabilidad y desempeño deseado.
## Índice
1. Controlabilidad
2. Observabilidad
3. Diseño de Controladores por Retroalimentación de Estados
4. Ejercicios
5. Conclusiones
## 1. Controlabilidad 
La controlabilidad es una propiedad fundamental de los sistemas de control, que describe la capacidad de llevar el sistema desde un estado inicial $x(t0)$ a cualquier estado final deseado en un tiempo finito, utilizando entradas de control adecuadas, en ese sentido, un sistema es controlable si, para cualquier estado inicial y final, existe un conjunto de entradas que permita alcanzar el estado deseado. Esto asegura que el sistema responda a comandos específicos en todas sus variables de estado, haciendo posible un control efectivo y preciso sobre su comportamiento.
### 1.1. Matriz de Controlabilidad
La matriz de controlabilidad es una estructura matemática que se utiliza para verificar si un sistema es controlable. Para un sistema de ecuaciones en el espacio de estados representado por:


$$X(k+1) = AX(k) + Bu(k)$$


la matriz de controlabilidad $U$ está definida como:


$$U = [B \; AB \; A^2B \; \dots \; A^{n-1}B]$$


Esta matriz describe cómo las entradas de control afectan cada variable de estado a través de sus combinaciones con las potencias de la matriz $A.$ Las dimensiones de $U$ son las mismas que las de la matriz $A$, y si el determinante de $U$ es distinto de cero o si el rango de $U$ es igual a la cantidad de variables de estado, el sistema es controlable. Esto implica que todas las variables del sistema pueden ser gobernadas por las entradas de control y que es posible llevar el sistema a cualquier estado deseado en un intervalo de tiempo finito.

>🔑 *Determinante:* Valor calculado a partir de la matriz que, si es diferente de cero, indica controlabilidad.

💡**Ejemplo:** 

Consideremos el sistema descrito por:

$$
\begin{bmatrix} x_1(k+1) \\
x_2(k+1) \end{bmatrix} = \begin{bmatrix} 1.5 & 1 \\
1 & 0 \end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix} + \begin{bmatrix} 1 \\
0 \end{bmatrix} u(k)
$$

$$
y(k) = \begin{bmatrix} 2 & -1 \end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix}
$$

Para construir la matriz de controlabilidad $U,$ calculamos $B$ y $AB$ de la siguiente manera:

$$
U = [B \; AB]
$$

1. Primero, tenemos la matriz $B$:
   
  $$
   B = \begin{bmatrix} 1 \\
   0 \end{bmatrix}
   $$

2. Luego, calculamos $AB:$
   
 $$
   AB = \begin{bmatrix} 1.5 & 1 \\
   1 & 0 \end{bmatrix} \begin{bmatrix} 1 \\
   0 \end{bmatrix} = \begin{bmatrix} 1.5 \\
   1 \end{bmatrix}
  $$


Entonces, la matriz de controlabilidad $U$ es:

$$
U = \begin{bmatrix} B & AB \end{bmatrix} = \begin{bmatrix} 1 & 1.5 \\
0 & 1 \end{bmatrix}
$$


Para verificar la controlabilidad, calculamos el determinante de $U$:

$$
\det(U) = 1
$$

Dado que el determinante de $U$ es distinto de cero, el sistema es controlable.

## 2. Observabilidad

### 2.1. Matriz de Observabilidad
>🔑 *Definición:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.
 
💡**Ejemplo:** 

## 3. Diseño de Controladores por Retroalimentación de Estados
### 3.1 Condiciones de diseño
### 3.2 Metodología de diseño
💡**Ejemplo:** 

## 4. Ejercicios
📚 **Ejercicio 1:**
📚 **Ejercicio 2:**

## 5. Conclusiones
Las conclusiones derivadas del tema indican que:

En primer lugar, la observabilidad y la controlabilidad son parámetros esenciales para determinar si un problema de control tiene solución. Estas propiedades permiten asegurar que el sistema puede ser tanto observado como controlado de manera efectiva, lo que es crucial para garantizar su estabilidad y rendimiento a lo largo de su operación.

Por otro lado, el método de retroalimentación de estados facilita la ubicación de los polos del sistema en cualquier lugar del espacio de estados. Esta capacidad de ajuste permite una personalización precisa de la dinámica del sistema, optimizando su desempeño y estabilidad en función de los requisitos específicos del diseño de control.

Por último, cuando un sistema se encuentra en forma canónica controlable, se reduce significativamente la cantidad de cálculos necesarios para obtener las ganancias de retroalimentación. Esta simplificación favorece la eficiencia en el proceso de diseño, mejorando la optimización y el control de sistemas complejos de manera más precisa y efectiva.

## Referencias
[1] Cote B., J. E., Controladores por retroalimentación de estados, 8° semestre, 2022. [Diapositivas]. Consultado el 13 de noviembre de 2024.
