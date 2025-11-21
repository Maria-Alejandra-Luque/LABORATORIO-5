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

# PARTE A - Fundamento teórico y adquisición de señal
## Descripción 
En esta parte se realiza la investigación teórica necesaria para comprender la variabilidad de la frecuencia cardiaca (HRV) y su relación con el sistema nervioso autónomo. Luego, se adquiere la señal ECG de un sujeto en dos condiciones distintas: reposo y lectura en voz alta, con el fin de analizar cómo cambia el balance simpático-parasimpático. <br> 
## Diagrama 
![Infografía de periódico moderno ordenado colorido](https://github.com/user-attachments/assets/de986083-a97a-49f7-a888-7099cf8e85fb)/><br> 


##  𝘼𝙘𝙩𝙞𝙫𝙞𝙙𝙖𝙙 𝙎𝙞𝙢𝙥𝙖𝙩𝙞𝙘𝙖 𝙮 𝙋𝙖𝙧𝙖𝙨𝙞𝙢𝙥𝙖𝙩𝙞𝙘𝙖 𝙙𝙚𝙡 𝙨𝙞𝙨𝙩𝙚𝙢𝙖 𝙣𝙚𝙧𝙫𝙞𝙤𝙨𝙤 𝙖𝙪𝙩𝙤𝙣𝙤𝙢𝙤 
El cuerpo humano está preparado para mantener un equilibrio entre la actividad y el descanso. Esto es posible gracias al sistema nervioso autónomo, encargado de regular muchas funciones involuntarias del organismo. Dentro de este sistema se encuentran el sistema nervioso simpático y el sistema nervioso parasimpático, dos fuerzas opuestas que actúan de manera complementaria para preservar el bienestar y la estabilidad del cuerpo.<br>

### Sistema nervioso simpático
Este sistema es el encargado de activar y acelerar las funciones del cuerpo, siendo responsable de la respuesta de “huida o lucha” cuando una persona se enfrenta a una situación de peligro o estrés. Su acción es crucial incluso en reposo, ya que prepara al organismo para responder ante emergencias.
El sistema nervioso simpático actúa mediante la activación de diferentes vías, lo que provoca un aumento del ritmo cardíaco y respiratorio, elevación de la presión arterial, dilatación de las pupilas y una redistribución del flujo sanguíneo: la sangre se desvía de la piel, el estómago y los intestinos para dirigirse al cerebro, al corazón y a los músculos necesarios para ejecutar una respuesta rápida frente a la actividad simpática.<br>
<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/020bdc9e-a239-4702-98f8-d14481371c70" /><br>

### Sistema nervioso parasimpatico
Este sistema controla la actividad del músculo liso, del músculo cardíaco y de las glándulas. Se encarga de la respuesta de descanso, ya que participa en la disminución del ritmo cardíaco, la relajación del tracto gastrointestinal y urinario, y el aumento de la actividad glandular e intestinal. Como resultado, el sistema parasimpático promueve el almacenamiento de energía y regula funciones vitales del organismo, como la digestión y la micción.<br>
<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/c19dd53b-295b-4d34-bd32-27721d647de7" /><br>

##  𝙀𝙛𝙚𝙘𝙩𝙤 𝙙𝙚 𝙡𝙖 𝙖𝙘𝙩𝙞𝙫𝙞𝙙𝙖𝙙 𝙨𝙞𝙢𝙥𝙖𝙩𝙞𝙘𝙖 𝙙𝙚𝙡 𝙨𝙞𝙨𝙩𝙚𝙢𝙖 𝙣𝙚𝙧𝙫𝙞𝙤𝙨𝙤 𝙖𝙪𝙩ó𝙣𝙤𝙢𝙤:

La regulación de la frecuencia cardíaca depende de la acción conjunta del sistema nervioso simpático y parasimpático. Ambos modulan la actividad de los nodos cardíacos y la contractilidad del miocardio mediante comunicación eléctrica y neuroquímica. El sistema simpático favorece el aumento de la frecuencia cardíaca, mientras que el parasimpático la reduce, relajando el corazón. El equilibrio entre ambos mantiene la homeostasis cardiovascular; cuando este balance se altera, pueden aparecer diversas condiciones y patologías.<br>

El corazón recibe inervación de ambas ramas del sistema nervioso autónomo a través del plexo cardíaco, situado alrededor de la base del corazón y de los grandes vasos. La inervación simpática se origina en la médula espinal a nivel torácico: las fibras preganglionares llegan al plexo y se distribuyen hacia los nodos SA, AV y el miocardio, liberando noradrenalina sobre los receptores beta-1 adrenérgicos, lo que incrementa la contractilidad y la frecuencia cardíaca.<br>

Por otro lado, el sistema parasimpático proviene del nervio vago. Sus fibras preganglionares hacen sinapsis en ganglios intrínsecos ubicados en la grasa cardíaca y la pared auricular. Luego liberan acetilcolina (ACh) sobre receptores muscarínicos M2 acoplados a proteínas G, lo que abre canales de potasio e hiperpolariza la membrana del nodo SA, alejando el potencial de membrana del umbral. Además, se reduce el AMPc y con ello la velocidad de conducción, ralentizando la despolarización espontánea y disminuyendo la contractilidad auricular y la frecuencia cardíaca.<br>

<img width="235" height="214" alt="image" src="https://github.com/user-attachments/assets/be489263-4c9b-4fdd-9770-8ffe82b37113" /><br>

##  V𝙖𝙧𝙞𝙖𝙗𝙞𝙡𝙞𝙙𝙖𝙙 𝙙𝙚 𝙡𝙖 𝙛𝙧𝙚𝙘𝙪𝙚𝙣𝙘𝙞𝙖 𝙘𝙖𝙧𝙙𝙞𝙖𝙘𝙖 (𝙃𝙍𝘾) 𝙤𝙗𝙩𝙚𝙣𝙞𝙙𝙖 𝙖 𝙥𝙖𝙧𝙩𝙞𝙧 𝙙𝙚 𝙡𝙖 𝙨𝙚𝙣̃𝙖𝙡 𝙚𝙡𝙚𝙘𝙩𝙧𝙤𝙘𝙖𝙧𝙙𝙞𝙤𝙜𝙧𝙖𝙛𝙞𝙘𝙖 (𝙀𝘾𝙂).

La variabilidad de la frecuencia cardíaca (HRV) analiza cómo cambia el tiempo entre un latido y otro del corazón, es decir, los intervalos RR obtenidos a partir del ECG. Estos cambios reflejan el equilibrio entre el sistema simpático y parasimpático, que regulan la actividad cardíaca.
Para calcularla, primero se detectan los picos R de la señal y se mide el intervalo entre cada par consecutivo. Con esta serie de datos se aplica un análisis en el dominio del tiempo o en el dominio de la frecuencia. En el primero suelen usarse parámetros como SDNN y RMSSD, mientras que en el segundo se estudian componentes como LF y HF, cuyo cociente LF/HF permite estimar el balance autonómico.<br>

La HRV se ha convertido en un indicador útil tanto en investigación como en clínica. Una variabilidad alta suele relacionarse con buena salud y adaptación fisiológica, mientras que una variabilidad baja puede asociarse con estrés o alteraciones autonómicas. Por ello, el análisis de HRV a partir del ECG es considerado un método no invasivo y confiable para evaluar el control nervioso del corazón.<br> 
<img width="1508" height="823" alt="image" src="https://github.com/user-attachments/assets/6fa7fa5f-ad91-4ef0-8d71-5e6c6b486071" /><br>

##  𝘿𝙞𝙖𝙜𝙧𝙖𝙢𝙖 𝙙𝙚 𝙥𝙤𝙞𝙣𝙘𝙖𝙧𝙚 𝙘𝙤𝙢𝙤 𝙝𝙚𝙧𝙧𝙖𝙢𝙞𝙚𝙣𝙩𝙖 𝙙𝙚 𝙖𝙣𝙖𝙡𝙞𝙨𝙞𝙨 𝙙𝙚 𝙡𝙖 𝙎𝙚𝙣̃𝙖𝙡 𝙍-
El diagrama de Poincaré es una herramienta empleada para el análisis no lineal de la variabilidad de la frecuencia cardiaca a partir de la serie de intervalos R-R, es decir, los tiempos entre latidos consecutivos. Mediante una transformación matemática, esta información se representa de forma gráfica para visualizar la dinámica del ritmo cardíaco. En este método, cada intervalo R-R se coloca en relación con el siguiente (RRₙ frente a RRₙ₊₁), generando una nube de puntos en un plano. La forma y dispersión de esta nube reflejan el comportamiento dinámico del sistema cardiovascular, permitiendo identificar niveles de regularidad, variabilidad o patrones particulares. Al ser una representación bidimensional, facilita la comprensión de cómo cambian los intervalos entre latidos a lo largo del tiempo y ofrece una visión más clara del comportamiento general del sistema nervioso autónomo.[5]

<img width="112" height="116" alt="image" src="https://github.com/user-attachments/assets/d75f40f5-f904-4600-9922-5b3e23fb4aa2" /><br>


Cuando el diagrama de Poincaré muestra una figura con forma de elipse estrecha y alargada, esto se interpreta como una baja variabilidad cardiaca. En esta condición, los intervalos entre latidos varían muy poco, lo cual sugiere que el sistema nervioso autónomo tiene una capacidad limitada para adaptarse a cambios internos o externos. En contraste, una figura más amplia, dispersa o aproximada a un círculo indica una mayor variabilidad cardíaca y un mejor equilibrio entre las ramas simpática y parasimpática.

A diferencia de los métodos lineales tradicionales, el diagrama de Poincaré aporta una perspectiva geométrica y topológica de la dinámica del ritmo cardíaco, permitiendo identificar comportamientos no lineales que no pueden ser detectados mediante estadísticas convencionales. Por esta razón, se utiliza con frecuencia para analizar la serie R-R y evaluar el control autonómico del corazón en situaciones de reposo, estrés o enfermedad.[4]<br>
<img width="146" height="151" alt="image" src="https://github.com/user-attachments/assets/5f0d411d-16bc-4f6b-9875-2bffc1d23085" /><br>


# PARTE B - Preprocesamiento, filtrado, detección de picos R y HRV en dominio del tiempo
## Descripción
En esta sección se implementan las etapas de procesamiento digital necesarias para limpiar la señal ECG, extraer los picos R y calcular los intervalos R-R. La señal es filtrada utilizando un filtro IIR diseñado por el estudiante, posteriormente se divide según las dos condiciones experimentales y se obtiene la serie temporal de HRV para cada segmento. <br> 
## Diagrama 
<img width="800" height="1448" alt="Infografía de periódico moderno ordenado colorido" src="https://github.com/user-attachments/assets/75472c18-b002-4268-877e-0cdedf6e2a97" /><br> 

# Diseño Filtro

<img width="327" height="883" alt="image" src="imagen_2025-11-20_214947303.png" />
<img width="327" height="883" alt="image" src="imagen_2025-11-20_215036048.png" />


## CÓDIGO 
```

#      LAB ECG - PREPROCESAMIENTO + HRV
#   FILTRO IIR + R-PEAKS + RR + POINCARÉ
#   ZOOM EN QRS + PICOS R MORADOS + RR MARCADO

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from scipy import signal
from google.colab import drive

# 1. MONTAR GOOGLE DRIVE

drive.mount('/content/drive')

# 2. PARÁMETROS

Fs = 500.0
seg_duration_s = 2 * 60  # 2 minutos

# Filtro IIR digital (orden 4)
b = np.array([0.04514067, 0.0, -0.09028134, 0.0, 0.04514067])
a = np.array([1.0, -3.31025739, 4.11831107, -2.30421103, 0.49616466])

```
Este fragmento define el inicio del procesamiento del laboratorio de ECG. Se importan las librerías necesarias para cargar datos, filtrarlos y graficar resultados. Luego se monta Google Drive para acceder a los archivos del experimento. Después se establecen los parámetros principales: la frecuencia de muestreo de la señal (500 Hz) y la duración de cada segmento de análisis (2 minutos). Finalmente, se declaran los coeficientes b y a del filtro digital IIR de orden 4, que será utilizado más adelante para limpiar la señal ECG antes de realizar la detección de picos R y el análisis de HRV. <br>

```
# 3. ECUACIÓN EN DIFERENCIAS

def print_difference_equation():
    print("\n=== ECUACIÓN EN DIFERENCIAS DEL FILTRO IIR ===\n")
    print(
        "y[n] = "
        + f"{b[0]:.8f} x[n] + "
        + f"{b[1]:.8f} x[n-1] + "
        + f"{b[2]:.8f} x[n-2] + "
        + f"{b[3]:.8f} x[n-3] + "
        + f"{b[4]:.8f} x[n-4] "
        + f"- {a[1]:.8f} y[n-1] - {a[2]:.8f} y[n-2] - {a[3]:.8f} y[n-3] - {a[4]:.8f} y[n-4]"
    )
    print("\n(Estados iniciales = 0)\n")
    )
```
Este fragmento de código carga una señal ECG, la filtra con un IIR de orden 4, detecta los picos R usando un método basado en derivada–cuadrado–ventana móvil, calcula los intervalos RR y sus versiones interpoladas, obtiene los índices de variabilidad cardíaca (SD1, SD2, CSI y CVI) y genera diversas gráficas: señal original vs filtrada, picos R marcados en morado, zoom del complejo QRS, curva RR(t) y diagramas de Poincaré para analizar la dinámica del ritmo cardiaco.. <br> 

```

# 4. CARGAR ECG

def load_ecg(path):
    df = pd.read_csv(path)

    if df.shape[1] == 1:
        x = df.iloc[:, 0].astype(float).values
        t = np.arange(len(x)) / Fs
        return t, x, Fs

    elif df.shape[1] == 2:
        t = df.iloc[:, 0].astype(float).values
        x = df.iloc[:, 1].astype(float).values
        Fs_est = 1.0 / np.mean(np.diff(t))
        return t, x, Fs_est

    else:
        raise ValueError("El CSV debe tener 1 o 2 columnas.")

```
Este fragmento lee un archivo CSV que contiene un ECG y organiza los datos según su formato: si el archivo tiene una sola columna, la toma como la señal ECG y crea el vector de tiempo usando la frecuencia de muestreo definida; si tiene dos columnas, interpreta la primera como tiempo y la segunda como la señal, calculando además la frecuencia de muestreo a partir de las diferencias entre muestras. Si el archivo no tiene 1 o 2 columnas, genera un error indicando que el formato no es válido. <br>

```
# 5. FILTRADO

def apply_iir(x):
    return signal.filtfilt(b, a, x)
```
Este fragmento aplica el filtro IIR definido por los coeficientes b y a a la señal ECG x utilizando filtfilt(), que realiza un filtrado hacia adelante y hacia atrás para evitar el desfase y obtener una señal filtrada sin retraso en fase. En resumen, limpia la señal eliminando ruido sin distorsionar la forma del ECG.<br> 

```
# 6. DETECCIÓN DE PICOS R

def detect_r_peaks(ecg_segment, fs):
    diff = np.diff(ecg_segment, prepend=ecg_segment[0])
    sq = diff**2
    win = max(1, int(150 * fs / 1000))
    integ = np.convolve(sq, np.ones(win)/win, mode='same')

    dist = int(0.25 * fs)
    thresh = np.mean(integ) + 0.5 * np.std(integ)
    peaks, _ = signal.find_peaks(integ, distance=dist, height=thresh)

    refined = []
    radius = int(0.05 * fs)
    for p in peaks:
        L = max(0, p - radius)
        R = min(len(ecg_segment)-1, p + radius)
        local = L + np.argmax(ecg_segment[L:R+1])
        refined.append(local)

    return np.unique(refined), integ

```
Este fragmento detecta los picos R dentro de un segmento de ECG. Primero calcula la derivada de la señal y la eleva al cuadrado para resaltar los complejos QRS; luego aplica una ventana móvil de 150 ms para obtener una señal integrada que facilita la detección. A partir de esta señal integrada, busca picos usando un umbral adaptativo y una distancia mínima entre latidos (250 ms). Después, cada pico inicial se refina buscando, en una ventana pequeña alrededor, el máximo real del ECG para ubicar con precisión el pico R. Finalmente, devuelve la lista de picos R detectados y la señal integrada usada en el proceso.<br>

```
# 7. INTERVALOS RR

def compute_rr(peaks, fs):
    if len(peaks) < 2:
        return np.array([])
    return np.diff(peaks) / fs


# RR interpolada para graficar
def interpolate_rr(peaks, rr, fs, total_len):
    if len(rr) < 2:
        return None, None
    t_rr = peaks[1:] / fs
    t = np.arange(total_len) / fs
    rr_interp = np.interp(t, t_rr, rr * 1000)
    return t, rr_interp

```
Este fragmento calcula los intervalos RR y genera una versión interpolada para graficarlos de manera continua. La función compute_rr() toma las posiciones de los picos R y obtiene los intervalos RR dividiendo la diferencia entre picos consecutivos por la frecuencia de muestreo. La función interpolate_rr() usa esos RR ya calculados para construir una señal RR(t) suave: primero obtiene el tiempo exacto de cada intervalo RR, luego genera una escala temporal uniforme y finalmente interpola los valores para obtener una curva continua en milisegundos. Si no hay suficientes RR, ambas funciones devuelven resultados vacíos.<br>

```
# 9. FUNCIÓN PRINCIPAL

def process_ecg_file(path):

    print("\nCargando archivo:", path)
    t, x, fs = load_ecg(path)

    print(f"Señal cargada: {len(x)} muestras — Fs={fs:.2f} Hz")
    print_difference_equation()

   
    # FILTRADO
    x_f = apply_iir(x)

    plt.figure(figsize=(18,5))
    plt.plot(t, x, alpha=0.5, label="Original")
    plt.plot(t, x_f, color="#FF00FF", label="Filtrada")
    plt.title("Señal Original vs Filtrada")
    plt.legend()
    plt.grid()
    plt.show()
```
Este fragmento de la función principal carga la señal ECG desde el archivo indicado, muestra en pantalla cuántas muestras tiene y cuál es la frecuencia de muestreo estimada, imprime la ecuación en diferencias del filtro IIR que se usará y luego aplica dicho filtro a la señal para eliminar ruido sin introducir desfase. Finalmente, grafica la señal original junto con la señal filtrada, permitiendo visualizar claramente el efecto del filtrado sobre el ECG.<br>

```

    # SEGMENTOS

    seg_len = int(seg_duration_s * fs)
    seg1 = x_f[:seg_len]
    seg2 = x_f[seg_len:2*seg_len]

   
    # DETECCIÓN R
    
    p1, _ = detect_r_peaks(seg1, fs)
    p2, _ = detect_r_peaks(seg2, fs)

    
    #   ECG FILTRADA + PICOS R (MORADO)
    #
    plt.figure(figsize=(18,6))
    plt.plot(seg1, color="#FF00FF", label="ECG Filtrada")
    plt.scatter(p1, seg1[p1], color="purple", s=25, label="R-peaks")
    plt.title("Segmento 1 — ECG Filtrada + Picos R (Morado)")
    plt.legend(); plt.grid(); plt.show()

    plt.figure(figsize=(18,6))
    plt.plot(seg2, color="#FF00FF", label="ECG Filtrada")
    plt.scatter(p2, seg2[p2], color="purple", s=25, label="R-peaks")
    plt.title("Segmento 2 — ECG Filtrada + Picos R (Morado)")
    plt.legend(); plt.grid(); plt.show()

    
    # ZOOM EN QRS (Modo B)
    
    def zoom_qrs(seg, peaks, title):
        i1 = peaks[5] - 200
        i2 = peaks[10] + 200
        i1 = max(0, i1)
        i2 = min(len(seg), i2)
        plt.figure(figsize=(18,5))
        plt.plot(seg[i1:i2], color="#FF00FF")
        plt.title(title)
        plt.grid()
        plt.show()

    zoom_qrs(seg1, p1, "Zoom centrado en QRS — Segmento 1")
    zoom_qrs(seg2, p2, "Zoom centrado en QRS — Segmento 2")

```
Este fragmento divide la señal ECG filtrada en dos segmentos de dos minutos, detecta los picos R en cada uno y luego genera visualizaciones que permiten evaluar la calidad de la detección. Primero calcula cuántas muestras corresponden a dos minutos y separa la señal en segmento 1 (reposo) y segmento 2 (lectura). Después aplica el algoritmo de detección de picos R a cada segmento para obtener las posiciones de los complejos QRS. Posteriormente grafica cada segmento mostrando la señal filtrada en magenta y los picos R marcados en color morado, facilitando la verificación visual de la detección. Finalmente, incluye una función que realiza un zoom alrededor de algunos complejos QRS para observarlos en detalle y confirmar que los picos detectados coinciden con la morfología real del QRS.<br>

```

    # RR
    rr1 = compute_rr(p1, fs)
    rr2 = compute_rr(p2, fs)

    t1_rr, rr1_ts = interpolate_rr(p1, rr1, fs, len(seg1))
    t2_rr, rr2_ts = interpolate_rr(p2, rr2, fs, len(seg2))

    # RR(t) CON MARCADORES DE RR REALES
    
    plt.figure(figsize=(18,5))
    plt.plot(t1_rr, rr1_ts, color="#FF00FF", label="RR(t) interpolado")
    plt.scatter(p1[1:]/fs, rr1*1000, color="purple", s=30, label="RR reales")
    plt.title("RR(t) — Segmento 1")
    plt.xlabel("Tiempo (s)")
    plt.ylabel("Intervalo RR (ms)")
    plt.legend()
    plt.grid()
    plt.show()

    plt.figure(figsize=(18,5))
    plt.plot(t2_rr, rr2_ts, color="#FF00FF", label="RR(t) interpolado")
    plt.scatter(p2[1:]/fs, rr2*1000, color="purple", s=30, label="RR reales")
    plt.title("RR(t) — Segmento 2")
    plt.xlabel("Tiempo (s)")
    plt.ylabel("Intervalo RR (ms)")
    plt.legend()
    plt.grid()
    plt.show()
```
Este fragmento calcula los intervalos RR de cada segmento y genera las gráficas que muestran su evolución temporal. Primero obtiene los RR reales restando las posiciones consecutivas de los picos R y convirtiéndolos a segundos. Luego interpola estos valores para construir una señal continua RR(t), lo que permite visualizar la variabilidad latido a latido sin saltos. Después grafica, para cada segmento, la curva RR(t) en color magenta y superpone los valores reales de los intervalos RR como puntos morados, de modo que se puede comparar la interpolación con los datos originales y analizar cómo cambia el ritmo cardíaco durante el reposo y durante la lectura.<br>

## GRÁFICAS 
<img width="776" height="323" alt="image" src="https://github.com/user-attachments/assets/295f2bdd-be58-4a81-b024-12ebd638bab9" /><br>
La gráfica muestra la comparación entre la señal ECG original y la señal filtrada mediante un filtro IIR de cuarto orden. La señal cruda presenta variaciones y componentes de alta frecuencia no deseados, mientras que la señal filtrada en color magenta evidencia una reducción significativa del ruido sin distorsionar la morfología del ECG. Este preprocesamiento permite resaltar los complejos QRS y preparar la señal para la detección precisa de picos R y el posterior análisis de variabilidad cardíaca (HRV).<br>

<img width="746" height="268" alt="image" src="https://github.com/user-attachments/assets/e3125e82-a14b-4fe8-a626-940f35445816" /><br>
La gráfica muestra el primer segmento de la señal ECG ya filtrada y los picos R identificados automáticamente, representados como puntos morados sobre la onda. La señal filtrada permite observar con claridad la morfología del complejo QRS, mientras que la marcación de los picos R confirma la correcta detección de los latidos durante los primeros dos minutos en reposo. Esta visualización es fundamental para validar el preprocesamiento y garantizar la precisión en el cálculo posterior de los intervalos R-R y el análisis de variabilidad cardíaca (HRV).<br>

<img width="751" height="271" alt="image" src="https://github.com/user-attachments/assets/89be3987-fbc3-499e-9cfa-1ccbcef5741c" /><br>
La gráfica del segundo segmento muestra la señal ECG filtrada durante la etapa de lectura en voz alta, junto con los picos R detectados automáticamente y marcados en color morado. Este periodo presenta una mayor variabilidad en la amplitud y en la distribución de los latidos, reflejando la influencia del esfuerzo cognitivo y vocal sobre el ritmo cardíaco. La correcta identificación de los picos R permite analizar cómo cambia la actividad cardíaca frente a una tarea activa, y sirve como base para el cálculo de los intervalos R-R y la evaluación del comportamiento autonómico en comparación con el reposo.<br>

<img width="733" height="226" alt="image" src="https://github.com/user-attachments/assets/3318e234-dc6d-4a12-b563-c3a3ce73e820" /><br>
La gráfica presenta un zoom del complejo QRS en el primer segmento, permitiendo observar con mayor detalle la morfología característica de cada latido. Al ampliar esta región, se evidencia un QRS bien definido y consistente, confirmando que el filtrado y la detección de picos R fueron precisos. Esta visualización es fundamental para validar que los puntos detectados corresponden efectivamente a los máximos del complejo QRS, garantizando la confiabilidad del cálculo posterior de los intervalos R-R y del análisis de variabilidad cardíaca.<br>

<img width="743" height="224" alt="image" src="https://github.com/user-attachments/assets/51742dfe-bc27-4b31-ab43-652328c1870e" /><br>
La gráfica muestra un zoom enfocado en los complejos QRS del segundo segmento de la señal de ECG, permitiendo observar con mayor detalle los picos asociados a la despolarización ventricular. Se aprecia un ritmo relativamente regular y amplitudes que oscilan entre aproximadamente −1.5 y +1.7 mV, lo cual es coherente con una señal cardíaca fisiológica. Este análisis resulta clave para validar la calidad del registro y preparar el procesamiento posterior, como la detección automática de picos R, segmentación de latidos o implementación de algoritmos como Pan–Tompkins.<br>

<img width="764" height="232" alt="image" src="https://github.com/user-attachments/assets/6bdeb197-3d23-4f24-9759-97ad3493a1f8" /><br>
La gráfica representa la evolución temporal del intervalo RR correspondiente al primer segmento de la señal de ECG. Se muestran los valores reales calculados a partir de los picos R y una curva interpolada que suaviza la variabilidad latido a latido. Se observa un ritmo cardíaco relativamente estable, con intervalos que oscilan mayormente entre 500 y 650 ms, salvo algunas variaciones puntuales que podrían estar asociadas a artefactos o fluctuaciones fisiológicas. Este análisis permite visualizar la dinámica de los intervalos RR y constituye la base para evaluar la variabilidad cardíaca (HRV) y explorar el estado autonómico del paciente.<br>

<img width="765" height="243" alt="image" src="https://github.com/user-attachments/assets/c746fc84-4e01-46ed-93c1-3d727d4c6b73" /><br>
La gráfica muestra la variación del intervalo RR a lo largo del segundo segmento de la señal de ECG. Los valores reales calculados a partir de los picos R se comparan con la curva interpolada, la cual permite visualizar de forma más continua la dinámica cardíaca. En este segmento se observan fluctuaciones más amplias que en el segmento anterior, con picos aislados que superan los 1200 ms e indican posibles latidos ectópicos o irregularidades transitorias. Aun así, el patrón general permanece dentro de un rango fisiológico, lo que permite usar este segmento para el análisis de variabilidad cardíaca (HRV) y la evaluación del balance autonómico.<br>
                                                                                                                                    








# PARTE C - Diagrama de Poincaré y análisis del balance autonómico
## Descripción
Esta parte consiste en construir el diagrama de Poincaré para cada segmento de ECG y analizar la dispersión de los puntos para determinar cambios en la actividad simpática y parasimpatica. Se calculan los índices CSI (simpático) y CVI (vagal) y se comparan entre reposo y lectura.<br>


## CÓDIGO 
```
#              PARTE C - LAB ECG
#       DIAGRAMA DE POINCARÉ + CVI / CSI

import numpy as np
import matplotlib.pyplot as plt

# 1. FUNCIONES — PARTE C
   
    # Convertir a ms
    rr_ms = rr * 1000.0
    
    # Mínimo 3 intervalos
    if len(rr_ms) < 3:
        return np.nan, np.nan, np.nan, np.nan
    
    # Cálculo clásico
    sd1 = np.std((rr_ms[1:] - rr_ms[:-1]) / np.sqrt(2))
    sd2 = np.std((rr_ms[1:] + rr_ms[:-1]) / np.sqrt(2))

    # Protecciones numéricas
    CVI = np.log10(max(sd1 * sd2, 1e-12))
    CSI = sd2 / max(sd1, 1e-12)

    return sd1, sd2, CVI, CSI


def plot_poincare(rr, title):
    """
    Genera el diagrama de Poincaré RR(n) vs RR(n+1) en MS
    """
    rr_ms = rr * 1000.0

    plt.figure(figsize=(6, 6))
    plt.scatter(rr_ms[:-1], rr_ms[1:], color="#FF00FF", s=20)
    plt.title(title)
    plt.xlabel("RR(n) [ms]")
    plt.ylabel("RR(n+1) [ms]")
    plt.grid()
    plt.show()


# 2. CÁLCULO DE SD1, SD2, CVI, CSI
#    (USANDO rr1 y rr2 DE LA PARTE B)


sd1_1, sd2_1, CVI1, CSI1 = poincare_indices_ms(rr1)
sd1_2, sd2_2, CVI2, CSI2 = poincare_indices_ms(rr2)


# 3. GRÁFICAS DE POINCARÉ

plot_poincare(rr1, "Poincaré — Segmento 1 (Reposo)")
plot_poincare(rr2, "Poincaré — Segmento 2 (Lectura)")


# 4. RESULTADOS NUMÉRICOS


print("\n========== ÍNDICES DE POINCARÉ ==========\n")

print("SEGMENTO 1 — REPOSO")
print(f"SD1 = {sd1_1:.2f} ms")
print(f"SD2 = {sd2_1:.2f} ms")
print(f"CVI = {CVI1:.4f}")
print(f"CSI = {CSI1:.4f}")

print("\nSEGMENTO 2 — LECTURA")
print(f"SD1 = {sd1_2:.2f} ms")
print(f"SD2 = {sd2_2:.2f} ms")
print(f"CVI = {CVI2:.4f}")
print(f"CSI = {CSI2:.4f}")

print("\n==========================================")

```
En la Parte C del código se utilizan los intervalos R-R obtenidos previamente para generar el diagrama de Poincaré y calcular los índices SD1, SD2, CVI y CSI. El código primero convierte los intervalos R-R a milisegundos y luego construye la gráfica Poincaré, que representa RR(n) frente a RR(n+1), permitiendo visualizar cómo varía el intervalo entre latidos consecutivos. Esto nos sirvio para la representación, para analizar la variabilidad cardiaca de manera gráfica y obtener SD1 y SD2, que son medidas matemáticas de la dispersión de los puntos. Con estos valores, el código calculo CVI y CSI, que son índices usados para cuantificar patrones de variabilidad en la señal del ECG. En resumen, la Parte C se implemento para la generación del diagrama de Poincaré y el cálculo automático de sus índices asociados.

## Gráficas 

<img width="518" height="480" alt="image" src="https://github.com/user-attachments/assets/b094e4cc-f0f9-41f8-ade8-c17aad8c2630" />
<img width="501" height="500" alt="image" src="https://github.com/user-attachments/assets/c752a722-cd5e-414a-9ace-ee02c911898a" />
<img width="252" height="198" alt="image" src="https://github.com/user-attachments/assets/51d84049-fe8d-4f10-b0e2-e64cfa37554f" /><br>

Los diagramas de Poincaré muestran un comportamiento claramente diferente entre el segmento de reposo y el segmento de lectura. En reposo, la nube de puntos es compacta y con poca dispersión, indicando un ritmo cardíaco estable y una baja variabilidad, coherente con un predominio parasimpático. Durante la lectura en voz alta, la nube aumenta su dispersión tanto en SD1 como en SD2, reflejando una mayor variabilidad instantánea y a largo plazo. Los índices CSI y CVI también aumentan, lo que sugiere una mayor activación simpática asociada al esfuerzo cognitivo y la variación respiratoria. En conjunto, los resultados evidencian que la lectura en voz alta genera un incremento en la variabilidad cardíaca y activa el sistema nervioso autónomo en comparación con el estado de reposo.
## Concluciones 
1. La variabilidad de la frecuencia cardíaca permitió evaluar con precisión el comportamiento autonómico del participante en las dos condiciones del experimento. A partir de los intervalos R-R derivados del ECG y del análisis no lineal mediante el diagrama de Poincaré, fue posible identificar cómo cambió el balance simpático–parasimpático entre el reposo y la lectura en voz alta, demostrando que la HRV es un indicador sensible a la actividad autonómica y a la demanda cognitiva.

2. Durante la fase de reposo (segmento 1), los parámetros no lineales mostraron valores bajos y estables (SD1 = 0.0685; SD2 = 0.0644), lo que refleja una variabilidad reducida y un ritmo cardíaco más regular. El diagrama de Poincaré presentó una nube de puntos compacta, indicando una dinámica cardiaca estable, asociada al predominio del tono parasimpático y a una mayor estabilidad del sistema cardiovascular en ausencia de estímulos.

3. En la condición de lectura en voz alta (segmento 2), se observó un aumento notable en la dispersión de los puntos del diagrama y un incremento de los índices de variabilidad (SD1 = 0.1161; SD2 = 0.1552). Este comportamiento evidencia un cambio en la dinámica autonómica: los intervalos R-R mostraron mayor fluctuación y los índices CSI y CVI aumentaron (CSI = 1.3371; CVI = –1.7442), indicando una mayor activación simpática, influenciada por la atención, el esfuerzo cognitivo y la alteración del patrón respiratorio durante la lectura.
En conjunto, los resultados demuestran que la lectura en voz alta genera una modificación clara en la variabilidad cardíaca, aumentando la actividad simpática y haciendo más evidente la dinámica no lineal de los latidos, mientras que en reposo predomina la estabilidad y el control parasimpático. Esto confirma la utilidad del análisis HRV y del diagrama de Poincaré para evaluar el comportamiento autonómico en diferentes estados fisiológicos.




# REFERENCIAS 
[1]Researchgate.net.de https://www.researchgate.net/figure/Figura-173-Los-sistemas-simpatico-y-parasimpatico_fig2_313160220<br>

[2]Sistema nervioso simpático. (2023, 30 octubre). Kenhub. https://www.kenhub.com/es/library/anatomia-es/sistema-nervioso-simpatico<br>

[3]Sistema nervioso parasimpático. (2023, 30 octubre). Kenhub. https://www.kenhub.com/es/library/anatomia-es/sistema-nervioso-parasimpatico<br> 
[4]Fishman, M., Jacono, F. J., Park, S., Jamasebi, R., Thungtong, A., Loparo, K. A., & Dick, T. E. (2012). A method for analyzing temporal patterns of variability of a time series from Poincaré plots. Journal Of Applied Physiology, 113(2), 297-306. https://doi.org/10.1152/japplphysiol.01377.2010.<br>
[5]Hrv_Admin. (s. f.). Understanding the Poincaré plot – HRV Health. https://hrvhealth.org/blog/?p=124.<br>
