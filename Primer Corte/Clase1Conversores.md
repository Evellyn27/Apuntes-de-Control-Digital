# Fundamentos y Procedimientos de la Conversión A/D y D/A en Control Digital
La conversión entre señales analógicas y digitales es un proceso fundamental en los sistemas de control digital, en donde se requiere adaptar señales continuas provenientes del mundo físico a un formato que pueda ser procesado por sistemas digitales, y viceversa, por esta razón, dentro del ámbito de la ingeniería, este proceso reúne la recolección de datos a través de sensores que interactúan con señales, las cuales deben ser transformadas adecuadamente para que los controladores digitales puedan manejarlas de manera eficiente. En este sentido, la conversión A/D permite convertir una señal analógica, como temperatura, velocidad o humedad, en una señal digital para su procesamiento, mientras que la conversión D/A hace posible que las señales digitales se conviertan nuevamente a analógicas para controlar dispositivos en el mundo real.

## Indice
1. Señales Analógicas y Digitales
2. Procedimiento de Conversión A/D
3. Procedimiento de Conversión D/A
4. Modelos Matemático
5. Aplicaciones Prácticas y Ejercicios
6. Conclusiones
## 1. Señales Analógicas y Digitales
Las señales pueden clasificarse en dos tipos fundamentales: analógicas y digitales, cada tipo tiene características distintivas que afectan su uso en diversos sistemas de comunicación y procesamiento.

A continuación se detallan las diferencias y características fundamentales de ambos tipos de señales:

>🔑 *Señal Analóga:* Las señales analógicas son continuas tanto en el tiempo como en la amplitud, lo que significa que pueden llegar a tomar cualquier valor dentro de un rango continuo, representando información de manera fluida e ininterrumpida. [1] 

![Señal Analóga](http://xkiller-damndx.mex.tl/imagesnew2/0/0/0/2/1/3/9/8/2/5/Standing_wave_2.gif)

Figura 1. Señal Analóga

>🔑 *Señal Digital:* Son discretas tanto en tiempo como en amplitud, puesto que representan información en forma de secuencias de valores binarios (0 y 1), obtenidas mediante la conversión de señales analógicas. [2]

![Señal Analóga](https://miro.medium.com/v2/resize:fit:1000/1*T05QpHC6DaUl7-9Xrqo5IA.gif)

Figura 2. Señal Digital

#### Comparativa entre señales
| Características 	| Señal Analogica 	| Señal Digital 	|
|:---:	|:---:	|:---:	|
| Continuidad 	| Fluida y continua, sin saltos. 	| Discreta, con intervalos definidos. 	|
| Susceptibilidad al Ruido 	| Alta, susceptible a interferencias y distorsiones. 	| Baja, más robusta frente a perturbaciones. 	|
| Procesamiento y Almacenamiento 	| Más difícil de procesar y almacenar debido a la continuidad. 	| Fácil de procesar y almacenar utilizando sistemas digitales. 	|
| Calidad de Información 	| Puede perderse debido a ruido y distorsión. 	| Mantiene la integridad con menos pérdida. 	|

## 2. Procedimiento de Conversión A/D
El proceso de conversión A/D se realiza en tres etapas: muestreo, cuantización y codificación.
### Muestreo
El muestreo es el proceso mediante el cual una señal analógica continua en el tiempo es capturada en intervalos de tiempo discretos, es decir que implica tomar "instantáneas" de la señal en momentos específicos, con el objetivo de obtener una secuencia de valores que puedan ser utilizados en sistemas digitales, por tanto hay dos aspectos que son esenciales en este proceso ya que incluye la frecuencia de muestreo, que es la tasa a la que se capturan los valores de la señal analógica, y el período de muestreo, que es el intervalo de tiempo entre cada muestra. 

#### Teorema del muestreo
En el teorema del muestreo establece que para representar correctamente una señal analógica en forma digital, la frecuencia de muestreo debe ser al menos el doble de la frecuencia máxima de la señal continua. Este principio, tambien conocido como el teorema de Nyquist-Shannon, asegura que la señal digital resultante conserve toda la información de la señal original, por tanto, si la frecuencia de muestreo es insuficiente, pueden surgir problemas como el aliasing, donde las frecuencias altas se confunden con frecuencias bajas, distorsionando la señal y comprometiendo la calidad de la representación digital.

💡**Ejemplo 1:** En este caso se tienen dos figuras. 

En la primera, se puede observar que se cumple con la condición de Nyquist, lo que evita que las copias del espectro de la señal original se mezclen y se recupere correctamente 

![Señal Analóga](https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/9aaa463948100481486a4bca02c072d98d89e6a6/Screenshot%202024-08-31%20201222.png)

Figura 3. Señal Muestreada

En la segunda figura, la condición de Nyquist no se cumple, lo que provoca que las copias del espectro se superpongan. Esta superposición dificulta la recuperación de la señal original y genera el fenómeno de aliasing

![Señal Analóga](https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/3c0e776d83616f144ae21ed4f9f465e3fe096eea/Screenshot%202024-08-31%20201541.png)

Figura 4. Señal Muestreada

### Cuantización
La cuantización es el proceso que sigue al muestreo de una señal analógica y este consiste en aproximar cada muestra de la señal al valor más cercano dentro de un conjunto finito de niveles predefinidos, donde estos niveles dependen de la resolución del convertidor A/D, que se mide en bits, por lo tanto, a mayor número de bits, mayor será la cantidad de niveles disponibles, lo que permite una aproximación más precisa de la señal original.

Sin embargo, la cuantización introduce un pequeño error conocido como error de cuantización, que es la diferencia entre el valor real de la señal y el valor cuantizado. Este error es inevitable, pero puede minimizarse aumentando la resolución del convertidor A/D.

### Codificación
Finalmente, los valores cuantizados se codifican en un formato binario, que es el lenguaje utilizado por los sistemas digitales. 

💡**Ejemplo 2:** si se usa un convertidor de 8 bits, la señal de entrada se representará mediante uno de los 256 valores posibles $2^8$.

## 3. Procedimiento de Conversión D/A
La conversión digital a analógica (D/A) es el proceso mediante el cual se transforma una señal digital, que se encuentra en formato binario, en una señal analógica continua. Esto se logra mediante un conversor digital-analógico (DAC), que toma una entrada digital (representada por bits) y genera una salida analógica proporcional. En ese sentido el proceso consta de: una entrada digital, una referencia y una salida analóga.

>🔑 *Entrada digital:* Es un conjunto de bits (0s y 1s) que representan un valor específico en formato binario. Estos bits son la forma en que la información se codifica digitalmente.

>🔑 *Referencia:* Es una magnitud fija, como un voltaje, que define el rango máximo de la señal analógica que se generará.

>🔑 *Salida analóga:* Es el valor continuo que se obtiene después de convertir la entrada digital

### Métodos de conversión

#### Resistencias ponderadas
La conmutación de corrientes ponderadas se basa en la idea de asignar una corriente específica a cada bit de una palabra digital. En un DAC de corriente ponderada, cada bit del valor digital de entrada controla un transistor o un interruptor que enciende o apaga una corriente específica.

##### Implementación Fisica:
En primer lugar, se utilizan varias fuentes de corriente, cada una asociada con un valor de bit específico, las cuales corresponden a los bits más significativos y menos significativos, para cada corriente se conmuta según el estado de los bits en la entrada digital: si un bit está en alto (1), la corriente asociada se conecta al nodo de salida; si está en bajo (0), la corriente no se conecta. En ese sentido, la corriente total en la salida es la suma de las corrientes activas, produciendo una señal analógica que refleja el valor digital de entrada.

![Señal Analóga](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTiQSWwrIX5m24vnkmSFH0fBlKv08Vx3xiLYQ&s)

Figura 4. Resistencias Ponderadas

#### Red R-2R
Consiste en resistencias de dos valores: R y 2R, y la red se conecta de manera que la resistencia total se mantiene constante, sin importar el número de bits, es así que cuando se aplican señales digitales, las resistencias y las tensiones se combinan para generar una salida analógica que representa el valor digital ingresado.

##### Implementación Fisica:
La red consiste en una serie de resistencias conectadas en una estructura jerárquica. Cada resistencia en la red tiene un valor de R, y cada resistencia en las ramas más cercanas al nodo de salida tiene un valor de 2R.

![Señal Analóga](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSr9cVYLiSXpHA6tO0LKOz3qOUJGn2aYEozlA&s)

Figura 4. Red R-2R

## 4. Modelo Matemático
En sistemas de control digital, aunque el muestreador y el retenedor realizan operaciones inversas sobre las señales, ambos utilizan componentes similares.

### Muestreador 
El muestreador idealmente se representa mediante un interruptor controlado por una señal de reloj y su salida es una secuencia de impulsos que representa los valores de la señal continua en los instantes de muestreo. [2] 

### Retenedor
El retenedor idealmente se representa como un circuito que mantiene cada valor muestreado constante durante el intervalo de muestreo, produciendo una señal continua en escalón.
#### Modelos de Retenedores:
1. ZOH: Mantiene los valores constantes durante el intervalo de muestreo.
2. FOH: Interpola linealmente entre muestras.
3. SOH: Interpola parabólicamente entre muestras.

## 5. Ejercicios
### Ejercicio de Resistencias ponderadas
Diseñar un conversor digital analógico de ganancia unitaria de 8 bits. Vref tiene un valor de 5 voltios. [4] 

### Solución 
Dado que la ganancia 𝐴 es igual a 1 y el voltaje de referencia 𝑉ref es de 5 voltios, el voltaje máximo de salida 𝑉omax se calcula como:
$Vomax = Vref * A = 5V$ 

El valor de la resistencia R1​ se elige como 1 kΩ. En consecuencia, se seleccionan los siguientes valores para las resistencias en serie: R2=2 kΩ, R3=4 kΩ, y así sucesivamente, hasta R8=128 kΩ.

La resistencia equivalente RP, que representa el paralelo de las resistencias de entrada R1​, R2​, R3​, …, R8​, es de 502 Ω.
$Rf = Rp * A = 502 Ω$ 

### Ejercicio de Red R-2R
Diseñar un conversor digital analógico R-2R de ganancia igual a 1.3 de 4 bits. De voltaje de referencia asuma 5 voltios. [3]

### Solución 

$Vomax​=Vref​×A=5V×1.3=6.5V$

Se escoge una resistencia R de 1 kΩ. Para determinar el valor de la resistencia de retroalimentación RF​, se usa la fórmula de ganancia para un amplificador inversor:

$Rf=\frac{A*R}{1-\frac{1}{2^{n}}}$
$Rf=1387Ω$

## 6. Conclusiones
En la implementación física de estos convertidores, es esencial seleccionar y diseñar componentes como amplificadores operacionales y redes resistivas con precisión para asegurar la calidad de la conversión y la integridad de la señal.
## Referencias
[1] “Comunicaciones”. Tipos y Modos de Comunicaciones. Accedido el 28 de agosto de 2024. [En línea]. Disponible: http://xkiller-damndx.mex.tl/frameset.php?url=/1488142_Caracteristicas-de-las-senales-y-Conceptos-de-Ondas.html

[2] F. Miyara, CONVERSORES D/A Y A/D, 2a ed. 2004.

[3] Wilaeba electronica. “Conversor digital analogico R-2R”. Índice de contenido. Accedido el 1 de septiembre de 2024. [En línea]. Disponible: https://wilaebaelectronica.blogspot.com/2017/01/conversor-digital-analogico-r-2r.html

[4] Wilaeba electronica. “Conversor digital analogico por suma ponderada”. Índice de contenido. Accedido el 1 de septiembre de 2024. [En línea]. Disponible: https://wilaebaelectronica.blogspot.com/2017/01/conversor-digital-analogico-por-suma-ponderada.html











