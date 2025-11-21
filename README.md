# VARIABILIDAD DE LA FRECUENCIA CARDIACA (HRV) Y BALANCE AUTONOMICO  LABORATORIO-5
## DESCRIPCIÓN 
Este laboratorio tiene como propósito analizar la variabilidad de la frecuencia cardíaca (HRV) como un indicador del balance entre la actividad simpática y parasimpática del sistema nervioso autónomo. Para ello, se adquiere una señal ECG real en dos condiciones fisiológicas diferentes (reposo y lectura en voz alta), se procesa digitalmente mediante filtrado, detección de picos R y cálculo de intervalos R-R, y finalmente se estudia la HRV tanto en el dominio del tiempo como mediante el diagrama de Poincaré, permitiendo obtener índices cuantitativos de actividad simpática y vagal. La práctica integra conceptos de fisiología, adquisición de señales y procesamiento digital. <br>
## OBJETIVOS
- Identificar cambios en el balance autonómico mediante análisis temporal de la variabilidad de la frecuencia cardíaca (HRV).<br>
- Analizar la variabilidad de la frecuencia cardíaca (HRV) como herramienta para evaluar el balance autonómico. <br>
- Adquirir y procesar correctamente una señal ECG utilizando métodos de filtrado y detección de picos R. <br>
- Comparar la respuesta autonómica del sujeto entre reposo y lectura en voz alta. <br>
- Aplicar herramientas de análisis temporal y no lineal (diagrama de Poincaré) para caracterizar la HRV.<br>
- Interpretar resultados fisiológicos relacionados con actividad simpática y parasimpática. <br> 
## PROCEDIMIENTO 
<img width="627" height="683" alt="image" src="https://github.com/user-attachments/assets/d07f50e0-a005-4168-b820-c8ecad102284" />

# PARTE A - Fundamento teórico y adquisición de señal
## Descripción 
En esta parte se realiza la investigación teórica necesaria para comprender la variabilidad de la frecuencia cardiaca (HRV) y su relación con el sistema nervioso autónomo. Luego, se adquiere la señal ECG de un sujeto en dos condiciones distintas: reposo y lectura en voz alta, con el fin de analizar cómo cambia el balance simpático-parasimpático. <br> 
# PARTE B - Preprocesamiento, filtrado, detección de picos R y HRV en dominio del tiempo
## Descripción
En esta sección se implementan las etapas de procesamiento digital necesarias para limpiar la señal ECG, extraer los picos R y calcular los intervalos R-R. La señal es filtrada utilizando un filtro IIR diseñado por el estudiante, posteriormente se divide según las dos condiciones experimentales y se obtiene la serie temporal de HRV para cada segmento. <br> 
# PARTE C - Diagrama de Poincaré y análisis del balance autonómico
## Descripción
Esta parte consiste en construir el diagrama de Poincaré para cada segmento de ECG y analizar la dispersión de los puntos para determinar cambios en la actividad simpática y vagal. Se calculan los índices CSI (simpático) y CVI (vagal) y se comparan entre reposo y lectura.<br>
