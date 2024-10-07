# Diseño de redes de atraso por análisis en frecuencia
El diseño de redes de atraso en sistemas de control digital es una técnica clave utilizada para optimizar el rendimiento de sistemas dinámicos en lazo cerrado mediante el análisis en frecuencia. Este enfoque se basa en herramientas como los diagramas de Bode, que permiten evaluar y ajustar los márgenes de estabilidad, la ganancia y el comportamiento en frecuencia del sistema. A lo largo de este documento, se detallan las ventajas del uso de diagramas de Bode, su relación con los controladores PID, y el procedimiento sistemático para el diseño de redes de atraso. Este método facilita la corrección de errores de estado estacionario y mejora la estabilidad del sistema sin aumentar la susceptibilidad al ruido.

## Índice
1.  Controladores por análisis en frecuencia
2.  Control PID en análisis de frecuencia
3.  Márgenes de ganancia y fase
4.  Ganancia proporcional
5.  Diseño de redes de atraso por análisis de frecuencia
6.  Ejercicios
7.  Conclusiones
10. Referencias




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

## 5. Ecuaciones
Para la edición de ecuaciones debe utilizar la etiqueta '$$' al comienzo y final de la ecuación para que la ecuación quede centrada ocupando una línea. Si se quiere que la ecuación quede integrada en el texto debe utilizar la etiqueta '$' al comienzo y final de la ecuación. Las ecuaciones pueden ser editadas utilizando el código LATEX, en el siguiente enlace encuentran un editor de ecuaciones que les genera el código. http://www.alciro.org/tools/matematicas/editor-ecuaciones.jsp . Sin embargo hay muchas otras herramientas que pueden utilizar para esto.

💡**Ejemplo 1:** si se va a representar la ecuación de la ley de Ohm se puede mostrar así $R=\frac{V}{I}$ o también,

$$R=\frac{V}{I}$$

## 6. Figuras
Todas las figuras que incluya deben ser generadas por ustedes, **no utilizar las figuras de las presentaciones**. Para incluir figuras puede seguir los siguientes pasos:
* Primero escribimos ![]().
* Después escribimos, dentro de los corchetes, el texto alternativo. Este es opcional y solo entra en acción cuando no se puede cargar la imagen correctamente.
* Después escribimos, dentro de los paréntesis, la ubicación del archivo (ya sea una url o una ubicación dentro de algun folder local). Se recomienda poner las imágenes en una carpeta que se llame imágenes dentro del repositorio github para que no tengan problemas al cargar las imágenes.

💡**Ejemplo 2:**

![Figura de prueba](images/plantilla/Captura2.PNG)

Figura 1. Figura de prueba

Incluya la respectiva etiqueta a modo de descripción de la figura y mantenga numeración consecutiva para todas las figuras de la clase.

## 7. Tablas
En caso de necesitar la inclusión de tablas para organizar información se recomienda el uso de la herramienta del siguiente enlace https://www.tablesgenerator.com/markdown_tables , la cual permite organizar la información dentro de la tabla y genera el código markdown automáticamente:

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

## 8. Código
Teniendo en cuenta que el curso requiere del desarrollo de código matlab, c, c++ u otro. Si requiere incluir pequeños segmentos de código en los apuntes hágalos de la siguiente manera:

💡**Ejemplo 4:**
```
var sumar2 = function(numero) {
  return numero + 2;
}
```

## 9. Ejercicios
Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## 10. Conclusiones
Agregue unas breves conclusiones sobre los temas trabajados en cada clase, puede ser a modo de resumen de lo trabajado o a indicando lo aprendido en cada clase

## 11. Referencias
Agregue un subtítulo al final donde pueda poner todas las referencias consultadas incluyendo el origen o fuente de los ejercicios planteados. Tambien dentro del texto referencie los textos o artículos consultados y las figuras y tablas dentro de la explicación de las mismas.
