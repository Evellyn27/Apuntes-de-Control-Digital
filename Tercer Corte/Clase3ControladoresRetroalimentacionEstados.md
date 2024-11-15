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


La matriz \( U \) es fundamental para determinar la controlabilidad del sistema. A continuación, se presentan las características principales de \( U \):

| **Característica**                | **Descripción**                                                                                       |
|-----------------------------------|-------------------------------------------------------------------------------------------------------|
| **Dimensiones**                   | Las mismas que la matriz \( A \), lo que asegura que \( U \) puede relacionarse directamente con las variables de estado. |
| **Determinante de \( U \)**       | Si el determinante es distinto de cero, indica que el sistema es controlable.                          |
| **Rango de \( U \)**              | Cuando el rango de \( U \) es igual al número de variables de estado, el sistema es controlable.       |
| **Significado de Controlabilidad** | Todas las variables del sistema pueden ser gobernadas por las entradas de control.                     |
| **Implicación**                   | Permite llevar el sistema a cualquier estado deseado en un intervalo de tiempo finito.                 |


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

La observabilidad es una propiedad fundamental en los sistemas de control que permite determinar si es posible conocer el estado interno del sistema a partir de sus salidas y entradas a lo largo del tiempo. Un sistema es observable si, al analizar las salidas, es posible reconstruir su estado completo.

### 2.1. Características Clave de la Observabilidad

| **Característica**                          | **Descripción**                                                                                         |
|---------------------------------------------|---------------------------------------------------------------------------------------------------------|
| **Definición**                              | La observabilidad permite inferir el estado interno de un sistema mediante sus salidas y entradas.      |
| **Componente Matemático**                   | Se utiliza una construcción de matrices que combinan la matriz \( C \) con las potencias de la matriz \( A \).                             |
| **Condición para ser Observable**           | Un sistema es observable si el determinante de la matriz formada por \( C \) y las potencias de \( A \) es diferente de cero, o si su rango es igual al número de variables de estado. |
| **Importancia**                             | La observabilidad es clave para poder estimar el estado completo del sistema, incluso si no se tienen todas las variables directamente observadas.  |

### 2.2. Construcción de la Matriz de Observación

Para un sistema descrito por:

$$
X(k+1) = AX(k) + Bu(k)
$$

$$
y(k) = CX(k) + Du(k)
$$

La matriz de observación se define como:

$$
V = \begin{bmatrix} C \\
CA \\
CA^2 \\
\vdots \\
CA^{n-1} \end{bmatrix}
$$

Este conjunto de matrices refleja cómo cada estado se ve en las salidas del sistema a lo largo del tiempo, proporcionando la herramienta para verificar si el sistema es observable.

💡**Ejemplo:** 

Consideramos el siguiente sistema:

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

**Paso 1: Construcción de la matriz de observación $V$.**

La matriz $C$:
  
   $$C = \begin{bmatrix} 2 & -1 \end{bmatrix}$$

Calculamos $CA$:
   
  $$
   CA = \begin{bmatrix} 2 & -1 \end{bmatrix} \begin{bmatrix} 1.5 & 1 \\
   1 & 0 \end{bmatrix} = \begin{bmatrix} 2 & 2 \end{bmatrix}
  $$

La matriz de observación $V$ es:

$$
V = \begin{bmatrix} 2 & -1 \\
2 & 2 \end{bmatrix}
$$

**Paso 2: Verificación de la observabilidad.**

Calculamos el determinante de $V$:

$$
\det(V) = 6
$$

Como el determinante es distinto de cero, concluimos que el sistema es observable.

## 3. Diseño de Controladores por Retroalimentación de Estados
Los controladores por retroalimentación de estados son una técnica esencial en la teoría de control moderno. Su propósito es modificar el comportamiento dinámico del sistema al realimentar todas sus variables de estado. Esto permite asignar los polos del sistema en lazo cerrado en ubicaciones específicas, mejorando así la estabilidad, el tiempo de respuesta y la capacidad de rechazo a perturbaciones.

### 3.1 Condiciones de diseño
El diseño de controladores por retroalimentación de estados requiere cumplir con las siguientes condiciones:

- **Controlabilidad:**  
  El sistema debe ser completamente controlable, lo que implica que todas las variables de estado pueden ser controladas mediante la entrada. La matriz de controlabilidad $U$ se define como:
  
 $$
  U = [B \quad AB \quad A^2B \quad \dots \quad A^{n-1}B]
  $$
  
  **Condición:** El rango de $U$ debe ser igual al número de estados $n$.

- **Medición de Variables de Estado:**  
  Todas las variables de estado deben ser **medibles** o **estimables** mediante un observador.


### 3.2 Metodología de diseño
El proceso de diseño sigue estos pasos:

**Verificación de la Controlabilidad:**
   
   Calcular la matriz de controlabilidad $U$ y verificar que su rango sea $n$.

**Obtención del Polinomio Característico en Lazo Abierto:**
   
   Determinar el polinomio característico del sistema:
   
  $$
   |zI - A| = z^n + a_1z^{n-1} + \dots + a_n
  $$

**Definición del Polinomio Característico Deseado:**
   
   Especificar el polinomio deseado según los requisitos de desempeño:
    
   $$
   P_d(z) = z^n + \alpha_1z^{n-1} + \dots + \alpha_n
   $$

**Determinación de la Matriz de Transformación $T$:**
   
   Si el sistema no está en forma canónica controlable, se utiliza la matriz $T$ para transformar el sistema:
   
   $$
   T = UW^{-1}
   $$
   
   Donde $W$ es una matriz de Vandermonde basada en los coeficientes del polinomio característico.

**Cálculo de las Ganancias del Controlador:**
   
   Finalmente, se calculan las ganancias $K$:
   
   $$
   K = (\alpha - a)T^{-1}
   $$

💡**Ejemplo:** 

**Sistema:**  

$$
A = \begin{bmatrix} 
0 & 1 & 0 \\ 
0 & 0 & 1 \\ 
-1 & -5 & -6 
\end{bmatrix}, \quad 
B = \begin{bmatrix} 
0 \\ 
0 \\ 
1 
\end{bmatrix}
$$

**Polos Deseados:**  

$$
z_1 = -0.2 + j0.4, \quad z_2 = -0.2 - j0.4, \quad z_3 = -0.02
$$

**Matriz de Controlabilidad:**  

   $$
   U = [B \quad AB \quad A^2B] = 
   \begin{bmatrix} 
   0 & 0 & -1 \\ 
   0 & 1 & -5 \\ 
   1 & -5 & -6 
   \end{bmatrix}
   $$
   
   **Rango:** 3 → El sistema es controlable.

**Polinomio Característico en Lazo Abierto:** 

   $$
   P(z) = z^3 + 6z^2 + 5z + 1
   $$

**Polinomio Característico Deseado:**  

   $$
   P_d(z) = z^3 + 0.402z^2 + 0.2008z + 0.0004
   $$
   
**Cálculo de las Ganancias:**  

  $$
   K = [-0.996 \quad -4.799 \quad -5.598]
   $$

## 4. Ejercicios
📚 **Ejercicio 1: Verificación de Controlabilidad**

Dado el sistema definido por las matrices:

$$
A = \begin{bmatrix} 
0 & 1 & 0 \\ 
0 & 0 & 1 \\ 
-2 & -3 & -4 
\end{bmatrix}, \quad 
B = \begin{bmatrix} 
0 \\ 
1 \\ 
1 
\end{bmatrix}
$$

**Cálculo de la matriz de controlabilidad** \( U \):

$$
U = [B \quad AB \quad A^2B]
$$

\( AB \):
  
  $$
  AB = \begin{bmatrix} 
  0 & 1 & 0 \\ 
  0 & 0 & 1 \\
  -2 & -3 & -4 
  \end{bmatrix}
  \begin{bmatrix} 
  0 \\ 
  1 \\ 
  1 
  \end{bmatrix} = 
  \begin{bmatrix} 
  1 \\ 
  1 \\ 
  -7 
  \end{bmatrix}
  $$

 \( A^2B \):
  
  $$
  A^2B = A(AB) = 
  \begin{bmatrix} 
  0 & 1 & 0 \\ 
  0 & 0 & 1 \\ 
  -2 & -3 & -4 
  \end{bmatrix}
  \begin{bmatrix} 
  1 \\ 
  1 \\ 
  -7 
  \end{bmatrix} = 
  \begin{bmatrix} 
  1 \\ 
  -7 \\ 
  27 
  \end{bmatrix}
  $$

Ahora, \( U \) es:

$$
U = \begin{bmatrix} 
0 & 1 & 1 \\ 
1 & 1 & -7 \\ 
1 & -7 & 27 
\end{bmatrix}
$$

Se calcula el determinante de \( U \):

$$
\text{det}(U) = 
\begin{vmatrix} 
0 & 1 & 1 \\ 
1 & 1 & -7 \\ 
1 & -7 & 27 
\end{vmatrix} = 0(1 \times 27 - (-7)(-7)) - 1(1 \times 27 - (-7)(1)) + 1(1(-7) - 1(1)) = 54
$$

El determinante es distinto de cero, por lo tanto, el rango es 3 y el sistema es controlable.

📚 **Ejercicio 2:  Verificación de Observabilidad**

Considere el sistema representado por las siguientes matrices:

$$
A = \begin{bmatrix} 
1 & 2 & 0 \\ 
0 & 1 & 3 \\ 
0 & 0 & 1 
\end{bmatrix}, \quad 
C = \begin{bmatrix} 
1 & 0 & 1 
\end{bmatrix}
$$

**Cálculo de la matriz de observabilidad** \( V \):

$$
V = \begin{bmatrix} 
C \\ 
CA \\ 
CA^2 
\end{bmatrix}
$$

\( CA \):
  
  $$
  CA = \begin{bmatrix} 
  1 & 0 & 1 
  \end{bmatrix}
  \begin{bmatrix} 
  1 & 2 & 0 \\ 
  0 & 1 & 3 \\ 
  0 & 0 & 1 
  \end{bmatrix}  = 
  \begin{bmatrix} 
  1 & 2 & 1 
  \end{bmatrix}
  $$

\( CA^2 \):
  
  $$
  CA^2 = C(A^2) = 
  \begin{bmatrix} 
  1 & 0 & 1 
  \end{bmatrix}
  \begin{bmatrix} 
  1 & 2 & 0 \\ 
  0 & 1 & 3 \\ 
  0 & 0 & 1 
  \end{bmatrix}^2 =
  \begin{bmatrix} 
  1 & 4 & 7 
  \end{bmatrix}
  $$

Entonces:

$$
V = \begin{bmatrix} 
1 & 0 & 1 \\ 
1 & 2 & 1 \\ 
1 & 4 & 7 
\end{bmatrix}
$$

Se calcula el determinante de \( V \):

$$
\text{det}(V) = 
\begin{vmatrix} 
1 & 0 & 1 \\ 
1 & 2 & 1 \\ 
1 & 4 & 7 
\end{vmatrix} = 1(2 \times 7 - 4 \times 1) - 0 + 1(1 \times 4 - 1 \times 2) = 12
$$

El determinante es distinto de cero, por lo tanto, el rango es 3 y el sistema es observable.

## 5. Conclusiones
Las conclusiones derivadas del tema indican que:

En primer lugar, la observabilidad y la controlabilidad son parámetros esenciales para determinar si un problema de control tiene solución. Estas propiedades permiten asegurar que el sistema puede ser tanto observado como controlado de manera efectiva, lo que es crucial para garantizar su estabilidad y rendimiento a lo largo de su operación.

Por otro lado, el método de retroalimentación de estados facilita la ubicación de los polos del sistema en cualquier lugar del espacio de estados. Esta capacidad de ajuste permite una personalización precisa de la dinámica del sistema, optimizando su desempeño y estabilidad en función de los requisitos específicos del diseño de control.

Por último, cuando un sistema se encuentra en forma canónica controlable, se reduce significativamente la cantidad de cálculos necesarios para obtener las ganancias de retroalimentación. Esta simplificación favorece la eficiencia en el proceso de diseño, mejorando la optimización y el control de sistemas complejos de manera más precisa y efectiva.

## Referencias
[1] R. A. Palacios Ochoa. “Implementación de controladores por realimentación de estados y controlador PID aplicado a un motor de DC con dos masas mediante dspace”. Scielo. Accedido el 14 de noviembre de 2024. [En línea]. Disponible: http://scielo.senescyt.gob.ec/scielo.php?script=sci_arttext&amp;pid=S1390-67122017000100022
[2] Cote B., J. E., Controladores por retroalimentación de estados, 8° semestre, 2022. [Diapositivas]. Consultado el 13 de noviembre de 2024.
