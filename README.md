

markdown
# Validación Estadística del Modelo de la Señal Cosmológica de 21 cm Reportada por el Radiotelescopio EDGES
**Autor:** Juan David Guerrero Uchima  
**Coordinador de Tesis:** Germán Chaparro

---

### **Validación Estadística de la Señal de 21 cm**
- Contribuyó a la investigación sobre la señal cosmológica detectada por el radiotelescopio EDGES.
- Realizó análisis estadísticos para validar la señal, asegurando la credibilidad de los hallazgos.
- Presentó los resultados en un informe detallado, destacando la importancia de los hallazgos en el campo de la cosmología.

El repositorio contiene la validación estadística de la señal cosmológica de 21 cm realizada por EDGES, compuesto por 4 modelos. Dos de estos modelos utilizaron las librerías Pyemcee, y los otros dos se realizaron mediante Emcee. Los modelos se dividen en dos categorías: uno puramente estadístico, aunque físicamente incorrecto, y otro que toma en cuenta consideraciones físicas al elaborar el modelo.

## Distribución del Contenido

En este repositorio se encuentran las carpetas con los modelos elaborados en Google Colaboratory, los modelos de Pyemcee y Emcee. También hay materiales en formato de PowerPoint para quienes deseen revisar de forma más explicada todos los aspectos del proceso de validación y los resultados obtenidos en el trabajo.

En la carpeta data puedes encontrar los datos tomados por el equipo de EDGES de la antena de radio, además de la carpeta Plots, donde están guardadas las principales gráficas que se elaboraron en el proyecto.

Además, hay dos archivos que explican en resumen cada uno de los pasos en la elaboración de este proyecto, además de enlaces a algunas lecturas recomendadas y material bibliográfico.
## Resumen

### Objetivo
Validar los modelos físicos elaborados por la colaboración del radiotelescopio EDGES.

### Modelación
Reproducir la detección reportada de la señal de 21 cm del hidrógeno primordial.

## Modelo

Los datos para nuestro modelo son frecuenciua vs temperatura sky.
 El modelo consiste en obtener $T_{sky}$ como la suma de $T_F$ (-.--------)y $T_{21}$ (Temperatura relacionada a la trancicion de 21 cm) $T_{sky}=T_F(\nu)+T_{21}(\nu)$
 
$T_F( \nu)$ esta modelada por la siguiente ecuación 

$$T_F(\nu)=a_o\left(\frac{\nu}{\nu_c}\right)^{-2.5}+a_1\left(\frac{\nu}{\nu_c}\right)^{-2.5}\log\left(\frac{\nu}{\nu_c}\right)+a_2\left(\frac{\nu}{\nu_c}\right)^{-2.5}\left[\log\left(\frac{\nu}{\nu_c}\right)\right]^2+a_3\left(\frac{\nu}{\nu_c}\right)^{-4.5}+a_4\left(\frac{\nu}{\nu_c}\right)^{-2.0}+$$

donde $T_F ( ν )$ es la temperatura de brillo de la emisión de primer plano, $ν$ es lafrecuencia, $ν_c$ es la frecuencia central de la banda observada y los coeficientes $a_n$ se ajustan a los datos. La función anterior es una aproximación lineal, centrada en $ν_c$ ,
$T_{21}$ tiene la siguiente expresón 
$$T_{21}=-A\left[\frac{1-e^{\tau e^B}}{1-e^{-\tau}}\right]$$

Donde 
$$B=\frac{4(v-\nu_o)^2}{w^2}\log\left(-{1\over \tau }\log\left({{1+e^{-\tau}}\over 2}\right)\right)$$


### Validación
Realizar un proceso de validación usando el criterio de discrepancia de Gelman-Rubin.

### Resultados
En los modelos analizados en el proyecto, no se logró validar completamente la absorción del hidrógeno primordial. Aunque hubo modelos estadísticamente sólidos, no se obtuvo un valor físico para la temperatura de primer plano (TF) o para la temperatura debida a la emisión de 21 cm.

```All libraries and datas are in the files
    For more complex infromation go the next link https://github.com/JuanDaGue/Seminario
```