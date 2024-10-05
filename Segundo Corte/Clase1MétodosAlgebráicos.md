# Métodos algebráicos
Los métodos algebraicos del control digital constituyen una herramienta clave para el diseño de controladores que permiten variar el comportamiento dinámico de los sistemas correspondientes en lazo cerrado, llevando a cabo así la estabilidad y el rendimiento deseados, en otras palabras se les describe como técnicas que permiten transformar las características de un sistema a partir de manipulaciones algebraicas de su función de transferencia, en ese sentido, entre los métodos algebraicos más relevantes están la igualación de modelo, que permite obtener la función de transferencia del sistema para seguir una respuesta predefinida; la igualación de coeficientes, que permite modificar los polos del sistema para garantizar la estabilidad y la respuesta rápida; y las ecuaciones diofánticas, que se ocupan de sistemas más complejos al combinar varias funciones de transferencia. Estos métodos de gran relevancia en aplicaciones en industrias como: el control de procesos, la automatización, y los sistemas embebidos seran revisados en este trabajo, y a partir de la explicación de los mismos, se evaluará su efectividad en la resolución de problemas prácticos, asi como sus consideraciones de implementación.
## Índice
1. Método de igualación por modelo
2. Método de igualación por coeficientes
3. Ecuaciones diofánticas
4. Ejercicios
5. Conclusiones

## 1. Método de igualación por modelo
La igualación por modelo es un procedimiento en el diseño de sistemas de control que tiene como propósito que el sistema en lazo cerrado (sistema real) reproduzca el comportamiento de un determinado modelo de referencia ya establecido, y el cuál comprende determinadas características en lo que respecta a la estabilidad, la respuesta dinámica y en la robustez del sistema controlado. Por lo tanto, el objetivo de este método es diseñar un controlador que permita que la salida del sistema sea una aproximación de la salida de un modelo de referencia que se ha diseñado bajo las mismas condiciones de entrada.
>🔑 *Sistema Causal:* Es aquel cuya salida en cualquier instante depende únicamente de los valores actuales o pasados de la entrada, nunca de valores futuros.
### 1.1. Características y Consideraciones
Al utilizar el método de igualación por modelo, es crucial tener en cuenta las siguientes consideraciones de implementación:
1. Causalidad:
2. Estabilidad del modelo objetivo:
3. Evitar cancelaciones polo-cero:
4. Grados de los polinomios:
5. Ceros de fase no mínima:

### 1.2. Procedimiento 

### 1.3. Ejemplos
### 1.4. Simluación

## 2. Método de igualación por coeficientes
### 2.1. Características y Consideraciones
### 2.2. Procedimiento 
### 2.3. Ejemplos
### 2.4. Simluación

## 3. Ecuaciones diofánticas en Contexto de Control Digital
### 3.1. Clasificación de Ecuaciones Diofánticas
### 3.2. Condiciones de Existencia de Soluciones
### 3.4. Aplicaciones en teoría de numeros 

Si en algún caso pretende dar un ejemplo explicativo ya sea a través de texto o através de ecuaciones matemáticos, utilizar la palabra 'Ejemplo' seguido de una numeración consecutiva dentro de la clase. Utilice el emoji 💡 antecediendo la palabra.

💡**Ejemplo 1:** si se va a representar la ecuación de la ley de Ohm se puede mostrar así $R=\frac{V}{I}$ o también,


💡**Ejemplo 2:**

![Figura de prueba](images/plantilla/Captura2.PNG)

Figura 1. Figura de prueba



💡**Ejemplo 3:** 

| **Resultado** | **x = número de intentos hasta primer éxito** |
|---------------|-----------------------------------------------|
|       S       |                       1                       |
|       FS      |                       2                       |
|      FFS      |                       3                       |
|      ...      |                      ...                      |
|    FFFFFFS    |                       7                       |
|      ...      |                      ...                      |

Tabla 1. Tabla de ejemplo

Cada tabla debe llevar la etiqueta que describa su contenido y numeración consecutiva para todas las tablas

💡**Ejemplo 4:**
```
var sumar2 = function(numero) {
  return numero + 2;
}
```

## 4. Ejercicios

## 5. Conclusiones

## Referencias

