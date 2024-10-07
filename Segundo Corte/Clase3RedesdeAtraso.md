# Diseño de redes de atraso por análisis en frecuencia
El diseño de redes de atraso en sistemas de control digital es una técnica clave utilizada para optimizar el rendimiento de sistemas dinámicos en lazo cerrado mediante el análisis en frecuencia. Este enfoque se basa en herramientas como los diagramas de Bode, que permiten evaluar y ajustar los márgenes de estabilidad, la ganancia y el comportamiento en frecuencia del sistema. A lo largo de este documento, se detallan las ventajas del uso de diagramas de Bode, su relación con los controladores PID, y el procedimiento sistemático para el diseño de redes de atraso. Este método facilita la corrección de errores de estado estacionario y mejora la estabilidad del sistema sin aumentar la susceptibilidad al ruido.

## Índice
1.  Controladores por análisis en frecuencia
2.  Control PID en análisis de frecuencia
3.  Márgenes de ganancia y fase
4.  Redes de atraso
5.  Ejercicios
6.  Conclusiones
7.  Referencias




## 1. Controladores por análisis en frecuencia
*Adelanto de Fase*
Función: Aumenta el ancho de banda del sistema y mejora los márgenes de estabilidad.
Beneficio: Permite que el sistema responda con mayor velocidad.
Consideración: Un incremento en la ganancia a alta frecuencia puede hacer al sistema más susceptible al ruido.

*Atraso de Fase*
Función: Reduce la ganancia en frecuencias altas sin afectar las frecuencias bajas.
Impacto: Disminuye el ancho de banda del sistema, lo que a su vez reduce la velocidad de respuesta.
Beneficio: Disminuye la afectación por ruido, aumentando la estabilidad.

*Atraso – Adelanto de Fase*
Función: Mejora los márgenes de estabilidad y aumenta el ancho de banda.
Beneficio: Disminuye el error en estado estacionario.
Consideración: Ayuda a evitar problemas relacionados con el ruido.


## 2. Control PID en análisis de frecuencia
![]()
El control PID es un tipo de controlador que combina las acciones de proporcional, integral y derivativa. Se considera un caso especial de una red de atraso-adelanto, que permite ajustar la dinámica del sistema controlado.

* Afecta predominantemente la región de alta frecuencia.
Beneficio: Incrementa el ángulo de adelanto de fase, lo que resulta en una mejora en la estabilidad y la rapidez de respuesta del sistema. Este componente ayuda a minimizar el sobrepaso y a lograr un ajuste más ágil.
Parte Proporcional-Integral (PI)

* Se comporta como una red de atraso, enfocándose en las bajas frecuencias.
Contribuye a eliminar el error en estado estacionario y asegura que el sistema alcance el valor deseado a largo plazo, mejorando así la precisión del control.
Sintonización del Control PID
Métodos de Sintonización: Es posible ajustar los parámetros del controlador PID mediante análisis en frecuencia, lo que permite optimizar el rendimiento en función de la respuesta del sistema.
Práctica en la Industria: En entornos industriales, la sintonización del PID se lleva a cabo generalmente utilizando métodos en el dominio del tiempo, que permiten ajustes más directos basados en la respuesta temporal del sistema. Este enfoque es preferido por su simplicidad y efectividad en la implementación práctica.

## 3. Márgenes de ganancia y fase

### 3.1. Márgen de ganancia
El margen de ganancia se define como el cambio en la ganancia de lazo abierto necesario para que un sistema en lazo cerrado se vuelva inestable. Este parámetro se expresa en decibelios (dB), lo que facilita la comparación y el análisis de las variaciones en la ganancia del sistema. La medición del margen de ganancia se realiza tomando como referencia la fase de 180°, un punto crucial que indica el límite en el que el sistema puede volverse inestable al cruzar el umbral de **0 dB**.

![]() Interpretación del Margen de Ganancia
* MG>0: Indica un margen de ganancia positivo, lo que significa que el sistema es estable. En este caso, el sistema puede tolerar aumentos en la ganancia antes de volverse inestable.
* 𝑀𝐺<0: Indica un margen de ganancia negativo, lo que implica que el sistema es inestable. Esto significa que cualquier aumento adicional en la ganancia puede llevar al sistema a un comportamiento incontrolado.

### 3.2. Márgen de fase
El margen de fase se define como el cambio en la fase de lazo abierto que es necesario para que un sistema en lazo cerrado se vuelva inestable. Este margen se expresa en grados (°), lo que permite evaluar la estabilidad del sistema a través del análisis de la fase. Para su medición, se toma como referencia la ganancia unitaria (0 dB), un punto crucial que determina el umbral en el que el sistema puede perder su estabilidad.

![]() Interpretación del Margen de Fase

* 𝑀𝑃>−180°: Indica un margen de fase positivo, lo que significa que el sistema es estable. Esto sugiere que el sistema puede tolerar variaciones en la fase antes de llegar a la inestabilidad.

* 𝑀𝑃<−180°: Indica un margen de fase negativo, lo que implica que el sistema es inestable. En este caso, cualquier cambio adicional en la fase puede llevar al sistema a un comportamiento incontrolado.

### 3.3. Medida de márgenes de estabilidad desde diagrama de Bode 


💡**Figura 1:**
**ADICIONAR IMAGENESSSSS**

Si el margen de ganancia (MG) y el margen de fase (MP) son positivos, el sistema se considera estable en lazo cerrado. Para garantizar un funcionamiento óptimo, es deseable que tanto MG como MP sean lo más grandes posible. Sin embargo, si alguno de estos márgenes es cero o negativo, el sistema puede volverse inestable en lazo cerrado, lo que podría comprometer su rendimiento y control.

### 3.4. Procedimiento de diseño
El procedimiento de diseño en control digital se desarrolla en varias etapas. Primero, se discretiza la planta analógica para obtener un modelo equivalente  𝐺(𝑧), lo que transforma la representación continua del sistema en una adecuada para el análisis digital. Luego, se convierte 𝐺(𝑧) a  G(ω) para trabajar en el dominio de frecuencia. Posteriormente, se grafican los diagramas de Bode, fundamentales para visualizar la respuesta en frecuencia y evaluar la estabilidad y rendimiento del sistema. A continuación, se aplica un método de diseño específico para la función de control C(ω), ajustando así los parámetros del sistema. Finalmente, se recupera C(𝑧) a partir de C(ω)para garantizar que el diseño sea programable en el sistema digital, completando el ciclo de diseño e integrando el controlador en la aplicación deseada.

## 4. Redes de atraso
![]() El diseño de redes de atraso se realiza siguiendo un procedimiento sistemático que asegura que el sistema cumpla con los requisitos de rendimiento establecidos. La metodología se puede resumir en los siguientes pasos:

 * Definición de Especificaciones del Sistema:
 
Determinar los márgenes de ganancia (MG) y margen de fase (MP) requeridos.
 *Transformación de la Planta:

Discretizar la planta analógica G(s) para obtener la representación G(z). Esta transformación se realiza mediante la aproximación de Tustin o la regla de bilinealidad.

<p align="center">$G(z) = G(s) \text{ mediante transformaciones como } z = \frac{2}{T}(1 - z^{-1})$</p>

 * Análisis de Frecuencia:

Graficar los diagramas de Bode de G(z) para observar el comportamiento del sistema. Esto incluye la amplitud y la fase en función de la frecuencia.

* Diseño de la Red de Atraso:
Definir la función de transferencia de la red de atraso C(s) como
<p align="center">$C(s) = \frac{1 + aT_{1}s}{1 + T_{1}s}$</p>

​donde 0<a<1 representa la relación de atenuación.

* Cálculo de Parámetros:
Determinar el valor de 
𝐾𝑝 para garantizar que se cumpla el requisito del error de estado estacionario. Utilizar la fórmula de error de estado estacionario para sistemas en lazo abierto:
<p align="center">$e_{v} = \lim_{s \to 0} \frac{1}{s K_{p} G(s)}$</p>
* Simulación y Ajuste:

Simular el sistema en condiciones de operación utilizando software especializado. Ajustar los parámetros hasta que se logren los márgenes de ganancia y fase deseados.

### 4.1 Consideraciones
Al diseñar redes de atraso, es fundamental tener en cuenta varias consideraciones para garantizar el rendimiento y la estabilidad del sistema:
![]()
*Margen de Estabilidad:
Asegurarse de que los márgenes de ganancia y fase sean positivos. Un MG o MP cero o negativo puede indicar inestabilidad en el sistema.

* Atenuación en Frecuencias Altas:
Las redes de atraso tienden a reducir la ganancia en frecuencias altas, lo que puede disminuir la sensibilidad del sistema al ruido. Es importante encontrar un balance adecuado entre la velocidad de respuesta y la robustez frente al ruido.

* Interacción con Controladores:
Comprender cómo las redes de atraso interactúan con otros controladores en el sistema, especialmente los PID. La parte proporcional del PID puede afectar la estabilidad del sistema si no se ajusta correctamente.

* Limitaciones en el Diseño:
Reconocer que los diseños pueden estar limitados por las características físicas de los componentes. Por ejemplo, en sistemas eléctricos, la frecuencia de corte puede estar determinada por las capacidades y resistencias de los circuitos.

* Documentación:
Mantener una buena documentación del proceso de diseño, incluyendo todas las ecuaciones, resultados de simulaciones y ajustes realizados. Esto facilitará la revisión y futuras mejoras del sistema.


## 9. Ejercicios
Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## 10. Conclusiones
En primer lugar, el diseño de redes de atraso permite mejorar la estabilidad del sistema en frecuencias bajas sin comprometer la ganancia en altas frecuencias, lo que resulta en una reducción del ruido. Esto es crucial para garantizar un rendimiento más robusto y confiable en entornos industriales donde las perturbaciones externas pueden ser significativas.

Seguidamente, al seguir una metodología estructurada que incluye la discretización de la planta y el análisis a través de diagramas de Bode, se logra ajustar de manera precisa los márgenes de ganancia y fase. Esto asegura que el sistema no solo sea estable, sino que también cumpla con los requisitos de error en estado estacionario y velocidad de respuesta.

Finalmente, es importante tener en cuenta las limitaciones físicas del sistema durante el proceso de diseño, ya que los componentes pueden restringir el rango de frecuencias que se pueden controlar.

## 7. Referencias
[1] Ogata, K. (2010). Modern Control Engineering. 5th ed. Prentice Hall.

[2]. Gene Franklin, J. D. Powell, & A. Emami-Naeini. (2014). Feedback Control of Dynamic Systems. 7th ed. Pearson.

[3]. UNAD. (n.d.). Compensación de adelanto, retraso y adelanto-retraso. Universidad Nacional Abierta y a Distancia. 
https://repository.unad.edu.co/bitstream/handle/10596/5790/documents.mx_compensacion-de-adelanto-retraso-y-adelanto-retraso-de.pdf;jsessionid=0CDD36E3DA7DBAF1A89C47C6B0CE2C25?sequence=1.

[4]. Fadel, M. (2023). Diseño de Compensadores. Universidad Nacional de Tucumán. https://catedras.facet.unt.edu.ar/sist-control/wp-content/uploads/sites/77/2023/12/Diseno-de-Compensadores-bis-Fadel.pdf.
