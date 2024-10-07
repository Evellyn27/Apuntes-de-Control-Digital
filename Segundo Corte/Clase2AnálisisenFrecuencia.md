# Análisis en Frecuencia 
En la teoría del control, el análisis de frecuencia es una técnica esencial, puesto que permite estudiar la respuesta de los sistemas dinámicos a distintas señales de entrada en función de la frecuencia, o dicho de otra manera, dicha técnica permite "hacerse una idea" sobre cómo es el comportamiento del sistema en el dominio de la frecuencia, en este sentido, este tipo de análisis utiliza herramientas como son los diagramas de Bode o de Nyquist (magnitud frente a fase) para determinar cuáles son las frecuencias que afectan a la respuesta del sistema y, en consecuencia a la estabilidad del mismo ante perturbaciones.
## Índice
1. Fundamentos del análisis de frecuencia
2. Resolución matemática mediante fasores
3. Diagramas de frecuencia
4. Análisis en tiempo discreto
5. Diagramas de Bode
6. Ejercicios
7. Conclusiones

## 1. Fundamentos del análisis de frecuencia

El análisis en frecuencia es un método que se basa en la suposición de que cualquier señal de entrada que puede expresarse como la suma de señales sinusoidales (ondas senos), que a través de la transformada de Fourier, posibilita observar cambios de comportamiento, estos pueden ser la amplificación, la atenuación o el desfase en la señal de salida al modificar la frecuencia de la señal de entrada.

<p align="center">$R=A\cdot sen(\omega kT+\phi)$</p>

>🔑 *Sistema dinámico:* Es un conjunto de reglas matemáticas que describe cómo cambia el estado de un sistema a lo largo del tiempo, ya sea de forma continua o discreta.

### 1.1. Comportamiento de sistemas dinámicos frente a cambios de frecuencia
Si un sistema dinámico está en el dominio tiempo y recibe una señal de entrada sinusoidal, la amplitud y la fase de la señal de salida pueden alterarse en función de la frecuencia de entrada.

>🔑 *Ganancia:* Es el cambio en la magnitud de la salida en relación con la magnitud de la entrada.

>🔑 *Fase:* La fase describe el retraso entre la entrada y la salida.

El comportamiento de un sistema dinámico frente a diferentes frecuencias depende del tipo de sistema:

* **Filtros pasa-bajos:** Atenúan las frecuencias altas y permiten el paso de las bajas.

* **Filtros pasa-altos:** Permiten las frecuencias altas y atenúan las bajas.

* **Sistemas resonantes:** Amplifican frecuencias en un rango específico.

Estos cambios de amplitud y fase en función de la frecuencia se pueden analizar y visualizar utilizando diagramas de Bode, que muestran la relación entre la frecuencia y la respuesta del sistema.

### 1.2. Variaciones en Amplitud y Fase
Las variaciones en amplitud y fase describen cómo un sistema afecta la señal de entrada, modificando su magnitud y su desfase temporal.
* **Variación en amplitud:**
La variación de amplitud se refiere a cómo cambia la magnitud de la señal de salida en comparación con la señal de entrada.

<p align="center">$A_{salida}=A_{entrada}\cdot \left| H (jw) \right|$</p>

Aquí, $\left| H (jw) \right|$ representa cómo el sistema afecta la amplitud de la señal en función de la frecuencia $w$

* **Variación de Fase:**
La variación de fase se refiere al desplazamiento temporal de la señal de salida en comparación con la señal de entrada.

<p align="center">$Fase_{salida}=\lt \left| H (jw) \right|$</p>

### 1.3. Comparación entre Análisis en Frecuencia y Análisis Temporal
El análisis de sistemas puede ser tratado desde distintas perspectivas, entre las cuales el análisis temporal y el análisis en frecuencia son dos de los enfoques más habituales. De cada uno de estos se extraerá información valiosa y complementaria del comportamiento del sistema frente a diversas condiciones. A continuación se presenta una tabla que recoge las diferencias fundamentales de ambos enfoques.

Tabla 1. Comparación entre Análisis en Frecuencia y Análisis Temporal

|      **Aspecto**     |                    **Análisis Temporal**                    | **Análisis en Frecuencia**                         |
|:--------------------:|:-----------------------------------------------------------:|----------------------------------------------------|
|     **_Enfoque_**    | Cambios de señales a lo largo del tiempo                    | Respuesta del sistema a diferentes frecuencias     |
| **_Representación_** | Gráficos de señales vs. tiempo                              | Diagramas de Bode o de Nyquist                     |
|       **_Uso_**      | Análisis de respuestas específicas a entradas               | Evaluación del comportamiento global del sistema   |
|     **_Método_**     | Transformada de Laplace o análisis en el dominio del tiempo | Transformada de Fourier o función de transferencia |

## 2. Resolución matemática mediante fasores
La resolución matemática mediante fasores es un enfoque que simplifica el análisis de sistemas lineales, permitiendo representar y manipular señales sinusoidales de forma más eficiente a través de números complejos, facilitando la obtención de respuestas en el dominio de la frecuencia.

>🔑 *Fasor:* Es una cantidad que tiene tanto magnitud como dirección, y que se representa gráficamente mediante un vector giratorio.

### 2.1. Representación de señales con fasores
La representación de señales mediante fasores es una técnica que permite simplificar el análisis de señales sinusoidales.

<p align="center">
  <img src="https://th.bing.com/th/id/OIP.zuyGPTaOr8swWMclaFrpOwHaD4?rs=1&pid=ImgDetMain" />
</p>

Fig. 1. Representación de señales con fasores

Y pueden estar representados tanto en forma polar:

<p align="center">$F=\left| F \right|\lt \theta$</p>

Como de forma retangular:

<p align="center">$F= a +jb$</p>

### 2.2. Relación entre función de transferencia y fasores

la función de transferencia actúa como un operador que transforma la entrada (en forma de fasor) en una salida (también en forma de fasor) al modificar tanto la amplitud como la fase.

<p align="center">$H(j\omega)=\frac{Y(j\omega)}{X(j\omega)}$</p>

### 2.3. Análisis de sistemas mediante Fasores
El proceso de análisis de sistemas dinámicos mediante fasores se puede desglosar en varios pasos clave:

1. **Sistema de Fasores:**
Se tiene una entrada fasorial, expresada así:
<p align="center">$A_{1}\lt \phi_{1}$</p>

<p align="center">$A_{1}sin(\omega_{1}t+\phi_{1})$</p>

Recordando, el sistema puede ser representado como una función de transferencia G(s), que relaciona la entrada y salida en forma fasorial:

<p align="center">
  <img src="https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/ec883afddec2edf759d6c28980f7f3a7a773a904/Imagenes/plantaControl.png" />
</p>

Fig. 2. Gráfico de sistema de procesos

 Por tanto,
 
<p align="center">$G(s)=\frac{A_{2}\lt \phi_{2}}{A_{1}\lt \phi_{1}}=M\lt \phi$</p>

Donde: 
* **Magnitud M:**
<p align="center">$M=\frac{A_{2}}{A_{1}}$</p>

* **Fase $\phi$ :**
<p align="center">$\phi=\phi_{2}-\phi_{1}$</p>

2. Expresión de la Función de Transferencia:
El análisis comienza expresando la función de transferencia en términos de la frecuencia:

<p align="center">$s=j\omega$</p>

Esto implica que para representar la función de transferencia en el dominio de la frecuencia, se debe considerar la equivalencia:

<p align="center">$z=e^{sT}$</p>

En el contexto del análisis de sistemas, se establece que:

<p align="center">$z=e^{j\omega T}$</p>

Esto permite trabajar con la función de transferencia en un dominio más manejable para el análisis sinusoidal.

💡**Ejemplo 1:**
Se tiene la función de trasnferencia con tiempo de muestreo de 0.1s:

<p align="center">$H(z)=\frac{1}{(z-0.1)(z-5)}$</p>

En términos de frecuencia se expresa como:

<p align="center">$H(e^{j\omega T})=\frac{1}{(e^{j\omega T}-0.1)(e^{j\omega T}-5)}$</p>

<p align="center">$H(e^{j\omega T})=\frac{1}{(Cos(\omega T)+jSen(\omega T)-0.1)(Cos(\omega T)+jSen(\omega T)-5)}$</p>
<p align="center">$H(e^{j\omega T})=\frac{1}{Cos^{2}(\omega T)-jSen^{2}(\omega T)-5.1jSen(\omega T)-5.1Cos(\omega T)+0.5+j2Cos(\omega T)Sen(\omega T)}$</p>

### 2.4. Limitaciones del análisis mediante fasores en sistemas no lineales

El análisis fasorial presenta limitaciones en sistemas dinámicos no lineales:

* **No linealidad:** No sigue el principio de superposición, lo que complica el análisis.
* **Dependencia de la amplitud:** La respuesta de salida varía con la entrada.
* **Métodos alternativos:** Se requieren técnicas como el análisis en el dominio del tiempo o series de Fourier para describir adecuadamente el comportamiento de estos sistemas.
  
## 3. Diagramas de frecuencia
Los diagramas de frecuencia permiten visualizar cómo un sistema responde a señales de entrada con diferentes frecuencias, por ende estos diagramas grafican la magnitud y la fase de la respuesta del sistema en función de la frecuencia. 
### 3.1. Representación gráfica
Los diagramas de frecuencia se representan principalmente a través de dos tipos:

* **Diagrama de Bode:** Se descompone en dos gráficos: uno que representa la respuesta del sistema en términos de amplificación o atenuación, y otro que muestra el desfase.
  <p align="center">
  <img src="https://fr.mathworks.com/discovery/bode-plot/_jcr_content/mainParsys/image_752431827.adapt.full.high.png/1550172621946.png" />
</p>

Fig. 3. Representación de Diagrama de Bode

* **Diagrama de Nyquist:** Representa la respuesta del sistema en un gráfico polar, donde se pueden observar simultáneamente los efectos de amplitud y desfase.

<p align="center">
  <img src="https://es.mathworks.com/help/control/ref/nyquistplotofdynamicsystemexample_01_es.png" />
</p>

Fig. 4. Representación de Diagrama de Nyquist

**Diferencias**

El Diagrama de Bode se caracteriza por representar la respuesta del sistema en dos gráficos separados: uno para la ganancia y otro para el desfase, lo que lo convierte en una herramienta ideal para analizar la estabilidad y los márgenes de ganancia y fase. Por otro lado, el Diagrama de Nyquist combina la información de magnitud y fase en un solo gráfico polar, lo que facilita una evaluación directa de la estabilidad del sistema mediante el criterio de Nyquist.
### 3.2. Análisis espectral
Este análisis ayuda a identificar qué frecuencias dominan en la señal y cómo el sistema filtra o amplifica estas frecuencias.

**Factores a tener en cuenta:**
* Resolución espectral
* Ruido
* Aliasing


### 3.3. Uso de escalas lineales y logarítmicas
En los diagramas de frecuencia, las escalas lineales y logarítmicas juegan un papel clave para la representación de las respuestas del sistema

Tabla 2. Comparación entre escalas lineales y logarítmicas

|     Tipo    |                           Descripción                           |
|:-----------:|:---------------------------------------------------------------:|
|    Lineal   | Representa las frecuencias con espaciado uniforme entre valores |
| Logarítmica | Las frecuencias se representan en potencias de diez             |

## 4. Análisis en tiempo discreto
### 4.1. Transformación bilineal (Tustin)
La transformación bilineal (también llamada método de Tustin) es una técnica utilizada para convertir un sistema continuo (en el dominio $s)$ a un sistema discreto (en el dominio $z)$ . La transformación se basa en una aproximación de la derivada que evita el aliasing y mejora la precisión de las respuestas dinámicas en el diseño de controladores discretos. 

El método de Tustin se expresa como:

<p align="center">$w=\frac{2}{T}\frac{z-1}{z+1}$</p>

Aproximando:
<p align="center">$z=\frac{\left( 1+\frac{wT}{2} \right)}{\left(1-\frac{wT}{2}\right)}$</p>

Se reemplaza $z=e^{jwT}$:

<p align="center">$w=j\frac{2}{T}tan\left( \frac{wT}{2} \right)$</p>

Se sustituye $w=jv$:

<p align="center">$v=\frac{2}{T}tan\left( \frac{wT}{2} \right)$</p>

### 4.2. Sistemas en tiempo discreto
Tras aplicar la transformación bilineal (Tustin), se mapea el plano z al plano w para analizar el sistema discreto en una representación más cercana al dominio continuo.Al operar en el plano w, es más fácil realizar ajustes en los controladores digitales mientras se mantienen las características deseadas del sistema original, especialmente en aplicaciones de filtrado y control.

## 5. Diagramas de Bode
### 5.1. Efecto de los parametros
En el diagrama de Bode, los polos tienen un efecto fundamental en la respuesta del sistema en frecuencia. Un polo cercano al eje imaginario $j\omega$ como se muestra en la imagen, causa un aumento en la magnitud hasta llegar a la frecuencia natural $\omega​_{n}$ después de lo cual la magnitud comienza a decaer.

<p align="center">
  <img src="https://github.com/Evellyn27/Apuntes-de-Control-Digital/blob/87c42b7803fe9952431bc7f913a6acd75cb603bc/Imagenes/Polosyceros.png"/>
</p>

Fig. 5. Diagrama de Bode en 3D

La presencia de un polo también afecta la fase, que desciende en una cantidad proporcional a la cercanía del polo a la frecuencia de interés. A medida que la frecuencia se aproxima a $\omega​_{n}$ la fase experimenta una transición, generalmente de -45° hasta -90° por cada polo.

Además, si el sistema presenta un amortiguamiento bajo (bajo $\zeta$), se observará un pico resonante en la magnitud alrededor de $\omega​_{n}$ como indica el máximo en la gráfica de magnitud de la imagen. Este efecto de resonancia es clave en sistemas de control que buscan estabilidad, ya que puede amplificar ciertas frecuencias, afectando la respuesta total del sistema.

### 5.2. Consideraciones claves para la interpretación de los diagramas de Bode

1. Identificar polos y ceros: Analizar cómo influyen en la magnitud y fase para determinar el tipo de filtro o respuesta que tiene el sistema.

2. Márgenes de estabilidad: Revisar los márgenes de fase y ganancia para determinar la robustez del sistema.

3. Frecuencia de corte: Determinar a qué frecuencias el sistema empieza a atenuar señales.

4. Pendientes de las curvas: La pendiente en la gráfica de magnitud ofrece información sobre la atenuación o amplificación del sistema, clave para definir si actúa como un filtro paso bajo, paso alto, etc.

5. Resonancia: Verificar si existen picos de resonancia que puedan generar amplificaciones no deseadas en frecuencias particulares.

## 6. Ejercicios
📚 **Ejercicio 1:**
Calcular la magnitud de la siguiente función de transferencia:

<p align="center">$H(s)=\frac{s^{2}+6s+8}{\left( s+3 \right)\left( s+5 \right)\left( s^{2}+s+5 \right)}$</p>

Se factoriza el numerador:

<p align="center">$(s+2)(s+4)=s^{2}+6s+8$</p>

Los ceros de la función son: 

<p align="center">$s=-2$</p>
<p align="center">$s=-4$</p>

Revisamos los polos de la función:

<p align="center">$s=-3$</p>
<p align="center">$s=-5$</p>
<p align="center">$s=-2$</p>

Ahora, se reemplaza s=jω en la función de transferencia:

<p align="center">$H(jw)=\frac{jw^{2}+6jw+8}{\left( jw+3 \right)\left( jw+5 \right)\left( jw^{2}+jw+5 \right)}
$</p>

Entonces:
<p align="center">$\left| jw+2 \right|=\sqrt{w^{2}+4}$</p>
<p align="center">$w=-2$</p>
<p align="center">$w=-4$</p>

El mismo procedimiento se le hace al denominador:

<p align="center">$w=-3$</p>
<p align="center">$w=-5$</p>

<p align="center">$∣H(jω)∣dB​=20log_{10}∣H(jω)∣$</p>
La magnitud en dB para ω=1 es aproximadamente -28.94 dB.

## 7. Conclusiones
De este trabajo se puede llegar a concluir lo siguiente:

En primer lugar, el análisis en frecuencia permite estudiar el comportamiento de los sistemas dinámicos en función de las diferentes frecuencias de entrada, proporcionando una visión clara sobre cómo responden en términos de amplitud y fase. Lo anterior, resulta clave para identificar los puntos críticos donde el sistema puede ser más vulnerable a inestabilidades o perturbaciones.

Por otra parte, los diagramas de Bode y Nyquist son herramientas fundamentales en este tipo de análisis, ya que permiten visualizar de manera gráfica las respuestas de un sistema a diversas frecuencias, facilitando la interpretación del comportamiento de amplificación o atenuación, así como los desfases introducidos en la señal de salida.

Finalmente, aunque el análisis de frecuencia es una técnica poderosa, presenta limitaciones en sistemas no lineales, donde la dependencia de la amplitud y la falta de superposición dificultan su uso, en tales casos, es necesario recurrir a otros métodos como el análisis en el dominio del tiempo o la serie de Fourier para lograr una caracterización más precisa del sistema.

## Referencias
[1] Diagrama de bode paso a paso: Lo que NO te enseñaron - 2024. (s.f.). Control Automático Educación. https://controlautomaticoeducacion.com/control-realimentado/1-diagrama-de-bode/#:~:text=Aquí%20aprenderas%20a%20graficar,%20hacer%20y

[2] Fasores. (s.f.). Análisis de Circuitos Eléctricos. https://circuitoselectricosac.blogspot.com/p/12-fasores.html#:~:text=Un%20fasor%20es%20un%20numero%20complejo%20que%20representa,eléctricos%20en%20corriente%20alterna%20excitados%20por%20fuentes%20sinusoidales.

[3] ¿Qué representa un diagrama de Bode y qué es un polo y cero de un diagrama de Bode? (2020, 14 de abril). Stack. https://isolution.pro/es/q/et13490787/que-representa-un-diagrama-de-bode-y-que-es-un-polo-y-cero-de-un-diagrama-de-bode

[4] Universidad De Cantabria. (s.f.). Análisis frecuencial. En Automática. Open Course Ware. https://ocw.unican.es/pluginfile.php/1829/course/section/1438/capitulo_7.1.pdf#:~:text=Esta%20metodología,%20se%20conoce%20como%20"Análisis
