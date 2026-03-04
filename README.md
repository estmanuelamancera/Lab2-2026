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
``` Python
# ============================================
# PARTE A
# ============================================

import numpy as np
import matplotlib.pyplot as plt
```
NumPy se utiliza para realizar operaciones matemáticas y trabajar con arreglos numéricos, especialmente para calcular la convolución y Matplotlib permite generar la representación gráfica de la señal resultante.

## Definición de la función graficar_convolucion
``` Python
def graficar_convolucion(nombre, h, x):
```
Se define una función que recibe:
nombre: identificador del estudiante.
h: respuesta del sistema (definida por los dígitos del código).
x: señal de entrada (definida por los dígitos de la cédula).

## Cálculo de la convolución
``` Python
 # Convolucion
    y = np.convolve(x, h)
```
Se calcula la señal de salida 
𝑦[𝑛]utilizando la función np.convolve(), que implementa la definición matemática de la convolución discreta:
<img width="500" height="300" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen4.png" />

## Creación del eje discreto
``` Python
 # Eje correctamente enumerado
    n_y = np.arange(0, len(y))
```
Se genera el eje horizontal de la gráfica, que representa los valores discretos de 𝑛 correspondientes a la señal de salida.

## Impresión de resultados en consola
``` Python
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
``` Python
 # Crear figura
    plt.figure(figsize=(10,6))
```
Se crea una ventana gráfica con un tamaño específico para visualizar correctamente la señal.

## Gráfica tipo stem (señal discreta)
``` Python
markerline, stemlines, baseline = plt.stem(n_y, y)
```
Se utiliza stem() porque la convolución es una señal discreta, no continua.Este tipo de gráfica representa cada muestra como un punto con una línea vertical.

## Configuración visual
``` Python
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
``` Python
 plt.show()
```
Se presenta la gráfica final en pantalla.

## Definición de datos
``` Python
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
``` Python
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
En esta parte de la práctica se definieron dos señales discretas periódicas: un coseno y un seno de frecuencia 100 Hz, muestreadas con un periodo de muestreo 𝑇𝑠 =1.25𝑚𝑠 para 0 ≤ 𝑛 < 9.
A partir de estas señales se calculó la correlación cruzada con el objetivo de analizar el grado de similitud entre ambas en función del desplazamiento temporal. Por lo tanto, se empleó la definición discreta de correlación y se obtuvo la secuencia 𝑟[𝑘] para retardos comprendidos entre −(𝑁−1) y +(𝑁−1).
Posteriormente, se realizo gráficamente la correlación en función del retardo 𝑘, lo que permitió identificar el comportamiento de la secuencia resultante y determinar el desplazamiento en el cual se presenta el máximo valor absoluto. Este análisis permitió evidenciar el desfase existente entre ambas señales.

![Infografía de periódico moderno ordenado colorido](https://github.com/user-attachments/assets/5a9dce4a-7957-4184-8d8d-7592ad436273)
## 1. CÓDIGO
# Definición de parámetros del sistema y se construyen las señales 
``` Python
import numpy as np
import matplotlib.pyplot as plt

# Parametros

Ts = 1.25e-3          # 1.25 ms
f = 100               # 100 Hz
n = np.arange(0, 9)   # 0 ≤ n < 9

# Definicion de señales
x1 = np.cos(2*np.pi*f*n*Ts)
x2 = np.sin(2*np.pi*f*n*Ts)

print("x1[n] =", np.round(x1,4))
print("x2[n] =", np.round(x2,4))
```
Posteriormente, se definen los parámetros del sistema, incluyendo el periodo de muestreo 𝑇𝑠=1.25 ms, la frecuencia de la señal 𝑓=100 Hz y el vector de índices discretos 𝑛, el cual contiene los valores en el rango 0≤ 𝑛 <9. Estos parámetros permiten establecer el dominio temporal discreto en el que se evaluarán las señales.
A continuación, se construyen las señales discretas 𝑥1[𝑛] y 𝑥2[𝑛] utilizando las funciones trigonométricas coseno y seno, evaluadas como cos (2𝜋𝑓𝑛𝑇𝑠) y sin(2𝜋𝑓𝑛𝑇𝑠), respectivamente. De esta manera, se obtiene la representación digital de ambas señales en función del tiempo discreto. Finalmente, se imprimen los valores de las muestras redondeadas, con el fin de verificar numéricamente los resultados obtenidos.

# Correlación cruzada
En esta sección se buscó determinar el grado de similitud entre las señales 𝑥1[𝑛] y 𝑥2[𝑛] en función del desplazamiento temporal. Para ello, se utilizó la función np.correlate() en modo 'full', esto calculó la correlación cruzada completa, con el fin de evaluar cómo varía la coincidencia entre ambas señales cuando una de ellas se desplaza respecto a la otra.

El objetivo principal fue identificar los valores de correlación asociados a cada retardo 𝑘, permitiendo posteriormente analizar en qué desplazamiento se presenta la máxima similitud y, por lo tanto, el desfase existente entre las señales.
``` Python
# Correlacion cruzada

r = np.correlate(x1, x2, mode='full')
k = np.arange(-len(x1)+1, len(x1))

print("\nRetardos k =", k)
print("Correlacion r[k] =", np.round(r,4))
```
# Pico absoluto
En esta sección se realizó la normalización de la correlación cruzada con el objetivo de escalar sus valores dentro del rango [−1,1]. Para ello, se dividió cada valor de la correlación 𝑟[𝑘] por el valor máximo absoluto de la misma.
Este procedimiento permite obtener una medida relativa de similitud independiente de la amplitud de las señales originales, facilitando la comparación e interpretación del resultado. La correlación normalizada 𝑟 𝑛𝑜𝑟𝑚[𝑘] conserva la forma de la secuencia original, pero expresa el grado de similitud en términos proporcionales.
``` Python
# Normalizacion
r_norm = r / np.max(np.abs(r))

print("\nCorrelacion normalizada =", np.round(r_norm,4))

# Encontrar pico absoluto

idx_peak = np.argmax(np.abs(r))
lag_peak = k[idx_peak]
valor_peak = r[idx_peak]

print(f"\nPico absoluto en k = {lag_peak}")
print(f"Valor del pico = {valor_peak:.4f}")
```
# Visualización 
En esta sección se grafica la correlación cruzada 𝑟[𝑘] utilizando una representación tipo stem, adecuada para señales discretas. Esto permite visualizar la distribución de los valores en función del retardo 𝑘 e identificar el punto de máxima similitud.

Posteriormente, se presenta la correlación normalizada 𝑟 𝑛𝑜𝑟𝑚[𝑘], lo que facilita la interpretación de los resultados en una escala relativa. Ambas gráficas permiten validar visualmente el análisis realizado.

```Python
# Grafica correlacion

plt.figure(figsize=(10,6))
markerline, stemlines, baseline = plt.stem(k, r)
plt.setp(stemlines, color="darkblue")
plt.setp(markerline, marker='o',
         markerfacecolor="skyblue",
         markeredgecolor="skyblue")
baseline.set_visible(False)

plt.title("Correlación cruzada entre x1[n] y x2[n]")
plt.xlabel("Retardo k")
plt.ylabel("r[k]")
plt.grid(True)
plt.show()

# --------------------------------------------
# Grafica correlacion normalizada
# --------------------------------------------

plt.figure(figsize=(10,6))
plt.stem(k, r_norm)
plt.title("Correlación cruzada normalizada")
plt.xlabel("Retardo k")
plt.ylabel("r_norm[k]")
plt.grid(True)
plt.show()
```
## 2.Gráficas y resultados
La función de correlación 𝑟[𝑘] permite medir la similitud entre 𝑥1[𝑛] y 𝑥2[𝑛] cuando una de ellas se desplaza en el tiempo. En los resultados obtenidos, el pico absoluto ocurre en 𝑘=2 con un valor de −3.5, lo que indica que el mayor grado de similitud entre ambas señales se presenta cuando una se desplaza dos muestras respecto a la otra. El signo negativo del pico muestra que las señales están invertidas en fase en ese punto, es decir,cuando una alcanza valores positivos la otra tiende a valores negativos. Esto refleja el desfase existente entre el coseno y el seno. Además, la correlación normalizada alcanza un valor de −1, confirmando que la similitud en magnitud es máxima y que se trata de una coincidencia casi perfecta pero invertida.
<img width="1466" height="434" alt="image" src="https://github.com/user-attachments/assets/afddda46-952e-4f6f-be91-8f9a94d2c21e" />

Las gráficas muestran cómo varía el grado de coincidencia entre ambas señales a medida que se modifica el retardo. Se aprecia que existe un punto donde la magnitud de la correlación es máxima, lo que indica el desplazamiento en el cual las dos secuencias presentan mayor correspondencia estructural. La versión normalizada confirma que esa coincidencia alcanza el valor extremo permitido, evidenciando una relación lineal fuerte entre las señales en ese desplazamiento específico. En general, el comportamiento simétrico de la gráfica refleja la naturaleza periódica de las secuencias analizadas y cómo su alineación cambia progresivamente con el corrimiento.
<img width="1392" height="883" alt="image" src="https://github.com/user-attachments/assets/6052dbab-1121-4ef8-9f7a-d830eca737cb" />

<img width="1418" height="858" alt="image" src="https://github.com/user-attachments/assets/477729b7-1759-4b68-85cf-f1fc977fe2c4" />

## 3. PREGUNTA
# ¿En que situación resulta útil aplicar la correlación cruzada en el procesamiento digital de señales?
La correlación cruzada resulta útil en el procesamiento digital de señales cuando se requiere medir el grado de similitud entre dos señales y determinar el desplazamiento temporal existente entre ellas. Es especialmente aplicada en Detección de Señales (Signal Detection), Sincronización en Sistemas de Comunicaciones Digitales, Estimación de Retardo Temporal (Time Delay Estimation, TDE), Procesamiento de Radar y Sonar, Análisis de Eco en Sistemas Acústicos, así como en Procesamiento de Señales Biomédicas y Reconocimiento de Patrones (Pattern Recognition)[1]. En estos casos, la correlación cruzada permite identificar el punto donde las señales presentan mayor coincidencia, facilitando la extracción de información relevante.






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
### SEÑAL
![SEÑAL EOG](https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/image.png?raw=true)



### Clasificación de la señal
La señal analizada corresponde a una señal EOG generada artificialmente mediante un generador de señales biológicas. Por lo tanto, puede clasificarse como determinística y periódica. Además, al encontrarse muestreada en un archivo digital para su análisis, corresponde a una señal discreta en el tiempo.

### Transformada de Fourier


##### Código
``` Python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from google.colab import files

# Subir archivo
uploaded = files.upload()

# Leer archivo (reemplaza con el nombre real si es necesario)
df = pd.read_csv(list(uploaded.keys())[0])

print("Columnas del archivo:")
print(df.columns)

# Extraer señal (ajusta nombres si es necesario)
senal = df.iloc[:,1].values
tiempo = df.iloc[:,0].values

dt = np.mean(np.diff(tiempo))
fs = 1/dt
N = len(senal)

senal = senal - np.mean(senal)

fft_vals = np.fft.fft(senal)
fft_freq = np.fft.fftfreq(N, dt)

positivos = fft_freq >= 0
fft_freq = fft_freq[positivos]
fft_magnitud = np.abs(fft_vals[positivos]) / N

plt.figure()
plt.plot(fft_freq, fft_magnitud)
plt.title("Transformada de Fourier")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Magnitud")
plt.grid()
plt.show()

psd = (1/(fs*N)) * np.abs(fft_vals)**2
psd = psd[positivos]

plt.figure()
plt.plot(fft_freq, psd)
plt.title("Densidad Espectral de Potencia")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Potencia")
plt.grid()
plt.show()
```


#### Transformada de la señal

![TF](https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/tf.png?raw=true)

#### Densidad espectral de potencia

![densidad espectral](https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/de.png?raw=true)

#### Estadisticos en el dominio de la frecuencia 

``` Python
# Frecuencia media (ponderada por potencia)
frecuencia_media = np.sum(fft_freq * psd) / np.sum(psd)

# Frecuencia mediana
psd_normalizada = psd / np.sum(psd)
acumulada = np.cumsum(psd_normalizada)

frecuencia_mediana = fft_freq[np.where(acumulada >= 0.5)[0][0]]

# Desviación estándar espectral
varianza = np.sum(((fft_freq - frecuencia_media)**2) * psd) / np.sum(psd)
desviacion_std = np.sqrt(varianza)

print("Frecuencia media:", frecuencia_media, "Hz")
print("Frecuencia mediana:", frecuencia_mediana, "Hz")
print("Desviación estándar:", desviacion_std, "Hz")

plt.figure()
plt.hist(fft_freq, bins=30, weights=psd)
plt.title("Histograma de Frecuencias (ponderado por potencia)")
plt.xlabel("Frecuencia (Hz)")
plt.ylabel("Potencia acumulada")
plt.grid()
plt.show()


``` 
#### Resultados


![rta](https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/rta.png?raw=true)

# ANALISIS RESULTADOS
### Alcance y limitaciones de la convolución y la correlación en señales biomédicas

La convolución y la correlación son herramientas fundamentales en el procesamiento de señales biomédicas. La convolución permite modelar la respuesta de sistemas y diseñar filtros digitales para reducir ruido o resaltar información relevante, como complejos QRS en un ECG. La correlación, por su parte, se utiliza para medir similitud entre señales, detectar patrones y estimar retardos temporales.

Sin embargo, presentan limitaciones. Ambas técnicas asumen condiciones ideales como linealidad o estabilidad temporal, que no siempre se cumplen en sistemas biológicos reales. Además, la presencia de ruido o artefactos puede afectar la precisión de los resultados, por lo que requieren un adecuado preprocesamiento de la señal.

### Alcance y limitaciones de la Transformada de Fourier en tiempo real

La Transformada de Fourier permite analizar el contenido frecuencial de una señal, identificar componentes dominantes y calcular su densidad espectral de potencia. Es ampliamente utilizada en señales biomédicas para estudiar ritmos fisiológicos y características espectrales.

En aplicaciones en tiempo real, su principal limitación es que asume que la señal es estacionaria durante el intervalo de análisis. Además, existe un compromiso entre resolución temporal y resolución en frecuencia. Aunque la FFT reduce el tiempo de cálculo, en sistemas con recursos limitados puede generar restricciones de procesamiento o latencia.

### CONCLUSIÓN
- En esta práctica se aplicó la Transformada de Fourier y la densidad espectral de potencia para analizar una señal EOG en el dominio de la frecuencia. Estas herramientas permitieron identificar las componentes frecuenciales dominantes y la distribución de energía de la señal.
- La correlación cruzada permite medir la similitud y estimar el desfase entre señales discretas. Los resultados obtenidos confirmaron que el máximo valor de correlación ocurre en un retardo específico, evidenciando el desplazamiento temporal entre el coseno y el seno. La representación gráfica y la normalización facilitaron la interpretación del comportamiento de ambas señales.
- El análisis espectral es fundamental en señales biomédicas, ya que posibles alteraciones en el contenido frecuencial pueden estar asociadas a patologías o a problemas en la adquisición, como ruido o interferencias. Por tanto, las técnicas aplicadas no solo permiten caracterizar matemáticamente la señal, sino también evaluar su calidad y apoyar procesos de diagnóstico.

### PREGUNTAS PARA LA DISCUSIÓN 
1. ¿Qué utilidad poseen herramientas como la convolución y la correlación en áreas como procesamiento de imágenes?
Las herramientas como la convolución y la correlación son fundamentales en el procesamiento de imágenes, ya que permiten analizar y modificar la información contenida en una imagen. La convolución se utiliza principalmente para aplicar filtros, como detección de bordes, suavizado o realce de detalles, mediante máscaras o kernels que transforman la imagen original [1]. Por su parte, la correlación es útil para la comparación y búsqueda de patrones dentro de una imagen, por ejemplo, en tareas de reconocimiento de objetos o alineación de imágenes.
2. ¿En cuáles contextos de aplicación la transformada de Fourier ofrece un conjunto de características con mayor poder discriminativo que las que
suelen considerarse desde el dominio temporal?
La transformada de Fourier ofrece un mayor poder discriminativo cuando la información relevante de una señal o imagen se encuentra en su contenido frecuencial más que en su forma temporal o espacial. Esto ocurre, por ejemplo, en el análisis de espectros, la detección de componentes periódicas, el filtrado en frecuencia, el procesamiento de audio, la compresión de imágenes y el análisis de texturas. En estos casos, trabajar en el dominio de la frecuencia permite separar componentes que en el dominio temporal pueden estar superpuestas o no ser fácilmente distinguibles. Además, la transformada de Fourier posee propiedades matemáticas que la relacionan directamente con operaciones fundamentales como la convolución y la correlación, lo que refuerza su importancia en el procesamiento de señales e imágenes.[2]
3. ¿En qué se diferencia la correlación cruzada de la convolución?
La correlación cruzada se diferencia de la convolución en que la correlación mide la similitud entre dos señales desplazando una respecto a la otra sin invertirla, mientras que en la convolución una de las señales se invierte antes del desplazamiento. Aunque matemáticamente son operaciones estrechamente relacionadas, conceptualmente la convolución se asocia al efecto que un sistema produce sobre una señal de entrada, mientras que la correlación se utiliza principalmente para medir semejanza o detectar coincidencias[3]. En el procesamiento digital de imágenes, ambas operaciones constituyen herramientas fundamentales para el análisis y la manipulación de información visual, siendo empleadas en tareas como filtrado, comparación y reconocimiento de patrones
   
### REFERENCIAS 
1. X. Zhi and S. Jiang, “Correlation and Convolution Image Filtering Application Analysis,” in Proceedings of the 7th International Conference on Education, Management, Information and Mechanical Engineering (EMIM 2017), Atlantis Press, Apr. 2017, pp. 162–166, doi: 10.2991/emim-17.2017.35 https://www.atlantis-press.com/proceedings/emim-17/25879248
2. P. Hariharan, “The Fourier transform, convolution, and correlation,” in Optical Holography: Principles, Techniques and Applications, Cambridge University Press, 1996, pp. 317–322, doi: 10.1017/CBO9781139174039.021 https://www.cambridge.org/core/books/abs/optical-holography/fourier-transform-convolution-and-correlation/CA63F0D0772985806DEC0A9194367D01
3. X. Zhi and A. Zhi, “Applied Research of Convolution and Correlation in Digital Image Processing,” in Proc. 2016 6th Int. Conf. Mechatronics, Computer and Education Informationization, Atlantis Press, 2016 https://www.atlantis-press.com/proceedings/mcei-16/25867650?utm_source
