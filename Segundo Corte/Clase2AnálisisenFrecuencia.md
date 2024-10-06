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
|      **Aspecto**     |                    **Análisis Temporal**                    | **Análisis en Frecuencia**                         |
|:--------------------:|:-----------------------------------------------------------:|----------------------------------------------------|
|     **_Enfoque_**    | Cambios de señales a lo largo del tiempo                    | Respuesta del sistema a diferentes frecuencias     |
| **_Representación_** | Gráficos de señales vs. tiempo                              | Diagramas de Bode o de Nyquist                     |
|       **_Uso_**      | Análisis de respuestas específicas a entradas               | Evaluación del comportamiento global del sistema   |
|     **_Método_**     | Transformada de Laplace o análisis en el dominio del tiempo | Transformada de Fourier o función de transferencia |

## 2. Resolución matemática mediante fasores
>🔑 *Fasor:* Es una cantidad que tiene tanto magnitud como dirección, y que se representa gráficamente mediante un vector giratorio.
### 2.1. Representación de señales con fasores
La representación de señales mediante fasores es una técnica que permite simplificar el análisis de señales sinusoidales.
<p align="center">
  <img src="https://th.bing.com/th/id/OIP.zuyGPTaOr8swWMclaFrpOwHaD4?rs=1&pid=ImgDetMain" />
</p>

### 2.2. Análisis de sistemas mediante fasores
### 2.3. Relación entre función de transferencia y fasores
### 2.4. Limitaciones del análisis mediante fasores en sistemas no lineales

## 3. Diagramas de frecuencia
### 3.1. Representación gráfica
### 3.2. Análisis espectral
### 3.3. Uso de escalas lineales y logarítmicas

## 4. Análisis en tiempo discreto
### 4.1. Transformación bilineal (Tustin)
### 4.2. Sistemas en tiempo discreto

## 5. Diagramas de Bode
### 5.1. Análisis de estabilidad
### 5.2. Uso de decibelios para la representación de ganancia
### 5.3 Interpretación del desfase en diagramas de Bode
### 5.4 Consideraciones de diseño basadas en diagramas de Bode
### 5.5 Efecto de la frecuencia de Nyquist en sistemas discretos

## 6. Ejercicios
📚
## 7. Conclusiones

## Referencias
