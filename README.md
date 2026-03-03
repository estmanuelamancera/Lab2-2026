### INFORME DE LABORATORIO #2.
# CONVOLUCIÓN, CORRELACIÓN Y TRANSFORMADA DE FOURIER

### DESCRIPCIÓN 
La presente práctica de laboratorio tiene como objetivo aplicar y analizar herramientas fundamentales del Procesamiento Digital de Señales, específicamente la convolución, la correlación y la Transformada de Fourier.
La correlación y la convolución constituyen operaciones básicas empleadas para extraer información de señales, secuencias discretas e incluso imágenes. Aunque matemáticamente son procedimientos relativamente sencillos, poseen una gran utilidad en múltiples aplicaciones. Su estructura permite analizarlas e implementarlas con eficiencia computacional, lo que las convierte en herramientas esenciales en ingeniería. La convolución se utiliza principalmente para el filtrado lineal de señales.
Durante la práctica, se realiza el cálculo manual y computacional de la convolución entre secuencias discretas, el análisis de la correlación cruzada como medida de similitud entre señales y la caracterización de una señal biológica tanto en el dominio del tiempo como en el dominio de la frecuencia. Asimismo, se emplean herramientas de programación para la visualización y análisis de resultados, fortaleciendo la relación entre los conceptos matemáticos y sus aplicaciones en ingeniería biomédica y procesamiento de señales reales.
Esta experiencia permite consolidar conceptos teóricos mediante su implementación práctica, evidenciando la importancia de estas técnicas en el análisis, filtrado y estudio de señales utilizadas en diferentes aplicaciones tecnológicas y biomédicas.

### OBJETIVOS
1. Reconocer la importancia de la aplicación de herramientas matemáticas como la convolución y correlación en el área de procesamiento de señales. 

2. Comprender la convolución como una operación que permite obtener la respuesta de un sistema discreto ante una entrada determinada. 

3. Analizar la correlación como medida de similitud entre dos señales. 

4. Aplicar la Transformada de Fourier como herramienta de análisis en el dominio de la frecuencia.


###  PARTE A.

En la Parte A de la práctica, se realiza el análisis de un sistema discreto definido a partir de los dígitos del código del estudiante y una señal de entrada construida con los dígitos de su cédula. El objetivo es determinar la señal de salida mediante la operación de convolución. Para ello, primero se desarrolla el cálculo manual utilizando la definición por sumatoria, detallando el procedimiento paso a paso y obteniendo la secuencia resultante. Posteriormente, se elabora su representación gráfica y secuencial de forma manual. Finalmente, se implementa el mismo procedimiento en Python para validar los resultados obtenidos analíticamente y se genera la correspondiente representación gráfica computacional, permitiendo comparar ambos métodos y verificar la correcta aplicación de la convolución discreta.

###  Calculos de la señal 𝑦[𝑛] resultante de la convolución usando sumatorias a mano y su grafica.
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen1.png" />
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen2.png" />
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen3.png" />

## Señal 𝑦[𝑛] resultante de la convolución con Python.
<img width="400" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Diagrama1.png" />


# CÓDIGO
## Importacion de librerias
```
# ============================================
# PARTE A
# ============================================

import numpy as np
import matplotlib.pyplot as plt
```
NumPy se utiliza para realizar operaciones matemáticas y trabajar con arreglos numéricos, especialmente para calcular la convolución y Matplotlib permite generar la representación gráfica de la señal resultante.

## Definición de la función graficar_convolucion
```
def graficar_convolucion(nombre, h, x):
```
Se define una función que recibe:
nombre: identificador del estudiante.
h: respuesta del sistema (definida por los dígitos del código).
x: señal de entrada (definida por los dígitos de la cédula).

## Cálculo de la convolución
```
 # Convolucion
    y = np.convolve(x, h)
```
Se calcula la señal de salida 
𝑦[𝑛]utilizando la función np.convolve(), que implementa la definición matemática de la convolución discreta:
<img width="500" height="300" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen4.png" />

## Creación del eje discreto
```
 # Eje correctamente enumerado
    n_y = np.arange(0, len(y))
```
Se genera el eje horizontal de la gráfica, que representa los valores discretos de 𝑛 correspondientes a la señal de salida.

## Impresión de resultados en consola
```
    # Mostrar secuencia
    print(f"\n===== {nombre.upper()} =====")
    print("h[n] =", h)
    print("x[n] =", x)
    print("y[n] =", y)
```
Se muestran en consola:
La respuesta del sistema.
La señal de entrada.
La señal resultante de la convolución.
Esto permite verificar numéricamente el resultado antes de graficarlo.

## Creación de la figura
```
 # Crear figura
    plt.figure(figsize=(10,6))
```
Se crea una ventana gráfica con un tamaño específico para visualizar correctamente la señal.

## Gráfica tipo stem (señal discreta)
```
markerline, stemlines, baseline = plt.stem(n_y, y)
```
Se utiliza stem() porque la convolución es una señal discreta, no continua.Este tipo de gráfica representa cada muestra como un punto con una línea vertical.

## Configuración visual
```
    # Líneas y puntos amarillo claro
    plt.setp(stemlines, color="lightyellow")
    plt.setp(markerline, marker='o',
             markerfacecolor="lightyellow",
             markeredgecolor="lightyellow")

    # Quitar línea base roja
    baseline.set_visible(False)

    # Configurar ejes
    ax = plt.gca()
    ax.set_facecolor("skyblue")

    # Bordes azul oscuro
    for spine in ax.spines.values():
        spine.set_color('darkblue')

    # Números azul oscuro
    ax.tick_params(axis='x', colors='darkblue')
    ax.tick_params(axis='y', colors='darkblue')

    # Forzar que aparezcan todas las muestras (0 a 15)
    ax.set_xticks(np.arange(0, len(y), 1))
    ax.set_xlim(0, len(y)-1)

    plt.title(f"Convolución y[n] - {nombre}", fontsize=14, color="darkblue")
    plt.xlabel("n", color="darkblue")
    plt.ylabel("y[n]", color="darkblue")

    plt.grid(True, color="white")
```

Se modifican:Colores de puntos y líneas,color del fondo,bordes del gráfico,valores mostrados en el eje x,título y etiquetas de los ejes.
Esta sección no altera el cálculo matemático, únicamente mejora la visualización.

## Mostrar la gráfica
```
 plt.show()
```
Se presenta la gráfica final en pantalla.

## Definición de datos
```
# -------------------------------------------------
# DATOS
# -------------------------------------------------

# Manuela
h_manuela = [5,6,0,0,8,7,4]
x_manuela = [1,0,1,4,1,8,7,8,6,7]

# Tomas
h_tomas = [5,6,0,0,8,8,0]
x_tomas = [1,0,2,8,7,8,0,4,3,0]

# Valentina
h_valentina = [5,6,0,0,8,6,7]
x_valentina = [1,0,0,7,4,6,7,4,6,7]
```
Se definen las secuencias:h[n]: sistema discreto y x[n]: señal de entrada.
Se hace esto para tres estudiantes distintos.

## Llamado de la función
```
# -------------------------------------------------
# GRAFICAS
# -------------------------------------------------

graficar_convolucion("Manuela", h_manuela, x_manuela)
graficar_convolucion("Tomas", h_tomas, x_tomas)
graficar_convolucion("Valentina", h_valentina, x_valentina)
```
Se ejecuta la función para cada conjunto de datos, generando:El cálculo de la convolución,la impresión en consola y la gráfica correspondiente.

# Resultados convolucion
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/C1.png" />
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/C2.png" />
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/C3.png" />


###  PARTE B.

###  PARTE C.
Análisis Espectral y Estadísticos de Frecuencia
Esta sección transforma la señal al dominio de la frecuencia mediante la Transformada de Fourier para identificar sus componentes rítmicos. Se calcula la Densidad Espectral de Potencia (PSD) y se extraen métricas avanzadas (frecuencia media, mediana y desviación) para cuantificar la distribución energética y el comportamiento del espectro.


###  Caracterización de la señal.
``` Python

import numpy as np

# Extraemos la columna de voltaje para el análisis
senal = df["Voltaje (V)"].values

# Cálculo de estadísticos
caracteristicas = {
    "Media": np.mean(senal),
    "Mediana": np.median(senal),
    "Desviación Estándar": np.std(senal),
    "Máximo": np.max(senal),
    "Mínimo": np.min(senal)
}

# Mostrar los resultados
print("--- CARACTERIZACIÓN DE LA SEÑAL ---")
for metrica, valor in caracteristicas.items():
    print(f"{metrica:20}: {valor:.6f}")

```


# ANALISIS RESULTADOS
### Alcance y limitaciones de la convolución y la correlación en señales biomédicas

La convolución y la correlación son herramientas fundamentales en el procesamiento de señales biomédicas. La convolución permite modelar la respuesta de sistemas y diseñar filtros digitales para reducir ruido o resaltar información relevante, como complejos QRS en un ECG. La correlación, por su parte, se utiliza para medir similitud entre señales, detectar patrones y estimar retardos temporales.

Sin embargo, presentan limitaciones. Ambas técnicas asumen condiciones ideales como linealidad o estabilidad temporal, que no siempre se cumplen en sistemas biológicos reales. Además, la presencia de ruido o artefactos puede afectar la precisión de los resultados, por lo que requieren un adecuado preprocesamiento de la señal.

### Alcance y limitaciones de la Transformada de Fourier en tiempo real

La Transformada de Fourier permite analizar el contenido frecuencial de una señal, identificar componentes dominantes y calcular su densidad espectral de potencia. Es ampliamente utilizada en señales biomédicas para estudiar ritmos fisiológicos y características espectrales.

En aplicaciones en tiempo real, su principal limitación es que asume que la señal es estacionaria durante el intervalo de análisis. Además, existe un compromiso entre resolución temporal y resolución en frecuencia. Aunque la FFT reduce el tiempo de cálculo, en sistemas con recursos limitados puede generar restricciones de procesamiento o latencia.
