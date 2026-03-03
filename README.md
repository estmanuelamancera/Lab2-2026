### INFORME DE LABORATORIO #2.
## CONVOLUCIÓN, CORRELACIÓN Y TRANSFORMADA DE FOURIER

### DESCRIPCIÓN 
La presente práctica de laboratorio tiene como objetivo aplicar y analizar herramientas fundamentales del Procesamiento Digital de Señales, específicamente la convolución, la correlación y la Transformada de Fourier.
La correlación y la convolución constituyen operaciones básicas empleadas para extraer información de señales, secuencias discretas e incluso imágenes. Aunque matemáticamente son procedimientos relativamente sencillos, poseen una gran utilidad en múltiples aplicaciones. Su estructura permite analizarlas e implementarlas con eficiencia computacional, lo que las convierte en herramientas esenciales en ingeniería. La convolución se utiliza principalmente para el filtrado lineal de señales.
Durante la práctica, se realiza el cálculo manual y computacional de la convolución entre secuencias discretas, el análisis de la correlación cruzada como medida de similitud entre señales y la caracterización de una señal biológica tanto en el dominio del tiempo como en el dominio de la frecuencia. Asimismo, se emplean herramientas de programación para la visualización y análisis de resultados, fortaleciendo la relación entre los conceptos matemáticos y sus aplicaciones en ingeniería biomédica y procesamiento de señales reales.
Esta experiencia permite consolidar conceptos teóricos mediante su implementación práctica, evidenciando la importancia de estas técnicas en el análisis, filtrado y estudio de señales utilizadas en diferentes aplicaciones tecnológicas y biomédicas.

### OBJETIVOS
1.Reconocer la importancia de la aplicación de herramientas matemáticas como la convolución y correlación en el área de procesamiento de señales. 

2.Comprender la convolución como una operación que permite obtener la respuesta de un sistema discreto ante una entrada determinada. 

3.Analizar la correlación como medida de similitud entre dos señales. 

4.Aplicar la Transformada de Fourier como herramienta de análisis en el dominio de la frecuencia.


###  PARTE A.

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
