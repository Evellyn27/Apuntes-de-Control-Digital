# Operaciones en el Espacio de Estados

Las operaciones en el espacio de estados son esenciales para analizar sistemas dinámicos complejos, ya que permiten modelar su comportamiento mediante vectores de estado y matrices, ofreciendo una descripción completa de todas las configuraciones posibles. A partir de una función de transferencia, se puede obtener su representación en espacio de estados, que puede adoptar distintas formas canónicas, como la controlable, observable o diagonal, dependiendo del enfoque del análisis. Por tanto, el enfoque en el espacio de estados, complementado con el análisis del polinomio característico, no solo permite evaluar propiedades esenciales como la estabilidad y la dinámica del sistema, sino que también ofrece un marco versátil para abordar problemas de control.

## Índice
1. Obtención del Espacio de Estados
2. Análisis Dinámico en el Espacio de Estados
3. Conversión entre Representaciones
4. Operaciones Matriciales en el Espacio de Estados
5. Ejercicios
6. Conclusiones
   
## 1. Obtención del Espacio de Estados
Para obtener el espacio de estados, se transforma el sistema original, descrito por una función de transferencia o ecuaciones diferenciales, en un conjunto de ecuaciones de primer orden. Esto se logra definiendo un vector de estado $$x$$ que contiene las variables necesarias para describir el sistema en el tiempo. La dinámica del sistema se expresa con matrices: $$A,$$ que relaciona los estados; $$B,$$ que muestra cómo la entrada $$u$$ afecta al estado; $$C,$$ que conecta los estados con la salida $$y,$$ y $$D,$$ que representa el efecto directo de la entrada en la salida.
>🔑 *Definición:* 
### 1.1 Espacio de Estados a partir de Función de Transferencia
Para construir una representación en el espacio de estados a partir de una función de transferencia $$G(z)$$ se descompone la función de transferencia en una forma que permita identificar los coeficientes que definirán las matrices $A,$ $B,$ $C$ y $D,$ las cuales describen la dinámica del sistema en el dominio temporal.

Dada una función de transferencia general en el dominio $z:$

$$
G(z) = \frac{b_0 z^n + b_1 z^{n-1} + \dots + b_{n-1} z + b_n}{z^n + a_1 z^{n-1} + \dots + a_{n-1} z + a_n}
$$

la forma canónica se obtiene estructurando las matrices en función de los coeficientes $a_i$ y $b_i$ (del denominador y numerador, respectivamente) de la función de transferencia.

### 1.2 Representación en Formas Canónicas
- **Forma Canónica Controlable**
- **Forma Canónica Observable**
- **Forma Canónica Diagonal**
## 2. Análisis Dinámico en el Espacio de Estados
### 2.1 Polinomio Característico
### 2.2 Raíces del Polinomio Característico

## 3. Conversión entre Representaciones
### 3.1 De Espacio de Estados a Función de Transferencia
### 3.2 De Función de Transferencia a Espacio de Estados

## 4. Operaciones Matriciales en el Espacio de Estados
### 4.1 Determinantes
### 4.2 Inversión y Transposición de Matrices

💡**Ejemplo 1:** 
$$R=\frac{V}{I}$$

## 5. Ejercicios

📚

## 6. Conclusiones


## Referencias
