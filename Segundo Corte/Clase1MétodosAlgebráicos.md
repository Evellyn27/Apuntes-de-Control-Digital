# Métodos algebráicos
Los métodos algebraicos del control digital son esenciales para diseñar controladores que ajusten el comportamiento dinámico de sistemas en lazo cerrado, garantizando estabilidad y rendimiento del sistema, por ende, estos controladores transforman las características del sistema mediante manipulaciones algebraicas de la función de transferencia. Entre ellos, destacan la igualación de modelo y la igualación de coeficientes, así como un método para el análisis de los mismos conocidos como las ecuaciones diofánticas, que permiten abordar sistemas más complejos. En ese sentido, este trabajo revisa estos métodos y su aplicación en industrias como el control de procesos, la automatización y los sistemas embebidos, evaluando su efectividad y consideraciones de implementación.
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
  
|            **Consideración**            |                                                **Descripción**                                               | **Condición Matematica**                                            |
|:---------------------------------------:|:------------------------------------------------------------------------------------------------------------:|---------------------------------------------------------------------|
|             **_Causalidad_**            | El controlador debe depender solo de valores presentes o pasados para garantizar la implementación práctica. | $y\left( t \right)=x\left( t-1 \right)$                             |
|  **_Estabilidad del  modelo objetivo_** | Los polos deben ubicarse dentro del circulo unitario                                                         | $P\left( z\right)=z^{2}+a_{1}z+a_{2} : \left\| z_{p} \right\|\lt 1$ |
| **_Evitar cancelaciones de polo-cero_** | Evitar la eliminación de polos y ceros, ya que esto puede restar características al sistema                  | $z_{p}\neq  z_{c}$                                                  |
|        **_Grado del polinomio_**        | El grado del numerador del controlador no debe superar  al del denominador del sistema.                      | $N\lt D$                                                            |
|      **_Ceros de fase  no mínima_**     | Preservar ceros de fase no mínima en el diseño                                                               | Considerar ceros de fase no mínima en $C(z)$                        |

### 1.2. Procedimiento 
El procedimiento para la igualación por modelo consiste en los siguientes pasos:
<p align="center">
  <img src="https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/0872a390c84464668af01df7957f61aade8816db/Imagenes/procedimiento.png" />
</p>

### 1.3.  Descripción del Proceso

1. **Definir la función de la planta en lazo abierto:**
Como primer paso se debe ejecutarse el cálculo de la función de transferencia del sistema en lazo abierto $G(z)$ que describe la dinámica natural de la planta sin control.
<p align="center">
  <img src="https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/996ea6fe1d28796c7c152e3ed1341f08853b751a/Imagenes/plantaControl.png" />
</p>

 Esta función se puede obtener directamente de las características físicas del sistema o bien mediante un modelado matemático.
 
<p align="center">$G\left( z \right)=\frac{B_{G(z)}}{A_{G(z)}}=\frac{b_{0}+b_{1}z^{-1}+...+b_{m}z^{-m}}{1+a_{1}z^{-1}+...+a_{n}z^{-n}}$</p>

Donde $B_{G(z)}$ es el numerador y $A_{G(z)}$ es el denominador de la función de transferencia de la planta.

2. **Definir el modelo de referencia:**
Con el comportamiento del sistema en lazo abierto determinado, se especificará la función de transferencia del modelo de referencia Go(z) que describe el comportamiento deseado del sistema en lazo cerrado, además este tendrá en cuenta aspectos como la estabilidad, el sobreimpulso o el tiempo de establecimiento.
</p>
<p align="center">$G_{0} =\frac{B_{G0}}{A_{G0}}$</p>

3. **Diseño del controlador:**
Con G(z) y Go(z) definidos, se calcula la función de transferencia del controlador C(z) que, cuando ambas funciones se cierran en el lazo, permiten que la función de transferencia del sistema en lazo cerrado sea igual a Go(z), logrando de esta forma que el sistema siguiendo el comportamiento deseado.

</p><p align="center">$C(z) =\frac{G_{0}}{G(z)(1-G_{0})}$</p>

4. **Verificación:**
Finalmente, una vez diseñado el controlador, se deben verificar las consideraciones decritas anteriormente para asegurar que el sistema sea implementable en la práctica.

### 1.3. Ejemplos Prácticos
💡
### 1.4. Simluación

## 2. Método de igualación por coeficientes
La igualación por coeficientes es un método algebraico que se utiliza con frecuencia para contrastar dos expresiones polinómicas o racionales y poder extraer las relaciones entre los coeficientes. En el contexto de control, el método iguala los distintos coeficientes del polinomio característico de un sistema, colocando los polos en las posiciones deseadas en el diseño de un controlador. 
### 2.1. Características y Consideraciones
Al utilizar el método de igualación por coeficientes, es fundamental considerar las siguientes pautas de implementación:
|                **Consideración**                |                                                                       **Descripción**                                                                      | **Condición Matematica**        |
|:-----------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------:|---------------------------------|
|      **_Incremento del Orden del Sistema_**     | Al multiplicar el polinomio del denominador de la planta  $D(z)$ por el denominador del controlador $A(z)$, el orden  del sistema en lazo cerrado aumenta. | $P_{0}=A(z)D(z)+B(z)N(z)$       |
|         **_Propiedad de las Funciones_**        | Las funciones de transferencia del controlador $C(z)$ y de la planta $G(z)$ deben ser propias.                                                             | $B(z)\lt A(z)$ y $N(z)\lt D(z)$ |
| **_Igualación en el Polinomio Característico_** | La igualación se realiza en el polinomio característico,  permite fijar la ubicación de los polos, pero no de ceros                                        | $D(z)=$ Polinomio                |
|           **_Orden del Controlador_**           | El orden de la función de transferencia del controlador $C(z)$ debe ser un grado menor que el de la planta en lazo abierto                                 | $A(z)\lt D(z)$                  |

>🔑 *Función impropia:* Una función de transferencia es impropia si el grado del numerador es mayor que el grado del denominador, esto puede resultar en un comportamiento no físico y potencialmente inestable en el sistema.

>🔑 *Función bipropia:*  Una función de transferencia es bipropia si el grado del numerador es igual al grado del denominador

### 2.2. Procedimiento 
<p align="center">
  <img src="https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/cc65b4113a45c8c91511db0b597729d4bfcf77c0/Imagenes/ProcedimientoE.png" />
</p>

### 2.3.  Descripción del Proceso
1. **Definir la función de la planta en lazo abierto:**
Al igual que el método anterior, como primer paso se identifica la función de trasnferencia en lazo abierto. es decir, en su forma:
</p><p align="center">$G(z)=\frac{N(z)}{D(z)}$</p>
En ese sentido, la función de transferencia describe la relación entre la entrada y la salida del sistema en el dominio $z$

2. **Establecimiento del Polinomio Deseado:**
En este paso, se define el polinomio característico deseado $P_{deseado}(z)$, el cual refleja las características de rendimiento que se esperan del sistema, en ese sentido, este polinomio se puede escribir en la forma general:
</p><p align="center">$P_{deseado}(z)=z^{n}+a_{n-1}z^{n-1}+...+a_{0}$</p>

3. **Formulación del Sistema en Lazo Cerrado:**
Este paso busca representar cómo interactúan la planta y el controlador cuando se aplica una retroalimentación negativa. En ese sentido se tiene que:
</p><p align="center">$G_{0}(z)=\frac{N_{0}(z)}{D_{0}(z)}$</p>

Sin embargo, esta expresión puede estar basada por la representación del controlador $C(z)$ y la función en lazo abierto $G(z)$:
</p><p align="center">$G_{0}(z)=\frac{C(z)G(z)}{1+C(z)G(z)}$</p>

Al desarrollar esta expresión, el polinomio característico en lazo cerrado se obtiene como:
</p><p align="center">$P_{cerrado}(z)=A(z)D(z)+B(z)N(z)$</p>
Aquí, $A(z)$ y $B(z)$ representan el denominador y el numerador de la función de transferencia del controlador $C(z)$

4. **Igualación de los Polinomios:**
Se iguala el polinomio característico del sistema en lazo cerrado con el polinomio deseado:
</p><p align="center">$P_{cerrado}=P_{deseado}$</p>
Esta igualación establece que el comportamiento dinámico del sistema en lazo cerrado debe coincidir con el comportamiento deseado. Por lo tanto:
</p><p align="center">$A(z)D(z)+B(z)N(z)=P_{deseado}$</p>

6. **Obtención de ecuaciones:**
Expandiendo la igualdad anterior, se obtienen ecuaciones para cada potencia de $z.$ En ese sentido, aquì se identifica los términos del polinomio característico deseado y los términos que resultan de $A(z)D(z)+B(z)N(z).$ A continuación, se muestra como se igualan:

* Para $z^{n}$ : para ecuaciones $A_{n}, B_{n}$
* Para $z^{n-1}$ : para ecuaciones $A_{n-1}, B_{n-1}$
* Y así sucesivamente hasta llegar a $z^{0}$
  
8. **Resolución de Ecuaciones:**
9. **Verificación:**
### 2.3. Ejemplos
### 2.4. Simluación

## 3. Ecuaciones diofánticas en Contexto de Control Digital
Las ecuaciones diofánticas son ecuaciones polinómicas que buscan soluciones de tipo entero, estas suelen ser utilizadas en áreas relevantes, como el caso del control digital, donde se aplican para la síntesis y el análisis de sistemas de control. 
### 3.1. Clasificación de Ecuaciones Diofánticas
### 3.2. Condiciones de Existencia de Soluciones
### 3.4. Aplicaciones en teoría de numeros 

## 4. Ejercicios

## 5. Conclusiones
Dentro de la temática, se pudo llegar a las siguientes conclusiones:

- En primer lugar, se identifica que la igualación por modelo permite alinear eficazmente las características de un sistema de control con un modelo deseado, sin embargo, cabe destacar que la precisión del controlador depende de la validez del modelo utilizado.

- Por otro lado, los parámetros del controlador ajustados por el método de igualación por coeficientes, proporciona un control mucho más robusto y efectivo sobre la estabilidad del sistema, no obstante, este limita la capacidad de la ubicación de los ceros, lo que puede afectar la respuesta transitoria del sistema.

- Finalmente, se evidencia que la integración de ecuaciones diofánticas contribuyen a tener un análisis de sistemas, estableciendo condiciones de diseño que aseguran la viabilidad de las soluciones en contextos discretos, esto resalta la interrelación entre la teoría matemática y su aplicación práctica en ingeniería

## Referencias

