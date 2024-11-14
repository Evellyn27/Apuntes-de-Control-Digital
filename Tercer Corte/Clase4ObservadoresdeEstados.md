# Observadores de estados y error de estado estacionario
El título de cada clase, correspondiente al tema general que se trabaje en clase. Siempre después de cada título de clase, redactar una breve introducción (mínimo un párrafo) que de una mirada general al tema
## Índice
1. Eliminación de error de estado estacionario
2. Observadores de estados
3. Metodologías de diseño
4. Ejercicios
5. Conclusiones
## 1.  Observadores de estados
Los observadores de estados son herramientas clave para estimar variables internas de un sistema que no pueden ser medidas directamente. Su implementación es fundamental en sistemas de control multivariable, permitiendo un control eficiente incluso con información incompleta.
### 1.1.
### 1.2.
### 1.3.

💡**Ejemplo:**
## 2. Eliminación de Error de Estado Estacionario
El error de estado estacionario es la diferencia persistente entre la salida real y la salida deseada en un sistema de control. Este error puede ocurrir incluso después de que la respuesta transitoria ha decaído, dejando solo la respuesta en estado estable. Para asegurar que el sistema alcance y mantenga el valor objetivo sin desviaciones, se utilizan técnicas de control como **regulación** y **servo**.

> 🔑 *Error de estado estacionario:* Es el error residual que permanece después de que las dinámicas transitorias han desaparecido, afectando la precisión en el estado estable.

### 2.1. Cálculo del Error de Estado Estacionario
La ecuación que describe el error de estado estacionario en un sistema de control es:

$$
e_{ss} = r_{ss} - y_{ss}
$$

donde:
- \( e_{ss} \) es el error de estado estacionario,
- \( r_{ss} \) es la referencia en estado estable, y
- \( y_{ss} \) es la salida en estado estable.

### 2.2. Técnicas para la Eliminación del Error de Estado Estacionario
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

### 2.3. Seguimiento Integral con Vector de Ganancias $F$
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
Con la ley de control $$ u = -K_a x_a + B_r r,$$ donde $$ x_a = \begin{bmatrix} x\\
v \end{bmatrix} $$ es el vector de estados ampliado, el sistema se puede expresar como:
    
     $$
     x_a(k+1) = A_a x_a + B_a u + B_r r
     $$
     
     y la salida es:
     
     $$
     y(k) = C_a x_a
     $$
     
   - Donde:
    
     $$A_a = \begin{bmatrix} A & 0 \\
      -C & 1 \end{bmatrix} ,$$
     
    $$B_a = \begin{bmatrix} B \\
 0 \end{bmatrix} ,$$
 
     $$C_a = \begin{bmatrix} C & 0 \end{bmatrix} ,$$
     
     $$ B_r = \begin{bmatrix} 0 \\
      1 \end{bmatrix} $$.

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

💡**Ejemplo:**
## 3. Metodologías de diseño

💡**Ejemplo:**
## 4. Ejercicios
📚 **Ejercicio 1:**
📚 **Ejercicio 2:**



## 5. Conclusiones
Conclusiones sobre el diseño de observadores de estados indican que:

En primer lugar, los observadores de estados permiten estimar todas las variables de estado de un sistema únicamente a partir de las medidas de su salida y las entradas conocidas. Esto resulta especialmente relevante en sistemas donde la medición directa de todas las variables de estado no es viable debido a limitaciones técnicas o económicas.

Además, es importante destacar que el diseño de un observador de estados depende de la condición de observabilidad del sistema. Esto implica que debe ser posible reconstruir los estados a partir de las entradas y salidas disponibles. En este sentido, cuando el sistema se encuentra en su forma canónicamente observable, los cálculos asociados al diseño del observador, como la determinación de las ganancias, se simplifican considerablemente, optimizando el proceso.

Por último, los observadores de estados representan una herramienta esencial en el control de sistemas dinámicos, ya que amplían las posibilidades de monitoreo y control en situaciones donde las mediciones directas son limitadas. Su correcta implementación garantiza un rendimiento eficiente y una mayor precisión en la estimación de estados críticos.



## Referencias
Agregue un subtítulo al final donde pueda poner todas las referencias consultadas incluyendo el origen o fuente de los ejercicios planteados. Tambien dentro del texto referencie los textos o artículos consultados y las figuras y tablas dentro de la explicación de las mismas.
