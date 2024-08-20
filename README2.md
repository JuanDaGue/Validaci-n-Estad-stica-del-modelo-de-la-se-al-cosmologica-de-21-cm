# Validaci-n-Estad-stica-del-modelo-de-la-se-al-cosmologica-de-21-cm
Validación Estadística del modelo de la señal cosmológica de 21 cm reportada por el radiotelescopio EDGES



# Validación Estadística del modelo de la señal cosmológica de 21 cm reportada por el radiotelescopio EDGES
**Autor:** Juan David Guerrero Uchima  
**Cordinador de tesis:** Germán Chaparro

---

## Resumen

### Objetivo
Validar los modelos físicos elaborados por la colaboración del radiotelescopio EDGES.

### Modelación
Reproducir la detección reportada de la señal de 21 cm del hidrógeno primordial.

### Validación
Realizar un proceso de validación usando el criterio de discrepancia de Gelman-Rubin.

### Resultados
En los modelos analizados en el proyecto, no se logró validar completamente la absorción del hidrógeno primordial. Aunque hubo modelos estadísticamente sólidos, no se obtenía un valor físico para la temperatura de primer plano (TF), o para la temperatura debida a la emisión de 21 cm.

---

## Introducción

**Experiment to Detect the Global Epoch of Reionization Signature (EDGES)**

Reportaron una distorsión espectral de la línea de 21 cm con un redshift cercano a z=20 que corresponde a un rango de radiofrecuencias entre 50 y 200 MHz.

---

## ¿Cómo se produjo la señal?

### Ionización
Exceso o falta de electrones respecto a un átomo o molécula neutra.

### Recombination
Ocurrió 380 mil años después del Big Bang.

### Reionización
Ocurrió en el rango de redshift (6 < z < 20) entre 150 millones y 1000 millones de años.

### Emisión de 21 cm

**Línea de 21 cm**  
La señal de 21 cm es una línea espectral de radiación electromagnética que se crea por una transición hiperfina del nivel de energía base del hidrógeno.

---

## Resultados y modelo de EDGES

**Señal**  
Perfil de absorción en el espectro radioeléctrico promediado por el cielo, centrado en una frecuencia de 78 MHz. Tiene un mejor ajuste de ancho completo a la mitad del máximo de 19 MHz y una amplitud de 0,5 K.

**Implicaciones**  
La amplitud del perfil es más de un factor de dos mayor que las predicciones más grandes.

---

## Objetivos

1. Descargar la base de datos y analizar los datos obtenidos. Con los datos obtenidos y los modelos físicos, elaborar una simulación de la señal, usando estadística bayesiana, con la cual se pueda obtener distribuciones de probabilidad para los parámetros físicos que dan cuenta de la forma espectral de la señal de 21 cm del hidrógeno primordial.
2. Verificar la capacidad del modelo para predecir datos similares a los que tomó la antena.
3. Determinar si el modelo predice correctamente las mediciones de la antena, o si las detecciones son un producto del rango de incertidumbre de los modelos.
4. Explorar si este análisis se puede utilizar para validar otros experimentos de la era de reionización con distintas antenas de radio.

---

## Datos y Gráficas

**Datos tomados por el radiotelescopio EDGES**

- [https://loco.lab.asu.edu/edges/edges-data-release/](https://loco.lab.asu.edu/edges/edges-data-release/), los cuales contienen la siguiente información:

**Modelación**  
Los datos utilizados son Frecuencia (ν[MHz]) vs Temperatura del cielo (Tsky[K]). La temperatura (Tsky) es modelada como la suma de TF “Temperatura de primer plano” y (T_21) “Temperatura de 21 cm”.

### Modelación

#### Temperatura Debida a la Emisión de 21 cm
T21 es modelada de acuerdo con la siguiente expresión.

#### Temperatura de Foreground
TF(ν) es la temperatura de brillo de primer plano debida a la emisión galáctica e ionosférica, la cual es modelada en forma polinomial en log(ν/νc).

#### Temperatura de Foreground (Reanálisis)
El modelo usado en [6] propone la implementación de la siguiente ecuación para TF(ν) que describe adecuadamente la solución al problema de transferencia radiativa de la emisión de primer plano a través de la ionosfera.

#### Temperatura de Foreground (Bowman)
Bowman realiza una aproximación lineal de la ecuación, asumiendo que b1, b2, y b3 son todos ≪1, con lo que produce la siguiente ecuación para la temperatura de primer plano.

#### Parámetros
Se puede ver que entre las expresiones T21 y TF tienen en total 9 parámetros.  
Estos parámetros son determinados mediante métodos bayesianos utilizando las librerías de Python (Emcee y PyMC3).

---

## Inferencia Bayesiana

La inferencia bayesiana es un tipo de inferencia estadística en la que las evidencias u observaciones se emplean para actualizar o inferir la probabilidad de que una hipótesis pueda ser cierta.

**Donde:**

- A es la hipótesis.
- B es el evento previo.
- P(Ai) es la probabilidad de tener Ai y se le conoce como la probabilidad previa.
- P(B|Ai) es conocida como la función de verosimilitud, la cual da la probabilidad de que se dé B dado Ai.
- El denominador de la ecuación, P(B|Ak)P(Ak), se le llama la probabilidad marginal, que se entiende como la probabilidad de observar la nueva evidencia.

---

## Máxima Verosimilitud

Donde sn es el error en los datos y θ = a0, a1, a2, a3, a4, A, v0, w, τ.

---

## Función Prior

Donde:

- θi son los valores de los parámetros que se conocen previamente.
- ani y bni determinan los intervalos en los cuales van a estar acotados estos parámetros.

**Función Posterior**  
La función posterior se obtiene de hacer el producto de las dos funciones: prior y verosimilitud. Como estas están definidas en base logarítmica, la posterior se obtiene de la suma.

---

## Muestreo de la Posterior

Estos conjuntos de parámetros se exploran a través de random walkers (caminantes aleatorios), cuya función es recorrer toda la distribución aplicando la regla de Bayes, encontrando el conjunto de parámetros que mejor represente la probabilidad posterior.

---

## Desarrollo

### Markov Chain Monte Carlo

**EMCEE**  
Permite encontrar una distribución de parámetros que es consistente con el conjunto de datos, extrayendo muestras de la función de probabilidad posterior.

**PYMC3**  
Realiza un muestreo de la posterior mediante un conjunto de funciones estadísticas incorporadas, para encontrar el conjunto de parámetros más probables.

### Validación (Método de las Discrepancias)

**Discrepancia de Freeman-Tukey**  
Donde:
- \( \Delta \) es la discrepancia.
- \( E_i \) son los valores esperados derivados del modelo.
- \( O_i \) son los valores medidos observados o valores sintéticos.

Para cada parámetro extraído k, es posible comparar la discrepancia simulada con la discrepancia observada. Si el modelo es representativo de los datos, entonces, para muchos gráficos de parámetros, las discrepancias simuladas y observadas deberían ser similares.

**Residuales**  
Están dados por la diferencia entre los datos observados y los datos generados por el modelo.

### Análisis de Convergencia (R-hat)

La librería de Arviz, la cual es una herramienta de análisis de modelos bayesianos que realiza pruebas diagnóstico para la carencia de convergencia comparando la varianza entre diversas cadenas con la varianza en cada cadena.

---

## Resultados

### Modelo PyMC3 (1.0) Priors Gaussianos

- **Profundidad de la Señal 21 cm**: A = 0.72 ± 0.09 K.
- **Criterio de Discrepancia P**: P = 0.82, modelo sólido estadísticamente.
- **Convergencia**: Rhat ≈1.002, las cadenas convergen totalmente.

### Modelo PyMC3 (2.0), Prior Gaussianos y σ Variable

- **Profundidad de la Señal 21 cm**: A = 0.38 ± 0.09 K.
- **Criterio de Discrepancia P**: P = 0.0, modelo estadísticamente poco confiable.
- **Convergencia**: Rhat ≈1.002, las cadenas convergen totalmente.

### Modelo (Bn) Emcee (3.0), Prior Uniformes y σ Fijo

- **Profundidad de la Señal 21 cm**: A = 0.60 ± 0.09 K, poco físico.
- **Criterio de Discrepancia P**: P = 0.35, modelo estadísticamente sólido.
- **Convergencia**: Rhat ≈1.002, las cadenas convergen totalmente.

### Modelo (Bn) Emcee (4.0), Prior σ Uniforme

- **Profundidad de la Señal 21 cm**: A = 0.54 ± 0.06 K.
- **Criterio de Discrepancia P**: P = 1.0, modelo estadísticamente poco confiable.
- **Convergencia**: Rhat ≈1.002, las cadenas convergen totalmente.

---

