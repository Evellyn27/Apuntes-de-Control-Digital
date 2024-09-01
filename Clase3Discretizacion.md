# Discretización de controladores Analógicos

## Indice
1. Discretización de señales Analógicas
2. Método de Invarianza al impulso
3. Método de Invarianza al Paso
4. Método de Euler Adelante
5. Método de Euler Atras
6. Método trapezoidal
7. Teorema de Muestreo de Nyquist
8. Conclusiones
9. Referencias



## 1. Discretización de señales Analógicas
La discretización de señales analógicas es el proceso mediante el cual una señal continua en el tiempo y en amplitud se convierte en una señal discreta, que es una secuencia de valores en instantes específicos. Este proceso es esencial para el procesamiento digital de señales, ya que permite que las señales analógicas sean manipuladas y analizadas utilizando sistemas digitales como computadoras y microcontroladores.

## 2. Método de Invarianza al impulso
Es una técnica para obtener una función de transferencia digital a partir de una función de transferencia analógica. La idea central es que la respuesta al impulso de un filtro analógico se puede mapear directamente a la respuesta al impulso de un filtro digital mediante una transformación.
>🔑*Proceso de Transformación:*
* Obtención de la Respuesta al Impulso Analógica:
Primero, se determina la respuesta al impulso del filtro analógico. La respuesta al impulso 
 $h_a(t)$ es la salida del filtro cuando se aplica un impulso unitario $δ(t)$ como entrada.

>🔑*Transformación a la Respuesta al Impulso Digital:*
*La respuesta al impulso analógica $h_a(t)$ se convierte en una secuencia discreta aplicando un muestreo en el tiempo. Esto se hace evaluando 
 $h_a(t)$  en intervalos de tiempo $T$, donde $T$ es el período de muestreo del sistema digital.

>🔑*Transformación de la Función de Transferencia:*
* La función de transferencia del filtro digital $H(z)$  se obtiene a partir de la transformada Z de la respuesta al impulso digital. Esto se puede hacer utilizando la transformada Z de la secuencia discreta obtenida en el paso anterior.

Ventajas:
* Simplicidad: El método de invarianza al impulso es relativamente simple y directo, especialmente cuando se trabaja con filtros que tienen una respuesta al impulso que puede ser fácilmente muestreada.
*Preservación de la Forma de Respuesta: Conserva la forma de la respuesta al impulso del filtro analógico, lo que puede ayudar a mantener ciertas propiedades del filtro original.

Desventajas: 
* Distorsión de Frecuencia: El método puede introducir distorsiones en la respuesta en frecuencia debido a la aproximación de la transformación.
* Limitaciones en el Diseño: Puede no ser adecuado para todos los tipos de filtros analógicos, especialmente si la respuesta al impulso analógica no es fácilmente muestreable.

## 3. Método de Invarianza al Paso
 El Método de Invarianza al Paso es una técnica utilizada para diseñar filtros digitales a partir de filtros analógicos mediante la preservación de la respuesta al paso de los filtros. Este método se basa en la idea de que la respuesta de un sistema digital a una entrada de escalón unitario debe coincidir con la respuesta del filtro analógico a una entrada de escalón unitario.

>🔑*Obtención de la Respuesta al Paso Analógica:*
* Primero, se determina la respuesta al paso del filtro analógico. La respuesta al paso $h_a(t)$  es la salida del filtro cuando se aplica una entrada de escalón unitario $u(t)$ como entrada.
*Matemáticamente, se puede expresar como  $$\[ h_a(t) = \mathcal{L}^{-1} { \frac{H_a(s)}{s}} \]$$  siendo $h_a(t)$ la función de transferencia del filtro analógico.

>🔑*Transformación a la Respuesta al Paso Digital:*
*La respuesta al paso del filtro digital $h_a[n]$ e obtiene muestreando la respuesta al paso analógica  $h_a(t)$  en intervalos regulares. Esto convierte la respuesta continua en una secuencia discreta.
* La respuesta al paso digital se representa como una secuencia de valores discretos en función del índice $n$, es decir $h_d[n]$
* 
>🔑*Transformación de la Función de Transferencia:*
* La función de transferencia del filtro digital $H(z)$ se calcula a partir de la transformada Z de la respuesta al paso digital $h_d[n]$. Esto proporciona la representación en el dominio Z del filtro digital.

Ventajas: 
* Simplicidad: El método es relativamente sencillo y proporciona una forma directa de convertir filtros analógicos en digitales preservando la respuesta al paso.
* Preservación de la Respuesta: Conserva la respuesta al paso del filtro analógico, lo que ayuda a mantener ciertas características del filtro original.

 Desventajas
* Distorsión de Frecuencia: La técnica puede introducir distorsiones en la respuesta en frecuencia debido a la aproximación utilizada para la transformación.
* Limitaciones en el Diseño: Puede no ser adecuado para todos los tipos de filtros analógicos, especialmente si la respuesta al paso no se adapta bien a la discretización.


## 4. Método de Euler Adelante
### Euler hacia adelante

- La aproximación discreta de la derivada es:
  $$\frac{d}{dkT} x(kT) = \frac{x(k+1) - x(k)}{T}$$

- Se sabe:
  $$\mathcal{L} { \frac{d}{dt} x(t) } = s X(s)$$

- Al aplicar la transformada Z:
  $$   \[Z{ \frac{x(k+1) - x(k)}{T}} = \frac{zX(z) - X(z)}{T} = \frac{z - 1}{T} X(z)\]$$

- Obtenemos:
  $$X(s) \approx \frac{z - 1}{T} X(z)\]\[s \approx \frac{z - 1}{T}$$

> Un controlador estable en tiempo continuo no necesariamente es estable en tiempo discreto.


## 5. Euler hacia atrás

- La aproximación discreta de la derivada es:
  $$\[\frac{d}{dkT} x(kT) = \frac{x(k) - x(k-1)}{T} \]$$

- Se sabe:
  $$\[ \mathcal{L} { \frac{d}{dt} x(t) } = s X(s)\]$$

- Al aplicar la transformada Z:
  $$\[ Z { \frac{x(k) - x(k-1)}{T}} = \frac{X(z) - z^{-1} X(z)}{T} = \frac{1 - z^{-1}}{T} X(z)  \]$$

- Obtenemos:
  $$\[ s X(s) \approx \frac{1 - z^{-1}}{T} X(z)$$
  $$\] \[ s \approx \frac{1 - z^{-1}}{T} = \frac{z - 1}{Tz}\]$$

> Un controlador estable en tiempo continuo es estable en tiempo discreto.

## 6. Método trapezoidal
Es una técnica utilizada para convertir sistemas de control continuos en sistemas discretos. Este método es particularmente valioso porque preserva las características de estabilidad y respuesta en frecuencia del sistema original cuando se traduce de tiempo continuo a tiempo discreto.La idea principal detrás del método de Tustin es utilizar una aproximación trapezoidal para la integral, que en esencia es un promedio ponderado de la derivada al principio y al final del intervalo de muestreo.
en términos de la variable z (de la transformada Z) de la siguiente manera:

$$\[s \approx \frac{2}{T} \cdot \frac{z - 1}{z + 1}\]$$

Ventajas del Método Tustin
* Conservación de Estabilidad: Un sistema estable en el dominio continuo sigue siendo estable cuando se discretiza utilizando la transformación de Tustin.
* Exactitud en la Respuesta en Frecuencia: El método proporciona una mejor aproximación a la respuesta en frecuencia del sistema continuo en comparación con otros métodos, como Euler hacia adelante o hacia atrás.
* Aplicaciones en Control Digital: Es ampliamente utilizado debido a su capacidad para manejar de manera efectiva el comportamiento de los sistemas en la discretización.

Limitaciones
* Sobrecarga computacional: Comparado con otros métodos más simples, como los métodos de Euler, la transformación de Tustin puede ser más computacionalmente intensiva debido a la necesidad de cálculos adicionales.

##7. Teorema de Muestreo de Nyquist

Es un principio fundamental en la teoría de señales y procesamiento digital. Este teorema establece las condiciones necesarias para poder reconstruir una señal continua a partir de sus muestras discretas sin pérdida de información.

*Principio del teorema:* 
El teorema afirma que una señal continua en el tiempo $x(t)$ que tiene un ancho de banda finito, es decir, cuya frecuencia más alta es $f_max$, puede ser completamente reconstruida a partir de sus muestras siempre que la frecuencia de muestreo $f_s$ sea mayor que el doble de la frecuencia más alta presente en la señal. Matemáticamente, esto se expresa como:

$$  f_s> f_max $$
Esta frecuencia mínima de muestreo se conoce como la frecuencia de Nyquist.

## 8. Conclusiones
* La discretización de señales analógicas es crucial para la implementación de sistemas digitales. Este proceso convierte señales continuas en datos discretos que pueden ser procesados por sistemas digitales.
* El proceso de discretización implica el muestreo (tomar muestras de la señal en intervalos regulares) y la cuantización (aproximar los valores de muestra a un conjunto finito de niveles). Ambas etapas afectan la precisión y calidad de la señal digitalizada.
* El teorema de muestreo de Nyquist establece que para evitar el aliasing, la frecuencia de muestreo debe ser al menos el doble de la frecuencia máxima de la señal analógica. Esto es fundamental para preservar la información en el proceso de discretización.


## 5. Referencias
1. Oppenheim, A. V., & Schafer, R. W. (2009). Discrete-Time Signal Processing (3rd ed.). Prentice Hall.
2. Kuo, B. C. (2003). Digital Control Systems: Theory, Hardware, and Software (3rd ed.). Oxford University Press.
3. Franke, T., & Thomas, H. (2001). Digital Signal Processing and Digital Filters. Springer.
4. Ogata, K. (2010). Discrete-Time Control Systems (2nd ed.). Prentice Hall.
5. Kester, W. (2005). The Data Conversion Handbook. Analog Devices.
