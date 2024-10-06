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

- **Causalidad:**  El controlador debe depender solo de valores presentes o pasados de la entrada.
<p align="center">$y\left( t \right)=x\left( t-1 \right)$</p>

<p align="center">
  <img src="https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/35f1954f074c0ea0cdaef944a6d5f84aa54e1f65/Imagenes/Causales.png" />
</p>
<p align="center">
Figura 1. Sistemas Causales
</p>

- **Estabilidad del modelo objetivo:** El modelo de referencia y el sistema en lazo cerrado deben ser estables, con polos dentro del círculo unitario
<p align="center">$P\left( z\right)=z^{2}+a_{1}z+a_{2} : \left| z_{p} \right|\lt 1$</p>

Donde: 

$z_{p}:$ Son los polos de la función

- **Evitar cancelaciones polo-cero:** Evitar cancelaciones entre polos y ceros que comprometan la estabilidad. 
<p align="center">$z_{p}\neq  z_{c}$</p>

- **Grados de los polinomios:** El grado del numerador del controlador no debe superar al del denominador del sistema.
<p align="center">$N\lt D$</p>

**Ejemplo:** Si la planta tiene una función de transferencia:

<p align="center">$G\left( z \right)=\frac{k}{z^{2}+a_{1}z+a_{2}}$</p>

Entonces, el controlador $C(z)$ debe tener un numerador de grado menor o igual a 2 para asegurar la causalidad y realizabilidad.

- **Ceros de fase no mínima:** Preservar ceros de fase no mínima en el diseño.

### 1.2. Procedimiento 
El procedimiento para la igualación por modelo consiste en los siguientes pasos:

1. **Definir la función de la planta en lazo abierto:**
Como primer paso se debe ejecutarse el cálculo de la función de transferencia del sistema en lazo abierto $G(z)$ que describe la dinámica natural de la planta sin control.
<p align="center">
  <img src="https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/996ea6fe1d28796c7c152e3ed1341f08853b751a/Imagenes/plantaControl.png" />
</p>

 Esta función se puede obtener directamente de las características físicas del sistema o bien mediante un modelado matemático.
 
<p align="center">$G\left( z \right)=\frac{B_{G(z)}}{A_{G(z)}}=\frac{b_{0}+b_{1}z^{-1}+...+b_{m}z^{-m}}{1+a_{1}z^{-1}+...+a_{n}z^{-n}}$</p>

Donde $B_{G(z)}$ es el numerador y $A_{G(z)}$ es el denominador de la función de transferencia de la planta.

3. **Definir el modelo de referencia:**
Con el comportamiento del sistema en lazo abierto determinado, se especificará la función de transferencia del modelo de referencia Go(z) que describe el comportamiento deseado del sistema en lazo cerrado, además este tendrá en cuenta aspectos como la estabilidad, el sobreimpulso o el tiempo de establecimiento.
</p>
<p align="center">$G_{0} =\frac{B_{G0}}{A_{G0}}$</p>

5. **Diseño del controlador:**
Con G(z) y Go(z) definidos, se calcula la función de transferencia del controlador C(z) que, cuando ambas funciones se cierran en el lazo, permiten que la función de transferencia del sistema en lazo cerrado sea igual a Go(z), logrando de esta forma que el sistema siguiendo el comportamiento deseado.

</p><p align="center">$C(z) =\frac{G_{0}}{G(z)(1-G_{0})}$</p>

7. **Verificación:**
Finalmente, una vez diseñado el controlador, se deben verificar las consideraciones decritas anteriormente para asegurar que el sistema sea implementable en la práctica.
### 1.3. Ejemplo
💡
### 1.4. Simluación

## 2. Método de igualación por coeficientes
La igualación por coeficientes es un método algebraico que se utiliza con frecuencia para contrastar dos expresiones polinómicas o racionales y poder extraer las relaciones entre los coeficientes. En el contexto de control, el método iguala los distintos coeficientes del polinomio característico de un sistema, colocando los polos en las posiciones deseadas en el diseño de un controlador. 
### 2.1. Características y Consideraciones
Al utilizar el método de igualación por coeficientes, es fundamental considerar las siguientes pautas de implementación:
-**Incremento del Orden del Sistema:**
La función en lazo cerrado del sistema se describe de esta manera:
</p><p align="center">$G_{0}=\frac{B(z)N(z)}{A(z)D(z)+B(z)N(z)}$</p>
Al multiplicar el polinomio del denominador de la planta $A(z)$ por el denominador del controlador $D(z)$, el orden del sistema en lazo cerrado aumenta.
</p><p align="center">$P_{0}=A(z)D(z)+B(z)N(z)$</p>
Este incremento en el orden del sistema puede afectar la complejidad del control y la estabilidad general del sistema.

-**Propiedad de las Funciones:**
Si se emplean las funciones de transferencia del controlador $C(z)$ y de la planta $G(z)$, al multiplicar el numerador de la planta $B(z)$ por el numerador de la función del controlador $N(z)$, será necesario que ambas funciones de transferencia sean propias, esto indica, que el grado del numerador sea menor de que el grado del denominador. 

>🔑 *Función impropia:* Una función de transferencia es impropia si el grado del numerador es mayor que el grado del denominador, esto puede resultar en un comportamiento no físico y potencialmente inestable en el sistema.
>>🔑 *Función bipropia:*  Una función de transferencia es bipropia si el grado del numerador es igual al grado del denominador
-**Igualación en el Polinomio Característico:**
Aunque la ubicación de los polos puede fijarse en posiciones deseadas, no hay forma de lograr que los ceros del sistema estén en la misma ubicación, lo que significa que es posible que la respuesta transitoria del sistema no sea ajustable, ya que puede afectar a su comportamiento.
-**Orden del Controlador:**
El orden de la función de transferencia del controlador $C(z)$ debe ser un grado menor que el de la planta en lazo abierto
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

