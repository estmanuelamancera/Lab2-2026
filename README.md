### INFORME DE LABORATORIO #2.
## CONVOLUCIÓN, CORRELACIÓN Y TRANSFORMADA DE FOURIER

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

###  Calculos de la señal 𝑦[𝑛] resultante de la convolución usando sumatorias a mano.
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen1.png" />
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen2.png" />
<img width="600" height="827" alt="image" src="https://github.com/estmanuelamancera/Lab2-2026/blob/main/IMAGENES/Imagen3.png" />

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
