# Operaciones en el Espacio de Estados

Las operaciones en el espacio de estados son esenciales para analizar sistemas dinámicos complejos, ya que permiten modelar su comportamiento mediante vectores de estado y matrices, ofreciendo una descripción completa de todas las configuraciones posibles. A partir de una función de transferencia, se puede obtener su representación en espacio de estados, que puede adoptar distintas formas canónicas, como la controlable, observable o diagonal, dependiendo del enfoque del análisis. Por tanto, el enfoque en el espacio de estados, complementado con el análisis del polinomio característico, no solo permite evaluar propiedades esenciales como la estabilidad y la dinámica del sistema, sino que también ofrece un marco versátil para abordar problemas de control.

## Índice
1. Obtención del Espacio de Estados
2. Análisis Dinámico en el Espacio de Estados
3. Conversión entre Espacio de Estados a Función de Transferencia
4. Ejercicios
5. Conclusiones
   
## 1. Obtención del Espacio de Estados
Para obtener el espacio de estados, se transforma el sistema original, descrito por una función de transferencia o ecuaciones diferenciales, en un conjunto de ecuaciones de primer orden. Esto se logra definiendo un vector de estado **$$x$$** que contiene las variables necesarias para describir el sistema en el tiempo. La dinámica del sistema se expresa con matrices: $$A,$$ que relaciona los estados; $$B,$$ que muestra cómo la entrada $$u$$ afecta al estado; $$C,$$ que conecta los estados con la salida $$y,$$ y $$D,$$ que representa el efecto directo de la entrada en la salida.
>🔑 *Canónica:* Se refiere a una forma estándar o estructurada de representar un sistema, generalmente en el contexto de funciones de transferencia, donde se identifican y organizan los coeficientes en matrices específicas para describir la dinámica del sistema.
### 1.1 Espacio de Estados a partir de Función de Transferencia
Para construir una representación en el espacio de estados a partir de una función de transferencia $$G(z)$$ se descompone la función de transferencia en una forma que permita identificar los coeficientes que definirán las matrices $A,$ $B,$ $C$ y $D,$ las cuales describen la dinámica del sistema en el dominio temporal.

Dada una función de transferencia general en el dominio $z:$

$$
G(z) = \frac{b_0 z^n + b_1 z^{n-1} + \dots + b_{n-1} z + b_n}{z^n + a_1 z^{n-1} + \dots + a_{n-1} z + a_n}
$$

la forma canónica se obtiene estructurando las matrices en función de los coeficientes $a_i$ y $b_i$ (del denominador y numerador, respectivamente) de la función de transferencia.

### 1.2 Representación en Formas Canónicas

La representación en formas canónicas organiza las matrices de espacio de estados para destacar propiedades como la controlabilidad y observabilidad, facilitando la manipulación del sistema. A continuación se presentan las tres formas canónicas más comunes:

- **Forma Canónica Controlable**

En esta forma, el sistema es controlable, lo cual significa que todos los estados pueden ser influenciados desde la entrada. Las matrices del sistema se estructuran así:

 $$
  A = \begin{bmatrix} 
       0 & 1 & 0 & \dots & 0 \\
       0 & 0 & 1 & \dots & 0 \\
       \vdots & \vdots & \vdots & \ddots & \vdots \\
       0 & 0 & 0 & \dots & 1 \\
       -a_n & -a_{n-1} & \dots & -a_1
   \end{bmatrix}
$$
  

$$
   B = \begin{bmatrix} 
       0 \\
       0 \\
       \vdots \\
       0 \\
       1 
   \end{bmatrix}, \quad C = \begin{bmatrix} b_n & b_{n-1} & \dots & b_1 \end{bmatrix}, \quad D = [0]
$$

💡**Ejemplo:**  

Dada la siguiente funcion de transferencia:

$$G(z) = \frac{z + 1}{z^2 + 1.3z + 0.4}$$

Los coeficientes del polinomio característico son $a_1 = 0.4$ y $a_2 = 1.3.$

* Ecuación de Estado:

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix} = A_c \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix} + B_c u(k)
$$

Sustituyendo las matrices:

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix} = \begin{bmatrix}
0 & 1 \\
-0.4 & -1.3
\end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix} + \begin{bmatrix} 1 \\
0 \end{bmatrix} u(k)
$$

* Ecuación de Salida:

$$
y(k) = C_c \begin{bmatrix} x_1(k) 
\\ x_2(k) \end{bmatrix}
$$

Sustituyendo la matriz $$C_c$$:

$$
y(k) = \begin{bmatrix} 1 & 0 \end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix}
$$


- **Forma Canónica Observable**
  
   Esta forma permite que todos los estados sean observables desde la salida del sistema, lo que facilita la estimación de estados internos a partir de mediciones:

$$
A = \begin{bmatrix} 
       0 & 0 & \dots & 0 & -a_n \\
       1 & 0 & \dots & 0 & -a_{n-1} \\
       0 & 1 & \dots & 0 & -a_{n-2} \\
       \vdots & \vdots & \ddots & \vdots & \vdots \\
       0 & 0 & \dots & 1 & -a_1
   \end{bmatrix}
$$


$$
   B = \begin{bmatrix} 
       b_n \\
       b_{n-1} \\
       \vdots \\
       b_1 
   \end{bmatrix}, \quad C = \begin{bmatrix} 1 & 0 & \dots & 0 \end{bmatrix}, \quad D = [0]
$$

💡**Ejemplo:** 

Retomando el ejemplo anteior se puefde expresar:

* Ecuación de Estado:

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix} = A_o \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix} + B_o u(k)
$$

Sustituyendo las matrices:

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix} = \begin{bmatrix}
0 & -0.4 \\
1 & -1.3
\end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix} + \begin{bmatrix} 1 \\
1 \end{bmatrix} u(k)
$$

* Ecuación de Salida:

$$
y(k) = C_o \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix}
$$

Sustituyendo la matriz $$C_o:$$

$$
y(k) = \begin{bmatrix} 0 & 1 \end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix}
$$

- **Forma Canónica Diagonal**

$$ \( P_1 = z_1; \, P_2 = z_2; \, \dots ; \, P_n = z_n \)$$  

   Cuando los polos del sistema son distintos, la matriz $A$ puede tomar una forma diagonal en la que cada elemento diagonal corresponde a un polo. Esta forma es útil para sistemas que pueden descomponerse en modos independientes:

 $$
   A = \begin{bmatrix} 
       P_1 & 0 & \dots & 0 \\
       0 & P_2 & \dots & 0 \\
       \vdots & \vdots & \ddots & \vdots \\
       0 & 0 & \dots & P_n
   \end{bmatrix}
$$

$$
   B = \begin{bmatrix} 
       1 \\
       1 \\
       \vdots \\
       1 
   \end{bmatrix}, \quad C = \begin{bmatrix} c_1 & c_2 & \dots & c_n \end{bmatrix}, \quad D = [0]
 $$

💡**Ejemplo:** 

La descomposición en fracciones parciales es:

$$
\frac{z + 1}{z^2 + 1.3z + 0.4} = \frac{C_1}{z + 0.8} + \frac{C_2}{z + 0.5}
$$

Se Multiplica por el denominador común

$$
z + 1 = C_1(z + 0.5) + C_2(z + 0.8)
$$

Expandiendo:

$$
z + 1 = C_1z + 0.5C_1 + C_2z + 0.8C_2
$$

Agrupamos los términos:

$$
z + 1 = (C_1 + C_2)z + (0.5C_1 + 0.8C_2)
$$

Comparando los coeficientes:

- Coeficiente de $z:$
  
 $$
  C_1 + C_2 = 1
$$

- Término independiente:
  
$$
  0.5C_1 + 0.8C_2 = 1
$$

Resolviendo el sistema de ecuaciones:

$$ C_1 + C_2 = 1 $$
$$ 0.5C_1 + 0.8C_2 = 1 $$

De la primera ecuación:

$$
C_1 = 1 - C_2
$$

Sustituyendo en la segunda ecuación:

$$
0.5(1 - C_2) + 0.8C_2 = 1
$$

Simplificando:

$$
0.5 - 0.5C_2 + 0.8C_2 = 1
$$

$$
0.3C_2 = 0.5
$$

$$
C_2 = \frac{5}{3}
$$

Sustituyendo en $C_1 = 1 - C_2\:$

$$
C_1 = 1 - \frac{5}{3} = -\frac{2}{3}
$$

Expresión final

$$
\frac{z + 1}{z^2 + 1.3z + 0.4} = \frac{-\frac{2}{3}}{z + 0.8} + \frac{\frac{5}{3}}{z + 0.5}
$$

* Ecuaciones de Estado

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix} =
\begin{bmatrix}
-0.8 & 0 \\
0 & -0.5
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k)
\end{bmatrix}+\begin{bmatrix}1 \\
1
\end{bmatrix}
u(k)
$$

* Ecuación de Salida

$$
y(k) =
\begin{bmatrix}
\frac{5}{3} & -\frac{2}{3}
\end{bmatrix}
\begin{bmatrix}
x_1(k) \\
x_2(k)
\end{bmatrix}
$$


## 2. Análisis Dinámico en el Espacio de Estados
El análisis dinámico en el espacio de estados es fundamental para estudiar el comportamiento temporal de un sistema. 
### 2.1 Polinomio Característico
El polinomio característico es fundamental para calcular los polos de un sistema en el espacio de estados. Estos polos están relacionados con los valores propios de la matriz $$A,$$ la cual describe las dinámicas del sistema en el espacio de estados. Los valores propios se encuentran resolviendo el polinomio característico, que se deriva del determinante de la matriz $$zI - A = 0,$$ donde $$I$$ es la matriz identidad y $$z$$ es la variable compleja asociada con los valores propios.

### 2.2 Raíces del Polinomio Característico

Para ilustrar cómo calcular las raíces del polinomio característico, se utiliza una matriz general $$A$$ de un sistema, cuyos polos se calcularán a partir de la ecuación característica derivada.

#### Paso 1: Formar la ecuación $$zI - A$$

La ecuación característica se obtiene restando la matriz $$A$$ multiplicada por la variable $$z$$ de la matriz identidad $$I$$:

$$
zI - A = \begin{bmatrix}
z & 0 & 0 \\
0 & z & 0 \\
0 & 0 & z
\end{bmatrix}
$$

- A
Este resultado dará lugar a una nueva matriz $$zI - A,$$ cuya determinante es el polinomio característico.

#### Paso 2: Calcular el determinante de $$zI - A$$

El siguiente paso consiste en calcular el determinante de la matriz $$zI - A.$$ Este determinante es el polinomio característico:

$$
\text{det}(zI - A) = p(z) = z^3 + a_2z^2 + a_1z + a_0
$$

#### Paso 3: Resolver el polinomio característico

El polinomio característico es una ecuación algebraica cuya solución se obtiene al encontrar las raíces de la ecuación:

$$
p(z) = 0
$$

Las raíces de esta ecuación corresponden a los polos del sistema, es decir, los valores propios de la matriz $$A.$$

💡**Ejemplo:** 

Consideremos el siguiente ejemplo con una matriz $$A$$ dada:

$$
A = \begin{bmatrix}
0 & -1 & 0 \\
0 & 0 & 1 \\
-6 & -11 & -6
\end{bmatrix}
$$

$$
zI - A = \begin{bmatrix}
z & 0 & 0 \\
0 & z & 0 \\
0 & 0 & z
\end{bmatrix} -\begin{bmatrix}
0 & -1 & 0 \\
0 & 0 & 1 \\
-6 & -11 & -6
\end{bmatrix}
= \begin{bmatrix}
z & 1 & 0 \\
0 & z & -1 \\
6 & 11 & z + 6
\end{bmatrix}
$$


$$
\text{det}(zI - A) = \begin{vmatrix}
z & 1 & 0 \\
0 & z & -1 \\
6 & 11 & z + 6
\end{vmatrix}
$$

- Calculamos este determinante por cofactores:

$$
= z \begin{vmatrix}
z & -1 \\
11 & z + 6
\end{vmatrix} -1\begin{vmatrix}
0 & -1 \\
6 & z + 6
\end{vmatrix}+ 0 \cdot \begin{vmatrix}
0 & z \\
6 & 11
\end{vmatrix}
$$

* Determinante de la primera submatriz:
  
$$
\[
\begin{vmatrix}
z & -1 \\
11 & z + 6
\end{vmatrix} = z(z + 6) - (-1)(11) = z^2 + 6z + 11
\]
$$

* Determinante de la segunda submatriz:

$$
\begin{vmatrix}
0 & -1 \\
6 & z + 6
\end{vmatrix} = 0(z + 6) - (-1)(6) = 6
$$

- Sustituyendo en la ecuación del determinante:

$$
\text{det}(zI - A) = z(z^2 + 6z + 11) - 1(6)
$$

$$
= z^3 + 6z^2 + 11z - 6
$$


El polinomio característico es:

$$
z^3 + 6z^2 + 11z - 6 = 0
$$

Para encontrar las raíces de esta ecuación, que corresponden a los polos del sistema, podemos factorizar el polinomio directamente:

$$
(z + 1)(z + 2)(z + 3) = 0
$$

Por lo tanto, los polos del sistema son:

$$
z = -1, \quad z = -2, \quad z = -3
$$


## 3. Conversión entre Espacio de Estados a Función de Transferencia

La conversión entre el espacio de estados y la función de transferencia es un proceso fundamental en el análisis y diseño de sistemas dinámicos, tanto continuos como discretos. A través de este procedimiento, se puede obtener una representación en el dominio de Laplace (o Z para sistemas discretos) de un sistema dinámico descrito por ecuaciones de espacio de estados.

#### 3.1 Procedimiento:

Consideremos un sistema discreto representado por las siguientes ecuaciones en espacio de estados:

$$\mathbf{x}(k+1) = A \mathbf{x}(k) + B \mathbf{u}(k)$$

$$\mathbf{y}(k) = C \mathbf{x}(k) + D \mathbf{u}(k)$$


Donde:
- $\mathbf{x}(k)$ es el vector de estado.
- $\mathbf{u}(k)$ es el vector de entrada.
- $\mathbf{y}(k)$ es el vector de salida.
- $A, B, C, D$ son matrices de dimensiones adecuadas.

El objetivo es encontrar la función de transferencia $G(z) = \frac{Y(z)}{U(z)},$ que es la relación entre la salida $Y(z)$ y la entrada $U(z)$ en el dominio $z.$

**Paso 1: Transformación de la ecuación en espacio de estados al dominio Z**:  
   Aplicando la Transformada Z a las ecuaciones en espacio de estados, obtenemos las siguientes ecuaciones en el dominio Z:
   
  $$z \mathbf{X}(z) - \mathbf{x}(z) = A \mathbf{X}(z) + B \mathbf{U}(z)$$
   
  $$\mathbf{Y}(z) = C \mathbf{X}(z) + D \mathbf{U}(z)$$
   
**Paso 2: Despeje de $$\mathbf{X}(z)$$**:  
   Para despejar $$\mathbf{X}(z),$$ se resuelve la ecuación de estado:
   
  $$
   (zI - A) \mathbf{X}(z) = B \mathbf{U}(z)
  $$
   
   Entonces:
   
   $$
   \mathbf{X}(z) = (zI - A)^{-1} B \mathbf{U}(z)
  $$
   
   **Paso 3: Sustitución en la ecuación de salida**:  
   Sustituyendo la expresión de $$\mathbf{X}(z)$$ en la ecuación de salida:
   
  $$
   \mathbf{Y}(z) = C (zI - A)^{-1} B \mathbf{U}(z) + D \mathbf{U}(z)
   $$
   
   **Paso 4: Función de transferencia**:  
   Finalmente, la función de transferencia \( G(z) \) se obtiene como la relación entre $$\mathbf{Y}(z)$$ y $$\mathbf{U}(z)$$:
   
   $$
   G(z) = \frac{\mathbf{Y}(z)}{\mathbf{U}(z)} = C (zI - A)^{-1} B + D
  $$

## 5. Ejercicios

📚 **Ejercicio 1:**

Dada la siguiente función de transferencia discreta:

$$
G(z) = \frac{z + 2}{z^2 + 1.4z + 0.5}
$$

Se requiere realizar la representación en el espacio de estados de la función de transferencia, identificando las matrices de estado y salida.

1. **Obten los coeficientes del polinomio característico** de la función de transferencia. Los coeficientes son:  
   -  $a_1 = 0.5$
   -  $a_2 = 1.4$

2. **Ecuación de Estado:**

La ecuación de estado tiene la forma:

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix} = A \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix} + B u(k)
$$

Donde las matrices $A$ y $B$ deben ser determinadas a partir de los coeficientes obtenidos.

Sustituyendo las matrices:

$$
\begin{bmatrix}
x_1(k+1) \\
x_2(k+1)
\end{bmatrix} = \begin{bmatrix}
0 & 1 \\
-0.5 & -1.4
\end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix} + \begin{bmatrix} 1 \\
0 \end{bmatrix} u(k)
$$

3. **Ecuación de Salida:**

La ecuación de salida tiene la forma:

$$
y(k) = C \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix}
$$

Donde la matriz $$C$$ es:

$$
y(k) = \begin{bmatrix} 1 & 0 \end{bmatrix} \begin{bmatrix} x_1(k) \\
x_2(k) \end{bmatrix}
$$


📚 **Ejercicio 2:**
Consideremos la siguiente matriz \( A \):

$$
A = \begin{bmatrix}
1 & -1 & 0 \\
0 & 0 & 1 \\
-4 & -8 & -5
\end{bmatrix}
$$

Ahora, calculamos \( zI - A \):

$$
zI - A = \begin{bmatrix}
z & 0 & 0 \\
0 & z & 0 \\
0 & 0 & z
\end{bmatrix} - \begin{bmatrix}
1 & -1 & 0 \\
0 & 0 & 1 \\
-4 & -8 & -5
\end{bmatrix}
= \begin{bmatrix}
z - 1 & 1 & 0 \\
0 & z & -1 \\
4 & 8 & z + 5
\end{bmatrix}
$$

El determinante de \( zI - A \) es:

$$
\text{det}(zI - A) = \begin{vmatrix}
z - 1 & 1 & 0 \\
0 & z & -1 \\
4 & 8 & z + 5
\end{vmatrix}
$$

Calculamos este determinante por cofactores:

$$
= (z - 1) \begin{vmatrix}
z & -1 \\
8 & z + 5
\end{vmatrix} - 1 \begin{vmatrix}
0 & -1 \\
4 & z + 5
\end{vmatrix} + 0 \cdot \begin{vmatrix}
0 & z \\
4 & 8
\end{vmatrix}
$$

* Determinante de la primera submatriz:

$$
\begin{vmatrix}
z & -1 \\
8 & z + 5
\end{vmatrix} = z(z + 5) - (-1)(8) = z^2 + 5z + 8
$$

* Determinante de la segunda submatriz:

$$
\begin{vmatrix}
0 & -1 \\
4 & z + 5
\end{vmatrix} = 0(z + 5) - (-1)(4) = 4
$$

Sustituyendo en la ecuación del determinante:

$$
\text{det}(zI - A) = (z - 1)(z^2 + 5z + 8) - 1(4)
$$

$$
= (z - 1)(z^2 + 5z + 8) - 4
$$

Ahora expandimos el producto:

$$
= z(z^2 + 5z + 8) - 1(z^2 + 5z + 8) - 4
$$

$$
= z^3 + 5z^2 + 8z - z^2 - 5z - 8 - 4
$$

$$
= z^3 + 4z^2 + 3z - 12
$$

El polinomio característico es:

$$
z^3 + 4z^2 + 3z - 12 = 0
$$

$$
z_1 \approx -4.47, \quad z_2 \approx 0.21, \quad z_3 \approx -0.74
$$

## 6. Conclusiones
Las conclusiones derivadas del tema indican que:

En primer lugar, es posible obtener diversas representaciones del espacio de estados a partir de la función de transferencia del sistema, en ese sentido, esta flexibilidad ofrece una alternativa eficaz para modelar sistemas dinámicos, permitiendo transformar la información de una forma que se adapte mejor a las necesidades del análisis o diseño del sistema, facilitando su comprensión desde distintas perspectivas.

De igual manera, también es factible obtener la función de transferencia a partir de cualquiera de las representaciones en el espacio de estados, lo que establece una relación bidireccional entre ambos enfoques. Esta capacidad de conversión entre modelos amplía las herramientas disponibles y facilita la selección del enfoque más adecuado en función de los requerimientos del análisis o el control del sistema.

Finalmente, cuando se trabaja con representaciones de estados, es indispensable la aplicación de las operaciones básicas con matrices, tales como la aritmética matricial, transposición, determinación de determinantes e inversión de matrices, por ende, estas operaciones son esenciales para la manipulación de los modelos y para obtener soluciones precisas en el análisis de la estabilidad y el control de sistemas dinámicos, asegurando que se pueda modelar, optimizar y controlar el comportamiento del sistema con eficacia.

## Referencias
