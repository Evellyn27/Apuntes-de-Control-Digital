# Estabilidad en Sistemas Discretos
En sistemas discretos, donde las señales y las operaciones se realizan en intervalos de tiempo discretos, la estabilidad se refiere a la capacidad del sistema para mantener su comportamiento deseado y no diverger hacia valores incontrolables o inestables con el tiempo. A diferencia de los sistemas continuos, donde se emplean métodos de análisis basados en la transformada de Laplace, los sistemas discretos utilizan herramientas como la transformada Z y el análisis de los polos y ceros en el dominio Z para evaluar su estabilidad

## Índice
1. Estabilidad Absoluta
2. Espacios de LaPlace y Z
3. Métodos de Evaluación de Estabilidad
4. Estabilidad Asintótica
5. Estabilidad BIBO
6. Ejercicios
7. Conclusiones


## 1. Estabilidad Absoluta
La estabilidad absoluta en sistemas discretos se refiere a la capacidad del sistema para mantenerse estable frente a perturbaciones o condiciones iniciales, es decir, un sistema discreto es estable si, tras una perturbación, su salida no crece sin límite y se mantiene acotada.

| Aspecto 	| Sistemas Continuos 	| Sistemas Discretos 	|
|:---:	|:---:	|:---:	|
|      Espacio de Análisis 	| Plano s (Transformada de LaPlace) 	| Plano Z (Transformada Z) 	|
| Criterio de Estabilidad 	| Polos en el semiplano izquierdo (Re(s) < 0) 	| Polos dentro del círculo unitario 	|
| Comportamiento de los Polos 	| Polos con partes reales negativas aseguran que la respuesta se amortigua con el tiempo 	| Polos dentro del círculo unitario aseguran que la respuesta se atenúa con el tiempo 	|

## 2. Espacios de LaPlace y Z
>🔑 *Transformada de LaPlace:*La Transformada de LaPlace es una técnica matemática comúnmente empleada para examinar sistemas lineales invariantes en el tiempo, tales como mecanismos, circuitos eléctricos y sistemas de control.

La Transformada de Laplace es una herramienta matemática crucial en ingeniería, utilizada para simplificar el análisis de sistemas lineales e invariantes en el tiempo, como circuitos eléctricos, sistemas mecánicos y sistemas de control. Su función principal es convertir funciones del tiempo continuo en el dominio complejo, transformando problemas descritos por ecuaciones diferenciales en ecuaciones algebraicas más manejables. Esta conversión facilita la resolución de ecuaciones diferenciales y permite un análisis detallado de la estabilidad y la respuesta de los sistemas ante diversas entradas. Al examinar la ubicación de los polos en el plano s, los ingenieros pueden evaluar la estabilidad del sistema y prever su comportamiento dinámico, haciendo de la Transformada de Laplace una herramienta esencial para el diseño y la evaluación de sistemas complejos.

>🔑 *Transformada Z:* La Transformada Z es un método matemático que se utiliza principalmente en el procesamiento digital de señales y en el control de sistemas y donde su objetivo principal es transformar una señal de tiempo discreto en una representación compleja en el dominio de la frecuencia.

La Transformada Z permite a los ingenieros analizar la estabilidad y el comportamiento dinámico de sistemas discretos al evaluar la ubicación de los polos en el plano Z. Al hacerlo, proporciona una visión clara de cómo las señales se atenúan o amplifican a lo largo del tiempo, haciendo de la Transformada Z una herramienta indispensable para el diseño y la optimización de sistemas de control digital y procesamiento de señales.

## 3. Métodos de Evaluación de Estabilidad
La estabilidad de un sistema discreto se evalúa mediante varios métodos, cada uno proporcionando una perspectiva diferente sobre la respuesta del sistema.

### Ubicación de Polos
Los polos de un sistema discreto se obtienen al analizar la ecuación característica del sistema, que se forma a partir de la función de transferencia. La estabilidad de un sistema discreto depende de la posición de estos polos en el plano Z.

#### Criterios de Estabilidad:

1. Estabilidad Global: Un sistema discreto es estable si todos sus polos están dentro del círculo unitario en el plano Z (es decir, si todos los polos tienen un módulo menor que 1). Esto garantiza que la respuesta del sistema a cualquier entrada será bounded (acotada) y no crecerá indefinidamente.

3. Estabilidad Marginal: Un sistema es marginalmente estable si al menos uno de los polos está en el círculo unitario y ningún polo está fuera de él. Esto implica que el sistema puede tener una respuesta que permanece constante o crezca lentamente, pero no se vuelve inestable.
 
5. Inestabilidad: Un sistema es inestable si al menos un polo está fuera del círculo unitario. En este caso, la respuesta del sistema crecerá sin límites, lo que indica que el sistema es inestable.

💡**Ejemplo 1:**  Sistema Estable Considere un sistema con la función de transferencia:

$H(z)= \frac{1}{\left(Z + 0,4  \right)\left(Z + 0,2\right)}$

z = -0,2
z = -0,4

Los polos de la función se encuentran dentro del circulo unitario, por tanto es estable.

## 4. Estabilidad Asintótica
Es una propiedad clave en el análisis de sistemas dinámicos, tanto en el contexto de sistemas continuos como discretos. En términos simples, un sistema es asintóticamente estable si, frente a una perturbación o una entrada, su salida regresa a un estado de equilibrio en el tiempo, y no solo esto, sino que lo hace de manera que se acerca al equilibrio conforme pasa el tiempo.

## 5. Estabilidad BIBO
Un sistema es BIBO estable si para cualquier entrada acotada (bounded input), la salida también es acotada (bounded output). En otras palabras, si la entrada del sistema está limitada en magnitud, la salida del sistema también lo estará.

### Criterio de Estabilidad de Jury
El criterio de estabilidad de Jury es un método algebraico que se utiliza para analizar la estabilidad de sistemas discretos descritos por su ecuación característica. El método convierte la ecuación característica en una forma que permite verificar la estabilidad BIBO sin necesidad de calcular los polos directamente.

1. Coeficiente a0>0: El coeficiente a0 es el coeficiente del término independiente en la ecuación característica, por tanto, para que un sistema sea BIBO estable, es necesario que a0 sea positivo.
2. Coeficiente an<a0​: Este criterio compara el coeficiente del término de mayor orden an con el coeficiente a0​.
3. Evaluar P(z) en z=1: El polinomio P(z) es la ecuación característica del sistema. Evaluar P(z) en z=1
 
$P(1)=a0+a1+a2+⋯+an$ 

Para que el sistema sea BIBO estable, P(1)>0. Esto asegura que el sistema no presenta una respuesta que se vuelve inestable cuando se somete a una entrada constante.

4. Evaluar P(z) en z=−1: Para ciertos sistemas, evaluar P(z) en z=−1 puede proporcionar información adicional sobre la estabilidad:
 
Si P(−1)>0 para n par, o Si P(−1)<0 para n impar,

### Construcción del Arreglo de Jury
El arreglo de Jury tiene la forma de una matriz que ayuda a determinar la estabilidad mediante la evaluación de los signos de sus elementos.

![](https://herramientasdecalculo.com/wp-content/uploads/2018/03/tabla-criterio-de-estabilidad-de-jury.png)

El procedimiento general para construir la matriz de Jury es el siguiente:

#### Construir las Filas Iniciales:
La primera fila de la matriz se forma con los coeficientes del polinomio 

P(z):[a0,a1,a2,…,an−1,an]

La segunda fila se forma con los coeficientes en orden inverso (es decir, empezando desde el coeficiente an​ hasta a0​): 

[an,an−1,an−2,…,a1,a0]

#### Completar la Matriz:

Luego, se completa la matriz de Jury siguiendo un algoritmo recursivo que utiliza las filas anteriores para construir nuevas filas. Cada nueva fila se calcula restando una combinación lineal de las filas anteriores, siguiendo un proceso llamado "eliminación de filas".

#### Evaluar la Estabilidad
Para determinar la estabilidad BIBO usando el criterio de Jury, se compara el primer y ultimo elemento de la columna.

Si el primero > ultimo, es estable, pero si sucede lo contrario es inestable

## 6. Ejercicios
### Ejercicio 1:
Determine si A(z) que se enuncia tiene raíces fuera del círculo unitario.

$A(z)= z^{4}-1,2z^{3}+0.07z^{2}+0.3z-0.08$

#### Analizando las condiciones

$a\left| 0,08 \right|\lt 1$
$1^{4}-1,2*1^{3}+0.07*1^{2}+0.3*1-0.08 = 0.09 > 0$
$-1^{4}-1,2*-1^{3}+0.07*-1^{2}+0.3*-1-0.08 = 1,89 > 0$

$\left| b3 \right|\gt \left| b0 \right| $

$\left| 0,99 \right|\gt \left| 0,20 \right| $

$\left| c3 \right|\gt \left| c0 \right| $

$\left| 0,94 \right|\gt \left| 0,31 \right| $

Se concluye que es estable.

### Ejercicio 2:
Determine si A(z) que se enuncia tiene raíces fuera del círculo unitario.

$A(z)= z^{3}-1,1z^{2}-0.1z+0.2$

#### Analizando las condiciones

$a\left| 0,2 \right|\lt 1$
$1^{3}-1,1*1^{2}-0.1*1+0.2 = 0$
$-1^{3}-1,1*-1^{2}-0.1*-1+0.2 = -1,8 \lt 0$

$\left| b3 \right|\gt \left| b0 \right| $

$\left| 0,96 \right|\gt \left| 0,12 \right| $

Se concluye que es estable.

## 7. Conclusiones
 

## Referencias
Agregue un subtítulo al final donde pueda poner todas las referencias consultadas incluyendo el origen o fuente de los ejercicios planteados. Tambien dentro del texto referencie los textos o artículos consultados y las figuras y tablas dentro de la explicación de las mismas.
